---
title: "linux-image won't install (again)"
date: 2005-02-15
forum: Repositories &amp; Backports
---

### Post by Rottweiler on 2005-02-15
A new kernel was issued yesterday to fix some exploits. But it won't install:
   
    ```
$ sudo apt-get update && sudo apt-get upgrade
  [snip]
  The following packages have been kept back:
    linux-image-2.6-386 linux-restricted-modules-2.6-386
  0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
``` 
   
   So I tried installing them manually (this worked before):
   
    ```
$ sudo apt-get install linux-image-2.6-386 linux-restricted-modules-2.6-386
  Reading Package Lists... Done
  Building Dependency Tree... Done
  Some packages could not be installed. This may mean that you have
  requested an impossible situation or if you are using the unstable
  distribution that some required packages have not yet been created
  or been moved out of Incoming.
  The following information may help to resolve the situation:
  
  The following packages have unmet dependencies:
    linux-restricted-modules-2.6-386: Depends: linux-restricted-modules-2.6.8.1-5-386 but it is not installable
  E: Broken packages
``` 
   
 I went to /var/cache/apt/archives and deleted the packages thinking that might help the "broken packages" problem but no change. So how do I get this to install.?
   
 Low key rant: Every time a kernel update is released, it's the same thing like this - it won't install without alot of manual intervention. I'm in the process of deploying Ubuntu on all my servers. When I get lots of these things running this will become a real pain real fast. Is there no way a kernel upgrade can be packaged such that it will just install like everything else without so much ratkilling?
   End of low key rant and apologies for being a whiny baby.
   
   Any help appreciated.

---

### Post by WW on 2005-02-15
I had the same problem.  However, I think the packages that didn't install are metapackages.  When I upgraded, the packages that contain the actual kernel and the restricted modules were installed.  I still don't understand what's going on with the kernel metapackages and why they aren't updated.

---

### Post by drasko on 2005-02-15
Why not dowloading those packages from the net and trying dpkg -i...
Migh pass, if the dependency chain don't continues ad infinitum...

Drasko

---

### Post by s.deleeuw on 2005-02-15
The linux-restricted-modules-2.6-686 linux meta package is broken. It depends on the non-existing package linux-restricted-modules-2.6.8.1-5-686.

So people, don't upgrade until this is fixed!


Sander

---

### Post by dodongo on 2005-02-15
Sander --  Is there any easy way to rectify this situation?  Unfortunately, the only network connection I have on my Ubuntu box uses the Aetheros wireless chipset drivers, which are (evidently) contained in the linux-restricted-modules package.

Given that I can't find a way to roll back my kernel modules to an earlier version that agrees with the linux-restricted-modules package I still have installed... do I just have to run off a wired connection till this gets fixed?

*sigh*  It's my own damn fault for doing the installation... but that doesn't really make it less frustrating :)

---

### Post by s.deleeuw on 2005-02-15
Sure. Did you already remove your old kernel and restricted-modules ? If not, you can just boot your previous kernel. If you did, just reinstall both the 2.6.8.1-4-686 image and restricted-modules. That should solve your problem for now...

Sander

---

### Post by Rottweiler on 2005-02-15
[QUOTE=s.deleeuw]So people, don't upgrade until this is fixed![/QUOTE]That's easy enough to comply with since the blessed thing won't install anyway. :shock:
   
   BTW,  did you hear officially somewhere that it is broken? I could't find a bugzilla report about it.

---

### Post by dodongo on 2005-02-15
Right-O ...  I forgot there was that option.  Everything's back to good for the time being!

Thanks!

---

### Post by s.deleeuw on 2005-02-15
Rottweiler: I didn't hear it officially

Just refresh your package list in Synaptic, right-click on linux-restricted-modules-2.6-686 -> Properties -> Dependancies. Here you can see that it depends on a not-existing package. So, that's the reason why I called this package broken.

