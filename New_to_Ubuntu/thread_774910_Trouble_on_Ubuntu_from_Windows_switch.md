---
title: "Trouble on Ubuntu from Windows switch"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by djteo on 2008-04-29
_

---

### Post by sdowney717 on 2008-04-29
well can you ping yahoo.com using the octet?
click applications - accessories, then select terminal

IF you can then it is a DNS server issue and then it is easy to fix.
scott@scott-desktop:~$ ping 66.94.234.13
PING 66.94.234.13 (66.94.234.13) 56(84) bytes of data.
64 bytes from 66.94.234.13: icmp_seq=1 ttl=54 time=90.0 ms
64 bytes from 66.94.234.13: icmp_seq=2 ttl=55 time=90.7 ms
64 bytes from 66.94.234.13: icmp_seq=3 ttl=54 time=90.2 ms

--- 66.94.234.13 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 90.000/90.327/90.741/0.308 ms
scott@scott-desktop:~$ 


scott@scott-desktop:~$ ping yahoo.com
PING yahoo.com (66.94.234.13) 56(84) bytes of data.
64 bytes from w2.rc.vip.scd.yahoo.com (66.94.234.13): icmp_seq=1 ttl=54 time=90.0 ms
64 bytes from w2.rc.vip.scd.yahoo.com (66.94.234.13): icmp_seq=2 ttl=54 time=89.7 ms
64 bytes from w2.rc.vip.scd.yahoo.com (66.94.234.13): icmp_seq=3 ttl=54 time=93.3 ms

--- yahoo.com ping statistics ---
4 packets transmitted, 3 received, 25% packet loss, time 3001ms
rtt min/avg/max/mdev = 89.744/91.069/93.380/1.676 ms
scott@scott-desktop:~$

---

### Post by djteo on 2008-04-30
Great! Now i can't even connect to the network...
What do you think the problem here might be? do you think i should connect via Lan after all?

---

### Post by Zalbor on 2008-04-30
> **djteo said:**
>  Although my router's network is visible by Ubuntu it just keeps asking me to give the right WEP key, even though i have already provided the right one for 10 times in a row with no luck at all. "Fine" i say no problem i remove the WEP key; Ubuntu connects just fine on the network...but (guess what is it this time??) !!No internet connection!!

About the wep key, make sure you're choosing the right type of WEP in the dialog. I had a similar problem at first when I got a laptop, and it was because I was choosing "wep passphrase" while I was using a "wep 128-bit hex key".

About the internet connection not working, it could be a number of things... DNS for example, are they set correctly?

---

### Post by djteo on 2008-04-30
Let me tell you..My router's default WEP key is 1234567890123 128-bit, Open.
Now as for the connection, i really didn't set up anything on Ubuntu, i was just trying to connect.. Do i have to use xISP tool or something?

---

### Post by geeree on 2008-04-30
> **djteo said:**
> I have the new Ubuntu 8.04 - Hardy Heron 64-bit installed inside Windows XP with 30Gb partitioned to it (Wubi style).

