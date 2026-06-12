---
title: "Setting env. variables - what's the right way?"
date: 2012-09-29
forum: New to Ubuntu
---

### Post by ThrashManiac on 2012-09-29
I have tried to get some variable through Java (System.getenv()) which was set inside ~/.bashrc 
It hasn't appeared in the list of variables. 

Than, I've added script.sh with it's variable declaration to /etc/profile.d/ and everything has worked perfectly.

This is what mighty Google has found: 
> Application Environment Setup Using /etc/profile.d/*

When a user logs in, environment variables are set from various places. That includes /etc/profile (for all users). 
Then all the files in the /etc/profile.d directory. 
Then ~/.bash_profile, then ~/.bashrc. 
/etc/profile.d/ is a good place to put your application specific setups.
The question is! What's the lifetime of variables declared through /etc/profile.d/ ? 

Only until logoff or is it permanent? If I modify PATH in the described way, the original has it's original value after I log off ?

---

### Post by The Cog on 2012-09-29
My understanding is that all of these files you can edit make permanent changes, such that the variable is set as you log in, every time you log in. 

I used to think that .bashrc was run whenever a bash shell was started, but this appears not to be true when working in a GUI (in XFCE at least, but I think the same may be true for other desktops). It seem that with the GUI, .bashrc is run as the GUI launches, and then all other bash shells started in the GUI inherit variables from when the GUI was started. As such, I found that after editing .bashrc, I had to logout/login the GUI before it took effect.

---

### Post by ThrashManiac on 2012-09-29
> **The Cog said:**
> My understanding is that all of these files you can edit make permanent changes, such that the variable is set as you log in, every time you log in. 

I used to think that .bashrc was run whenever a bash shell was started, but this appears not to be true when working in a GUI (in XFCE at least, but I think the same may be true for other desktops). It seem that with the GUI, .bashrc is run as the GUI launches, and then all other bash shells started in the GUI inherit variables from when the GUI was started. As such, I found that after editing .bashrc, I had to logout/login the GUI before it took effect.
So, basically, if I will add to this kind of script (/etc/profile.d/Script.sh) this code: 
```
PATH=$PATH:/opt/java/jdk1.6.0_35/bin
```
...this will result in PATH with multiple **/opt/java/jdk1.6.0_35/bin** records?

---

### Post by Paddy Landau on 2012-09-29
For Ubuntu (there are some differences from other distros such as Lubuntu):

[LIST]
[*][FONT=Lucida Console]/etc/profile[/FONT] and [FONT=Lucida Console]/etc/profile.d/*.sh[/FONT] are session-wide and apply to all users. They apply when logging in, after the GUI has been created but before Gnome gets going.
[/LIST]

[LIST]
[*]Then [FONT=Lucida Console]~/.profile[/FONT]. This is also session-wide, but applies only to the user who owns that file.
[/LIST]

[LIST]
[*]Finally, for interactive terminals only (not session-wide), both [FONT=Lucida Console]/etc/bash.bashrc[/FONT] and [FONT=Lucida Console]~/.bashrc[/FONT] in that order. The former is for all users and the latter for only the user who owns the file.
[/LIST]
For your purposes, the best place is in [FONT=Lucida Console]/etc/profile[/FONT] if all users need it, or [FONT=Lucida Console]~/profile[/FONT] if only you need it.

---

