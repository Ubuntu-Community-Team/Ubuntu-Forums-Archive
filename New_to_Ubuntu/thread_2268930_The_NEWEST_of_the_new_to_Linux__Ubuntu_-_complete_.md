---
title: "The NEWEST of the new to Linux / Ubuntu - complete newbie"
date: 2015-03-12
forum: New to Ubuntu
---

### Post by Joe_Foster on 2015-03-12
Hello everyone. I'm a longstanding Microsoft guy who is just migrating into a new role supporting some Ubuntu laptops. 

I am wondering the usual questions, trying to get a base under me - 

1. Is there any good Admin kind of guide I can read to familiarize myself with the complete Ubuntu / Linux OS ? I need everything. I really am starting from complete zero here. 

2. How does one enable the "Admin" section of the Ubuntu Desktop OS ? I installed Ubuntu, but don't see it listed. At least this would give me something to try to connect / familiarize myself with ?

3. What are the common "gotchas" or things I REALLY SHOULD know to successfully support this OS ? I am planning in keeping everything completely standardized, on all machines. Conversely, what should I NOT do ?

4. From what I have seen so far, the boot process itself, to be honest, scares me. I cannot even begin to fathom it's processing, or, what each of these individual modules refers to, or, worse yet, how to repair one of them should they crash / cascade and take everything else down with it. How do I even remotely begin to make sense of this boot process / items within?

5. What common types of problems do you experience with this OS? What are some of the most frequent problems I should expect to see, and their resolutions?

6. I really do have ZERO Linux experience, so I appreciate the steps in the right direction, so ANYTHING else that may come to mind, please, by all means, feel free to share !

I sincerely thank you, and look forward to hearing from you !

-Joe

---

### Post by v3.xx on 2015-03-12
Easy way is to give it a test drive.  Whatever ubuntu you want to use can be burned to dvd and tried out without installing.

