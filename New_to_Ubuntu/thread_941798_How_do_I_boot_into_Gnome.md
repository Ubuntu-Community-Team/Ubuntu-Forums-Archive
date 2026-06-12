---
title: "How do I boot into Gnome"
date: 2008-10-08
forum: New to Ubuntu
---

### Post by dta983 on 2008-10-08
Hey. I think this question has been asked before but the answer didn't help me. I recently installed ubuntu 8 on my computer. When I log in it brings me to a black screen with white text that says username@username:~$  . I can also get into root but it is a black screen too. How do I boot into a desktop? Did I do something wrong in install? My comp is a Viao Laptop that is about a year old so the specs should be fine. I also have a dual boot with Windows XP. The XP part works fine. I apologize if this question is extremely obvious. 


Thanks!
DT

---

### Post by SunnyRabbiera on 2008-10-08
did you try typing GDM in the terminal?
Perhaps something did go wrong with installing ubuntu

---

### Post by mihaiv on 2008-10-08
What version of ubuntu have you installed, desktop or server?

---

### Post by Big_Kahunaca on 2008-10-08
Have you tried 'startx'?

---

### Post by dta983 on 2008-10-08
I believe I have desktop version installed. If i type in GDM it says command not found.

---

### Post by Big_Kahunaca on 2008-10-08
sudo /etc/init.d/gdm start
sudo /etc/init.d/gdm stop

sudo /etc/init.d/gdm restart

Have you tried the above?

---

### Post by dta983 on 2008-10-08
It says command not found for each of the three

---

### Post by The Cog on 2008-10-08
That sounds like you installed the server version.
Try this:
**sudo aptude install ubuntu-desktop**

---

