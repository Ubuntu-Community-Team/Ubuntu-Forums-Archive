---
title: "can flash run on 64-bit systems"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by boner454 on 2008-07-20
i want to use adobe flash player but when i went to install it said it does not work on 64 bit
```
dan@dan-laptop:~$ cd /home/dan/Desktop/install_flash_player_9_linux 
dan@dan-laptop:~/Desktop/install_flash_player_9_linux$ ./flashplayer-installer

ERROR: Your architecture, \'x86_64\', is not supported by the
       Adobe Flash Player installer.

```
 how can i get it to work or get another version that will work

---

### Post by silkstone on 2008-07-20
Take a look at this tutorial...

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Scroll down to the section headed 'Troubleshooting - Adobe Flash Player' and there are detailed instructions for installing Flash 9 or Flash 10 on 32-bit and 64-bit Hardy.

Hope that helps - it's a long tutorial and you only need that bit, but the rest is worth looking at.

---

### Post by drs305 on 2008-07-20
This is another good link on how to set up flash. The thread is huge but you only need to accomplish the steps in the very first section:
[Flash 9 install script for AMD64 (nspluginwrapper)]("http://ubuntuforums.org/showthread.php?t=772490")

---

### Post by tjwoosta on 2008-07-20
i have heard alot of crap nonsense about flash and java on 64bit machines here on the beginner forums but **its simply not true**


i have three seperate machines running ubuntu 64bit and with every one of them flash and java just straight up worked no problems

this is how i install flash
(first remove old flash)
then
```
sudo apt-get install flashplugin-nonfree
```

also  install ubuntu restricted extras
```
sudo apt-get install ubuntu-restricted-extras
```

then add medibuntu repository to install w64codecs  (dont know if its needed for flash but it wont hurt)
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

after adding the repository do this

```
sudo apt-get install w64codecs
``` (thats w32codecs if you have a 32bit ubuntu)

and i never had to install java it just worked out of the box  

(or maybe it came from the restricted extras... i dunno but i have it and it works fine)

---

### Post by steveneddy on 2008-07-20
> **tjwoosta said:**
> i have heard alot of crap nonsense about flash and java on 64bit machines here on the beginner forums but **its simply not true**


i have three seperate machines running ubuntu 64bit and with every one of them flash and java just straight up worked no problems

this is how i install flash
(first remove old flash)
then
```
sudo apt-get install flashplugin-nonfree
```

also  install ubuntu restricted extras
```
sudo apt-get install ubuntu-restricted-extras
```

then add medibuntu repository to install w64codecs  (dont know if its needed for flash but it wont hurt)
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

after adding the repository do this

```
sudo apt-get install w64codecs
``` (thats w32codecs if you have a 32bit ubuntu)

and i never had to install java it just worked out of the box  

(or maybe it came from the restricted extras... i dunno but i have it and it works fine)

Perfectly said.

Flash 10 is in the repos.

---

### Post by barney385 on 2008-07-20
> **tjwoosta said:**
> i have heard alot of crap nonsense about flash and java on 64bit machines here on the beginner forums but **its simply not true**


i have three seperate machines running ubuntu 64bit and with every one of them flash and java just straight up worked no problems

this is how i install flash
(first remove old flash)
then
```
sudo apt-get install flashplugin-nonfree
```also  install ubuntu restricted extras
```
sudo apt-get install ubuntu-restricted-extras
```then add medibuntu repository to install w64codecs  (dont know if its needed for flash but it wont hurt)
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

after adding the repository do this

```
sudo apt-get install w64codecs
``` (thats w32codecs if you have a 32bit ubuntu)

and i never had to install java it just worked out of the box  

(or maybe it came from the restricted extras... i dunno but i have it and it works fine)

Yep, this worked for me OP.

---

### Post by gandaran on 2008-07-20
> i have heard allot of crap nonsense about flash and java on 64bit machines here on the beginner forums but its simply not true

I agree

> and i never had to install java it just worked out of the box

java comes with the ubuntu-restricted-extras package and so does adobe flash 9, no need to run the flash install command, the only problem with the ubuntu-restricted- extras is that it install open-java, maybe it's okay for you, but sun-java6 is a whole lot better.


> steveneddy
Flash 10 is in the repos

it is but only if the proposed and backports are enabled (not recommended)

edit:
sorry, I just remember now there's no 64-bit sun-java6-plugin! I'm a 32-bit user.

---

### Post by arpanaut on 2008-07-20
Near the bottom of this page: [http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)

there is instruction for installing Flash 10 Beta.
I just installed Hardy-64 on my laptop and this worked extreemly well and I think that it works better than Flash-9 on my regular Hardy system, (10 is going on going on "old reliable" later tonight) Honestly Flash 9 on Hardy is about my only with this release.

---

