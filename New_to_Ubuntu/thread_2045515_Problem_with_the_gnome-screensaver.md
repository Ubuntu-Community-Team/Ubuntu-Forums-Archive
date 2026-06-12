---
title: "Problem with the gnome-screensaver"
date: 2012-08-21
forum: New to Ubuntu
---

### Post by Bufeu on 2012-08-21
Hi, I have a extremely irritating problem with the gnome-screensaver. When my screen is locked and I then reawaken it, by moving the mouse or  pressing the keyboard, the password entry screen appears. I have measured the time that it takes to the screen to go blank, and it's always 1 minute, no matter what I do. I don't want my screen to go blank, it's just annoying to rewake it, and sometimes the blank screen is impossible to wake; the only thing I can do is to restart it using the power button. I run BOINC on my laptop and the fans is still going when it's impossible to wake, so I'm sure the system is still running. The hibernate mode is off by default in Ubuntu, and I have even checked if I have hibernate on, but no.
I found the problem with the lock screen [here]("http://askubuntu.com/questions/143314/how-do-i-change-the-length-of-time-the-lock-screen-appears-for"), but without any solution.
I am very grateful for any tips and suggestions for solutions!

Thanks

---

### Post by Bufeu on 2012-08-21
Anyone?

---

### Post by Bufeu on 2012-08-22
No one out there who can help me? :(

---

### Post by Buntu Bunny on 2012-08-22
It can be done! 

Go to system settings.
Click on brightness and lock
turn lock off
uncheck "Require my password when waking from suspend"

That's it. :)

---

### Post by Bufeu on 2012-08-29
> **Buntu Bunny said:**
> It can be done! 

Go to system settings.
Click on brightness and lock
turn lock off
uncheck "Require my password when waking from suspend"

That's it. :)
](*,)
I still want to type in my password to unlock the screen, that's the whole point of locking the screen. I just don't want the screen to go black!

---

### Post by Bufeu on 2012-09-15
No one out there? :-(

---

### Post by hypnot0ad on 2012-09-15
On some of my computers I have had some of the screen savers do this to me. It could be something like a graphical error, or bad install of said screen saver.
Does this happen with every screen saver you've used?

---

### Post by Peter Maunder on 2012-09-15
The gnome-screensaver in Gnome3 only provides a blank screen. This has been the case for some time. XSCREENSAVER provides all the bells and whistles. 

There are a number of entries on this subject. 

However, if you use the Software Centre to remove the gnome-screensaver and install xscreensaver, you will not find the entries under screensaver, you must look under gnome-screensaver and xscreensaver and xscreensaver-.

---

### Post by Bufeu on 2012-09-15
> **hypnot0ad said:**
> On some of my computers I have had some of the screen savers do this to me. It could be something like a graphical error, or bad install of said screen saver.
Does this happen with every screen saver you've used?No, this is not happening when I use xscreensaver. But, I want to keep gnome-screensaver, but without annoying blank screens. I found this, but without a solution: [http://askubuntu.com/questions/143314/how-do-i-change-the-length-of-time-the-lock-screen-appears-for](http://askubuntu.com/questions/143314/how-do-i-change-the-length-of-time-the-lock-screen-appears-for).
This appears on both my computers and VMs.

---

### Post by NikTh on 2012-09-15
Hi , 

try this in terminal ```
gsettings set org.gnome.desktop.screensaver idle-activation-enabled false
``` 

Above command will disable screensaver. 

**To enable it again** ```
gsettings set org.gnome.desktop.screensaver idle-activation-enabled true
```

Thanks

---

### Post by Bufeu on 2012-10-01
> **NikTh said:**
> Hi , 

try this in terminal ```
gsettings set org.gnome.desktop.screensaver idle-activation-enabled false
```Above command will disable screensaver. 

**To enable it again** ```
gsettings set org.gnome.desktop.screensaver idle-activation-enabled true
```Thanks
Thanks, but it doesn't work. If I lock the screen, the screen turns off after exactly one minute.
I have searched on Google, asked here on Ubuntu Forums, asked the developers themselves. No answer. :(

---

