---
title: "Can't mount live session from USB flashdrive"
date: 2013-02-10
forum: New to Ubuntu
---

### Post by WorBry on 2013-02-10
Hi,

I've never used Linux before so please bear with me. Trying to 'test-drive' Ubuntu 12.10 from a USB stick. Couldn't use a DVD as my CD/DVD drive has packed-up. 

I've installed the bootable ISO on the stick (2GB Cruzer) using the Pendrive Universal USB installer. Had to change the file format from Fat32 to Fat for my PC to recognize it. 

Upon booting, it started off OK and got to the Welcome screen with the option to Test or Install. After selecting Test, the timer thingy rotated for a bit and then went to a black screen showing just the mouse cursor. I left it like that for maybe 20 monutes, but no change, other than the cursor disappearing. 

Tried it on another PC (Dimension 3100, all Intel components) and it worked perfectly, as also did the ISO burned on a DVD. 

Tried the same with Mint 14.1 Cinnamon. That got a bit further. The welcome screen gave me the option to Launch which I did (hoping it wasn't actually installing). The screen with the big green Mint Logo and some tabs (whatever it's called) opened up. But as soon as I clicked a tab (Mozilla for example) the screen locked (displaced mosaic sort of pattern) and text starts to appear, the first of which I recall saying 'Failed to idle channel 1'. I try and exit and it just displays more 'Failed to idle..." this and that. 

Again, when I tried it on the Dimension, everything went perfectly. 

Here are system hardware details of my Pc. It was was custom built around 8 years ago.

Motherboard: MSI (Via) KT4AV 
CPU: Athlon AMD XP2800+ (2.09GHz, 166MHz FSB)
RAM: 2 x 512MB DDR-400 (PC-3200) set to 166MHz bus.
GPU: nVidia GeForce FX5200 128MB (on AGP with 256MB aperture) 
HDD: 80GB WD Caviar IDE 

Reading around, it seems this issue often crops up with PC's using nVidia GPU's. So, I'm wondering if this is a graphics driver issue. 

If so, is there a distro/version that might be better suited to my system. I don't want to give up, but there seems little point in installing if there are going to be the same issues. 

Thanks a lot.

---

### Post by Sealbhach on 2013-02-10
Definitely it sounds like it's the graphics card, it's an old one. The driver you need is not on the Live CD, you have to install it after you get to a full working desktop. 

You need Nvidia driver 173.14.35. See details and how you can get it [here]("http://askubuntu.com/questions/153915/how-to-install-drivers-for-nvidia-geforce-fx-5200-on-precisehttp://").

There is a splash screen during normal bootup, which might be causing problems. You can disable the splash screen by pressing and holding down Shift at the start of the boot. This will bring up the grub menu.

Press "e" to edit the first line and change the part that reads 

```
splash quiet
```

to

```
nosplash noquiet
```

Then press Enter to continue to boot as normal. Hope that helps.

.

---

### Post by grahammechanical on 2013-02-10
If that advice does not work try

1) Press Enter at the first purple screen
2) Press Enter to select English at the next screen
3) Press F6 and scroll down the list and select nomodeset. Press Enter.
4) Press F10 to boot.

Regards.

---

### Post by WorBry on 2013-02-10
> **Sealbhach said:**
> Definitely it sounds like it's the graphics card, it's an old one. The driver you need is not on the Live CD, you have to install it after you get to a full working desktop. 

You need Nvidia driver 173.14.35. See details and how you can get it [here]("http://askubuntu.com/questions/153915/how-to-install-drivers-for-nvidia-geforce-fx-5200-on-precisehttp://").[/QUOTE

OK, thanks but I don't quite get the other part:

[QUOTE=Sealbhach;12502807]There is a splash screen during normal bootup, which might be causing problems. You can disable the splash screen by pressing and holding down Shift at the start of the boot. This will bring up the grub menu.

Press "e" to edit the first line and change the part that reads 

```
splash quiet
```to

```
nosplash noquiet
```Then press Enter to continue to boot as normal. Hope that helps.

.

By 'normal bootup', do you mean after installation, or is this something that can be applied when booting for a 'live' try-out. And I'm not too sure which splash screen you are referring to and when to press and hold Shift. 

Immediately after the device boot, there is:

1. Purple screen with two icons at the bottom, rectangle and man figure. Pressing Shift does nothing. 
2. Then the purple screen with the Ubuntu logo and the pulsating red dots underneath.  
3. Followed by a screen with swirling purplish-yellow pattern.  
4. Then the 'Try" or 'Install' window appears. 
5. Clicking 'Try' leaves swirling pattern screen again, with rotating timer, for a short while before the screen goes black with just the cursor.  

On the other PC (where it worked), the black screen lingered for just a short while before opening up the desktop. On my PC it just stays black. The only thing that changed it was pressing Ctrl-Alt-Delete and then Enter, which brought up another screen for remote log-on (requesting User and Password) which thankfully had a shutdown button at the top. 

So, at what point exactly should I press and hold Shift?

---

### Post by WorBry on 2013-02-10
> **grahammechanical said:**
> If that advice does not work try

1) Press Enter at the first purple screen
2) Press Enter to select English at the next screen
3) Press F6 and scroll down the list and select nomodeset. Press Enter.
4) Press F10 to boot.

