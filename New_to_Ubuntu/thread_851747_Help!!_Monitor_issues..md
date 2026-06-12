---
title: "Help!! Monitor issues."
date: 2008-07-07
forum: New to Ubuntu
---

### Post by LordDelta on 2008-07-07
Ok, so, I need a bit of help getting my system back to normal, without reinstalling ubuntu.

Here's my problem(s). I'm running on a Macbook Core 2 Duo, I've got triple boot setup on this machine, Mac, Ubuntu (HH), Windows, and HH is installed to an ext3 partition. Initially, everything was working fine, save some wireless stuff, but I fixed that with the ndiswrapper stuff.

Anyways, my goal in doing this is to setup a system for working on the lg3d-wonderland stuff (Java3D, Project Looking Glass, MPK20 stuff combined). So I kinda went crazy a little bit in the package manager, and being a noob at linux, I think I messed up some stuff. First, I know this computer uses an Intel GM950 or something like that as a video card, but when I was using the bootcamp driver disk for linux I noted it looked like it was doing something for nvidia and ati drivers, even though this laptop doesn't actually have either cards, so I thought it might have been doing something with virtualizations. Anyhow so one of the things I install from the package manager is the nvidia-glx stuff....and I suspect that is where my big problems began. Because shortly after, I can't use the desktop effects, which definitely worked to begin with, and other weird stuff starts happening like my transparent terminal starts showing the desktop instead of the window it is on top of. However, not caring too much about fancy effects, I just take it that something I did disabled the fancy effects, no biggy, right? 

Well, I'm trying to compile the Wonderland client, and when I run it, it complains there is no GLX support. I do a bit of googling, and searching, it seems like I have GLX installed, but something went screwy with my xorg.conf file, or I have one too many drivers, like nvidia drivers installed. So, my next steps involve doing 3 things (that I can remember, at least):

1. Removing the nvidia-glx packages that I can find when I search "glx" in the package manager
2. Adding:
{
Section "Modules"
 Enable "dri"
 Enable "glx"
EndSection
}
to the xorg.conf file
3. Some guy posted about his desktop effects not working, so I try installing something he does.

Then I restart. On booting back up, it tells me something about not being able to properly recognize the graphics card, and being in low resolution mode, so I'm stuck in 800x600 right now.

Previously, glxinfo and glxgears had been telling me something about XLib not having a GLX extenstion on device 0:0, but now when I run them, glxgears shows me gears, and glxinfo prints a bunch of stuff. So I figure this weird thing with the graphics card must be to do with this thing that I installed, which I use apt-get to uninstall, and then I reboot. However, the same screen issues persist, though the glx seems to be working. Sorta. I still have issues running the lg3d-wonderland stuff, but probably for different reasons now. Which, btw, I know works on ubuntu, I got it working on a previous installation that I managed to trash while using parted, which did something fun with the mbr I think, when I tried using it to get a fat32 partition that windows would be able to see.

So...I've decide to stop trying to fix things myself for now, I don't want to break this box anymore, and get some real help, instead of trying to guess what my problem is from other people's problems.

---

### Post by cprofitt on 2008-07-08
I do not have an intel based video card, but I know there were some issues with the i915 video chipset with resolution... that may be your issue...

do an 
```

lspci | grep VGA

```

Then search on the specific chipset it detects.

---

### Post by LordDelta on 2008-07-08
Well, the output of that command was:

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

But I think I fixed my problem. Unless it suddenly decides to revert on me again. What I did was 
sudo /etc/init.d/gdm stop
sudo dpkg-reconfig (there was more to this command, but I forget, anyways it rewrote my xorg.conf file)
sudo /etc/init.d/gdm start

And my resolution fixed itself somehow. I'm not sure if everything is actually fixed, but it seems to work for now....>_> or at least till the next time it randomly can't recognize my video card.

---

