---
title: "Is there a way to make Ubuntu boot first"
date: 2011-09-14
forum: New to Ubuntu
---

### Post by kooba on 2011-09-14
...without having to experience the boot screen?

I'd rather have Ubuntu boot first than have to deal with the menu everytime I turn the computer on.  
Thanks guys.

---

### Post by Rex Bouwense on 2011-09-14
There sure is.  I am assuming you have a dual boot and not a WUBI install.  Is that correct?

---

### Post by mikewhatever on 2011-09-14
If you don't see the boot menu, how are you going to boot other OSs (presumably Windows)?

---

### Post by Lisiano on 2011-09-14
Ubuntu is always default if you installed from the CD/USB. If you are using Wubi then boot Windows and do this
Right click Computer -> Properties -> Advanced System Settings (Just Advanced if on XP) -> Startup and Recovery (Settings) -> Pick Ubuntu instead of Windows -> (Optional) Decrease the time the menu is shown -> OK -> OK -> Reboot.

You can disable showing the list if you want to but then to see the list you must hold F8.

Under GRUB you need to change a file. Press ALT+F2 and type ```
gksudo 'gedit /etc/default/grub'
``` and change ```
#GRUB_HIDDEN_TIMEOUT=0
```to ```
GRUB_HIDDEN_TIMEOUT=0
```
Then hold Shift whenever you want to see a list

EDIT: Also open a terminal (CTRL+ALT+T) and type ```
sudo update-grub
``` and wait until it is done

---

### Post by Rex Bouwense on 2011-09-14
Mike, you just read his post different than I did.  I guess that is what happens when we do not get enough information from the OP.  I just thought he wanted to change his default OS so Ubuntu booted and he didn't have to fool with the menu (unless he wanted to boot something else).

---

### Post by kooba on 2011-09-14
Sorry for the lack of info'.  I have Win7-64 on an SSD at the moment. On my old Dell laptop I did a WUBI install of Ubuntu 11.04 and love it. 
So, I'd like to install 11.04 on my desktop and use it for surfing (which is all I really do, along with photo editing).  Didn't know that a CD and WUBI install would be different in logging in? 
I thought the only difference between the two would be the process of installing.  Unless I misunderstood?  Thanks.

---

### Post by Rex Bouwense on 2011-09-14
There is a difference although using it you would probably not notice it until something broke.  WUBI is normally used to try out the OS.  If you decide that you like it, generally a full install on it's own partition follows.  That of course is not a rule and some people continue to use Ubuntu that was WUBI installed for a long time.

---

### Post by Lisiano on 2011-09-14
Difference between Wubi and CD:
1) Wubi can be uninstalled. CD can not.
2) Wubi boots by using the Windows bootloader. CD uses GRUB.
3) Wubi creates a file and installs everything in it (Like Virtual machines). CD uses a actual partition.

Else, most stuff is exactly the same. But it is recommended to install via CD to avoid future problems (Reinstalling Windows kills the Wubi install, etc)

---

### Post by Rex Bouwense on 2011-09-14
So, unless I am thoroughly confused you want to install Ubuntu on your desktop which I take already has Windows installed.  This one is easy.  If you have a bootable CD with 11.04 on it slide it into the tray and turn the computer on.  Make sure that booting from the CD is ahead of the hard drive and when the screen comes up asking you what you want to do, select try Ubuntu.  This done to see if it will work with your hardware and if all of the programs work.  You can skip this step and many people do.  After you are satisfied select install Ubuntu and you will be asked how you want to install.  Most people select install side by side.  If that is what you want, select it and sit back for 20-30 minutes while Ubuntu installs.  Go get a cup of coffee and enjoy.

---

### Post by kooba on 2011-09-14
I appreciate the replies, the WUBI/CD explanation helped.

Now when I install via the CD on my desktop alongside Windows 7, I'll no doubt get a menu listing the 2 OS, Linux and Windows 7.  Then of course I have to choose the OS and hit enter, that's what I want to avoid.

I'd rather turn my computer on and have it boot straight into Ubuntu.

---

