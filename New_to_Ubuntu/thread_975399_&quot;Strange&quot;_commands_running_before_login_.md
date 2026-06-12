---
title: "&quot;Strange&quot; commands running before login screen"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by JohnnyMalakian on 2008-11-08
Hello, fellow Ubuntu users!

First of all, I apologize if this isn't the correct section to post my problem, but since I'm still a beginner in Ubuntu, I decided to place it here.

Some days ago, I re-managed my Ubuntu partition (nothing major, just adding some free space through GParted) and since then, everytime I choose to go to the Ubuntu OS, it gives me a bit of the loading screen, and before I get to the login screen, the screen shows me some command lines running. Here is a screenshot:

[[IMG]http://img519.imageshack.us/img519/9348/sany0021ia8.th.jpg[/IMG]](http://img519.imageshack.us/img519/9348/sany0021ia8.jpg)

Now, this doesn't give me any conflicts or problems, but it just kept bugging my mind on why does it appear. Is there anyway to "remove" it?


Will keep in touch. ;)
Stay cool, people!

[[[[]]]]/****** :popcorn: :guitar:

---

### Post by nhasian on 2008-11-08
thats just the normal startup procedure of linux.  usually its hidden behind the ubuntu logo during startup.  nothing to worry about.  :)

---

### Post by JohnnyMalakian on 2008-11-08
Thanks for the quick reply, **nhasian**.

Yeah, I presumed it would be something like that. I'm just kinda picky with this things. Is this screen "hideable"? lol xD

Cheers, mates!
Thanks once again for the hint. ;)

---

### Post by Kellemora on 2008-11-08
Hi Johnny

Yes MOST of it is hideable!
Interestingly, in 8.04, having it hidden is the DEFAULT and many of us go and remove the line that hides it.

If you mess up here, taint my fault!  Because the change is made in your bootloader!

```
gksu gedit /boot/grub/menu.lst
```
Then ADD the words Quiet and Splash behind the letters ro in the boot linuz command line.

Wait a minute, I see you are brand new posting here.  Let me add a file designed for just the opposite as it will be more informative.  Now remember, this file shows the exact opposite, how to REMOVE the words quiet and splash, you want to ADD the words quiet and splash if they are not there.

If they are there, you have a different problem or a different Ubuntu Version than 8.04.1 the LTS version.

Boot Text Not Showing During Boot-up?  Easy fix!
Ubuntu 8.04 Hardy Heron

From a Noob for fellow Noobs!

I don't know about the rest of you, but I HATE looking at a blank screen and NOT knowing what's going on during boot-up.

If you would like to see just what's going on during boot-up, here is a quick and easy way to make it happen!

Left Click on Applications, from Accessories select Terminal.

In Terminal type  gksu gedit /boot/grub/menu.lst (if you are using grub that is).

If you are multi-booting several Distro's select the first Ubuntu entry, which is the normal boot.  There will also be a Recovery boot, normally under it, and possibly a memtest under that.

In the Normal Boot listing you will see a line that reads 'kernel' /boot/vmlinuz at the end of this line, after the 'ro' you will find  the words 'quiet' and 'splash'.

See OPTION below line that reads SAVE and Exit.

Simply remove these two words, leaving everything else intact.
Don't worry about the word 'quiet' under initrd in the left column.

SAVE and Exit.

OPTION:  As a precaution, you may want to Comment out the existing line by placing a pound sign and a space (# ) in front of the existing line, then copy and paste it below the original.  Uncomment the new line by removing the pound sign and make the changes to this new pasted line.  You can always comment out the new line and uncomment the original line and be right back where you were before making any changes.

When you reboot, you should see all the boot-up text just as in other Distro's!

To Undo, just follow the above directions to put back the two words you removed.

The above was tested on the following machines with complete success:
HP Pavilion 753n, 2.53GHz Intel P4, 512mb, Intel 82845G/GL video card.
e-machines T4165, 1.6GHz Intel P4, 256mb, AGP 3D video card.
Compaq 5420, 1.47GHz Athlon XP1700, Savage 4 AGP video card.
e-machine T6524, 2.30GHz Athlon 64-3500+, ATP Radion Express 300 video card.


TTUL
Gary/aka Kellemora
9/10/08 – rev 9/15/08

---

### Post by JohnnyMalakian on 2008-11-11
Hey again!

I had to format my computer yesterday (due to it being so clogged up with so many stuff for a long time) and so I reinstalled Windows XP and Ubuntu all again. Needless to say, it's all working ok now with the splash screen, being the commands hidden behind it again. :D

But nonetheless, I'm saving your post for further need, **Kellemora**, thanks a bunch, to both of you! ;)


Stay cool, ppl!
[[[]]]/*****
:guitar: :popcorn:


EDIT: Just to say - [SOLVED]

---

