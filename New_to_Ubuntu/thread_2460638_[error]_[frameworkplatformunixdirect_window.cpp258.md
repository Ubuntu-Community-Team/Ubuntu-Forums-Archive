---
title: "[error] [framework/platform/unix/direct_window.cpp:258] Direct-to-display: No display"
date: 2021-04-15
forum: New to Ubuntu
---

### Post by maketopsite on 2021-04-15
Can't run Vulkan samples [https://github.com/KhronosGroup/Vulkan-Samples](https://github.com/KhronosGroup/Vulkan-Samples)

```
./build/linux/app/bin/Release/x86_64/vulkan_samples --sample layout_transitions
[info] Logger initialized
[info] Window created
[info] Initializing Vulkan sample
[info] VK_KHR_get_physical_device_properties2 is available, enabling it
[info] Enabled Validation Layers:
INTEL-MESA: warning: Ivy Bridge Vulkan support is incomplete
[info] Found GPU: Intel(R) HD Graphics 4000 (IVB GT2)
[info] Found GPU: GeForce GTX 660M
[error] [framework/platform/unix/direct_window.cpp:258] Direct-to-display: No displays found
[info] Selected GPU: GeForce GTX 660M
[info] Dedicated Allocation enabled
[info] Device supports the following requested extensions:
[info]          VK_KHR_get_memory_requirements2
[info]          VK_KHR_dedicated_allocation
[info]          VK_KHR_swapchain
[info] Depth format selected: VK_FORMAT_D32_SFLOAT
[info] glTF file contains extension: KHR_lights_punctual
[warning] ASTC not supported: decoding background.ktx
[warning] ASTC not supported: decoding sponza_flagpole_diff.ktx
[warning] ASTC not supported: decoding lion.ktx
[warning] ASTC not supported: decoding sponza_thorn_diff.ktx
[info] Loaded gltf image #3 (sponza_thorn_diff.ktx)
[warning] ASTC not supported: decoding vase_plant.ktx
[info] Loaded gltf image #0 (sponza_flagpole_diff.ktx)
[warning] ASTC not supported: decoding spnza_bricks_a_diff.ktx
[info] Loaded gltf image #1 (lion.ktx)
[warning] ASTC not supported: decoding sponza_ceiling_a_diff.ktx
[info] Loaded gltf image #4 (vase_plant.ktx)
[warning] ASTC not supported: decoding sponza_column_a_diff.ktx
[info] Loaded gltf image #2 (background.ktx)
[warning] ASTC not supported: decoding sponza_arch_diff.ktx
[info] Loaded gltf image #8 (sponza_arch_diff.ktx)
[warning] ASTC not supported: decoding sponza_column_c_diff.ktx
[info] Loaded gltf image #5 (spnza_bricks_a_diff.ktx)
[warning] ASTC not supported: decoding sponza_details_diff.ktx
[info] Loaded gltf image #7 (sponza_column_a_diff.ktx)
[warning] ASTC not supported: decoding sponza_floor_a_diff.ktx
[info] Loaded gltf image #6 (sponza_ceiling_a_diff.ktx)
[warning] ASTC not supported: decoding sponza_column_b_diff.ktx
[info] Loaded gltf image #9 (sponza_column_c_diff.ktx)
[warning] ASTC not supported: decoding vase_dif.ktx
[info] Loaded gltf image #11 (sponza_floor_a_diff.ktx)
[warning] ASTC not supported: decoding spnza_bricks_a_diff.ktx
[info] Loaded gltf image #10 (sponza_details_diff.ktx)
[warning] ASTC not supported: decoding vase_hanging.ktx
[info] Loaded gltf image #12 (sponza_column_b_diff.ktx)
[warning] ASTC not supported: decoding vase_round.ktx
[info] Loaded gltf image #13 (vase_dif.ktx)
[info] Loaded gltf image #14 (spnza_bricks_a_diff.ktx)
[warning] ASTC not supported: decoding sponza_curtain_blue_diff.ktx
[warning] ASTC not supported: decoding chain_texture.ktx
[info] Loaded gltf image #15 (vase_hanging.ktx)
[warning] ASTC not supported: decoding sponza_curtain_diff.ktx
[info] Loaded gltf image #16 (vase_round.ktx)
[warning] ASTC not supported: decoding sponza_curtain_green_diff.ktx
[info] Loaded gltf image #17 (chain_texture.ktx)
[warning] ASTC not supported: decoding sponza_fabric_green_diff.ktx
[info] Loaded gltf image #21 (sponza_fabric_green_diff.ktx)
[warning] ASTC not supported: decoding sponza_fabric_blue_diff.ktx
[info] Loaded gltf image #22 (sponza_fabric_blue_diff.ktx)
[warning] ASTC not supported: decoding sponza_fabric_diff.ktx
[info] Loaded gltf image #23 (sponza_fabric_diff.ktx)
[warning] ASTC not supported: decoding sponza_roof_diff.ktx
[info] Loaded gltf image #18 (sponza_curtain_blue_diff.ktx)
[info] Loaded gltf image #20 (sponza_curtain_green_diff.ktx)
[info] Loaded gltf image #19 (sponza_curtain_diff.ktx)
[info] Loaded gltf image #24 (sponza_roof_diff.ktx)
[info] Time spent loading images: 1.293359 seconds across 4 threads.
HWCPipe [INFO] : Mali profiler initialization failed: Failed to get HW info.
[warning] Tiles killed by CRC match : not available
[warning] External Write Bytes : not available
[info] FPS: 0.5
[info] FPS: 397.0
[info] FPS: 419.3
[info] FPS: 416.5
[info] FPS: 419.0
[info] FPS: 422.8
[info] FPS: 424.3


```

```
__NV_PRIME_RENDER_OFFLOAD=1   ./build/linux/app/bin/Release/x86_64/vulkan_samples --sample layout_transitions
[info] Logger initialized
[info] Window created
[info] Initializing Vulkan sample
[info] VK_KHR_get_physical_device_properties2 is available, enabling it
[info] Enabled Validation Layers:
INTEL-MESA: warning: Ivy Bridge Vulkan support is incomplete
[info] Found GPU: Intel(R) HD Graphics 4000 (IVB GT2)
[info] Found GPU: GeForce GTX 660M
[error] [framework/platform/unix/direct_window.cpp:258] Direct-to-display: No displays found
[info] Selected GPU: GeForce GTX 660M
[info] Dedicated Allocation enabled
[info] Device supports the following requested extensions:
[info]          VK_KHR_get_memory_requirements2
[info]          VK_KHR_dedicated_allocation
[info]          VK_KHR_swapchain
[info] Depth format selected: VK_FORMAT_D32_SFLOAT
[info] glTF file contains extension: KHR_lights_punctual
[warning] ASTC not supported: decoding lion.ktx
[warning] ASTC not supported: decoding sponza_flagpole_diff.ktx
[warning] ASTC not supported: decoding sponza_thorn_diff.ktx
[warning] ASTC not supported: decoding background.ktx
[info] Loaded gltf image #3 (sponza_thorn_diff.ktx)
[warning] ASTC not supported: decoding vase_plant.ktx
[info] Loaded gltf image #1 (lion.ktx)
[warning] ASTC not supported: decoding spnza_bricks_a_diff.ktx
[info] Loaded gltf image #2 (background.ktx)
[warning] ASTC not supported: decoding sponza_ceiling_a_diff.ktx
[info] Loaded gltf image #0 (sponza_flagpole_diff.ktx)
[warning] ASTC not supported: decoding sponza_column_a_diff.ktx
[info] Loaded gltf image #4 (vase_plant.ktx)
[warning] ASTC not supported: decoding sponza_arch_diff.ktx
[info] Loaded gltf image #5 (spnza_bricks_a_diff.ktx)
[warning] ASTC not supported: decoding sponza_column_c_diff.ktx
[info] Loaded gltf image #6 (sponza_ceiling_a_diff.ktx)
[warning] ASTC not supported: decoding sponza_details_diff.ktx
[info] Loaded gltf image #7 (sponza_column_a_diff.ktx)
[warning] ASTC not supported: decoding sponza_floor_a_diff.ktx
[info] Loaded gltf image #8 (sponza_arch_diff.ktx)
[warning] ASTC not supported: decoding sponza_column_b_diff.ktx
[info] Loaded gltf image #9 (sponza_column_c_diff.ktx)
[warning] ASTC not supported: decoding vase_dif.ktx
[info] Loaded gltf image #10 (sponza_details_diff.ktx)
[warning] ASTC not supported: decoding spnza_bricks_a_diff.ktx
[info] Loaded gltf image #11 (sponza_floor_a_diff.ktx)
[warning] ASTC not supported: decoding vase_hanging.ktx
[info] Loaded gltf image #12 (sponza_column_b_diff.ktx)
[warning] ASTC not supported: decoding vase_round.ktx
[info] Loaded gltf image #13 (vase_dif.ktx)
[warning] ASTC not supported: decoding chain_texture.ktx
[info] Loaded gltf image #16 (vase_round.ktx)
[warning] ASTC not supported: decoding sponza_curtain_blue_diff.ktx
[info] Loaded gltf image #15 (vase_hanging.ktx)
[warning] ASTC not supported: decoding sponza_curtain_diff.ktx
[info] Loaded gltf image #17 (chain_texture.ktx)
[warning] ASTC not supported: decoding sponza_curtain_green_diff.ktx
[info] Loaded gltf image #14 (spnza_bricks_a_diff.ktx)
[warning] ASTC not supported: decoding sponza_fabric_green_diff.ktx
[info] Loaded gltf image #21 (sponza_fabric_green_diff.ktx)
[warning] ASTC not supported: decoding sponza_fabric_blue_diff.ktx
[info] Loaded gltf image #22 (sponza_fabric_blue_diff.ktx)
[warning] ASTC not supported: decoding sponza_fabric_diff.ktx
[info] Loaded gltf image #23 (sponza_fabric_diff.ktx)
[warning] ASTC not supported: decoding sponza_roof_diff.ktx
[info] Loaded gltf image #18 (sponza_curtain_blue_diff.ktx)
[info] Loaded gltf image #19 (sponza_curtain_diff.ktx)
[info] Loaded gltf image #24 (sponza_roof_diff.ktx)
[info] Loaded gltf image #20 (sponza_curtain_green_diff.ktx)
[info] Time spent loading images: 1.320886 seconds across 4 threads.
HWCPipe [INFO] : Mali profiler initialization failed: Failed to get HW info.
[warning] Tiles killed by CRC match : not available
[warning] External Write Bytes : not available
[info] FPS: 0.5
[info] FPS: 392.4
[info] FPS: 425.0
[info] FPS: 415.6
[info] FPS: 422.8
[info] FPS: 415.0
[info] FPS: 416.4
[info] FPS: 421.3
[info] FPS: 419.9
[info] FPS: 422.6


```

I can run this sample compiled in another linux distribution.

Anyone know please what to do ?

---

### Post by maketopsite on 2021-06-04
solved by upgrading nvidia driver and rebuilding project

---

