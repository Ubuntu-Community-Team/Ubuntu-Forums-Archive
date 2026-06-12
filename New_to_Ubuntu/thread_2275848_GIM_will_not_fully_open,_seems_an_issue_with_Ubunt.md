---
title: "GIM will not fully open, seems an issue with Ubuntu, not Gimp"
date: 2015-04-28
forum: New to Ubuntu
---

### Post by riverguy99 on 2015-04-28
Just installed a new 12.04 on a Dell D-630 laptop.  Everything works great, all apps open fine, except GIMP.  When I click on it, the opening screen pops up and then it disappears.  The icon still shows the app as open.  I have removed it several times and re-installed it both through the Download Center and in Terminal.  I've tried it with different terminal command suggestions, too. Same results.

Any clues would be very helpful. Since I get the same results from several different sources of the program, does this not point to it being an issue with my 12.04 installation?

BTW, I have it on three other identical laptops in our office and it has always installed without a hitch.

Thank you!

---

### Post by steeldriver on 2015-04-28
Have you tried starting it from a terminal (or just removing/reinstalling it from the terminal)? it sometimes gives useful error messages

Most often (in my experience) gimp startup problems are related to the user's .gimp directory e.g. ~/.gimp-2.8 (depends on the version) - you could move or rename that to see if it helps

---

### Post by riverguy99 on 2015-04-28
Yes, I've both uninstalled and re-installed it in Terminal.  In Terminal, I used several different install command suggestions from different sites and removed it before any attempts at re-installation.  I also uninstalled and re-installed it in Software Center.  Maybe I'll try an older version next time to see if that makes a difference.  Funny thing is that it does start, right up to the opening screen and then it disappears.  The little triangles stay on the icon, making me believe that maybe it is actually open but somehow hidden?  Nothing else is open at the same time, so it's not behind another program.

---

### Post by newbie14 on 2015-04-28
Try uninstall gimp first, and then install gimp again using this tutorial:

[http://ubuntuforums.org/showthread.php?t=2274160&p=13267263#post13267263](http://ubuntuforums.org/showthread.php?t=2274160&p=13267263#post13267263)

---

### Post by riverguy99 on 2015-04-29
I'm toast for the day so will continue tomorrow,  Here's another clue:  Just for fun, I removed the existing GIMP install and then installed 2.6.  It worked fine!  Then I upgraded back to 2.8 and it wouldn't fully open again, just like before.  There are no messages, no other clues.  The "GIMP 2.8" box comes on the display, it looks like it's working, and then it disappears.  The launcher icon still shows it to be open.

---

### Post by Holger_Gehrke on 2015-04-29
Three things I can think of:
1) Uninstalling a program doesn't remove the programs configuration. Even 'apt-get purge' leaves the personal configuration in your home directory alone. Try moving '~/.gimp-2.8' out of the way or deleting it.
2) Try starting gimp from a terminal with  'gimp --verbose'. This makes gimp produce a lot of output that might be helpful.
3) I have on one occasion had gimp on a different virtual desktop, and until i moved it back to the primary it staid there across exiting and restarting gimp ...

---

### Post by riverguy99 on 2015-04-29
I figured it out.  It took getting out of the box.  I have an external display on this machine, and I finally figured out that even though everything else was opening fine on that display, Gimp was opening on the laptop display.  The laptop is tucked away under the desk and is basically the CPU for this setup.  I reconfigured the setup as dual displays, mirrored.  I did this only because I cannot figure out (yet) how to get it to work as an external display only.  I'll address that one in another post.

Thank you everyone for your assistance, as usual!

---

