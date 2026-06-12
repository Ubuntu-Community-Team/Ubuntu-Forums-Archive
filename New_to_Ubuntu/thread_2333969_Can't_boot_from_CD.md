---
title: "Can't boot from CD"
date: 2016-08-15
forum: New to Ubuntu
---

### Post by Delupara on 2016-08-15
A little ashamed but I do not know why it isn't working. I burned the new 16.04.1-desktop-amd64, put it in the disk tray, I restarted. I went straight to my uefi boot file and skipped the cd. 

I believe it has been burned properly
Secure boot is disabled
The boot mode is uefi
The boot order had cd/dvd put in first place.

yet it completely ignores my dvd. no idea what I'm doing wrong.

---

### Post by lisati on 2016-08-15
If you're trying regular Ubuntu, it won't fit on a CD, you'll have to use a DVD.

---

### Post by Delupara on 2016-08-15
My bad I always confuse cd with dvd. I meant dvd

---

### Post by Bucky Ball on 2016-08-15
An oddity as to why it's not working from BIOS, but try this. Hit F12 at boot and that should take you to a list of boot device options. Choose the DVD and that should give us a better idea of exactly what is happening if and when it throws an error.

Post back exactly what happens and any messages you receive after you select the DVD as boot device, please. ;)

---

### Post by Delupara on 2016-08-15
I forgot that I could do that, thanks for reminding me.

Now, something quite bothersome (to me at least) arose when I selected CD, there were two option to boot from:

fedora
windows boot manager

The lather one is weird, since I thought fedora overwrote my MBR, but it seems that I can still use it to get straight to windows, without going by GRUB from my old fedora distro.

I believe the windows boot manager is a legacy based boot, so fedora who got installed in uefi didn't affect it.


Regardless, in both cases, no errors were thrown, Fedora brought me into grub and windows boot manager brought me into windows. Both completely ignored my burned dvd.

---

### Post by mook765 on 2016-08-15
Your DVD doesn't seem to be bootable. How did you create the DVD ?
If you just copied the image to the DVD, that will not work. You have to burn the image to the DVD, that will create a bootable DVD...
In windows, you can use tools like ImgBurn, just works fine...
The reason that your windows-bootloader is not overwritten could be that you have windows and fedora on different hard-drives...( can only guess as you don't show much specs off your system )...

---

### Post by Delupara on 2016-08-15
> **mook765 said:**
> Your DVD doesn't seem to be bootable. How did you create the DVD ?
If you just copied the image to the DVD, that will not work. You have to burn the image to the DVD, that will create a bootable DVD...
In windows, you can use tools like ImgBurn, just works fine...
The reason that your windows-bootloader is not overwritten could be that you have windows and fedora on different hard-drives...( can only guess as you don't show much specs off your system )...

I've used imgburn........ an no I only have 1 hard drive with 2 partitions (one is my windows and the other ESP)

---

### Post by mook765 on 2016-08-15
You have only one hard-drive which has two partitions (ESP and Windows), so where is Fedora installed ?
When your Windows runs in legacy-mode and Fedora is installed in UEFI-mode, Windows and Fedora cant be on the same drive!!
Mystic...
Indeed, your Windows seems to be installed in UEFI-mode too, as you have Windows installed on a drive which has an ESP.
So where is your old Fedora-distribution? Is the Fedora-partiotion deleted ?
Have you verified the checksums off your downloaded ISO ?
When you burned the ISO to DVD, did you use the lowest possible speed ?
When  you use ImgBurn, did you choose "Write Image file to disk" ?

---

### Post by Delupara on 2016-08-15
> **mook765 said:**
> So everything seems to be alright.Make sure that hibernation (fast-boot) in windows is disabled.
Now i understand that you want to install Fedora, which appeared in your boot-options. Just choose Fedora in the UEFI-boot-menu...
But before you proceed, please read this:
[https://ubuntuforums.org/showthread.php?t=2147295](https://ubuntuforums.org/showthread.php?t=2147295)
Update your UEFI-firmware to the latest version.
Provide more information about your hardware,so you may get more tips from our gurus here on the site.
Installing in UEFFI-mode might be tricky...
Good luck...

Wrong, I removed fedora to replace it with ubuntu. I'm simply too lazy to remove GRUB as well

---

### Post by mook765 on 2016-08-15
I edited my last post already, so that is what i thought, you removed Fedora...
Your DVD is not bootable, burn another one, see my Questions my last edited post.

---

### Post by Delupara on 2016-08-15
I'm feeling a little stupid right now. Apparently I mistook HDD/ssd with odd. And now that I selected odd to boot, everything is fine. This is what happens when you try to do things at 4 in the morning. Sorry for taking people's times -_-

---

### Post by mook765 on 2016-08-15
It is really difficult to find out what the problem is, if you don't have enough information...
It would be much better, if you reveal as much information as possible, when you start a thread.
Hardware specs, important changes which you made to the system...
Make clear what you want to do, a moment i thought you want to install Fedora...(16.04.1-desktop-amd64 is not clear enough)
Good Information can safe a lot of time...
Never mind :)

---

### Post by mook765 on 2016-08-15
Cheers!!!

---

### Post by Delupara on 2016-08-15
and I am live speaking from ubuntu. Now to fix the other issue, I will update [this post]("https://ubuntuforums.org/showthread.php?t=2333966"), so if you still wanna help me @mook765, you can come there

---

