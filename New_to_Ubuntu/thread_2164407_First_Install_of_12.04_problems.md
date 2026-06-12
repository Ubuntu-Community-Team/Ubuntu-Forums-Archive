---
title: "First Install of 12.04 problems"
date: 2013-07-31
forum: New to Ubuntu
---

### Post by geomcd1949 on 2013-07-31
Intel i7-4770 with onboard graphics (Gallium 0.4 on llvmpipe (LLVM 0x300) )
Vertex4 128Gb SSD
ASRock H87 Pro4 Motherboard

Just built computer. Installed 12.04 from disk and updated. Now I get:

1. In Systems Settings > Appearance, no ability to change the size of Launcher icons (the slider just isn't there),

2. In Systems Settings > Displays, the Asus HD monitor is not recognized (that is, the monitor is listed as "Laptop"). A monitor connected with a DVI cable also is listed as "Laptop." Clicking "Detect Monitor" has no effect.

3. Won't recognize two monitors when both are connected when computer is off, then computer started (HD monitor shows a white background with black vertical stripes),

4. No Sound (the only two options I get in All Settings > Sound are Digital Output (S/PDIF) and Analog Output. [No confiurations of these will play sound.] The monitor plays sound when connected to another computer, so I know it works. I tried to get sound both through the HD cable connecting the monitor and a green single cord that connects to the computer and the to monitor (sorry, I don't know its nomenclature). No sound will play in ANY configuration that is available in the System Settings > Sound options with either the green cable or the HD cable.

Thanks for any advice.

~George

---

### Post by TheFu on 2013-07-31
Which GPU does it have? Did you load the binary vendor libraries for it?  Did you use the vendor's program to manage dual monitors?
* nvidia-ettings
* whatever ATI uses

On my ATI AMD-E350, the audio drivers are part of the video driver code, until the video drivers were installed, the audio didn't work.

Sorry that I don't use the stock Ubuntu GUI, so I can't describe how to do anything via point-n-click.
There's a CLI program, alsamixer, that controls sound output to different audio devices and levels. To determine the available devices, run **aplay -l**

So, if you can confirm the video drivers are installed and running, write back and we can start with audio troubleshooting. There is a great Ubuntu Sound Troubleshooting webpage - google finds it easy, but it is best used when the drivers have not been loaded.

---

### Post by newb85 on 2013-07-31
If the launcher icon size slider is missing, you're running Unity2D, not the standard Unity.  That probably means you don't have the proprietary graphics drivers installed.  Pull up the Dash (the Ubuntu icon in the top-left corner of the screen) and go to Additional Drivers.  See if the proprietary drivers for your GPU are available there.

---

### Post by geomcd1949 on 2013-07-31
Thanks Fu!

Graphics card is the HD 4600 in the CPU. The All Settings > Details listing is Gallium 0.4 on llvmpipe (LLVM 0x300. 

I did not load vendor libraries for it (don't know how).

Return for **aplay -l** is:

**** List of PLAYBACK Hardware Devices ****
card 1: PCH [HDA Intel PCH], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

All Settings > Additional Drivers gives "No Proprietary Drivers Are In Use on This system."

Thanks!

~Geo.

---

### Post by geomcd1949 on 2013-07-31
Thanks Newb,

1. Additional Driver search doesn't list any available drivers. 

2. How can I tell if I'm running Unity 2D or 3D?

3. If I'm running 2D, how do I activate 3D?

Thanks.

~Geo.

---

### Post by Vladlenin5000 on 2013-07-31
An Intel such as yours should work out-of-the-box, unlike ATI or nVidia which require proprietary drivers for better performance. 
As for the sound even weirder. HDMI would require further settings but the analog output, the audio green cable you mentioned, should just work. That, of course, unless the audio isn't somehow deactivated on BIOS...

---

### Post by TheFu on 2013-07-31
Perhaps if you posted the relevant drivers loaded, that would make some ideas click?
[http://blog.jdpfu.com/2013/04/27/linux-troubleshooting-101-knowing-your-hardware](http://blog.jdpfu.com/2013/04/27/linux-troubleshooting-101-knowing-your-hardware) for background and **lsmod** for the total list. Please pair that down to just the video and audio drivers and post using a -code- tag here so spacing isn't funny.

---

### Post by geomcd1949 on 2013-07-31
Fu,

I've decided to install Ubuntu 13.04 instead of 12.04 LTS, but I see in your signature an invitation to ask why users should run an LtS. So I ask you why.

Thanks.

George

---

### Post by deadflowr on 2013-07-31
Intel graphics cards are open-source only, so there will not be any listed in the additional drivers.
They are built into the system, so what you have is what is considered the most stable for the system.
There are always newer drivers, and drivers with updates released, but as a whole, Ubuntu tries to provide the most stable for the system, and newer drivers can cause problems if not properly tested before release.

A reason for going LTS vs standard(12.04 vs 13.04) is that LTS has longer support and provides a roughly more stable environment to work with.
Albeit, 13.04 has been incredibly stable for me.
Unfortunately, the support for non-LTS versions is only 9 months, as opposed to 5 years for LTS.

---

### Post by TheFu on 2013-07-31
> **deadflowr said:**
> Intel graphics cards are open-source only, so there will not be any listed in the additional drivers.
They are built into the system, so what you have is what is considered the most stable for the system.
There are always newer drivers, and drivers with updates released, but as a whole, Ubuntu tries to provide the most stable for the system, and newer drivers can cause problems if not properly tested before release.

A reason for going LTS vs standard(12.04 vs 13.04) is that LTS has longer support and provides a roughly more stable environment to work with.
Albeit, 13.04 has been incredibly stable for me.
Unfortunately, the support for non-LTS versions is only 9 months, as opposed to 5 years for LTS.

Well stated, thought some non-LTS releases have shorter and some have longer support periods if you look at historical data. Here is [http://blog.jdpfu.com/2013/07/19/why-ubuntu-users-should-run-an-lts-release](http://blog.jdpfu.com/2013/07/19/why-ubuntu-users-should-run-an-lts-release) my considered response to the question.

The only times someone should run a non-LTS release are:
* developers on bleeding edge stuff (most corporate devs should **never** use bleeding edge anything.
* testers supporting the developers
* if new hardware is **only** supported in a newer release - popular hardware support will probably be back-ported to the current LTS, however.
* if they just like unstable operating systems and programs that don't always work.

Running an LTS does have drawbacks around 18 months after the release. Software devs usually stop patching programs for it and look to the next LTS release alpha for a platform.  I've been stuck with a non-functioning IM client for about 4 months before 12.04 was released and I was still running 10.04.  Nothing is perfect.

---

### Post by deadflowr on 2013-07-31
It used to be 3 years on the desktop and 5 years on the server, but they decided that having all run for 5 years made more sense.
LTS-wise.

At the same time, they dropped Standard release(as non-LTS version are called) support from 18 months to 9.
The reasoning behind that was that most people running a standard release would upgrade fairly quickly.
and since most move to newer releases when they come(or shortly there after) it wasn't efficient for them to continue support for a handful of users.
A patch, so to say, on plugging a drain on already limited resources.

---

### Post by geomcd1949 on 2013-07-31
Solution: **Ubuntu 12.04**, a long term support release, **is no longer supported by the Intel Linux Graphics Installer**. It seems the installer only supports the last two Ubuntu and Fedora releases and doesn't take LTS releases into account.

Therefore, if you try to install 12.04 in a system that has an Intel processor released after 12.04 was released, your integrated graphics card won't be recognized.

The solution is here: [http://www.webupd8.org/2013/05/intel-linux-graphics-installer.html](http://www.webupd8.org/2013/05/intel-linux-graphics-installer.html), where you can install the **Intel Linux Graphics Installer.**

---

### Post by deadflowr on 2013-08-01
> [COLOR=#000000]Therefore, if you try to install 12.04 in a system that has an Intel processor released after 12.04 was released, your integrated graphics card won't be recognized.[/COLOR]

Not quite true.
LTS release have point releases, which provide upgraded kernels and newer graphics stacks.
Currently in 12.04.2 you have the quantal kernel and X stack, and in 12.04.3 it'll be the raring stack.
You will only have the older stacks if you installed the now defunct older versions of 12.04.(12.04.0, and 12.04.1) and haven't upgraded the kernel to the lts-quantal kernel.

---

### Post by TheFu on 2013-08-01
> **deadflowr said:**
> Not quite true.
LTS release have point releases, which provide upgraded kernels and newer graphics stacks.
Currently in 12.04.2 you have the quantal kernel and X stack, and in 12.04.3 it'll be the raring stack.
You will only have the older stacks if you installed the now defunct older versions of 12.04.(12.04.0, and 12.04.1) and haven't upgraded the kernel to the lts-quantal kernel.

All the people doing **apt-get upgrade** and not **apt-get dist-upgrade** will learn why they want dist-upgrade now.
**$ sudo apt-get update && sudo apt-get dist-upgrade**
is what I do on every machine here, every Saturday morning.  It updates to the newer kernels, while retaining overall LTS stability.  I have no idea what the GUI patching tools do - haven't used them .... uh .... ever.

---

