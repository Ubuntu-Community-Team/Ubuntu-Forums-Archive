---
title: "Clean install of 12.10 on to Dell Workstation 360 PC"
date: 2012-12-14
forum: New to Ubuntu
---

### Post by John butler on 2012-12-14
After 2 false starts . I bought a CD of ubuntu 12.10 from the linux shop to install onto a fully formatted HDD . Dell BIOS shows : " Missing operating system " & will not take me to the CD boot . Can amyone suggest where I go from here ? Pleeese !

---

### Post by dannyboy79 on 2012-12-14
are you able to enter the bios and change the boot order to boot to the cdrom first? OR some computers have a F11 (or similar) button press that will take you to a menu of items to boot to.

---

### Post by GordThompson on 2012-12-14
On Dell machines the key to enter the BIOS setup is usually [F2].

@John

When you power-up the machine and the "DELL" screen appears you should see a prompt that says

F2 = Setup

(often in the top-right corner of the screen). Tap the [F2] key several times until the setup menu appears. 

Once there, look for the menu option that affects the "boot order" and make sure that the CD/DVD drive has priority over the hard disk (HDD). After you exit setup (saving your changes) then the machine should boot from the DVD.

---

### Post by debodas on 2012-12-14
You'll need to change the boot order in your BIOS (press and hold f2 when starting up); set the dvd drive as the top boot priority. Then save changes an exit (normally something like f10, but it will tell you), and it should reboot into the dvd, which you can then install from.

---

### Post by John butler on 2012-12-16
Thanks for the suggestions . I got the machine to start the installation via the CD then got : > I/O Space for GPIO uninitiallised     Screen went to black after a short time and then the dreaded : " Cannot display this video mode "
                Optimum resolution 1280 x 1024 60 HZ 
  What now ??
    This is where I was at my first attempt Oh dear !

---

### Post by GordThompson on 2012-12-16
> **John butler said:**
> I got the machine to start the installation via the CD then got : > I/O Space for GPIO unitiallised     Screen went to black after a short time and then the dreaded : " Cannot display this video mode "
                Optimum resolution 1280 x 1024 60 HZ 
  What now ??
The first thing I would try would be the 'nomodeset' trick. In the instructions [here]("http://ubuntuforums.org/showthread.php?t=1613132"), scroll down a bit to the section "How to enable kernel options on the livecd (before install)".

---

### Post by grahammechanical on 2012-12-16
When the CD first starts to load you see a purple screen with two icons at the bottom. Press Enter. Select your language (default is English) Press enter then press F6. Scroll down the list until you highlight nomodeset. Press Enter to accept the selection of nomodeset and then press ESC to go back to the Try or Install screen.

The session will now run without attempting to determine the correct video mode. This should get you to a Live session or an Install session depending on your choice. The install should succeed. You may need to install a proprietary video driver after installation.

Regards.

---

### Post by John butler on 2012-12-21
Loaded " nomodeset " , then got : .  .  [    52.942595]  lpc_ich 0000:00:1f.o: .
>IO space for GPIO uninitiallized      
  I left this to see if anything would progress , but nothing after 30 minutes ; what should I do now ?

---

### Post by John butler on 2012-12-23
Do I need to install suitable Graphics drivers ? If so , to what spec .

---

