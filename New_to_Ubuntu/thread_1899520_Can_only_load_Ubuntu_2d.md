---
title: "Can only load Ubuntu 2d"
date: 2011-12-23
forum: New to Ubuntu
---

### Post by Justin534 on 2011-12-23
Hi everyone,

So I'm brand new to Ubuntu and Linux so you'll have to forgive me if I seem ignorant about probably everything Ubuntu and Linux related. Anyways, I'm having some problems in that when I login I can only login using the Ubuntu 2d desktop.

I first installed Ubuntu with the windows installer and everything was working great, but of course I decided to tinker with things. I noticed that under system info my graphics card was being displayed as unknown, so I wasn't sure if Ubuntu was using the card properly. I think I installed some packages following instructions from a website and now my graphics card is displayed as Intel IGD. 

However, whenever I try to login to the Ubuntu 3d desktop it just loads up the background with a horizontal bar across the top and thats it. Everything seems to work fine though when I load Ubuntu 2d desktop. Any help would be much appreciated, I would like to see if I can fix this without having to scrap everything and doing a fresh install.

Thanks and Best Regards.

---

### Post by MG&amp;TL on 2011-12-23
So...are you now using the windows installer, or have you partitioned now?

What specs are your system?

---

### Post by Justin534 on 2011-12-23
Wow, that was a quick reply...

I'm using the Asus eee 1011px netbook and here are the specs taken from CNET:

**_Processor_**
Processor Intel Atom N570 / 1.66 GHz
Multi-Core Technology Dual-Core
64-bit Computing Yes

**_RAM_**
Installed Size 1.0 GB / 2.0 GB (max)
Technology DDR3 SDRAM
Form Factor SO DIMM 204-pin
Configuration Features 1 x 1 GB

_Note:_ I upgraded to 2.0gb

**_Storage_**
Hard Drive 250.0 GB - Serial ATA-300 - 5400.0 rpm

**_Video_**
Graphics Processor / Vendor Intel GMA 3150 Dynamic Video Memory Technology 4.0

**_Ubuntu Installed_**
Ubuntu 11.10 64 bit

---

### Post by Justin534 on 2011-12-23
Also, I am still using Ubuntu that was installed via the windows installer. I get into Ubuntu by restarting the computer and using the windows boot loader to boot into Ubuntu. I'm not sure if it created a separate partition for Ubuntu or not.

---

### Post by MG&amp;TL on 2011-12-23
Wubi (Windows UBuntu Installer) does not make partitions, so you're all good. :)

I'm not sure if your 'puter will run Unity-I'd say it's probably borderline. Could you open a terminal-type "terminal" into the dash, it opens as a purple box.

Type:

```
 /usr/lib/nux/unity_support_test -p 
```

and paste the output here.

Was it running beforehand? How did you know?

---

### Post by Justin534 on 2011-12-23
Output:

OpenGL vendor string:   Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) IGD 
OpenGL version string:  1.4 Mesa 7.12-devel

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

**Was it running before?**
Yes, I cant remember what the command was that I typed into terminal but it returned "unity" instead of "unity-2d" indicating that I was running the unity 3d desktop. Also, I have to deliberately select Unity-2d when I login now as opposed to the default Unity login. When I try logging in with Unity 3d I get just the background image with a minor separation at top (where the menu bar would be). Unity 2d Also, looks slightly different when it comes to the launcher than Unity 3d. I'm sure I messed with some setting I probably shouldn't have, or maybe installed something that changed a setting. Just not sure how to figure out what happened.

---

### Post by MG&amp;TL on 2011-12-24
If I'm honest, wubi can be quite weird in terms of performance and 3d, my personal opinion is 'backup your stuff, then reinstall'-but we can try to recover if you'd rather.

I don't think you're meant to install drivers in wubi, I've never tried. Can you post a  screenshot of the 'hardware drivers' screen?

---

### Post by Justin534 on 2011-12-24
> **MG&TL said:**
> If I'm honest, wubi can be quite weird in terms of performance and 3d, my personal opinion is 'backup your stuff, then reinstall'-but we can try to recover if you'd rather.

I don't think you're meant to install drivers in wubi, I've never tried. Can you post a  screenshot of the 'hardware drivers' screen?

I was thinking of just doing a fresh install from scratch... but, I've already installed some applications and made some customizations I would like to keep. Oh well, I'm sure a fresh install might be the best way to go - or at least the easiest. I also just noticed that unity 3d works when I log into the guest account, but not my main account. Oh well.

Thanks for the tips.

