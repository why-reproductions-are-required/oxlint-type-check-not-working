# oxlint type-check not working reproduce

oxlint type-check should work, but it doesn't.

## oxlint type-check not working

```bash
vp lint --type-aware --type-check

Found 0 warnings and 0 errors.
Finished in 194ms on 6 files with 107 rules using 16 threads.
```

## tsc working

```bash
vpx tsc --noEmit

apps/website/src/main.ts:2:28 - error TS2307: Cannot find module './assets/typescript.svg' or its corresponding type declarations.

2 import typescriptLogo from "./assets/typescript.svg";
                             ~~~~~~~~~~~~~~~~~~~~~~~~~

apps/website/src/main.ts:3:22 - error TS2307: Cannot find module './assets/vite.svg' or its corresponding type declarations.

3 import viteLogo from "./assets/vite.svg";
```

## tsgo working

```bash
vpx tsgo --noEmit

apps/website/src/main.ts:3:22 - error TS2307: Cannot find module './assets/vite.svg' or its corresponding type declarations.

3 import viteLogo from "./assets/vite.svg";
                       ~~~~~~~~~~~~~~~~~~~

apps/website/src/main.ts:4:21 - error TS2307: Cannot find module './assets/hero.png' or its corresponding type declarations.

4 import heroImg from "./assets/hero.png";
                      ~~~~~~~~~~~~~~~~~~~

packages/utils/tests/index.test.ts:2:20 - error TS2834: Relative import paths need explicit file extensions in ECMAScript imports when '--moduleResolution' is 'node16' or 'nodenext'. Consider adding an extension to the import path.

2 import { fn } from "../src";
                     ~~~~~~~~
```
