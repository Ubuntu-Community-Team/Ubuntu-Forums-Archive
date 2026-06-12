---
title: "Unable to install Lubuntu on HP Mini 1151NR"
date: 2015-02-12
forum: New to Ubuntu
---

### Post by paul194 on 2015-02-12
Hello all.  I've decided to use my old HP Mini 1151NR laptop/netbook, but since it is bloated with Windows XP, I wanted to completely remove it and try out Lubuntu.  I have used Ubuntu on another PC in the past and seemed to like it and wanted to try Lubuntu on this smaller, older netbook.  Because this HP Mini does not have a CD/DVD drive, the only way to install it is through a USB Flash drive.  I have taken the ISO from Lubuntu's website and tried a number of different programs to convert the ISO to a bootable USB (I've tried Rufus, Universal USB Installer, and Unetbootin. I am doing this on a Windows 7 machine).  When the process finishes and I place the USB flash drive in the HP Mini, I boot up to the USB, I get a initial Lubuntu install screen, but every time I click "install Lubuntu", I get a black screen and it stays like that.  I've tried the Lubuntu 14.10, 14.04.1, and even the daily live (15) ISO files.  As I've mentioned before, I've also tried a number of different ISO to USB programs.  I have even tried a number of different USB flash drives (2GB Corsair Flash Voyager,  1GB USB Pendrive, 8GB Data Traveler 100G2, and even a USB enclosure with an old IDE 2.5" HDD.)  Every method ends up the same:  I hit enter at "install Lubuntu" and get a black screen.  The same thing happens when I select to run Lubuntu without installing.  Yes, I am making sure I am downloading the 32bit ISO (as the processor is a 1.60GHz Intel Atom Processor N270).

Why am I having such problems installing this on a HP Mini Netbook?
Any help would be greatly appreciated!

---

### Post by mörgæs on 2015-02-13
Hi, welcome to the fora.
I suggest that you try some boot options, for example **nomodeset**.

If we knew your graphics processor we could give more precise advice.

---

### Post by paul194 on 2015-02-13
> **mörgæs said:**
> Hi, welcome to the fora.
I suggest that you try some boot options, for example **nomodeset**.

If we knew your graphics processor we could give more precise advice.

Hello!  It is an integrated graphics.  From HP's website, the video driver (for Windows XP) is "Intel Graphics Media Accelerator Driver for Microsoft Windows XP" ver 1.00A.  I believe it is a Intel 945 Graphics.


I hope this information helps.

---

### Post by mörgæs on 2015-02-13
Dang - second time I guessed wrong about the graphics card.

This might help:
[http://ubuntuforums.org/showthread.php?t=2264920&p=13227184&viewfull=1#post13227184](http://ubuntuforums.org/showthread.php?t=2264920&p=13227184&viewfull=1#post13227184)

---

### Post by kerry_s on 2015-02-13
how long did you wait ? my mom has the hp 1010nr, damn things are slow as hell with windows starter. i booted up elementary os once to see how it runs live & it took a while to load but got there eventually.

---

### Post by paul194 on 2015-02-13
> **kerry_s said:**
> how long did you wait ? my mom has the hp 1010nr, damn things are slow as hell with windows starter. i booted up elementary os once to see how it runs live & it took a while to load but got there eventually.

I let it sit there for 10 mins and still have a blank screen.

---

### Post by kerry_s on 2015-02-13
> **paul194 said:**
> I let it sit there for 10 mins and still have a blank screen.

wait a little longer, it could need more time to load the usb to memory.

---

### Post by paul194 on 2015-02-14
> **mörgæs said:**
> Hi, welcome to the fora.
I suggest that you try some boot options, for example **nomodeset**.

If we knew your graphics processor we could give more precise advice.


Okay, What do I need to do?  I press f9 to enter the USB boot, I select the USB drive, I press "Tab" and then I type "nomodeset"
It seems to boot, but then I get a black screen.  Am I to do "nomodeset" some other time?  

Just saying "I suggest that you try some boot options, for example **nomodeset**" does me no good unless you tell me specificallly how to do it.

Any help is appreciated.

---

### Post by paul194 on 2015-02-14
> **kerry_s said:**
> wait a little longer, it could need more time to load the usb to memory.

okay... 30 mins later... no difference.

Something tells me something else is wrong...

---

### Post by kerry_s on 2015-02-14
> **paul194 said:**
> okay... 30 mins later... no difference.

Something tells me something else is wrong...

yeah, intel graphics is supported out of the box. have you tried any other versions, say xubuntu for example ?
i tried my moms hp 210-1010nr earlier today, booted up xubuntu no issues, everything worked even wireless. they should be close specs wise.
i use an atom 330 board in this mini pc, just installed xubuntu this mourning.

does your model have a vga port ? maybe try hooking up to external see what it does.
did you try moving the pointer, make sure the screen didn't time out ?
have you tried pressing ctrl+alt+f1 see if theres any message in console ?

sorry, just throwing thoughts out.

---

### Post by paul194 on 2015-02-14
> **kerry_s said:**
> yeah, intel graphics is supported out of the box. have you tried any other versions, say xubuntu for example ?
i tried my moms hp 210-1010nr earlier today, booted up xubuntu no issues, everything worked even wireless. they should be close specs wise.
i use an atom 330 board in this mini pc, just installed xubuntu this mourning.

does your model have a vga port ? maybe try hooking up to external see what it does.
did you try moving the pointer, make sure the screen didn't time out ?
have you tried pressing ctrl+alt+f1 see if theres any message in console ?

sorry, just throwing thoughts out.


Okay lets start:
"have you tried any other versions, say xubuntu for example"
No.  Its a low powered netbook.  Thats why I'm trying Lubuntu.  Have I tried other thousands of versions of linux on this netbook?  No.  I did various google searches on Linux distros that may work best-  I have tried Ubuntu on a separate PC before, that is why I am trying Lubuntu on this netbook. But anything else on the netbook, no.  

"does your model have a vga port"  No It does not.

"did you try moving the pointer..."  Of course... nothing happens...

"have you tried pressing ctrl+alt+f1" I've tried ctrl+alt+f1 and still have a blank screen and nothing happened.

Any other ideas?

---

### Post by kerry_s on 2015-02-14
for the nomodeset thing when you boot up instead of hitting enter to select, press e to edit, it will show the startup line at the bottom just add to the end.
you might also want to try "vga=791" if nomodeset don't work.

---

### Post by mörgæs on 2015-02-14
The nomodeset option was a mistake. I tried to say that in post 4.

Try the alternate Lubuntu.

---

### Post by kerry_s on 2015-02-14
> **mörgæs said:**
> The nomodeset option was a mistake. I tried to say that in post 4.

Try the alternate Lubuntu.

oops, sorry for stepping on your toes. :lolflag:

alternate ? is that the text mode installer version ?

---

### Post by paul194 on 2015-02-14
> **kerry_s said:**
> for the nomodeset thing when you boot up instead of hitting enter to select, press e to edit, it will show the startup line at the bottom just add to the end.
you might also want to try "vga=791" if nomodeset don't work.


Okay...
You guy (or ladies) need to please specify:
"Please (blah blah blah) when (blah blah blah) happens...."

I've tried various ISO to USB boot loading programs and they all look and act different. When using one program to convert the ISO to a bootable USB, it looks different, it looks a certain way, but when I use another program, It looks and acts totally different.  

So.  For instance.  When I use unetbootin (which is what the Ubuntu site recommends), when it boots from USB,  it counts down.   I press "tab" and then press "e" to see if "edit" occurs.  Nope.  Black screen, as usual.  
Please help:  Perhaps I am not inputting the "nomodeset" mode in correctly.  What is the correct procedure?  

I've hit tab and then tried "vga=791" then, enter, and enter, and black screen.
I rebooted and tried "vga=791" again, instant blank screen.  Rebooted AGAIN and did the same thing.  Got an instant blank screen again...

Any other ideas?

---

### Post by paul194 on 2015-02-14
> **mörgæs said:**
> The nomodeset option was a mistake. I tried to say that in post 4.

Try the alternate Lubuntu.

???
I've been trying Lubuntu.... nothing else...

---

### Post by mörgæs on 2015-02-14
> **kerry_s said:**
> oops, sorry for stepping on your toes.

You didn't. No problem!

---

### Post by kerry_s on 2015-02-14
i only use unetbootin to make my usb installer.

could you try xubuntu, just to rule out it's not the lubuntu image. xubuntu is just as lite, basically same apps installed, just easier to work with. aka: user friendly

---

### Post by sudodus on 2015-02-14
Check that the download was good, that the iso file matches the ***md5sum***. See this link [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

Installing from the alternate iso file uses a text based menu system, and is not as sensitive to problems with graphics (as the desktop iso file). You can get the alternate iso file here: [https://help.ubuntu.com/community/Lubuntu/Alternate_ISO/14.04.1](https://help.ubuntu.com/community/Lubuntu/Alternate_ISO/14.04.1)

See more tips and tweaks to help installing in the following links

[https://wiki.ubuntu.com/Lubuntu/AdvancedMethods](https://wiki.ubuntu.com/Lubuntu/AdvancedMethods)
[Old hardware brought back to life]("http://ubuntuforums.org/showthread.php?t=2130640")
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

And the following link explains how to add boot options

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

It may look in a different way with ***Unetbootin*** compared to a boot CD or a pendrive created with the ***Startup Disk Creator*** or ***mkusb*** or ***Win32 Disk Imager***. Lubuntu is slightly different from standard Ubuntu but I think the instructions may help you anyway. Unetbootin is a good tool to create USB boot drives, but if you still have problems to add boot options, please try another tool.

---

### Post by paul194 on 2015-02-14
Thank you all.
I downloaded the lubuntu-14.10-alternate-i386 one.  Checked md5 (its good).  Deleted unetbootin and downloaded and installed again.  But the ISO on the USB, selected a proper video mode, and it is working now.
Thanks.

---

### Post by sudodus on 2015-02-15
Congratulations and thanks for sharing your solution :KS

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

