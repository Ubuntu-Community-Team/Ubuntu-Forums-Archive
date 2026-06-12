---
title: "Ubuntu Running Pretty Slow, No Propriatary Driver?"
date: 2012-02-27
forum: New to Ubuntu
---

### Post by unknowngal on 2012-02-27
Hello! Decided to come back to Ubuntu yet again, can't seem to pull away from it for long. Agh. :P But anyway...

I decided to install it on my old computer which ran XP, it's got -possibly- close to 1 gig of memory but not quite, 80 gb hard drive, and it ran XP fine, but I decided to install Ubuntu last night and I noticed that first, the CD's installation was slower than on my Windows 7 machine. The windows can be resized but it's pretty choppy and slow. The animations on the Unity bar are smooth, no problem there, but programs load slow, windows are slow, I'm not sure exactly what's going on since I thought Ubuntu would run fast on this machine despite its age.

Now, I did try to update the driver, thinking it would be an NVIDIA one, but it turns out there is no driver available. I checked with a command as to what graphics driver I actually have and it gave me this:

00:02.0 VGA compatible controller [0300]: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device [8086:2562] (rev 03)

I tried going to an Intel Linux website to see if I could download a driver, but none of the links there worked when I pasted them into Terminal. Such as this one:
[FONT=monospace]
[/FONT]git://anongit.freedesktop.org/git/xorg/driver/xf86-video-intel

So I'm stumped, and this is the only computer I have now, and I do want to use Ubuntu on it. I'm worried however that I may need to use a slimmer -buntu version, but ALSO worried that THOSE might end up slow as well.

Any help is greatly appreciated!!

---

### Post by HeroOfCanton on 2012-02-27
I would give Xubuntu (fairly light) or Lubuntu (extremely light) a shot. Unity can be pretty tough on a lower end video cards. You can give them a "test run" before committing if you would like by running the lines below and then selecting them from the login screen at boot.

```
sudo apt-get install xubuntu-desktop
sudo apt-get install lubuntu-desktop
```I switched to XFCE on my laptop more because of layout preference, however the speed was greatly improved which was a nice bonus. :)

---

### Post by unknowngal on 2012-02-27
Hey HeroOfCanton, thanks for replying to me! :) I'll try them both out to see how they run on here. XFCE would be Xubuntu right? :)

---

### Post by HeroOfCanton on 2012-02-27
> **unknowngal said:**
> Hey HeroOfCanton, thanks for replying to me! :) I'll try them both out to see how they run on here. XFCE would be Xubuntu right? :)

Correct. The common DE's (Desktop Environments) for ubuntu are Gnome (default), XFCE (xubuntu), KDE (kubuntu), and LXDE (lubuntu). They all have their own strengths and weaknesses. Just have to find the one that suits you best. :)

Once you find one you like I suggest downloading and installing the correct full distro (xubuntu, kubuntu, whatever). Otherwise you are just running a shell on top of a bloated system with Gnome **and** the one you are using.

---

### Post by unknowngal on 2012-02-27
*is back again* :P Well, I tried Xubuntu, and unfortunately the windows still sort of lagged in resizing, though moving them around there was no lag. However, when I played a music file, Banshee loaded and froze, I had to restart the computer manually. In the end, even Xubuntu was slow. Right now I'm on Lubuntu, and it seems to be better than Xubuntu, however when playing video, the graphics are not so good, they're discolored and pixelated. I don't remember them being that bad when using Windows XP on here, and also when using Audacious, the animation that shows the music/rhythm/beat/etc. plays for a second, then stops. I do notice a little slowing when opening a couple of programs. Any ideas on what could be going on? I hope I don't have to end up using something like Puppy Linux or something. o__o; Thank you!!

---

### Post by HeroOfCanton on 2012-02-27
Are these flash videos? If so, try googling flash-aid. I'm not sure what Audacious uses for the animation...

You may need to keep working on those drivers. To use git you need to install it first. Try running the code below and then trying to get those drivers again.

```
sudo apt-get install git-core
```Hope that helps!

---

### Post by unknowngal on 2012-02-27
Nope, they weren't flash videos, they were .avi files. Also, I did run the code you gave me, and it showed that everything was already installed.

