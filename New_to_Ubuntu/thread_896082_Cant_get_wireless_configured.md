---
title: "Cant get wireless configured"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by n0nc3ntz on 2008-08-20
Hello All,

I just installed Ubuntu on an old laptop of mine for the first time ever, ive heard good things. I am trying to get my wireless card to work, I have a Linksys WPC54G 

lspci: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller rev 02

My iwconfig output for wlan0 says I have a card that should be configured but when I go to System > Administration > Network I dont see any card for the wireless interface. I am using this guide:  [https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

I really dont know where to go from here but im sure this being the linux community can help a brotha out.

n0nc3ntz

---

### Post by caljohnsmith on 2008-08-20
First off, welcome to the forums. :)

Try this for you wireless card:
```
sudo modprobe -r bcm43xx b43 ssb ndiswrapper
sudo depmod -ae
sudo modprobe b43
iwconfig
```
Then check if your wireless interface shows up after doing the iwconfig command above. It should be wlan0, eth1, or similar. Use that below:
```
sudo ifconfig <interface> up
sudo iwlist scan
```
After doing the iwlist command, do you see any available networks?

---

### Post by n0nc3ntz on 2008-08-20
I put in 

sudo modprobe -r bcm43xx b43 ssb ndiswrapper
sudo depmod -ae

and i got FATAL: could not open /lib/modules/2.6.24-19-generic/modules.dep.temp for writing: Permission denied.

Now I know im not root but I have to have access to this file right ?? I mean i did install the thing

---

### Post by caljohnsmith on 2008-08-20
That's not a good sign you got that error. Do you get any other errors when you use "sudo" with other commands? Anyway, try doing the rest of those commands I gave after depmod, as depmod is not necessarily crucial at this point.

---

### Post by n0nc3ntz on 2008-08-20
Nevermind, I was able to run the commands...

When I run "sudo iwlist scan" it says my Network is down but when 

I try sudo ifconfig wlan0 up it says SIOCSIFFLAGS: No Such file or directory

---

### Post by caljohnsmith on 2008-08-20
OK, try doing:
```
sudo apt-get install b43-fwcutter
sudo ifconfig wlan0 up
sudo iwlist scan
```
If the above doesn't work, then:
```
sudo /etc/init.d/networking restart
sudo ifconfig wlan0 up
sudo iwlist scan
```

---

### Post by n0nc3ntz on 2008-08-20
I am not able to bring my wireless card up it seems. My permission has been denied. I do know about router IOS and from the looks of the prompt "sudo" temporarily lets me log into the root account or an admin of some sort. My prompt after sudo and password is

n0nc3ntz@n0nc3ntz-laptop:~$

I assume I would be in administration mode. Is there some thing im doing wrong here....
 
I keep getting SIOCSOFFLAGS: Permission denied 

trial by fire style right of the bat I suppose

---

### Post by Flyingjester on 2008-08-20
[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102) try this post

---

### Post by caljohnsmith on 2008-08-21
> **n0nc3ntz said:**
> I am not able to bring my wireless card up it seems. My permission has been denied. I do know about router IOS and from the looks of the prompt "sudo" temporarily lets me log into the root account or an admin of some sort. My prompt after sudo and password is

n0nc3ntz@n0nc3ntz-laptop:~$

I assume I would be in administration mode. Is there some thing im doing wrong here....
 
I keep getting SIOCSOFFLAGS: Permission denied 

trial by fire style right of the bat I suppose
"sudo" by itself does not log you in as root, it merely allows you to run a single command as root:
```
sudu <command>
```
To log in as root, you could do "sudo -i", but that is definitely not recommended for those new to Linux; you could then easily do alot of damage to your system if you are not careful. Can you copy/paste the exact output of the previous commands I gave?

---

