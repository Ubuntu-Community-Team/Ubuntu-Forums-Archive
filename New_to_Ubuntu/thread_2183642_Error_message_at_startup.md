---
title: "Error message at startup"
date: 2013-10-25
forum: New to Ubuntu
---

### Post by Timoteo32 on 2013-10-25
**Problem**: I can sign in and I get the message: > Unable to launch "startxfce4" X session..."startxfce4" not found, falling back to default session Then it loads a blank screen. I can see my desktop background but no nav bar at the top or anything. I can click the power button and the normal restart screen comes up.


**Current Status**: I have a flashdrive with Ubuntu (12.04?) start disk on it and I used that to boot up and backup most of my stuff but I'd like to avoid a reinstall if I can.  I'm going to create another one with the version of Xubuntu I've been using if that's helpful.


**Backstory**: I was cleaning up some of the apps I don't use through the software center. Since I only use webmail I uninstalled Thunderbird and something that was called Check Mail or something. I think it was the later that caused the problems. I just clicked yes on the box listing all the components that would be unistalled cause I assumed they were only related to mail.  Afterwards I couldn't open any system folders and was getting an error message about what I think was "thunrar" maybe? Anyway, I thought a restart might clean up some stuff from what I changed but that's when the above problem happened.

---

### Post by ajgreeny on 2013-10-25
Run the command ```
grep -iw remove /var/log/dpkg.log
``` after logging in at the command line from pressing Ctrl+Alt+F1 and you may see what you have removed listed by date.  The simplest way to get back to normal is just to run ```
sudo apt-get install xubuntu-desktop
```

---

### Post by Timoteo32 on 2013-10-25
Awesome. Trying now.

Mate, you're a life saver! Thank you! I don't know where I'd be without kind souls like yourself who help us out of the goodness of your heart. I've come around to Ubuntu but I would still have no clue how to do anything like this. Blessings!

---

