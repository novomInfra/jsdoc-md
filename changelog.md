# jsdoc-md changelog

## 5.0.1

### Patch

- Updated dependencies.
- Use [`snapshot-assertion`](https://npm.im/snapshot-assertion) for snapshot assertions in tests.

## 5.0.0

### Major

- Support Node.js v10+, from v8+.
- Updated the [`globby`](https://npm.im/globby) dependency to v10, which may affect how the `jsdoc-md` command `--source-glob` argument and `jsdocMd` function `sourceGlob` option work.
- Replaced the [`yargs`](https://npm.im/yargs) dependency with [`arg`](https://npm.im/arg), for a smaller install size. This affects the `jsdoc-md` command:
  - The `--help`/`-h` argument is gone.
  - The `--version`/`-v` argument is gone.
  - Short arguments can’t be used with `=` (e.g. `jsdoc-md -m readme.md` works, `jsdoc-md -m=readme.md` doesn’t), see [zeit/arg#51](https://github.com/zeit/arg/issues/51).
  - Behavior using quotes around argument values may have changed.

### Minor

- Added a new `cwd` option for the `jsdocMd` function.
- Setup [GitHub Sponsors funding](https://github.com/sponsors/jaydenseric):
  - Added `.github/funding.yml` to display a sponsor button in GitHub.
  - Added a `package.json` `funding` field to enable npm CLI funding features.

### Patch

- Updated dependencies.
- Removed the now redundant [`eslint-plugin-import-order-alphabetical`](https://npm.im/eslint-plugin-import-order-alphabetical) dev dependency.
- Stop using [`husky`](https://npm.im/husky) and [`lint-staged`](https://npm.im/lint-staged).
- Replaced the [`tap`](https://npm.im/tap) dev dependency with [`test-director`](https://npm.im/test-director) and [`coverage-node`](https://npm.im/coverage-node), refactoring the tests accordingly. This vastly reduces the dev install size.
- Replaced the deprecated [`circular-json`](https://npm.im/circular-json) dev dependency with [`flatted`](https://npm.im/flatted).
- Added a new [`disposable-directory`](https://npm.im/disposable-directory) dev dependency, using it to replace the `createTestFile` helper and improve tests.
- Added a new [`hard-rejection`](https://npm.im/hard-rejection) dev dependency to ensure unhandled rejections in tests exit the process with an error.
- Test the CLI.
- Use strict mode for scripts.
- Use less arrow functions for better stack traces.
- Replaced every `forEach` loop with `for` `of`.
- More consistent module exports style.
- Removed `package-lock.json` from `.gitignore` and `.prettierignore` as it’s disabled in `.npmrc` anyway.
- Added a package `main` field and moved the index and bin files.
- Use GitHub Actions instead of Travis for CI.
- Simplified the readme “Setup” section.
- Improved CLI docs with examples.
- Documented how files are excluded via `.gitignore`.

## 4.0.1

### Patch

- Display quotes around string literal types that are empty or only contain whitespace, to avoid resulting empty inline code and markdown rendering issues.

## 4.0.0

### Major

- `@param` and `@prop` default values are now parsed as JSDoc types; an invalid type will result in an error.

### Minor

- Richer markdown for `@param` and `@prop` default values:
  - `null`, `undefined`, `void`, number, string, and boolean literal values display as inline code.
  - JSDoc member name references display as links.

### Patch

- Updated dependencies.
- Renamed `test:js` package script to `test:tap`.

## 3.1.0

### Minor

- Exclude “See” and “Examples” headings from generated table of contents.

### Patch

- Updated dependencies.
- Simplified the `prepublishOnly` script.

## 3.0.0

### Major

- Support Node.js v8+, from v6+.

### Minor

- Support the nullable literal type (`?`).
- Support the void literal type (`function(): void`).
- Automatically adjust heading levels in descriptions and examples to suit the surrounding document.

### Patch

- Updated dependencies.
- Reduced the published size of `package.json` by moving dev tool configs to separate files.
- Removed `.html` from [usejsdoc.org](http://usejsdoc.org) links.
- Removed the test file glob from the `test:js` script args as [`tap`](https://npm.im/tap) now finds the files automatically.
- Refactored `typeJsdocAstToMdAst`.
- Test `typeJsdocAstToMdAst` with an unknown type, and more clearly test every possible type.
- Test `outlineMembers` with missing members.
- Test `membersToMdAst` with a parameter default value.

## 2.1.0

### Minor

- Render any combination of supported tags, even if they are illogical (e.g. `@param` with `@prop`). This fixes `@kind constant` not rendering an associated `@type`.
- `@kind typedef` without an associated `@type` no longer causes an error. Linting would be a better way to ensure the right combination of tags are used.

### Patch

- Updated dev dependencies.

## 2.0.1

### Patch

- Fix `<hr />` incorrectly appearing above non top level members.

## 2.0.0

### Major

- `@kind member` now displays an associated `@type` and throws an error if there is none.

### Minor

- Separate top level member sections with `<hr />`.

### Patch

- Updated dev dependencies.
- Use default [`tap`](https://npm.im/tap) reporter for tests.
- Simplify package `test:js` script glob.

## 1.7.1

### Patch

- Updated dependencies.
- Allow Babel to load config relative to files being parsed.
- Stopped automatically linking global types to MDN.
- Simplified ESLint config.

## 1.7.0

### Minor

- Added MDN links for [`Uint8Array`](https://mdn.io/uint8array) types and updated snapshot tests, fixing [#11](https://github.com/jaydenseric/jsdoc-md/issues/9) via [#12](https://github.com/jaydenseric/jsdoc-md/pull/12).

### Patch

- Updated dependencies.
- Updated package scripts and config for the new [`husky`](https://npm.im/husky) version.
- Added a missing test for the `Promise` type MDN link.

## 1.6.0

### Minor

- Support Node.js v6+, from v8.5+.

### Patch

- Work around a Babel breaking change to parsing decorators, see [babel/babel#8562](https://github.com/babel/babel/issues/8562).

## 1.5.0

### Minor

- Use [mdn.io](https://github.com/lazd/mdn.io) for shorter [MDN](https://developer.mozilla.org) links in generated markdown.
- `Promise` types now link to their MDN docs.

### Patch

- Updated dependencies.
- Removed the [`npm-run-all`](https://npm.im/npm-run-all) dev dependency and stopped using it for package scripts.
- Swapped readme badge order.

## 1.4.0

### Minor

- Sort members in the documentation outline, fixes [#8](https://github.com/jaydenseric/jsdoc-md/issues/8).
- Explicitly left align table cell contents.
- Display parameter and property names as inline code.

### Patch

- Updated dependencies.
- Configured Prettier to lint `.yml` files.
- Ensure the readme Travis build status badge only tracks `master` branch.
- Use [Badgen](https://badgen.net) for the readme npm version badge.

## 1.3.0

### Minor

- Default documentation for global types (such as `Object`) can be overridden using `@typedef`.
- Also auto-link MDN articles for global types `function` and `Date`.

### Patch

- Varied capitalization of global types (such as `Object`) results in a consistently lowercase MDN link slug.

## 1.2.0

### Minor

- Generate function return documentation, fixes [#7](https://github.com/jaydenseric/jsdoc-md/issues/7).

## 1.1.0

### Minor

- Support [JSDoc inline tag links](http://usejsdoc.org/tags-inline-link) (e.g. `` [`b` method]{@link A#b} ``) for descriptions and tags with markdown content, closes [#5](https://github.com/jaydenseric/jsdoc-md/issues/5).

### Patch

- Correct slugs for successive type member links, fixes [#6](https://github.com/jaydenseric/jsdoc-md/issues/6).
- Display CLI options as code in the readme.
- Internally refactor `jsdocAstToMember` to `jsdocToMember`.

## 1.0.0

Initial release.
