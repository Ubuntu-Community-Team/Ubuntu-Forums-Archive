---
title: "How to install Ubuntu on 2nd HD in ThinkPad T60 (dual boot)"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by archer6 on 2008-05-29
I have a ThinkPad T60 (model 2007-73U) with 2 SATA Hard Drives. One in the computer, the other in the Ulta Bay. Win XP came on the main  HD (#1) inside the computer. 

I just installed a new hard drive (#2) in the ultra bay. 

Goal: To leave XP untouched on the main drive (#1) and to run Ubuntu 7.10 or 8.04 (which version do you suggest?) on the ultra bay drive (#2).

After reading all the posts about dual booting with 2 hard drives here, I'm simply confused. 

What is the easiest most sensible way to accomplish this? 

Thanks Your Help Is Appreciated!

---

### Post by Shortz on 2008-05-29
Personally i'd slap on the latest rev - 8.04 onto Disk #2.
no need to worry about a boot loader, as the installer will install the grub one to hd0 - the first hard disk @ the MBR.

If you havn't got a copy yet - go and download the 8.04 CD from [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

When done, just slot the disk in your CD/DVD rom drive, and make sure your bios is set to boot from the CD/DVD rom, and THEN your hard disk, so you can boot the live cd up, and install that way - or if you know what your doing, install it just from selecting install at the menu.

And if you have problems, you can always come back for more advice :)

-Shortz

---

### Post by archer6 on 2008-05-29
> **Shortz said:**
> Personally i'd slap on the latest rev - 8.04 onto Disk #2.
no need to worry about a boot loader, as the installer will install the grub one to hd0 - the first hard disk @ the MBR.

If you havn't got a copy yet - go and download the 8.04 CD from [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

When done, just slot the disk in your CD/DVD rom drive, and make sure your bios is set to boot from the CD/DVD rom, and THEN your hard disk, so you can boot the live cd up, and install that way - or if you know what your doing, install it just from selecting install at the menu.

And if you have problems, you can always come back for more advice :)

-Shortz

Wow... fast response...thanks!

Sounds like a great plan. One thing that I forgot about is that I will have to remove HD2 from the ultra bay to install the CD drive in the bay to use it to install Ubuntu on the new drive.

So: If I remove the main HD1 from inside and temporarily install the new drive inside (where drive 1 was), put the CD drive in the ultrabay, install Ubuntu on drive 2 (now in drive one position). Then once installed remove the CD, replace it with Drive 2 in Ultabay and put Drive 1 back inside computer. 

Will this work?

Thanks again.

---

### Post by kwacka on 2008-05-29
Probably would work, but then you'd have to screw around with grub to get it to boot properly.

I don't know much about 'wubi' (I'm totally Ms-free) but it might work for you.
[http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by archer6 on 2008-05-29
> **kwacka said:**
> Probably would work, but then you'd have to screw around with grub to get it to boot properly.

I don't know much about 'wubi' (I'm totally Ms-free) but it might work for you.
[http://wubi-installer.org/](http://wubi-installer.org/)

I read about wubi and do not want to use it, as it installs Ubuntu "within" XP like a windows application. 

My goal is to eventually go 100% Ubuntu, however presently I have just a couple of apps I must use in Windows. And because I want the two operating systems completely independent, I bought the second hard drive for use in the ultra bay. 

So it sounds like if I buy a USB optical drive, then I could leave both hard drives in place and install from the external CD drive. Does that sound like the best way to achieve the goal?

---

### Post by kwacka on 2008-05-29
Sounds fine to me.

One other alternative - as you want to go 100% linux - is backup, install Ubuntu on your internal drive, then install XP under VMware/VirtualBox.

---

### Post by archer6 on 2008-05-29
> **kwacka said:**
> Sounds fine to me.

One other alternative - as you want to go 100% linux - is backup, install Ubuntu on your internal drive, then install XP under VMware/VirtualBox.

Kudos'

Hmmmm...... another fine option. Decisions....Decisions....:)

It just gets better, a great adventure if you ask me!

---

### Post by archer6 on 2008-05-30
So, here's where I'm at in terms of hardware configuration prior to loading Ubuntu 8.04. 

ThinkPad T60 with 2 hard drives, for dual boot use. 

