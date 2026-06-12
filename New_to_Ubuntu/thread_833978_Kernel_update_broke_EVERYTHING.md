---
title: "Kernel update broke EVERYTHING"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by lolwhites on 2008-06-19
I ran the update manager today and got the new kernel. I was asked if I wanted to keep the old grub or update automatically and chose the automatic option.

When I rebooted I got the GRUB menu, but whichever option I choose, I get an error message - something about "disk not found" but I can't quote verbatim here as I'm on a work PC.

Any advice? I have a live CD if necessary.

---

### Post by PmDematagoda on 2008-06-19
Boot the Ubuntu Live CD, once you are in the desktop mount the drive with Ubuntu and post the outputs of:-
```
cat /path-to-drive/boot/grub/menu.lst
```
and
```
sudo fdisk -l
```

---

### Post by bumanie on 2008-06-19
You could try booting with the previous kernel if you still have that option in the grub menu. If that works, you can then uninstall the newer kernel via synaptic and wait and see if future kernel's work or not.

---

### Post by hortimech on 2008-06-19
I also got the new kernel,  2.6.24-19-generic, this broke my Xserver, Nvidia.
When laptop rebooted only got 800x600, got a wizard saying running in low graphics mode, reconfigured (using the wizard) to 1600x1200 using Nvidia 8 card, tested ok but will not start xserver in anything other than 800x600.
Checked the /etc/X11/xorg.conf this seems ok. rebooted and got the low graphics wizard again.
Rebooted again and this time selected the previous kernel, no wizard and 1600x1200 as before.

There would seem to be something wrong with the  2.6.24-19-generic kernel, I do not know what, but I have commented it out of my /boot/grub/menu.lst

EDIT: when I said I have commented it out of my /boot/grub/menu.lst I really meant I will, When I tried to, that is when I found out that there was at least one other problem! my keyboard layout had changed from UK to USA, the # key had moved to shift-3

DO NOT INSTALL THE  2.6.24-19-generic kernel, there may be other problems I have not yet found.

---

### Post by Harpoon on 2008-06-19
I guess misery does love company. I feel much better after having read this thread.

This kernel update borked my install, too, and in strange and mysterious ways:  nautilus hung on "creating properties window" (from a right-click on the file), and media players would crash if I attempted to add a file to the playlist, among other things.

The easiest solution is booting an older kernel.  However, in my case I found that doing

sudo dpkg-reconfigure -a

cleared up most, if not all, of the update related problems.  The upside is that doing this saved me from a reinstall.  The downside is that it is a slow, tedious, and potentially painful exercise. Approach this one with both extra time and a fair bit of caution.

---

### Post by ByteJuggler on 2008-06-19
> **hortimech said:**
> 
DO NOT INSTALL THE  2.6.24-19-generic kernel, there may be other problems I have not yet found.

Eish.  Strange. (Guess I was lucky, I've updated both my machines and seen no ill effects, [one has Nvidia gfx, other is ATI] so fortunately it's not like everyone will have problems with the update. )

:confused:

---

### Post by GavinZac on 2008-06-19
> **hortimech said:**
> I also got the new kernel,  2.6.24-19-generic, this broke my Xserver, Nvidia.
When laptop rebooted only got 800x600, got a wizard saying running in low graphics mode, reconfigured (using the wizard) to 1600x1200 using Nvidia 8 card, tested ok but will not start xserver in anything other than 800x600.
Checked the /etc/X11/xorg.conf this seems ok. rebooted and got the low graphics wizard again.
Rebooted again and this time selected the previous kernel, no wizard and 1600x1200 as before.

There would seem to be something wrong with the  2.6.24-19-generic kernel, I do not know what, but I have commented it out of my /boot/grub/menu.lst

EDIT: when I said I have commented it out of my /boot/grub/menu.lst I really meant I will, When I tried to, that is when I found out that there was at least one other problem! my keyboard layout had changed from UK to USA, the # key had moved to shift-3

