---
title: "Updated to Geforce GTX 750T, unable to log in"
date: 2014-12-20
forum: New to Ubuntu
---

### Post by jan_jan_64 on 2014-12-20
I bought a new graphics card today - a Geforce GTX 750TI. After reading around various places regarding how to install the drivers, which went a little over my head (I downloaded the drivers from the site but struggled to get the files to run), I found a similar thread on the help forums that said that person had used the command "sudo apt-get install nvidia-current". Since at least working in the terminal I can understand, I figured this was the best option for me. I ran the command, everything downloaded and unpackaged, and I restarted the computer. However, now I cannot get logged in - after putting in my account password on start-up, I am stuck at the loading screen. Im running ubuntu 14.04. If you need any more info let me know and I will see if I can figure out how to get it T_T Please help!

---

### Post by oldfred on 2014-12-20
While I normally suggest installing from Ubuntu's repository, it is not the most current version of nVidia drivers.

Since I was thinking of getting the 750Ti I have seen several posts.

You do need a newer version of driver than is in repository. 
There are three ways to install the nVidia driver and they often conflict. 
You can install the .run file from nVidia, but then have to rebuild manually initrd with every kernel update, so not really recommended.
You can install from Ubuntu repository which is normally recommended unless your card is not yet supported in versions available.
Or you can download from a ppa where it is pre-configured to work. And that is what you need.

You do also need to purge any previous installs. And if nVidia created the xorg, remove that also as its setting may need to be different.

Can you boot with nomodeset, or recovery mode or an old kernel. If not you may have to chroot into your install from live installer.

 Lists installed version, in/with your kernel:
dkms status
# Houseclean out all old versions to avoid issues
sudo apt-get remove --purge < nvidiadriverpackagename>
# [ using the correct names] for each driver, before running:
sudo apt-get purge nvidia*
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

      
 Maxwell 750 