#1 original internal on board HD with XP Pro SP3
#2 second HD in ultra bay (new empty HD) for Ubuntu 8.04

I have a USB external DVD drive to load the Ubuntu Live CD. 

The Two Goals: 
1) Install Ubuntu on new UltraBay HD, keeping the two: XP & Ubuntu, completely separate on their own respective hard drives, and avoid modifying the windows MBR, or have to go into the BIOS settings. 

2) Be able to remove the Ubuntu drive from the UltraBay and have the computer function as a normal windows only machine without further actions required. 

Questions:
Can I install Ubuntu to it's drive while both HD's are in the computer? Or will Grub sense the presence of XP and modify the MBR? 

Or... do I need to remove the inside HD with XP on it, set it aside and install the new Hard drive in that position to install Ubuntu, thereby eliminating the chance that the MBR is written to. 

Then move the new Ubuntu drive back to the UltraBay, re-install the original XP HD back in it's place inside the computer. 

I have searched, and read the long threads here on dual booting with two HD's and still I'm not sure how to accomplish this. There was one comment I read to the effect of adding a line to Grub which then causes it to list the choices upon boot up. This way one could keep the BIOS settings, and the win MBR as they are. It also said that one could then remove the Ubuntu HD at anytime and the computer would function as a normal XP laptop. 

However what that post lacked was clear instructions for the exact way to enter the command line changes in Grub, using the Terminal. As very new user, it's unfamiliar to me. 

Therefore if this is indeed possible and someone would be so kind as to provide exact step by step instructions on this I would be very grateful. 

Thank You ! for your time and help.

---

### Post by kwacka on 2008-05-30
Firstly - ensure that you can boot from the USB DVD.

