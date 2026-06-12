---
title: "wireless switch turned off, wont respond to touch."
date: 2012-03-03
forum: New to Ubuntu
---

### Post by Jake5 on 2012-03-03
Hey, just installed a dual boot of lubuntu and ubuntu, I can't connect to my WiFi router because my wireless hardware switch is unresponsive. I am looking for a command that will turn the switch on from the cli, any help would be greatly appreciated. Thanks!

---

### Post by Jake5 on 2012-03-03
So this was not an issue in ubuntu as it has a dropdown menu with an enable wireless option, it worked every time until just now when I went to reply to a similar new thread with instructions. Now the enable WiFi button doesn't work, its not selectable.

---

### Post by Jake5 on 2012-03-03
So I am looking for a command to change the status from Disabled to Enabled, see attached.
Any help would be greatly appreciated.

---

### Post by Lokireloaded on 2012-03-03
[http://ubuntuforums.org/showthread.php?t=1424046]("http://ubuntuforums.org/showthread.php?t=1424046")

I'm not sure if it works for lubuntu. But it may get you there.

---

### Post by MG&amp;TL on 2012-03-03
Okay, output of:

```
sudo ifconfig <interface> up
``` please. :)

If you are using wireless, <interface> is usually wlan0.

---

### Post by Jake5 on 2012-03-03
> **MG&TL said:**
> Okay, output of:

```
sudo ifconfig <interface> up
``` please. :)

If you are using wireless, <interface> is usually wlan0.

Yep, Tried that, getting this weird rf-kill response

---

### Post by audiomick on 2012-03-03
Jake, if you want to post output from your terminal, you can use shift+ctrl+c in the terminal to copy.

Paste it here between code tags, the # button at the top of the post window.

I find that easier than making a screenshot and attaching that.

---

### Post by Jake5 on 2012-03-03
sorry, hope this helps,

```
Compaq-Presario-CQ60-Notebook-PC:~$ sudo ifconfig wlan0 up
[sudo] password for jake5: 
SIOCSIFFLAGS: Operation not possible due to RF-kil
```

---

### Post by kevdog on 2012-03-03
hmm
how about 
sudo rfkill unblock wifi

---

### Post by ts3 on 2012-03-03
My hardware switch acts up sometimes (e.g. I have disabled the wireless through the switch, then forget and reboot with the switch off, then just pressing the button won't turn the wireless on for some reason).  I run 

```
rfkill list all
sudo rfkill unblock all
```

If this doesn't work the first time (i.e. wireless is still off and running rfkill list all still shows a hardware block) I have to press the switch again (toggle is the word for this methinks) and then run sudo rfkill unblock all again.  

No idea if this is your issue but it works for my set-up on an hp laptop.

---

### Post by Jake5 on 2012-03-03
It returns:
```
sudo: rfkill: command not found
```
Even when I use RF-kill.

---

### Post by Jake5 on 2012-03-03
Thanks for all of your help guys, couldn't have done it without your advice, got it up and running, had to run the commands a few times before it worked, but I am typing this in Lubuntu right now with a working wireless connection. Heres the code if interested:
```
jake5@jake5-Compaq-Presario-CQ60-Notebook-PC:~$ man rfkill
No manual entry for rfkill
jake5@jake5-Compaq-Presario-CQ60-Notebook-PC:~$ sudo rfkill unblock wlan0
[sudo] password for jake5: 
sudo: rfkill: command not found
jake5@jake5-Compaq-Presario-CQ60-Notebook-PC:~$ sudo RF-kill bunblock wlan0
sudo: RF-kill: command not found
jake5@jake5-Compaq-Presario-CQ60-Notebook-PC:~$ rfkill list all
The program 'rfkill' is currently not installed.  You can install it by typing:
sudo apt-get install rfkill
jake5@jake5-Compaq-Presario-CQ60-Notebook-PC:~$ sudo apt-get install rfkill
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  rfkill
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 7,806 B of archives.
After this operation, 65.5 kB of additional disk space will be used.
Err http://us.archive.ubuntu.com/ubuntu/ oneiric/main rfkill i386 0.4-1
  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/r/rfkill/rfkill_0.4-1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
jake5@jake5-Compaq-Presario-CQ60-Notebook-PC:~$ sudo rfkill unblock wlan0
sudo: rfkill: command not found
jake5@jake5-Compaq-Presario-CQ60-Notebook-PC:~$ sudo apt-get remove rfkill
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package rfkill is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jake5@jake5-Compaq-Presario-CQ60-Notebook-PC:~$ sudo apt-get install rfkill
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  rfkill
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 7,806 B of archives.
After this operation, 65.5 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ oneiric/main rfkill i386 0.4-1 [7,806 B]
Fetched 7,806 B in 0s (17.9 kB/s)
Selecting previously deselected package rfkill.
(Reading database ... 130095 files and directories currently installed.)
Unpacking rfkill (from .../archives/rfkill_0.4-1_i386.deb) ...
Processing triggers for man-db ...
Setting up rfkill (0.4-1) ...
jake5@jake5-Compaq-Presario-CQ60-Notebook-PC:~$ ifconfig wlan0 up
SIOCSIFFLAGS: Permission denied
jake5@jake5-Compaq-Presario-CQ60-Notebook-PC:~$ sudo ifconfig wlan0 up
SIOCSIFFLAGS: Operation not possible due to RF-kill
jake5@jake5-Compaq-Presario-CQ60-Notebook-PC:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: hp-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
jake5@jake5-Compaq-Presario-CQ60-Notebook-PC:~$ sudo rfkill unblock all
jake5@jake5-Compaq-Presario-CQ60-Notebook-PC:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hp-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes
jake5@jake5-Compaq-Presario-CQ60-Notebook-PC:~$ sudo rfkill unblock all
jake5@jake5-Compaq-Presario-CQ60-Notebook-PC:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hp-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes
jake5@jake5-Compaq-Presario-CQ60-Notebook-PC:~$ ifconfig wlan0 up
SIOCSIFFLAGS: Permission denied
jake5@jake5-Compaq-Presario-CQ60-Notebook-PC:~$ sudo ifconfig wlan0 up
jake5@jake5-Compaq-Presario-CQ60-Notebook-PC:~$ ^C
jake5@jake5-Compaq-Presario-CQ60-Notebook-PC:~$ sudo ifconfig wlan0 up
jake5@jake5-Compaq-Presario-CQ60-Notebook-PC:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hp-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
jake5@jake5-Compaq-Presario-CQ60-Notebook-PC:~$ rfkill unblock all
jake5@jake5-Compaq-Presario-CQ60-Notebook-PC:~$ sudo if config wlan0 up
sudo: if: command not found
jake5@jake5-Compaq-Presario-CQ60-Notebook-PC:~$ sudo ifconfig wlan0 up

```

---

