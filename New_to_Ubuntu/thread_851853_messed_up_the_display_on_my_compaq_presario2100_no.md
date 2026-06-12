---
title: "messed up the display on my compaq presario2100 notebook"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by AndrewEsther on 2008-07-07
I've been having problems with the LCD screen on my Compaq Presario2100 (old, I know), and so I decided that I was going to use the video out and just use an old CRT monitor instead of dealing with the incessantly flashing, seizure-causing LCD screen of DOOOOM!

Now, when I start it up, it just sits there with its blank screen, and I get nothing from the video out (the CRT tells me to check the input, as if it were not plugged in at all)

I am running Kubuntu on it, and can still start it up in recovery mode and see the command line appear on the LCD screen. Can anyone tell me how to change the default display device back to the onboard LCD monitor??


Thanks  :confused:

---

### Post by kuja on 2008-07-07
Well, so long as you don't have anything about it in your /etc/X11/xorg.conf file, you could probably just disconnect it and reboot to go back to using your default display. Same can be said of the CRT though .... if it's plugged in when you turn the computer on it should output to it instead (at least after X starts), assuming it wants to behave.

---

### Post by AndrewEsther on 2008-07-07
I finally got something on the CRT output... it takes me all the way through the xubuntu loading screen, the progress bar reaches the far right, then the screen blinks, and tells me this:

/etc/gdm/failsafeXServer: line 47: [: too many arguments
Warning: Could not retrieve EDID because get-edid is not installed

I hit escape to exit that dialouge and then get this:

*Starting anac(h)ronistic cron anacron
*Starting deferred execution scheduler atd
*Starting periodic command scheduler crond
*Checking battery state...
*Running local boot scripts (/etc/rc.local)
^@[   94.600000] serial8250: too much work for irq10

---

### Post by kuja on 2008-07-07
EDID is monitor related, it provides the video card all the info it should need to know about the monitor. 

Try installing the "read-edid" package and trying it again.

---

### Post by AndrewEsther on 2008-07-07
and how do I go about doing that? I tried using apt-get and I got nothing except a message telling me that read-edid isn't a valid operation.

---

### Post by kuja on 2008-07-07
You probably forgot to put "install" before the package name.

What I think you put:
```
sudo apt-get read-edid
```

What you need:
```
sudo apt-get **install** read-edid
```

---

