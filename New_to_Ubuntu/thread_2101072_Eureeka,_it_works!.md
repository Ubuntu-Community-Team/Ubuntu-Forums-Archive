---
title: "Eureeka, it works!"
date: 2013-01-03
forum: New to Ubuntu
---

### Post by dreamkatcha on 2013-01-03
Hi,

I finally managed to get Ubuntu to boot from my USB drive with the help of Thibaut Lauziere from the LinuxLive USB Creator site. It turns out you have to disable UEFI (known as secure boot in my BIOS) in order for it to be recognised. Problem is you can't run a multiboot Windows 8/Ubuntu system without flicking this switch on and off each time you flip back and forth between the two. If you don't re-enable it when booting Windows 8, the boot manager thinks the installation is defective and in need of repair. My jaw dropped when I first thought my installation was knackered!

Another spanner in the works for me was that I wasn't able to enter the BIOS to re-enable secure boot after installing Ubuntu because the F2 key no longer worked. This allows access to the BIOS on my Samsung laptop and also doubles as one of the brightness control buttons - you select which it operates as by toggling the function key. The thing is function key presses no longer register on boot up so unless the function key is left in the right state when you restart from Ubuntu you can't access the boot options.

Anyway, I got there in the end and I'm impressed so far. If I can manage to get my iPod Shuffle and EyeTV DTT TV tuner working under Ubuntu I'll probably ditch Windows altogether. What are my chances and what's the best software to use? Any tips would be much appreciated.

Also, if I decided to remove all the Windows and Samsung recovery partitions from my drive, would Grub detect that Linux is the only OS installed and remove Windows from the boot list option screen automatically?

---

### Post by lykwydchykyn on 2013-01-03
> **dreamkatcha said:**
> 
Also, if I decided to remove all the Windows and Samsung recovery partitions from my drive, would Grub detect that Linux is the only OS installed and remove Windows from the boot list option screen automatically?

You have to run:
```

sudo update-grub

```

...after removing the partitions for GRUB to re-detect and rewrite its menu.

---

### Post by Calinou on 2013-01-03
UEFI has nothing to do with Secure Boot, you can use UEFI without using Secure Boot. However, the inverse is not possible.

---

### Post by oldfred on 2013-01-03
Are you not able to get into your UEFI/BIOS with f2 because of this bug.

       UEFI boot live-usb bricks SAMSUNG 530U3C,np700z5c laptop - fix released
