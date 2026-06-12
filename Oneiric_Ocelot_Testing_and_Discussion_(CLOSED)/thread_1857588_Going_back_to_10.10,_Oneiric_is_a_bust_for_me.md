---
title: "Going back to 10.10, Oneiric is a bust for me"
date: 2011-10-10
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by crjackson on 2011-10-10
I stupidly expected that since Oneiric worked great for me in the LiveUSB enviourment, that it would work just as well doing a full install. It doesn't!

To make matters worse, I backed up using DeJa Dup and some of the packages (archives) were borked and I could't recover. Long story short I lost A LOT of data.

Back on 10.10 now, if anyone knows how to make this thing work with an nVidia 8800 let me know.

Some things I tried.

I dropped to the recovery terminal and updated everything - No Joy!

I booted with "nomodeset" - No Joy!

I installed nvidia drives from the terminal - No Joy!

I'd really like to figure out how to make this thing work if anyone wants to offer some help.

Thanks...

---

### Post by madjr on 2011-10-10
i wonder why it seemed fine in the live usb environment

---

### Post by kansasnoob on 2011-10-10
> **crjackson said:**
> I stupidly expected that since Oneiric worked great for me in the LiveUSB enviourment, that it would work just as well doing a full install. It doesn't!

To make matters worse, I backed up using DeJaVu and some of the packages (archives) were borked and I could't recover. Long story short I lost A LOT of data.

Back on 10.10 now, if anyone knows how to make this thing work with an nVidia 8800 let me know.

Some things I tried.

I dropped to the recovery terminal and updated everything - No Joy!

I booted with "nomodeset" - No Joy!

I installed nvidia drives from the terminal - No Joy!

I'd really like to figure out how to make this thing work if anyone wants to offer some help.

Thanks...

I'm especially curious about the cause of your data loss. Could you explain further?

---

### Post by BigSilly on 2011-10-10
You have the same graphics card as me OP (my 9800 is essentially a re-badged 8800), and I've been fine with it. Funnily enough though, the issues you list sound like the ones I had with the last release, and I ended up having to switch away for a while because I could not get it to work.

When you are installing, did you check the box to include non-free software? I made sure I ticked this box and it gave me the Nvidia proprietary by default, and I've been fine with it. I haven't had to do any tweaking. Was it a beta or the daily you installed? Did you check the MD5Sum of your download? It might just be worth waiting till the final is released or try a daily.

---

### Post by spsf on 2011-10-10
I have a 8600 GT here, no problems with video...
Installed nvidia drivers too!
However I dumped ubuntu and moved to xubuntu

---

### Post by crjackson on 2011-10-10
> **madjr said:**
> i wonder why it seemed fine in the live usb environment

I can't explain that myself...

---

### Post by crjackson on 2011-10-10
> **kansasnoob said:**
> I'm especially curious about the cause of your data loss. Could you explain further?

One or more of the archives created was corrupted I suppose. It tossed an error trying to read, and when I tried to open the file with the archive manager it told me it was corrupted.

---

### Post by crjackson on 2011-10-10
> **BigSilly said:**
> You have the same graphics card as me OP (my 9800 is essentially a re-badged 8800), and I've been fine with it. Funnily enough though, the issues you list sound like the ones I had with the last release, and I ended up having to switch away for a while because I could not get it to work.

When you are installing, did you check the box to include non-free software? I made sure I ticked this box and it gave me the Nvidia proprietary by default, and I've been fine with it. I haven't had to do any tweaking. Was it a beta or the daily you installed? Did you check the MD5Sum of your download? It might just be worth waiting till the final is released or try a daily.

The install source is fine, I've used it on 2 other systems without issues.

Yes, I ticked all the boxes...

I'm guessing it's a graphics card issue since it threw these errors.

* stopping automatic crash report generation [fail]

* starting load fallback graphics devices [fail]

* starting LightDM display manager [ok]

and it just hangs at the last entry forever. Perhaps it's not the graphics adapter but I believe it's related.

---

