---
title: "How to uninstall gnome-do (failed to remove via Software Center)"
date: 2012-04-05
forum: New to Ubuntu
---

### Post by jps2012 on 2012-04-05
What's the best way to uninstall gnome-do, given that I've tried uninstalling via the Software Center, and that failed. I started having problems after installing it (it seemed to cause a lock-down, preventing me from switching to any other program), and adding it to the startup menu. I couldn't even kill it using a process ID in Terminal. 

I searched the forums and noted that someone recommended using the S Center, not uninstalling via Terminal. But ... I'm thinking that's my only remaining option ... right? 

There are several recommendations in the forum, for removing programs (none specific to gnome-do). Given how new I am to the command line, I'd like to ask which of the following would be best: 

sudo apt-get remove gnome-do
sudo apt-get purge gnome-do
sudo service gdm stop

---

### Post by dniMretsaM on 2012-04-05
> **jps2012 said:**
> What's the best way to uninstall gnome-do, given that I've tried uninstalling via the Software Center, and that failed. I started having problems after installing it (it seemed to cause a lock-down, preventing me from switching to any other program), and adding it to the startup menu. I couldn't even kill it using a process ID in Terminal. 

I searched the forums and noted that someone recommended using the S Center, not uninstalling via Terminal. But ... I'm thinking that's my only remaining option ... right? 

There are several recommendations in the forum, for removing programs (none specific to gnome-do). Given how new I am to the command line, I'd like to ask which of the following would be best: 

sudo apt-get remove gnome-do
sudo apt-get purge gnome-do
sudo service gdm stop

The first command you mention will remove GNOME-Do. The second will remove it and it's configuration files. The last one is unrelated to your issue. I would recommend
```
sudo apt-get purge gnome-do
```

---

### Post by utnubuuser on 2012-04-06
sudo apt-get remove gnome-do --purge

(though dniMretsaM's command is more concise)

---

### Post by dniMretsaM on 2012-04-06
> **utnubuuser said:**
> sudo apt-get remove gnome-do --purge

(though dniMretsaM's command is more concise)

Those are essentially the same thing. I only use the [FONT=Courier New]--purge[/FONT] option when I'm auto-removing stuff.
```
sudo apt-get autoremove --purge
```

For uninstalling, I just use [FONT=Courier New]purge[/FONT] instead of [FONT=Courier New]remove[/FONT].

---

### Post by jps2012 on 2012-04-06
Thanks, folks. I feel much better about using a command if it's confirmed as safe. It's going to take me a while before I feel comfortable with the command line.

---

