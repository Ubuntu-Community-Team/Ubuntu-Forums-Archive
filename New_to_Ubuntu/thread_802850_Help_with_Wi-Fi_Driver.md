---
title: "Help with Wi-Fi Driver"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by ocampod on 2008-05-21
[FONT="Arial"]Hello,

I am an Ubuntu noob and I just installed Ubuntu on my laptop but I cannot get the wifi connection to work. I read somewhere that I have to use Disk Wrapper with my Windows wireless wi-fi driver. Here is my problem:

I cannot seem to find the wireless driver on the Toshiba website and I don't know how to exactly use Disk Wrapper. I have a Toshiba Satellite P205-S6307. Any help would surely be appreciated :).

Dave O[/FONT]

---

### Post by superprash2003 on 2008-05-21
first look at system->administration->restriced drivers and see if you can enable any WLAN drivers .. also post your iwconfig output

---

### Post by ocampod on 2008-05-21
superprash,

I'm sorry for sounding like such a noob, but where would I go about getting the iwconfig output?

---

### Post by amingv on 2008-05-21
By Disk Wrapper I guess you mean Ndiswrapper, if so it's fairly easy to install with it.

First, here is your driver (I got it from the Toshiba webpage after all, have care to look closely next time):
[http://files.filefront.com/driver+wifi+intel+v1110argz/;10294769;/fileinfo.html](http://files.filefront.com/driver+wifi+intel+v1110argz/;10294769;/fileinfo.html)

Now unpack it, open up a terminal and follow these instructions, for now we'll assume you unpacked in /home/user/driver:

```
cd /home/user/driver
sudo modprobe -r ndiswrapper
ndiswrapper -i NETw4v32.INF
```

You should see something like this:
```
installing netw4v32 ...
```
Now:
```
ndiswrapper -l
```
should show:
```
netw4v32 : driver installed
        device (XXXX:XXXX) present
```
Finally, do:
```
sudo ndiswrapper -m
sudo modprobe ndiswrapper
```

And you should be good to go.

---

### Post by superprash2003 on 2008-05-22
if the above worked then cool.. you could post your iwconfig output by going to the terminal(applications->accessories->terminal) and then type iwconfig and copy paste it here

---

### Post by daniel000 on 2008-05-22
hi everyone i have the same prob, cant get the wifi light on when using ubuntu

i typed iwconfig into the the terminal an this is what i got

lo

eth 

both had no wireless conections

---