### Post by crjackson on 2011-10-10
> **spsf said:**
> I have a 8600 GT here, no problems with video...
Installed nvidia drivers too!
However I dumped ubuntu and moved to xubuntu

Well, I'd really like to get this worked out so that all of my systems are running the same OS. I have 2 more upgrade, but they have ATI cards. Since I can't trust the results I get using the LiveUSB, I'm hesitant to even try now.

---

### Post by crjackson on 2011-10-10
I'm open to suggestions...

---

### Post by ventrical on 2011-10-10
> **crjackson said:**
> I'm open to suggestions...

Download the Beta  and burn it to CD.

You will have to get synaptic from terminal after install.

---

### Post by MAFoElffen on 2011-10-10
> **crjackson said:**
> The install source is fine, I've used it on 2 other systems without issues.

Yes, I ticked all the boxes...

I'm guessing it's a graphics card issue since it threw these errors.

* stopping automatic crash report generation [fail]

* starting load fallback graphics devices [fail]

* starting LightDM display manager [ok]

and it just hangs at the last entry forever. Perhaps it's not the graphics adapter but I believe it's related.
Have you tried to boot into tty text and install GDM... Maybe its a problem loading LightDM(?)  Depending on how old the ISO was built... 
Mine here, I had 3 test boxes that had problems booting on lightd until recently.  Until then, that;s where they were crashing.  Those 3 work great on today's daily using lightdm.

Instead of fixing from your USB, maybe dl today's daily?  Just a suggestion.

---

### Post by effenberg0x0 on 2011-10-10
Ok, lets start from the beginning and try to understand what is going on there. 

**1) Boot to Recovery** **/ Seeing & Editing Grub Boot Options.**
I believe you can boot, since you said you tried "nomodeset" into grub kernel line, right?
If this is correct, let's boot to **Recovery Mode** and work from there. 

All you have to do is** reboot** your system, **hold shift to see grub**, and press the letter **"e"** over the recovery option. This will edit the recovery option, so can have a look at what we're about to boot. Make sure it looks like this:

```
linux   /boot/vmlinuz-x.x.x-xx-generic root=UUID=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx recovery nomodeset

```If your recovery kernel line has these options (recovery rnomodeset), press **ctrl+x **and let it boot.

**2) Recovery Options** **/ Root Shell With Networking**
Eventually the screen will ask you what you want to do in recovery.
You'll choose to drop you [B]to a root shell prompt with networking.
[/B]
[B]3) Checking the Blacklist
[/B]Lets make sure your VGA card is not blacklisted before proceeding. You should see no output from the next command. 
```

cat /etc/modprobe.d/blacklist.conf | grep -i nvidia
```If you do have some output from the previous command, run...
```
sudo nano /etc/modprobe.d/blacklist

```...and remove the line that says anything about nvidia. Press Ctrl+X, Y, <enter> to Save and Exit.

**4) Purging Video Drivers**
Let's purge the current video drivers we can find in this machine, before we proceed with a correct installation of new ones. This is the safest way to make sure things have a better chance of working.
 
You shouldn't have any Graphical Session running in recovery and, unless some other things got messed up, you probably don't. But, just to be safe, run these commands:
```

sudo service gdm stop
sudo service lightdm stop
sudo killall -s KILL /usr/bin/X

```At this point, we can safely go ahead and remove video drivers. Run the following commands:
```
sudo apt-get remove --purge nvidia* fglrx*

```APT will warn you that it is about to remove packages. Proceed if its listing is of nvidia-* packages and ATI packages.

**5) Updating / Upgrading your install**
Before we proceed to a install of the driver, I wanted to reboot your system. Again, this is just a "let's do things the safe way" procedure. Since we're rebooting, lets take advantage of that and update / upgrade BEFORE the VGA Driver setup. 
```
sudo apt-get update && sudo apt-get upgrade

```Let APT run, download the packages and install them. when it is finished, we will boot again to recovery.
```
sudo reboot now
```Get your finger on shift and prepare to enter grub options again.

