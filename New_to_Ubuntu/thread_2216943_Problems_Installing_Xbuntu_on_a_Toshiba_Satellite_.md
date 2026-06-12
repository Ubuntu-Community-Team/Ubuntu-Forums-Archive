---
title: "Problems Installing Xbuntu on a Toshiba Satellite 5000, Pentium III"
date: 2014-04-14
forum: New to Ubuntu
---

### Post by ross4 on 2014-04-14
After some research, I decided to try Xubuntu on my old Toshiba laptop (Satellite 5000, see specifications at end) but I have not been able to get very far.
 
Steps so far:
Burned a CD of Xubuntu 12.04.4 desktop i386, booted it on my Toshiba Satellite P100 ( a somewhat newer laptop). Works fine in LiveCD mode (even detected my WiFi).
 
Tried booting it on the Satellite 5000 various times with somewhat different results, depending on what steps I took:
 
1.     Straight boot: CD starts up, runs for a short time, screen goes white and stays that way.
 
After that, using a single keystroke to get to the boot menu, I have tried:
 
1.      Deleting the ‘quiet splash’ and then pressing ‘enter’: lots of text whizzing by, -> top 1/3 of screen retains text & and bottom 2/3 fades to grey, finally all white screen and stays that way
2.     Using F6, selecting ‘nomodset’ at the boot menu: after a short time, “Xubuntu 12.04” appears on black screen with dots moving across under it, presumably showing progress, 1-2 minutes or so of CD activity then text (some white, some yellow & one red ‘fail’) flash across the screen too quickly to read, screen turns completely black and stays that way.
3.     Using F6, selecting ‘acpi=off’: much the same results as #2 above but no ‘fail’ text and the screen showed a very brief flash of a narrow band of scrambled colours. Then black.
 
I tried a few other boot line commands (i915.modset=0, vga=771) but the results always end in either a white screen or a black screen. I figure it is about time to ask for help rather than getting into endless combinations of parameters (if that is the right term).
 
If anyone KNOWS of any available distribution of any flavor of Linux that will work on my machine, I will be happy to drop this and use that.
Otherwise, any suggestions?
 
My machine:
Toshiba Laptop Satellite 500
Intel Pentium III processor
1.10  GHz, 512 MB of RAM, available hard  drive space 26.7 GB
Video Card: NVIDIA GeForce4 440 Go
 
Regards,
Ross

---

### Post by mörgæs on 2014-04-14
Hi, welcome to the fora.

Sorry for giving you this answer to your first post, but I would consider a Pentium 3 too slow to be of any practical use. You could try a [minimal Lubuntu]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall") in combination with the boot options you mentioned, but that's not the main problem. 

If you get an operative system running, which browser, media player, <insert other applications here> runs satisfactory on such hardware?

---

### Post by aeyeaws on 2014-04-14
p3 will run everything except for flash aplhonse. kthxbye

---

### Post by ibjsb4 on 2014-04-14
Yes, instead of FF or Chome, you will be looking at browsers like Arora and Midori or less.


Xubuntu is too heavy for you.  What I would be tempted to try would be Lubuntu Alt-install CD and do a full install.


