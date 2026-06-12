---
title: "A more complicated way to log on to root?"
date: 2005-12-30
forum: Programming Talk
---

### Post by kybishop on 2005-12-30
I was looking at the login screen setup under system -> administrator, and i was wondering, where is the code it chages when you choose to automatically log in as a user. couldn't i manually edit it so i can log on as root (because the application doesn't have root as a choice)

---

### Post by psusi on 2005-12-30
You do not log in as root except in recovery mode.  If you need root privleges use sudo.  See [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by harisund on 2005-12-30
Yes.. it is generally not a very good idea to log in as root.. However, there are some work arounds.. 

1. If you want to avoid typing sudo behind almost everything you need to get done, you could do 
sudo -r
This will then give you a root terminal. I normally keep one terminal with the root prompt for quick administration ..  Everything you do will be in sudo mode, so you can actually open synaptic from this and it wouldn't ask for the password. 

2. You could edit the /etc/sudoers file such that you are not asked a password. You still have to sudo every time, but atleast you wouldn't have a password. 

3. You can actually create the root account (whose home folder will be in /root.) This can be done using sudo passwd root. Then you can enable root login through GDM (least advisable, if you ask me.)

---

### Post by kybishop on 2005-12-30
i checked the option to log in as root and i do, but i still can't get the login setup to let me select root as an option for automatic startup,

---

### Post by Burke on 2006-01-05
Couldn't you, instead of typing "sudo -r", simply type "su"?  Or is that a security risk?

---

