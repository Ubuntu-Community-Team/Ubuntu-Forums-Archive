---
title: "Upgrade Issues"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by flyby4 on 2008-07-08
Hi,
I'm still relatively new to Ubuntu.   I have just upgraded from 7.10 to 8.04 hoping it would help with some odd issues from 7.10.  Instead I just got a few more.

1) I have had an issue with 7.10 and 8.04 where the sound card works intermittently.  By Intermittently I mean if it works at login it keeps working.  If it does not work at login then it stays that way.  I have a winXP dual boot set up and have noticed that if I restart from winXP it is more likely to work.  With 7.10 it originally worked for some time but after an update the sound died.  I went through a series of steps I found on the forum and managed to get it to work again but since have had this intermittent issue.  Sound always works in winXP.

2) Since the update to 8.04 I have not been able to change the screen resolution on the fly.  I notice that the restricted nVidia drivers have been disabled.  Is that why or is something broken?

3) For some reason i can not write to writeable CD-R or CD-RW with my CD burner.  It is recognised as a burner but it keeps asking to insert writable media.  Have tried 20 CD-R's and different brands.  The burner works in windows.

PC is pretty old (666MHz Pentium 111).  I actually prefer Ubuntu and have invested quite a bit of time learning the apps but my understanding of the OS is still miniscule.

Steve

---

### Post by 449 on 2008-07-08
I didn't know you could run Ubuntu on such low specs...

I can't answer your question ,but I'd recommend you try a lighter distro like Fluxbuntu. Do you get a lot of freezes?

---

### Post by jamewill on 2008-07-08
a)how much RAM does this computer have?
and which sound card.   To checkthe latter...

sudo lspci

b) does problem 1) happen after suspend on windowx but is ok if windows fully shutdown b4 ubuntu boot.   God knows why but worked for me

c) have you tried another program (you don't mention name of current one)
e.g. sudo apt-get install k3b

jw

---

### Post by flyby4 on 2008-07-09
Ubuntu actually runs a lot better than winXP.  Has 3/4Gb of RAM and an older soundblaster card with Ensoniq (?sp) ES1371 chip set.  It does not freeze often, though it will slow down under a heavy application load or if the eye candy is a bit over the top.  Even if it appears to freeze it recovers in a few seconds.  A new PC would be good it just isn't going to happen for a year or so :)

Issue one happens from a cold boot or full shut down.  It is more likely to work correctly from a restart from windows.

I have tried using several different programs and they all have the same issue, no sound.  Even the sound that occurs with the splash screen is absent.  Ubuntu knows about the card and which driver to use.  If I run through the comprehensive sound guide on this forum I can usually get it to work, but the next update stuffs it up again.  There must be something wrong for this to keep occuring.

I am currently remote but will run your command in a couple of hours.

Steve

---

### Post by kevmitch on 2008-07-09
So which steps in the comprehensive sound guide have given you working audio in the past? Based on your statement that upgrades seem to break it, I might think that you need to recompile the alsa modules for your kernel

```
sudo m-a a-i alsa-source
```

If this is the case, then you will need to execute this command whenever your upgrades include any linux-image-* packages.

---

### Post by flyby4 on 2008-07-09
Getting the ALSA drivers from a fresh kernal section where you remove and reinstall the linux-sound-base fixes the problem.

---

### Post by kevmitch on 2008-07-09
mmm. so you apparently have uninstall and reinstall the alsa packages on upgrade? If you haven't touched any of the alsa configuration files yourself between a fresh install of these packages and the upgrade, this sounds worthy of a bug report. 

Does this fix your problem completely? I.e, does it make sound work 100% of the time?

---

### Post by flyby4 on 2008-07-09
Yes that worked!!!  :)  That is much easier to do than the previous work around.  Thanks a lot for your help.  When i have a minute I'll put in a bug report as you have suggested.

---

