---
title: "No Nvidia drivers seem to work on Ubuntu 11.10"
date: 2011-12-17
forum: New to Ubuntu
---

### Post by Bobblesnatcher on 2011-12-17
Hi folks,
 
As my post count will tell you, I'm new to the forums. I'm also new to Linux and Ubuntu. After a bit of faffing around I eventually managed to install 11.10 onto my **Dell Dimension 9200** desktop by updating from 10.04. Ubuntu seems to work fine but I don't seem to have any 3D functionailty. I'm assuming this is down to the fact that I don't have any drivers installed for my **Nvidia Geforce 7900 GS** card. I've made several attempts to install the drivers listed in Additional Drivers but no matter which driver I install, the end result remains the same. Ubuntu fails to start and instead I'm presented with a checklist. All of these have [OK] next to them, except for something about autocrash generating which has [Fail] next to it. 
 
By entering the terminal with Ctrl+Alt+F1 I'm able to get rid of the Nvidia driver by using the following:
 
> 
sudo apt-get purge nvidia*
sudo rm /etc/X11/xorg.conf
sudo nano /etc/X11/xorg.conf
sudo apt-get install --reinstall xserver-xorg-core libgl1-mesa-glx:i386 libgl1-mesa-dri:i386 
libgl1-mesa-glx:amd 64 libgl1-mesa-dri:amd64
sudo dpkg-reconfigure xserver-xorg
sudo reboot

 
This seems to return things back to the way they were before I attempted to install the driver. 
 
After giving up on installing the drivers from Additional Drivers, I decided to try the official Nvidia driver. I had read that these were unsupported but I didn't really have any other options. So I've tried to install *NVIDIA-Linux-x86-290.10.run *but have ended up with the same result. Before the installation of the official driver, I was prompted with an error that stated that the Nouveau Kernal driver needed to be uninstalled but that an attempt could be made by the installation to disable it.
 
Even though I've 'disabled' the Nouveau Kernal driver it prompts me with the same checklist as before. 
 
So my question, basically, is how do I install a driver for my card successfully? Am I supposed to get rid of the mentioned kernal driver completely? Is my card even supported properly? A little advice would be very grateful as so far all I've achieved has been down to me piecing things together from solutions scattered around the internet.
 
Thank you for reading and any response would be greatly appreciated.
 
P.S. 
 
Sorry in advance if I haven't given enough information about the hardware.

---

### Post by MrSpike16 on 2011-12-17
Your card is properly supported and Additional Drivers has the drivers you need and are Nvidia official drivers.  Something is probably messed up from the 10.04 to 11.04  upgrade.

You should never have to remove the Nouveau driver, but can as a last resort.  Using the Additional drivers or X-Swat repository (for latest Nvidia driver) will "take care of" the Nouveau driver for you.

Nouveau is the open source Nvidia driver in case you didn't know.
 
Lets first make sure you have the current Linux headers installed so that the Nvidia kernel module can be installed.

Find your current kernel version, can use this command in Terminal:
```
uname -r
```
Now look for the two linux-headers using Software Centre or Synaptic Package Manager which are for your current kernel version.  Install if necessary

Example (Ubuntu 10.04); 
uname -r returned 2.6.32-36-generic  so I am looking for linux-headers-2.6.32-36 and linux-headers-2.6.32-36-generic

If this isn't the problem then we will need boot log(s) or error messages with Nvidia driver installed.  I will be busy for a while so hopefully somebody can assist you with what log(s) are required if this is necessary.

---

### Post by MrSpike16 on 2011-12-17
To try the latest Nvidia driver use the X-swat repository instead of the download from Nvidia site.  

Use these commands in Terminal:
```
sudo apt-get purge nvidia*
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current nvidia-settings 
```

You don't need first command if you don't have Nvidia drivers installed.

---

### Post by alpage2 on 2011-12-17
Hi Bobblesnatcher - did the posts above solve your problem?

If not, the comprehensive troubleshooting guide that may help is in the Installation & Upgrades Forum - here:

[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

There is a lot of information there, but for installing the latest driver from Nvidea - go to the second post by MAFoElffen, where he includes links to posts which describe in detail the selecting of the correct driver, and installing the binary driver. If you follow it fully, it will start you off with cleaning out old packages, downloading and installing some additional packages needed to build the driver against your current kernel, blacklisting some other drivers which could be interfering - and then installing the new driver - all done in a terminal window, so you don't even need the graphics to be working!

If you run into any problems, or anything is not clear, post back here.

---

### Post by Bobblesnatcher on 2011-12-18
Hi guys,

Thanks for the responses. I've tried the first two posts with no success. 
>  uname -r  That told me I had 3.0.0.15-generic, so I checked the Software Centre for those headers and it only gave me the option to remove[I] linux-headers-3.0.0-15 3.0.0-15.24 and linux-headers-3.0.0-15-generic 3.0.0-15.24.

[/I]The second post gave me the same result as I mentioned in my original post with the additional failure of starting LightDM display. So I used the commands I listed previously to restore it again.

I'll try following the troubleshoot guide posted and see if that works.

Thanks for the help, I'll let you know how it works out.

---

### Post by BC59 on 2011-12-18
You are using pre-released updates and maybe that's why you have problems in the installation.
If the application for additional drivers fails, then the best way to install the proprietary video drivers is through Synaptic. If you don't have it, install Synaptic and search for Nvidia.

---

### Post by Bobblesnatcher on 2011-12-18
Hello again,

I'm still not having any luck. I followed the steps in the troubleshoot guide on how to install the latest Nvidia driver for my card and blacklist any conflicting drivers but that gave the same result. I do have Synaptic but it's a little confusing. I'm not sure which Nvidia packages I'm supposed to install.

I tried installing *nvidia-current-updates-dev *which also marked *nvidia-settings-updates *and *nvidia-current-updates *for installation. But that gave me the same results as before. I managed to get it all working again without the drivers by purging nvidia* and removing the blacklisted drivers that I added.

I'll try and install the drivers I listed in Synaptic again (unless someone knows that those are the wrong ones to install) and get a copy of the boot.log when it all goes wrong. I've found where it saves the log but I'm guessing I'll have to find it using the terminal and copy it to somewhere as I won't be able to access it in display mode.

---

### Post by jockyburns on 2011-12-18
I don't know whether this helps, but with 11.04 release, when the NVidea drivers were installed, they would show as not having been installed. The update manager used to show that the drivers had been downloaded, but not installed. Yet opening a terminal would show that they were indeed installed and working correctly. 
I would think that this bug had been fixed in 11.10 though.

---

### Post by Bobblesnatcher on 2011-12-18
When I type lsmod in the terminal it doesn't list nvidia anywhere, I can see nouveau in the list but nothing relating to nvidia.

I've managed to copy the boot log from when I installed the nvidia drivers I listed from Synaptic. I've only managed to read it using notepad through wine however. For some reason it won't open with text editor. I've included the contents below if it helps. Should I also get a copy of messages? If so, which file do I need to copy? There seem to be a lot of variations in /var/log/


> fsck from util-linux 2.19.1
/dev/sda1: clean, 305994/60678144 files, 5913040/242682112 blocks
 * Stopping Flush boot log to disk[74G[ OK ]
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
 * Starting AppArmor profiles       [80G  [74G[ OK ]
 * Setting sensors limits       [80G  [74G[ OK ]
speech-dispatcher disabled; edit /etc/default/speech-dispatcher
 * Stopping Failsafe Boot Delay[74G[ OK ]
 * Stopping System V initialisation compatibility[74G[ OK ]
 * Starting System V runlevel compatibility[74G[ OK ]
 * Stopping automatic crash report generation[74G[[31mfail[39;49m]
 * Starting eCryptfs[74G[ OK ]
 * Starting restore sound card(s') mixer state(s)[74G[ OK ]
 * Starting ACPI daemon[74G[ OK ]
 * Starting save kernel messages[74G[ OK ]
 * Stopping eCryptfs[74G[ OK ]
 * Starting anac(h)ronistic cron[74G[ OK ]
 * Starting regular background program processing daemon[74G[ OK ]
 * Starting deferred execution scheduler[74G[ OK ]
 * Starting the Winbind daemon winbind       [80G  [74G[ OK ]
 * Starting bluetooth       [80G  [74G[ OK ]
 [33m*[39;49m PulseAudio configured for per-user sessions
saned disabled; edit /etc/default/saned
 * Stopping restore sound card(s') mixer state(s)[74G[ OK ]
 * Stopping anac(h)ronistic cron[74G[ OK ]
 * Stopping save kernel messages[74G[ OK ]
 * Stopping cold plug devices[74G[ OK ]
 * Stopping log initial device creation[74G[ OK ]
 * Starting load fallback graphics devices[74G[ OK ]
 * Starting configure network device security[74G[ OK ]
 * Stopping load fallback graphics devices[74G[ OK ]
 * Starting GNOME Display Manager[74G[ OK ]
 * Starting LightDM Display Manager[74G[ OK ]
 * Starting Userspace bootsplash[74G[ OK ]
 * Stopping GNOME Display Manager[74G[ OK ]
 * Starting anac(h)ronistic cron[74G[ OK ]
 * Stopping anac(h)ronistic cron[74G[ OK ]
 * Stopping Userspace bootsplash[74G[ OK ]

---

### Post by Bobblesnatcher on 2011-12-18
Ah, new knowledge:

When I type > sudo nvidia-installer --latest it tells me I have 275.43 installed. Does that mean that the driver is working properly and I've been messing it up? If so why is it not listed in lsmod?


EDIT-- Ok, ignore what I've said above. I think what that's telling me is that the Nvidia driver is installed but Nouveau is what is being used. I've now used > sudo nvidia-installer --update to get the latest driver (290.10). Then I've updated the blacklist with the drivers listed in the troubleshoot. I've also created the files /etc/udev/rules.d/90-modprobe.rules ( RUN+="sbin etc...) and /etc/modprobe.d/nouveau-kms.conf ( options nouveau etc...). Then I've run > sudo update-initramfs -u.

It still isn't loading Ubuntu though. I've had a look at the syslog and the only references to Nvidia I can find are listed below.

> 
nvidia: moudule license 'NVIDIA' taints kernel
Disabling lock debugging due to kernel taint

nvidia 0000:01:00.0 PCI INT A-> GSI 16 (level, low) -> IRQ 16
nvidia 0000:01:00.0 setting latency timer to 64

NVRM: loading NVIDIA UNIX x86 kernel module 290.10



After all of that at the end of the log, before what I believe is me opening the console, is this line.

> 
Init: lightdm main process(1720) terminated with status 1


Does anyone know what I'm doing wrong?

---

### Post by MrSpike16 on 2011-12-18
It looks like your Nvidia Kernel module is loading OK.  Problem maybe with Xorg.

You need the "Xorg.0.log" file.    You might find an old log from when you booted with the Nvidia driver to save you some work and time.

It is possible that Xorg is looking in the wrong place for a file or something like that.

By the way you are not doing anything wrong, dist. upgrades tend to mess things up.

---

### Post by Bobblesnatcher on 2011-12-19
Am I able to copy this onto a USB drive through the terminal and then view it with notepad from another computer? That way I can copy and paste from this windows PC without undoing what I've done so far.

---

### Post by MrSpike16 on 2011-12-19
I find it much easier to use a Ubuntu CD to retrieve and view logs after a crash.  Once you are at the terminal, put in your Ubuntu CD.  Now reboot and use Try Ubuntu.  

```
sudo reboot
```For 10.04 CD click on Places and find and click on the ie; "84 GB Filesystem" type entry which will mount and open Nautilus.  You can drag and drop files to the usb drive.  For 11.10 CD (Unity), click on Home Folder, then look on left side below Devices.   Don't look in Computer > File System as this is files for your currently running OS!!.

If viewing logs in Windows use Wordpad as Notepad will be a mess (no formatting).

Grab the kern.log from the /var/log folder also.  The kern.log may contain lines from the previous boot also so look at the date/time to start viewing last boot info.

---