[Edit] Is this the best guide for installing the latest version of ubuntu? [https://help.ubuntu.com/11.10/installation-guide/i386/index.html](https://help.ubuntu.com/11.10/installation-guide/i386/index.html)[edit]

---

### Post by grahammechanical on 2011-12-24
The Systems Info utility was newly introduced in 11.10. It is still under development. It tells me "Graphic Driver Unknown." One day this will be fixed. But I do not think that it has a high priority. There are bigger issues to be fixed first.

May I suggest that you try to put things back to the way they were before you tried to fix the "graphic driver unknown" issue? Deactivate that driver that you installed and activate the one that was being used before.

There is another thing that we can check. Did you install Compiz Configuration Settings Manager? Did you use that to try to get some special desktop effects?

I ask this because some of those Compiz special effects mess up Unity 3D. They cannot mess up Unity 2D. Compiz Settings Manager does not work on Unity 2D.

So, if you have tried to set up some special effects using Compiz Configuration Settings Manager, then while you are in Unity 2D remove those changes and then try logging out of 2D and then back into 3D.

Regards.

---

### Post by MG&amp;TL on 2011-12-24
Yeah, that guide's good, or this one:

[http://psychocats.net/ubuntu/installing]("http://psychocats.net/ubuntu/installing")

That's another thing; can you show us your compiz config if you have it?

---

### Post by gandaran on 2011-12-24
>  I also just noticed that unity 3d works when I log into the guest account, but not my main account
login using the unity 2d (not the guest account) then delete the following compiz folders
/home/'user'/.compiz-1 
/home/'user'/.config/compiz-1 
/home/'user'/.gconf/apps/compiz-1
/home/'user'/.gconf/apps/compizconfig-1
logout and then login with unity 3d
getting rid of the compiz configuration files will reset to default settings

---

### Post by Justin534 on 2011-12-24
> **gandaran said:**
> login using the unity 2d (not the guest account) then delete the following compiz folders
/home/'user'/.compiz-1 
/home/'user'/.config/compiz-1 
/home/'user'/.gconf/apps/compiz-1
/home/'user'/.gconf/apps/compizconfig-1
logout and then login with unity 3d
getting rid of the compiz configuration files will reset to default settings

Will just uninstalling compiz accomplish this as well?

---

### Post by lolpenguin on 2011-12-25
> **Justin534 said:**
> Will just uninstalling compiz accomplish this as well?

If you uninstall compiz you will break even more stuff. Running
```
unity --reset
```should reset Unity so that it works.

---

### Post by gandaran on 2011-12-25
> **Justin534 said:**
> Will just uninstalling compiz accomplish this as well?
no, removing compiz wont remove user configuration files, run the reset command or if that doesn't work delete your user compiz files

---

### Post by Justin534 on 2011-12-26
> **lolpenguin said:**
> If you uninstall compiz you will break even more stuff. Running
```
unity --reset
```should reset Unity so that it works.

...ya realized that the hard way. Anyways, I just ended up doing an uninstall through Windows and installed Ubuntu on its own dedicated partition along with a partition for a 2.0 gb swap file.

I just wanted to thank everyone for posting in this thread. I know none of you had to and all you guys were really helpful.

Thanks!

Oh ya, one more thing... I wasn't sure if Ubuntu had a built in firewall or how to turn it on. Also, what would you guys recommend as far as ant-virus software?

---

### Post by MG&amp;TL on 2011-12-27
> **Justin534 said:**
> ...ya realized that the hard way. Anyways, I just ended up doing an uninstall through Windows and installed Ubuntu on its own dedicated partition along with a partition for a 2.0 gb swap file.

I just wanted to thank everyone for posting in this thread. I know none of you had to and all you guys were really helpful.

Thanks!

Oh ya, one more thing... I wasn't sure if Ubuntu had a built in firewall or how to turn it on. Also, what would you guys recommend as far as ant-virus software?

Great! Welcome to "ubuntu proper"...

[https://wiki.ubuntu.com/BasicSecurity]("https://wiki.ubuntu.com/BasicSecurity")

Personally, I never use a firewall or AV; Linux is by nature more secure than windows, also nobody can be bothered to write viruses for it.
However, depending on what you use your 'puter for, and you rlevel of paranoia.

If I did use any; I would suggest Gufw and ClamAV.

No problem, hope you have fun. Maybe you can come back and do the same one day. :D

---

### Post by Henkdroid on 2011-12-27
Try the command :
> unity --reset
this will undo any changes you will have made to Unity 3D

---

