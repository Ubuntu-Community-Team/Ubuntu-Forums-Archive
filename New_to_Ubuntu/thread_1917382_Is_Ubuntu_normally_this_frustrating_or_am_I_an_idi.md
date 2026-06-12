---
title: "Is Ubuntu normally this frustrating or am I an idiot?"
date: 2012-01-29
forum: New to Ubuntu
---

### Post by Agent Foxtrot on 2012-01-29
I received a not-very-old HP Pavilion d4000 from my dad that had no HDD and a busted PSU.  I installed a fresh PSU and a virgin Western Digital 320GB hard drive into it, then installed Ubuntu 11.10 off a boot disk and installed GNOME 2.  Things starting going downhill when I met a sound issue/video driver issue.  I posted a question in [this thread which largely went ignored]("http://ubuntuforums.org/showthread.php?t=1912827").

Now I'm running into another issue: Ubuntu hangs at the startup screen, and I have no idea why.  So far it's been 30 minutes and it's still hanging.  Reboots do nothing.  I've tried getting into the GRUB menu by holding down Shift at boot, but it still goes to the Ubuntu startup screen.

I've heard over and over again that Ubuntu is the friendliest distro to newbies, but I'm not seeing it.  I'm a computer science major and while new to Linux, I know my way around a box.  

Any ideas on what I can do?  Is Ubuntu usually this difficult to get working?

---

### Post by Kixtosh on 2012-01-29
First of all ... I think you're probably an idiot! ... :shock: ... :tongue: ... :biggrin:

Secondly, why in particular are you installing Gnome 2? Usually, just installing Ubuntu gets most people where they need to be for regular usage.

---

### Post by anewguy on 2012-01-29
Fresh install = can be blown away with no damage. So......

- get the 32-bit desktop ISO then verify the md5sum

- burn the ISO to a CD at a slower speed

- boot the CD
 
- select install

- at partitioning be sure the existing (except swap - it won't matter) are marked for formatting

- when it finishes, remove the CD and reboot

- what happens?

- don't try installing Gnome 2.  Instead, follow the sticky on the forum for bringing back the Gnome desktop in place of unity.

Dave ;)

BTW - remember what I always say "that's MISTER idiot to you!"  ;)

---

### Post by mikewhatever on 2012-01-29
Installing Gnome2 on 11.10 is a bad idea. It will most certainly break things. Do you, by any chance, mean the fallback mode of Gnome3?

---

### Post by dodo3773 on 2012-01-29
There has been quite a few people with problems regarding shutdown and boot lately. You are not alone but you are definitely an idiot hahahaha just kidding. I am not 100% sure but I think these problems may be related to the new display manager. Maybe try switching to gdm. Here is a link on how to do it:

 [http://www.webupd8.org/2011/07/how-to-switch-between-gdm-lightdm-or.html](http://www.webupd8.org/2011/07/how-to-switch-between-gdm-lightdm-or.html)

Now the next question is: How are you going to try it if you cannot boot your system? Maybe you could switch to an available tty by pressing ctrl+alt+f2 (or f1, f3, f4 (it does not matter which; usually by default there are 1-6 with 7 being your gui or X ) ). After that log into the console any type startx. I do not see why that would not work if is in fact a dm issue.

---

### Post by Kixtosh on 2012-01-30
> **anewguy said:**
> Fresh install = can be blown away with no damage. So......

- get the 32-bit desktop ISO then verify the md5sum

- burn the ISO to a CD at a slower speed

- boot the CD
 
- select install

...

- don't try installing Gnome 2. ...

BTW - remember what I always say "that's MISTER idiot to you!"  ;)

What he said!

---

### Post by Agent Foxtrot on 2012-01-30
> **Kixtosh said:**
> First of all ... I think you're probably an idiot! ... :shock: ... :tongue: ... :biggrin:

Secondly, why in particular are you installing Gnome 2? Usually, just  installing Ubuntu gets most people where they need to be for regular  usage.I didn't      know I could "switch back" to GNOME... I thought I had to install it.

[QUOTE=anewguy]Fresh install = can be blown away with no damage. So......

- get the 32-bit desktop ISO then verify the md5sum

- burn the ISO to a CD at a slower speed

- boot the CD
 
- select install

- at partitioning be sure the existing (except swap - it won't matter) are marked for formatting

- when it finishes, remove the CD and reboot

- what happens?

- don't try installing Gnome 2.  Instead, follow the sticky on the forum for bringing back the Gnome desktop in place of unity.

Dave :wink:

BTW - remember what I always say "that's MISTER idiot to you!"  :wink:[/QUOTE]What's the benefit of burning a CD slower?  Make sure the existing *what* are marked for formatting?

[QUOTE=dodo3773]There has been quite a few people with problems regarding shutdown and  boot lately. You are not alone but you are definitely an idiot hahahaha  just kidding. I am not 100% sure but I think these problems may be  related to the new display manager. Maybe try switching to gdm. Here is a  link on how to do it:

 [http://www.webupd8.org/2011/07/how-t...ightdm-or.html]("http://www.webupd8.org/2011/07/how-to-switch-between-gdm-lightdm-or.html")

Now the next question is: How are you going to try it if you cannot boot  your system? Maybe you could switch to an available tty by pressing  ctrl+alt+f2 (or f1, f3, f4 (it does not matter which; usually by default  there are 1-6 with 7 being your gui or X ) ). After that log into the  console any type startx. I do not see why that would not work if is in  fact a dm issue.[/QUOTE]Sorry, what are tty and gdm?

---

### Post by anewguy on 2012-01-30
Let's see:

> Make sure the existing what are marked for formatting?
- at partitioning be sure the existing (except swap - it won't matter) are marked for formatting ====>>>>>_partitions!_


> I didn't know I could "switch back" to GNOME... I thought I had to install it.  Hence my:

- don't try installing Gnome 2. Instead, follow the sticky on the forum for bringing back the Gnome desktop in place of unity.

Look at the 1st page of the forum - one of the stickies is for using gnome.


> What's the benefit of burning a CD slower?

Many CD's have been burned that installed fine but then Ubuntu had problems.  Going back and burning the CD at a slower speed seems to fix that.  Checking the md5sum is the only way to know you got a good download.


Some of these things may sound strange - but they're based on a lot of experience from the forums.


tty, as used above, refers to a terminal session.  The terminal is text driven (and can use the old terminal graphics) so there is no GUI

gdm = gnome desktop manager

---

### Post by shuttleworthwannabe on 2012-01-30
@OP
Did you check that all the hardware were in working order and all Ubuntu drivers were installed?

---

