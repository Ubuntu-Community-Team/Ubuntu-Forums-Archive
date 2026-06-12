---
title: "[SOLVED] Live CD doesn't boot!"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by ApUUbunU on 2008-05-24
Hello Everybody!
I am new to these forums, and Ubuntu, eager to try Hardy Heron.

One problem though, the Live CD I have burned doesn't boot as I start up the computer. I used the right ISO file, and the right method of burning the ISO. I'm really not sure what caused this problem.

As I startup the computer, there is no option to boot any system, and the computer automatically starts up on Windows XP. I remember to leave the disk in the drive as I shut down the computer previously.

After looking on the net, I haven't found any solutions, or similar problems for that matter. It would be appreciated if someone could help me with my problem.

Thanks!

---

### Post by Enthralled on 2008-05-24
Did you set your BIOS to boot from CD?

---

### Post by overdrank on 2008-05-24
> **ApUUbunU said:**
> Hello Everybody!
I am new to these forums, and Ubuntu, eager to try Hardy Heron.

One problem though, the Live CD I have burned doesn't boot as I start up the computer. I used the right ISO file, and the right method of burning the ISO. I'm really not sure what caused this problem.

As I startup the computer, there is no option to boot any system, and the computer automatically starts up on Windows XP. I remember to leave the disk in the drive as I shut down the computer previously.

After looking on the net, I haven't found any solutions, or similar problems for that matter. It would be appreciated if someone could help me with my problem.

Thanks!
Hi and welcome, have you set your system to boot from the cd drive in bios?
Edit to slow lol :)

---

### Post by diablo75 on 2008-05-24
It sounds like you need to edit your BIOS settings so that the default boot order will seek a bootable image from your CD-ROM/DVD drive First, followed by your hard drive.  Some PC's also include a boot menu that can be accessed by hitting one of the Function keys at the top (often F12) during POST, though this may not be available for you so you'll just have to edit your boot order.  Right now, your hard drive is being sought before your CD-ROM.

---

### Post by forestpixie on 2008-05-24
You need to get into the bios when the pc starts - del or something similar, might be F something - watch the screen.

You need to change boot options so that it boots from cd first.

---

### Post by worldy on 2008-05-24
Maybe you set the option to boot from harddisk .

Make sure your first boot device is CD/DVD.

---

### Post by forestpixie on 2008-05-24
Wow - lost that race :)

---

### Post by ApUUbunU on 2008-05-24
Thanks for your speedy replies!

Yes, I thought that the BIOS setting might be important, I saw something about that on the Internet, but wasn't sure.

However, as I boot up, I see, "BIOS not detected".

I toggle F2, and still, I can't change the BIOS settings. Is there any other way that I could boot from the CD by changing the BIOS settings from inside XP?

---

### Post by Crossroads on 2008-05-24
You can't change the BIOS settings from inside Windows XP.

You earlier post says that your PC boots into Windows, ignoring the LiveCD. So I do not understand why you would get the "BIOS not detected" message.

What's F2 meant to do?

To get into my BIOS I have to press DELETE at the right time. Once there I can change the ordeer of my boot devices (as the other repliers have mentioned).

What motherboard (or PC model) do you have?

---

### Post by AChitnis on 2008-05-24
Well, its odd, but the BIOS isn't detected, though it still works.

I tried a Wubi installation earlier, and that worked alright, I was able to choose the operating system perfectly, Windows XP or Ubuntu. Ubuntu worked fine by the way.

F2 is supposed to access the BIOS settings, but I shall try DELETE as you said.

By motherboard I think you mean what processor am I running on: an AMD 1.8GHz x86model and its probably 64-bit.

I think thats the information you need to know.

Thanks

PS I am also ApUUbunU, I created two profiles as one was initially accidentally blocked. I will only use ApUBunU from now on...

---

### Post by ApUUbunU on 2008-05-25
Well, I have some progress of this. If any oneelse is having similar problems, this might help:

Initially, I tried to open the Ubuntu CD through Windows - it wouldn't load, probably an error in the burning.
So I decided to burn another CD, and it did work!.

Using Wubi, I made an installation that worked correctly. However, I could not select Ubuntu, as I was using a wireless keyboard, which needed some drivers. This came out to be useful later, when I rebooted my computer with the disk still in the drive.

I rapidly pressed DELETE as was recommended during bootup and hey presto! the BIOS settings came up, much to my amusement. I am now in the process of deciding whether to use an Wubi installation, or a installation made through the live CD.

Thanks everyone for helping!

---