[B]6) Recovery Mode / Installing Nvidia Drivers
[/B]Maybe the last update installed you a new kernel or changed your kernel line options. Choose the **latest **kernel recovery, which is probably under the **second** grub option, press the letter** "e"** and lets look again for the recovery line. It should like what I showed you above in step 1 (only ro, recovery, and nomodeset). You'll press Ctrl+X to boot this option and once again drop to a [B]root shell prompt with networking.

[/B]Now we could use **nvidia-current** from Ubuntu repos (the official proprietary driver), we could use **Nouveau** (the Open Source alternative) or **download Nvidia Installer** from Nvidia website. I like the Nvidia driver installer, as it does some attempts to find and locate conflicting files, etc. It's your option. At this point, as we 're trying hard to play as safe as possible, lets use Nvidia's installer.

```
cd
mkdir nvidia_driver
cd nvidia_driver
```If you are using Ubuntu 32-Bits:
```
wget http://us.download.nvidia.com/XFree86/Linux-x86/285.05.09/NVIDIA-Linux-x86-285.05.09.run
```If you are using Ubuntu 64-Bits:
```
wget http://us.download.nvidia.com/XFree86/Linux-x86_64/285.05.09/NVIDIA-Linux-x86_64-285.05.09.run
```Once the download is finished, lets run it:
```
sudo chmod +x NVIDIA*
sudo ./NVIDIA*
```Let the procedure run, answering **YES** to all questions until it exits. Let the installed make X adjustments (xorg.conf) as it asks you to. Again, **YES** to **ALL** questions.

**7) Disable Plymouth, safer "text" grub.**
I've seen reports that it is a good idea to disable plymouth and graphic  grub after VGA drivers first install / conflicts. I would trust them now and  tune my system later when everything is working better. If you concur,  do this:

```
sudo nano /etc/default/grub
```Remove "splash" and "quiet" and add "text" to the line GRUB_CMDLINE_LINUX_DEFAULT=""

Press this to save the file and exit nano:
Ctrl+X, Y, <enter>

Update grub:
```
sudo update-grub
```Reboot your system:
```

sudo reboot now
```Now, you'll let it boot or, if you want to, you can edit grubs **MAIN **line just to check that it has no weird options. Lets boot it normally, not recovery this time.

[B]8) First boot with new VGA driver 
[/B]If you get to lightdm, this is great. If not, don't panic.

**8a) No Graphical user interface after boot (stuck at console)**
- Make sure you cannot manually start a GUI session using "sudo service lightdm start".
- Switch to another VT using Ctrl+Alt+F1 to F6 if your current one don't offer you a login prompt. 
- After login, run these commands and report back the results:
```
DISPLAY=:0.0 /usr/lib/nux/unity_support_test -p
glxinfo | grep -i "direct rendering"
sudo cat /var/log/Xorg.0.log 
dmesg | grep -i nvidia
sudo ls -lah /usr/lib32/libGL*

```Try to get the error message(s) you see to here so we have something to work with.

