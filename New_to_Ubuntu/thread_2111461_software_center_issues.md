---
title: "software center issues"
date: 2013-02-02
forum: New to Ubuntu
---

### Post by killanna on 2013-02-02
Ok any time i try to download anything from the software centre if locks up with applying changes then when i cancel it it sits and cancels forever and wont go away rebooting dose not help stays cancelling when you open the software centre got it to go away once but same thing happened the next time i tried to download same thing happened.

tried sudo apt get-purge software-center
sent me into this thing that i had to unlock 
did the sudo apt configure -a something 
then it starts going on about flash player but then it just sits there and doesn’t give me a prompt to do anything elts 

I don’t understand why i'm having so many issues on this pc with 12.04 I have had none with my laptop and 12.10

---

### Post by fantab on 2013-02-02
Post the output of:

```
$ sudo apt-get update
```

---

### Post by srekcahrai on 2013-02-02
First try this code:
```

sudo rm -R /var/lib/dpkg/lock
sudo dpkg --configure -a

```

If this doesn't work then use this command
```

sudo rm -R /var/lib/dpkg/lock
sudo rm -R /var/cache/apt/archives/
sudo dpkg --configure -a

```

---

### Post by killanna on 2013-02-02
here is the dialogue

killanna@killanna-System-Product-Name:~$ sudo rm -R /var/lib/dpkg/lock
rm: cannot remove `/var/lib/dpkg/lock': No such file or directory
killanna@killanna-System-Product-Name:~$ sudo rm -R /var/cache/apt/archives/
killanna@killanna-System-Product-Name:~$ sudo dpkg --configure -a
Setting up update-notifier-common (0.119ubuntu8.6) ...
Setting up libfaad2 (2.7-7) ...
Setting up libgstreamer-plugins-bad0.10-0 (0.10.22.3-2ubuntu2.1) ...
Setting up libslv2-9 (0.6.6+dfsg1-1) ...
Setting up libquicktime2 (2:1.2.3-4build2) ...
Setting up gstreamer0.10-plugins-bad (0.10.22.3-2ubuntu2.1) ...
Setting up flashplugin-installer (11.2.202.261ubuntu0.12.04.1) ...
Setting up libmjpegtools-1.9 (1:1.9.0-0.5ubuntu7) ...
Setting up gstreamer0.10-plugins-bad-multiverse (0.10.21-1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
killanna@killanna-System-Product-Name:~$

---

### Post by killanna on 2013-02-02
still having issue

---

### Post by ibjsb4 on 2013-02-02
> **killanna said:**
> still having issue

Please update as posted above and post output using code tags.

```
sudo apt-get update
```

[ATTACH]230960[/ATTACH]

---

### Post by willygatti on 2013-03-30
I'm having the same issue on Ubuntu 12.10.  I tried all the suggestions in this thread and I still can't install applications from the Ubuntu Software Center.  What else can I do?

```
willygatti@willygatti-Inspiron-1525:~$ sudo apt-get update
[sudo] password for willygatti: 
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/

```

---

### Post by fantab on 2013-03-30
@willygatti: there seems to be another apt application, like Software Center or Synaptic or Software Updater, open. Use only one apt application at a time. If you are using Terminal to update then close all other Update software.

---

