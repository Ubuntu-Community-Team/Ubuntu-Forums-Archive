---
title: "Can not remove avast antivirus"
date: 2012-06-11
forum: New to Ubuntu
---

### Post by Bob Saget on 2012-06-11
I installed it, tried to update it, and then the program keeps crashing with an invalid argument.  So I decided to uninstall it.  I can't find it in the ubuntu software center even though it went through there to install in the first place.  I know I can use terminal to uninstall it, but here's my problem


> patrick@ubuntu:~$ sudo apt-get remove avast4workstation - avast! antivirus for Linux
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


I am currently updating my system with the 254 updates I got hit with.  Any chance that is the otherr process using the directory?

---

### Post by deadflowr on 2012-06-11
Yep. If your currently updating your system, let it finish then do what you want to do./var/lib/dpkg/lock means the service is in use. Messing with it can cause big problems.

---

### Post by wilee-nilee on 2012-06-11
How about we actually fix the error it is easy.

Open this file.
  	 	 	 	 	 	   ```
sudo gedit /etc/sysctl.conf
```
At the end of the file insert this.
   	 	 	 	 	 	   
```
kernel.shmmax = 128000000
```
Then run this command

       	 	 	 	 	 	   ```
sudo sysctl -p
```


Avast will work now.

---

### Post by Bob Saget on 2012-06-11
ok the  last few lines in that file opened on gedit went like this after the editing 

> # Log Martian Packets
#net.ipv4.conf.all.log_martians = 1
#kernel.shmmax = 128000000

I then see this in terminal


> (gedit:4691): GLib-GIO-WARNING **: Missing callback called fullpath = /root/.local/share/recently-used.xbel

sudo sysctl -p appears to cause no response in terminal, and avast still claims an invalid argument.

---

### Post by wilee-nilee on 2012-06-11
No # in front of the line that comments it out.                                   ```
kernel.shmmax = 128000000
```  Then run this command in lieu of a reboot that will just load it.
                                  ```
sudo sysctl -w kernel.shmmax=128000000
```
You had no response from the second command due to putting the stanza in commented out.

---

### Post by Bob Saget on 2012-06-11
ok thanks my system updates are almost through I'll let them finish up before I reboot.  Gonna sleep on it though, my internet is a bit slow.  I'll let yall know how it goes tomorrow, 12 June  I got a job to wake up to. =\

---

### Post by Bob Saget on 2012-06-11
ok I took the comment out, then did sudo sysctl -p, terminal replied with kernel shmmax=128000000

and avast works now.

Thanks for the help man.  I appreciate it.

---

### Post by mosaic2s on 2012-06-12
to remove any application, you should use synaptic package manager.

---

### Post by wilee-nilee on 2012-06-12
> **Bob Saget said:**
> ok I took the comment out, then did sudo sysctl -p, terminal replied with kernel shmmax=128000000

and avast works now.

Thanks for the help man.  I appreciate it.

No problem it seemed at least getting it working was a good option, you can remove it later if you want.

It will give false positives so always look on the web before you wipe something.

I get reoccurring false hits on a W7 page.file a XP virtual, both attached to comodo running on both.

---

### Post by Bob Saget on 2012-06-12
avast triggered a bunch of internal errors in ubuntu as soon as I logged in, so bad the error reporter crashed.  needless to say, > sudo apt-get remove avast4workstation   lol

---

### Post by Matthew Ianniello on 2012-07-13
Thanks for the solution.

---