DO NOT INSTALL THE  2.6.24-19-generic kernel, there may be other problems I have not yet found.

If you've manually installed nvidia drivers on one kernel, you're going to need to manually install them on the new kernel also.

---

### Post by chrisccoulson on 2008-06-19
You shouldn't need to manually install the NVIDIA drivers for a new kernel if they are installed from the official repository and all the kernel meta packages are installed. If they are all installed correctly, then everything you need should be pulled in automatically during a kernel upgrade. If the NVIDIA drivers aren't getting updated, then it's likely that you're missing a meta-package, or you're running the hardy-proposed repository (which is meant for testing), or an unsupported third party repository

---

### Post by GavinZac on 2008-06-19
> **chrisccoulson said:**
> You shouldn't need to manually install the NVIDIA drivers for a new kernel if they are installed from the official repository and all the kernel meta packages are installed. If they are all installed correctly, then everything you need should be pulled in automatically during a kernel upgrade. If the NVIDIA drivers aren't getting updated, then it's likely that you're missing a meta-package, or you're running the hardy-proposed repository (which is meant for testing), or an unsupported third party repository

By manually, i meant *manually*. Compiling it from the Nvidia website.

---

### Post by chrisccoulson on 2008-06-19
> **GavinZac said:**
> By manually, i meant *manually*. Compiling it from the Nvidia website.
Sorry, I missed that bit in your post;)

---

### Post by mvavrik on 2008-06-19
> I also got the new kernel, 2.6.24-19-generic, this broke my Xserver, Nvidia.
When laptop rebooted only got 800x600, got a wizard saying running in low graphics mode, reconfigured (using the wizard) to 1600x1200 using Nvidia 8 card, tested ok but will not start xserver in anything other than 800x600.
Checked the /etc/X11/xorg.conf this seems ok. rebooted and got the low graphics wizard again.
Rebooted again and this time selected the previous kernel, no wizard and 1600x1200 as before.


I seem to be having this same issue.  I'm running 64-bit 8.04, just as an FYI.  I'm having the exact same issue. I also tried booting into recovery mode, dropping to root, and installing the nvidia drivers. I'm being told that there is no "kernel interface" and one cannot be compiled. Here is the output from the nvidia driver installer.

[I]No precompiled kernel interface was found to match your kernel; would you like the installer to attempt to download a kernel interface for your kernel from the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: Yes)
ERROR: Unable to connect to download.nvidia.com (unknown host)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;this means that the installer will need to compile a kernel interface for your kernel.
ERROR: You do not appear to have libc header files installed on your system.
Please install your distribution's libc development package.[/I]


I installed the libc development package and attempted to reinstall the Nvidia drivers and still now success.



> You shouldn't need to manually install the NVIDIA drivers for a new kernel if they are installed from the official repository and all the kernel meta packages are installed. If they are all installed correctly, then everything you need should be pulled in automatically during a kernel upgrade. If the NVIDIA drivers aren't getting updated, then it's likely that you're missing a meta-package, or you're running the hardy-proposed repository (which is meant for testing), or an unsupported third party repository


I'm afraid that that I'm running the hardy-proposed repository, which is why the 'enabled' nvidia drivers are not correcting the issue.

---

