---
title: "New User would like GUI in Ubuntu Server 8.10"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by Yaegermeister on 2008-11-30
Hello,

I have just literally installed Ubuntu Server 8.10 and when it boots up all I get is the terminal.  I log in using the username and password that I established during setup.  

Here is what I would like to be able to do.  Have a GUI.  I don't know Linux enough to do it all from the command line.  Maybe someday but not yet.  I want to do mainly two things with this server. One is to put files on a drive on the server that I can access from the NET wherever I happen to be.  Two I would like to use this as a host for online gaming.  I am pretty sure that this can be done with this software but I do not know how to do it.

C**an someone help me get a GUI and setup a DHCP so this machine can connect to the internet.  Thank you!**

PS.  No issues during installation.  Did not setup networking settings.

John

---

### Post by cariboo on 2008-11-30
To install the Ubuntu desktop at the prompt type:

```
sudo apt-get install ubuntu-desktop gdm
```

This will install the desktop and its dependencies. This will also install network manager which will automagically set up your internet connection.

Jim

---

### Post by Xiong Chiamiov on 2008-11-30
Of note is that you don't need Ubuntu Server for it to act as a server; Server edition merely has a lot of the normal desktop crap cut out that is normally installed, but you probably want.

---

### Post by Yaegermeister on 2008-11-30
Thanks Cariboo907, I will give it a go in the morning.  

Xiong,  So would I be able to do what I want to with the desktop version?

John

---

### Post by Xiong Chiamiov on 2008-11-30
You would.  The only difference between the versions (besides a slightly different kernel) is the packages preinstalled.  If you're not comfortable with Linux and the terminal yet, then I'd suggest starting with the normal desktop version.  If you gain enough knowledge later and want to improve performance by cutting out the GUI, you can do so.

---

### Post by Yaegermeister on 2008-11-30
Ok,

I tried the sudo apt-get install ubuntu-desktop gdm and I get the following:

Reading package lists...done
Building dependency tree
Reading state information...done
E: Could not find package ubuntu-desktop

It brings me back to the server@ubuntu:~$ prompt.

Any ideas?

Thanks, John

---

### Post by halitech on 2008-11-30
might not be connected to the net yet. issue this command and post back the info
```
cat /etc/network/interfaces
```

---

### Post by Dr Small on 2008-11-30
Bust solution is to reinstall with the Desktop edition if you are not comfortable with a command line, as that's what the server edition was built for.

---

### Post by halitech on 2008-11-30
why go through downloading and reinstalling if he has server installed? would be easier just to install what he needs in one command in thee terminal then get synaptic and install the rest of what he wants.

---

### Post by Dr Small on 2008-11-30
> **halitech said:**
> why go through downloading and reinstalling if he has server installed? would be easier just to install what he needs in one command in thee terminal then get synaptic and install the rest of what he wants.
It is possible, but the other way is meerly more simple if he has the Desktop cd laying on his desk.

---

### Post by halitech on 2008-11-30
I guess we are both making assumptions, you assume they have the desktop cd and their system can handle the install of such and I assumed we will easily be able to get their network up and running easily. Let's see what happens :)

---

### Post by louieb on 2008-11-30
> **Yaegermeister said:**
> Ok, I tried the sudo apt-get install ubuntu-desktop gdm and I get ...
1st try getting an IP address
```
sudo dhclient 
```
then try updating your software sources 
```
sudo aptitude update
```then bring your software up to date
```
sudo aptitude full-upgrade
```then try adding the desktop.

---

