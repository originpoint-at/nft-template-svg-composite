# SVG Composite template for CandyMint

[CandyMint][1] is a platform for creating and minting NFTs. This repository contains the svg-composite template to help creators building their own assets repository.

## Usage

1. Click `Use this template` to create your own repository
1. Put images in the `image` directory
1. Update the `layouts.yaml` file
1. Connect your repository with your collection created in the CandyMint platform

## Template Structure

```text
image
├── graphic                  # suite
│   ├── 01_circie            # layer, should be sequential
│   │   ├── circle_01.svg    # item, should be sequential
│   │   ├── circle_02.svg
│   ├── other layers...
├── other suites...
README.md
layouts.yaml
```

- `image/<suite>/<layer>/<item>.svg` is the core structure of the SVG Composite template:
- `README.md` is the README file of the repository.
- `layouts.yaml` is the configuration file of the NFT items, see [Anatomy](#anatomy) for more details.

## Anatomy

```yaml
template: svg_composite       # template name, DO NOT change
engine: 0.1.0                 # engine version, DO NOT change
config:
  mime: image/svg+xml         # image mime type
  size:
    width: 512                # image width
    height: 512               # image height
    # ...                     # other properties used internally, DO NOT change
suites:
  - name: graphic             # suite name, should be unique and same as the directory name
    layers:
      - name: 01_circle       # layer name, should be unique and same as the directory name
        items:
          - value: circle_01       # trait value of the item, will include in the NFT metadata
            image: circle_01.svg   # file name of the item
            trait_type: circle     # trait type, can be arbitrary string, will include in the NFT metadata
            display_type: string   # display type of the trait, can be string or number, etc.
          - value: circle_02
            image: circle_02.svg
            trait_type: circle
            display_type: string
          # other items...
      # other layers...
  # other suites...
```

**Caveats:**

- The `image` directory **MUST** contain only images.
- The `layouts.yaml` file **MUST** be valid YAML.
- **Image Size**: This template is designed for on-chain storage by default, taking into account Gas fees, currently, it supports image sizes up to **50KB**.
- **Layer Composite**: This template generates the final NFT image by merging layers. In the layouts file, the first layer in the suite is at the bottom, and the last layer is at the top. Please organize the layers appropriately.
- In order to build a solid collection, the layers and their items **MUST** be sequential.
- **Preserving order in `layouts.yaml`**: CandyMint allows managing multiple collection versions. When adding new images and updating the `layouts.yaml`, it's crucial to append new elements at the end. **DO NOT** rearrange the existing order of backgrounds, layers, or items. This ensure all versions function correctly.

## TODO

- [ ] Add a license

## Other Templates

- [Default Template](https://github.com/originpoint-at/nft-template-default)
- [SVG Composite Template](https://github.com/originpoint-at/nft-template-svg-composite)
- [PNG Composite Template](https://github.com/originpoint-at/nft-template-png-composite)

## Relative Links

- [CandyMint][1]
- [CandyMint Testnet][2]
- [CandyMint Docs][3]
- [PNG Composite Tool][5]
- [Discord][4]
- Twitter
- Telegram

[1]: https://candymint.io
[2]: https://testnet.candymint.io
[3]: https://docs.candymint.io
[4]: https://discord.gg/DyP5Vxw5VB
[5]: https://candymint.io/tools/png-composite-tool