I tried going through all the steps here: [https://help.ubuntu.com/community/Git](https://help.ubuntu.com/community/Git)

But I got stuck at the part that says "...but replace **yourserver.com** with the actual name of your server. Note that **gitosis** is an account already on your system that was created when you installed the gitosis package."

I'm not sure what my server is. :confused:

I tried all the links here: [http://intellinuxgraphics.org/download.html](http://intellinuxgraphics.org/download.html)

But they didn't work. Just says "No such file or directory" for each one.

---

### Post by HeroOfCanton on 2012-02-27
That server thing is only if you are hosting a server to allow others to use git. You don't need all of that.

Did a whole bunch of digging only to end up on the exact same page you already posted... I did, from there, find a link to this tar archive which seems to be active.

[http://xorg.freedesktop.org/archive/individual/driver/](http://xorg.freedesktop.org/archive/individual/driver/)

Maybe you can get it downloaded from there. Getting it installed after the extraction may require more knowledge than I have though. :)

---

### Post by unknowngal on 2012-02-27
Thank you for the link. :) I don't have a clue as to which Intel file to download though. And yeah, to install it would be also another issue. :confused:

---

### Post by HeroOfCanton on 2012-02-27
The 2D driver should be one of the (many) ones with "video-intel" in the name. The 3D mesa drivers seem to be either not there, or named something else...

Honestly though, looking through these forums, there seems to be a lot of problems with this card. The only ones I saw that claimed a "good fix" involved buying another graphics card. :rolleyes:

Seems like the drivers for that one are pretty awful, even once installed. Don't shoot the messenger. :P

---

### Post by unknowngal on 2012-02-27
No worries, I won't. :P Hmm. I downloaded the tar file, uncompressed it, and I ran this:

tar -xzvf /home/username/Downloads/xf86-video-intel-1.9.94.tar.gz

It gave me all this:

xf86-video-intel-1.9.94
xf86-video-intel-1.9.94/README
xf86-video-intel-1.9.94/configure.ac
xf86-video-intel-1.9.94/aclocal.m4
xf86-video-intel-1.9.94/Makefile.am
xf86-video-intel-1.9.94/Makefile.in
xf86-video-intel-1.9.94/config.h.in
xf86-video-intel-1.9.94/configure
xf86-video-intel-1.9.94/COPYING
xf86-video-intel-1.9.94/config.guess
xf86-video-intel-1.9.94/config.sub
xf86-video-intel-1.9.94/depcomp
xf86-video-intel-1.9.94/install-sh
xf86-video-intel-1.9.94/ltmain.sh
xf86-video-intel-1.9.94/missing
xf86-video-intel-1.9.94/src
xf86-video-intel-1.9.94/man
xf86-video-intel-1.9.94/man/Makefile.am
xf86-video-intel-1.9.94/man/Makefile.in
xf86-video-intel-1.9.94/man/intel.man
xf86-video-intel-1.9.94/src/modes
xf86-video-intel-1.9.94/src/parser
xf86-video-intel-1.9.94/src/Makefile.am
xf86-video-intel-1.9.94/src/Makefile.in
xf86-video-intel-1.9.94/src/brw_defines.h
xf86-video-intel-1.9.94/src/brw_structs.h
xf86-video-intel-1.9.94/src/sf_prog.h
xf86-video-intel-1.9.94/src/wm_prog.h
xf86-video-intel-1.9.94/src/common.h
xf86-video-intel-1.9.94/src/i2c_vid.h
xf86-video-intel-1.9.94/src/i810_accel.c
xf86-video-intel-1.9.94/src/i810_common.h
xf86-video-intel-1.9.94/src/i810_cursor.c
xf86-video-intel-1.9.94/src/i810_dga.c
xf86-video-intel-1.9.94/src/i810_driver.c
xf86-video-intel-1.9.94/src/i810.h
xf86-video-intel-1.9.94/src/i810_io.c
xf86-video-intel-1.9.94/src/i810_memory.c
xf86-video-intel-1.9.94/src/i810_reg.h
xf86-video-intel-1.9.94/src/i810_video.c
xf86-video-intel-1.9.94/src/i810_wmark.c
xf86-video-intel-1.9.94/src/i830_3d.c
xf86-video-intel-1.9.94/src/i830_accel.c
xf86-video-intel-1.9.94/src/i830_bios.c
xf86-video-intel-1.9.94/src/i830_bios.h
xf86-video-intel-1.9.94/src/i830_common.h
xf86-video-intel-1.9.94/src/i830_crt.c
xf86-video-intel-1.9.94/src/i830_cursor.c
xf86-video-intel-1.9.94/src/i830_debug.c
xf86-video-intel-1.9.94/src/i830_debug.h
xf86-video-intel-1.9.94/src/i830_display.c
xf86-video-intel-1.9.94/src/i830_display.h
xf86-video-intel-1.9.94/src/i830_driver.c
xf86-video-intel-1.9.94/src/i830_dvo.c
xf86-video-intel-1.9.94/src/i830.h
xf86-video-intel-1.9.94/src/i830_i2c.c
xf86-video-intel-1.9.94/src/i830_io.c
xf86-video-intel-1.9.94/src/i830_lvds.c
xf86-video-intel-1.9.94/src/i830_memory.c
xf86-video-intel-1.9.94/src/i830_modes.c
xf86-video-intel-1.9.94/src/i830_video.c
xf86-video-intel-1.9.94/src/i830_video.h
xf86-video-intel-1.9.94/src/i830_reg.h
xf86-video-intel-1.9.94/src/i830_sdvo.c
xf86-video-intel-1.9.94/src/i830_sdvo.h
xf86-video-intel-1.9.94/src/i830_sdvo_regs.h
xf86-video-intel-1.9.94/src/i830_tv.c
xf86-video-intel-1.9.94/src/i915_3d.c
xf86-video-intel-1.9.94/src/i915_3d.h
xf86-video-intel-1.9.94/src/i915_reg.h
xf86-video-intel-1.9.94/src/i915_video.c
xf86-video-intel-1.9.94/src/i965_video.c
xf86-video-intel-1.9.94/src/i830_exa.c
xf86-video-intel-1.9.94/src/i830_xaa.c
xf86-video-intel-1.9.94/src/i830_render.c
xf86-video-intel-1.9.94/src/i915_render.c
xf86-video-intel-1.9.94/src/i965_render.c
xf86-video-intel-1.9.94/src/local_xf86Rename.h
xf86-video-intel-1.9.94/src/i810_dri.c
xf86-video-intel-1.9.94/src/i810_dri.h
xf86-video-intel-1.9.94/src/i830_dri.c
xf86-video-intel-1.9.94/src/i810_hwmc.c
xf86-video-intel-1.9.94/src/i830_dri.h
xf86-video-intel-1.9.94/src/packed_yuv_sf.g4a
xf86-video-intel-1.9.94/src/packed_yuv_wm.g4a
xf86-video-intel-1.9.94/src/exa_sf.g4a
xf86-video-intel-1.9.94/src/exa_sf_mask.g4a
xf86-video-intel-1.9.94/src/exa_sf_rotation.g4a
xf86-video-intel-1.9.94/src/xvmc
xf86-video-intel-1.9.94/src/exa_wm_maskca.g4a
xf86-video-intel-1.9.94/src/exa_wm_maskca_srcalpha.g4a
xf86-video-intel-1.9.94/src/exa_wm_masknoca.g4a
xf86-video-intel-1.9.94/src/exa_wm_nomask.g4a
xf86-video-intel-1.9.94/src/exa_wm_rotation.g4a
xf86-video-intel-1.9.94/src/exa_sf_mask_prog.h
xf86-video-intel-1.9.94/src/exa_sf_prog.h
xf86-video-intel-1.9.94/src/exa_sf_rotation_prog.h
xf86-video-intel-1.9.94/src/exa_wm_maskca_prog.h
xf86-video-intel-1.9.94/src/exa_wm_maskca_srcalpha_prog.h
xf86-video-intel-1.9.94/src/exa_wm_masknoca_prog.h
xf86-video-intel-1.9.94/src/exa_wm_nomask_prog.h
xf86-video-intel-1.9.94/src/exa_wm_rotation_prog.h
xf86-video-intel-1.9.94/src/bios_reader
xf86-video-intel-1.9.94/src/ch7017
xf86-video-intel-1.9.94/src/ch7xxx
xf86-video-intel-1.9.94/src/ivch
xf86-video-intel-1.9.94/src/sil164
xf86-video-intel-1.9.94/src/reg_dumper
xf86-video-intel-1.9.94/src/reg_dumper/Makefile.am
xf86-video-intel-1.9.94/src/reg_dumper/Makefile.in
xf86-video-intel-1.9.94/src/reg_dumper/main.c
xf86-video-intel-1.9.94/src/reg_dumper/reg_dumper.h
xf86-video-intel-1.9.94/src/reg_dumper/xprintf.c
xf86-video-intel-1.9.94/src/sil164/Makefile.am
xf86-video-intel-1.9.94/src/sil164/Makefile.in
xf86-video-intel-1.9.94/src/sil164/sil164.c
xf86-video-intel-1.9.94/src/sil164/sil164_module.c
xf86-video-intel-1.9.94/src/sil164/sil164.h
xf86-video-intel-1.9.94/src/sil164/sil164_reg.h
xf86-video-intel-1.9.94/src/ivch/Makefile.am
xf86-video-intel-1.9.94/src/ivch/Makefile.in
xf86-video-intel-1.9.94/src/ivch/ivch.c
xf86-video-intel-1.9.94/src/ivch/ivch_module.c
xf86-video-intel-1.9.94/src/ivch/ivch_reg.h
xf86-video-intel-1.9.94/src/ch7xxx/Makefile.am
xf86-video-intel-1.9.94/src/ch7xxx/Makefile.in
xf86-video-intel-1.9.94/src/ch7xxx/ch7xxx.c
xf86-video-intel-1.9.94/src/ch7xxx/ch7xxx_module.c
xf86-video-intel-1.9.94/src/ch7xxx/ch7xxx.h
xf86-video-intel-1.9.94/src/ch7xxx/ch7xxx_reg.h
xf86-video-intel-1.9.94/src/ch7017/Makefile.am
xf86-video-intel-1.9.94/src/ch7017/Makefile.in
xf86-video-intel-1.9.94/src/ch7017/ch7017.c
xf86-video-intel-1.9.94/src/ch7017/ch7017_module.c
xf86-video-intel-1.9.94/src/ch7017/ch7017_reg.h
xf86-video-intel-1.9.94/src/bios_reader/Makefile.am
xf86-video-intel-1.9.94/src/bios_reader/Makefile.in
xf86-video-intel-1.9.94/src/bios_reader/bios_dumper.c
xf86-video-intel-1.9.94/src/bios_reader/bios_reader.c
xf86-video-intel-1.9.94/src/xvmc/Makefile.am
xf86-video-intel-1.9.94/src/xvmc/Makefile.in
xf86-video-intel-1.9.94/src/xvmc/I810XvMC.c
xf86-video-intel-1.9.94/src/xvmc/I810XvMC.h
xf86-video-intel-1.9.94/src/parser/xf86Parser.h
xf86-video-intel-1.9.94/src/parser/xf86Optrec.h
xf86-video-intel-1.9.94/src/modes/xf86Modes.h
xf86-video-intel-1.9.94/src/modes/xf86Modes.c
xf86-video-intel-1.9.94/src/modes/xf86cvt.c
xf86-video-intel-1.9.94/src/modes/xf86Crtc.h
xf86-video-intel-1.9.94/src/modes/xf86Crtc.c
xf86-video-intel-1.9.94/src/modes/xf86Cursors.c
xf86-video-intel-1.9.94/src/modes/xf86EdidModes.c
xf86-video-intel-1.9.94/src/modes/xf86RandR12.c
xf86-video-intel-1.9.94/src/modes/xf86RandR12.h
xf86-video-intel-1.9.94/src/modes/xf86Rename.h
xf86-video-intel-1.9.94/src/modes/xf86Rotate.c
xf86-video-intel-1.9.94/src/modes/xf86DiDGA.c

After that, I have no idea what to do. :P :confused:

---

### Post by unknowngal on 2012-02-27
Anybody? ^_^;; Or is this computer just really more or less unsalvagable unless one installs a new graphics card? :| 

Thank you!

---

### Post by HeroOfCanton on 2012-02-27
> **unknowngal said:**
> Anybody? ^_^;; Or is this computer just really more or less unsalvagable unless one installs a new graphics card? :| 

Thank you!

Wish I could continue to help, but compiling and installing the driver is still a bit out of my knowledge range for ubuntu. What I read seemed to indicate the people doing it "successfully" went from slow processing and odd looking icons to full system lock-ups though. :(

On the bright side, you can probably get a PCI graphics card really cheap. Just make sure it's linux compatible:

[http://www.linux-mips.org/wiki/PCI_graphics_cards#Cards_supported_by_the_Linux_framebuffer_driver](http://www.linux-mips.org/wiki/PCI_graphics_cards#Cards_supported_by_the_Linux_framebuffer_driver)
[http://www.linuxdoc.org/HOWTO/PCI-HOWTO-5.html](http://www.linuxdoc.org/HOWTO/PCI-HOWTO-5.html)

---

### Post by Miljet on 2012-02-27
I'm not much on compiling programs either, but just wanted to point out that the first thing that jumped out at me in your list of extracted files is a README file. Those usually give you some instructions for installing.

---

