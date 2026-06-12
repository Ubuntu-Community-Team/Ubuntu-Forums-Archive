---
title: "Help! &quot;Grub Rescue&quot;"
date: 2017-01-05
forum: New to Ubuntu
---

### Post by wfriedwaldgmail.c on 2017-01-05
what did I do wrong?  Rather than powering down, I put my ubuntu laptop into suspend mode overnight.

today, when I tried to turn it back on (it's always come back on before) I didn't get anything - I pushed the power off and on & now I get something called "grub rescue" -

"unknown filesystem" ?

help!

what do I do?

nuts! I needed this tonight for a presentation!

w

---

### Post by oldfred on 2017-01-05
Best never to force shutdown, unless this does not work. You often then corrupt file system and need fsck to repair it. Same for Windows and it needing chkdsk.

 Holding down Ctrl+Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is, and S can be before E, but others should be in order
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[https://en.wikipedia.org/wiki/Magic_SysRq_key](https://en.wikipedia.org/wiki/Magic_SysRq_key)
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274) 

      
 #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by wfriedwaldgmail.c on 2017-01-06
nuts! rats! nuts again!

this is a little complex - basically I have to create another live drive and start all over again?  there's no other way to repair the OS?

nuts!  Okay, I'm going to have to put this off for a few days at least.

rats!

(but thanks.)

w

---

### Post by oldfred on 2017-01-06
You should not have to install, just run fsck.

But if you find install easier, and have all your data fully backed up and either do not reconfigure anything then re-install may be a good choice.

---

### Post by wfriedwaldgmail.c on 2017-01-06
Thanks!

so I 
* boot from the flash drive 
* go into the terminal
* and run "sudo e2fsck -C0 -p -f -v /dev/sdb1" (I guess the prompt will tell me which partition name to use in place of "sdb1" - yes?

thanks!

w

---

### Post by oldfred on 2017-01-06
You have to either know what partition(s) are ext4 and use those or run fdisk/parted/gdisk commands to list partitions, so then you do know.
And you have to then manually edit example with your correct partitions.

Each of these should show partitions, if UEFI then gdisk will show gpt partitions. If old install fdisk may not work on new gpt partitions.
sudo parted -l
sudo fdisk -lu
sudo gdisk -l /dev/sda

---

### Post by wfriedwaldgmail.c on 2017-01-06
I am back to square one.

I thought I had created a bootable flash drive using UNETbootin.

When I stick in the Flash Drive in the USB slot, I hit F9 to get boot options:
BOOT from EFI file
Notebook Hard drive 
USB hard drive

but none of these seem to work - 

I am guessing I have to change something in the BIOS to tell it to boot from the USB drive, but I have no idea what.

(I posed this question here a few months ago, and I got an answer that worked - but now I can't find any of my forum messages that go back more than a few weeks...)

---

### Post by oldfred on 2017-01-06
Is your system UEFI or BIOS. 
If it gives UEFI boot option hardware is UEFI, but need to know if you installed in UEFI or BIOS boot mode.

You want to then boot flash drive in that boot mode.
You may have to turn off Secure Boot in UEFI and may also have to turn on allow UEFI boot from flash drive/USB ports. Settings vary by vendor so you have to review them. 
If you updated UEFI from vendor it reverts to defaults for most settings & you have to remember to redo them.

My old BIOS system had boot of flash drive underneath the hard drive boot option as another hard drive.
My UEFI boot shows multiple UEFI entries, one is UEFI:flash drive where flash drive is label or brand of flash drive.

---

### Post by wfriedwaldgmail.c on 2017-01-06
thanks again.

this is not going to be easy!

when I try BOOT FROM USB HARD DRIVE - I just get a blinking cursor in the upper left hand corner of the screen, nothing else.

it gives me the option to BOOT FROM EFI FILE 
the boot option menu doesn't say anything about UEFI anywhere.

in F10 BIOS SYSTEM CONFIGURATION, SECURE BOOT seems to be DISABLED.

LEGACY SUPPORT is also ENABLED.

I have pretty much given up on fixing the existing file system OS, I am resigned to having to re-install the whole system - I don't care about losing any data already on the machine, it's all expendable.

UEFI BOOT ORDER - here in SYSTEM CONFIGURATION - aha - USB DISKETTE ON KEY/USB HARD DRIVE is first.

maybe it's a buggy flash drive?  but I know the HP Stream 11 can at least read it ...

what to do?

thanks again!

w

---

### Post by oldfred on 2017-01-06
Is this one of the 32bit UEFI systems that was designed to be Windows only like a Apple table iPad is Apple only?
Back when designed Linux did not have a 32 bit UEFI, so they thought they had a Windows only system configuration.
And there was no reason to put a 32 bit boot loader on a 64 bit device.

 [http://h30434.www3.hp.com/t5/Windows/Linux-on-the-HP-Stream-tablet/td-p/4829188](http://h30434.www3.hp.com/t5/Windows/Linux-on-the-HP-Stream-tablet/td-p/4829188)
AMD Kaveri vs. Intel Skylake With The Latest Linux/Mesa Open-Source Drivers

---

### Post by tea for one on 2017-01-06
> **wfriedwaldgmail.c said:**
> I am back to square one.

I thought I had created a bootable flash drive using UNETbootin.

When I stick in the Flash Drive in the USB slot, I hit F9 to get boot options:
BOOT from EFI file
Notebook Hard drive 
USB hard drive

but none of these seem to work - 

I am guessing I have to change something in the BIOS to tell it to boot from the USB drive, but I have no idea what.

(I posed this question here a few months ago, and I got an answer that worked - but now I can't find any of my forum messages that go back more than a few weeks...)

Press F10 to enter Set up utility
Arrow right to System Configuration
Arrow down to Boot Options
Arrow down to Legacy Support
Change Disabled to Enabled

Save and exit

Restart and press F9 to select USB drive

Good luck

---

### Post by Geoffrey_Arndt on 2017-01-07
Herr Friedwald:

>   Just a few questions . . when putting laptop into suspend, how did you do it and was the laptop connected to power or running off battery?

>   If you're not running a dual-boot system (I don't recall you gave ANY laptop make, model or specs . . not a good start in any forum) . . . . so, if NO dual boot, then you don't need uefi mode, change totally to legacy mode.

>   Unetbootin is not a great app anymore for creating bootable usb sticks . . lots of unresolved issues.     Use something like "Etcher" instead.    [URL="https://etcher.io/"]https://etcher.io/

[/URL]

---

### Post by wfriedwaldgmail.c on 2017-01-08
(I just tried to post something and was told that it didn't go through - apologies if that missing message turns up & this is a duplicate!)

thanks again

I tried building a second uNETbootin flash drive to start up from - on the chance that the first one was buggy.  But no, the second one did not work either.  (When I try to boot from the flash drive, I once again just get a blinking cursor in the upper left corner.)

I may start a new thread - I'm no longer trying to save the existing system, at this point I'd be happy to wipe the current OS and start all over with a fresh install.

I did manage to do this about 6-7 weeks ago, I did a Ubuntu 14 install, then upgrade to 16, and it worked fine, until a few days ago, when I was stupid enough to force power off.  (stupid me!)

Again grateful for any help.

Below, some screen shots, including the uNETbootin settings, which may be useful.
(actually check the uNETbootin settings first - I do NOT have the ISO option checked - should the flash drive be an ISO?)

thanks again,

Will




 [ATTACH=CONFIG]273086[/ATTACH][ATTACH=CONFIG]273087[/ATTACH][ATTACH=CONFIG]273088[/ATTACH][ATTACH=CONFIG]273089[/ATTACH][ATTACH=CONFIG]273090[/ATTACH]

---

### Post by wfriedwaldgmail.c on 2017-01-08
PS: oh! I just saw the two messages from Tea for One & Mr. Arndt.

Legacy support seems to have been enabled all this time - even with that option on "ENABLED" I still get the blinking cursor when I try to boot from the drive.

I went into "suspend" the proper way, manually using the menu (I didn't let the timer / power save option do it automatically).  Then I let it sit overnight.  When it wouldn't turn on (the way it usually does after a few hours).  I held the power button to force it off - as I've done with the machine before (but not with the current 16.04 OS) and that's then I got the "Grub Rescue" prompt.  Now I know better!

sorry, this is an HP Steam 11 (2014 laptop) - a "saved" windows machine that I bought new...

yes, this will be just one system, happy to be instructed on how to switch totally to legacy mode.

Am happy to try ETCHER ... although I currently have no idea if the problem is uNETbootin or something in the BIOS.  (Like I say, in November I was able to get it going using uNETbootin.) will try etcher  - thanks.

one more screen shot:
[ATTACH=CONFIG]273091[/ATTACH]

thanks again to all of you - Old Fred, Tea for Two, and Mr. Arndt!

w

---

### Post by oldfred on 2017-01-08
Many vendors use the same UEFI in multiple systems with just variations for options in those models.
 Some HP will not boot a flash drive that is gpt partitioned. Some only boot from the USB2 port not USB3 ports.
[http://ubuntuforums.org/showthread.php?t=2213631&p=13468260#post13468260](http://ubuntuforums.org/showthread.php?t=2213631&p=13468260#post13468260) 

Do not know if any of these are similar?

 HP Envy - Legacy boot seems to mean either UEFI or Legacy depending on which is found to boot from
[http://ubuntuforums.org/showthread.php?t=2167063](http://ubuntuforums.org/showthread.php?t=2167063)
Installing Ubuntu on HP Envy-6  Details of what worked post #11
[http://ubuntuforums.org/showthread.php?t=2123975](http://ubuntuforums.org/showthread.php?t=2123975)
HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)

---

### Post by wfriedwaldgmail.c on 2017-01-08
okay! 

Yes!

that seems to have worked: I used ETCHER to make the boot USB flash drive and it seems to have succeed where uNETbootin failed.

okay, so far so good.

and I will NEVER leave it in SUSPEND / SLEEP mode again ... from now on I turn it all the way off when I'm not using it.

yes!

thanks!

w

---

