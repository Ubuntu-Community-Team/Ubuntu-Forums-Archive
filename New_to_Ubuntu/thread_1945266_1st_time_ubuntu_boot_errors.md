---
title: "1st time ubuntu boot errors"
date: 2012-03-22
forum: New to Ubuntu
---

### Post by jaklans on 2012-03-22
Helo
I have just put together a new buget apu computer and atemptet to use ubuntu on it (about $100 cheeper than windows:roll:) Ive tried almost everything i could find online but the system would never boot (from disks and usb flash; ssd is shiping late). When booted the computer displays a little code or something and then my moniter goes into sleep mode.(connected but displaying nothing) I think this might have to do with the apu (gpu+cpu). This hurts my pride, but I know basicly nothing about linux so please explane every step.

---

### Post by Gleichsnerd on 2012-03-22
Welcome to the forums!

First off, we need some details. What are the specs of your computer? What version of Ubuntu are you trying to install? Are you obtaining the .iso or whatnot from a Canonical source or another website?

---

### Post by anewguy on 2012-03-23
The apu's that I know of are all AMD, and that means the gpu is going to be AMD/ATI - I believe I've read something like the 5400 series.  I've had several AMD processors and several AMD/ATI discreet graphics cards - never the APU.  However, that combination *should* boot without any problem.  I might suspect there is just something simple going on, but as already mentioned, we need the specs on the PC:

- motherboard make and model
- which APU you have installed
- how much memory
- any other add-in cards (you didn't add a discreet video card by chance?)
- the version of Ubuntu you are trying to work with
- how you created your boot media - where did you get the ISO, did you burn it to CD or use unetbootin to create a bootable USB media?
- if usb, does your motherboard support booting from USB?
- is the BIOS set to try booting USB, then the CD and then any hard drive type media (including SSD)?

As much detail as we can possibly get will help us help you.

Welcome to Ubuntu!

Dave ;)

---

### Post by jaklans on 2012-03-23
Sorry, forgot specs:
ASUS f1a75-m pro
amd a6-3500 APU
gskill sniper 1866 8gb (2x4)
Ubuntu 11.10
 
Also got 2 hhds from another computer but the OS is striped between the 2 and I cant use them (Error for windows 'Error loading operating system) Can I setup raid from bios?
 
I am desperate and I think the universe hates me

---

### Post by jaklans on 2012-03-23
P.S. I forgot to mention I burned USB flash with pendrive linux and got ubuntu from ubuntu.com
 
(also I do have a verry old nvidia 6 siries gpu if I should try that)
 
 
I know the universe hates me

---

### Post by wildmanne39 on 2012-03-23
Hi, try these options in this link until you find one that works hopefully because it is probably that you need to install your driver for your nvidia card which you will be able to do after you boot.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Thanks

---

### Post by anewguy on 2012-03-23
> **jaklans said:**
> P.S. I forgot to mention I burned USB flash with pendrive linux and got ubuntu from ubuntu.com
 
(also I do have a verry old nvidia 6 siries gpu if I should try that)
 
 
I know the universe hates me

Nah - not the entire Universe - Jupitor maybe but they're kinda testy little gray dudes anyway :)   

On a serious note, I'll have to do more research later.  I'm currently on Windows on a netbook laying bed due to a bad back, so I'm really not up to getting up one of the desktops to do some testing.  I'll get back to you as soon as I'm doing better.  So, if someone else doesn't give you the answer, I haven't forgotten you - just laid up :)

Dave ;)

---

### Post by anewguy on 2012-03-24
> **wildmanne39 said:**
> Hi, try these options in this link until you find one that works hopefully because it is probably that you need to install your driver for your nvidia card which you will be able to do after you boot.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Thanks

+1.  If you are using that nVidia card also, you'll need your monitor plugged into that card.  Then follow the link that wildmanne39 posted - you want to edit the boot line and add nomodeset and then let it boot.  This will hopefully get you to a booted GUI screen, at which point you can try the restricted/additional drivers and see if there is a driver found for your card.  After you install that driver, you will probably also need to make the nomodeset option permanent, so be sure to read the information in the link carefully - it includes a section on editing and updating the files and grub2 as needed under 11.10 to make the option permanent.  If you forget, just add it in the boot options again and once booted go in and make those changes.

Please post back with ANY questions, any errors, etc..  Everyone is here to try to new people have a pleasant experience with Ubuntu, and we want yours to be as well!

Dave ;)

---

### Post by jaklans on 2012-03-24
GRRRRRRRRRRRRRRR!
almost done with my post but it got deleated so I might be breef
It works but I want to use the integrated 6000 on the APU
 
also I want to run windows for games so I took 2 HHDs from a old computer but I think windows was spread in a raid config and my progress is barred by 'Error loading operating system' any time I boot. It might be the wrong forum but I try anyway.
 
Jupiters still big enough to count as 3, so thats a third of the universe
 
 
P.S. Ill be gone for 2 days so I wont be in this post

---

### Post by wildmanne39 on 2012-03-24
Hi, did you look open additional drivers? that usually has a driver for your card, I have a 6150 myself.

If the driver is there and you activate it then reboot and you should not need to make nomodeset permanent.
thanks

---

### Post by anewguy on 2012-03-24
If I understand correctly, you are now booting but off the old discreet card.  To use the integrated GPU then you must have another set of video connections on the motherboard.  Remove the discreet card completely from the box and attach your monitor to one of the motherboard video connectors and try booting.  If you're booting purely AMD/ATI, which you should be at that point, you shouldn't need nomodeset at all - it should just boot.  And as wildmanne39 pointed out, the driver will be available in the restricted drivers.  Your APU provides AMD/ATI 6430 capabilities.

So, what you do is based on 2 scenarios:

If you have no video connections from your motherboard, then you'll need to leave the nVidia card there, boot with nomodeset, make nomodeset permanent, and look in restricted drivers.

If you have video connections from you motherboard, remove the nVidia card completely so there is no discreet video card in any slot.  Then plug the monitor into one of the video connections from your motherboard and just boot - no "nomodeset" will be needed.  Go to restricted drivers and install the driver.  There will be a world of difference in the video on the 6430 versus the old nVidia card.

Now, for your hard drives:

If indeed they are a raid set, you may still be able to clear that all out using Ubuntu first.  With Ubuntu booted, try disk utility and see what it says for those disks.  You may be able to (1) remove all partitions, leaving a clean drive and/or (2) remove all partitions and format ntfs (I personally would leave the NTFS formatting to Windows.  But it might take more to take the raid flag out of the header information.  So, once you have Ubuntu booted, start up disk manager and take a good clear screen shot of what it shows for those 2 disks and post it in a reply back here.

If Ubuntu recognizes the raid set, it's possible to reverse that all out using disk utility.  That's why we really need to see the information first before we tell you what to do.

dave ;)

---

### Post by jaklans on 2012-03-27
Ok
The discreet GPU has been taken out but the integrated graphics creates nothing but a frozen pink (like the loading screen without the loading) Any driver instalers are unacessable beond that screen
 
On the drives
the drives ar labled as a 500 gb filesystem (250gb each) Can I efectivly transfer gust windows to the SSD (and then use the rest as a raided data/software SSD cashing drive?)
 
2 PSes
sorry I didnt respond, didnt know there were 2 pages
you dont have to domb down the hard ware, I know all that
Thanks

---

