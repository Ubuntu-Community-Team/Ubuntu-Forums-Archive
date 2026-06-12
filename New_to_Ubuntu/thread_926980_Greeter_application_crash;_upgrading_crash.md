---
title: "Greeter application crash; upgrading crash"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by ZipGun47 on 2008-09-22
I had been running 7.04 for a while, and finally decided to upgrade to 7.10. While letting the upgrade process run via the package manager, the process froze and I had to turn the computer off. When I re-booted, there were various issues that stemmed presumably from the upgrade crash, but the system worked in a basic fashion (I could use Firefox, for example). So I tried re-running the upgrade again. This time, it seemed to go through without issue, but now I get a greeter application crash message when I try to boot up Ubuntu. The only way to get anywhere is to start up using my boot disc, but this only takes me to a generic desktop as I can't log in under my user name. 

My question is, how do I fix this? Any help, in the most dumbed down language possible, would be greatly appreciated. I've seen a few threads about greeter crashes, but none of them seemed to apply to my situation or made any sense in terms of what I might need to do. Thanks.

---

### Post by northern lights on 2008-09-22
Can you please give the error message verbatim and describe at what point in the boot process it appears? Thank you.

---

### Post by ZipGun47 on 2008-09-22
Sure, right before the log in screen appears, after having run through the start up procedures, a small window appears stating "The greeter application appears to be crashing. Attempting to use a different one." There is a button to click Okay, which results in some further start up procedures, which leave off at "Running local boot scripts (/etc/rc.local), at which the system seems to hang. 


Not sure if it relates in anyway, but on the startup screen prior to attempting to load the log in, after "Starting kernel event manager," it states: udevd[2686] udev_rules_init: could not read 
'udev/rules.d/libmtp.rules': no such file or directory

---

### Post by northern lights on 2008-09-22
Upon booting, select "Recovery Mode" from the GRUB menu.
Should the menu not appear automatically, hit 'ESC' when you see "GRUB loading - Stage 1.5" on the screen.

Run ```
sudo vim /etc/gdm/gdm.conf-custom
``` to open 'gdm.conf-custom'

Press i to enter into insert mode. Locate the following line```
GtkModulesList=gail:atk-bridge:/usr/lib/gtk-2.0/modules/libdwellmouselistener:/usr/lib/gtk-2.0/modules/libkeymouselistener

``` and comment it (put a pound/hash/'#' in front of the line).

Hit 'ESC' and type```
:wq
```to save and quit.

Reboot.

Hopefully, the greeter won't crash.

---

### Post by ZipGun47 on 2008-09-22
Okay, I hit ESC and got a list of Ubuntu, kernel 2.6.20-17 and so on. Hit 'c' for a command line, and entered the first command. However, it gave me a "Error 27 - Unrecognized command' response. Now what?

---

### Post by northern lights on 2008-09-23
> **ZipGun47 said:**
> Okay, I hit ESC and got a list of Ubuntu, kernel 2.6.20-17 and so on. Hit 'c' for a command line, and entered the first command. However, it gave me a "Error 27 - Unrecognized command' response. Now what?
Please enter the Recovery Mode, i.e. what is most likely the second option in the menu. The GRUB command line is useless. How did you get the idea of hitting 'c' - I don't recall writing that...
:)

---

### Post by ZipGun47 on 2008-09-23
Sorry, I had forgotten than reocvery mode meant booting from the CD rather than the hard drive. At least I hope that's what you meant. At no point does it say GRUB loading stage 1.5 either, but anyway.


I booted in recovery mode, and upon reaching the desktop, accessed the terminal window and executed the command above, and hit 'i'. I see the INSERT mode, but there is only the GDM Configuration Customization File instructions, and then bracketed selections like [daemon], [security], and so on. How do I see the line you are telling me to comment out? Or did I do something wrong again? Which is probably the case?

---

### Post by northern lights on 2008-09-23
> **ZipGun47 said:**
> Sorry, I had forgotten than reocvery mode meant booting from the CD rather than the hard drive. At least I hope that's what you meant. At no point does it say GRUB loading stage 1.5 either, but anyway.
[...]
Or did I do something wrong again? Which is probably the case?
Unfortunately you did.

"Recovery Mode" does not mean booting from CD at all. It should be an entry in the GRUB menu.
The menu will by default appear if you installed Ubuntu aside Windows (or any other OS). If Ubuntu is the only OS installed, you have to make it appear by hitting 'ESC' during the boot process. After BIOS and CMOS did their thing, "Stage 1.5" should appear on the screen for 1 to 3 seconds.

---

### Post by ZipGun47 on 2008-09-23
Okay, I'm confused. This is what I get when I hit ESC after the initial bootup (at no point does it say GRUB loading stage 1.5 though):
Ubuntu, kernel 2.6.20-17-generic
Ubuntu, kernel 2.6.20-17-generic (recovery mode)
Ubuntu, kernel 2.6.20-16-generic
Ubuntu, kernel 2.6.20-16-generic (recovery mode)
Ubuntu, kernel 2.6.20-12-generic
Ubuntu, kernel 2.6.20-12-generic (recovery mode)
Ubuntu, kernel 2.6.20-11-generic
Ubuntu, kernel 2.6.20-11-generic (recovery mode)
Ubuntu, kernel 2.6.20-10-generic
Ubuntu, kernel 2.6.20-10-generic (recovery mode)
Ubuntu, memtest86+

I picked the second one, and it ran through some further processing and gave me a command line. I entered the first command per your post above, and got the same thing as I did before, namely a bunch of text and the bracketed terms I mentioned above. What am I doing wrong?

---

