---
title: "Stable nvidia-current 280.13 in repos now"
date: 2011-08-05
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-08-05
The newest stable Nvidia proprietary driver, nvidia-current (280.13-0ubuntu1) has just entered official Oneiric repos.

Here:
[https://launchpad.net/ubuntu/oneiric/+source/nvidia-graphics-drivers/280.13-0ubuntu1](https://launchpad.net/ubuntu/oneiric/+source/nvidia-graphics-drivers/280.13-0ubuntu1)

> **Changelog**
nvidia-graphics-drivers (280.13-0ubuntu1) oneiric; urgency=low

  * debian/nvidia-current.postinst{.in}:
    - Make nvidia.icd a slave link.
    - Make libOpenCL.so a slave link for both architectures.
  * New upstream release:
    - Added support for the following GPUs:
      o GeForce GT 540
      o GeForce GTX 570M
      o GeForce GTX 580M
    - Fixed memory error and abort reported by glibc when running
      the application FieldView from Intelligent Light.
    - Fixed an OpenGL driver bug that caused an application crash
      when running Altair HyperMesh.
    - Fixed a performance problem when switching between stereo
      and monoscopic rendering in the application Smoke.
    - Fixed poor X driver handling of pixmap out of memory
      scenarios.
    - Fixed an interrupt handling deficiency that could lead to
      performance and stability problems when many NVIDIA GPUs
      shared few IRQs.
    - Fixed bugs in the VDPAU presentation queue that could cause
      GPU errors and hangs when destroying a presentation queue.
      This happens when exiting applications, and also when
      toggling to and from full-screen mode in Adobe Flash.
    - Fixed a GLX bug that could cause the X server to crash when
      rendering a display list using GLX indirect rendering.
    - Fixed a GLX bug that could cause a hang in applications that
      use X server grabs.
    - Fixed an X driver bug that caused 16x8 stipple patterns to
      be rendered incorrectly.
    - Fixed a GLX_EXT_texture_from_pixmap bug that caused
      corruption when texturing from sufficiently small pixmaps
      and, in particular, corruption in the GNOME Shell Message
      Tray.
    - Added unofficial GLX protocol support (i.e. for GLX indirect
      rendering) for the following OpenGL extension:
      o GL_EXT_vertex_attrib_64bit
    - Added GLX protocol support (i.e. for GLX indirect rendering)
      for the following OpenGL extensions:
      o GL_ARB_half_float_pixel
      o GL_EXT_packed_depth_stencil
 -- Alberto Milone <email address hidden>   Tue, 02 Aug 2011 15:03:40 +0200

---

### Post by Harry33 on 2011-08-05
Hmm, my advice is to not update to this one.
For me, synaptic hangs and then the whole system hangs.

What was surprising, was that after a few downgrades and reinstalls my system will not boot anymore, kernel will not load.
The system hangs almost right after grub, with no messages.

---

### Post by dino99 on 2011-08-05
> **Harry33 said:**
> Hmm, my advice is to not update to this one.
For me, synaptic hangs and then the whole system hangs.

What was surprising, was that after a few downgrades and reinstalls my system will not boot anymore, kernel will not load.
The system hangs almost right after grub, with no messages.

is it with mesa 7.11 or 7.12 ?

on my side i stay with 280.04 as newest versions dont bring much fixes and/or features (interesting for latest gpu only), and i still experience hangs like you if i use either: 7.11 + >280.04 or 7.12 + >280.04

---

### Post by Harry33 on 2011-08-05
> **dino99 said:**
> is it with mesa 7.11 or 7.12 ?

on my side i stay with 280.04 as newest versions dont bring much fixes and/or features (interesting for latest gpu only), and i still experience hangs like you if i use either: 7.11 + >280.04 or 7.12 + >280.04

I haven't got the change to install 7.12 branch mesa.
So I have only tested with 7.11 from official repos.
280.04 is the only 280-version that works here.
280.11 and 280.13 will cause synaptic to hang (terminal will not respond) and then the system will not reboot.

And now 280.13 broke my system.
I have to chroot and purge it, because kernel won't load anymore.

---

### Post by sgage on 2011-08-05
> **Harry33 said:**
> Hmm, my advice is to not update to this one.
For me, synaptic hangs and then the whole system hangs.

What was surprising, was that after a few downgrades and reinstalls my system will not boot anymore, kernel will not load.
The system hangs almost right after grub, with no messages.

280.13 is working fine for me.

---

### Post by 3vi1 on 2011-08-05
280.13 works fine here too (GTX 465).

---

### Post by Quackers on 2011-08-05
Have you tried synaptic package manager?
It fails to respond after being opened here, then doesn't want to close, as Harry33 mentioned earlier.

---

### Post by Harry33 on 2011-08-05
> **Harry33 said:**
> I haven't got the change to install 7.12 branch mesa.
So I have only tested with 7.11 from official repos.
280.04 is the only 280-version that works here.
280.11 and 280.13 will cause synaptic to hang (terminal will not respond) and then the system will not reboot.

And now 280.13 broke my system.
I have to chroot and purge it, because kernel won't load anymore.

After chrooting, purging and reinstalling both kernel and nvidia-current_280.04
I am back to business.

It is very odd if somenone (who has nvidia-current_280.13) can start synaptic and after that does not have a hanging system (gnome-termnal not responding).
Really, only 280.04 works for me.

---

### Post by sgage on 2011-08-05
After further trials...

When I first login to Unity, Synaptic starts up fine and functions as expected. However, it does not want to quit, and finally asks to be force-quit. Then it won't start back up until a re-login. However, there are seemingly no other system problems stemming from this.

I am running nouveau for the time being, because I use Synaptic a lot.

---

### Post by Harry33 on 2011-08-05
> **sgage said:**
> After further trials...

When I first login to Unity, Synaptic starts up fine and functions as expected. However, it does not want to quit, and finally asks to be force-quit. Then it won't start back up until a re-login. However, there are seemingly no other system problems stemming from this.

I am running nouveau for the time being, because I use Synaptic a lot.

Right Sgage, so you too have the same bug with nvidia-current 280.13.
I have found that it is only synaptic that bothers with that driver.
There is however a bigger tendency to speed a processor up to 100% with this 280.13.

I am going to make a bug report about this.

---

### Post by Harry33 on 2011-08-05
Here is the bug (821702) report

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/821702](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/821702)