Linux is a "literate operating system," something that a person coming over from Windows does not realize. Thus you do not use Linux just "as is"---in fact Linux will almost never work as is on your computer---but learn how your computer works and how the Linux kernel works and then use various applications after understanding them. Linux is different from Windows in that it give you a chance to learn all this. See for example: [http://tldp.org/LDP/intro-linux/html/](http://tldp.org/LDP/intro-linux/html/). 

Hope this helps,
Girish.

---

### Post by Mogurijin on 2008-04-30
Your problems remind me of driver issues. The default wireless drivers in Ubuntu suck. I would recommend using ndiswrapper. You can follow [these]("http://ubuntuforums.org/showthread.php?t=760568") instructions, but instead of the driver used, use the driver off of you driver cd. Hopefully it will work better.

---

### Post by djteo on 2008-04-30
> **geeree said:**
> Linux is a "literate operating system," something that a person coming over from Windows does not realize. Thus you do not use Linux just "as is"---in fact Linux will almost never work as is on your computer---but learn how your computer works and how the Linux kernel works and then use various applications after understanding them. Linux is different from Windows in that it give you a chance to learn all this. See for example: [http://tldp.org/LDP/intro-linux/html/](http://tldp.org/LDP/intro-linux/html/). 

Hope this helps,
Girish.

I would really like to learn linux.I 've been working in windows for 12 years now i feel like i m home inside windows, linux seems hostile to me for now (because i m not used to it). That's why i installed linux inside windows, to feel more secure knowing that i can use windows anytime i can. I wish one day i can say that about linux.I wish i ll see linux as my familiar OS later on. thanks for the guide.

Furthermore i cant understand how LILO or GRUB work and are being configured..

---

### Post by billgoldberg on 2008-04-30
Yes, wireless connection is one of ubuntu's weak points (lack of good drivers, actually not ubuntu's fault, but that's besides the point).

Ndiswrapper should sort your problems out.

But on fiesty (old ubuntu release) I had the same problem.

Ubuntu could see the network but wouln't accept my wep key.

Instead of the "network manager" I use WICD (or wcid, can't remember). I downloaded it, removed network manager and use wicd to connect to my wireless network. It might be worth a try. (keep the ubuntu cd by hand to reinstall network manager should wicd don't work)

---

### Post by Stefanie on 2008-04-30
i had more or less the same problem on my gutsy installation (not wubi but a full install). I typed the correct network key 10 times in a row, but without succes. 
in the end i tried "connect to other wireless network" (you'll see this option when you click on the icon in the taskbar). you can type the name of your network and for the network key there are more options (i think WPA2 personal worked for me). i think i still had to try a few times, but in the end it connected and i've never had any problems ever since...
i don't know if this works on a wubi hardy installation, though.

---

### Post by Jeffrey Tooker on 2008-04-30
> **djteo said:**
> I would really like to learn linux.I 've been working in windows for 12 years now i feel like i m home inside windows, linux seems hostile to me for now (because i m not used to it). That's why i installed linux inside windows, to feel more secure knowing that i can use windows anytime i can. I wish one day i can say that about linux.I wish i ll see linux as my familiar OS later on. thanks for the guide.

Furthermore i cant understand how LILO or GRUB work and are being configured..

I have had some of the same frustrations as you have and I am just starting in Ubuntu (Gutsy). After banging my head against Gutsy for about a week I came to the conclusion that Windows is related to Ubuntu about the same way English is related to Arabic.  Windows and Ubuntu are both languages in a real sense.  Their structure and syntax are different.  Thinking that Ubuntu is made to act like Windows for me does not work. For every similarity there is a dissimalarity.  I am thinking of learning Ubuntu in the same manner I would learn Arabic.  That is start out from the absolute basics.  The parallels will surface in time on their own.  There are certain terms and operations that are common to both Operating Systems.


 I found a tutorial in the first sticky on this list: 

[http://ubuntuforums.org/showthread.php?t=500020](http://ubuntuforums.org/showthread.php?t=500020) 

It concerns itself with "Loading"  It starts out with the most basic of Command Line.  I have printed out the tutorial and all of the references and put them in a binder.  Then when I open Ubuntu (I have a dual boot machine), I can follow the tutorial.  I have taken a red pencil and highlighted the most important phrases.  This will allow me to refer back to the folder in times of need.

From all I have talked to the "Command Line" is the lifes blood of Ubuntu.  I am working my way through Command Line.  It is a new language.  It shows the unity of structure of Linux.  Every thing starts from /.  I feel that learning the absolute basics first will make for a more friendly relationship witth the OS.

Jeffrey Tooker
Paynes Ck. Ca.

---

### Post by Lori700698 on 2008-04-30
It was the stupid driver giving me issues!RTL8187B  I had to upload the driver to a disk (windows 98 driver) then get it to my desk top, then make it a zip/archive to get it to move to a folder that I created for it.  The key was the driver showed up, but it wasn't working.  I found that if you right click applications and go to edit menus/administration and there is an option for windows drivers, I got it open and sure enough the driver showed, but didn't work so I had to set it to the new .inf driver (windows 98) that I just put in my files.  I gathered directions from all over the place to figure this out.  If you need help let me know and I will sit down and re-map it out for you.

---

### Post by Tatty on 2008-04-30
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

Try this as a good wifi troubleshooting guide.

Windows has a massive advantage over linux when it comes to hardware compatibility for one reason:  Pretty much all hardware is extensively tested by the manufacturers to make sure it works seamlessly with windows.  The Linux community has to make *almost* all possible hardware work with linux with little or no help from the manufacturers.  
Its an ongoing uphill struggle for the time being.  But the vast majority of the time you can get all the hardware to work, with a bit of fiddling.

---

### Post by Mogurijin on 2008-05-01
I have found little in the ways of wireless adapters that the ndiswrapper can't solve. However, I haven't tried to many =/

---

