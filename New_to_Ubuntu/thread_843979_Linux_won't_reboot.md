---
title: "Linux won't reboot"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by zaivala on 2008-06-29
Just in the past 24 hours, my Linux refuses to close down when I click on the little green guy to reboot -- the system locks up and I have to do a cold reboot (i.e., turn off the power switch).  I need to occasionally boot to Windoze for work purposes, and I don't like booting down by turning off the power.  Any ideas what might fix this?

Moss

---

### Post by svk on 2008-06-29
Switch to the TTY (CTRL + ALT + F1), login there, and issue this command as root:

**shutdown -h now**

Does it lock immediately?  Do you see any diagnostic messages before the system locks up?  What is the last thing you see?  This info would help in tracing down the problem.

---

### Post by untermensch on 2008-06-29
I have the same problem too. I was messing around in TTY mode and wanted to shut down, and it was going threw I guess the normal shutdown procedures and it freezes up. doesn't do that when I am using the GUI, just when I use TTY.

---

### Post by zaivala on 2008-06-29
> **svk said:**
> Switch to the TTY (CTRL + ALT + F1), login there, and issue this command as root:

**shutdown -h now**

Does it lock immediately?  Do you see any diagnostic messages before the system locks up?  What is the last thing you see?  This info would help in tracing down the problem.

It asks for my login and password, I enter those, it gives me a promptm, I type the command, and it says "Must be root to issue command" (paraphrased from my poor memory).  Hey, don't get me wrong, typing in my login and password should give me root.

Also, you didn't say how to get back to Gnome... I think Ctrl-Alt-F5 or F6 did it...  

BUT... while I was in my command line, I typed the magickal IBM Three Finger Salute (Ctrl-Alt-Del) and it rebooted without a hitch.

Moss

---

### Post by untermensch on 2008-06-29
You have to use sudo. sudo shutdown -h now

---

### Post by svk on 2008-06-29
Does the shutdown appear to go normally, and Linux safely comes to a halt and everything, but simply fails to power off the actual hardware?

---

### Post by zaivala on 2008-06-29
> **svk said:**
> Does the shutdown appear to go normally, and Linux safely comes to a halt and everything, but simply fails to power off the actual hardware?

Just goes normally and reboots.  Which is what I want, not a power down.

Untermensch, thanks for the sudo tip... I gotta learn this someday... anybody know of a Ubuntu HH book?

---

### Post by untermensch on 2008-06-29
There is a book to learn about Ubuntu, several actually. Not sure the names and all. Mainly just start reading forums, and you can always use the IRC chats to ask questions. 