---

### Post by VinDSL on 2011-08-05
I'll upgrade, when I get back to the abode, and report back later.  ;)

After reading this thread, I *think* I may have had an instance or two where Synaptic didn't fully close.

It didn't cause any problems, except occasionally apt-get reports that another program is running, and the resources are locked, e.g. I cannot do an update.

When I do a top and/or ps, I can't see Synaptic running, but maybe a flag isn't clearing, or whatever.

---

### Post by sgage on 2011-08-05
> **Harry33 said:**
> Right Sgage, so you too have the same bug with nvidia-current 280.13.
I have found that it is only synaptic that bothers with that driver.
There is however a bigger tendency to speed a processor up to 100% with this 280.13.

I am going to make a bug report about this.

Let us know when you do, and we'll all "me too" it...

---

### Post by rv65 on 2011-08-05
Can't log in with this new driver. It hangs after I log in (I still get the cursor though).

---

### Post by Harry33 on 2011-08-06
> **rv65 said:**
> Can't log in with this new driver. It hangs after I log in (I still get the cursor though).

If you can get to the console (recovery mode from grub menu), reinstall kernel and downgrade the nvidia-current.

---

### Post by VinDSL on 2011-08-06
Sorry, Harry!  I tried to break UbuOO, but...

I just got home, un-pinned 280.04, and ran an update.

Bottom line: Dern it, 280.13 is working fine...

I did a cold boot, after performing the updates - did another update with Synaptic - no updates waiting.

Then, from CLI, I ran the apt-get twins, and they weren't holding anything back, nor did Synaptic fail to close.

So, I'm at a loss, as to what's causing you guys (and gal) so much grief.

---

### Post by VinDSL on 2011-08-06
You know, I was just thinking...

The only thing I'm personally holding back now e.g. pinned is the cairo 2D vector graphics library aka libcairo2.

Maybe this makes all the difference, yes?

In general, the latest version(s) of libcairo2 make my PC almost unusable (while running nvidia drivers)...

I'm running 1.10.2-2ubuntu2 (natty).

1.10.2-2ubuntu2 BREAKS wayland (no gl backend) - which is an accomplissement des désirs, IMO!  :D

---

### Post by sgage on 2011-08-06
> **Harry33 said:**
> Here is the bug (821702) report

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/821702](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/821702)

Thanks! I've gone and piled on :KS

---

### Post by Harry33 on 2011-08-06
> **VinDSL said:**
> You know, I was just thinking...

The only thing I'm personally holding back now e.g. pinned is the cairo 2D vector graphics library aka libcairo2.

Maybe this makes all the difference, yes?

In general, the latest version(s) of libcairo2 make my PC almost unusable (while running nvidia drivers)...

