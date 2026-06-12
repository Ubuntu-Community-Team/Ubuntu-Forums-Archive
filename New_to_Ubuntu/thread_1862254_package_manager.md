---
title: "package manager"
date: 2011-10-16
forum: New to Ubuntu
---

### Post by protpisys on 2011-10-16
I just updated to 11.04 and tried to open the pkg manager to attempt to solve the google earth font issue and got this message instead:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

so I did, try to run "dpkg --configure -a" that is,  and got the following error message: 

error: requested operation requires superuser privilege

I have a healthy self-image but I'm not at all sure about the "superuser" thing...Help, thanks

---

### Post by protpisys on 2011-10-16
sorry I meant to say that I updated from 11.04 to 11.10

---

### Post by westie457 on 2011-10-16
> **protpisys said:**
> I just updated to 11.04 and tried to open the pkg manager to attempt to solve the google earth font issue and got this message instead:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

so I did, try to run "dpkg --configure -a" that is,  and got the following error message: 

error: requested operation requires superuser privilege

I have a healthy self-image but I'm not at all sure about the "superuser" thing...Help, thanks


Hello, welcome to the Forum

The error message is telling you that you need to be an administrator.

Run the command again with 'sudo' at the front. Like this ```
sudo dpkg --configure -a
```

You will be asked for your password that you set up when you installed. Nothing will show on the screen as you type, it is being registered.

Post back here if any problems.

Thank you.

---

### Post by Old_Grey_Wolf on 2011-10-16
Most of the time running the command "sudo dpkg --configure -a" doesn't fix the problem. If that is true this time run these commands in the terminal ```
sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by protpisys on 2011-10-16
all at once or one rafter another?

---

### Post by protpisys on 2011-10-16
all at once apparently, thanks

---

### Post by protpisys on 2011-10-16
ok so that worked, now I have the:  END-USER LICENSE AGREEMENT FOR MICROSOFT SOFTWARE  covering the terminal screen and, it appears hanging the program, the only place it looks like one could agree to whatever it says and get on w/one's life is at the bottom where there's a "<OK>"  but it's just text, not a link of any kind, so there's no apparent way to get through that screen and continue using the terminal

---

### Post by westie457 on 2011-10-16
> **protpisys said:**
> ok so that worked, now I have the:  END-USER LICENSE AGREEMENT FOR MICROSOFT SOFTWARE  covering the terminal screen and, it appears hanging the program, the only place it looks like one could agree to whatever it says and get on w/one's life is at the bottom where there's a "<OK>"  but it's just text, not a link of any kind, so there's no apparent way to get through that screen and continue using the terminal

The Okay button works after scrolling to the bottom of the text. About 95% of people never bother reading it anyway.

---

### Post by snowpine on 2011-10-16
You can use the Tab key to highlight the OK button, then press Enter. :)

---

### Post by protpisys on 2011-10-16
scrolling did nothing but the tab button worked, thanks

---

### Post by protpisys on 2011-10-16
but google earth's still illegible? I tried changing the font through the options menu but still often unreadable

---

### Post by madjr on 2011-10-16
this guide might help with some issues you may encounter:

[http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html](http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html)

---

