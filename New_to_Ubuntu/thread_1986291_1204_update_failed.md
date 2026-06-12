---
title: "1204 update failed"
date: 2012-05-24
forum: New to Ubuntu
---

### Post by leedsal on 2012-05-24
Hi everyone.

I have no great knowledge of UBUNTU and have come unstuck updating from 11-10 to 12-04. I have previously downloaded new systems onto a cd and updated my computer from the cd. On this occaision I decided to download 12-04 from the software centre direct. The download stopped before completion and the system just froze. I am now  unable to  start the computer. I have tried to use a live cd but this won't load either.

I'd be most grateful if anyone can help.

Cheers

Leedsal

---

### Post by QIII on 2012-05-24
Can you explain what you mean by "unable to start the computer"?

---

### Post by recap on 2012-05-24
Sounds like hardware failure...?

---

### Post by leedsal on 2012-05-24
Hi,

Thanks for getting back. When I attempt to start the computer it goe to a screen that has a heading-

GNU GRUB version 1.99-12ubuntu5.

Below this I have options of-

Ubuntu, with Linux 3.0.0-17-generic (recovery mode)
Previous Linux versions
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)

There are instructions at bottom of screen telling me to select one of the above

---

### Post by QIII on 2012-05-24
If there is not one above the one that says "recovery mode", select previous versions and let us know what happens.

Use the arrow keys on your keyboard.

---

### Post by leedsal on 2012-05-24
Hi QIII,

My mistake, selected the top option. Now have purple screen. In the middle of screen it says ubuntu, underneath this writing is 5 dots that change in colour from white to red in succession

---

### Post by QIII on 2012-05-24
And that goes on indefinitely?

I suspect you attempted to reinstall without first disabling or un-installing your video driver.

Start again and select recovery mode.  When you get there, you should have a choice to continue booting.  Select that.

Your boot will continue in verbose mode with a lot of scrolling text.  It will probably die somewhere.  Jot down some notes on what it says and let us know.

---

### Post by leedsal on 2012-05-24
Thats as far as it gets!

---

### Post by leedsal on 2012-05-24
Hi QIII,

Thanks for your time. After I've selected recovery mode I get the scrolling text as you suggested. When this stops it goes on to a window with the heading-

Recovery Menu (filesystem state: read only)

In the window it gives the following options

resume                            Resume normal boot
clean                               Try to make free space
dpkg                                Repair broken packages
failsafeX                          Run in failsafe graphic mode
fsck                                 Check all file systems
grub                                Update grub bootloader
network                           Enable networking
root                                Drop to root shell prompt
system-summary             System summary

[CENTER]Ok
[LEFT]If I try using the arrow keys to select one of these options the screen goes back to  the purple ubuntu screen with the white dots. The only difference is that the screen now says Ubuntu 11.10
[/LEFT]
[/CENTER]

---

### Post by Senior_Buckethead on 2012-05-24
Graphics problems can be a real problem during installs. Does your motherboard have onboard video? If it does Id suggest that you take out your graphics card and boot using onboard video.
I know my graphics card created all sorts of problems during install.

If you cant get ubuntu to play nice at all and run from Live CD, and you cant get any of the boot install options to work, perhaps you could try partition magic, which is a separate iso that runs as a live CD. I have used it lots and its great for rescuing files from systems that dont boot (especially non compliant windows machines).  Using partition magic to remove any personal files you have on your machine and then cleaning the drive and starting again.

Partition magic can be found here:
[http://partedmagic.com/doku.php?id=downloads](http://partedmagic.com/doku.php?id=downloads)

Just a thought.

---

### Post by QIII on 2012-05-24
The "Blast off and nuke 'em from orbit" method does not solve the problem.  There is no reason to do a new install at this point. 

What graphics card do you have?

---

### Post by leedsal on 2012-05-24
Thanks Senior_Buckethead, I'll need to look into that. This is starting to sound a little more serious than I thought!

---

### Post by QIII on 2012-05-24
Don't arm the nuke.  This is probably not difficult.

Your graphics card?

---

### Post by leedsal on 2012-05-24
Not sure what graphics card I have. Will need to do a little research. The machine is a Novatech laptop, model A15A

---

### Post by QIII on 2012-05-24
Intel graphics.

I have some things I need to get to, so I have to go.

Please see darkod's post (#2) here:

[nomodeset]("http://ubuntuforums.org/showthread.php?t=1986166&highlight=nomodeset")

---

