---
title: "D:\ubuntu-14.04-desktop-i386"
date: 2014-06-01
forum: New to Ubuntu
---

### Post by Frank_Deutsch on 2014-06-01
Hi gurus, 
Absolute new to Ubunt, so please be gentle :-)
2 questions:
No. 1. OK, I downloaded it and it's on a DVD (D:\ubuntu-14.04-desktop-i386) and tried to install it, by clicking onto wubi.exe.
It's to go on a Win 7 laptop and I don't want Win 7 compromised.
After 2 or 3 failed attempts, ready to give up with Ubuntu. simply, I don't have that much time to stuff around.
My question is: Can the CD's as supplied by [http://www.ubuntu.org.au/](http://www.ubuntu.org.au/) (order CD's) install Ubuntu without being connected to the net, same as any other program, (have CD will install and ready to go, ) or will it be another 2-hours plus waiting for Ubuntu to install.
No. 2. A friend of mine gave me his old desk top, I wiped everything by using D-Ban, so it has no operating system. How do I install Ubuntu onto this machine? I want to keep away from Windows as I don't have the original CD's anyhow.
If there is a CD that I can purchase which will install Ubuntu (without being connected to the net) that would be great.
Any help/advise appreciated.
Best regards
Frank

---

### Post by vanadium on 2014-06-01
For nr. 1: The Ubuntu installation CD can be used to install the OS without being connected to the internet. you however will need internet connection to update the system, and eventually for extra options such as restricted codecs, additional languages, ....
For nr. 2: You need to boot up the computer using the installation CD of Ubuntu. Then, you will have the option just to run the system from the CD in order to try it, or to install it on the computer.
Rather than using a CD, one can also create a bootable USB from the downloaded iso file. This works faster than with a CD, but your target computer must be able to boot from an attached USB drive. Your old desktop may or perhaps may not yet be able to do so.

---

### Post by Frank_Deutsch on 2014-06-01
Thank you Vanadium, thanks for the help.
I am off to buy the bootable CD from [http://www.ubuntu.org.au/](http://www.ubuntu.org.au/) and Bob;s your autie's live-in-lover. :-)

Best regards to all
Frank

---

### Post by 3rdalbum on 2014-06-01
If you see one file on the DVD, then you burnt it wrong.

You need to follow the instructions on the Ubuntu site - basically you use the "Write image to disc" or "Burn ISO Image" function of your DVD recording software. Or use a program that only burns Iso images.

When that is done, change your BIOS "Boot Order" so it checks the DVD drive first. Then reboot the computer and eventually you will be asked if you want to try Ubuntu or install it. 

When you use the installer it will ask you if you want to install side-by-side with Windows, erase the disk and install Ubuntu, or Something Else. Choose the "side-by-side" option of course and then answer the questions and Ubuntu will install.

You can't use Wubi. It doesn't work well - if at all. There is no reason not to use the normal Ubuntu installer to create a dual-boot.

---

### Post by mörgæs on 2014-06-01
> **Frank_Deutsch said:**
> 
A friend of mine gave me his old desk top...

It's of course different what people call 'old', but generally speaking Lubuntu is a better option than Ubuntu for old gear, especially if the graphics card is weak.

---

### Post by rahul4557 on 2014-06-02
If you are having a Windows Machine the best way would be to make a Bootable USB by downloading an ISO image from **UBUNTU** [http://www.ubuntu.com/download/desktop/](http://www.ubuntu.com/download/desktop/) and using "**RUFUS**" [http://rufus.akeo.ie/](http://rufus.akeo.ie/) to write the ISO to USB drive.

USBs are faster than CD/DVDs.

---

### Post by mastablasta on 2014-06-02
first thing to do after download is check if the image is exactly the same as on server. thi sis not necessary if you use torrent. anyway you do a md5sum check: _[COLOR=#810081][https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)[/COLOR]_ 

then you burng the iso how to burn iso to DVD: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

then you installside by side. if you want to leave windows completely alone wubi is not supported anymore. you can still give the OS a try - you can use virtualbox instead. here is a simple howto: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

---