[https://help.ubuntu.com/community/Lubuntu/Alternate_ISO](https://help.ubuntu.com/community/Lubuntu/Alternate_ISO)


This iso can also be used for a minimal install.

---

### Post by ross4 on 2014-04-14
Thanks for the various replies.
I will be quite happy to try Lubuntu but it seems to me, and I am indeed an absolute beginner at Linux, that my immediate problem is getting past the white screen/black screen problem. If I try something like Lubuntu, won't I just as likely run into the same situation? 

I would like to begin by using a LiveCD approach so that I can see if whatever I use will actually operate, even at a minimal speed, on the old Satellite 5000. If it does, I'll try an actual install of whatever distribution I can get to work.

---

### Post by mörgæs on 2014-04-15
There's a reason that I didn't point you to a live system: It's unlikely that it works on your hardware.
Best option is a non-graphical install.

---

### Post by roger_1960 on 2014-04-15
Hi

Yes, I would try a non graphical install of Lubuntu.  If no good then puppy linux should work.  I have also had success with Bodhi Linux (uses ubuntu repositories) on old laptops.

Roger

---

### Post by ibjsb4 on 2014-04-15
Another P3

[http://ubuntuforums.org/showthread.php?t=2216372](http://ubuntuforums.org/showthread.php?t=2216372)

---

### Post by baphomet2 on 2014-04-15
Another choice could be to install Ubuntu server, run the update/upgrade, install/check the video driver, then install whichever desktop system you want (xubuntu-desktop, etc).

---

### Post by oldfred on 2014-04-15
With nVidia you will need nomodeset. And that is an old video chip, so older driver would be required.

i915.modset=0, vga=771
The i915 is for systems with Intel video chips.
And the vga=??? is obsolete setting.

---

### Post by ross4 on 2014-04-15
Success!
Well!!! Thanks to everyone who suggested things! I decided to try Lubuntu 13.10. Downloaded it, burned it, checked it and booted it. I am now writing this message on Firefox on Lubuntu on my rather ancient (and, yes, rather slow) Toshiba 5000 from the CD. I guess my next step is to actually install it on this machine and then starting learning more about Linux.

As I said, I am a total novice at Linux so I'll probably be starting a few new threads on the forum soon (e.g. Tried to install and Screwed up ...)

Again, thanks to all who helped.
Ross

---

### Post by ibjsb4 on 2014-04-15
keep us posted  :)

---

### Post by ross4 on 2014-04-16
Well, I installed Lubuntu on my system using the alternate install and all went well. However, when the machine re-booted, I was faced with that white screen again.

Now I am not sure where to go. I think it might be because I need to somehow install the correct Nvidia drivers which can be found at nividia.com. 

I'm not sure if this is relevant or not, but I don't think I selected 'nomodest' when I ran the installation. Does that information somehow get passed to installation? If so, should I just re-boot from the CD and re-install? Or, is there a key stroke I can use after booting or mid boot to get me to a text screen (and then what do I do)?

Any suggestions on my next step? 

Thanks in advance.
Ross

---

### Post by oldfred on 2014-04-16
Do not install from nVidia, use repository. 

You have to specify nomodeset on grub menu. If you just installed Lubuntu, you will not automatically get grub menu as you only have one system and it is pretty sure that is what you want to boot.
If you hold shift key down from BIOS menu should then appear.

Use e on first entry, scroll to linux line and replace quiet splash with nomodeset.

       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Last part of first screen shows some examples of grub.

It looks like the 96.xxx legacy driver may be correct.
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)
Not sure how Lubuntu does it, but Ubuntu has system drivers update.

---

### Post by ross4 on 2014-04-17
Thank you! With those clear, concise instructions I was able to boot up and log in to my 'new' Lubuntu laptop. I'm looking forward to playing around with it and learning a bit about Linux in general.

---

### Post by ross4 on 2014-05-04
I'm posting this on Absolute Beginners because that is what I am but it may be better under a different section. I am trying to figure out how to install a driver for my NVIDIA GeForce4 440 Go card on my Toshiba Laptop Satellite 500
(Intel Pentium III processor 1.10 GHz, 512 MB of RAM, available hard drive space 26.7 GB). I just installed Lubuntu 14.04 (and did an up-date).  I've done a lot of searching and even downloaded the legacy GPU version 96.43.21. First, though, I thought I would try the ubutntu documentation page BinaryHowtoNvidia. There, I get lost. I never got any message saying restricted drivers are available. When I try to follow the second suggestion: go toSystem -> Administration -> Additional Drivers. I can't this path. If I try Preferences->Additional Drivers (which kind of looks like the right way to go),  a search starts and, after quite a while the message comes back: "No additional drivers available". The next suggestion on this help page is to install using commands but when I go to LXTerminal and type in the first command "jockey-text --help", the response is "command not found'.

I'm feeling quite frustrated because I have been doing my best to search out answers without starting a new thread here but so far no luck.

Btw, the reason I want to install the drivers is that with the present (and only) display option, the print is too small for my aged eyes.

Thanks for any help that anyone can give.

---

### Post by mörgæs on 2014-05-04
Threads merged. Since this is the same hardware it's better to keep it all in one thread.
I have removed the 'solved' flag.

---

### Post by ibjsb4 on 2014-05-04
> Btw, the reason I want to install the drivers is that with the present  (and only) display option, the print is too small for my aged eyes.

I hear ya, got the same thing going on.  I don't know about your drivers, but wondered if you know about this.

[http://ubuntuforums.org/showthread.php?t=1924290&p=11683606#post11683606](http://ubuntuforums.org/showthread.php?t=1924290&p=11683606#post11683606)

---

### Post by ross4 on 2014-05-05
Thank you! A big help.  Now installing the drivers is not as urgent a priority, though, in the interest of learning more about Lubuntu and linux I would like to know how to do it. 
Thanks again.

---

### Post by ibjsb4 on 2014-05-05
> in the interest of learning more about Lubuntu

Check it out :)

[http://ubuntuforums.org/showthread.php?t=1844755](http://ubuntuforums.org/showthread.php?t=1844755)

---

### Post by ross4 on 2014-05-08
Wow, more than enough!
Thanks

---

