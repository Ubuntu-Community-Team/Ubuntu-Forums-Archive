---
title: "[SOLVED] I broke it! User's $HOME/.dmrc file is being ignored."
date: 2008-11-28
forum: New to Ubuntu
---

### Post by kansasnoob on 2008-11-28
At start up I get this full error message:

> User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. Users $HOME directory must be owned by user and not writable by other users.


Hmmm, how did that happen? Well look here:

[http://ubuntuforums.org/showthread.php?t=991346](http://ubuntuforums.org/showthread.php?t=991346)

Yeah, I played, and played, and I broke it!

Now, I could easily just reinstall! This is actually a test hard drive that I've been using since the Beta release of Intrepid anyway.

I just decided until I need my Windows crap back I'll just use the heck out of this "test drive" trying things I'd otherwise be reluctant to do.

But in this case I'd really like to know how to fix the authorizations/ownership of the files in question. Basically restore the home directory default permissions:confused:

---

### Post by a0u on 2008-11-28
Make sure you are the owner of the file:
```
sudo chown <user> ~/.dmrc
```Be sure to replace <user> with your own username.

Reset permissions:
```
sudo chmod 644 ~/.dmrc
```Reassign ownership of all files in your home back to yourself:
```
sudo chown -R <user> ~
```Reset permissions for the home directory:
```
sudo chmod 750 ~
```

---

### Post by kansasnoob on 2008-11-28
Well, if I did this right, this is what I got:

> lance@lance-desktop:~$ sudo chown lance ~/.dmrc
[sudo] password for lance: 
lance@lance-desktop:~$ sudo chmod 644 ~/.dmrc
lance@lance-desktop:~$ sudo chown -R lance ~
chown: cannot access `/home/lance/.gvfs': Permission denied
lance@lance-desktop:~$ sudo chmod 750 ~
lance@lance-desktop:~$ 



I wanted to send this before I restart again.

I'll post back!

---

### Post by kansasnoob on 2008-11-28
It works!

All seems accessible!

No error warnings!

You're a genius!

---

### Post by a0u on 2008-11-29
> **kansasnoob said:**
> It works!

All seems accessible!

No error warnings!

You're a genius!

There is a more detailed guide to **[Solving .dmrc and $HOME Permission Errors]("http://ubuntuforums.org/showthread.php?p=6138880")**, if you need it in the future.

---