sudo = super user do. It allows you to do root commands without having to be root (because you really need to know what you're doing with root.)

---

### Post by zaivala on 2008-06-29
At any rate, Ctrl-Alt-F1, Ctrl-Alt-Del did what I was trying to do.  What's the switch for shutdown reboot?

---

### Post by untermensch on 2008-06-29
I think you could enter TTY mode and enter sudo shutdown -r now. I think. don't hold me to that.

---

### Post by zaivala on 2008-06-29
Of course, none of this answers the question, why won't clicking the Gnome Exit Guy work?

Moss

---

### Post by zaivala on 2008-06-29
> **svk said:**
> Does it lock immediately?  Do you see any diagnostic messages before the system locks up?  What is the last thing you see?  This info would help in tracing down the problem.

The system locks immediately... usually when my system locks, the screen goes dim, meaning that it's trying to get enough memory to run something, and it clears up later.  Not so when I click the green guy -- no dimming, and nothing else I click works.

---

### Post by untermensch on 2008-06-29
O, for that you'd have to ask someone more knowledgeable. I'm quite ignorant about Ubuntu. Umm, sometimes GUI's are weird? You have bad karma?

---

### Post by zaivala on 2008-06-29
> **untermensch said:**
> O, for that you'd have to ask someone more knowledgeable. I'm quite ignorant about Ubuntu. Umm, sometimes GUI's are weird? You have bad karma?

I have great karma, and no dogma... even wrote an article on that...

Hugs,
Moss

---

### Post by untermensch on 2008-06-29
Maybe your chi is off? I'm really not sure? Is there any updates available?

---

### Post by svk on 2008-06-29
Gee, I'm at a loss here.  I ran a google search and it seems some other people have this problem, too.

Here are a couple things you could try:
[http://ubuntuforums.org/showpost.php?p=4233212&postcount=15](http://ubuntuforums.org/showpost.php?p=4233212&postcount=15)
[http://ubuntuforums.org/showpost.php?p=2757329&postcount=9](http://ubuntuforums.org/showpost.php?p=2757329&postcount=9)

Tell us if any of these work.  Seems to be a common problem.  I ran this google search:

[  site:ubuntuforums.org ubuntu shutdown hangs]("http://www.google.com/search?hl=en&q=+site:ubuntuforums.org+ubuntu+shutdown+hangs")

A lot of the results on the front page described the exact problem you're having.

Meanwhile, you can try rebooting from the terminal using **sudo reboot**.  It may be quicker to do the same thing by hitting ALT+F2 and typing in **gksudo reboot**.

Someone ought to file a bug report, if there is not one already.  I never wrote one, so any other takers?

---

### Post by cariboo on 2008-06-29
Nows a good time as any to start submitting bugs, you can do it here:

[https://bugs.launchpad.net/](https://bugs.launchpad.net/)

Jim

---

### Post by zaivala on 2008-06-29
> **cariboo907 said:**
> Nows a good time as any to start submitting bugs, you can do it here:

[https://bugs.launchpad.net/](https://bugs.launchpad.net/)

Jim

Don't think I know enough to use the right words to see if it has already been reported, I've been searching a few minutes now...  I don't think "clicking the little green man hangs my system" is technical enough...

I did find the bug report email address, and described my problem to whoever reads that account. (Second update) "Your message was rejected."  No reason given.

---

### Post by JEV2 on 2008-06-29
i think i have the same problem, i put shutdown it goes through all the phase, shows the loading bar once it hit to nothing i hear the shut down noise but it's still on and the bar and Ubuntu logo are still there on the screen, and i have to turn it off by the power switch behind the desktop case.

i still can't figure out if it's Ubuntu or hardware problem.

---

### Post by zaivala on 2008-06-29
> **JEV2 said:**
> i think i have the same problem, i put shutdown it goes through all the phase, shows the loading bar once it hit to nothing i hear the shut down noise but it's still on and the bar and Ubuntu logo are still there on the screen, and i have to turn it off by the power switch behind the desktop case.

i still can't figure out if it's Ubuntu or hardware problem.

Well, if it's the same problem, it's happening much later for you than me.  I click the little green guy and absolutely nothing happens... and it won't let me do anything about it, except turn off the power.

---

### Post by zaivala on 2008-06-29
I figured it out... 

Under System - Preferences - Screensaver, I had clicked Power Management - General and set it to "When Power Button is pressed..." - Shut Down (other option is Ask Me).  Ask Me is the default.  I had changed it to Shut Down.

Now, that still is no reason that it did not shut down... but it works now.

---

### Post by untermensch on 2008-06-29
I'm not sure how that fixed it either, however if your post has been solved please mark it as such. (someone had to remind me the other day :(       )

---

### Post by zaivala on 2008-06-29
> **untermensch said:**
> I'm not sure how that fixed it either, however if your post has been solved please mark it as such. (someone had to remind me the other day :(       )

Well, it is yet to be determined why, when this setting is set to Shut Down, it doesn't do anything other than lock the system... the original question is answered, at least for working purposes, but the original problem is not.

---

### Post by untermensch on 2008-06-29
I'm confused? I thought you said it would shutdown now?

---

### Post by zaivala on 2008-06-29
> **untermensch said:**
> I'm confused? I thought you said it would shutdown now?

...but when it didn't shut down, it had a legitimate setting under which it should have shut down, not locked up.  So the locking up problem still exists, at least with some users who change that setting.

---

### Post by untermensch on 2008-06-29
O ok, I'm sorry. been a long day =\ Hmm, so it is still freezing? the terminal command works but not the "green man"?

---

### Post by zaivala on 2008-06-29
> **untermensch said:**
> O ok, I'm sorry. been a long day =\ Hmm, so it is still freezing? the terminal command works but not the "green man"?

When I use that setting, it still freezes.  I have changed the setting.  But my point is that anyone else using that setting could have the same problem I did, which is why I'm not marking this "Solved" yet.

---

### Post by untermensch on 2008-06-29
O ok, that makes a lot more sense now.I'm slow =[  :lolflag:

---

### Post by zaivala on 2008-07-20
Update:  It still freezes, approximately half the time.  Some reboots work fine, others don't.  I have solved the problem with Ctrl-Alt-F1, Ctrl-Alt-Del... Ctrl-Alt-F1 seems to be the only keystroke that works when it freezes.  I'm sure there's a good explanation for that (and probably some other keystrokes I don't know about), but I wouldn't have known about THAT without this forum.

---

### Post by zaivala on 2008-10-16
Well, it got solved the hard way.

I have a Eee PC 701, with an installation disk that was SUPPOSED to run a program to make a boot disk out of a USB drive.  I bought the jumpdrive, and ran the disk on my desktop computer... and it tried to INSTALL Eee PC Linux (based on Xandros), destroying all the data on my hard drive.  So I had to reinstall everything... and it works great now.  Must have been a damaged installation causing the problem.  (I never got the jumpdrive made, but I figure I should be able to just COPY the disk to the jumpdrive, as it has proven itself to be a bootable installation disk.  Trust me, that's not what the instructions said.)

It's odd.  I have now installed Ubuntu 8.04 on this computer 4 times, and each time there is a different glitch in the completed installation.  The latest installation was better than the others... and I have prevented my loss-of-data problem by keeping all of my personal files on an external hard drive.  (The last two "crashes" had me backing the data up on that drive, so I only lost a week's worth of data that had not been backed up each time.)  

The only problem I have (or rather, remember having) right now is Ubuntu won't let me put shortcuts on my Desktop for folder on the external drive.  No biggie.

Moss

---