[https://bugs.launchpad.net/ubuntu-cdimage/+bug/1040557](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1040557)


If you can get into UEFI you should turn UEFI secure boot off, but still have UEFI on. Some UEFI menus seem to reverse logic as they say to use UEFI (meaning without secure boot?) and then have separate settings for secure boot and legacy/BIOS boot.


Boot-Repair will convert a BIOS install to UEFI boot, but be sure you can get into UEFI menu first.


       
 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by dreamkatcha on 2013-01-04
> **lykwydchykyn said:**
> You have to run:
```

sudo update-grub

```

...after removing the partitions for GRUB to re-detect and rewrite its menu.

Brilliant! That's so simple I think even I could cope with that, thanks. :)

> UEFI has nothing to do with Secure Boot, you can use UEFI without using Secure Boot. However, the inverse is not possible.

I stand corrected. I assumed since the legacy OS option is unavailable when Secure Boot is enabled, they must be interchangeable somehow. I've clearly spent too much time around Macs. It's been years since I've really tinkered with a PC.

> Are you not able to get into your UEFI/BIOS with f2 because of this bug.

No, I don't think that quite fits my situation and my laptop is the NP350E7C-A05UK model. I can get into the BIOS, but only if the F2 key functions as such, rather than a brightness adjuster. My Windows 8 installation hasn't actually been damaged in any way, it's just that it appears to insist on having Secure Boot enabled to run. I tried the option that allows you to operate UEFI as well as legacy OSs simultaneously, but to do this you have to disable Secure Boot and hence Windows throws a wobbler.

Oh well, my goal is to ditch Windows 8 altogether sooner or later so it's not the end of the world. Maybe Windows 7 will play nicely with Ubuntu, maybe I'll live purely in the Linux world at home.

I didn't get much time to experiment, but managed to scan some TV channels and get a picture/sound with Me-TV. It crashed the first time I ran it and on the second go I couldn't change the channel away from some tacky home shopping station. Aaaggh! Spare me!

---

### Post by dreamkatcha on 2013-01-05
Just a quick update: I worked out how to change channels in Me TV - you have to drag the top of the lower status bar upwards to reveal the EPG and then click on the channel names from there. Really bizarre decision to hide such a fundamental feature away with no visible way to access it if you ask me.

That aside, it works pretty well out of the box. It does exactly what you need it to do and nothing more, which is a nice change from some of the iTunesesque software out there.

Ubuntu really doesn't like my keyboard. I ran into some more problems with this duel key, function switch thing. I tried turning up the volume with the F8 key and it behaved as if I'd kept my finger on it after I'd let go. The volume went to the max and continued to flash. As a result menu and status bar options became inaccessible and my mouse buttons stopped working. In the end I had to reboot with the power button and use the slider bars to make adjustments rather than the F keys.

Something else I noticed is that there's a lot of uncomfortable 'tearing' as you scroll web pages in Firefox as if the display can't refresh fast enough to keep pace.

Finally I noticed there were two instances of Rhythmbox installed so uninstalled one. They both vanished and now I can't click the install button in the software centre to re-install it.

---

### Post by dreamkatcha on 2013-01-07
Well I bit the bullet, wiped all my partitions and started again intending to just run Ubuntu. I setup an Ext4 partition, a boot partition and a swap file partition, and *tried* to use the remaining space for my data. I seem to be able to run it from my hard drive, but all of a sudden the BIOS boot options have gone very flakey. Sometimes I'm able to see my USB drive, sometimes not. Sometimes my hard drive is available to select, sometimes not.

When I first booted into the OS I thought maybe I was running it from the USB drive seeing as it was so slow and there's no option in the software centre to install anything (the install button alongside applications simply isn't there). 

The other problem I'm having is that I can't format the remaining space on my hard drive to create a partition for my data. I get the message "error formatting after initial wipe: Timed out waiting for object (udisk-error-quark,0). It doesn't matter what structure I try to use, all I get is error messages.

I don't understand why everything ran so smoothly the first time round when I still had Windows 8 installed. The only thing I did differently then was to setup an Ext2 partition to install Ubuntu to.

Any advice would be much appreciated please seeing as I've thrown all my eggs in one basket with no backup. [-o<

---

### Post by oldfred on 2013-01-07
Did you install in UEFI or BIOS and did you use gpt or MBR?
Secure boot & fast boot off?

Other Samsungs:
       Samsung Ultrabook Windows 8 & Ubuntu & recovery boot
[http://ubuntuforums.org/showthread.php?t=2097690](http://ubuntuforums.org/showthread.php?t=2097690)
Samsung Series 7 - post #5 Windows 8 & UEFI, Ubuntu only to new SSD
[http://ubuntuforums.org/showthread.php?p=12382951](http://ubuntuforums.org/showthread.php?p=12382951)

    
But some Samsung have a bad UEFI which now grub has to try to work around.
       UEFI boot live-usb bricks SAMSUNG 530U3C,np700z5c laptop - fix released
[https://bugs.launchpad.net/ubuntu-cdimage/+bug/1040557](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1040557)

---

### Post by dreamkatcha on 2013-01-08
I installed in BIOS as Ubuntu wouldn't boot in UEFI. I'm not sure if it was gpt or MBR, I don't remember being given the choice. Secure Boot was off and I don't know about fast boot.

Anyway after a few reboots things seem to have settled down a bit, although I haven't tried booting from USB again since. While it's not blindingly faster than Windows 8 as I had it expected, it runs quick enough now and I'm able to install new software. I managed to format the remaining free space on my hard drive as Ext4 purely by repeating what I'd already done until it worked. I have no explanation for any of this.

With a bit of Googling I managed to find a project called Linux on my Samsung which provides modified Ubuntu packages to improve compatibility. To complete the process I'm supposed to install 'Samsung Tools' but I'm getting permission denied messages when I use the command:-

./configure
make
sudo make install

What am I doing wrong?

I really hope it offers improved CPU throttling because at the moment my fan is spinning most of the time while the computer is idling.

---

