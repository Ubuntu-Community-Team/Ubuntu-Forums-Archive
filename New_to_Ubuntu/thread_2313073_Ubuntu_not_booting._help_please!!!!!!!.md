---
title: "Ubuntu not booting. help please!!!!!!!"
date: 2016-02-09
forum: New to Ubuntu
---

### Post by bijaydeyp on 2016-02-09
Hi ,
I am new to ubuntu(14.04 lts) & Linux world.I set dual boot pc with windows 7.everything was fine until sunday.
 The problem is my pc doesn't boot into ubuntu now & shows black screen(photo 1.boot-menu, 2.black screen).then I have to switch off the power button, to start the PC again.
But I saw it boots into Windows without any problem and also into 'Advanced options with Ubuntu' >  'Ubuntu with linux 3.16.0-49-generic(recovery mode)' >  recovery menu(photo 3.boot with advanced options, 4.boot with recovery). But again, not with the 'Ubuntu with linux 3.16.0-49-generic' option.
 If I go for recovery option from bios-setup, results are same but hardly it shows this screen(photo 5.from recovery mode of BIOS-setup).look at the last line of screen. surprisingly, in this case it boots automatically & normally.I'm not understanding what's wrong with it.


can anyone help me please?    only you guys can save me!!

---

### Post by grahammechanical on 2016-02-09
From description I am not clear what the situation is. I will review it as I understand things.

1) The Grub boot menu loads - Good.
2) Selecting Windows 7 loads Windows 7 - Good
3) Selecting Ubuntu loads to a black screen - Bad.
4) Selecting Advanced options + recovery mode loads to a recovery menu - Good.

Does selecting Resume load to a login screen and a working desktop?

You have 4 versions of the Linux kernel.

> Linux 3.16.0-49
Linux 3.16.0-48
Linux 3.16.0-44
Linux 3.16.0-43

Each of those kernels has a recovery mode. Selecting Ubuntu at the Grub boot menu will load Linux 3.16.0-49 and that loads to a black screen. When we open Advanced options for Ubuntu at the top of the list is Linux 3.16.0-49. This is logical because Linux 3.16.0-49 is the latest version and after entering Advanced options we might want to load the latest kernel without backing out back to the Grub menu screen by pressing Esc.

Try selecting Linux 3.16.0-48 or -44 or -43. They are previous kernels and they worked fine. It might just be kernel 3.16.0-49 that is causing this problem. And the developers might fix the problem in a few days and send out another kernel.

To get a better idea of what is going wrong we might need to edit the boot parameters of Linux 3.16.0-49. We can do that from the Advanced options sub-menu. But first lets us get you to a working desktop.

Oh, by the way, I do not understand what you are saying when you are saying this

> If I go for recovery option from bios-setup, results are same but hardly  it shows this screen(photo 5.from recovery mode of BIOS-setup).look at  the last line of screen. surprisingly, in this case it boots  automatically & normally.

Do you perhaps have 2 hard disks. One with Windows 7 on and one with Ubuntu on? And when you say "I go for recovery option from bios-setup" It means that you are selecting a different drive to boot from? If you have 2 drives it could be that you have 2 versions of Grub. One version installed on one drive that loads Linux 3.16.0-49 which is broken. And another version on the other driver that does not have kernel 3.16.0-49 but has kernel 3.16-48 as the latest kernel and that loads correctly.

I can only guess what is happening here.

Regards.

---

### Post by bijaydeyp on 2016-02-10
@grahammechanical 
thanks for your time.


 "Oh, by the way, I do not understand what you are saying when you are saying this
If I go for recovery option from bios-setup, results are same but hardly it shows this screen(photo 5.from recovery mode of BIOS-setup).look at the last line of screen. surprisingly, in this case it boots automatically & normally."
I said so due to this photo(Booting full screen-1,Booting screen-2).look, there is a recovery option with F2 key during Booting.


 "Does selecting Resume load to a login screen and a working desktop?
ye4s.it does.
 "Try selecting Linux 3.16.0-48 or -44 or -43. They are previous kernels and they worked fine. It might just be kernel 3.16.0-49 that is causing this problem. And the developers might fix the problem in a few days and send out another kernel."
I tested each Linux kernel+ recovery mode e.g. 'Ubuntu with linux 3.16.0-49-generic(recovery mode)' option.they all working. but those without recovery mode e.g. 'Ubuntu with linux 3.16.0-49-generic' aren't working.see photo (3.boot with advanced options). that's strange!


 "Do you perhaps have 2 hard disks. One with Windows 7 on and one with Ubuntu on?"
nope.I have single HDD.


Hey, is it possible due to  'system settings' changed by mistake?

---

### Post by oldfred on 2016-02-10
Also did you install proprietary graphics driver directly from nVidia?
That is integrated into kernel, but a new kernel then does not get updated with driver.
Only if you install from Ubuntu repository or ppa does a new kernel get updated to use driver.

---

### Post by bijaydeyp on 2016-02-11
here is a brief description of the problem


I seted up dual-boot pc(windows7+ubuntu 14.04) & am using linux(ubuntu) during last 8 months only.both the OS worked fine until last sunday.
 while starting ubuntu,it loads into black screen + blinking cursor. even I tried with different kernels, no ubuntu logo, no login screen, unable to reboot.
 but it can load windows7 and different 'linux kernels with recovery mode' nicely.


Dear forum members, can anyone tell me how to fix this without reinstalling ubuntu?

---

### Post by oldfred on 2016-02-11
Recovery mode uses nomodeset, so that is why I asked about proprietary video drivers.
Nomodeset is often required with nVidia or AMD, until  proprietary driver is installed. But only if installed from repository, not vendor will it work when you get a kernel update.

Have you tried nomodeset from first boot line?
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

If you can boot, post this:
#What is installed, if no proprietary drivers, it just returns with no output.
dkms status

 # list drivers available, same list as system settings,  software updates,  additional drivers or last tab
ubuntu-drivers devices
# or
ubuntu-drivers devices | grep recommended

---

### Post by bijaydeyp on 2016-02-11
@oldfred. I am so sorry for that.


 "Also did you install proprietary graphics driver directly from nVidia?"
I have built-in graphics card--Intel GMA 3150. no video drivers i have installed and it is a non-UEFI system.


 "Have you tried nomodeset from first boot line?"
not yet.
ok.I will let you know about the testing.

---

### Post by oldfred on 2016-02-11
Some Intel need different boot parameters than nomodeset. Some just work.

       # Usually Intel works with one of these:
i915.modeset=0
i915.i915_enable_rc6=1
video=1280x1024-24@60  # but change to your monitor size  not 1280x1024
video=VGA-1:1280x1024-24@60  # but change to your monitor size
# Other settings in addition to above for other hardware related issues
acpi=0
acpi_osi=linux
acpi_backlight=vendor
noalpic

---