**8b) No panel / launcher on Unity** **after Video Driver install**
- Try to follow the instructions posted here: [http://ubuntuforums.org/showthread.php?t=1856053](http://ubuntuforums.org/showthread.php?t=1856053) . You're few commands close to having a perfect Unity session.

Good luck,
Effenberg

---

### Post by effenberg0x0 on 2011-10-10
And for your ATI hardware, follow the very similar instructions posted here: [http://ubuntuforums.org/showthread.php?t=1857059](http://ubuntuforums.org/showthread.php?t=1857059)

Regards,
Effenberg

---

### Post by crjackson on 2011-10-10
effenberg0x0,

Thanks for all the great info. It's too late tonight for me to image my drive and start from scratch, but I will do this first thing tomorrow and post back with results.

---

### Post by jbicha on 2011-10-10
Please report the deja-dup backup bug. Data loss issues are taken very seriously.

---

### Post by effenberg0x0 on 2011-10-10
@jbicha I'm not familiar with Deja-dup (I use back in Time saving to a sshfs directory that is a remote mdadm RAID 5 array). 
But I was thinking that maybe he backed up files FROM a encrypted $HOME or saved backup files TO a encrypted $HOME.

Then hell broke loose in his setup, he attempts fixes, probably a reinstall, or to access his files mounting the unit from a live USB/CD etc: at this point we can't really say whether the encryption key is changed or if encryption is on/off at all. 

In such a scenario, wouldn't deja-dup look at a encrypted backup file and say it is corrupted? But in reality, it is just encrypted?

I'm just guessing / thinking of a possible solution for the OP.

Regards,
Effenberg

---

### Post by crjackson on 2011-10-10
> **effenberg0x0 said:**
> @jbicha I'm not familiar with Deja-dup (I use back in Time saving to a sshfs directory that is a remote mdadm RAID 5 array). 
But I was thinking that maybe he backed up files FROM a encrypted $HOME or saved backup files TO a encrypted $HOME.

Then hell broke loose in his setup, he attempts fixes, probably a reinstall, or to access his files mounting the unit from a live USB/CD etc: at this point we can't really say whether the encryption key is changed or if encryption is on/off at all. 

In such a scenario, wouldn't deja-dup look at a encrypted backup file and say it is corrupted? But in reality, it is just encrypted?

I'm just guessing / thinking of a possible solution for the OP.

Regards,
Effenberg

No, my machine has 4 internal HD's and 4 external USB HD's. I don't use encryption either in my home directories or in my back ups.

I backed up to an internal SATA drive that is used exclusively for backing up.

---

### Post by effenberg0x0 on 2011-10-11
Ok, this is good news. Recovering encrypted stuff after crisis oscillates between impossible and too damn difficult. If you still have this backup in a separate HDD, keep it there and safe no matter what. Once your PC is OK and running smooth, you can start to think and consider real possibilities to recover it. Maybe we can still recover your data.

Regards,
Effenberg

---

### Post by madjr on 2011-10-11
the unity test:

[IMG]http://i.stack.imgur.com/byHkO.png[/IMG]

[http://www.webupd8.org/2011/10/how-to-find-out-if-your-computer-can.html](http://www.webupd8.org/2011/10/how-to-find-out-if-your-computer-can.html)

---

### Post by GlennLChugg on 2011-10-11
I've been in 11.10 since Beta 2 and updated NVidia drivers (Proprietary) via Software Update Center every time a new version comes out:

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce GTX 460/PCI/SSE2
OpenGL version string:  4.1.0 NVIDIA 280.13

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

The only problem I had, which has since been fixed was the screen wouldn't come back after a suspended system.

Compiz was crashing a lot during the last few weeks, but over this last week it's been really stable, even running WINE games.

The first thing I did when I got to the desktop (Fresh install) was to click the Additional Hardware Drivers and pick the NVidia Proprietar, then rebooted to a much smoother Unity experience.

I do hope your problems can be solved, the more people who are using the 11.10 release, the better 12.04 LTS will be, as it's based on 11.10 and unless people offer bug reports and develop for Gnome3, Unity, we'll forever be stuck with Legacy OS's that work better for some, and thats not how a OS can progress/grow.

---

### Post by crjackson on 2011-10-11
effenberg0x0,

I followed the steps you outlined and the only problem I had was that the NVIDIA*.bin turned out to be an NVIDIA*.run file.

I never could get that file to install (yes I made executable) due to the file system reporting read only folder access (from root). I couldn't make it work

However, after doing all the steps previous to that, it loaded to a full desktop. No splash screen, it was all garbled but I was then able to you the "additional drivers" tool and installed the driver listed at the very top.

On reboot, EVERYTHING seems to work correctly including the splash screen.

Thanks for you help.

---

### Post by effenberg0x0 on 2011-10-12
Hey crjackson,  That is great! 

I'll be looking at the error you mentioned (read only folder access), thanks for the heads up. Hope you have a better experience with Oneiric from now on.

Regards,
Effenberg

---

