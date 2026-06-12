---
title: "black screen bug acer aspire 5334"
date: 2012-05-04
forum: New to Ubuntu
---

### Post by fattyz on 2012-05-04
All my Ubuntu problems would b solved proly with a fix for this.  My acer aspire 5334 goes black when i upgrade to any version of ubuntu beyond 10.04.

This is a known bug hardware incompatibility but it really stinks because I have had to go back to winblows due to functionality I can't get without the ability to upgrade.

FattyZ

---

### Post by fattyz on 2012-05-07
Goes to black screen with any version upgrade beyond 10.04.  Actually, you can see the login screen but soooooo faintly that you can't locate the mouse or manage to see if you are typing in your password.

sigh  :(:(:(:(:(:(:(:(

---

### Post by alepira on 2012-05-07
Well Fattyz,

It will look really weird but in my Acer 4336 that happened too.
Switching to TTY1 to TTY5 with CTRL+ALT+F1..F5 works and the screen becomes bright and usable on 11.10.
After thinking a lot, the easiest possible solution came om mind: Fn+BrightPlus !!
Worked for me, the screen just starts at lowest (zero) background light. After adjusting it, the next boots was always fine (sometimes after packages upgrade, it returns but the solution works again).
Now, after an upgrade to 12.04 LTS, other problems rised up, but this one is past... :)

Good luck!

---

### Post by ajmc on 2012-05-07
I have the same problem with my aspire 4736 with Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller. {you can check with : lspci | grep VGA}... If we have the same graphics controller then I have the link to fix the display. Before reading the link below your need to press & hold shift to edit the grub opts.  you need to add i915.nomodeset=0 which is intel's equivalent to nomodeset.  Then read the link below on how I did it...

[http://www.icpep.org/mobile-series-4-display-problem-on-ubuntu-10-10-or-higher/](http://www.icpep.org/mobile-series-4-display-problem-on-ubuntu-10-10-or-higher/)

---

### Post by alepira on 2012-05-07
Mine is:
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
And now that you said, I tried something at grub option too, but they do not solved the problem (great odds I did it wrong)...

---

### Post by fattyz on 2012-05-08
Thanks guys, i'll try everything and anything!  Even if it's a no fix, it's nice to know others are working to try and get a solution.
:)

---

### Post by fattyz on 2012-05-17
I got 12.04 working by mistake.  I copy paste this into terminal, "sudo do-release-upgrade -d" thinking I was fixing the fact I had no upgrade button on update manager.  Well, that command did a full upgrade to 12.04.  I got black screen.  I typed in password blind and you see the screen a little when it switches from the login to the OS. I reeboot and selected previous ubuntu versions from boot loader and viola, 12.04 appears.

I am looking at the new grub menu which I never use, I always go back to the traditional one.  I do not know why it is working or how long I'll have it up but I'll keep going and keep you posted.

Oh and at first it kept asking me for wireless router password every minuet or so, I fix that then plug in my Iphone and it appears so I am already ahead of the game.):P  I never got it working in 10.04.

---

### Post by fattyz on 2012-05-17
I guess when you select previous version from bootloader you get a lesser graphics version or something?  I dont know.  When I try to start normally I still get black screen but run previous version gets me 12.04 running but no compiz.  I suspect this is a lesser graphics mode.

WRONG WORKING

Dudes I was wrong.  All is well.  Compiz is working and my HDTV torrent downloads are working without any choppy video.  I don't know how this is but on each reboot I will use bootloader to go to "previous versions" and keep running 12.04.

---

### Post by fattyz on 2012-05-18
All is up and running well. Seems a little buggy, a little shaky, but, it also has a faster look and feel, snappy on switching windows and compiz effects runs nicely.  

Good not to have to switch back to windows for anything, at least for now.

---

### Post by Fourmyle on 2012-05-19
I'm using the same work around with an acer Aspire 7250. The system locks up with the screen flashing alternate light and dark unless I choose to boot a previous version on startup. Then it works, well other then the sound and wifi :-P using a ASUS USB-N10 to get wifi and for now just don't bother with the internal speakers and mic. Plug in headphones work. 
It would be nice to know what's different in the startup when using the "Previous version" as opposed to the most recent. I'm on my third upgrade kernal so far and they all work as soon as they become "previous" so it has to be something in the start sequence itself.

---

### Post by fattyz on 2012-05-19
Wow, that is strange.  I don't know what the difference is but I'm all good and everything is working so, why bother?  I am going to try the function key solution from that earlier post next time I boot (I did try bright keys but they did not work)  Anyway, I like the newer version a lot and I have enough to keep going for now.

Thanks all,

---

