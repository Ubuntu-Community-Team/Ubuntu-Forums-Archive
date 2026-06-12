---
title: "Every Vulkan application crashes in Ubuntu 17.10"
date: 2017-10-21
forum: Programming Talk
---

### Post by timo-wiren on 2017-10-21
I installed Ubuntu 17.10 and LunarG SDK 1.0.61.1. Every Vulkan application, including LunarG samples, crash with a segmentation fault in swapchain creation:

```
#3  0x00007ffff6e3c1ea in terminator_CreateSwapchainKHR () from /home/glaze/Downloads/VulkanSDK/1.0.61.1/x86_64/lib/libvulkan.so.1
```

Has anyone encountered this? I tried both Wayland and X.org. Crashes happen both with validation layers enabled and disabled. My GPU is Radeon R9 Nano and it's using RADV implementation. **vulkaninfo** doesn't crash and properly lists validation layers and instance extensions.

---

### Post by ragatron on 2017-10-30
It happens for me too, they need to update to 17.2.3, or 17.2.4. As a work around until they fix it I've been using the debian package for mesa-vulkan-drivers found here. [https://packages.debian.org/sid/mesa-vulkan-drivers](https://packages.debian.org/sid/mesa-vulkan-drivers)

---