### Post by Rex Bouwense on 2011-09-14
That solution was given to you by Lisiano (post #4).  However, if you change to timeout value to 0, you will never be able to boot into Windows.  If that is what you want change it to 0.

---

### Post by qamelian on 2011-09-14
Ubuntu will boot automatically after a 10 second delay. You don't need to interact with the boot menu at all unless the delay bothers you.

---

### Post by kooba on 2011-09-14
Saw post #4 after the fact, thanks again guys, really appreciate the quick help with all this.
\\:D/
I'll just set my value to something less than 10.  I'm impatient and sometimes I do walk away from the computer, but that's a learned behaviour from years of Windows usage and its boot up times.
Hence the reason I'm slowly switching to Linux.
Now if only Photoshop CS5 would be easier to install and run via Wine/Linux.

---

### Post by Rex Bouwense on 2011-09-14
I know that this is off the subject and I'll probably get axed but take a look at GIMP.  It might do what you need to do.

---

### Post by Lisiano on 2011-09-16
I'd like to remind that holding/rapidly pressing Shift/Esc should make GRUB show the menu even on a 0s timeout. Same with Windows if you try loading it from GRUB (Second you press the Win7 entry, start holding F8 and you'll get the Windows booting options like safe mode, etc)
So it is possible to boot with a 0s delay, in both Win and Lin.

---

### Post by bcbc on 2011-09-16
> **Lisiano said:**
> I'd like to remind that holding/rapidly pressing Shift/Esc should make GRUB show the menu even on a 0s timeout. Same with Windows if you try loading it from GRUB (Second you press the Win7 entry, start holding F8 and you'll get the Windows booting options like safe mode, etc)
So it is possible to boot with a 0s delay, in both Win and Lin.

I've seen many forum posts from people who've set the timeout to 0 on Vista/Win7 and holding F8 does not bring up the windows boot manager. So setting Wubi as the default and the timeout to 0 (and also 1) is not recommended. If you want Ubuntu as the default it's time to consider a normal install - or just live with a countdown of 10.

Future Wubi releases plan to hide the second boot menu (grub2) on wubi installs, but so far in the current dev release this isn't working.

---

### Post by Lisiano on 2011-09-16
I always get the menu when I hold F8 the few hundred milliseconds after I press Enter on the Win7 entry. That is before even my GRUB background disappears. I'm going to try setting that to 0 on my netbook and get the menu (Ubuntu, Backtrack, Win7 triple boot).

EDIT: Disabled the list in Win7. Rebooted. Selected Win7. Held F8. Got the Advanced Boot Options. Pressed Esc and got my humble list of only Win7.

EDIT 2: I wouldn't have said it would work if I didn't know it from my experience. When I was trying out a Win7 driver that would let it use Swap as a pagefile (Decided to not do it later) I used that method to disable Driver Enforcement on my desktop (Ubuntu, Win7 - Dual boot).

---

### Post by bcbc on 2011-09-16
> **Lisiano said:**
> I always get the menu when I hold F8 the few hundred milliseconds after I press Enter on the Win7 entry. That is before even my GRUB background disappears. I'm going to try setting that to 0 on my netbook and get the menu (Ubuntu, Backtrack, Win7 triple boot).

EDIT: Disabled the list in Win7. Rebooted. Selected Win7. Held F8. Got the Advanced Boot Options. Pressed Esc and got my humble list of only Win7.

EDIT 2: I wouldn't have said it would work if I didn't know it from my experience. When I was trying out a Win7 driver that would let it use Swap as a pagefile (Decided to not do it later) I used that method to disable Driver Enforcement on my desktop (Ubuntu, Win7 - Dual boot).
Are you saying you tested this with Win7 as the default OS? It's not clear. I can point you to any number of threads where setting Ubuntu (wubi) as the default and the timeout to 0 prevents booting into Windows.

Based on this I think it's prudent to warn users not to do this.

---

### Post by Lisiano on 2011-09-16
Gah. I don't know how but I misread what you said. But testing this in a VM (Vanilla Win7), holding does not trigger the Advaced Boot Options BUT rapidly clicking DOES. Since it's a VM I could make a screencapture showing that it works. Currently I'm off to harrass a system with Win7. It previously had XP on it. I'll edit this post after I get the result.

EDIT: YES. YES it works. So it works on VM's, Win7 on metal, GRUB -> Win7 (With list), GRUB -> Win7 (No list).
Although the last test machine did start beeping due to too rapid pressing of F8... Actually because I started pressing too soon (POST didn't even end)

EDIT 2: I could continue this testing further with installing a fresh Win7 and Wubi on a VM. But due to the way the Win Bootloader works (In fact any bootloader), it shouldn't make any difference what is it's default menu entry.

---

