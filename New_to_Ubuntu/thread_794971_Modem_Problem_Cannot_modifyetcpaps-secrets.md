---
title: "Modem Problem: Cannot modify/etc/paps-secrets"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by Sealbhach on 2008-05-15
Hi,
I'm dialing up using Gnome-PPP from a USB Huawei E220 wireless modem. It has worked on Linux before but I did a fresh install and I'm getting this error (from the connection log in Gnome-PPP):

[B]cannot modify /etc/paps-secret
(some conment about flaky Password)

cannot modify /etc/chap-secret
(some conment about flaky Handshake)[/B]

I brought the readout to work with me on a thumb drive but this work-PC can't read it (so this is the gist of the problem).

Has it got anything to do with the ISP or is it something to do with User Access Control being set by Network Manager in Ubuntu?

Have had some "unable to resolve host" problems but I think they're sorted now.



.

---

### Post by Sealbhach on 2008-05-15
Please,
I'm desperate to get my modem working, I have no internet connection.

I suspect it's a simple matter of passwords.

The passwords from the ISP are:

```
Username:
Password:
```

Both are blank.


.

---

### Post by linuxonbute on 2008-05-15
> **Sealbhach said:**
> Please,
I'm desperate to get my modem working, I have no internet connection.

I suspect it's a simple matter of passwords.

The passwords from the ISP are:

```
Username:
Password:
```

Both are blank.


.

Well if you know the user name and password I suspect that you can edit the file as the root user:
sudo vim /etc/pap-secrets

---

### Post by Sealbhach on 2008-05-15
> **linuxonbute said:**
> Well if you know the user name and password I suspect that you can edit the file as the root user:
sudo vim /etc/pap-secrets


Thanks, but I don't know how to do that- what to put there, I mean.

First of all, I'm trying to establish if it's the ISP refusing me access or User Account Control in Ubuntu that's stopping me.

.

---

### Post by plucky on 2008-05-15
Sealbhach

The way to edit those files are to use **pppconfig** or **wvdial.conf**.The files are actually in **/etc/ppp/pap-secrets** and **/etc/ppp/chap-secrets**.


To edit the files open a terminal ```
sudo pppconfig
``` and a window will open.Input the correct data for your modem.


See [here](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer?highlight=(howto)|(modem)) for further information.


Good Luck

---

### Post by linuxonbute on 2008-05-15
> **Sealbhach said:**
> Thanks, but I don't know how to do that- what to put there, I mean.

First of all, I'm trying to establish if it's the ISP refusing me access or User Account Control in Ubuntu that's stopping me.

.

Your ISP should have given you the user name and password.
If you just got a windows install disc then you should just ring them and ask for the name and password although, in my experience you get a letter from them and it says in it what they are.

---

### Post by Sealbhach on 2008-05-15
I didn't get no letter. I bought a modem that loads its own drivers.

This is the Dialup.ini file from the folders it installed in Vista:

```
[Profiles]
Default=3 USB Modem(Default)
[3 USB Modem(Default)]
Apn=3internet
IP=0
IP Dynamic=0
Number=*99#
User=
Password=
Authentication protocol=0
Dns Dynamic=0
Wins Dynamic=0
```

The username and password are supposed to be blank.

I think I'll try Vodafone, I asked three.co.uk to send me the settings I need for Linux but I got no reply. I'm fed up with them and their crappy modem that's really too slow anyway.

/rant

.

.

---

### Post by spiderbatdad on 2008-05-15
my uderstanding is gnome-ppp uses wvdial. From your terminal run ```
sudo wvdialconf
gksu gedit /etc/wvdial.conf
``` input your username and password, then save the file. Try launching wvidal from the terminal before using gnome-ppp: ```
sudo wvdial
```

---

### Post by Sealbhach on 2008-05-16
I think it's a bug. [Bug # 121487]("https://bugs.launchpad.net/ubuntu/+source/gnome-ppp/+bug/121487").

This readout from that bug report is exactly what I'm getting too:

```
WvDial Modem<*1>: CONNECT
WvDial<*1>: Carrier detected. Waiting for prompt.
WvDial<Notice>: Don't know what to do! Starting pppd and hoping for the best.
WvDial<Notice>: Starting pppd at Tue Oct 2 03:07:50 2007
[B]WvDial<Err>: Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
WvDial<Err>: --> PAP (Password Authentication Protocol) may be flaky.
WvDial<Err>: Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
WvDial<Err>: --> CHAP (Challenge Handshake) may be flaky.[/B]
WvDial<Notice>: Pid of pppd: 8884
WvDial<*1>: Using interface ppp0
```

As far as I know, it's not the ISP that's looking for a password, it's that bloody User Account Control thing in Ubuntu (which I don't bloody well need and want to disable completely).

Can someone help me to get Gnome-PPP to be able to modify these files?




.

---

### Post by Sealbhach on 2008-05-22
Well, I've got connected now. 

I think I didn't have Stupid Mode on, I think that's what caused it.

Even though I have a working connection now, when I look at the log in Gnome-PPP it still shows that Flaky Paps message, so it's not a showstopper.

Thanks everyone for their help and encouragement.


.

---

### Post by nowshining on 2008-05-22
i've always ignored those aand all worked fine dialing into my isp.

---

