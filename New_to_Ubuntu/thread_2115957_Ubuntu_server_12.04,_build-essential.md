---
title: "Ubuntu server 12.04, build-essential"
date: 2013-02-14
forum: New to Ubuntu
---

### Post by uttamhathi on 2013-02-14
ok i am a newbee
i have installed ubuntu server 12.04 the problem is that 
sudo apt-get install XXXX installs nothing
build essentials does not exists
thought i could work samba does not reflect in my xp
/get/samba/smb.conf does not work 
/get/XXXX.yyy is basically permission denied
thus its unusable to me
working on this for a week 2-3 hrs a day have not reached anywhere to call it working

---

### Post by oldos2er on 2013-02-14
Post moved to its own thread.

---

### Post by snowpine on 2013-02-14
Welcome to the forums!

First use:

```
sudo apt-get update
```

Then you ought to be able to install build-essential:

```
sudo apt-get build-essential
```

If there are any errors, then please copy & paste the terminal output in its entirety so we can help. :)

---

### Post by Zill on 2013-02-14
> **uttamhathi said:**
> ...
sudo apt-get install XXXX installs nothing
build essentials does not exists...
Quite correct - build essentials does *not* exist!

But "build-essential" does.

```
sudo apt-get install build-essential
```

---

### Post by gordintoronto on 2013-02-14
"/get/samba/smb.conf does not work"

What are you trying to do? What you typed is not a command. Perhaps you want:
sudo nano /etc/samba/smb.conf

Unless you are trying to run a high-volume web site or database, or are running on very limited hardware, I suggest installing Ubuntu Desktop, then install the server programs on top of it. That way, all the standard GUI tools are available.

If all you want is folder sharing, there is no need to edit smb.conf, it can all be done in the GUI.

---

### Post by mastablasta on 2013-02-15
> **gordintoronto said:**
>  
Unless you are trying to run a high-volume web site or database, or are running on very limited hardware, I suggest installing Ubuntu Desktop, then install the server programs on top of it. That way, all the standard GUI tools are available.
 .
 
that would be a waste of system resources. besides icewm would be quite enough to jst have a GUI.
 
and furthermore there are specific server GUI such as webmin and zentyal for example. server is then acessed and configured from another computer via web browser.

---

### Post by gordintoronto on 2013-02-15
I saw no indication that the OP had mastered SSH or any other remote management tool.

99.9% of modern computers have ten times as much system resources available as you need to run a file server -- but using the command line baffles many people. It's a simple trade-off.

Most people just want to get the job done, not spend the next two years learning about the tools you suggest.

---

### Post by cariboo on 2013-02-15
Instead of running a gui desktop when you don't need it, install your favourite desktop, and either remove or disable the desktop manager. For example to install Gnome:

```
sudo apt-get install -y gnome-desktop-environment
```

Once the install is finished, reboot, and you should be taken to a prompt. To run in an gui environment, at the prompt type:

```
startx
```

and when you're done, just log out.

---

