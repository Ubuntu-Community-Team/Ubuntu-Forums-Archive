---
title: "Getting started with OpenGL/GLM"
date: 2014-10-08
forum: Programming Talk
---

### Post by mark allyn on 2014-10-08
Hello everyone,

I'm trying to get started writing GLM code, but am confused on several fronts, and the various tutes I've reviewed have not clarified them.  Perhaps one of you folks can help out.

I downloaded the glm-dev UBUNTU package and installed it.  No problem.

First, I'm not clear on whether the package contains all the headers and libraries needed.  In particular, some tutes indicate that libglut must be present, but it isn't in my /usr/lib or anywhere else, for that matter.  Ditto the header for that lib.  If it isn't in the package, how do I get it?

Second, a number of tutes discuss the need for video drivers and compatibility.  I don't know how to handle this issue.  The current display has these properties:

             description: VGA compatible controller
             product: 82Q33 Express Integrated Graphics Controller
             vendor: Intel Corporation

I haven't any idea whether this driver will respond appropriately to my code, and if not, how would I set about modifying the driver.  I really don't want to mess up my pretty ACER box.  

Somebody who could guide me through this maze would be a true friend.  Steeldriver, are you there?  How about it, Old Fred?

Regards,
Mark Allyn

---

### Post by mark allyn on 2014-10-09
Hello everyone,

OK, so I'm updating previous query.  I succeeded in downloading all the necessary code.  I latched onto a tute that provides code for a simple shaded triangle.  I compiled and linked and was feeling pretty good.  But, when the code runs it gtenerates a seg fault.  Investigation indicated that the code was failing because my version of OpenGL is 1.4 and the particular application required OpenGL 2.1.  Ugh.

Using glxinfo | grep version command the following is the response:


> server glx version string: 1.4
client glx version string: 1.4
GLX version: 1.4
OpenGL version string: 1.4 Mesa 10.1.3

So, here's the query. ** How do I set about upgrading to version 2.1?**  I realize this may require an upgrade to the graphics driver and perhaps -- hopefully, not-- an upgraded video card.  

Running lshw -c video yields:

> 
*-display               
       description: VGA compatible controller
       product: 82Q33 Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:44 memory:f0100000-f017ffff ioport:1240(size=8) memory:e0000000-efffffff memory:f0000000-f00fffff



Further info about the i915 driver comes from modinfo i915:
> 
filename:       /lib/modules/3.13.0-36-generic/kernel/drivers/gpu/drm/i915/i915.ko
license:        GPL and additional rights
description:    Intel Graphics
author:         Tungsten Graphics, Inc.
license:        GPL and additional rights
srcversion:     5CEC27750601BA0C8E6DE21


Plus a lot more which I haven't included.

Can someone tell me if I also need to upgrade the driver and/or the card?  I am uncertin how to test for support for OpenGL 2.1.

Regards,
Mark Allyn

---

