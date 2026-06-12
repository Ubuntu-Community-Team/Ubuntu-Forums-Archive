---
title: "New ubuntu 14 problems"
date: 2015-07-21
forum: New to Ubuntu
---

### Post by pecanbrown on 2015-07-21
I have a PC with win 7 installed. It was running strange so I wanted to install so stability. I installed ubuntu 14.04, 32 bit on a dvd and tried to run the dvd. I could neither try it or install it, both options with the same result. The desktop would appear and after a few seconds would go black with the rectangular screen saver which shows when win 7 is shutting down flashing on and off. I thought that the dvd player was too slow so I tried other measures. I could not get 14.04 installed on the flash drive because that option did not show up on 'Lili USB creator', so I installed 15 on the flash drive which worked just fine. I noticed that all the free books were ubuntu 14.04 or lower and decided it would be better to have the books and version the same. Installed ubuntu 14 alongside win 7 and guess what? I am still getting that wierd black screen with the rectangular flashing. The only thing I can do is shut down the system and start over rebooting. I am sad now because when the machine starts it ask which system I want to use and the only one which works is  win 7.  Does that mean there is something wrong with my HD? If not, what could be the problem?

---

### Post by oldfred on 2015-07-21
If 15.04 worked you may have a newer system that needed the newer drivers in 15.04?

What brand/model system and particularly what video card/chip?
Often video issue.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

---

### Post by pecanbrown on 2015-07-21
No, I do not have a newer system. i have a lenovo system with pentium dual core 3.2ghz. 2gb memory. 32 bit operating system with win 7 utimate, service pack 1. I have a EN L1950wD monitor. I believe it is a Intel G41 chipset.

Ubuntu 15 worked differently. I could never install 14 on the thumb drive only on the DVD and I never put 15 on the thumb drive, so maybe we are talking apples and oranges? I was having problems with that as well.

In am confused about your post, after often a video issue. I understood nothing after that sentence.

---

### Post by oldfred on 2015-07-21
Do you get grub menu when you boot? Or is this just with live installer?
Or if just Linux you will not get grub menu unless you hold shift key.
And then try nomodeset or other boot options. First boot after install is different that booting live installer.

 Installer BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)



But if Intel chip for video it may then be one of the other settings, not nomodeset which is usually for nVidia or AMD video chips/cards.

---

### Post by grahammechanical on 2015-07-21
Can I ask a question?

When you install Ubuntu 14.04 was Windows loaded an running and did you install by clicking wubi.exe? I ask because of your statement about the appearance of the rectangular screen saver which shows when Windows 7 is shutting down. If we are running Ubuntu from a DVD disc or a USB stick we do not get Windows 7 dialogs. We may get something similar looking but as I do not run Windows 7 I do not know what it is you are seeing.

Regards.

---

### Post by Bucky Ball on 2015-07-21
Welcome. That is a point. Are you trying to install Ubuntu inside Windows rather than to its own partition? That option is no longer supported and best to not go there if that is where you're headed. :)

---

### Post by Vladlenin5000 on 2015-07-21
Besides the aforementioned (huge) issue of you possibly installing using Wubi, this also concerned me: 
> **pecanbrown said:**
> In am confused about your post, after often a video issue. I understood nothing after that sentence.

Some clarification is in order.
Some Nvidia cards and, notably, **Nvidia integrated chips of your CPU's era** - pentium dual core - do not play well with the Ubuntu's default open source, hence what comes next to "often a video issue" is a fairly detailed method to add a required parameter, *nomodeset*, in order to boot a graphical installation and/or an already installed system with video (often low resolution) so you can easily add the recommended nvidia proprietary drivers, reboot, and hopefully everything will be fine in the end.
But this is mere speculation. You haven't posted yet your graphics card/chip, please do so the troubleshooting can proceed or, that being ruled out, move on to a different direction.

---

### Post by pecanbrown on 2015-07-26
I am sorry. I have not been back to the forum. I did not understand olfred and I tried to look over the info he told me without success. It has been a about a week since i installed 14 and at the time i was trying so many things that I cannot answer your question properly. What I can tell you is this, I put 14 on a dvd and installed it on my computer from there as a dual boot with win 7. I understand about what I am seeing and what I should see and I do not understand it either but something is terribly wrong with my computer and it has worked properly for a short time and then incorrectly.
This is what happens at the GRUB(what i understand it is the menu whih gives you the choice between ubuntu and windows).
If i choose ubuntu I will see ubuntu for about 2 seconds and then the screen goes black. I wiggle my mouse and I see a half second flash of the rectangle I see when win 7 is shutting down. I have gotten ubuntu 14 to work a couple of times. I installed software and now nothing.

---

### Post by pecanbrown on 2015-07-26
I believe this is my graphics card, Intel(R) G41 Express Chipset

---

### Post by pecanbrown on 2015-07-26
Thank u Vladlenin! for helping me to understand a little better on what is going on. The funny thing is I have tried several things but something is going on with the monitor and now i have lost or messed up 2 usb 3.0, 16 gb drives that are no longer working in ubuntu or win 7. I need help. PLEASE someone. Does it help that I am an American currently living in China, trying to get a PC working properly because my Mac has stopped working. The software has been reinstalled but it is ghost version and the security is not working properly. I do need help.

---

### Post by sandyd on 2015-07-26
Hi, can you boot into Windows 7, and go to Add/Remove Programs.

Is there a program with the name similar to "Wubi" or "Ubuntu" there?

Thanks.

---

### Post by pecanbrown on 2015-07-26
Hi Sandyd, thanks for your speedy response. I can boot into win 7. I ent to the uninstall or change a program. There is not 'wubi' or 'ubuntu' there. Just some of the programs that I have installed, firefox, vlc media.

---

### Post by Bucky Ball on 2015-07-26
> **pecanbrown said:**
> Does it help that I am an American currently living in China ...

Unsure what relevance this has to your problem. This is an international forum and getting support has nothing whatsoever to do with your nationality or location. We are not affiliated with any country or region.

When you get to the list of kernels and Windows at boot, choose the Ubuntu kernel and press 'e'. Find the line that ends in quiet splash and make it look like this:

quiet splash nomodeset

follow the instructions at the bottom of the page to save the changes and continue with boot.

---

### Post by pecanbrown on 2015-07-26
Bucky Ball, I did not mean to offend. I was saying that to give some background into myself and my computer hopefully that would help with solving then issues.

I tried what u said.  I choose 'ubuntu', pressed 'e' and then I went straight to the installed ubuntu where the menu stayed for about 2 seconds and then disappeared. I never got the opportunity to look at a line or add anything to it.

---

### Post by oldfred on 2015-07-26
Nomodeset may not work with Intel video.
And depending on version of Intel, slightly different boot parameters may be required. 
You add these just like nomodeset instructions. Often better to replace the quiet splash, so you can see boot process. Try each of these, not all of them at once. If one does work we can make it a permanent setting. Manually adding at grub menu is a one time change.

 # Usually nVidia or AMD work with this:
nomodeset
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

### Post by pecanbrown on 2015-07-26
So I had to reboot and when i did the video resolution had changed and it was bigger.

---

### Post by pecanbrown on 2015-07-26
Olfred how do i make these changes you mentioned above?

---

### Post by oldfred on 2015-07-26
That may be a default video size like 800x600. 
You may need one of the other settings, I posted above, but using your monitor/screen size.

---

