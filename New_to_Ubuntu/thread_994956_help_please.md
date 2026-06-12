---
title: "help please"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by cybuss on 2008-11-27
hello i need help with a problem,
every time i try to install updates this pops up

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

im new to ubuntu so i have no idea what to do

thanks for the help

---

### Post by dje on 2008-11-27
Welcome :)

open Applications >> Accessories >> Terminal and run (clue - look at the error message ;)):
```
sudo dpkg --configure -a
```
if prompted for a password enter your normal logon password (there will be no feedback as you type, this is normal)

next time please use the search function of the forums this has been posted many times before and please use a descriptive thread title so your thread can be found more easily and maybe attract more help ;)

dje

---

### Post by cybuss on 2008-11-29
whats with the super user thing now? when i type in the command run it says requires superuser privilege how do i make myself super user? i am the only user

---

### Post by linux_tech on 2008-11-29
In a terminal type:

```
sudo su
```

---

### Post by ugm6hr on 2008-11-29
> **cybuss said:**
> whats with the super user thing now? when i type in the command run it says requires superuser privilege how do i make myself super user? i am the only user

This explains a little about the sudo security model: [http://www.psychocats.net/ubuntu/security#sudoisnotroot](http://www.psychocats.net/ubuntu/security#sudoisnotroot)

---

### Post by m_duck on 2008-11-29
Superuser is the main administrator. In most distributions, this is its own user named "root" however in Ubuntu, this account is disabled by default. The first user on the machine (yours) can be temporarily granted root privileges to carry out administrative tasks (installing/uninstalling/modifying system files etc) using "sudo" (SUperuser DO). So, to run the command "dpkg --configure -a" as the superuser, you actually need to run ```
sudo dpkg --configure -a
``` as mentioned by dje.

[More info on sudo in Ubuntu](https://help.ubuntu.com/community/RootSudo).

---

### Post by Tyke91 on 2008-11-29
Basically, you have got user accounts for doing normal things, and a superuser account for doing administrative things. This superuser is named "root" and you can gain root privileges through the sudo command (you can also configure sudo to give you less power, or to give others a lower level of privileges, but we won't go into that right now)

The advantage to this is security. If you are randomly surfing to a website and it downloads somthing to your hard drive without your knowledge (which barely happens in linux anyway) AND it somehow managed to run correctly (which barely happens in linux anyway) then it could ONLY mess up your user's home directory, and the system on the whole would be safe.

Alternatively, you could always run as root, then accumulate a bunch of garbage where you don't need garbage, and wind up reinstalling every month like some windows users do.

---

### Post by cybuss on 2008-11-29
thanks guys, thats alot of info but i got another question about adobe crap
when i go to blizzard then click diablo 3 to watch the videos this is what happens where video things are and i just cant figure it out,

Please get Adobe Flash Player to display this content.

how do i get adobe flash player to display it and how do i find out if i have adobe and latest version?
thanks

---

### Post by nothingspecial on 2008-11-29
```
sudo apt-get install flashplugin-nonfree
```


Then restart firefox

---

### Post by ugm6hr on 2008-11-29
To sort out most multimedia issues, I'd suggest you follow the advice here: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Make sure you use the correct version (i.e. Hardy vs Gutsy etc).

---

