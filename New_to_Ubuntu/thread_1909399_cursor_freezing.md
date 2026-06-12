---
title: "cursor freezing"
date: 2012-01-15
forum: New to Ubuntu
---

### Post by gertrude58 on 2012-01-15
I recently installed ubuntu on a 3year old toshiba L300 laptop for my computer novice husband.He found windows too confusing as it kept nagging him to do updates and virus scans etc.He likes it vey much and is now in the process of entering contacts into Thunderbird.The only problem he has is the cursor freezing from time to time.He has to do a hard shutdown with the power button and then restart the laptop to continue typing.What could be causing this?Do you think it's a hardware problem or is it ubuntu?:confused:
It is running ubuntu 11.10

---

### Post by BC59 on 2012-01-15
Looks like a bad installation of the system, but you never could be sure.
Try to open (CTRL+ALT+T) and run in a terminal:

```
sudo dpkg --configure -a
```and
```
sudo apt-get -f install
```

to see if there is a badly installed package.

---

### Post by Fernhill Linux Project on 2012-01-15
If ubuntu freezes or crashes, press "Ctrl-Alt-F1" 
This will take you to a command line interface (CLI).
Login and then type "top" to launch top, the default CLI task manager.
You can kill any problem process by pressing "k" and then typing in the PID shown on left and pressing enter. 
When I have had this problem using abiword and chromium, killing pulseaudio solved the problem.
To return to the graphical interface (GUI) press "Ctrl-Alt-F7" or "Ctrl-Alt-F8" 

If this does not resolve the issue, press "Ctrl-Alt-F1" again, 
Login if needed and then type "sudo shutdown -r now" to restart your computer.
You can also use "sudo restart lightdm" to restart the display manager & return to the graphical login screen.

---

### Post by gertrude58 on 2012-01-15
Thanks,will try suggestions if the problem recurs.

---

### Post by shad0w_walker on 2012-01-15
Does the whole system freeze or just the mouse? I'm wondering if the problem might be a weird bug in how Ubuntu is handling the touchpad. There is an option (I believe in mouse preferences) that causes the touchpad to disable automatically when you type (To avoid accidentially tapping other stuff) and auto reenable after a half second or so, maybe it's not quite managing that. Try turning it off and seeing if the problem carries on.

---

