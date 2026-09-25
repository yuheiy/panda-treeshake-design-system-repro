# Transitive design-system import reproduction

With Panda 2.0.0-beta.18, `treeshakeDesignSystem: true` omits a style imported through another package. The app imports `button` from `@repro/ds` and `CheckIcon` from `@repro/icons`. The icon package imports `icon` from `@repro/ds/Icon`. Panda scans only the app's `src` directory.

Run:

```sh
pnpm install
pnpm run reproduce
```

Compare `packages/app/true.css` and `packages/app/false.css`. With `treeshakeDesignSystem: true`, the CSS includes the directly imported button's `color: red` but omits the icon's `--icon-size: 20px`. With the option set to `false`, the CSS includes both declarations.
