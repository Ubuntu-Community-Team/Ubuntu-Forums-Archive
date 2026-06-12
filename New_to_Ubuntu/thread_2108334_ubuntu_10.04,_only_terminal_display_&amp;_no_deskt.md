---
title: "ubuntu 10.04, only terminal display &amp; no desktop"
date: 2013-01-24
forum: New to Ubuntu
---

### Post by deepikarc on 2013-01-24
Hello, I am Deepika, I am new to this forum, About 2 hrs. ago I faced a major problem : after login, only the terminal was appearing and no desktop. This problem occurred after following the 3 commands to sync iphone to the rhythmbox :

sudo add-apt-repository ppa:pmcenery/ppa
sudo apt-get update
sudo apt-get dist-upgrade

After doing the above I restarted & then only terminal was appearing and no desktop. I have uninstalled libimobiledevice package but still no change. If anyone has any solutions to this problem please let me know. Thanks.

---

### Post by mikewhatever on 2013-01-24
You may want to try the recovery mode. Once there, install ppa-purge with

apt-get install ppa-purge

then run

ppa-purge ppa:pmcenery/ppa

That should remove the ppa and every package from it.

---

### Post by deepikarc on 2013-01-24
Tried the command but it says :

E: Couldn't find package ppa-purge

---

### Post by mikewhatever on 2013-01-24
Too bad. I guess ppa-purge is not available for Lucid. :(

---

### Post by deepikarc on 2013-01-24
Hi again, I removed the ppa:pmcenery from /etc/apt/sources.list.d/ and also removed the ppa gpg key using : [FONT=&quot]sudo apt-key del id. Now to some extent I am sure that I have removed the ppa repository. 

After that I did the following 
sudo apt-get update but it says it fails to fetch few files. e.g : could not resolve: security.ubuntu.com, could not resolve : archive.canonical.com, could not resolve dl.google.com
 
Then i run the command : sudo apt-get dist upgrade and it says 0 upgraded,0 newlly installed, 0 to remove and 0 not upgraded. Then i run the command : sudo apt-get install ubuntu-desktop and it says, could not resolve : in.archive.ubuntu.com, security.ubuntu.com 

And then also tried : sudo aptitude install gnome, but still no luck.

Please reply asap.
[/FONT]

---

### Post by Adam_GUI on 2013-01-24
Are you connected by ethernet?  Do you get anything interesting from ifconfig or trying to ping anything on the outside?

---

### Post by deepikarc on 2013-01-24
I have the wi-fi.

---

### Post by deepikarc on 2013-01-24
Ok, i am in huge problem, first my desktop is not there and only terminal and secondly i am having problems with internet. I have do everything using the terminal. Thus first i need to fix the wifi prob and den the desktop problem. can u suggest a way to install wifi using terminal?

---

### Post by Adam_GUI on 2013-01-24
My sane reccomendation is to boot from live media, backup your files, and reinstall.  Maybe not what you want to hear for 10.04.  But, it's the least time-consuming way.

But, if you're up for crazy...  You can try to dpkg-reconfigure everything in your apt cache.

cd /var/cache/apt/archives/
sudo apt-get dpkg-reconfigure *.deb

That may stall out with errors and or take an eternity.

---

### Post by squakie on 2013-01-24
> **deepikarc said:**
> Ok, i am in huge problem, first my desktop is not there and only terminal and secondly i am having problems with internet. I have do everything using the terminal. Thus first i need to fix the wifi prob and den the desktop problem. can u suggest a way to install wifi using terminal?
Jeez - I screwed up royally, so I've deleted what I originally had here.  Sorry!

Could you post back the output of:

lspci

lshw | grep VGA

---

### Post by deepikarc on 2013-01-27
Hi everyone, 

Wanted to say that I got my Desktop back. Really relieved. These r the steps followed :

1)First,connected my laptop to the internet device with ethernet cable. Then type :
```
ifconfig
```

and you'll see that eth0 is functioning. How did I get to know that -- RX packets and TX packets were giving NON ZERO numbers, and giving IP addresses. This was a signal to--wired internet connection is available.
 
2)Now to enable the internet, I had to open a file and do some changes. So this is what I did:

```
sudo gedit/etc/network/interfaces
```

Then in that file, added the following lines : 
```
auto eth0
iface eth0 inet dhcp.
```

Then run :
```
sudo /etc/init.d/networking restart
```

Then to see if internet was working fine or not. I typed 
```
~$ firefox
```
After that webpage opened and the internet was working fine. I was so happy at this moment, but still had to solve the real problem of fixing my Desktop.

3)Then executed the following commands :

```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install ubuntu-desktop
sudo apt-get install --reinstall ubuntu-desktop
```

Then came out of the terminal, and logged in again and WALA --- My DESKTOP was BACK. I was just toooo happy at this moment. 

4) Now the next thing that I wanted to fix was the wifi (wireless internet connection). So for that first of all, detached the ethernet cable.
Then opened a file, by typing :
```
sudo gedit/etc/network/interfaces
```
And deleted the previous 2 lines that I added
```
auto eth0
iface eth0 inet dhcp
```

Made sure that only these 2 lines r present :
```
auto lo
iface lo inet loopback
```

and then restarted the network manager by typing: 
```
sudo service network-manager restart
``` 

And then, the symbol of wifi was coming on the panel.Clicked on the wifi connection that I wanted, and that was it. Even my wifi was now working. 

So everything is back to normal. But during this trouble I learned a lot. And am really thankful to the Ubuntu and Linux Forums to be there, without w/c I couldn't have solve the problem at all. All the above commands and procedures, I got it from the forums, through different threads posting their problems. Internet is just amazing, makes the world come to one place and share their ideas and is a great help. 

Also thanks to ADAM_GUI, who popped 'the most important question' in my mind : whether my internet is working or not. And then later I realized becoz my net wasn't working, none of the commands of updating/installing/upgrading were working. So I understood the first thing I had to do was to fix the internet, and only after that I could install/update/upgrade the system to get the Desktop back. So thanks a lot.

---

