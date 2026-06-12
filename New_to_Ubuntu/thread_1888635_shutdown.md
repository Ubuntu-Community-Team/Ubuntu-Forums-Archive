---
title: "shutdown"
date: 2011-11-29
forum: New to Ubuntu
---

### Post by cmcanulty on 2011-11-29
I have tried dconf-editor and several other things but can not get a shutdown or restart option in "11.10 gnome-classic no effects" even the log out option doesn't work all I can do is forcefully power off.

---

### Post by bluexrider on 2011-11-29
**shutdown command**

shutdown  arranges for the system to be  brought down in a safe way.   All logged-in users are notified that the  system is going down and,  within the last five minutes of TIME, new  logins are prevented. The  shutdown utility provides an automated  shutdown procedure for supersers  to nicely notify users when the system  is shutting down, saving them  from system administrators, hackers, and  gurus, who would otherwise not  bother with such niceties.
**How do I use shutdown command?**

The  shutdown command can be used to turn off or reboot a computer. Type  the  command as follows to shutdown server / computer immediately:
 $ sudo shutdown -h now
 OR
 $ sudo shutdown -h 0 
**How do I shutdown compute at specific time?**

To shutdown computer at 6:45pm, enter:
 $ sudo shutdown -h 18:45 "Server is going down for maintenance" 
 At 6:30pm message will go out to all user and 6:45 system will shutdown.
Please note that you can also use halt or poweroff or reboot command for stopping and restarting the system:
 $ sudo halt
 OR
 $ sudo poweroff
**How do I reboot computer?**

Simply use reboot command:
 $ sudo reboot
 OR
 $ sudo shutdown -r 0

You may want to try this

---

### Post by cmcanulty on 2011-11-29
I actually by luck figured out the problem my setup  was ldm and it should be Gdm I also deleted mate which seemed buggier than classic. I can't believe how hard they have made it just to do what was easy before and how less customizable it is. I think the idea was to make sure every task takes 2 to 3 times the mouse clicks as before. And even something as mundane as shutdown is now a task that needs research and tweaking all day.If I wasn't too stupid to learn a new distro I would be long gone as many are. Is there never a point where they say whoops we screwed up and maybe we should regroup?

---

### Post by cmcanulty on 2011-11-29
I fixed mine went to synaptic and changed ldm to gdm and now the options are back but still I can't undimm the laptop monitor or get the screen slider back.

---

### Post by bluexrider on 2011-11-29
> **cmcanulty said:**
> I actually by luck figured out the problem my setup  was ldm and it should be Gdm I also deleted mate which seemed buggier than classic. I can't believe how hard they have made it just to do what was easy before and how less customizable it is. I think the idea was to make sure every task takes 2 to 3 times the mouse clicks as before. And even something as mundane as shutdown is now a task that needs research and tweaking all day.If I wasn't too stupid to learn a new distro I would be long gone as many are. Is there never a point where they say whoops we screwed up and maybe we should regroup?

In regards to original problem. There was no mention that MATE was involved. Please include all pertained information it helps.

Glad you got it going.

---