I'm running 1.10.2-2ubuntu2 (natty).

1.10.2-2ubuntu2 BREAKS wayland (no gl backend) - which is an accomplissement des désirs, IMO!  :D

Yes you seem to hit the nerve.
The issue may very well be libcairo2. And that would not be the first time.

---

### Post by mc4man on 2011-08-06
> **Harry33 said:**
> Yes you seem to hit the nerve.
The issue may very well be libcairo2. And that would not be the first time.
See the same here on my p4 w/ 1GB, in this case use the current  O cairo source built without gl support. No issues  with synaptic closing out, ect.
(will comment that in bug

---

### Post by Harry33 on 2011-08-06
If you want use the latest non-gl build cairo,
use this Oneiric earlier version 1.10.2-2ubuntu4.

Here:
[https://launchpad.net/ubuntu/+source/cairo/1.10.2-2ubuntu4](https://launchpad.net/ubuntu/+source/cairo/1.10.2-2ubuntu4)

---

### Post by sgage on 2011-08-06
> **Harry33 said:**
> If you want use the latest non-gl build cairo,
use this Oneiric earlier version 1.10.2-2ubuntu4.

Here:
[https://launchpad.net/ubuntu/+source/cairo/1.10.2-2ubuntu4](https://launchpad.net/ubuntu/+source/cairo/1.10.2-2ubuntu4)

Thanks Harry!

---

### Post by Harry33 on 2011-08-06
Now after testing cairo (1.10.2-2ubuntu4), the latest non gl build of cairo,
I can confirm there are no nvidia proprietary driver hang up nor CPU speeding up issues.
This issue is fixed.
However I do reckon either nvidia-current or libcairo2 must be patched somehow to overcome this in future if gl is to be enabled.

---

### Post by VinDSL on 2011-08-06
> **Harry33 said:**
> Now after testing cairo (1.10.2-2ubuntu4), the latest non gl build of cairo[...]
1.10.2-2ubuntu4 is working fine on my PC as well.

Pinned  ;)

---

### Post by Harry33 on 2011-08-07
> **VinDSL said:**
> 1.10.2-2ubuntu4 is working fine on my PC as well.

Pinned  ;)

Hi VinDSL,
if you do not want to keep pinned cairo packages, you can download a new built from Mingming test PPA. There is the version 1.10.2-6ubuntu2.2 (which is the highest version).
It is a new non gl build.

Here:
[https://launchpad.net/~portis25/+archive/test](https://launchpad.net/~portis25/+archive/test)

---

### Post by VinDSL on 2011-08-07
Thanks, Harry!

I'll try it in the morning.

Looks like the i386 version is scheduled to build in 5 hours.

---

### Post by VinDSL on 2011-08-07
Source:  [https://launchpad.net/ubuntu/+source/cairo/1.10.2-2ubuntu4/+build/2487193](https://launchpad.net/ubuntu/+source/cairo/1.10.2-2ubuntu4/+build/2487193)

Worked a treat, Harry!  :D

Additionally, apport is functional again.

I haven't been able to send crash reports lately. Apport reported I was running "obsolete" software (cairo2) and wouldn't allow me to send bug reports.  Now apport works too!

---

### Post by mc4man on 2011-08-09
You can go back to using the O packages - rebuilt with no gl today
cairo (1.10.2-6ubuntu3)

---

### Post by Harry33 on 2011-08-10
> **mc4man said:**
> You can go back to using the O packages - rebuilt with no gl today
cairo (1.10.2-6ubuntu3)

That is true, the bug #821702 is fixed for now and the unnecessary
libegl1-mesa, libgbm1, libwayland0, libxcb-dri2-0 and libxcb-xfixes0
can be removed.

---

### Post by dino99 on 2011-08-10
hey fixed till next time ;)

---

### Post by VinDSL on 2011-08-10
> **dino99 said:**
> hey fixed till next time ;)
LoL!  You think they learn by now...  :)

---

### Post by VinDSL on 2011-08-10
> **Harry33 said:**
> That is true, the bug #821702 is fixed for now and the unnecessary
libegl1-mesa, libgbm1, libwayland0, libxcb-dri2-0 and libxcb-xfixes0
can be removed.
Confirmed.

Installed:
[LIST]
[*]libcairo 1.10.2-6ubuntu3
[/LIST]
Removed:
[LIST]
[*]libegl1-mesa
[*]libgbm1
[*]libwayland0
[*]libxcb-dri2-0
[*]libxcb-xfixes0
[/LIST]
Working great!

---

