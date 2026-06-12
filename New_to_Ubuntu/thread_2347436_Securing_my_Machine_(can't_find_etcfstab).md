---
title: "Securing my Machine (can't find /etc/fstab)"
date: 2016-12-25
forum: New to Ubuntu
---

### Post by apol1 on 2016-12-25
Hi there :smile: 

Im looking to crack down on security on my Ubuntu 16.04 LTS

though Ubuntu is already miles ahead as far as security, Id like to have a tank on my castle wall anyway 

Im following a security guide found here [http://www.itsecurity.com/features/ubuntu-secure-install-resource/](http://www.itsecurity.com/features/ubuntu-secure-install-resource/)

However I can't find my /etc/fstab file to begin. 

Additional advice is welcomed as well :smile:

Machine Specs

Video Card: 4GB EVGA NVIDIA GeForce GTX970 GDDR5 video card
Ram: 
DDR4 Memory
   32GB Crucial Ballistix DDR4-2400MHz (4 x 8GB), CAS 16 latency, low voltage

Motherboard

   Asus X99-A/USB 3.1 Intel X99 based chipset, ATX Motherboard

OS: UbuntuLTS 16.04

I am grateful for any and all help :smile:

---

### Post by mikewhatever on 2016-12-25
It's not really a good idea to follow such howtos blindly without much understanding. While the article has some valid points for a server admin, it's of limited value where tanks and castles are involved. All in all, it's a major overkill, unless of course you have nothing better to do.
For example, take the firs two steps:
...I quote from the help page: [https://help.ubuntu.com/community/StricterDefaults?action=show&redirect=UnsafeDefaults](https://help.ubuntu.com/community/StricterDefaults?action=show&redirect=UnsafeDefaults)
> 
There are a few reasons for it to be mounted read/write in specific configurations, such as real-time configuration of a Synaptics touchpad for laptops, but for servers and desktop installations there is no benefit to mounting /run/shm read/write.

Note: MANY programs will not work if you make /run/shm read-only (e.g. Google Chrome). 

Disabling SSH root login is important, but first, ssh-server is not installed by default, and second, root login is disabled by default if you do install ssh-server.

---

### Post by ian-weisser on 2016-12-25
mikewhatever is right. That article is not good advice for a new user.

Editing /etc/fstab safely requires two skills you may not have yet: How to use a terminal, and how to use sudo in a terminal.
A third skill is strongly advised: How to use a terminal-based text editor(like 'nano').

Without those skills, it's easy to accidentally damage your system.

A good security guide for Ubuntu is at [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

Also, this forum has an excellent Security subforum, with many great threads on security threats both real and imagined.

---

### Post by Morbius1 on 2016-12-25
Are we all kinda missing the original issue. Regardless of the value of the HowTo he is following he is missing /etc/fstab. It's not that it's empty it's that it is not present on his system.

How can this be?

---

### Post by mikewhatever on 2016-12-25
> **Morbius1 said:**
> Are we all kinda missing the original issue. Regardless of the value of the HowTo he is following he is missing /etc/fstab. It's not that it's empty it's that it is not present on his system.

How can this be?

I wouldn't be surprised if /etc/fstab was not missing, and the OP just didn't know how to find it. ...probably a good thing in this case.

---

### Post by ian-weisser on 2016-12-25
> **Morbius1 said:**
> How can this be?
It usually means the OP is looking with the GUI file manager (which starts at ~) instead of the terminal, and -understandably- hasn't yet grasped the full intricacies of the filesystem.

That's why my response discussed skills that need to be learned.
Learning the system and the skills are important parts of keeping it secure.

---

### Post by Geoffrey_Arndt on 2016-12-25
Yes . . even with Nautilus search - it takes about 2 seconds max to find fstab.    The trick is you have to start the search from the top of the file system ("computer" in Nautlius) versus "home" . . . . just sayin.

---

### Post by apol1 on 2016-12-29
Thanks for stopping me from nuking myself, Im not sure what you mean by the first two steps.

What is SSH?

---

### Post by ian-weisser on 2016-12-29
SSH is a method to securely login to a remote system, or to securely send commands to a remote system.
 See [https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH) for information about what SSH is about how to use (or avoid) it.

It's important for new tinkerers to understand that all of Ubuntu's features and power are not built on top of the OS.
Those features *are* the OS, in plain sight for all to see, available for you to directly interact with and integrate your own features to.
With that power comes the ability to break your system when you interfere with vital processes.

---

### Post by ericshor on 2016-12-29
I have no /etc/fstab file either,

---

### Post by Morbius1 on 2016-12-30
> **ericshor said:**
> I have no /etc/fstab file either,
Then you are running macOS not Linux.

Seriously, if you run this command it shows nothing?
```
ls -al /etc | grep fstab
```

---

### Post by apol1 on 2017-01-03
heres the output ls -al /etc | grep fstab
-rw-rw-r--   1 root root      750 Oct 26 23:17 fstab

how do I post my terminal output in the code box?

---

### Post by ian-weisser on 2017-01-03
> **apol1 said:**
> -rw-rw-r--   1 root root      750 Oct 26 23:17 fstab
Yes, that's your /etc/fstab. It's in the correct place, doing it's job.

> **apol1 said:**
> how do I post my terminal output in the code box?
See [https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168) for very good instructions

---

### Post by apol1 on 2017-01-06
Great! What exactly is it doing? would it be a smart idea to somehow lock my computer from being accessed remotely? Id like the only way to mess with it be from my home keyboard.

---

### Post by ian-weisser on 2017-01-06
/etc/fstab has absolutely nothing to do with preventing remote access.
Forget those online checklists.
Forget most of what you know about Windows security.

Then take a deep breath.
And start fresh at [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

---

### Post by TheFu on 2017-01-07
> **apol1 said:**
> Great! What exactly is it doing? would it be a smart idea to somehow lock my computer from being accessed remotely? Id like the only way to mess with it be from my home keyboard.

Dude.  The other folks here are too nice to say it, but you need to get some basic Linux skills before worrying about this stuff. You appear to be extremely new to Linux. Extremely.  Not recognizing /etc/ makes this obvious. That directory is a very important location for all Unix-like systems.

The good news is that knowledge is free and easy to get, with just a little reading, some hands-on practice, and experience. If you want to learn, get some basic knowledge about the way the OS works, where things are located and file permissions. If you are coming from Windows, [read this first]("http://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html"). 
[http://blog.jdpfu.com/2014/12/28/learning-linux](http://blog.jdpfu.com/2014/12/28/learning-linux) - has my considered recommendations for learning Linux. There is a free, no-hassle, PDF book in there which can take you from noob to power-user.  That book is published and available at most bookstores. It isn't a "self-published" thing.

Your thirst for knowledge is a great asset. Use it. Learn.  

The main things you need to do for a secure (as possible) Ubuntu Desktop is:
a) stay patched
b) perform automatic, daily, versioned, backups

Everything after that is just noise, without the proper understanding of what any other settings actually do, anyone is just as likely to break the system as to secure it. Making a trivial mistake out of ignorance is something we all do when first starting out.  Builds character. ;)

Plus, this stuff is fun, right?

---

### Post by ian-weisser on 2017-01-07
> **TheFu said:**
> Making a trivial mistake out of ignorance is something we all do when first starting out.  Builds character. ;)

Plus, this stuff is fun, right?

+1
Oh, yeah.
Right on all counts.

---

