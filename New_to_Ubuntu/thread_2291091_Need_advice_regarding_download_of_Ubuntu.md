---
title: "Need advice regarding download of Ubuntu"
date: 2015-08-17
forum: New to Ubuntu
---

### Post by vikki2 on 2015-08-17
Update:  i downloaded imgburn and successfully made an install disc!  phew.  now, part two:  installation.
Update 2:  I did it!  My stumbling block was not understanding ISO files and how they work.  Once I got what I needed via imgburn I was able to burn an installation dvd.  Got the new hard drive today, put in and my Acer is like new!
Thank you for all you're help!

Hi.  I'm brand new and have moderate pc knowledge.  I'm trying to figure out how to properly download and install Ubuntu in anticipation of replacing the hard drive in my Acer 5352-BZ493 laptop (don't want Windows.)
I downloaded and burned Ubuntu from the web site but it has no files (almost like flat picture, nothing else.)  P.S.  Just did some more reading and it seems I incorrectly burned the disc as a file.  So, I will let Vuze burn it.
So, upon some internet reading I decided to use a bit-torrent, keeping in mind I do have limited knowledge, and am downloading on Vuze right now.  
Any guidance on how to proceed is deeply appreciated.  
Thank you!
P.S.  since this posting i've done further internet research and it may be windows vista causing the problem with the file?
Here's what I read:  "A major reason that many average PC users have trouble with ISO files is  that Windows XP and Vista do not recognize them natively. If you try to  open an ISO file in these older versions of Windows, they do not know  what to do with it unless you have installed some third-party software  to manage ISO files. However, Windows 7 does have a feature to burn ISO  files to a CD or DVD. Windows 8 finally provided a native Windows  facility for mounting ISO files."
So, any suggestions to deal with this?  I'm learning as I go.  I really appreciate your help :)

---

### Post by grahammechanical on 2015-08-17
Which web site? This one?

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

What version did you download? Ubuntu 15.04 only has support up to the end of January. Ubuntu 14.04 has support for 5 years from April 2014. Did you follow either of these two guides?

[http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows](http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows)

[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

What we download is an ISO image file. It is an archive. We only see the files it has once we have "burned" the file to the DVD disc or the USB stick. Burning an ISO image to a DVD disc is not the same as copying it to the DVD disc.

You then enter the machine's boot system utility (called BIOS or UEFI) and set the motherboard to boot from the DVD drive or USB port, whatever is relevant, and the live session should load and you can then test Ubuntu.

You have not told us the hardware you have or what other operating system is on it. So, just in case, here is some more reading:

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

Regards.

---

### Post by vikki2 on 2015-08-17
i downloaded 15.  now when i try to burn it on vuze it says this:  "Incompatible file formats.  The files you're trying to add to your dvd playlist do not contain compatible video files.  Please check your files and try again."  This is the same thing that happened when I tried burning with Windows. I'm obviously having trouble understanding ISO files and how to download them properly.  Ugh.  Thank you!

---

### Post by vikki2 on 2015-08-17
p.s. since i have to start again i'll download 14 instead.  i vaguely understand what you've said about the difference between copying and burning, but where am i going wrong? nothing i download ever says "trusty" or looks like any of the images i've seen as examples. "Burning an ISO image to a DVD disc is not the same as copying it to the DVD disc."  Okay, this is where i'm going wrong then, but i get the option to save the file, and each time it downloads but i see no files afterward.  It might be windows vista causing the problem.  i'm just so frustrated.  i've download ubuntu 3 or 4 times.  :(
thanks

---

### Post by hansdown on 2015-08-17
Welcome to the forum, vikki2.

Have a look at this link, and post back if we can help with anything.

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by vikki2 on 2015-08-17
p.s. since i have to start again i'll download 14 instead.  i vaguely understand what you've said about the difference between copying and burning, but where am i going wrong?  thanks

---

### Post by vikki2 on 2015-08-17
i can't even get that far.  i'm not ready to install--the new hard drive will be here the end of this week.  at this point i am having trouble even getting the downloaded ubuntu iso files opened or dealt with properly for a dvd burn to be used for the install.  if someone can please tell me about that part.  i'm using windows vista.  i have vuze but that also cannot burn the iso file.

---

### Post by hansdown on 2015-08-17
This may be a good option,vikki2.

[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

---

### Post by SuperFreak on 2015-08-17
If you can't create a Live USB here are directions for burning ISO to DVD using Windows
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by vikki2 on 2015-08-18
thank you!

---

### Post by oldrocker99 on 2015-08-18
Unetbootin, available for Linux, Mac and Windows, will write an .ISO file to a USB stick, which does need to be FAT formatted. Works like a charm.

And a bootable USB will load and install **much** faster than a bootable DVD.

---

