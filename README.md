<br />

<a href="https://liblava.dev">
    <img align="left" src="docs/assets/liblava_200px.png" width="110">
</a>

<br />

<a href="https://liblava.dev"><img src="docs/assets/liblava.svg"></a>

**A modern and easy-to-use library for the Vulkan® API**

<br />

[![version](https://img.shields.io/badge/2024_rolling-0.8.1-cf1020)](https://github.com/liblava/liblava/tags) [![License](https://img.shields.io/github/license/liblava/liblava)](#license) [![CodeFactor](https://img.shields.io/codefactor/grade/github/liblava/liblava)](https://www.codefactor.io/repository/github/liblava/liblava) &nbsp; [![Discord](https://img.shields.io/discord/439508141722435595)](https://discord.liblava.dev) [![Donate](https://img.shields.io/badge/donate-PayPal-3b7bbf.svg)](https://donate.liblava.dev) [![Twitter Follow](https://img.shields.io/badge/follow-@liblava-00acee)](https://twitter.com/liblava)

<br />

**lava**  provides **essentials** for **low-level graphics** - suited for **prototyping**, **tooling**, **profiling** and **education**. 

> **This lean framework** is written in **neat C++23** and it strives for a **modular rolling release** as far as possible. We *don't* want to promise too much... but **lava runs** really smoothly **on Windows** and **Linux**.

<br />

➜ &nbsp; [Download](https://github.com/liblava/liblava/releases) &nbsp; • &nbsp; [Documentation](https://docs.liblava.dev) (Tutorial + Guide) &nbsp; • &nbsp; [Projects](#projects) &nbsp; • &nbsp; [Modules](#modules) &nbsp; • &nbsp; [Collaborate](#collaborate)

<br />

# In a nutshell

<a href="https://vulkan.org/">
    <img align="right" src="docs/assets/Vulkan_RGB_Dec16.svg" width="270">
</a>

* **liblava** is written in **modern C++** with latest **Vulkan support**
* Provides **run loop** abstraction for **window** and **input handling**
* Plain **renderer** and  **command buffer model**
* Batteries included ➜ runtime **shader compilation**
* **Texture** and **mesh** loading from **virtual file system**
* **Camera**, **imgui**, **logger** and much more...

<br />

[![engine](https://img.shields.io/badge/lava-engine-brightgreen.svg)](#lava-engine) [![app](https://img.shields.io/badge/lava-app-brightgreen.svg)](#lava-app) [![frame](https://img.shields.io/badge/lava-frame-brightgreen.svg)](#lava-frame) &nbsp; [![block](https://img.shields.io/badge/lava-block-red.svg)](#lava-block) [![asset](https://img.shields.io/badge/lava-asset-red.svg)](#lava-asset) [![resource](https://img.shields.io/badge/lava-resource-red.svg)](#lava-resource) [![base](https://img.shields.io/badge/lava-base-red.svg)](#lava-base) &nbsp; [![file](https://img.shields.io/badge/lava-file-blue.svg)](#lava-file) [![util](https://img.shields.io/badge/lava-util-blue.svg)](#lava-util) [![core](https://img.shields.io/badge/lava-core-blue.svg)](#lava-core)

<br />

# Take a look

```c++
#include "liblava/lava.hpp"
#include "imgui.h"

int main(int argc, char* argv[]) {

    lava::engine app("imgui demo", { argc, argv });
    if (!app.setup())
        return lava::error::not_ready;

    app.imgui.layers.add("demo window", []() {
        ImGui::ShowDemoWindow();
    });

    return app.run();
}
```

<br />

# Demos

|||
|:-|:-|
| ![demo](res/demo/screenshot.png) | [![lava demo](https://img.shields.io/badge/lava-demo-brightgreen.svg)](liblava-demo/main.cpp)<br />**free download on ➜ [itch.io](https://demo.liblava.dev)**<br /><br /> The collection includes all stages to play around. - *You can easily switch between them.* |
|||

## Stages

|||
|:-|:-|
| ![light](res/light/screenshot.png) | [![spawn](https://img.shields.io/badge/lava-light-brightgreen.svg)](liblava-demo/light.cpp)<br />**deferred shading + offscreen rendering**<br /><br />Small demo that showcases how to render to an offscreen framebuffer and sample from it. - *It is a challenge in itself and also a compact solution.* |
| ![spawn](res/spawn/screenshot.png) | [![light](https://img.shields.io/badge/lava-spawn-brightgreen.svg)](liblava-demo/spawn.cpp)<br />**uniform buffer + camera**<br /><br />This loads a very large mesh from file and simply textures it. - *Use your gamepad to control the camera if there is one around.* |
| ![lamp](res/lamp/screenshot.png) | [![lamp](https://img.shields.io/badge/lava-lamp-brightgreen.svg)](liblava-demo/lamp.cpp)<br />**push constants to shader**<br /><br />Classic lamp to relax and where colors can be easily switched. - *Unfortunately it also consumes power - so be aware!* |
| ![shapes](res/shapes/screenshot.png) | [![shapes](https://img.shields.io/badge/lava-shapes-brightgreen.svg)](liblava-demo/shapes.cpp)<br />**generating primitives**<br /><br />Switch between basic shapes and use the camera to fly around. - *A great start for your next interactive application.* |
| ![generics](res/generics/screenshot.png) | [![generics](https://img.shields.io/badge/lava-generics-brightgreen.svg)](liblava-demo/generics.cpp)<br />**float, double & int meshes**<br /><br />This demo shows how to check GPU features and render mesh data with custom vertex layout. - *There is a chapter about it in the Guide.* |
| ![triangle](res/triangle/screenshot.png) | [![triangle](https://img.shields.io/badge/lava-triangle-brightgreen.svg)](liblava-demo/triangle.cpp)<br />**unique classic mesh**<br /><br />Where graphics programming always begins. - *An example that illustrates how little it actually takes to render a triangle.* |
|||

<br />

# Projects

|||
|:-|:-|
| <img src="https://raw.githubusercontent.com/pezcode/lava-rt/main/demo/res/cubes/screenshot.png"> | [![rt cubes](https://img.shields.io/badge/lava-rt_cubes-brightgreen.svg)](https://github.com/pezcode/lava-rt)<br /> **raytraced reflecting cubes**<br /><br />*Vulkan raytracing with liblava*<br />Support for the Vulkan KHR ray tracing extensions with idiomatic wrappers. ➜ [pezcode](https://github.com/pezcode) |
| | *Do you have a project? Submit it with a [pull request](#collaborate)* |
|||

<br />

# Modules

## lava [engine](liblava/engine) 

[![engine](https://img.shields.io/badge/lava-engine-brightgreen.svg)](liblava/engine/engine.hpp) [![producer](https://img.shields.io/badge/lava-producer-brightgreen.svg)](liblava/engine/producer.hpp) [![props](https://img.shields.io/badge/lava-props-brightgreen.svg)](liblava/engine/props.hpp)

&nbsp; ➜ &nbsp; *depends on [app](#lava-app)*

## lava [app](liblava/app)

[![app](https://img.shields.io/badge/lava-app-brightgreen.svg)](liblava/app/app.hpp) [![camera](https://img.shields.io/badge/lava-camera-brightgreen.svg)](liblava/app/camera.hpp) [![forward_shading](https://img.shields.io/badge/lava-forward_shading-brightgreen.svg)](liblava/app/forward_shading.hpp)

[![benchmark](https://img.shields.io/badge/lava-benchmark-brightgreen.svg)](liblava/app/benchmark.hpp) [![config](https://img.shields.io/badge/lava-config-brightgreen.svg)](liblava/app/config.hpp) [![imgui](https://img.shields.io/badge/lava-imgui-brightgreen.svg)](liblava/app/imgui.hpp)

&nbsp; ➜ &nbsp; *depends on [frame](#lava-frame) + [block](#lava-block) + [asset](#lava-asset)*

## lava [frame](liblava/frame)

[![argh](https://img.shields.io/badge/lava-argh-brightgreen.svg)](liblava/frame/argh.hpp) [![driver](https://img.shields.io/badge/lava-driver-brightgreen.svg)](liblava/frame/driver.hpp) [![frame](https://img.shields.io/badge/lava-frame-brightgreen.svg)](liblava/frame/frame.hpp) [![gamepad](https://img.shields.io/badge/lava-gamepad-brightgreen.svg)](liblava/frame/gamepad.hpp) [![input](https://img.shields.io/badge/lava-input-brightgreen.svg)](liblava/frame/input.hpp)

[![render_target](https://img.shields.io/badge/lava-render_target-brightgreen.svg)](liblava/frame/render_target.hpp) [![renderer](https://img.shields.io/badge/lava-renderer-brightgreen.svg)](liblava/frame/renderer.hpp) [![swapchain](https://img.shields.io/badge/lava-swapchain-brightgreen.svg)](liblava/frame/swapchain.hpp) [![window](https://img.shields.io/badge/lava-window-brightgreen.svg)](liblava/frame/window.hpp)

&nbsp; ➜ &nbsp; *depends on [resource](#lava-resource)*

<br />

## lava [block](liblava/block)

[![attachment](https://img.shields.io/badge/lava-attachment-red.svg)](liblava/block/attachment.hpp) [![block](https://img.shields.io/badge/lava-block-red.svg)](liblava/block/block.hpp) [![descriptor](https://img.shields.io/badge/lava-descriptor-red.svg)](liblava/block/descriptor.hpp) [![render_pass](https://img.shields.io/badge/lava-render_pass-red.svg)](liblava/block/render_pass.hpp) [![subpass](https://img.shields.io/badge/lava-subpass-red.svg)](liblava/block/subpass.hpp)

[![compute_pipeline](https://img.shields.io/badge/lava-compute_pipeline-red.svg)](liblava/block/compute_pipeline.hpp) [![render_pipeline](https://img.shields.io/badge/lava-render_pipeline-red.svg)](liblava/block/render_pipeline.hpp) [![pipeline](https://img.shields.io/badge/lava-pipeline-red.svg)](liblava/block/pipeline.hpp) [![pipeline_layout](https://img.shields.io/badge/lava-pipeline_layout-red.svg)](liblava/block/pipeline_layout.hpp)

&nbsp; ➜ &nbsp; *depends on [base](#lava-base)*

## lava [asset](liblava/asset)

[![load_image](https://img.shields.io/badge/lava-load_image-red.svg)](liblava/asset/load_image.hpp) [![load_mesh](https://img.shields.io/badge/lava-load_mesh-red.svg)](liblava/asset/load_mesh.hpp) [![load_texture](https://img.shields.io/badge/lava-load_texture-red.svg)](liblava/asset/load_texture.hpp) [![write_image](https://img.shields.io/badge/lava-write_image-red.svg)](liblava/asset/write_image.hpp)

&nbsp; ➜ &nbsp; *depends on [resource](#lava-resource) + [file](#lava-file)*

## lava [resource](liblava/resource)

[![buffer](https://img.shields.io/badge/lava-buffer-red.svg)](liblava/resource/buffer.hpp) [![mesh](https://img.shields.io/badge/lava-mesh-red.svg)](liblava/resource/mesh.hpp) [![primitive](https://img.shields.io/badge/lava-primitive-red.svg)](liblava/resource/primitive.hpp)

[![format](https://img.shields.io/badge/lava-format-red.svg)](liblava/resource/format.hpp) [![image](https://img.shields.io/badge/lava-image-red.svg)](liblava/resource/image.hpp) [![texture](https://img.shields.io/badge/lava-texture-red.svg)](liblava/resource/texture.hpp)

&nbsp; ➜ &nbsp; *depends on [base](#lava-base)*

## lava [base](liblava/base)

[![base](https://img.shields.io/badge/lava-base-red.svg)](liblava/base/base.hpp) [![instance](https://img.shields.io/badge/lava-instance-red.svg)](liblava/base/instance.hpp) [![memory](https://img.shields.io/badge/lava-memory-red.svg)](liblava/base/memory.hpp) [![queue](https://img.shields.io/badge/lava-queue-red.svg)](liblava/base/queue.hpp)

[![platform](https://img.shields.io/badge/lava-platform-red.svg)](liblava/base/platform.hpp) [![device](https://img.shields.io/badge/lava-device-red.svg)](liblava/base/device.hpp) [![physical_device](https://img.shields.io/badge/lava-physical_device-red.svg)](liblava/base/physical_device.hpp)

&nbsp; ➜ &nbsp; *depends on [util](#lava-util)*

<br />

## lava [file](liblava/file)

[![file](https://img.shields.io/badge/lava-file-blue.svg)](liblava/file/file.hpp) [![file_system](https://img.shields.io/badge/lava-file_system-blue.svg)](liblava/file/file_system.hpp) [![file_utils](https://img.shields.io/badge/lava-file_utils-blue.svg)](liblava/file/file_utils.hpp) [![json_file](https://img.shields.io/badge/lava-json_file-blue.svg)](liblava/file/json_file.hpp) [![json](https://img.shields.io/badge/lava-json-blue.svg)](liblava/file/json.hpp)

&nbsp; ➜ &nbsp; *depends on [core](#lava-core)*

## lava [util](liblava/util)

[![log](https://img.shields.io/badge/lava-log-blue.svg)](liblava/util/log.hpp) [![math](https://img.shields.io/badge/lava-math-blue.svg)](liblava/util/math.hpp) [![random](https://img.shields.io/badge/lava-random-blue.svg)](liblava/util/random.hpp) [![thread](https://img.shields.io/badge/lava-thread-blue.svg)](liblava/util/thread.hpp)

[![hex](https://img.shields.io/badge/lava-hex-blue.svg)](liblava/util/hex.hpp) [![layer](https://img.shields.io/badge/lava-layer-blue.svg)](liblava/util/layer.hpp) [![telegram](https://img.shields.io/badge/lava-telegram-blue.svg)](liblava/util/telegram.hpp)

&nbsp; ➜ &nbsp; *depends on [core](#lava-core)*

## lava [core](liblava/core)

[![data](https://img.shields.io/badge/lava-data-blue.svg)](liblava/core/data.hpp) [![id](https://img.shields.io/badge/lava-id-blue.svg)](liblava/core/id.hpp) [![misc](https://img.shields.io/badge/lava-misc-blue.svg)](liblava/core/misc.hpp) [![time](https://img.shields.io/badge/lava-time-blue.svg)](liblava/core/time.hpp) [![types](https://img.shields.io/badge/lava-types-blue.svg)](liblava/core/types.hpp) [![version](https://img.shields.io/badge/lava-version-blue.svg)](liblava/core/version.hpp)

<br />

# Collaborate

Use the [issue tracker](https://github.com/liblava/liblava/issues) to report any bug or compatibility issue.

:heart: &nbsp; Thanks to all [contributors](https://github.com/liblava/liblava/graphs/contributors) making **liblava** flow...

<br />
<br />

If you want to **contribute** - we suggest the following:

1. Fork the [official repository](https://github.com/liblava/liblava/fork)
2. Apply your changes to **your fork**
3. Submit a [pull request](https://github.com/liblava/liblava/pulls) describing the changes you have made

<br />

## Support

<br />

**Need help?** &nbsp; Please feel free to ask us on ➜ [Discord](https://discord.liblava.dev)

<br />

| Help maintenance and development | Every star and follow motivates |
|---------:|:---------|
| [![paypal](https://www.paypalobjects.com/en_US/i/btn//btn_donate_SM.gif)](https://donate.liblava.dev) | [![GitHub Stars](https://img.shields.io/github/stars/liblava/liblava?style=social)](https://github.com/liblava/liblava/stargazers) &nbsp; [![Twitter URL](https://img.shields.io/twitter/follow/liblava?style=social)](https://twitter.com/liblava) |

<br />

# License

**liblava** is licensed under [MIT License](LICENSE) which allows you to use the software for any purpose you might like - including commercial and for-profit use. However - this library includes several [Third-Party](docs/README.md#Third-Party) libraries which are licensed under their own respective [Open Source](https://opensource.org) licenses ➜ They all allow **static linking** with closed source software.

> **All copies of liblava must include a copy of the MIT License terms and the copyright notice.**

<br />

**Vulkan** and the Vulkan logo are trademarks of the <a href="http://www.khronos.org" target="_blank">Khronos Group Inc.</a>

Copyright (c) 2018-present - <a href="https://lava-block.com">Lava Block OÜ</a> and [contributors](https://github.com/liblava/liblava/graphs/contributors)

<br />
<br />

<a href="https://liblava.dev"><img src="docs/assets/liblava_200px.png" width="50"></a>
