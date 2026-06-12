---
title: "edubuntu 14.04 not turning off"
date: 2014-06-18
forum: New to Ubuntu
---

### Post by jaxom98 on 2014-06-18
Hello, I have just updated from edubuntu 12.04 to edubuntu 14.04.  This is a clean install.

When I click on shutdown it does not. On clicking shut down in the verification window, the screen blanks then goes to a white screen with edubuntu and the ubuntu logo on it as at start up with the activity indicator dots moving. There it hangs. I have left it for 4 hours and it is still hanging. Ihave done several test shutdowns, and all shut downs have hung. To turn off takes a hard shutdown each time.
What has gone wrong and how do I fix it?

Hardware : HP Pavillion  DV6000 with a 1Tb hdd
System  Dual boot win7  with  edubuntu 14.04

---

### Post by Dreamer Fithp Apprentice on 2014-06-19
Pardon me if I'm pointing out what you consider obvious but I'm wondering what you call a "hard shutdown". To me that would mean```
sudo shutdown -h now
```You're not just killing the power are you? If so, you'll create less problems for yourself if you'll open a terminal (should be in your menu somewhere, or try cntr-t, or cntrl-alt-t) and use the code above. Or if you can't get a terminal up, sometimes even in a system generally unresponsive you can still get a tty (which is like a terminal without a window that fills the whole monitor) by pressing cntrl-alt-F1 or try a different F-number, up to 6, if you don't get a login prompt. If you do get one, log in with your regular user name and password. That may sound odd since you're already logged in and trying to log OUT, but trust me, this is how it works. You're logged in through x which is the program that manages the gui-point-clicky stuff and x is running (and hung) in tty 7. Once you get logged in on another tty you can enter the shutdown command above. Either way, tty or regular terminal-emulator-in-a-window, it will ask for you password and upon entering it, the system should shut down in a fashion less likely to cause problems when you reboot. Sometimes you can get a tty to work when the regular "terminal" won't. This is also handy when some program is locking your system up and you need to kill it with ```
killall someprogram
```or something similar.

Now as to fixing the graphical shutdown thing, I'm on shaky ground since I've never used Edubuntu, but if you can figure out the name of the program that runs it you can try reinstalling it. I don't use a graphical shutdown anymore having put that code as an entry in my menu. I have used them in the past, most recently with LXDE & Lubuntu. LXDE's is provided by the program lxde-logout and Lubuntu's is provided by lubuntu-logout, but experimenting with apt-get and browsing synaptic doesn't seem to indicate any "edubuntu-logout" nor anything likely looking.

Another thing you could try is to press Esc when the system is supposed to be shutting down. That MIGHT suppress the stupid graphic with the dots that is obscuring the text in the tty where the shutdown should be going on and if it does work you might find some message there that would give you a clue to what is wrong.

If you don't get a better answer here or figure it out yourself soon, I'd try reposting, maybe at a busier time of day and/or maybe in the Desktop environments subforum. Or you might try the edubuntu users mailing list mentioned here:
[https://edubuntu.org/community](https://edubuntu.org/community)

---

### Post by jaxom98 on 2014-06-21
Hello Dreamer Fithp Apprentice,
1) A hard shut down is pressing and holding the on/off button down until the laptop shuts down
2) escape button , fail
3) cntrl alt f1 ,message:  Ubuntu 14.04 LTS jason-HP-Pavillion-dv6700-Notebook-PC tty1
                                    jason-HP-Pavillion-dv6700-Notebook-PC login: ModemManager[565]: <warn> Could not aquire the 'org.freedesktop.ModemManager1' service name
                                    ModemManager[565]: <info> ModemManager is shutdown
These 3 lines are on a black screen , line 4 is a blinking curser.
4) cntrl alt f2-f6 all want login and password. 
5)sudo shutdown -h now  fail
6)sudo kill all some program and variations  fail
7)Reread top text . In via cntrl alt f2 (tty2), logged in and entered sudo shutdown -h now   failed , ended up on white screen with "edubuntu " and linux logo on it and hung
8) did some updates and restarted and hung on shutdown
9) Edubuntu is basicly Ubuntu with a slightlydifferent desktop and a 4 part education package.

---

### Post by jaxom98 on 2014-06-22
away until 26th

---

### Post by Dreamer Fithp Apprentice on 2014-06-23
Since "sudo shutdown -h now" in a tty failed, it would seem the problem is deeper than the Edubuntu graphical logout program. If nobody has come up with a better suggestion by the time you get back, you might want to try reinstalling. Sorry I can't think of anything else at the moment.

---

### Post by jaxom98 on 2014-06-27
Hello Dreamer Fithp Apprentice, I did a reinstall , finally and it worked. Go figure. I expected a repeat of the shutdown failure.  All good, thank for your help.

---