And #1
[https://ubuntu-manual.org/](https://ubuntu-manual.org/)

[URL="http://ubuntuguide.org/wiki/Ubuntu_Trusty"]http://ubuntuguide.org/wiki/Ubuntu_Trusty

[https://help.ubuntu.com/14.04/ubuntu-help/index.html](https://help.ubuntu.com/14.04/ubuntu-help/index.html)

[/URL]

---

### Post by dino99 on 2015-03-12
Welcome to Linux Joe :p

i feel i can propose to you some readings which might help you alot. Check the first link below, and then glance at the sub-links to get an overview about Ubuntu/Linux  ):p

---

### Post by Frogs Hair on 2015-03-12
This can be found in the Wiki link/s provided above .

[https://wiki.ubuntu.com/Booting](https://wiki.ubuntu.com/Booting)

---

### Post by grahammechanical on 2015-03-12
> [COLOR=#000000]role supporting some Ubuntu laptops. [/COLOR]

The people using these Ubuntu laptops, will they be using them in some specialist way or will they be the usual, normal kind of user? If you are supporting the kind of user that wants to do the usual kind of things then you do not need to get too involved in how Linux works. But you will need to know how Ubuntu works.

> [COLOR=#000000]the boot process itself, to be honest, scares me.[/COLOR]

It completely mystifies me! But then I do not need to know the ins and outs of booting and loading Ubuntu in order to offer support on this forum.

Identify what the users want to do with these machines. And workout how to do it. And try to identify what can go wrong and what needs to be done to fix things. Studying threads on this forum can help with this.

If you read the threads on this forum you will see the difficulty we have in finding out what hardware people have and what they have done to cause the problem and what they are trying to do. Often people will say that there is problem and then expect us to know how to fix it without them explaining what it is that they are seeing on the screen. You will be in the same situation. Be ready to ask questions to draw out of the person what is happening on the computer.

Become experienced in installing Ubuntu and setting up internet access. Every install of Ubuntu has a Ubuntu desktop guide. It is called help. Learn how to do things and then you can teach others to do things.

Become familiar with Recovery mode. We find it in the Advanced Options for Ubuntu sub-menu. 

Study how to partition and reinstall using the Something Else option. A default install of Ubuntu will put Ubuntu in one partition and the user's data and configuration files into a folder called /home on that same partition. Re-installing Ubuntu risks loosing user data. But, if we have a separate /home partition instead of a /home folder then we can re-install Ubuntu without deleting the user's data and configuration files. Learn how to install Ubuntu by creating partitions and using the Something Else option. A re-install fixes a lot of problems.

Learn how an internet search using wiki ubuntu <subject> can lead you to documentation for doing different things in Ubuntu and Linux. Try searching for "wiki ubuntu install" and "wiki ubuntu partitioning." I do this all the time.

Knowing certain Linux commands is useful but what is more useful is understanding what the results mean. Practice running the commands on a working Ubuntu then copy the printout into a document then you will have something to compare with a printout of the command from a non-working Ubuntu. The differences will help identify what needs to be fixed.

If you want training, then try to give help on this forum. It is a fine way of being trained to give support on Ubuntu.

Regards.

---

### Post by bookrt on 2015-03-12
I am not sure what you mean by "Admin Section". What are you trying to do that you would expect to find there?

As far as booting and such, you might want to familiarize yourself with GRUB. This is the bootloader and you can manually edit the file with different options. You can choose whether to have a visible menu to choose your OS, or boot straight to your default desktop. You can choose to load certain graphics or audio drivers, etc. If your system ever crashes following an update and you want to revert to a previous version or boot into system recovery, you will need to familiarize yourself with GRUB.

[https://help.ubuntu.com/community/Grub2/Setup#Configuring_GRUB_2](https://help.ubuntu.com/community/Grub2/Setup#Configuring_GRUB_2)

If you want to learn more about what GRUB is actually doing, I would suggest manually editing grub to remove the "quiet splash" command. This will then make visible in real time all of the processes it goes through to boot the OS. By doing this exercise, you will simultaneously learn how to use a text editor, how to edit a system file, learn at least one GRUB option, and learn more about what GRUB actually does.

[http://unix.stackexchange.com/questions/152908/how-to-bootup-reboot-in-verbose-mode](http://unix.stackexchange.com/questions/152908/how-to-bootup-reboot-in-verbose-mode)

---

### Post by ian-weisser on 2015-03-12
Ubuntu is designed to be easily discoverable and have safe defaults.
The preferred way of learning to navigate your system is to play with it. It's hard to break.

If you try to do something that requires admin permission, like install or remove software, the system will prompt for the administrator's password. That's your clue that you are in admin territory.

You must unlearn the Windows ways of software and security. Do not download packages from random websites. Use Software Center instead. Do not install random drivers from the internet for hardware compatibility. Purchase compatible hardware, and the Linux Kernel will magically recognize it. Do not try to install an antivirus application. Windows viruses and malware do not work in Linux. Ubuntu has a very good security team, and we handle security a very different way. Do not try to install a firewall application. The Linux Kernel includes a firewall already, which many users don't need (nothing useful is listening).

You must become accustomed to the Debian/Ubuntu *software packages* which you manage using Software Center, and which receive frequent security and bugfix updates through Software Updater.

The "most common problems" were long ago fixed, and are no longer common problems. If you run into a problem, ask.

---

### Post by maclenin on 2015-03-12
**Joe_Foster!**

[This is where I started]("http://psychocats.net/ubuntu/") - and I've never looked back!

Good luck!

---

### Post by mastablasta on 2015-03-13
> **Joe_Foster said:**
> 
2. How does one enable the "Admin" section of the Ubuntu Desktop OS ? I installed Ubuntu, but don't see it listed. At least this would give me something to try to connect / familiarize myself with ?


you mean root/sudo ? : [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Also man command is your friend. :P

> 
5. What common types of problems do you experience with this OS? What are some of the most frequent problems I should expect to see, and their resolutions?


if PC uses components that have good opensource driver support then hardly any maintenance is needed from this point. 
if you use some nVidia or AMD GPU might proprietary driver - this is the first issue - drivers may get overwritten on kernel update and might need a reinstall. it shouldn't happen, but occasionally it does. 2 times so far for me in 3 years. it's easy to solve but requires a few commands to be input
if there is poor support with drivers then experience can be painful.

it might be good to set the unattended updates to push at least security patches automatically to the users. they do not cause issues I mentioned before.

otherwise I suggest you explore the OS yourself a bit. see what you come up with. maybe install it in virtual box mess it up completely restore it and start messing it up again.

on (especially) laptops sometimes an upgrade (not update but version upgrade) makes stuff not to work. manual hacking or workarounds are then necessary (until they fix the bug, if they fix it).

also windows programs won't work on Ubuntu :P well actually some will via WINE.

---

### Post by coldraven on 2015-03-13
As already mentioned the Software Centre is where you can search for packages. You can also install Synaptic Package Manager, think of it as Software Centre Pro. You cannot run two package managers at the same time. If you are running, say, Synaptic then try to do a command line install it won't work, they all use the same commands underneath.
I found it useful for discovering things that I had never heard of. Also if you right click on an installed application, under Properties, it will show you where all it's files are kept. Sometimes you discover related documents in a place where you would not normally look.
```
sudo apt-get install synaptic
```
The man command is your friend, like this
```
man <program_name>
```
or this :)
```
man man
```
If you don't know a command you can try this (using copy as an example).
```
man -k copy
```
or
```
apropos copy
```
As for point number five:
I installed Ubuntu 10.04 on my computer illiterate neighbours laptop. It had no anti-virus software and no firewall configuration. **In four years I had no support calls and was working perfectly.** I just updated it to Ubuntu 14.04 and swapped the HDD for a SSD. It now boots in 11 seconds!

---

### Post by kevdog on 2015-03-13
Good luck to you man -- yes I suppose I was in your shoes one day -- I had to be -- it has been so long that I can't remember.  My only advice is to keep having fun and don't be afraid to read a lot of things on either the forums or internet.  Don't get too frustrated.  And start with a goal in mind -- just not for general knowledge.

---

