# Change Log

All notable changes to this project will be documented in this file. This
project adheres to [Semantic Versioning](http://semver.org/).

## Unreleased

## 0.5.9

### Fixes

- Fix unsafe var errors on functions ([#471](https://github.com/open-policy-agent/opa/issues/471), [#467](https://github.com/open-policy-agent/opa/issues/467))

### Miscellaneous

- Fix docs example of set union
- Fix file watch bug causing panic in server mode
- Modify AST to represent function names as refs
- Refactor runtime to separate init and start
- Refactor test runner to accept Store argument

## 0.5.8

### Fixes

- Substitute comprehension terms requring eval ([#453](https://github.com/open-policy-agent/opa/issues/453))

### Miscellaneous

- Add alpine-based Docker image
- Add stdin mode to opa fmt
- Fix syntax error in comprehension example
- Improve input parsing performance in V0 API
- Refactor loader to read inputs once (allows use of process substitution)
- Remove backup creation from fmt subcommand
- Remove use of sprintf in formatter

## 0.5.7

This release adds a new `test` subcommand to OPA. The `test` subcommand enables policy unit testing. The unit tests are expressed as rules containing assertions over test data. The `test` subcommand provides a test runner that automatically discovers and executes these test rules. See `opa test --help` for examples.

### Fixes

- Fix type error marshalling bug ([#391](https://github.com/open-policy-agent/opa/issues/391))
- Fix type inference bug ([#381](https://github.com/open-policy-agent/opa/issues/381))
- Fix unification bug ([#436](https://github.com/open-policy-agent/opa/issues/436))
- Fix type inferecen bug for partial objects with non-string keys ([#440](https://github.com/open-policy-agent/opa/issues/440))
- Suppress match errors if closures contained errors ([#438](https://github.com/open-policy-agent/opa/issues/438))

## 0.5.6

As part of this release, logrus was revendored to deal with the naming issue. If you use logrus, or one of your other dependencies does (such as Docker), be sure to check out https://github.com/sirupsen/logrus/issues/570#issuecomment-313933276.

### Fixes

- Fix incorrect REPL interpretation of some exprs ([#433](https://github.com/open-policy-agent/opa/issues/433))
- Fix inaccurate location information in some parser errors ([#214](https://github.com/open-policy-agent/opa/issues/214))

### Miscellaneous

- Add Terraform Testing tutorial to documentation
- Add shorthand for defining partial documents (e.g., `p[1]` instead of `p[1] { true }`)
- Add walk built-in function to recursively process nested documents
- Refactor Policy API response representations based on usage

## 0.5.5

This release adds [Diagnostics](http://www.openpolicyagent.org/docs/rest-api.html#diagnostics) support to the server. This greatly improves OPA's debuggability when deployed as a daemon.

### Miscellaneous

- Fix data race in the parser extensions
- Fix index.html GET requests returning error on empty input
- Fix race condition in watch test
- Fix image version in HTTP API tutorial
- Add metrics command to the REPL
- Limit length of pretty printed values in the REPL
- Simplify input query parameters in data GET requests
- Update server to support pretty explanations

## 0.5.4

### Miscellaneous

- Properly remove temporary files when running `opa fmt -d`
- Add support for refs with composite operands (e.g,. `p[[x,y]]`)

## 0.5.3

### Fixes

- Add support for raw strings ([#265](https://github.com/open-policy-agent/opa/issues/265))
- Add support to cancel compilation after some number of errors ([#249](https://github.com/open-policy-agent/opa/issues/249))

### Miscellaneous

- Add Kubernetes admission control tutorial
- Add tracing support to rego package
- Add watch package for watching changes to queries
- Add dependencies package to perform dependency analysis on ASTs

## 0.5.2

### Fixes

- Fix mobile view navigation bug
- Fix panic in compiler from concurrent map writes ([#379](https://github.com/open-policy-agent/opa/pull/379)
- Fix ambiguous syntax around body and set comprehensions ([#377](https://github.com/open-policy-agent/opa/issues/377))

### Miscellaneous

- Add support for set and object comprehensions
- Add support for system.main policy in server
- Add transaction support in rego package
- Improve type checking error messages
- Format REPL modules before printing them

## 0.5.1

### Fixes

- Correct `opa fmt` panic on missing files
- Fix minor site issues

### Miscellaneous

- Add rego examples with input and compiler
- Add support for query cancellation

## 0.5.0

### User Functions

OPA now supports user-defined functions that have the same semantics as built-in
functions. This allows policy authors to quickly define reusable pieces of logic
in Rego without overloading the input document or thinking about variable
safety.

### Storage Improvements

The storage layer has been improved to support single-writer/multiple-reader
concurrency. The storage interfaces have been simplified in the process. Users
can rely on https://godoc.org/github.com/open-policy-agent/opa/storage/inmem in
place of the old storage package.

### Website Refresh

The website has been redesigned and the documentation has been ported over to
GitBook.

### `opa check` and `opa fmt`

OPA supports two new commands that check and format policies. Check out `opa
help` for more information.

### Miscellaneous

- Add YAML serialization built-ins
- Add time built-ins

### Fixes

- Fixed incorrect source locations on refs and manually constructed terms. All
  term locations should be set correctly now.
- Fixed evaluation bug that caused partial sets and partial objects to be
  undefined in some cases.

## 0.4.10

This release includes a bunch of new built-in functions to help with string manipulation, JWTs, and more.

The JSON marshalling built-ins have been renamed. Policies that used `json_unmarshal` and `json_marshal` before will need to be updated to use `json.marshal` and `json.unmarshal` respectively.

### Misc

- Add `else` keyword
- Improved undefined built-in error message
- Fixed error message in `-` built-in
- Fixed exit instructions in REPL tutorial
- Relax safety check for built-in outputs

## 0.4.9

This release includes a bunch of cool stuff!

- Basic type checking for queries and virtual docs ([#312](https://github.com/open-policy-agent/opa/pull/312))
- Optimizations for HTTP API authorization policies ([#319](https://github.com/open-policy-agent/opa/pull/319))
- New /v0 API to support webhook integrations ([docs](http://www.openpolicyagent.org/documentation/references/rest-v0))

### Fixes

- Add support for namespaced built-ins ([#314](https://github.com/open-policy-agent/opa/issues/314))
- Improve logging to include request/response bodies ([#328](https://github.com/open-policy-agent/opa/pull/328))
- Add basic performance metrics ([#320](https://github.com/open-policy-agent/opa/pull/320))

### Miscellaneous

- Add built-ins to un/marshal JSON
- Add input form to diagnostic page

## 0.4.8

### Miscellaneous

- Fix top-level navigation links
- Improve file loader error handling

## 0.4.7

### Fixes

- Fix recursive binding by short-circuiting ref eval ([#298](https://github.com/open-policy-agent/opa/issues/298))
- Fix reordering for unsafe ref heads ([#297](https://github.com/open-policy-agent/opa/issues/297))
- Fix rewriting of single term exprs ([#299](https://github.com/open-policy-agent/opa/issues/299))

## 0.4.6

This release changes the `run` command options:

- Removed glog in favour of Sirupsen/logrus. This means the command line arguments to control logging have changed. See `run --help` for details.
- Removed `--policy-dir` option. For now, if policy persistence is required, users can treat policies as config files and manage them outside of OPA. Once OPA supports persistence of data (e.g., with file-based storage) then policy persistence will be added back in.

### Fixes

- Add support for additional HTTP listener ([#289](https://github.com/open-policy-agent/opa/issues/289))
- Allow slash in policy id/path ([#292](https://github.com/open-policy-agent/opa/issues/292))
- Improve request logging ([#281](https://github.com/open-policy-agent/opa/issues/281))

### Miscellaneous

- Add deployment documentation
- Remove erroneous flag.Parse() call
- Remove persist/--policy-dir option
- Replace glog with logrus

Also, updated Docker tagging so that latest points to most recent release (instead of most recent development build). The most recent development build can still be obtained with the {version}-dev tag.

## 0.4.5

### API security

This release adds support for TLS, token-based authentication, and authorization in the OPA APIs!

For details on how to secure the OPA API, go to http://openpolicyagent.org/documentation/references/security.

### Fixes

- Fix stray built-in error messages ([#275](https://github.com/open-policy-agent/opa/issues/275))
- Update error codes and messages throughout ([#237](https://github.com/open-policy-agent/opa/issues/237))
- [Fix evaluation bug with nested value refs](https://github.com/open-policy-agent/opa/pull/276/commits/e3336cce130eedda08f224ce4f28e19212447dcb)
- [Fix rego.Eval to close transactions](https://github.com/open-policy-agent/opa/pull/276/commits/745bd235127fae6bc22ff870bf62922c9358ccc0)
- [Fix buggy usage of errors.Cause](https://github.com/open-policy-agent/opa/pull/276/commits/bdf43b6a52de639e4f66810306311641ed7eea85)

### Miscellaneous

- Updated to support Go 1.8

## 0.4.4

### Fixes

- Fix issue in high-level Go API ([#261](https://github.com/open-policy-agent/opa/issues/261))

## 0.4.3

### Fixes

- Fix parsing of inline comments ([#258](https://github.com/open-policy-agent/opa/issues/258))
- Fix unset of input/data in REPL ([#259](https://github.com/open-policy-agent/opa/issues/259))
- Handle non-string/var values in rule tree lookup ([#257](https://github.com/open-policy-agent/opa/issues/257))

## 0.4.2

### Rego

This release changes the Rego syntax. The two main changes are:

- Expressions are now separated by semicolons (instead of commas). When writing rules, the semicolons are optional.
- Rules are no longer written in the form: `head :- body`. Instead they are written as `head { body }`.

Also:

- Set, array, and object literals now support trailing commas.
- To declare a set literal with one element, you must include a trailing comma, e.g., `{ foo, }`.
- Arithmetic and set operations can now be performed with infix notation, e.g., `x = 2 + 1`.
- Sets can be referred to like objects and arrays now ([#243](https://github.com/open-policy-agent/opa/issues/243)). E.g., `p[_].foo = 1 # check if element in has attr foo equal to 1`.

### Evaluation

This release changes the evaluation behaviour for packages. Previously, if a package contained no rules OR all of the rules were undefined when evaluated, a query against the package path would return undefined. As of v0.4.2 the query will return an empty object.

### REST API

This release changes the Data API to return an HTTP 200 response if the document is undefined. The message body will contain an object without the `result` property.

### Fixes

- Allow sets to be treated like objects/arrays

### Miscellaneous

- Added high level API for Go users. See `github.com/open-policy-agent/opa/rego` package.
- Improved expression String() function to handle infix operators better.
- Added support for set intersection and union built-ins. See language docs.

## 0.4.1

### Rego

For more details on these changes see sections in [How Do I Write Policies](http://www.openpolicyagent.org/documentation/how-do-i-write-policies/).

- Added new **default** keyword. The default keyword can be used to provide a default value for rules with complete definitions.
- Added new **with** keyword. The with keyword can be used to programmatically set the value of the input document inside policies.

### Fixes

- Fix input document definition in REPL ([#231](https://github.com/open-policy-agent/opa/issues/231))
- Fix reference evaluation bug ([#238](https://github.com/open-policy-agent/opa/issues/238))

### Miscellaneous

- Add basic REST API authorization benchmark

## 0.4.0

### REST API changes

This release contains a few non-backwards compatible changes to the REST API:

- The `request` document has been renamed to `input`. If you were calling the
  GET /data[/path]?request=value you should update to use [POST
  requests](http://www.openpolicyagent.org/documentation/references/rest#get-a-document-with-input)
  (see below).

- The API responses have been updated to return results embedded inside a
  wrapper object: `{"result": value}`. This will allow OPA to return unambiguous
  metadata in future (e.g., pagination, analysis, etc.) If you were previously
  consuming Data API GET responses, you should update your code to access the
  value under the `"result"` key of the response object.

- The API models have been updated to use snake_case
  ([#222](https://github.com/open-policy-agent/opa/issues/222)). This would only
  affect you if you were previously consuming error responses or policy ASTs.

The Data API has been updated to support the [POST
requests](http://www.openpolicyagent.org/documentation/references/rest#get-a-document-with-input).
This is the recommended way of supplying query inputs.

### Built-in Function changes

The built-in framework has been extended to support simplified built-in
implementations:

- Refactor topdown built-in functions
  ([#205](https://github.com/open-policy-agent/opa/issues/205))

### Fixes

- Add cURL note to REST API docs ([#211](https://github.com/open-policy-agent/opa/issues/211))
- Fix empty request parameter parsing ([#212](https://github.com/open-policy-agent/opa/issues/212))
- Fix handling of missing input document ([#227](https://github.com/open-policy-agent/opa/issues/227))
- Improve floating point literal support ([#215](https://github.com/open-policy-agent/opa/issues/215))
- Improve module parsing errors ([#213](https://github.com/open-policy-agent/opa/issues/213))
- Fix ast.Number hash and equality
- Fix parsing of escaped strings

### Miscellaneous

- Improve evaluation error messages

## 0.3.1

### Fixes

- Fixed unsafe vars with built-in operator names bug ([#206](https://github.com/open-policy-agent/opa/issues/206))
- Fixed body to rule conversion bug ([#202](https://github.com/open-policy-agent/opa/issues/202))
- Improved request parameter handling ([#201](https://github.com/open-policy-agent/opa/issues/201))

### Miscellaneous

- Improved release infrastructure

## 0.3.0

The last major/minor release of 2016! Woohoo! This release contains a few
non-backwards compatible changes to the APIs.

### Storage API changes

These changes simplify and clean up the storage.Store interface. This should
make it easier to implement custom stores in the future.

- Update storage to support context.Context ([#155](https://github.com/open-policy-agent/opa/issues/155))
- Update underlying number representation ([#154](https://github.com/open-policy-agent/opa/issues/154))
- Updates to use new storage.Path type ([#159](https://github.com/open-policy-agent/opa/issues/159))

### The request Document

These changes update the language to align query arguments with state stored in
OPA. With these changes, OPA can readily analyze policies and determine
references that refer to state stored in OPA versus query arguments versus local
variables.

These changes also update how query arguments are provided via the REST API.

- Updates to how query arguments are handled [#197](https://github.com/open-policy-agent/opa/pull/197)

### topdown API changes

- topdown.Context has been renamed to topdown.Topdown to avoid confusion with Golang's context.

### Fixes

- Add help topics to REPL ([#172](https://github.com/open-policy-agent/opa/issues/172))
- Fix error handling bug in Query API ([#183](https://github.com/open-policy-agent/opa/issues/183))
- Fix handling of prefixed paths with -w flag ([#193](https://github.com/open-policy-agent/opa/issues/193))
- Improve exit handling in REPL ([#175](https://github.com/open-policy-agent/opa/issues/175))
- Update parser support for <var> = <term> rules ([#192](https://github.com/open-policy-agent/opa/issues/192))

### Miscellaneous

- Add Visual Studio and Atom plugins
- Add lazy loading of modules during compilation
- Fix bug in serialization of empty objects/arrays

## 0.2.2

### Fixes

- Add YAML loading and refactor into separate file ([#135](https://github.com/open-policy-agent/opa/issues/135))
- Add command line flag to eval, print, and exit ([#152](https://github.com/open-policy-agent/opa/issues/152))
- Add compiler check for consistent rule types ([#147](https://github.com/open-policy-agent/opa/issues/147))
- Add set_diff built-in ([#133](https://github.com/open-policy-agent/opa/issues/133))
- Add simple 'show' command to print current module ([#108](https://github.com/open-policy-agent/opa/issues/108))
- Added examples to 'help' output in REPL ([#151](https://github.com/open-policy-agent/opa/issues/151))
- Check package declarations for conflicts ([#137](https://github.com/open-policy-agent/opa/issues/137))
- Deep copy modules in compiler ([#158](https://github.com/open-policy-agent/opa/issues/158))
- Fix evaluation of refs to set literals ([#149](https://github.com/open-policy-agent/opa/issues/149))
- Fix indexing usage for refs with intersecting vars ([#153](https://github.com/open-policy-agent/opa/issues/153))
- Fix output for references iterating sets ([#148](https://github.com/open-policy-agent/opa/issues/148))
- Fix parser handling of keywords in variable names ([#178](https://github.com/open-policy-agent/opa/issues/178))
- Improve file loading support ([#163](https://github.com/open-policy-agent/opa/issues/163))
- Remove conflict error for same key/value pairs ([#165](https://github.com/open-policy-agent/opa/issues/165))
- Support "data" query in REPL ([#150](https://github.com/open-policy-agent/opa/issues/150))

### Miscellaneous

- Add new compiler harness for ad-hoc queries
- Add tab completion of imports

## 0.2.1

### Improvements

- Added support for non-ground global values
- Added several new string manipulation built-ins
- Added TextMate grammar file
- Setup Docker image build and push to Docker Hub as part of CI

## 0.2.0

### Language

- Set literals
- Composite and reference values in Rule head
- Complete Rule definitions containing variables
- Builtins for regular expressions, string concatenation, casting to numbers

### Compiler

- Improved error reporting in parser and compiler

### Evaluation

- Iteration over base and virtual documents (in the same reference)
- Query tracing and explanation support

### Storage

- Pluggable data storage support

### Documentation

- GoDoc strings with examples
- REST API specification
- Concise language reference

### Performance

- Per-query cache of virtual documents in topdown

And many other small improvements and fixes.

## 0.1.0

### Language

- Basic value types: null, boolean, number, string, object, and array
- Reference and variables types
- Array comprehensions
- Built-in functions for basic arithmetic and aggregation
- Incremental and complete rule definitions
- Negation and disjunction
- Module system

### Compiler

- Reference resolver to support packages
- Safety check to prevent recursive rules
- Safety checks to ensure successful evaluation will bind all variables in head
  and body of rules

### Evaluation

- Initial top down query evaluation algorithm

### Storage

- Basic in-memory storage that exposes JSON Patch style API

### Tooling

- REPL that can be run to experiment with ad-hoc queries

### APIs

- Server mode supports HTTP APIs to manage policies, push and query documents, and execute ad-hoc queries.

### Infrastructure

- Basic build infrastructure to produce cross-platform builds, run
  style/lint/format checks, execute tests, static HTML site

### Documentation

- Introductions to policy, policy-enabling, and how OPA works
- Language reference that serves as guide for new users
- Tutorial that introduces users to the REPL
- Tutorial that introduces users to policy-enabling with a Docker Authorization plugin