When you install you can have the option to install grub wherever you want (there's an 'advanced' box to tick at about Question 5). If your BIOS will allow you to boot from the second drive (with Ubuntu installed) select there as the grub and choose this drive as first boot option.

If the drive is not present, the BIOS will send to the second boot option, the internal Windows drive with untouched MBR.

Your /boot/grub/menu.lst might look something like:
title           Ubuntu 8.04, kernel 2.6.24-17-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-17-generic root=UUID=e2d3a777-d2b1-4f0e-a4b1-9a9d6b6c8174 ro quiet splash
initrd          /boot/initrd.img-2.6.24-17-generic
quiet


title           Windows XP
root            (hd1,0)
# makeactive
chainloader     +1

---

### Post by Mentem on 2008-05-30
Not sure if this applies to you, but when I installed ubuntu on my ide harddrive that was installed in a usb-mount, the installation succeeded, but when I started the computer, I got error 21(if I remember the number correctly... the error(I googled it) was about not finding drive), and I had to connect the drive to my motherboard cables(luckily I had room for it) to get the computer running again.

seems like ubuntu doesn't like being in an usb drive, my bios detected the usb drive too.

---

### Post by archer6 on 2008-05-30
> **kwacka said:**
> Firstly - ensure that you can boot from the USB DVD.

When you install you can have the option to install grub wherever you want (there's an 'advanced' box to tick at about Question 5). If your BIOS will allow you to boot from the second drive (with Ubuntu installed) select there as the grub and choose this drive as first boot option.

If the drive is not present, the BIOS will send to the second boot option, the internal Windows drive with untouched MBR.

Your /boot/grub/menu.lst might look something like:
title           Ubuntu 8.04, kernel 2.6.24-17-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-17-generic root=UUID=e2d3a777-d2b1-4f0e-a4b1-9a9d6b6c8174 ro quiet splash
initrd          /boot/initrd.img-2.6.24-17-generic
quiet


title           Windows XP
root            (hd1,0)
# makeactive
chainloader     +1

In the event I cannot boot from the USB I have a DVD drive for the UltraBay, so should I then remove the Internal HD with XP, replace it with the new drive. Install Ubuntu, chose to have Grub on the same drive. 

Then remove and replace the main XP drive inside and the Ubuntu drive to the UtraBay? 

Also I have no preference as to which drive boots first, as long as I have a screen appear when booting that gives me a choice of which OS I want. 

Finally do I use the sudo command in the terminal to gain access to the lines to me modified as you have outlined above? 

Thanks for your personal attention!

---

### Post by archer6 on 2008-05-30
> **Mentem said:**
> Not sure if this applies to you, but when I installed ubuntu on my ide harddrive that was installed in a usb-mount, the installation succeeded, but when I started the computer, I got error 21(if I remember the number correctly... the error(I googled it) was about not finding drive), and I had to connect the drive to my motherboard cables(luckily I had room for it) to get the computer running again.

seems like ubuntu doesn't like being in an usb drive, my bios detected the usb drive too.

Thanks for the tips, I will have to watch for this.

---

### Post by kwacka on 2008-05-30
> **archer6 said:**
> In the event I cannot boot from the USB I have a DVD drive for the UltraBay, so should I then remove the Internal HD with XP, replace it with the new drive. Install Ubuntu, chose to have Grub on the same drive. 

Then remove and replace the main XP drive inside and the Ubuntu drive to the UtraBay? 

Also I have no preference as to which drive boots first, as long as I have a screen appear when booting that gives me a choice of which OS I want. 

Finally do I use the sudo command in the terminal to gain access to the lines to me modified as you have outlined above? 

Thanks for your personal attention!

If you install ubuntu to the internal drive, it will have grub installed to that drive (obviously) at hd0,0.

Moving it to the bay, and re-installing the Xp drive will (if your BIOS automatically recognises the internal drive as the first drive) cause the Ubuntu's drive to be re-located to hd1,0.

If you can change your BIOS to recognise the Ubuntu (bay) drive as the first disk there's no problem. You can add the Windows option to grub as hd1,0.

You do need root privileges to change menu.lst.

---

### Post by archer6 on 2008-05-30
> **kwacka said:**
> If you install ubuntu to the internal drive, it will have grub installed to that drive (obviously) at hd0,0.

Moving it to the bay, and re-installing the Xp drive will (if your BIOS automatically recognises the internal drive as the first drive) cause the Ubuntu's drive to be re-located to hd1,0.

If you can change your BIOS to recognise the Ubuntu (bay) drive as the first disk there's no problem. You can add the Windows option to grub as hd1,0.

You do need root privileges to change menu.lst.

I'm completely open minded and flexible to which drive goes in each bay. Whatever is the best way, is what I want to do, and frankly being so new, I have no idea.

The goal is simply to have both Ubuntu and XP available to me. I must have XP for work, and I want Ubuntu to learn and eventually move to 100% as my only personal OS. As I can do my work on a desktop there but have been doing it on my ThinkPad for the obvious flexibility of not having to go into the office. 

So with that in mind what is the best setup: which drive in which bay, and that's how I will set it up. 

Thanks Again! :)

---

### Post by kwacka on 2008-05-31
XP in main, Ubuntu in bay

BIOS set to boot bay first, with main second device.

Grub installed on bay.

I.e. If bay is in place, grub gives choice of XP or Ubuntu.

If bay is removed, BIOS starts XP immediately.

---

### Post by cariboo on 2008-05-31
You are setting yourself up for a whole bunch of problems with what you want to do. If i understand correctly you want to be able to use your laptop with out your second drive connected to the computer. If you install ubuntu on the second hdd you will not be able to boot the computer when the second drive is disconnected as the code needed to boot is on your second hard drive. I know this from personal experience as I have hardy installed on an internal hard drive and I just installed intrepid on an external sata drive. Seeing as the last install I did was on the external drive grub now lives on that hard drive. If it isn't turned on I get a grub 15 file not found. You will run into the same thing if you don't have your external drive connected.

You better rethink things before proceeding. I would suggest if you have enough room on your internal drive install ubuntu on it and use the external drive for data. Format it as NTFS and both windows and Ubuntu can access it.

Jim

---

### Post by archer6 on 2008-05-31
> **kwacka said:**
> XP in main, Ubuntu in bay

BIOS set to boot bay first, with main second device.

Grub installed on bay.

I.e. If bay is in place, grub gives choice of XP or Ubuntu.

If bay is removed, BIOS starts XP immediately.

Brilliant! Just the clarification I was looking for!
Frankly I have spent so much time reading all the posts about dual drives and dual booting I was on information overload. I needed someone to help me pull all this info together and you've done a great job. Short, to the point and easy to follow.

This is a great community and I look forward to ramping up my knowledge so I may give back to others here.

My Hats Off To You!........ Now I may proceed in confidence. 

Cheers.....:)

---