But it IS important not to try upgrading. If you boot the new kernel (which DOES install), the restricted-modules are not available. So if you own a ATI or NVIDIA graphics card, GDM will not load anymore...

---

### Post by Xian on 2005-02-15
[QUOTE=s.deleeuw]If you boot the new kernel (which DOES install), the restricted-modules are not available. So if you own a ATI or NVIDIA graphics card, GDM will not load anymore...[/QUOTE]
Just in case someone did install the new kernel and tossed their old one, you can still start X but you will need to revert your X11 config device driver notation to a pre-nvidia/ati state. For example, if you are running a nvidia driver you just need to change the driver listed under the "Device" Section of your /etc/X11/XF86Config-4 file from "nvidia" to "nv". This will allow you to boot using the updated kernel and login to gnome via gdm.

---

### Post by daniels on 2005-02-15
The problem is that some kernel security updates touch core kernel structures, which mean that all the modules linked against it have to rebuilt, and this doesn't always get done immediately; give it some time.

---

### Post by ritger on 2005-02-16
Patience is ofcourse important, however when running Warty (stable) it might be an idea to keep back the new (in this case linux-image-686) package until all dependencies are met. Is there an ETA on when the updated package becomes available?

As for anything else, Ubuntu rules :-)

---

### Post by Rottweiler on 2005-02-16
[QUOTE=daniels]The problem is that some kernel security updates touch core kernel structures, which mean that all the modules linked against it have to rebuilt, and this doesn't always get done immediately; give it some time.[/QUOTE]Thank you.
   
   But how were we supposed to know this?
   
 There was nothing in the USN that said "wait". And so-far seemingly all kernel updates have not been willing to install without a lot of manual intervention.
   
 I don't understand why this must be. I'm converting all my RH/FC servers to Ubuntu and the last thing I can endure is having to be constantly tweaking them to get updates to install.
   
   Why can't kernel updates just install like everything else? (Excepting the necessity for a reboot, of course).

---

### Post by daniels on 2005-02-16
This time, everyone tried to get everything installing smoothly as per the lessons of the past, but one more unexpected thing cropped up (specifically: they were uploaded at the same time, so when l-r-m built, linux-headers-* wasn't available).  Bear in mind Ubuntu is only young; we haven't been doing kernel security updates for years.

---

### Post by Yukonjack on 2005-02-17
[QUOTE=Xian] if you are running a nvidia driver you just need to change the driver listed under the "Device" Section of your /etc/X11/XF86Config-4 file from "nvidia" to "nv". This will allow you to boot using the updated kernel and login to gnome via gdm.[/QUOTE]

First thing I tried but it did not work for me all I did was removed the nvidia-glx and re-installed it then reboot and I was back to normal with kernel 2.6.8.1.5-K7

---

### Post by nocturn on 2005-02-17
Any news on this issue yet?  Is it safe to install the updates?

---

### Post by WW on 2005-02-17
I re-upgraded a few minutes ago, and was able to get the upgraded linux-restricted-modules packages and nvidia-glx.  So yes, it appears to have been fixed.

---

### Post by nocturn on 2005-02-23
Strange, this issue still is not fixed for me.

I tried:
aptitude update
aptitude upgrade 

again yesterday (2005-02-22), the restricted modules is still broken.

---

### Post by jflorian on 2005-11-25
Hey guys, apt-get is doing exactly what it is supposed to here.  From the man page on apt-get under the upgrade section:
_under no circumstances  are  currently  installed packages removed, or packages not already installed retrieved and installed_
So, the meta linux-image package is being upgraded, but the specific linux-image-<version> upon which it depends is a NEW package.  If you want to install new packages along with the upgrades you must:
```
sudo apt-get dist-upgrade
```
If you observe apt-get closely most packages won't mention any details about the specific version except for cases like a major release (e.g., php4 vs. php5) and in those cases you won't be seeing the number increment for an upgrade.  In other words, linux-image-a.b.c-y is not an upgrade of linux-image-a.b.c.-x.

Hope this helps.

---

