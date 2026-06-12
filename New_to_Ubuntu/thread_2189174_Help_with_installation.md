---
title: "Help with installation"
date: 2013-11-21
forum: New to Ubuntu
---

### Post by sohail.connected on 2013-11-21
hello guys,
	I am a newbie in this complicated ubuntu world and i need some help in installing ubuntu 13.10. I hav 4 partitions:


1st partition - NTFS
2nd Partition - NTFS
3rd partition - NTFS
4th partition - NTFS


The first partition has windows 8 pro in it. I want to install saucy salmander in partition 2. and i want to use the 4th partition as swap.Since the 2nd partition already has ubuntu 10.04 in it which is not wroking(?Major GUI Error) i will format the 2nd partition and install ubuntu 13.10 using the USB Live disk that i have created. I will be using custom installation option for this. Where do i set the mount point for my 2nd partition after formating it? Okay so after this i have no issues but in the future i will install ubuntu 12.04 in the 3rd partition as well(Not sure but mostly no). So when i do that how do i tell both the distros to use the same swap partition(4th partition)


Also could you pls explain me about maintaining a seperate grub partition that some users talk about?


And i will also like to know about how all the programs in my 13.10 distro must be automatically be installed in 12.04 and not only the programs but also any other files like those in my HOME folder. 


also is it possible to install 2 distros in the same partition(I know its stupid but i have seen it)


Thanks in advance

---

### Post by Bucky Ball on 2013-11-21
Firstly, you can upgrade 10.04 to 12.04 in one click using the update manager. Set software sources>updates to notify of long-term support releases.

Secondly, if you are doing a manual install, then go ahead and install 13.10 right over 10.04. 

Just a note: There is no possibility you can have 10.04 installed on any of these partitions as they are ALL NTFS. Ubuntu will not install on that filesystem. You need to use EXT*. So, I'm presuming you have Windows with a Ubuntu Wubi install. That is not a dual-boot, that is Ubuntu installed in Win like any other program would be.

Your /swap partition only needs to be 2Gb and mount points will be made when you install. You are limited to four primary parititions also, so I'd probably have a rethink.

Give that list again and add exactly what you have installed where.

The only way to install two OSs in one partition is by installing one as a virtual machine.

As for this:
> 
And i will also like to know about how all the programs in my 13.10 distro must be automatically be installed in 12.04 and not only the programs but also any other files like those in my HOME folder. 

Two installs on two separate partitions will have nothing to do with each other so not sure what you're asking there, sorry. You can have them use the same /home or /data partition so they are accessing the same personal data, but as for programs, they need to be installed separately in each OS. ;)

---

### Post by sohail.connected on 2013-11-21
Oh Oh sorry mate,


2nd partition is EXT4
4the partition is swap :)


And one more thing. I am assuming that u like and know lots about bucky-balls and i had one question. How do u implant a lanthanum atom inside the buckyball to get a rage-in-the-cage molecule??

---

### Post by sohail.connected on 2013-11-21
> **Bucky Ball said:**
> You can have them use the same /home or /data partition so they are accessing the same personal data, but as for programs, they need to be installed separately in each OS. ;)
 So how do u make them use the same /home or /data partition. Thanks mate and pls answer my lanthanum question above

---

### Post by Bucky Ball on 2013-11-21
> **sohail.connected said:**
> 
And one more thing. I am assuming that u like and know lots about bucky-balls and i had one question. How do u implant a lanthanum atom inside the buckyball to get a rage-in-the-cage molecule??

Ha, sorry. Like them? Yes. Know a lot about them? No. Can't answer that. Bit out of my league. But I can answer this:

When you install the first OS (presuming you have that on sda2) you have a couple of options. 

1/ If you have a /data partition you can install as per normal, with the /home folder defaulting to inside /. You then delete the folders in there, like /Documents, /Videos, etc. and create symlinks to folders that already exist (or don't) on your /data partition. 
Then, when you install the second OS on another partition (or third or fourth) you do the same, create symlinks in /home folder to the folders on your /data partition. 

This is the method I use. That way, doesn't matter what OS you boot, you're always accessing the same data.

2/ When you install the OS, create a separate /home partition. When you install the second OS, do a manual install (Something Else) and mark the existing /home and /swap as 'use' but DO NOT have them ticked to format. The second install will then use these partitions by default WITHOUT wiping the data inside the /home partition.

As you already have a /swap partition there is no need to create a new one for any other Ubuntu install (and some other distros, too).

For instance, if you have a data partition, you could boot from a LiveCD, grab the personal data (or the folders containing it) from the 10.04 /home folder and dump it into the /data partition, then install over 10.04, delete the folders in the new install's /home partition and create symlinks to the data folders in /data. New OS, same data.

---

### Post by sohail.connected on 2013-11-21
Hello Buck ball, Thanks for ur reply. Installed ubuntu 13.10 properly. But i made one big blunder. I set my USERNAME as the-coder. Is there a way to change it to carbogen-chemist(i am a chem lover)??

And do u brainiac devs by-heart each and every code?? Like i asked how to install oracle java in freenode irc(#xda-devs) and 100 people replied. Do u remember all codes or u have a way to you know just work it out?

---

### Post by simbauad on 2013-11-21
Oops! Never had this problem. Try:
```
sudo nano /etc/hostname
```
Replace the-coder with carbogen-chemist
To save the file ctrl+o and then to exit ctrl+x and then tell us if it changes your username.

---

### Post by Bucky Ball on 2013-11-21
> **sohail.connected said:**
> 
And do u brainiac devs by-heart each and every code?? Like i asked how to install oracle java in freenode irc(#xda-devs) and 100 people replied. Do u remember all codes or u have a way to you know just work it out?

No memory tricks involved (generally). Experienced users tend to keep a record of things that people ask frequently and solutions to problems, bits of code to do common stuff, etc., and bookmark helpful websites. Easy really! ;)

---

### Post by sohail.connected on 2013-11-22
> **simbauad said:**
> Oops! Never had this problem. Try:
```
sudo nano /etc/hostname
```
Replace the-coder with carbogen-chemist
To save the file ctrl+o and then to exit ctrl+x and then tell us if it changes your username.

the-coder@Angel-desktop:~$
This is how it shows up in my terminal. What u said to do, i did but that allows me to change my hostname(Angel-desktop) iwanna change my username(the-coder) and make it carbogen-chemist@Angel-desktop:~$

---

### Post by Bucky Ball on 2013-11-22
Please research before posting. There are SOOOO many pages on the interwebs telling you how to do this:

[https://duckduckgo.com/?q=change+username+ubuntu](https://duckduckgo.com/?q=change+username+ubuntu)

```
sudo usermod -l carbogen-chemist the-coder
```

---

### Post by sohail.connected on 2013-11-22
Sorry boss. Did searching but dint get anything satisfactory. But thanks for helping me out there. :)

---

### Post by simbauad on 2013-11-22
Ok sorry I didn't quite understand your question. Anyway, doing what mod said will solve your problem. And yes, it's compulsory that you do some research work before starting a thread. And another thing, any other problems you face should be started in a new thread. Please do not ask unrelated questions on an existing thread. Take a look here [http://ubuntuforums.org/showthread.php?t=1006656](http://ubuntuforums.org/showthread.php?t=1006656). Mark this thread as solved since your original question has been answered.

---

### Post by Bucky Ball on 2013-11-22
> **simbauad said:**
> Mark this thread as solved since your original question has been answered.

+1. If it you have Ubuntu installed and running, please mark as solved and post another thread for anything else. Good luck with it. ;)

---

