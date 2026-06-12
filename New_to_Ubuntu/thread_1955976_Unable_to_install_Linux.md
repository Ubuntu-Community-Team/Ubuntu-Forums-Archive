---
title: "Unable to install Linux"
date: 2012-04-10
forum: New to Ubuntu
---

### Post by saagar on 2012-04-10
Hi everybody, 
I am **unable to install any linux **on my desktop. Well, I **am not a beginner** but .....

Every linux installation hangs on black screen just after i select install from boot options.
I tried with Ubuntu, Fedora and openSuse.
Even live cd is not booting.
What to do ??
Am having windows XP installed right now.

---

### Post by TeoBigusGeekus on 2012-04-10
Are you sure you've burnt the isos correctly?
Have you per chance created data cds with the iso files in them?

---

### Post by ravinfy on 2012-04-10
Oh yeaa! TeoBigusGeekus is right... 
If you are planning on installing from a Pen Drive, dont just copy the ISO image on to the pen drive and expect it to boot from it... you need to convert it to a Bootable disk. 

See some notes I wrote about a similar issue: 
[http://ubuntuforums.org/showthread.php?t=1954735]("http://ubuntuforums.org/showthread.php?t=1954735")

Hope this helps.. we`l be happy to help if you need any more info.

---

### Post by scottstensland on 2012-04-10
on boot up when you see the purple screen hold down shift and it will show
the ubuntu options screen - hit F6 which shows how to disable
various kernel options - specific to each laptop, ubuntu will go
black screen if it cannot handle all these options activated.
Try various combinations - for my laptop I need to disable :

noacpi 
nomodeset

ubuntu will work - it may take some trial and error though

Answer back if it gets frustrating
Good Luck

Scott Stensland

---

### Post by muteXe on 2012-04-10
i dont't think it has anything to do with ubuntu specifically, as the OP has tried three different distributions. 
what about if you select the "try without installing" option rather than the install option?

If you've installed XP, boot into that, put in one of your linux cd's. Can you see the contents of the disk in windows explorer?

---

### Post by ravinfy on 2012-04-10
Nice thought, muteXe! 
Saagar, I would try muteXe`s idea first - how about you "Try Ubuntu" from within your Windows XP first? 

Let us know if it works and/or you see the "Install Ubuntu" prompt and we can take it from there... 

Ravi

---

### Post by mastablasta on 2012-04-10
try to boto with nomodeset or some other boot option:

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by Peripheral Visionary on 2012-04-10
On my old Dell there's a big DELL screen that appears at first power-on and lasts only a few seconds. During that short window of time I press F12 a few times to enter the boot menu and then select "Boot from CD-ROM drive" and hit ENTER. With my LiveCD (the iso file - *image*, not data) in the CD-ROM device at boot up, it then boots into whatever is on my LiveCD.

I realize you're not a newbie, but believe it or not, even experienced users fall back on old habits like looking for an Auto-run kinda thing on a CD. Just offering it for the benefit of others who might be helped...

---

### Post by critin on 2012-04-10
> **Every linux installation hangs on black screen [COLOR=Red]just after i select install from boot options[/COLOR]**.
I tried with Ubuntu, Fedora and openSuse.
**Even live cd is not booting**.

If you're getting to the TRY, INSTALL, screen, it is booting.  Black screens at this point could be a graphics issue.  Is the live cd that doesn't boot the same cd as the one that gave you choices?  

Using the cd that gave you the choice to install, choose TRY instead.  Then if you get to the desktop without dark screen, choose to install from the desktop option.

It may be a bad burn if none of the cds work.  I prefer installing with flash thumb drives, it rarely misbehaves and it saves on cds too.  unetbootin works for me.

---

### Post by saagar on 2012-04-11
Thanks everybody..
This is what happens when i try Ubuntu WUBI... It installs inside windows and after reboot
shows some "Try(hd0 .... error prefix" something.. for a very short while and then hangs on
"Completing the Ubuntu installation. For more inst. boot options press 'ESC' now. 0"

If i hit ESC before timeout then no option there, except ACPI workaround, is working. 
When i start with ACPI Workaround, it completes the later part of installation and after the next reboot shows me the GRUB screen. But selecting the normal Ubuntu startup hangs on the purple screen. Cant do anything there. Neither shift key nor CTRL+ALT+DEL works there.

---

### Post by saagar on 2012-04-11
I tried two of the linux, opensuse and fedora by installing them from Pen Drive.. For that i used UNetBootin... Even that is not working... Fedora hangs on white screen with a blinking cursor on top-left corner and opensuse on that green screen with a chameleon !! same happens using cds..

---

### Post by critin on 2012-04-11
Ah, Wubi.  That's different.   It won't boot to install, it installs inside of windows like any windows app.  Does your installer look like this one?  It's easier than using just the .exe for me. 

You'll need to uninstall/delete any previous references to wubi in Windows before it will work.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by anejo on 2012-04-11
You don't say how old the machine is... but on a Lenovo W500 I had a similar experience. Went back to a previous version. I was telling a Microsoft support person (hey... don't mock me!) my story and he smiled and came did a BIOS update. The live-CD stopped manifesting black screens... and the rest is history.

---

### Post by saagar on 2012-04-11
Hey Guys,
**Problem solved!**
problem was of something called ACPI
I set it off and Ubuntu installed properly and then i edited the grub and set it off permanently!
**Thanks** for your support!

---

### Post by saagar on 2012-04-11
Special thanks to [scottstensland]("http://ubuntuforums.org/member.php?u=932572")
Thanks a lot!

---