### Post by philinux on 2008-06-19
[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

Scroll down to the paragraph on Proposed. 

I've unchecked this repo now, not good for main system. Using them in vbox though.

---

### Post by chrisccoulson on 2008-06-19
> **mvavrik said:**
> I'm afraid that that I'm running the hardy-proposed repository, which is why the 'enabled' nvidia drivers are not correcting the issue.
I'm also running hardy-proposed with kernel -19 and up-to-date NVIDIA drivers. I only mentioned the hardy-proposed repository as it might sometimes contain held-back packages and packages out of sync (I think), which might cause problems for some people - but that isn't the case at the moment. Kernel -19 from hardy-proposed has everything needed to run properly (including restricted-mopdules and backported-modules and ubuntu-modules)

---

### Post by mvavrik on 2008-06-19
> I've unchecked this repo now, not good for main system. 

I plan on doing this but am now looking for some way to "roll-back" these changes OR a way to get the Nvidia drivers working again.  

System > Administration > Hardware drivers shows that the Nvidia proprietary/restricted (*those could be incorrect labels*) are enabled as they should be.  However, my resolution is still 800x600 and this change seems to have affected all kernel versions.  Thanks for the information though.

---

### Post by philinux on 2008-06-19
> **mvavrik said:**
> I plan on doing this but am now looking for some way to "roll-back" these changes OR a way to get the Nvidia drivers working again.  

System > Administration > Hardware drivers shows that the Nvidia proprietary/restricted (*those could be incorrect labels*) are enabled as they should be.  However, my resolution is still 800x600 and this change seems to have affected all kernel versions.  Thanks for the information though.

Try nvidia-settings first
If that dont work then..
Reboot and press esc at grub stage 1.5. Choose recovery mode. A menu will appear. Choose xfix. This is supposed to be the new xorg reconfigure.

---

### Post by mvavrik on 2008-06-19
> Try nvidia-settings first
If that dont work then..
Reboot and press esc at grub stage 1.5. Choose recovery mode. A menu will appear. Choose xfix. This is supposed to be the new xorg reconfigure.

Unfortunately, I have tried both those things; I could acces NVIDIA settings but remember receiving an error due to the drivers (exact wording unknown right now) and also tried recovery mode and choosing xfix, which did not resolve the issue.  I did not however "press esc at grub stage 1.5" and I must say I'm not familiar with this.  What I did was choose the "recovery" kernel from the grub menu, which I tried for the ...19 kernel and the ...18 kernel.

---

### Post by philinux on 2008-06-19
Ah, if I understand you , try booting with the 18 kernel not its recovery mode.

Are you running the the nvidia driver from the repo or the driver from nvidia.com?

---

### Post by chyneymon on 2008-06-19
Whew! fist off - thanks to finally posting this. i thought I was the only one in panic after kernel -19. My screen resolution and video drivers were messed up. I went into low-graphics mode and I couldn't choose anything higher than 800 x 600.After some fiddling around I found that this worked for me:

A manual re-install of the nvidia drivers 173.14.05 from the website. After this, I was able to manually reconfigure the resolution the screen (and choose higher resolutions). but I found that when I rebooted I was still in a lower graphics setting than usual. So then I went to System --> Preferences --> Screen Resolution and was able to select the native resolution of my lcd panel (1680 x 1050). Try it out, hope it helps.

---

### Post by mvavrik on 2008-06-19
> Ah, if I understand you , try booting with the 18 kernel not its recovery mode.

Are you running the the nvidia driver from the repo or the driver from nvidia.com?

I have tried booting to non-recover kernel 18 & 19 with no luck.  I'm running the nvidia driver from the repo and also tried to install the driver from 'recovery' manually which did not work.

> After this, I was able to manually reconfigure the resolution the screen (and choose higher resolutions). but I found that when I rebooted I was still in a lower graphics setting than usual. So then I went to System --> Preferences --> Screen Resolution and was able to select the native resolution of my lcd panel (1680 x 1050). Try it out, hope it helps.

I have tried that as well but my monitor shows up as "undetected" and I cannot raise my resolution.  I did notice that when I reinstalled from 32-bit to 64-bit, I had much less nvidia functionality available to me such as (Nvidia utility was minimal, lmsensors didn't pick up GPU temps, and that sort of thing)

---

### Post by philinux on 2008-06-19
cat /proc/driver/nvidia/version

Just to be sure post the output of the above.

And I'd run this. Then log out then in

sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by mvavrik on 2008-06-19
I'll post the driver version and run the command above, tonight.  Unfortunately I didn't boot my machine this morning so I can't connect to it remotely to do these tasks.  Could you recommend the next step if > sudo dpkg-reconfigure -phigh xserver-xorg doesn't work?

Thanks for the help so far.

---

### Post by mvavrik on 2008-06-19
!

---

### Post by QCompson on 2008-06-19
I guess I'm going to hold off upgrading to -19 then.  It seems like I just upgraded to -18.

---

### Post by philinux on 2008-06-19
> **QCompson said:**
> I guess I'm going to hold off upgrading to -19 then.  It seems like I just upgraded to -18.

I'm running 19 here just fine. I had to recompile my nvidia driver though.
But thats the case with every kernel update for me.

---

### Post by Sef on 2008-06-19
> I guess I'm going to hold off upgrading to -19 then. It seems like I just upgraded to -18.

If everything is working fine for you, it is fine not to.

I did upgrade to -19 and all went well, but I know that is not everyone's experience.

---

### Post by mvavrik on 2008-06-19
> thats the case with every kernel update for me.

I've upgraded from kernel .16 through .18 without any problems but .19 goofed up the nvidia drivers for me.

---

### Post by gnrathon on 2008-06-19
its strange, with every kernel update my computer seems to get fast and performs better

at first with the pre-installed kernel that comes with the intitail ubuntu install
i got very glitch graphics  and it was impossible to use screensavers

but now with the update everything works absolutely fine.

So perhaps it all just depends on your system.

---

### Post by mvavrik on 2008-06-19
Does anyone know of a way to "roll-back" changes that were made through Symnaptic?  For example, could I "undo" the .19 kernel update?

---

### Post by stchman on 2008-06-19
> **lolwhites said:**
> I ran the update manager today and got the new kernel. I was asked if I wanted to keep the old grub or update automatically and chose the automatic option.

When I rebooted I got the GRUB menu, but whichever option I choose, I get an error message - something about "disk not found" but I can't quote verbatim here as I'm on a work PC.

Any advice? I have a live CD if necessary.

Amazing, I had the kernel update on three machines and no problems whatsoever.

Also I recommend that you use startupmanager and not manually edit your menu.lst file.

---

### Post by hortimech on 2008-06-19
For all those who said that you need to reinstall the Nvidia drivers when a new kernel is installed, WHY?
I started with -16, went to -17 then -18 without reinstalling the drivers, but it would seem that the -19 kernel has problems for some people, just rolling back to -18 got me back to a usable resolution, I just had to set my keyboard layout again and turn on compiz again.
If I did nothing other than using an earlier kernel to cure the problem, it follows that there is something wrong with the latest kernel.

---

### Post by mvavrik on 2008-06-19
> ust rolling back to -18 got me back to a usable resolution, I just had to set my keyboard layout again and turn on compiz again.

That makes sense but how exactly do you "roll-back" to .18?  I've tried booting to the .18 kernel but the .19 kernel update seems to have affected that as well.  

Thanks.

---

### Post by lolwhites on 2008-06-19
OK, have now got back from work and can give some more details:

When I boot, the GRUB options are:
> Ubuntu 8.04.1 2.6.24-19-generic
Ubuntu 8.04.1 2.6.24-19-generic (recovery mode)
Ubuntu 8.04.1 2.6.24-18-generic
Ubuntu 8.04.1 2.6.24-18-generic (recovery mode)

The Windows XP option that used to be there has gone (it's a dual boot).
Unfortunately, whichever option I choose, I get:
> Error 21: selected disk does not exist
I can still boot with the Live CD, mount the partitions

* cat '/media/disk/boot/grub/menu.lst'* gives this:
> #hiddenmenu
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=cdfc1bc0-d14b-4b48-ad24-7bb40ec2ccde ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=2

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=false

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=cdfc1bc0-d14b-4b48-ad24-7bb40ec2ccde ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=cdfc1bc0-d14b-4b48-ad24-7bb40ec2ccde ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-18-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=cdfc1bc0-d14b-4b48-ad24-7bb40ec2ccde ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-18-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=cdfc1bc0-d14b-4b48-ad24-7bb40ec2ccde ro single
initrd		/boot/initrd.img-2.6.24-18-generic

### END DEBIAN AUTOMAGIC KERNELS LIST


*sudo fdisk -l* gives:

> Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x38673866

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7649    61440561    7  HPFS/NTFS
/dev/sda2            7650       29647   176698935   83  Linux
/dev/sda3           29648       30401     6056505    5  Extended
/dev/sda5           29648       30401     6056473+  82  Linux swap / Solaris


Any advice?

EDIT: I managed to replace the menu.lst file with one of the backups while working from the Live CD and now it seems to be working fine. I'll be back if I find anything's broken though!

---

### Post by mvavrik on 2008-06-19
> **philinux said:**
> cat /proc/driver/nvidia/version

Just to be sure post the output of the above.

And I'd run this. Then log out then in

sudo dpkg-reconfigure -phigh xserver-xorg


The output of the command is:
[I]cat /proc/driver/nvidia/version
cat: /proc/driver/nvidia/version: No such file or directory[/I]

---

### Post by mvavrik on 2008-06-19
This is confusing.

1. I boot to the .19 kernel recovery option.
2. I select the 'fix xserver' option.
3. Then I select the 'fix broken packages option'
4. I then 'resume boot as normal' 

and wouldn't you know it, it boots with 1024x768 resolution.  When I restart and boot into the .19 kernel normally, same problems again (low resolution and the screen is "cut" and shifted)

Is there anywhere to specify which .conf file xserver uses when booting to a certain kernel?

---

### Post by hortimech on 2008-06-20
This is similar to what happened to me, if I boot with the -19 kernel I get the "ubuntu is running in low graphics mode" dialog. If I then run "reconfigure" ( or is it configure? ) from the dialog, I can test at 1600x1200 but only get 800x600 when the desktop is started. If I now reboot and select the -18 kernel from the grub menu list, it starts normally. Nothing is changed but the kernel hence the problem must be the kernel.
I have now commented out the two entries for the -19 kernel in my /boot/grub/menu.lst reset everything and am now not having any problems.
It is my opinion that the -19 kernel is fatally flawed somehow and cannot recommend it to anybody.

---

### Post by Rorke on 2008-06-20
OK, I thanked you in advance. You said 'If I manually installed drivers before, I'd have to do it again' Can you explain how? Both my setups are really new, and I can't remember how to do stuff like that. I think I screwed one of my systems with 19 and some proposed releases.
I have 'No proprietary Drivers' listed by the hardware drivers menu.

---

### Post by nickpaton on 2008-06-20
Just for the record, also had a problem when installing -19 kernel.

specs:  HP NX6125 laptop, AMD CPU, Radeon graphics, broadcom wireless.

Running 7.10 i386 desktop.

Found that wireless was broken.  Sure it can be fixed by the usual methods, but just posted this to let others know.

Many thanks to you all for the hard work in working on improving Ubuntu.   It's a great testimony to you as to how few problems there have actually been over the years. :)

Nick

---

### Post by mvavrik on 2008-06-20
I feel a little ashamed, but I did a fresh install last night.  Three days and no solid workaround to get these .19 kernel issues resolved is too much for me.  I would like to say that the forum members have been very helpful...Thank you!

---

### Post by hortimech on 2008-06-27
Just an update to this, its FIXED for me, how I hear you saying, well I just waited until who ever sends out the updates, got round to sending the other half of the updates to go with the first half:mad:

Could I please make an heart felt plea to who ever sends out the updates:

PLEASE, PLEASE, PLEASE, if the update has the word KERNEL in it, please make sure all relevant updates are ready and send them out together:rolleyes:

---

