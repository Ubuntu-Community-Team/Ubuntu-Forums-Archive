---
title: "graphics problem loading ubuntu 12.04 live usb on old PC"
date: 2013-10-20
forum: New to Ubuntu
---

### Post by Peter_Heft on 2013-10-20
AMD athlon 908 mhz with 768 mb ram  graphics card matrox millennium g450 dual head   running XP and tired of windows.      used Automated Universal MultiBoot UFD Creation Tool to create live usb of Ubuntu 12.04 32bit.   When that didn't work added Lubuntu 13.04.   Both boots fail after the screen with (Lu)Buntu in the center and the four dots underneath changing color.     Is that the startup screen?   last mesg with Ubuntu is failsafe-x main process terminated with status 1.   last mesg with Lubuntu is lightdm main process terminated with status 1.   Thanks for any help.   I have done some searches in forums and reached the conclusion that it is graphics related.  There is no wireless card.

---

### Post by mastablasta on 2013-10-21
have you tried with nomodeset boot option? : [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by Peter_Heft on 2013-10-21
Thanks for the response.  I found a thread that seemed to relate    
**[SIZE=2][ubuntu freezes at startup screen after installation]("http://ubuntuforums.org/showthread.php?t=1677870")[/SIZE]**

and tried everything there by editing the /boot/grub/loopback.cfg on the live usb.  found how to change live usb boot options.
the file does not look like the one in the post.  I will paste it here with RED [COLOR=#ff0000]XXXXX[/COLOR] where I have made changes. 

menuentry "Try Ubuntu without installing" {
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper iso-scan/filename=${iso_path} quiet splash [COLOR=#ff0000]XXXX[/COLOR]--
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity iso-scan/filename=${iso_path} quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    linux    /casper/vmlinuz  boot=casper integrity-check iso-scan/filename=${iso_path} quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Test memory" {
    linux16    /install/mt86plus
}
Thanks for the link to the manual.  None of the changes have gotten me any further in booting
Help, please

---

### Post by Peter_Heft on 2013-10-21
I wanted something to work so this is being added browsing with sea monkey in Wary Puppy 5.5 on the same PC.  Wary Puppy had no problem getting graphics to work.
Why does Ubuntu not load?  Something with more power ought to work on here.
Please help!

---

### Post by Bashing-om on 2013-10-21
Peter_Heft; Hi ! Simpler is better.
Try as mastablasta advised. In that link is:
"Changing the CD's Default Boot Options"
f6 key and choose "nomodeset"
continue the boot process.

Asvise of results.

[INDENT][INDENT]it is just a process
[/INDENT][/INDENT]

---

### Post by Peter_Heft on 2013-10-22
Hi Bashing-om and thanks.  Can't get to the advanced welcome page options, the little keyboard logo never appears.  Trying to get something to happen after the screen with UBUNTU 12.04 and the four dots underneath I hit some keys and hit esc. two interesting mesg; load fallback graphic devices was a fail, and this file=/cdrom/preseed/ubuntu.seed from grub as above "does not exist", the file does exist but the path is wrong(?) it isn't a cdrom. The rest whips by too fast to catch much.  From what I have seen of Puppy Ubuntu should be great! Thanks

---

### Post by mastablasta on 2013-10-22
the boot options are before the logo and dots appear. [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
you might want to use other options there since you have an older maschine.

also i am not sure how well that CPU is supported. Might be good to try something with non-pae kernel.

you can also try the Alternate CD (it's a text based install). Stick with lighter desktops (Xubuntu, Lubuntu)


the GPU is not familiar to me. but you are not supposed to fix the cfg file liek oyu did. you need to add the parameter on boot when the boot screen comes up and where you select what you wan't to do (install try etc.)

---

### Post by squakie on 2013-10-22
I'm making the assumption here that when you stated they fail at boot that you mean trying to boot from either on the USB flash to try to install Ubuntu/lubuntu is failing.  If so, I'm thinking perhaps you should download and try the alternate install iso.  It will be text based but sometimes helps on systems that for one reason or another won't run the GUI'd based installer.  You could try that and see if you can install.  It will be the normal GUI'd desktop after it boots.

I also think I would stick with lubuntu since it uses lxde for managing the desktop and doesn't require some of the things that Unity in "normal" Ubuntu does from the graphics adapter, since this is an older system.

---

### Post by Peter_Heft on 2013-10-22
Thanks to both of you.  I am going to try the text/alternate iso of Lubuntu as a live usb.  Will report back.

---

### Post by Bashing-om on 2013-10-22
Peter_Heft; Good thing !

We do want to see this through to resolution, up and running 'buntu !

[INDENT][INDENT][INDENT]if at first you don't succeed, try "something else" ( skydiving excepted )
[/INDENT][/INDENT][/INDENT]

---

### Post by Peter_Heft on 2013-10-23
Thanks for the support!  I'm a stubborn old german, so giving up is not even possible.  I got xubuntu running as a live usb and it worked with the standard desktop install, I had downloaded both and tried the desktop one first. This time I used "Linux Live USB creator", was that the difference?
Now that you got me up and running are we done and install help is separate or may I continue here?
Thanks again for the help.
Peter

---

### Post by Bashing-om on 2013-10-23
Peter_Heft; Hey ,

Pleased that you are pleased.
As you are now up and running, standard operating procedure is to close this thread as "solved".  This aids in the forum format. And yes by all means open as many new threads - one theme per thread - as needed to satisfy all your needs. That gains additional views for those knowledgeable with that given situation to render assistance.

Solved: 1st post -> thread tools.

[INDENT][INDENT]happy trails to you
[/INDENT][/INDENT]

---

### Post by Peter_Heft on 2013-10-23
Thanks again for the help!  It is great to know that friendly and willing help is as close as my browser.
I forgot to mention that the live usb booted up without any intervention.  I love the name UBUNTU!

---

