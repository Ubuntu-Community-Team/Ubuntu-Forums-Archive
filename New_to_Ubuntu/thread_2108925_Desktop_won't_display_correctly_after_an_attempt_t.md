---
title: "Desktop won't display correctly after an attempt to fix HDMI audio"
date: 2013-01-26
forum: New to Ubuntu
---

### Post by crobertsbmw on 2013-01-26
I was trying to fix the audio so that it would forward for HDMI output. I tried this:

[http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29_BETA.2FEXPERIMENTAL](http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29_BETA.2FEXPERIMENTAL)

to install the catalyst and .deb stuff. And then I restarted my computer. Before I even got a chance to see if my audio problem was fixed the the display went all weird. The display doesn't show me anything besides a blank background. I saw this recent question: I can see a background, nothing more? and wasn't able to see anything under the list of drivers. I ran

sudo lshw -C display.

Here is the output:

*-display UNCLAIMED
 description: VGA compatible controller product: RS880M [Mobility Radeon HD 4200 Series]         vendor: Advanced Micro Devices [AMD] nee ATI physical id: 5 bus info: pci@0000:01:05.0 version:  00 width: 32 bits clock: 33MHz capabilities: pm msi vga_controller bus_master cap_list configuration: latency=0 resources: memory:e0000000-efffffff ioport:3000(size=256) memory:f0300000-f030ffff memory:f0200000-f02fffff

Any ideas on how to fix this problem. Whatever I did has gimped me pretty bad.

---