### Post by kwacka on 2008-05-31
Just make sure that grub is not associated with the MBR of the XP disk, otherwise you will get the problems cariboo907 experienced.

Take a look at the sites for installing (e.g.) Damn Small Linux to USB flash drives.

---

### Post by archer6 on 2008-05-31
> **kwacka said:**
> Just make sure that grub is not associated with the MBR of the XP disk, otherwise you will get the problems cariboo907 experienced.

Take a look at the sites for installing (e.g.) Damn Small Linux to USB flash drives.

Thanks for the heads up, and I will check out the sites as suggested.

Thanks!

---

### Post by shifty21 on 2008-08-31
I'm about to try the same thing when my hd caddy comes in the mail. My approach was similar to that which was mentioned earlier.

I was going to download Ubuntu and burn it to a disk. My Thinkpad T30 will support USB boot and I was going to use a USB to IDE cable to boot from a spare CD-ROM. I was going to install it to the 20gig drive in the Ultrabay caddy and keep the WinXP on the main notebook HD. I just figured that if I wanted to use Linux instead of XP, I'd just manually chose from the BIOS at startup to boot from the second HD. That way, I could keep each OS separate.

archer6: did you have any luck with your project?

---

### Post by archer6 on 2008-08-31
> **shifty21 said:**
> My Thinkpad T30 will support USB boot and I was going to use a USB to IDE cable to boot from a spare CD-ROM. I was going to install it to the 20gig drive in the Ultrabay caddy and keep the WinXP on the main notebook HD. I just figured that if I wanted to use Linux instead of XP, I'd just manually chose from the BIOS at startup to boot from the second HD. That way, I could keep each OS separate.

archer6: did you have any luck with your project?
Yes, I had a wonderful experience with mine, it turned out perfectly. Here is the procedure I used beginning with my T60. 
First I removed the main internal hard drive. This was to avoid having anything written to the MBR. 
Next I installed my 2nd hard drive into the UltraBay. I then used an external USB optical drive to install Ubuntu from CD to the second hard drive in the UltraBay. Once that was done, I re-installed the main (internal) hard drive. Could not have been easier. 

First scenario: I boot up, if I do nothing, it boots into XP as it did when brand new out of the box.
Second scenario: I boot up, during the splash screen I press F11 it activates Rescue and Recovery.
Third scenario: I boot up, during the splash screen I press F12, the boot menu appears, I select the UltraBay drive and it boots into Ubuntu. 

An additional benefit is that now with the entire Linux setup on the Ultra bay drive I can remove it and install it in any of my other ThinkPads, without any mods required. Terrific...:)

---

### Post by shifty21 on 2008-08-31
Congrats!

I don't think that I'm going to remove the hard drive from the Thinkpad before I load Ubuntu to the Ultrabay. Unless you've read differently, I think that as long I'm carefull to pick the right HD, it should install to the Ultrabay without affecting the local HD.

Sound good?

---

### Post by archer6 on 2008-09-02
> **shifty21 said:**
> Congrats!

I don't think that I'm going to remove the hard drive from the Thinkpad before I load Ubuntu to the Ultrabay. Unless you've read differently, I think that as long I'm carefull to pick the right HD, it should install to the Ultrabay without affecting the local HD.
Their is indeed a reason you must remove the main hard drive, prior to installing Linux. 
It has to do with Grub writing to the Master Boot Record (MBR)on the Windows Drive. I know this because I was given the instructions, to set mine up by a fellow Linux user that has a lot of experience. One thing to note is that the R&R of the main drive is less than 2 minutes. One simple screw to be removed along the bottom edge of the drive end cap. Then the drive slides out very easily, you do your install with the 2nd drive in the Ultrabay via USB external drive and your all set. 
The distinct advantage of this method is then everything Linux is on the 2nd drive. Thus you can easily remove it for using an optical drive in the bay, and ultrabay battery or whatever. Also the boot up process is simplied, with no tweaks or adjustments needed in the BIOS. 

Hope this helps
Cheers!

---

### Post by shifty21 on 2008-09-02
Thanks for the good advice, I guess I get to take apart a T30!

---

### Post by archer6 on 2008-09-06
> **shifty21 said:**
> Thanks for the good advice, I guess I get to take apart a T30!
Let us know how it goes, you will most likely find it's quite easy.

Cheers!

---