Regards.

Thanks. Tried that, but, after selecting nomodeset, pressing F10 did nothing.

---

### Post by C.S.Cameron on 2013-02-10
1GB RAM is minimal for Ubuntu, you might give Lubuntu or Xubuntu a try.

---

### Post by Sealbhach on 2013-02-11
[QUOTE=WorBry;12503231]
By 'normal bootup', do you mean after installation, or is this something that can be applied when booting for a 'live' try-out.[ /QUOTE]

Yes, I meant at the live try out. But you won't be able to install the driver onto the live CD, any changes will be lost on a reboot. But at least you could determine whether it is just the splash screen that is causing the bootup to halt.

.

---

### Post by Sealbhach on 2013-02-11
> **WorBry said:**
> 
By 'normal bootup', do you mean after installation, or is this something that can be applied when booting for a 'live' try-out.



Yes, I meant at the live try out. But you won't be able to install the  driver onto the live CD, any changes will be lost on a reboot. But at  least you could determine whether it is just the splash screen that is  causing the bootup to halt.

.

---

### Post by WorBry on 2013-02-11
Ah, OK, so that's the Grub menu. No, disabling the splash screen didn't help either. 

Tried Lubuntu and it did load OK, so maybe it is RAM related. I'd recently upgraded the the other PC (Dimension) from the original 512MB DDR2 to 2GB. My old box, with original 2 x 512MB DDR-400 (PC-3200), can take up to 3GB DDR-333 (PC-2700), but I don't know if it's worth throwing money at it to change out the memory. Ancient motherboard and AGP graphics card and no prospect to upgrade the CPU. 

I'll maybe give Xubuntu a try also. 

Cheers.

---

### Post by WorBry on 2013-02-11
Just a couple of other questions: 

Presently I'm running XP Pro SP3. My principal reasons for wanting to try linux are:

1.  Security: freedom from Ant-Virus, Ant-Spyware and Firewall overheads,  updates and malware scans. Ditched the memory hogging Internet security  suite provided by my ISP, in favor of free Avast AV, Comodo Firewall and  Malewarebytes in reserve. That's about the lightest, least obtrusive  combo that works. Is it correct that linux doesn't need AV and  Anti-Spyware, and what about Firewall, is that built in?

Edit: Ah, OK, the Lubuntu FAQ explained that:

