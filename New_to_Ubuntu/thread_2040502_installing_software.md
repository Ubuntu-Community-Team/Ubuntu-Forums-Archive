---
title: "installing software"
date: 2012-08-11
forum: New to Ubuntu
---

### Post by cilybeb on 2012-08-11
I want to download software  manslide to produce a slideshow with different soundtracks for the pictures. it is not available in  uibuntu software centre.
the instructions to download manually are:

To install Manslide (2.0.3) under Ubuntu 12.04/11.10, open the terminal and run this sequence of commands:

**sudo add-apt-repository ppa:upubuntu-com/graphics**

**sudo apt-get update**

**sudo apt-get install manslide**
can anyone guide me to where I should type in the commands 
thanks in advance

---

### Post by Kalanac on 2012-08-11
hit:

ctrl+alt+t

This will open a terminal window.  Type the commands in there.

---

### Post by cilybeb on 2012-08-11
I am trying to instsall manslide and have come up to the following message: 
```
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe Translation-en
Fetched 1,093 kB in 2s (408 kB/s)
Reading package lists... Done
paul@paul-G41MT-S2P:~$ sudo apt-get install manslide
Reading package lists... Done
Building dependency tree       
Reading state information... Done
manslide is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 73 not upgraded.
paul@paul-G41MT-S2P:~$ 
paul@paul-G41MT-S2P:~$ 
paul@paul-G41MT-S2P:~$ sudo apt-get install manslide
Reading package lists... Done
Building dependency tree       
Reading state information... Done
manslide is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 73 not upgraded.
paul@paul-G41MT-S2P:~$
```
can anyone tell me how I can go from here to insatll 
thanks in advance

---

### Post by ajgreeny on 2012-08-11
What that says is that manslide is already installed and is also the latest version that is available from the repos.

Have you added the ppa [https://launchpad.net/~upubuntu-com/+archive/graphics](https://launchpad.net/~upubuntu-com/+archive/graphics) which is needed for manslide?  See [http://ubuntuforums.org/showthread.php?t=2040502](http://ubuntuforums.org/showthread.php?t=2040502) for details.

---

### Post by Elfy on 2012-08-12
Please do not post duplicates, it dilutes community effort. Threads merged

---

### Post by cilybeb on 2012-08-12
apologies but on absolute beginner because I am  that.
can anyone help with the install please

apologies for 3rd post on this subject. I am still struggling to find a way of completing the install of manslide.
I have confirmation that it is installed but am left with  the message :
paul@paul-G41MT-S2P:~$ 
and cannot figure what I should now do. can anyone shed any light??

---

### Post by Shadius on 2012-08-12
> **cilybeb said:**
> apologies but on absolute beginner because I am  that.
can anyone help with the install please

apologies for 3rd post on this subject. I am still struggling to find a way of completing the install of manslide.
I have confirmation that it is installed but am left with  the message :
paul@paul-G41MT-S2P:~$ 
and cannot figure what I should now do. can anyone shed any light??

That's just your host name, I believe. If you read through the output, you'll see that it statese that *manslide* is already installed.

> manslide is already the newest version.

---

### Post by cilybeb on 2012-08-12
I realise that I am being told that manslide is installed but the lasr line:
paul@paul-G41MT-S2P:~$ 
is as far as I can go . I am unsure how to complete the installation from that point. manslide does not appear in my dash
thanks for the advice

---

### Post by Shadius on 2012-08-12
> **cilybeb said:**
> I realise that I am being told that manslide is installed but the lasr line:
paul@paul-G41MT-S2P:~$ 
is as far as I can go . I am unsure how to complete the installation from that point. manslide does not appear in my dash
thanks for the advice

Does anything come up in the Dash when you type in "manslide"?

---

### Post by cilybeb on 2012-08-12
thanks for all the help. manslide now installed and working

---

