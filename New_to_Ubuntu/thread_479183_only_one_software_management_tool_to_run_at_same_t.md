---
title: "only one software management tool to run at same time problem"
date: 2007-06-20
forum: New to Ubuntu
---

### Post by mjp29 on 2007-06-20
when telling a file to execute

i get a message that only one software management tool to run at the same time

and to please close other applications like [e.g.] update manager, aptitude, synaptic first


how do I close these other applications that I can't see running to make my file execute my update?

---

### Post by wormser on 2007-06-20
only one software updater/installer can run at a time.  I believe this is because it access a data base and it only allows one user so the DB does not get messed up.  Does this happen all the time?  When did it start?  You can go into System> Administration> System Monitor and look to see if there are any of those programs  running.  Also try rebooting.

---

### Post by mjp29 on 2007-06-20
I don't know if it happens all the time, I am new to ubuntu

But following your instructiions, the only thing in system>administration>system monitor that is being used is "gnome-system-monitor" by the system.

I have rebooted and did it again and no success.

---

### Post by wormser on 2007-06-20
Can you give a step by step directions on what you are doing.  This will help us help you.

---

### Post by theracerdude on 2007-10-24
i'm having the same problem it happens when ever i try to install limewire.  i cancelled it the first time and i think that maybe why.

---

### Post by mjp29 on 2009-09-20
Downloaded Limewire and initial attempt to install stalled for over an hour.

Rebooted and downloaded again and now get this message that only one software tool allowed to run at the same time when trying to install.

Any ideas what's going bezerk here?

error message also suggests closing update manager, synaptic, or aptitude  -  but how can I even tell if one of those is running.

---

### Post by Paqman on 2009-09-20
You can only have one of the different package management tools running at once. So you can't use apt-get in the terminal while you've got Synaptic working, for example.

---

### Post by mjp29 on 2009-09-20
> **Paqman said:**
> You can only have one of the different package management tools running at once. So you can't use apt-get in the terminal while you've got Synaptic working, for example.

Makes sense to me.  But where on the ubuntu desktop can I see what is running and force it to quit.

p.s. I did a restart and didn't intentionally tell any of these installer programs to start up

---

### Post by Paqman on 2009-09-20
> **mjp29 said:**
> Makes sense to me.  But where on the ubuntu desktop can I see what is running and force it to quit.

p.s. I did a restart and didn't intentionally tell any of these installer programs to start up

System > Admin > System Monitor.

You may have Update Manager running in the background. It does quietly start itself up and check for updates in the background. It should only take a couple of minutes though, so you might find you're now ok to go.

---

### Post by hambone79 on 2009-09-20
You can try running each of these commands:

**Find apt-* processes**
```
sudo ps -A | grep "apt"
```

**Find update-manager processes**
```
sudo ps -A | grep "update-manager"
```

**Find synaptic processes**
```
sudo ps -A | grep "synaptic"
```

If anything is found it will print out a message that looks something like this (this is searching for "apt" processes with the process ID underlined):

```
_5574_ pts/3   00:00:00 apt-get
```

To kill this process, type this command:
```
sudo kill -9 5574
```

BTW, you may want to check out Frostwire instead of Limewire. It's basically the same app without all the spyware

---

### Post by mjp29 on 2009-09-20
> **Paqman said:**
> System > Admin > System Monitor.

You may have Update Manager running in the background. It does quietly start itself up and check for updates in the background. It should only take a couple of minutes though, so you might find you're now ok to go.

After about 45 minutes I came back and still same messages.

---

### Post by theozzlives on 2009-09-20
```
sudo dpkg --configure -a
```

---

### Post by mjp29 on 2009-09-20
> **hambone79 said:**
> You can try running each of these commands:

**Find apt-* processes**
```
sudo ps -A | grep "apt"
```

**Find update-manager processes**
```
sudo ps -A | grep "update-manager"
```

**Find synaptic processes**
```
sudo ps -A | grep "synaptic"
```

If anything is found it will print out a message that looks something like this (this is searching for "apt" processes with the process ID underlined):

```
_5574_ pts/3   00:00:00 apt-get
```

To kill this process, type this command:
```
sudo kill -9 5574
```

BTW, you may want to check out Frostwire instead of Limewire. It's basically the same app without all the spyware

tried all of that in terminal

still no luck

just curious - how does one tell (without code) what is all running?

---

### Post by mjp29 on 2009-09-20
> **theozzlives said:**
> ```
sudo dpkg --configure -a
```

did that and now get a different message inside the installer

message is 

error:  failed to satisfy all dependencies - broken cache

---

### Post by drs305 on 2009-09-20
> **mjp29 said:**
> 
just curious - how does one tell (without code) what is all running?

As was mentioned earlier, you can run System Monitor. (System, Administration, System Monitor: Processes tab).

In this case though, since you are trying to find installation apps, which are run as root, you should open System Monitor as root so you can view root's running processes:
```

gksu gnome-system-monitor

```

---

### Post by drs305 on 2009-09-20
> **mjp29 said:**
> did that and now get a different message inside the installer

message is 

error:  failed to satisfy all dependencies - broken cache

Try running this, it attempts to update the cache and looks for broken dependencies.
```
sudo apt-get check
```

Also, another way to view current apps is via command line: either "top" or "htop". You have to install "htop" but it is much more versatile.

---

### Post by mjp29 on 2009-09-20
hmmm

don't get the mssg that other installers are running anymore

however, now, even after reboot, the installer says the cache is broken

curious as to what cache is broken - perhaps one of the many command lines i typed into terminal broke the cache of the computer and i should do a system reinstall

only trying out ubuntu on a computer i'm going to put a bigger hd on and reinstall ubuntu anyways if i can get things to work like i'm use to them working on os x

---

### Post by mjp29 on 2009-09-20
> **drs305 said:**
> Try running this, it attempts to update the cache and looks for broken dependencies.
```
sudo apt-get check
```

Also, another way to view current apps is via command line: either "top" or "htop". You have to install "htop" but it is much more versatile.

entered the command line and got

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
E: Unmet dependencies. Try using -f.
michael@michael-desktop:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
michael@michael-desktop:~$

---

### Post by theozzlives on 2009-09-20
> **mjp29 said:**
> hmmm

don't get the mssg that other installers are running anymore

however, now, even after reboot, the installer says the cache is broken

curious as to what cache is broken - perhaps one of the many command lines i typed into terminal broke the cache of the computer and i should do a system reinstall

only trying out ubuntu on a computer i'm going to put a bigger hd on and reinstall ubuntu anyways if i can get things to work like i'm use to them working on os x

Try```
sudo apt-get clean
```

---

### Post by drs305 on 2009-09-20
> **mjp29 said:**
> entered the command line and got

You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
E: Unmet dependencies. Try using -f.
michael@michael-desktop:~$ **apt-get -f install**
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
michael@michael-desktop:~$

This needs to be run as root, again with no other APT/synaptic/add-remove apps running:
```
sudo apt-get -f  install
```

---

### Post by sandyd on 2009-09-20
> **mjp29 said:**
> did that and now get a different message inside the installer

message is 

error:  failed to satisfy all dependencies - broken cache
```

sudo apt-get -f install 

```

or
```

sudo *dpkg* --*force*-all --[I]purge limewire

```

to completely remove limewire.
[/I]

---

### Post by vpgautham on 2010-04-24
Dear hambone79 ,

 You are realy great.I also had the same problem when installing a deb package your advice helped me . You are great man

---

