---
title: "Wrote new CD for Ubuntu install and it won't work"
date: 2012-07-16
forum: New to Ubuntu
---

### Post by Lega11yblonde on 2012-07-16
I don't know what I might have done wrong.  I downloaded 12.04, wrote it to disc and then verified the disc.  Then I did a reboot and the computer went straight to Windows, no boot screen at all.  I tried to turn the computer off and left it off for five minutes and then turned it on:  same result.  Windows 7 Home Premium booted and I had no boot screen or request to install.

Suggestions, comments?

---

### Post by drmrgd on 2012-07-16
Have you verified that your CD-ROM drive is set to boot before the Windows HDD in BIOS?  You may need to change your boot order in BIOS to boot from the CD-ROM

---

### Post by Lega11yblonde on 2012-07-16
PS I used a disc I wrote earlier and the same result.  I think that worked before on another Compaq.

---

### Post by Lega11yblonde on 2012-07-16
> **drmrgd said:**
> Have you verified that your CD-ROM drive is set to boot before the Windows HDD in BIOS?  You may need to change your boot order in BIOS to boot from the CD-ROM

How do I do that?

---

### Post by Rex Bouwense on 2012-07-16
There are some specific steps that you have to do when you download an ISO.
First, after the download you need to check the MD5Sum.  I assume that you have done that, however here are two sites just in case.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/UbuntuHashes#A12.04_LTS](https://help.ubuntu.com/community/UbuntuHashes#A12.04_LTS)

Second, you need to burn the image to a CD.  Again I am assuming that you did this and not merely copied the files to a CD.  Merely coping the files does not make the CD bootable and will do you absolutely no good.

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Assuming all that good stuff has been done correctly you must change the BIOS to reflect a change in boot order.  Pop the CD into the tray and turn the computer on.  Shortly (or after some time since this is Windows) a screen will appear and at the bottom it will tell you to hit a certain key to enter set up set up.  Do that.  Now you are in the BIOS.  Navigate to boot and change the order of boot devices to CD first and then hard drive.  Save changes, exit, and allow the computer to boot and you will be booting from your CD.  Take it for a test drive (try it and make no changes to your computer.)  If everything works you can later decide to install.

---

### Post by drmrgd on 2012-07-16
It all depends on the computer you have.  When you start it up,  you should see a splash screen that will say "Press <somekey> to enter Setup" or something like that.  Usually it'll be something like "Escape", F1, F12, or something along those lines.  If you do a Google Search on your computer model, you might find information on how to access your particular BIOS settings.  Please post back your computer model, and maybe someone here will know right away.

Once you're in the BIOS settings menu, you'll look for something like a Boot menu, which should list your devices and what order to check each for a bootable OS.  Move the CD-ROM to the first position, save and exit, and the system should reboot.  When it does, it'll try to boot from the CD-ROM first, and if there is a bootable disc in there (like your Ubuntu setup disc), it'll boot to it.  If not, it'll move to the next item in the list and try that one, and so on until it runs out of options.  

Hope that helps!

---

### Post by Lega11yblonde on 2012-07-16
I logged into the BIOS and changed the boot order.  Then I tried the disc again and it worked--up to a point.  I could log onto my wireless, but when it popped my disc out to restart, I found that I got immediately taken back to Windows again.  I chose the option to install within windows, but installed wubi.exe, so I should have had the links to choose whether I wanted windows or ubuntu.  I didn't.  

Any ideas what to do now?

Sorry if that sounds somewhat nonsensical and out of sorts/order.  That's just me today.

---

### Post by drmrgd on 2012-07-16
I've never done the wubi install as I prefer to dual boot instead.  Here are the instructions for a wubi installation from the Ubuntu Wiki, though:

[https://wiki.ubuntu.com/WubiGuide/](https://wiki.ubuntu.com/WubiGuide/)

That might help you to find out how to set up the bootloader correctly (if wubi uses one that is!).

---

### Post by Rex Bouwense on 2012-07-16
You should have said that you wanted to use a WUBI install.  That installs Ubuntu inside of Windows just like any other program.  I have never used the WUBI install either, but the site drmrgd has given you should answer all of your questions.  If not just post back here and someone will help you.

---

### Post by Pheonix m6 on 2012-07-16
just a simple guess............
boot ur windows and then load ur ubuntu disc in your dvd/cd drive.try running the setup from there...it will ask u for a reboot.

---

### Post by Lega11yblonde on 2012-07-16
See Phoenix that's what happened, and that is what I did.  I too want a dual reboot and when I look for the Ubuntu I've supposedly installed I can't find it!  

But when it reboots it just goes straight back to windows.  I'm confused by that, actually.  I have done that three times, and I don't know how to use partitions.  If I want a dual boot system, which I've done before but guess at this point it was beginners luck, what do I do?

---

### Post by sudodus on 2012-07-16
> **Lega11yblonde said:**
> ... I don't know how to use partitions.  If I want a dual boot system, which I've done before but guess at this point it was beginners luck, what do I do?
In order to get a dual boot system you need to

- either learn a little about partitions, how to change size, create new ones, and install file systems,

- or let Ubuntu do it for you.

But first, make it easier for us to help by letting us know about your system:

- cpu, ram, graphics card

- hdd configuration: Try Ubuntu (boot a live session from CD or USB but don't install) and from that system run the following commands and post the output in a reply
```
sudo fdisk -lu
``` and ```
df
```
Maybe you can also run ```
gparted
``` press ***alt + PrintScreen*** and attach the picture to a reply.

---

### Post by Lega11yblonde on 2012-07-17
My computer is a really cheap Compaq Presario, with an Intel Celeron cpu 8800 @ 1.50 Hz and 1.50 GHz
I have 2 gigs of RAM with 1.85 usable
And an Intel HD Graphics Family driver with 821 mb memory.

As for doing a print screen, I actually have work to do today so it might be later tonight to try that.

---

### Post by sudodus on 2012-07-17
> **Lega11yblonde said:**
> My computer is a really cheap Compaq Presario, with an Intel Celeron cpu 8800 @ 1.50 Hz and 1.50 GHz
I have 2 gigs of RAM with 1.85 usable
And an Intel HD Graphics Family driver with 821 mb memory.

As for doing a print screen, I actually have work to do today so it might be later tonight to try that.

I think you can run Ubuntu at least without 3D graphics, and it might be nice with Xubuntu with the light desktop environment XFCE. So I suggest that you download also the Xubuntu iso file.

-o-

Try Ubuntu (boot a live session from CD or USB but don't install) and from that system run the following commands and post the output in a reply
```
sudo fdisk -lu
``` and ```
df
```
Maybe you can also run ```
gparted
``` press ***alt + PrintScreen*** and attach the picture to a reply.

-o-

If you have problem booting:

- Have you checked your BIOS menu system, if there are ways to give your CD/USB drive priority to boot? Reboot with the USB drive connected, and check (in the BIOS menus) if it is recognized as one of the hard disk drives, and in that case put it first in the list.
 
 - Did you check (with md5sum) that the download was good?
 
 - Can you check in another computer, if you can boot a live system 'try Ubuntu' without installing it?

- Try with some boot option, start with **nomodeset** according to this link
[[COLOR="Red"]_https://help.ubuntu.com/community/BootOptions_[/COLOR]]("https://help.ubuntu.com/community/BootOptions")

---

