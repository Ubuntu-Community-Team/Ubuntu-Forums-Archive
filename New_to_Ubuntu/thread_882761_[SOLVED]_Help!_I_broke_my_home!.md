---
title: "[SOLVED] Help! I broke my /home!"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by diego898 on 2008-08-07
I followed the advice of someone on this post:
[http://ubuntuforums.org/showthread.php?t=876495](http://ubuntuforums.org/showthread.php?t=876495)

to change my /home partition to 
```

chmod 750 $HOME
```

Then, I followed psychocats tutorial to MOVE my /home to another partition. I thought everything worked great I had no problems. Now when I restarted and went to login, I type in my username and password, only to get


> Users' $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users.

Naturally, I just press OK and the screen changes as if its trying to go to my desktop from the login screen, stays that beige color for a while until I get 

> The GNOME session manager was unable to lock the file '/home/diego/.ICEauthority'. Please report this as GNOME bug. Sometimes this error may occur if the file's directory is unwritable, you could try logging in via the failsafe session and ensuring that is it.

So, I press ok and it takes me back to my login screen. Since the tutorial for moving /home has been widely used, I am almost pretty sure it has to do with the fact that I changed the permissions on my /home directory before I tried to move it. Can anyone help me correct this problem?


Thanks in advance.

---

### Post by limasierra on 2008-08-07
At login select the failsafe option and login. Then open a terminal and type```
chmod 755 $HOME
```

---

### Post by tamoneya on 2008-08-07
what you need to do is get to recovery console.  You do this by hitting "escape" when grub loads (the thing directly after the bios).  There is an option for recovery mode.  When you select it it will put you into a root shell so you have to be careful because you can do some serious damage.  Here are the commands that should fix things. <username> equals your username

```
sudo chown -R <username>:<username> /home/<username>
sudo chmod 644 /home/<username>/.dmrc
```

---

### Post by tamoneya on 2008-08-07
> **limasierra said:**
> At login select the failsafe option and login. Then open a terminal and type```
chmod 755 $HOME
```

Just adding more permissions to things doesnt just make things magically better.  It can cause serious problems sometimes especially when you are dealing with system files instead of just user files.

---

### Post by diego898 on 2008-08-07
Well I was able to boot into ubuntu now with no problems. How can I verify that my /home is now on the seperate partition and that everything is fine? Is there some kind of diagnostic I can run?

---

### Post by tamoneya on 2008-08-07
> **diego898 said:**
> Well I was able to boot into ubuntu now with no problems. How can I verify that my /home is now on the seperate partition and that everything is fine? Is there some kind of diagnostic I can run?

Go system -> administration -> system monitor.  Then go into the filesystems tab and it will show you all your mount points.

---

### Post by diego898 on 2008-08-07
That shows /home as being on the seperate partition so thats ok. I dont know if this is related, but now when I try to type sudo apt-get autoclean I get this:
> 
diego@Zeus:~$ sudo apt-get clean
diego@Zeus:~$ sudo apt-get autoclean
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
diego@Zeus:~$ sudo apt-get install gtkorphan
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


I dont know if this is related?

---

### Post by howlingmadhowie on 2008-08-07
no, it's not likely that that's related. it sounds like aptitude crashed while installing software. if you start synaptic, it gives you the option of automagically fixing this sort of thing.

if you don't want to use synaptic, have a look to see if /var/lib/dpkg/lock exists. if it does, try deleting it and as root touching a new one.

---

### Post by diego898 on 2008-08-07
How do I make synaptic fix this?

---

### Post by tamoneya on 2008-08-07
> **diego898 said:**
> How do I make synaptic fix this?

howlingmadhowie's post is right on.  run this command:```
sudo rm -i /var/lib/dpkg/lock
```

---

### Post by suryapraveen on 2008-08-12
appreicate it 

really helpful

my ubntu is back

---