[https://help.ubuntu.com/community/Lubuntu/Setup#Applications](https://help.ubuntu.com/community/Lubuntu/Setup#Applications)
 
2.  Smoother ad-free web-browsing. Firefox runs with XP on my box OK, but  pages with images are still fairly slow to load and YouTube videos are  rather jittery. The Chromium browser that comes with Lubuntu is  definitely smoother even when mounted off the USB stick. Presumably though there would be the option to try other browsers?
 
3.  Seeing if it can provide better playback of HD video content  (AVCHD/Bluray). Best I can achieve at present is with MPC-HC player  using FFDShow codecs and some tweaks. VLC doesn't do very well, at least  on my XP machine. Aside from installing the linux nVidia driver, any  recommendations for the optimum player/codec set-up as a starting point -  I could maybe get into tweaks once I'm more familiar with the system.

Otherwise, I'm not too bothered about other features - office etc. 

I  have just one 80GB WD IDE hard-drive and given the price of new IDE  drives (gig-for-gig nearly twice that of SATA) I am not too keen on  installing a second drive just to run linux. Most of my docs I store on  external USB drives. A couple of things that concern me about installing  linux along side Windows (XP) are:

1. Reports of not being able to boot into Windows from the Grub menu.
2.  Presently I use Acronis True Image 2013 to backup (full disc partition)  Windows. I don't think it can handle both Windows and linux, correct? I  know linux has it's own back-up application - Clonezilla - but I'm  thinking, if I decided that I wanted to go back to just XP, would I be  able to restore from an Acronis partition back-up without any problems? 

Cheers.

Edit: Here's a thought:

[http://www.pclinuxos.com/forum/index.php?topic=95904.0](http://www.pclinuxos.com/forum/index.php?topic=95904.0)

Do you think this might be possible with any of the 'light' distros?

---

### Post by Sealbhach on 2013-02-12
Bluray is a locked down format, you won't be able to play Bluray DVDs in Linux, at least not without a lot of messy hacking requiring at least 40GB of disk space, Most other codecs are fine, you don't need to worry about those except Silverlight. 

You don't need to run antivirus, but from time to time you can do a virus scan with ClamAV, if you want to.

There are lots of other browsers you can try: Opera, Midori, Qupzilla, Arora, Rekonq... Personally I use Firefox with Adblock and NoScript Add-ons. The NoScript Add-on cuts down on loading unnecessary  page elements I don't want to see.

My suggestion would be to get a bigger USB stick, about 8GB or so, and install Ubuntu directly onto the USB, just as if it were a normal hard drive. That way you can run Linux normally, access files and documents in your Windows installation (copy them over to the USB), save a lot of your files and data on the USB stick, doing all this while leaving your main Windows XP installation unchanged.

.

---

### Post by WorBry on 2013-02-12
Thanks for taking the time to reply. 

I wasn't thinking about playing Blurays from disc as such (no way I'd install a Bluray drive in this old box). Rather to playback x264 encoded AVCHD (some Blu-ray compliant) video files (mkv and mp4), mostly home video (no rips). 

Yes, installing on an external USB drive might be an alternative. Saw the prescribed method for USB sticks:

[http://ubuntuforums.org/showthread.php?t=1872303](http://ubuntuforums.org/showthread.php?t=1872303)

Presumably, this could be applied to an external USB HDD drive as well. I have a spare USB2.0/Firewire 40G Lacie drive that I'm not using for much. Shame I can't boot from firewire - it would probably be faster. No PCI-E slot on this machine either, so no prospect of upgrading to to USB 3.0. There are IDE - SATA interface adapters (some bidirectional) that theoretically allow SATA hard-drives to be connected to IDE slots, but apparently they are rather hit and miss. So, I'll maybe give the USB 2.0 a shot. 

Main reason I'm using this old PC is that my laptop (Dell Inspiron 1420) died recently by reason of nVidia GPU defect meltdown. I'm thinking to maybe try and replace the board with an Intel GPU integrated version...can be done. Would void the Dell OEM Vista edition, but would be perfect for running linux.  

One other thing I've noticed whilst playing around in the try-out Live environment. Tried 'installing' some additional apps (e.g. VLC player) using Software Center. Looks like it's starting to download but then 'Failed to download package files - check internet connection'. What's all that about? I'm connected on home LAN through an ADSL gateway. No problem with the connection. 

Cheers.

---

### Post by Sealbhach on 2013-02-12
> **WorBry said:**
> 

One other thing I've noticed whilst playing around in the try-out Live environment. Tried 'installing' some additional apps (e.g. VLC player) using Software Center. Looks like it's starting to download but then 'Failed to download package files - check internet connection'. What's all that about? I'm connected on home LAN through an ADSL gateway. No problem with the connection. 

Cheers.

That can only mean the connection to the server you are downloading from has been disconnected. You could try changing to a different server, you can do that (I think) from the Software Centre by looking at the repositories and doing a "Select best Server" test. See [this]("http://www.hecticgeek.com/2012/10/try-this-fix-if-ubuntu-software-repositories-are-slow/").

.

---

### Post by WorBry on 2013-02-13
Well I've tried installing Lubuntu on the Lacie 20GB USB external drive and it works perfectly well with the Dimension (3100) PC (I'm writing from it just now), but (wouldn't you know it) not on my machine. 

The installation process appears to start but just at or slightly after the point of 'configuring system locales' the installation window' closes and the little timer just continues endlessly - I left it for an hour, just to see if it would eventually complete. Tried with and without installing the updates/3rd party apps option, but no difference. 

I'm tempted to think again that it might be some hardware/driver issue, but the installation doesn't even get as far as the hardware configuration part. 

What to try next? Guess I could try it on a USB stick, but I suspect it wouldn't be any different. 

Thanks.

Edit: Just wondering. Looking at the processes during installation, at one point it appears to removing a lot of unneeded packages. Would I be right in thinking that it actually loads full blown 'Ubuntu' first and then cuts it back to whats needed for Lubuntu? If so, could be the memory capacity thing again?

---

### Post by WorBry on 2013-02-13
Watched the installation process again and it's actually failing at the point of 'configuring apt..." just after 'configuring system locales'

Tried also unplugging my logitech webcam before powering up. No change.

Why would configuring APT files present a problem - surely it does that during the 'live' tryout session doesn't it - so why would it be a problem during installation. 

Having absolutely no clue how to troubleshoot this issue, I've run out of try-this-and-thats.

---

### Post by Sealbhach on 2013-02-13
Maybe it's running out of disk space or something?

Sometimes it works better if you install from the Minimal CD. It's low graphics and installs just a minimal system which you can add to later. 

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

So if you install just the base system and shut down, when you start up again, you get only a command prompt, no visible desktop. You could then get a full desktop by doing

```
sudo apt-get install lubuntu-desktop
```Which will install everything you need.

You could also experiment, try adifferent desktop

```
sudo apt-get install xfce4
```See how that works.

---

### Post by WorBry on 2013-02-13
Can't see how it could be disk space as it installed without any problems when I used the other PC (Dimension); I partitioned and formatted the drive in exactly the same way. 

Just got a 16GB USB stick to try instead of the external USB HDD with exactly the same result. 

I might add that I've now hooked up a USB CD/DVD drive and have been installing from the burned DVD ISO; I got fed up finding that after exploring the 'live' mount on a USB stick the PC would no longer find the boot files on the stick on a re-boot; I dunno, something corrupted. It did it on the Dimension PC also, so it wasn't just my PC misbehaving. 

So, I'll maybe try installing from USB stick to UB stick and see how that goes; I read somewhere (I think this forum) that apt configuration issues can arise when installing from DVD to USB; something to do with the CD file structure. 

Well, if no joy with that, I'll give the minimal CD a shot. 

Thanks again.

---

### Post by WorBry on 2013-02-14
Same issue with USB stick to USB stick install, and also with Xubuntu.

So, I'm giving the 'alternate CD' installation a go. I've got to the partitioning/formatting stage and have opted for 'Manual'. 

Can't see any option though for selecting 'device for bootloader installation' or is that not part of this 'base system package'. Just want to make sure that Grub2 doesn't get installed to the MBR of the internal HDD. 

Cheers.

Edit: Rats, it's at the end of the installation and requires typing in the device /dev. Didn't note it down, so left blank and of course now can't boot. So, I'll run it again. But at least the system installation did go to completion, which is progress....I hope.

Thanks for your help.

Edit: Rather than re-installing (takes a good deal longer than a 'normal' install), am I right in thinking that Grub2 can be added to the existing installation? I guess I would need to do that from the installation CD (or maybe the Lubuntu CD) but how?

---

### Post by Sealbhach on 2013-02-14
Yes, you can reinstall Grub from a Live CD at any time using the chroot method. See [here ]("http://ubuntuforums.org/showthread.php?t=1581099")for details. 

.

---

### Post by WorBry on 2013-02-14
Great, thanks.

---

### Post by WorBry on 2013-02-14
OK, so rather than trying to assimilate and probably mess up the Croot thing I decided to completely re-install the 'base system' from the Alternate CD (on DVD).

First, as I had done before, loaded Lubuntu 'Live', went to GParted, selected the USB drive, unmounted each partition, created a new partition table and set up the partitions again. So, it was set-up for a new installation. I noted that the USB stick was designated /dev/sdb. Shut down and removed the DVD.  

I then booted the 'Alternate CD' DVD (with the USB stick still connected) and chose to install with command line. Installation starts etc etc. When it gets to the segment for partitioning/formatting, I again choose Manual. What surprised was that the screen showed the USB stick on top as dev/sda and the internal hard below as dev/sdb. (Strange, as whenever I tried the 'normal' Lubuntu installation (from DVD or USB), it always showed the internal HDD first as dev/sda and the USB stick as dev/sdb) Anyhow, I set-up the formats and insertion points as the screen showed, and then when (an hour later) it got to the final Grub configuration, what else could I do but enter 'dev/sda' as the device to install to. So, the installation completes. On re-boot I hit F11 to pull up the Boot Menu just to make sure the USB stick was still recognized and select to boot from it. Nothing. Black screen with the flashing prompt at top left hand corner. Same thing if I just let it re-boot.  

Man, what's the problem now. Of course, I'm wondering (horror of horrors) whether Grub has actually been loaded on the internal HDD. So, I re-boot from the HDD - no grub menu, just boots to XP as normal. So it surely must be on the USB stick?   

So, I read around and come across several posts saying that problem is because the USB stick gets designated as the second drive (hd 1,0) in the Grub directory (on the stick) and that it requires editing the directory to make it the first boot drive (hd 0,0). Don't really understand why it would do that. 

[http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html](http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html)

I checked the BIOS and it is set to boot from the USB stick before the internal HDD. This said, no matter what I set to be the first boot device, the BIOS always seems to re-instate the Floppy Drive as the first device. Is that maybe the problem? Regardless, the methods described for changing the Grub directory include steps that are beyond me. 

And then this sdb vs sda thing. When I checked the designation of the USB stick after the installation, Lubuntu 'Live' (Gparted) showed it to be dev/sdb. So why did show as dev/sda during the installation. Only thing I can think of is that the Alternate CD installation consults the BIOS boot order and shows the USB stick as the first drive, whereas a 'Live' CD session consults Grub (on the CD) which reports the internal HDD as the first drive. That figures, because if, when loading the 'live' CD, I select boot from the first drive, it boots the internal HDD to Windows. 

So if Grub on the USB stick (assuming it's there) likewise defaults the internal HDD as the first drive, I can see how the boot would go nowhere. BIOS finds and queries MBR on the USB stick as the first (BIOS set) device, but Grub says No, the internal HDD is the first device....and so the boot argument continues. Is that how it goes?  

So, how does a novice like me confirm that Grub is indeed installed, and then how to resolve this first-boot device issue (hd 1.1) vs (hd 1.0)....if that is indeed the issue.

I'm at the point of giving up.....at least for today. 

Sorry to be so verbose. As my avatar declares, I'm still at the level of 'spilling the beans'. :wink:

Edit: If it's of any relevance, this is how I set up the partitions when I prepared the 16GB USB stick for installation:

After using Lubuntu 'Live' (GPart) to unmount the previous (flawed) installation and create a new partition table I allocated partitions to the unallocated space as:

First (primary partition) - 7000MB - unformatted 
Second (primary partition) - 2000MB - unformatted  
Third (primary partition) - 2200MB - linux swap  (based on the understanding that the Swap partition should be around 2x the RAM capacity) 
Fourth (primary partition) - what remained - formatted as Fat32. 

When it came to the installation :

First partition - formatted to 'journaling....Ext4' with mount point set to  \  
Second partition - formatted to 'journaling....Ext4' with mount point set to \home 
Third partition - no change - Swap
Fourth partition - tempted to leave alone but thought it best to set to Fat32 again with no mount point. 

And when it came to configuring Grub I was careful to enter just the device path (dev/sda) not the first partition. 

Did I do something wrong? 

I'd post a screen shot of what it now looks like but don't know how to screen capture from Lubuntu 'Live'.

---

### Post by WorBry on 2013-02-15
Seems this User had the same issues as me:

[http://ubuntuforums.org/showthread.php?t=1536330](http://ubuntuforums.org/showthread.php?t=1536330)

My PC (as old as it is) definitely does boot from USB (with legacy USB devices enabled), and booted from the Lubuntu 'Live' ISO on a USB stick perfectly well, so why not the installed system? What does the Pendrive USB installer do to the boot-loader that makes it work?

I might add also that the 18GB USB stick is a regular Lexar USB2.0 'jump drive' - so there were no fancy-pants (launchpad, security, back-up) applications on the disk that could have caused trouble, and surely anything like that would have been wiped off when it was re-formatted?

Aha, If I look at the USB stick, as it is now, in XP Disc Management it shows:

The 7000MB (6.84 GB) primary partition that the linux \ was mounted to, as a Volume (E:) Healthy(Active), but no format
The 2000MB (1.95 GB) primary partition that the linux \home was mounted to, as Healthy (Unknown Partition) - no format
The 2200MB (2.15 GB) primary partition that the linux-swap was mounted to, as Healthy (Unknown Partition) - no format
The remaining 3.69 GB primary partition that was formatted, as Fat32 as just Healthy

What's more it states that each of the four partitions has 100% free space!!! Yikes. The Alternate CD CLI installer did appear to complete the process ending with the re-boot prompt, and nothing has been installed on the internal HDD. So, was it somehow wiped? 

Edit: Checked again from the Lubuntu 'live' and GParted confirms it is there on the stick:

/dev/sdb 14.62GB

/dev/sdb1   ext4 Capacity: 6.84GB Used: 955.17MiB **Flagged: boot **(I assume that means it has been correctly flagged as the boot sector)
/dev/sdb2   ext4 Capacity: 1.95GB Used:66.37MiB
/dev/sdb3  linux-swap Capacity: 2.15GB
/dev/sdb4  fat32 Capacity: 3.69GB Used:7.36MiB

So it must surely be a Grub issue?

Out of curiosity though I'm wondering why the Fat32 partition has 7.36MiB used as I did not select it for any mount point during the installation. Yet it has a path:

/media/lubuntu/9372-DAC3

What's that about? Maybe because it's mounted in the Lubuntu 'Live' session? I was thinking of maybe reformatting that partition as ext4 or maybe fat16 so see if made a difference, but if there are system files there I don't want to mess it up. 

Again, sorry for this meandering diatribe, but I'm really grasping at straws trying to deduce where the problem lies.

---

### Post by oldfred on 2013-02-15
BIOS do not always report drives in same order. It may depend also if already plugged in or plugged in after boot. You just have to keep track of where it is.

Windows does not 'see' Linux partitions, so it is normal for it to be blank when viewed from Windows. 

Since you have nVidia and it may have not seen the Windows install to add that to grub yet, you could be booting thru the grub menu and hitting the nVidia issue. You have to add nomodeset with nVidia to boot. 

From BIOS select to boot flash drive and from BIOS hold shift key down and you should get grub menu. Then press e on Ubuntu entry and replace splash quiet with nomodeset.
       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by WorBry on 2013-02-15
Just to be clear, this is the 'minimal CD' base system that I've just installed on the USB stick (I wrongly referred to it before as 'Alternate CD'). I've actually just run the whole installation again, this time with just two partitions - a single ext4 partition for the \ system mount and a swap. No change. 

I've tried holding the Shift key down when booting from the USB drive (selected from Boot Menu - F11 on my PC). I get the same black screen as before, except that now there is text GRUB before the flashing prompt at the top left corner. No Grub Menu as such. 

It's not possible to key-in any text after the cursor. Tried pressing a variety of keys (Return, Escape, Shift etc). The only thing that changes it is a Ctrl-Alt-Del to reboot. 

The BIOS still has the USB stick set before the internal HDD in the boot order. Tried unplugging other USB devices (external USB CD-ROM, USB printer), and disabling the internal HDD in the BIOS boot devices, but no different. 

What to do?

---

### Post by oldfred on 2013-02-15
If you install minimal, you should just get terminal login, no gui. But that would avoid any graphical issues.
You have to install everything as minimal just is enought to boot and to get on line to download whatever apps you want.

---

### Post by WorBry on 2013-02-15
I wonder if this is an issue with the motherboard not being able to read the boot from an ext4 format partition:

[http://ubuntuforums.org/showthread.php?t=1878994](http://ubuntuforums.org/showthread.php?t=1878994)

When I was first trying to boot the Ubuntu 'Live' (ISO) from a USB stick using the Pendrive USB installer, I recall it failed initially and required pre-formatting the stick as plain old FAT, instead of Fat32. 

So, maybe it's the same issue now with the installed 'minimal system' on the stick - it needs a FAT partition to boot from. 

Any suggestions for how that could be done simply - without getting into all of the advanced code/patching stuff. Way over my head at this stage. Don't care having to re-install if it's simply a question of setting up a FAT partition and assigning the Boot sector to it during installation. 

Otherwise, I'm getting nowhere.

---

### Post by WorBry on 2013-02-15
> **oldfred said:**
> If you install minimal, you should just get terminal login, no gui. But that would avoid any graphical issues.
You have to install everything as minimal just is enought to boot and to get on line to download whatever apps you want.

That's what I've done. The install on the stick is the 'minimal system'. 

I just don't seem to be able to get as far as the terminal log-in. Just this black screen immediately after boot with a flashing cursor (plus the words GRUB, if I hold down Shift) that goes no-where and doesn't allow any key text entry.

---

### Post by oldfred on 2013-02-15
If you just have grub then it is not booting and grub is not correctly installed.

Is it grub> or grub rescue>  ?

Does this show anything?

       ls #lists partitions

---

### Post by WorBry on 2013-02-15
I'm sorry, I am an absolute beginner and do not understand what you are asking. 

To summarize my long winded posts. 

I am trying to install a working linux distro on a USB drive. When I first tried out Ubuntu and Mint I was unable to even mount the 'live' environments on my PC. 

Due to the RAM limitations of my PC (1GB DDR) it was suggested to me that I try a 'lighter' distro - Lubuntu or Xubuntu. 

The Lubuntu 'live' environment loaded satisfactorily, but when I came to try and install to a USB drive (flash or external HDD) it would not complete (aborted at the apt configuration step). Possibly this involved hardware issues (nVidia GPU?), I don't know. But it was suggested that I try installing the 'minimal' system first and then install the desktop. 

So that is what I am now attempting to do. The 'minimal' installation (from the Mini ISO CD) appears to complete satisfactorily but there is now a problem booting to the system; as I described, on booting the USB device, the Grub menu does not appear, and it is not possible to proceed beyond a black screen showing only a blinking prompt. Shift only brings up the same screen with the text GRUB, but no menu. 

The reasons for this are unclear. Is it a problem with the Grub installation/configuration or is it a problem with the BIOS not being able to read the installed boot instructions on the USB drive.   

My only intervention in the installation of the Grub boot-loader was to choose that it be installed on the USB device, which I believe I did correctly. I have now repeated the installation several times over, with the same result. 

Since it was possible to boot the Lubuntu 'Live' (ISO) from a USB stick, the PC is clearly capable of booting from USB. However, this required the USB stick format t be changed from Fat32 to Fat before the ISO was installed on the USB stick with the Pendrive USB Installer. So I am logically wondering whether the boot directory of the 'minimal system' likewise needs to be installed in a FAT partition in order for the BIOS to boot.  

I have no idea how to trouble shoot this problem and am hoping for advice on how to do so in the simplest terms possible. 

I thoroughly appreciate the advice I have received thus far and hope that once I have gained some experience with a working system I will have a better understanding of both the terminology and basic methods. But for now, I remain a new born......or perhaps more accurately a 'still born'.

Thanks.

---

### Post by oldfred on 2013-02-15
Are you installing from one USB flash to another or from a CD/DVD to the flashdrive. Are you doing a full install or an installer.

       Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

    
If a full install. 
If only a 16GB flash drive I would not partition it other than / (root) and swap. You have to install grub to the MBR of the flash drive. For grub boot flag is not required but a few BIOS will not let you boot without a boot flag, so it usually is a good idea to have one on a primary partition.

You should just be able to install Lubuntu. 

If you are trying to install an installer version or liveCD version then that formats the drive as part of the install.
LiveCD install
       Also instructions for CD/DVD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

    
       Full install of 12.04 to USB device C.S.Cameron post #5
[http://ubuntuforums.org/showthread.php?t=2060493](http://ubuntuforums.org/showthread.php?t=2060493)

---

### Post by WorBry on 2013-02-15
> **oldfred said:**
> Are you installing from one USB flash to another or from a CD/DVD to the flashdrive. Are you doing a full install or an installer.

Installing from DVD burned ISO to USB stick. As I mentioned, the full Lubuntu install stalled (at the apt configuration step). The Minimal CD install is from the DVD burned mini.iso. 

    > **oldfred said:**
> If a full install. 
If only a 16GB flash drive I would not partition it other than / (root) and swap. You have to install grub to the MBR of the flash drive. For grub boot flag is not required but a few BIOS will not let you boot without a boot flag, so it usually is a good idea to have one on a primary partition.

That's exactly how it was set-up last two times I tried to install. 

> **oldfred said:**
> If a full install.You should just be able to install Lubuntu. 

For some reason it fails (as per above).

> **oldfred said:**
> If you are trying to install an installer version or liveCD version then that formats the drive as part of the install.
I know, but one guide I read advised that it made things easier to set up the partitions using GPart first, and then it's just a question of formatting and setting the mount points during the installation. Does it make any difference?

> **oldfred said:**
> Also instructions for CD/DVD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

    
       Full install of 12.04 to USB device C.S.Cameron post #5
[http://ubuntuforums.org/showthread.php?t=2060493](http://ubuntuforums.org/showthread.php?t=2060493)

Thanks. I'll have a read through. Just trying another install - this time to an external USB HDD, to see if it does better.

---

### Post by WorBry on 2013-02-15
SUCCESS !!!!! The 'minimal CD' install to the USB External HDD worked and booted as it should. So I've logged on and am now ready to get the full Lubuntu desktop from the command prompt. Now should I enter:

```
sudo -i apt-get install lubuntu-desktop 
apt-get dist-upgrade 
apt-get autoclean 
rm /var/cache/apt/archives/*.deb 
reboot
```As stated on the 'Minimal CD' information page:

[https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall)

or just enter:

```
sudo apt-get install lubuntu-desktop

```as SealBHach suggested earlier in the thread

BTW - during the 'minimal' installation, I selected NO (default) for security auto-updates, as recommended in the guide on the 'Minimal CD' page.

Edit: I did the full post-install autoclean etc reboot thing. OK, so it works. Whoopie. First impressions - desktop is a bit slow running off the external USB HDD, but web browsing is definitely smoother than FireFox in XP. Smooth videos on YouTube. Only thing is something somewhere had knocked out my USB HP Photosmart printer when I booted to XP, although that wouldn't be diffucult. Had to re-install. Hope that's not going to be an ongoing conflict.

So, I guess the problem with the install on the USB stick is bootloader issue. I'd still like to resolve that as the Lacie external HDD is a bit of a pain to use. Requires plugging into power and runs quite hot over a period of time. Whether a USB stick would be faster or slower I've yet to see....possibly faster for small files. Maybe install an IDE internal drive if I can find one cheap.

---

### Post by Sealbhach on 2013-02-16
Good to hear you got somewhere with this. You ought to be able to use the USB stick in exactly the same way you use the USB hard drive, as long as you have enough space on the stick.  Working from a USB will be somewhat slower than from a normal hard drive or SSD.

Maybe as you get more expertise you will figure out what was wrong.
.

---

### Post by WorBry on 2013-02-16
Thanks.

Yes, this 'boot' issue with the USB stick installation is really bugging me. 

I ran exactly the same installation routine on my wife's PC (the Dimension 3100) and it booted perfectly from the same USB stick, as did the installation that I had prepared on my own PC (obviously didn't let it load beyond the Grub menu). 

So, it's not the stick or the installation and has to be a particular querk in the way my PC's BIOS handles USB boot instructions. 

I was able to boot the Lubuntu 'Live' ISO on a USB stick (tried it again with this stick). In that case, I used the Pendrive Universal USB Installer which uses the SysLinux bootloader. 

If I could just find a step-through procedure (simple enough for me to understand) of how to get Syslinux working with Grub, I'm sure it could be done. I know it has something to do with pointing Syslinux at menu.1st in the Grub folder, but stuff like this:

[http://ubuntuforums.org/showthread.php?t=1387725](http://ubuntuforums.org/showthread.php?t=1387725)

Totally over my head at this point. 

Meanwhile I'm trying few other hit-and-miss things like mounting the boot directory in a separate partition and then trying different file formats - ext3 didn't work, tried to mount on Fat32 and Fat16 but the partitioner wouldn't allow it. I'm trying ext2 just now. Just stabbing in the dark really.

---

### Post by WorBry on 2013-02-16
Is this not the magic formula I so fervently seek:

[http://jasonwryan.com/blog/2012/07/09/syslinux/](http://jasonwryan.com/blog/2012/07/09/syslinux/)
[I]
Ridiclously easy[/I], apparently. 

So, I assume by that I should be able to install the said Syslinux Pacman utility on the Lubuntu installation that I currently have working on USB external drive and from there edit the 'unbootable' one on the USB stick? 

Can but try. 

Wow, so that's what 'Grub' looks like under the microscope. My lawn is infested with those things and now I'm putting them in my PC as well? :biggrin:

---

### Post by Sealbhach on 2013-02-16
Heh, seems like you have some kinds of bugs in your hardware. :D

Anyway, pacman is the name of the package manager in the Arch distro, it is the equivalent of apt-get or aptitude in Debian  based systems. it's not really anything to do with syslinux.

I think you may already have syslinux installed, if not you can get it by

```
sudo apt-get install syslinux
```To view the manual for syslinux or any other package, do

```
man syslinux

```though it might be easier to follow a guide on the internet. 

I don't think that how-to that you linked to will work on an Ubuntu system, only Arch. I just checked and I don't have a syslinux.cfg on my system anywhere.

.

---

### Post by WorBry on 2013-02-16
Yes, in fact the several articles I've come across about replacing Grub2 with syslinux were all about Arch. I'm sure it can be done but there's no way I could translate those routines into Ubuntunese.

Seems to me (at least) that probably a better way to do it would be to install the 'mimimal system' (again) without installing Grub2 (no idea how to do that, as the CLI installer doesn't give the option) and then install Syslinux afterwards, along the lines of the method used for creating a bootable 'live' USB stick from the ISO.  

[https://help.ubuntu.com/10.04/installation-guide/i386/boot-usb-files.html](https://help.ubuntu.com/10.04/installation-guide/i386/boot-usb-files.html)

As I understand, Syslinux requires a Fat16 partition. Possibly the new USB disc did have one (at some point), but I suspect after all the re-partitioning and formatting it's probably wiped. Still, creating one, at the same as setting up the partitions for the linux system, would be straightforward. 

Putting Syslinux on the Fat16 partition likewise seems quite straightforward. 

Where I come unstuck is how to create a syslinux.cfg configuration file that points to the system binary (kernel). The procedure given in the above 'USB installer' guide obviously refers to installer ISO image whereas I'm looking to configure it to load an installed system.  

I'm sure it's quite straightforward, just can't figure it. 

I'm just wondering also if it's really necessary to not install Grub2 or uninstall it for Syslinux to work. Surely SysLinux would simply override Grub2 and so it could probably be just left there?

BTW - I've just checked and I do have the syslinux and mtools packages already installed.

---

### Post by WorBry on 2013-02-16
Here we go, I think this is a step in the right direction:

[http://shallowsky.com/linux/extlinux.html](http://shallowsky.com/linux/extlinux.html)

Obviously, however, this describes a method for installing syslinux (extlinux) on a system that is actively running.  In my case I want to be able to apply these commands to the system directories of another device (the unbootable USB stick) from within an actively running system (Lubuntu running off the USB external HDD). Again, I'm not sure how you would do that.

And then, where does this Fat16 partition come into it. No mention of that in this guide, just that on installation it automatically creates a directory /boot/extlinux, at least in Deban. 

OK, I'm confused again.

---

### Post by WorBry on 2013-02-23
Finally came to the conclusion this is a BIOS issue. Bought a refurbished 150GB IDE HHD for just a little more than the 16GB USB stick cost. The installed minimum system plus Lubuntu desktop boots and works fine.    This said, I have been looking at other distro options. Tried the Mint 14 xfce and whilst the installation (from Live CD) stalls at exactly the same point as Lubuntu did, it does at least work in the 'live' environment (as a mentioned at the start of this thread - when I tried Mint 14 Cinammon 'Live' it always froze-up).   As far as I can tell there is not an equivalent Mint 'minimal CD', but I'm if it would it be possible to install the Mint 14 xfce desktop on the (ubuntu) 'minimal' system? Might be a crazy question, but I thought I'd ask.  Also came across this 'unofficial' LMDE Xfce version     [http://forums.linuxmint.com/viewtopic.php?f=61&t=122592](http://forums.linuxmint.com/viewtopic.php?f=61&t=122592)

---

### Post by WorBry on 2013-02-25
Found a solution for the 'installation hang' problem when installing 'full' system (Ubuntu or Mint) from the 'Live' CD, at least on my PC.  Removed the ubiquity slide show that plays (or tries to play) at the start of the installation (after copying over files and the user configuration sequence). In doing so there were no hangs and the install completed as it should. Evidently having the slide show play at the same time as the installation placed too great a demand on resources.   Can't really understand why it's put there anyway, when there is opportunity to explore the system in the 'live' environment before deciding to install. There should at least be an option to disable it.

---