[http://ubuntuforums.org/showthread.php?t=2214805](http://ubuntuforums.org/showthread.php?t=2214805)
Usually better to use PPA.
[http://ubuntuforums.org/showthread.php?t=2252908](http://ubuntuforums.org/showthread.php?t=2252908)
[http://www.phoronix.com/scan.php?page=article&item=evga_geforce_gtx750&num=1](http://www.phoronix.com/scan.php?page=article&item=evga_geforce_gtx750&num=1)

You may also need support software and newer kernel also. Not sure if one ppa is better than another. Links to several and some discussions. You will want the newest version available, so any examples with specific kernels should be adjusted to newest available.

 Updated driver search by nVidia model
[http://www.geforce.com/drivers](http://www.geforce.com/drivers)


14.04 drivers for Nvidia GeForce GT 730 desktop board - (similar issue different model)
[http://ubuntuforums.org/showthread.php?t=2240702](http://ubuntuforums.org/showthread.php?t=2240702)
PPA for nVidia mamarley pps
[http://ubuntuforums.org/showthread.php?t=2256437&p=13185945#post13185945](http://ubuntuforums.org/showthread.php?t=2256437&p=13185945#post13185945)
[https://launchpad.net/~mamarley/+archive/ubuntu/nvidia](https://launchpad.net/~mamarley/+archive/ubuntu/nvidia)
Install Nvidia 340.24 from ppa:xorg-edgers/ppa
[http://www.sysads.co.uk/2014/07/install-nvidia-340-24-driver-ubuntu-14-04/](http://www.sysads.co.uk/2014/07/install-nvidia-340-24-driver-ubuntu-14-04/)
All the current drivers xorg-edgers PPA
[https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa/+packages](https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa/+packages)
Oibaf PPA discusion
 [http://www.phoronix.com/scan.php?page=article&item=ubuntu_1310_oibaf&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1310_oibaf&num=1)
New kernels ppa
[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D](http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D)
Ubuntu Kernel Mainline PPA
[http://www.phoronix.com/scan.php?page=article&item=amd_cat144_hd56&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_cat144_hd56&num=1)
[https://launchpad.net/~kernel-ppa/+archive/ubuntu/pre-proposed](https://launchpad.net/~kernel-ppa/+archive/ubuntu/pre-proposed)
Kernel updater script - also git methods
[https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater](https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater)

---

### Post by jan_jan_64 on 2014-12-20
Thanks! There is a lot of information there, it will take me a while to digest it all... In the mean time, I can tell you that I can get to the recovery mode menu, but I am not sure where to go from there - I wanted to try the purge command from the root shell prompt, but it wont recognise my root password for some reason - if I could get a walkthrough (think like a 5 year old could understand) or if there is a known link to one, that would really help. Other than that I do not know where to go from there. The ppa route sounds the best (and simplest!) way for me right now so I will start reading up on it..

---

### Post by oldfred on 2014-12-20
If in recovery mode you have to select correct mode to have everything work. I know one mode is read only, another mode or setting is required to turn on Internet. Part of that is so you can do different repairs or change settings which may not otherwise be allowed. I have not used recovery mode for ages so not sure what changes it now has.

If you do get nVidia purged and reboot you may need nomodeset. My old system with 9600GT care would only boot with nomodeset until I installed the nVidia driver. My newer system with 620gt card does work with nouveau, but I get a bit of screen tearing only on these quick reply posts. But I have not tried movies yet with new system, but youtube works without issues.

Do you have an older kernel in grub menu and does that boot perhaps? Or can you use nomodeset on current kernel?
The chroot route is a lot of commands to type in with live installer, so best if you can at least get to a working terminal.

---

### Post by jan_jan_64 on 2014-12-20
Ah, I got access finally to the root menu on the recovery mode screen finally (I was being a retard). I want to run the purge command, but I actually dont know which driver package it was - the command I ran was sudo apt-get insteall nvidia-current... Is there a way I can find out exactly which driver was installed from the system recovery menu?

---

### Post by jan_jan_64 on 2014-12-20
Ah, I just saw your reply. Sorry, I dont even know how to operate the forums properly T_T I tried to figure out nomodeset but so far tutorials are going over my head. Ill get back to you if I figure it out...

---

### Post by oldfred on 2014-12-20
I think this just shows what verions are in repository like you would see in System Settings, drivers & updates tab.
 # list drivers available, same list as system settings,  software updates,  additional drivers or last tab
ubuntu-drivers devices

I do not yet have a nVidia driver installed but this may show it?

 dkms status
This shows card, but do not remember if details of nVidia shown:
sudo lshw | grep -A 11 display


 dpkg -l | grep nvidia
apt-cache policy nvidia-current

---

### Post by jan_jan_64 on 2014-12-20
OK. I tried to use the purge command from the root shell in the recovery mode menu. No good. I ran the commands you just gave me and yes they tell me which driver number is installed but Im struggling to match with with a package name. I have not been able to fine any tutorial I can undestand to allow me to boot in nomodeset. So im still sat at the GRUB menu unable to proceed :( any other thoughts? You have given me lots of information but I am afraid a lot of it is rather advanced for me so Im not able to follow all so well.

---

### Post by jan_jan_64 on 2014-12-20
Some relative success - I managed to remove the drivers via the recvery mode root shell menu finally \o/ although it still didnt allow me to log in. I then added an xorg ppa and ot the latest update. Still not able to progress beyond login.

---

### Post by jan_jan_64 on 2014-12-20
another update: after trying out various different tutorials on installing compatible drivers, I finally managed to actually get logged in! Im not exactly sure how. I know the drivers are still not correct, however, as the graphics are still all stretched and low res. So I suppose the big question now is - how do I find out which driver is compatible and safe, and how can I install it correctly?

---

### Post by oldfred on 2014-12-20
In post #2, use link to nVidia to find the correct driver for your card. It probably will be the newest.
And then add one of the ppa that has nVidia drivers and update.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

I have never used ppa, so not sure what it then adds. 
But my understanding is that while you can install & show nVidia drivers from Ubuntu repository it will then also include all the drivers in the ppa also.


This shows the commands for the 340 version, but you should use the newer one. I know there is at least one, maybe two newer. Not sure which may be still beta which I would not install.

[http://www.sysads.co.uk/2014/07/install-nvidia-340-24-driver-ubuntu-14-04/](http://www.sysads.co.uk/2014/07/install-nvidia-340-24-driver-ubuntu-14-04/)

Commands posted in above:

```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get install nvidia-340
```    

This also shows 343.xx & 346.xx for all current versions of Ubuntu. Plus lots of other things, some for very old video as well.
[https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa/+packages](https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa/+packages)

---

### Post by jan_jan_64 on 2014-12-20
But I already took the latest driver from the Nvidia website, that is what caused the issue in the first place. I also have made the ppa repository and it didnt do anything. I have an even bigger problem now, however - I was looking for drivers which were recommended as working with 14.04 online.  I followed the steps in the tutorial here: [http://linuxg.net/how-to-install-nvidia-334-21-on-the-most-popular-linux-systems/](http://linuxg.net/how-to-install-nvidia-334-21-on-the-most-popular-linux-systems/) and now I cant even reach the login screen. The purple ubuntu screen flashes purple for a moment, then turns to black, then takes me to the comand line screen as if I pressed ctrl+alt+F1. After trying to type in my log in details, the screen will just go blank escpet for an orange flashing cursor *sigh* I managed to turn off the xserver so Im going to assume this is because the xserver has not restarted perhaps? I tried to use the lighdm restart command but it doesnt work. I used the ubuntu-drivers devices command to see what package is installed (so I might be able to use the purge command again), and according to this there are 2 drivers - nvidia-340 and xserver-xorg-video-nouveau. Im not sure about nouveau, but what I attempted to install was Nvidia 334.21. I am now very, very confused :/

---

### Post by oldfred on 2014-12-20
Often the nVidia site version works until you get a new kernel then you have to re-run parts of it to recreate initrd file as when from nVidia directly it is not in dpkg.

While the procedure may be ok, in your link, the 334 version is older than the version in the Ubuntu repository.

And installing different versions from different sources almost always creates conflicts like you now have found.
You must purge one nVidia installed from one source before attempting to install from another source.

And it is not drivers working with 14.04, but drivers that work with 750Ti. 
Did you follow this thread which is specific to 750?
[http://ubuntuforums.org/showthread.php?t=2214805](http://ubuntuforums.org/showthread.php?t=2214805)

If it created an xorg, but you may not have one.
 sudo mv /etc/X11/xorg.conf /etc/X11/xorg/conf.old
      
 Lists installed version, in/with your kernel:
dkms status
# Houseclean out all old versions to avoid issues
sudo apt-get remove --purge < nvidiadriverpackagename>
# [ using the correct names] for each driver, before running:
sudo apt-get purge nvidia*

Are you able to boot with nomodeset, recovery mode, or an older kernel?

      
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.

---

### Post by jan_jan_64 on 2014-12-20
I read through the thread but I did not understand most of it. Unless there is a list of console commands to use/step by step instructions I am pretty lost as to how to follow it.   If I have to remove one of the drivers, which one do you think I should remove? Nvidia or Nouveau? Running "sudo mv /etc/X11/xorg.conf /etc/X11/xorg/conf.old" returns "mv: cannot stat '/etc/X11/xorg.conf". Does this mean it was not created properly? Running "dkms status" lists 4 things, all related to "3.13.043-generic, x86-64". 2 are "nvidia-331-updates". I edited quiet splash for nomodeset but so far I have not seen any difference. I am not sure what nomodeset is supposed to do, actually... I also am not sure when you say to boot with an older kernel. Again, I am very much a newbie here. Thank you for all of your help and patience so far!

---

### Post by oldfred on 2014-12-20
I mentioned you may not have an xorg file. It is now not standard. So if an error it probably is just that it was never created.

Not sure of internals, but nomodeset prevents system from switching to something that does not work. My older nVidia card always needed nomodeset since about Ubuntu 10.10 when they added something to kernel for video.

It seems then you have installed nvidia 331 which is too old for your card. You need to uninstall it.

If you boot to grub menu you get the current kernel, now the others may be in the sub-menu but you should have recovery mode so you can get into a repair terminal console if needed, and any older kernels that may not have the nVidia driver integrated into it. Sometimes then older kernel will boot.

I think the command will be 

sudo apt-get remove --purge nvidia-331-updates
sudo apt-get purge nvidia*

Then you may not be able to boot without nomodeset until newer nVidia driver is installed.

This says there was a bug in 343, so either install 340 or perhaps 346. But some of the very new nVidia drivers require the newest support software and kernels. Then it is more complicated and I cannot really help that much.

Did you read this:
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_1310_oibaf&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1310_oibaf&num=1)
```
Enabling and upgrading the open-source graphics drivers for Intel, AMD Radeon,  and Nouveau (NVIDIA) can be as easy as running [B]
sudo apt-add-repository ppa:o[/B]**ibaf/graphics-drivers && sudo apt-get update && sudo apt-get  dist-upgrade** 
It's as easy as that.
```

---

### Post by jan_jan_64 on 2014-12-20
Great, thats was really clear, thanks!  So I uninstalled 331 with the command lines you gave. After that, I rebooted and was able to log in (I changed to nomodeset a few restarts ago, I assume it is still set and helped). I ran sudo apt-add-repository ppaibaf/graphics-drivers && sudo apt-get update && sudo apt-get dist-upgrade, and everything seemed to work well, but after rebooting, I am back to the original problem - after entering my login credentials, nothing loads and Im stuck on the loading screen again...

---

### Post by oldfred on 2014-12-20
Did the nVidia driver correctly install?
Again do you need nomodeset? Or if you added nomodeset as a permanent setting you need to remove it.
Can you boot recovery mode or older kernel?

Run this again:
 dkms status
      
 ubuntu-drivers devices
            sudo dpkg-reconfigure {insert version installed}
sudo nvidia-xconfig

---

### Post by jan_jan_64 on 2014-12-21
Okay!, So - I checked the edit on the GRUB screen, after a restart it read as quiet splash again, so Im assuming it was not permanently saved. I havent been able to boot from an older kernel but still able to access the recovery menu, where I am running from tht root shell. Running "dkms status" returned two lines, "bbswitch, 0.7, 3.13.0-43-generic, x86_64: installed" and "nvidia, 334.21, 3.13.0-43-generic, x86_64: installed". Runnung "ubuntu-drivers devices" also returns two packages listed under driver, nvidia 340 and xorg nouveau again. I already removed 334 as you recommended yesterday and then ran the long command from the Phoronix forum. so it seems to have landed me back where I started again :/ I was not able to run the "purge nvidia" command as "nvidia" by itself was not recognised. I am assuming I should not still have 2 things listed here, but do not know which I actually need. I would like to run the last two command lines you gave me, but at the moment, I am not sure what package I should select for the reconfigure command.

---

### Post by oldfred on 2014-12-21
My only other suggestion is to try 14.10 or even 15.04, although it is not even to beta yet.
It is not just the video drivers but support software & the kernel. With the newer Ubuntu you get all that automatically without all the hassles of manually updating with the ppa. But support only lasts 9 months and the you have to upgrade to the next version of Ubuntu.

---

### Post by jan_jan_64 on 2014-12-21
So as far as you can see there are no errors here? Can you tell me how it SHOULD look when running"ubuntu-drivers devices"? Should there still be 2 listed? Can you tell me which driver name I should use when running the command line "sudo dpkg-reconfigure {insert version installed}"? There are 2 listed and I dont know which one to use/keep. The long command line from Phoronix had the "sudo apt-get dist-upgrade", which I already entered yesterday. Isnt that the command for upgrading?

---

### Post by JeQhdMD on 2014-12-21
If I recall correctly, another way you can verify which video drivers are installed is to use a gui package manager such as "Synaptic" (if not installed, install it from the Ubuntu Software Center).

Then you can type "nvidia" in search field, and you'll see which drivers are installed (in column "installed version").   Use that info with either the terminal (aka console) or try to uninstall via synaptic instead (not sure if that's doable, but it's worth a try)

I would also second Old Fred's recommendation to update your install (of Ubuntu to 14.10 or later) as this will provide the latest "kernel" which is the key to all of your issues.

---

### Post by jan_jan_64 on 2014-12-21
@ JeQhdMD - Although that sounds like a great idea, I actually cant get logged in to download anything, so I wouldnt be able to get Synaptic to try and fix it (Im currently reporting from an old netbook). I shall try upgrading and see if if fixes the problem.

---

### Post by jan_jan_64 on 2014-12-21
After some fiddling around, I managed to install nvidia 340 and get logged in, but the graphics are even worse than before - mega huge. I have tried running "sudo apt-get dist-upgrade" and "sudo apt-get upgrade", but each time was told there is nothing to update or upgrade. I also followed the ubuntu wki instructions and it says my software is up to date. How can I upgrade to 14.10? Also, although I installed nvidia 340, when I run "dkms status", I still get 3 things returned: "bbswitch, 0.7, 3.13.0-43-generic, x86_64: installed", "nvidia-340, 340.65, 3.13.0-43-generic, x86_64: installed" and "nvidia-340, 340.65, 3.13.0-43-generic, x86_64: installed". I assume having 3 here is no good. Or does this mean 340 is no good also?? Any spcific instructions of what to do next?

---

### Post by oldfred on 2014-12-21
Others have reported 340 works, but then that must be with a newer kernel and support software, if in 14.04 or with 14.10 or testing in 15.04.

---

### Post by jan_jan_64 on 2014-12-21
Then can you help me upgrade? As I said, I have followed the wiki instructions and used the terminal commands I know to upgrade to 14.10 but it does not seem to recognise that there is an upgrade available.

---

### Post by oldfred on 2014-12-21
I stopped using upgrades with 9.04, I did do upgrades every 6 months from 6.06 to 9.04 but had issues.
Be sure to remove all ppa first.
Back up all your data, particularly /home. Many end up having to do new install as ppa, or special drivers or applications interfere with upgrade.

       # latest stable release
sudo do-release-upgrade

See 
man do-release-upgrade

You may want to try -d or other options first.

---

### Post by jan_jan_64 on 2014-12-21
Im sorry, but I dont know how to do pretty much all of the things you just said. I shall look up how to remove a ppa. Other than transfering some files to a hard drive, I dont know how to back up my data. I only did a fresh install a few months ago - do people really end up doing a fresh install on such a regular basis? I have no idea what -d is ow what to do with it either. As stated, really newbie.

---

### Post by jan_jan_64 on 2014-12-21
I used purge ppa to remove ppa:xorg-edgers/ppa - apparently there was an error and not everything was reverted. Also in the returned lines there were some errors regarding nvidia-340 and it said the package has been removed. When I ran the "dkms status" command afterwards, only one driver is listed - "bbswitch, 0.7, 3.13.0-43-generic". So theres no nvidia driver now?

---

### Post by oldfred on 2014-12-21
I would think you have no nVidia driver. 
How did bbswitch get installed? from a ppa or from Ubuntu's system settings drivers. 
If from Ubuntu I would not expect that to be an issue.

---

### Post by jan_jan_64 on 2014-12-21
I assume its the default driver, but I mentioned it in a post yesterday already that it was listed as being installed along with the nvidia drive. Indeed the nvidia driver is gone - every time I try to run something in the terminal, I continue to get error messages saying each time that it is attempting to remove nvidia 340 and that it cannot :/ there is something veeeeery wrong. I have been trying to use the tool on the nvidia website to find out which driver is recommended for me, but it requires java and I cant even figure out how to get java running T_T My god this is turning in to such a big mess. So as it stands it seems I have the default driver installed, which makes sense considering how terrible my screen looks right now. Having nvidia 340 did not seem to work. If I reinstall 340 run your command lines for upgrading, how likely is something to go wrong? I am not sur ehow to fully back up my system and am very unprepared for major programming fallout if this does not work correctly...

---

### Post by jan_jan_64 on 2014-12-21
OK, I managed to get rid of the nvidia 340 error issue. However, when trying to reinstall, I have a problem - the instructions you gave to me install nvidia 340 was with a ppa, but to update to 14.10, you told me to remove the ppa, which then removed 340 (partially and unsuccessfully). How do I remove the ppa for upgrade whilst still keeping the driver? :/

---

### Post by oldfred on 2014-12-21
You have to reinstall the driver after the update. 

And may need nomodeset or whatever other work arounds you had. But then new version may not need as much.

---

### Post by JeQhdMD on 2014-12-22
OK, Jan, given your current circumstances, here's what I recomend:

1).   Use another computer to go to:    [http://partedmagic.com/](http://partedmagic.com/)   (thjis website provides an outstanding, user friendly tool to fix your system from many issues (but not the nvidia issue)).   Nevertheless, you should consider paying a small amount (like $5.00 or so) to get the link for the download file.   Save that file and use a good cd/dvd burning software to burn the "iso image to a standard CD).   If your other system doesn't have optical media (cd/dvd), then download the image anyway and burn the iso to  "usb flash-stick".  Several windows programs can do that, I think "Pendrive Linux" is a good one ([http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)).

2.)   Use the new bootable cd/dvd or usb flash to boot up your hosed computer.   Parted Magic will allow you to load the live linux CD to your computer's RAM . . . runs much faster & better than most live linux distros.

3).   After about 5 minutes or so, you should have a "live session" activated on your PC.   The first thing you do with this is to use the provided file manager to scan and look for your files on your ubuntu partition (this is all via the gui file manager).   You should be able to find your home directory.   Copy your important files to another usb stick.   Once all your key files are secured and copied - - then you need to get the Ubuntu 14.10 iso image that's suitable for your sytem (32 or 64 bit).   Repeat the burning process to a new disk or usb stick and you're read to do a "fresh install" of Ubuntu instead of a system or distro upgrade.

4).   Let the new system completely install (and if you don't know how to install a new Ubuntu system, let us know what your particulars are (such as dual-boot, such as what other OS, such as what type firmware (if an older system, probably uses standard BIOS, if a newer system, may use UEFI).    

5).   IF the new system won't boot to the graphical user interface (unity), then you may have to do the "nomodeset" bootup option OR install a different distro such as Ubuntu Mate or Linux Mint Mate.    Those will NOT require the nviida driver to load up a very decent useable desktop, but later you can install the nvidia drivers via the gui method for that distro.  (ask on those specifics once you're there . . . meanwhile, you have a decent useable install).

There are very good and detailed instructions online about how to do these steps at the Ubuntu site and at the other linked sites I've listed.   This is a fair amount of work, but in the end may be easier for you than what you're trying to do now.

BTW . . . the iso image files can be accessed via distrowatch (go to the distro listings and navigate to distro home pages, look for download page).   [http://distrowatch.com/](http://distrowatch.com/)
'

---

