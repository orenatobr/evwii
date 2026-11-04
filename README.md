# Enhanced vWii (evWii)

> **This is a fork.** The official repository is **[GaryOderNichts/evwii](https://github.com/GaryOderNichts/evwii)**. All credit for evWii goes to GaryOderNichts and its contributors; please report general bugs and ask general questions there.
>
> This fork is based on upstream `v0.4` (commit `978b006`) and adds:
> - **Finer TV viewport width presets:** 720, 712, 704, 696, 688, 680, 672, 656, 640.
> - **Finer TV viewport height presets (480p):** 480, 472, 464, 456, 448, 440, 432.
> - **Finer TV viewport height presets (576i):** 576, 560, 544, 528, 512, 496, 480.
>
> All presets are centered and the original preset values are unchanged, so existing configs keep working. For example, 688 wide by 456 high hides the black borders of injected Wii games on a 16:9 TV without editing the JSON.
>
> Test builds: [Releases](https://github.com/orenatobr/evwii/releases). They are not yet verified on hardware beyond compiling. Changes to this repository are merged only through pull requests approved by the owner. Licensed GPL-2.0, same as upstream.

This is a plugin for [Aroma](https://aroma.foryour.cafe) which tries to improve some of the Wii U's virtual Wii features.  
It works by patching features used for setting up the vWii mode while still in Wii U mode. This also includes [DMCU](https://wiiubrew.org/wiki/Hardware/DMCU) patches.  
Note that the plugin will not be active when booting vWii mode using the [Boot Selector](https://github.com/wiiu-env/AutobootModule).

## Features
- Allows enabling the 4 second power button press to force power off while in vWii mode.
- Allows setting custom viewport values in the DMCU firmware. This can undo the forced cropping of overscan in vWii mode. The TV viewport has fine, centered presets (width 720 to 640 and height 480/576i down to 432/480 in steps of 4 to 8 px), so the image can be zoomed just enough to hide the black borders without editing the JSON.
- Allows fully replacing the DMCU firmware using a file loaded from the SD Card (`wiiu/dmcu.d.hex`).

## Examples
**GamePad (viewport unchanged):**  
<img src="https://i.imgur.com/3GCQrD0.png" width=600px/>

**GamePad (viewport adjusted):**  
<img src="https://i.imgur.com/7jkR2BQ.png" width=600px/>

*Note:* These are not actual GamePad captures, but visualizations of what viewport adjustments do.

## Building
For building you need: 
- [wups](https://github.com/wiiu-env/WiiUPluginSystem)
- [wut](https://github.com/devkitPro/wut)
- [libmocha](https://github.com/wiiu-env/libmocha)

You can also build evWii using Docker:
```
# Build docker image (only needed once)
docker build . -t evwii_builder

# make 
docker run -it --rm -v ${PWD}:/project evwii_builder make

# make clean
docker run -it --rm -v ${PWD}:/project evwii_builder make clean
```

## Special Thanks
- [@vaguerant](https://github.com/vaguerant/) and [@Ingunar](https://github.com/Ingunar) for all of the vWii testing they have done for this!
