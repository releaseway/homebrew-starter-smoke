# Homebrew starter acceptance tap

Permanent non-production target for testing taps created from
[homebrew-tap-starter](https://github.com/releaseway/homebrew-tap-starter).
Use the starter to create a product tap. Production packages and end users should
not depend on this repository.

The [release fixture](https://github.com/releaseway/release-fixture) owns the
product source, specs and acceptance orchestration. This repository owns the
generated Formula state and inherited tap validation/deletion workflows.

## Run starter acceptance

Follow the fixture's
[Homebrew acceptance guide](https://github.com/releaseway/release-fixture#homebrew-acceptance).
Use its immutable fixture tag and matching automation candidate, with:

- `tap-repository: releaseway/homebrew-starter-smoke`;
- `tap-secret: STARTER_TAP_DEPLOY_KEY`.

The dedicated deploy key is stored in the release fixture and must have write
access to this tap. The workflow only accepts the allowlisted tap/credential pair.
Acceptance updates this test tap's source and prebuilt Formulae, then verifies the
public workflow outputs and resulting state.

## Validate or maintain the tap

Run **Actions → test → Run workflow** for shared Formula syntax and audit checks.
The [test workflow](.github/workflows/test.yml) is the source of truth for its
full-SHA homebrew-actions dependency.

Run **Actions → delete formula** with a Formula name and `dry-run` to preview
deletion. A normal run pushes to the default branch with the tap's workflow token;
a missing Formula fails. Deleting a Formula does not uninstall existing copies.

Dependabot proposes updates to the inherited workflows. Changes to the starter
are not automatically copied into this repository. For product setup and write
credentials in a new tap, use the
[starter guide](https://github.com/releaseway/homebrew-tap-starter#connect-a-product).

## License

MIT. Package licenses are declared independently in their product Formula specs.
