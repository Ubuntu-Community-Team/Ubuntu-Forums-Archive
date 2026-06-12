---
title: "Chown Messed up my login?"
date: 2013-08-13
forum: New to Ubuntu
---

### Post by Ryan_Chipman on 2013-08-13
Recently I suffered a corrupted profile that caused my computer to totally freeze whenever I logged in due to gnome settings daemon becoming unresponsive. After scouring these forums and others for a while, I couldn't find any specific advice, so I had to just recreate my profile. To do this, I created a new user, copied my home directory (/home/rchipman/) to /home/rchipman.bak/ and created a new empty home directory /home/rchipman/. I chowned this directory to rchipman so I could use it, and then logged back in as myself (rchipman).

Now, I proceeded to copy my files back into my newly created home directory from the backup, and, as I was copying them in, noticed that I didn't own the hidden directories, so I ran (from my home directory) chown -R rchipman .* to own all the hidden directories in my home folder.
At this point, everything seemed to be up and running like new, other than the fact that I had lost my unity keybindings (I suspect this may have been due to my attempts to reset unity and ccsm during the initial stages of troubleshooting, and it wasn't a big deal anyways). However, a few hours later, I realized that something else was up:

Now, I do not need to type my correct password to log in to my account...in fact, I do not even need to type anything -- just hitting enter will log me in without any trouble. I have a sneaking suspicion that I may have messed something up with chown. Furthermore, I can no longer log in to the account I had created to help with the new home directory creation...whatever I type for the password, the login screen just goes black for a second, and then reappears. If anyone could help me identify what I messed up and point me in the right direction as far as fixing it, I would greatly appreciate it!

(Using ubuntu 13.04, 64-bit)

Update: If I log in without using the correct password, I am prompted to (and have to enter the correct password to successfully do so) unlock my keyring, because it was not successfully unlocked at login.

---

### Post by Ryan_Chipman on 2013-08-21
bump

---

### Post by Werne on 2013-08-21
That sounds like a potential mess. Log into rchipman and post the output of the following commands:
```
echo $HOME
cat /etc/passwd | grep $USER
```

---

### Post by gordintoronto on 2013-08-21
The easiest solution might be to backup all your files (twice!!!) and reinstall.

---

