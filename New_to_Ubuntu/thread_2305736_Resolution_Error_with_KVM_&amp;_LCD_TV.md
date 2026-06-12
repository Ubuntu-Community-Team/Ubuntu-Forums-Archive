---
title: "Resolution Error with KVM &amp; LCD TV"
date: 2015-12-08
forum: New to Ubuntu
---

### Post by russell14 on 2015-12-08
After installing Ubuntu 14.04 while hooked up to a 15" VGA monitor, I decided to move the box to my rack.  I then plugged everything into a Belkin OmniView KVM.
I rebooted, and am now stuck @ 720x400 for the display.  The display is an LG 32" LCD tv.  The same KVM/display is running a Win7 box @ 1024x768 and *was* running an older install of Ubuntu at the same resolution.  Below is my lshw & xrandr outputs:

bsd@bsdserver2:~$ sudo lshw -C display
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: MGA G200eW WPCM450
       vendor: Matrox Electronics Systems Ltd.
       physical id: 1
       bus info: pci@0000:09:01.0
       version: 0a
       width: 32 bits
       clock: 33MHz
       capabilities: pm vga_controller bus_master cap_list
       configuration: latency=64 maxlatency=32 mingnt=16
       resources: memory:f7000000-f7ffffff memory:faffc000-faffffff memory:fb000000-fb7fffff

bsd@bsdserver2:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 720 x 400, current 720 x 400, maximum 720 x 400
default connected primary 720x400+0+0 0mm x 0mm
   720x400        70.0* 

Is there any way to increase the resolution that xrandr has available or am I stuck?

Thanks for any ideas.

---

### Post by sandyd on 2015-12-08
Issues are caused by [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1316035](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1316035)

Drivers are not loaded (Display unclaimed)

From the comments, it seems that the best you can get is a low resolution VESA (the default driver when no video driver is loaded or available) display on the screen.

Someone tried setting the VESA resolution manually (see [here]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1316035/comments/42")), and it worked for them, so you likely want to try that fix out first.

---

### Post by russell14 on 2015-12-10
Whelp, that explains that.  Thank you.  
I tried that link you suggested, it still refuses to render above 720.  
I'm not particularly tied to any distro, so I might just reinstall 12 or see if 15 has the same bug.  
Might just go ahead and buy a nvidia card be done with it.
Thank you again for the info.

---

