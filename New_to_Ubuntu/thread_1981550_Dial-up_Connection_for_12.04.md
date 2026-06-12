---
title: "Dial-up Connection for 12.04"
date: 2012-05-17
forum: New to Ubuntu
---

### Post by RGF183 on 2012-05-17
[SIZE=2]No Internet connection Ubuntu 12.04

In Windows when setting up a dial-up internet connection there is a dilog box for entering my ISP phone number.  I can find no such thing in Ubuntu.  Can you please help?

I have trolled through many posts concerning the inability to access Internet but none mention this specific problem.

I have had my hard drive upgraded and had Ubuntu downloaded into partition E, Windows is in C: and obviously I have to re-boot.  So please keep answers simply as poss with little techogobble.[/SIZE]:wink:

---

### Post by Face-Ache on 2012-05-17
Do you have **any** internet connection in Ubuntu 12.04?

If so, you could try KPPP, installed via the Ubuntu Software Centre - *KPPP is a modem dialer for connecting to a dial-up Internet Service Provider. It displays statistics and accounting information to help users keep track of connection costs.*

How's Auckland today? Weather as bad as Hamilton?  :)

---

### Post by Irihapeti on 2012-05-17
Disclaimer: it's been a few years now since I ran dialup.

There's also Gnome-PPP, which does the same job but doesn't install all the KDE libraries.

If you are really stuck and can't download anything, there's pppconfig already installed. You need to open a terminal for this and type "sudo pppconfig", then follow the instructions.



Face-Ache: I don't know what the weather is like in Hamilton today, but in Auckland it's patchy - sort of fine and then pouring with rain. 16 degrees C it says in my weather applet.

---

### Post by Face-Ache on 2012-05-17
Irihapeti's suggestion is probably your best option at this stage RGF183; saves trying to download and install anything new.

Irihapeti; yeah same in Hamilton, but more rain than fine periods! :)

---

### Post by RGF183 on 2012-05-18
> **Face-Ache said:**
> Do you have **any** internet connection in Ubuntu 12.04?

If so, you could try KPPP, installed via the Ubuntu Software Centre - *KPPP is a modem dialer for connecting to a dial-up Internet Service Provider. It displays statistics and accounting information to help users keep track of connection costs.*

How's Auckland today? Weather as bad as Hamilton?  :)
Hi Face-Ache

I am still trying to get my head around how these forums work, having been computing since 1989 (in Oz) Tried one there once - a science forum - and all people did was slag off each other.  Really pleased Ubuntu community is helpful.

Answer is no, have attempted using e-mail problem.  So I have to access this site using damn MS.

Sun shining now (Sat noon)

Cheers
Roger

---

### Post by barrykgerdes on 2012-05-18
Sounds a bit like my problem with 12.04. no wireless card,  no install, would not even find a LAN connection.

Barry

---

### Post by Face-Ache on 2012-05-18
> **RGF183 said:**
> Hi Face-Ache

I am still trying to get my head around how these forums work, having been computing since 1989 (in Oz) Tried one there once - a science forum - and all people did was slag off each other.  Really pleased Ubuntu community is helpful.

Answer is no, have attempted using e-mail problem.  So I have to access this site using damn MS.

Sun shining now (Sat noon)

Cheers
Roger

Okay, give Irihapeti's solution a try using pppconfig. In a terminal, enter;
```
sudo pppconfig
```

And then go through the steps - i'd try and talk you through it some more, but i don't personally have dial-up connection!

---

### Post by lkraemer on 2012-05-19
RGF183,
You will need to set up the pap-secrets and/or chap-secrets file by running the following in a Terminal Window:
```

sudo pppconfig

```
You will need your userlogin, password, ISP provider information, and
pap or chap information for the connection. (You can set up pap and
then chap, if pap doesn't work.) Basically you just answer the questions
that are presented. You can delete configurations and start over if
you need to from the menu selections.

For more information, within *nix try:
```

man pppd
man pppconfig

```
pap-secrets file contains:
(NOTE: File Format for 10.04)
```

# Every regular user can use PPP and has to use passwords from /etc/passwd
*       hostname        ""      *

# UserIDs that cannot use PPP at all. Check your /etc/passwd and add any
# other accounts that should not be able to use pppd!
guest   hostname        "*"     -
master  hostname        "*"     -
root    hostname        "*"     -
support hostname        "*"     -
stats   hostname        "*"     -

# OUTBOUND connections

# Here you should add your userid password to connect to your providers via
# PAP. The * means that the password is to be used for ANY host you connect
# to. Thus you do not have to worry about the foreign machine name. Just
# replace password with your password.
# If you have different providers with different passwords then you better
# remove the following line.
#       *       password
"yourusername@yourisp.net" provider "yourpassword"

```
ASSUME:
your loging name is GeraldJones
your password is MyPassWord

Your last section of the pap-secrets file should be:
```

# OUTBOUND connections

# Here you should add your userid password to connect to your providers via
# PAP. The * means that the password is to be used for ANY host you connect
# to. Thus you do not have to worry about the foreign machine name. Just
# replace password with your password.
# If you have different providers with different passwords then you better
# remove the following line.

#	*	password
"GeraldJones" provider "MyPassWord"

```
If you named provider something different, then just substitute that for the provider in pon and poff.
Let's assume showmenet

Original ISP named provider
To connect use the first command. To Disconnect use the second command.
```

pon provider
poff provider

```
Modified ISP named showmenet
```

pon showmenet
poff showmenet

```
This should get you connected. You then need to open your Browser, and make sure OFFLINE is not checked.  It is in the Top Left selection under
FILE:

You should be able to browse, and surf. Now download and setup wvdial or disconnect.

**DOWNLOAD & install wvdial if isn't installed:**
Install wdvial so you can use it to locate the Modem. You will have
to configure wvdial. Those details are later in this posting......
If you insert your *nix LiveCD you can select the CDR from the Repo's menu
and  install wvdial from the LiveCD.


Now that ppp is setup, you will need to set up wvdial. Power up the modem,
and connect it to your serial port.  In a Terminal window do:
```

sudo wvdialconf /etc/wvdial.conf

```
You should get a configuration file like this at
/etc/wvdial.conf (you may need to add/change a few things...)

wvdial.conf contains:
```

[Dialer Defaults]
Auto DNS = yes
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Baud = 48800
New PPPD = yes
Stupid mode = yes
;carrier check = no
Modem = /dev/ttyACM0
ISDN = 0
Phone = 4460568
Password = yourpassword
Username = yourusername@yourisp.net

```


Now assuming that your pap-secrets and or your chap-secrets file is
correct you should be able to use wvdial to dial the connection with:
```

wvdial /etc/wvdial.conf

```



DIALOUT GROUP:
You need to be a member of "dialout". You can use this command in a Terminal Window to see if you are already a member.
```

groups

```
My results were:
> 
larry@debian:~$ groups
larry dialout cdrom floppy sudo audio dip video plugdev netdev bluetooth scanner vboxusers
larry@debian:~$

I can add my loginname with:
```

useradd –G dialout loginname

```

Now go back and try wvdial. It should now work.
Now assuming that your pap-secrets and or your chap-secrets file is
correct you should be able to use wvdial to dial the connection with:
```

wvdial /etc/wvdial.conf

```
You should hear the modem go OFFHOOK with dialtone, Dial, and connect.
REMEMBER after wvdial dials, you can pick up a handset and monitor the
activity by listening to what is going on with the communications.
If your config file is correct you should authenticate and then control
will be passed to ppp. You will see several strings of HEX (funny characters)
and then you should stay connected. (you will use CNTL C to
terminate the session when you are done, but for this session you MUST
leave the Terminal window OPEN...) You may have to uncheck the box
marked OFFLINE when you open your browser to make it online. Surf,
then terminate the open session with CNTL C in the open terminal window
where you initiated wvdial.

Now that it works set up Gnome-PPP. From now on, you can just click on Gnome-PPP and run it from the GUI.

[http://ubuntuforums.org/showthread.php?t=1720726](http://ubuntuforums.org/showthread.php?t=1720726)
[http://ubuntuforums.org/showthread.php?t=1614599](http://ubuntuforums.org/showthread.php?t=1614599)
[http://ubuntuforums.org/showthread.php?t=1979936](http://ubuntuforums.org/showthread.php?t=1979936)



lk

---

### Post by RGF183 on 2012-05-23
Hi Ikraemer

Thanks a lot for detailed reply.  A bit over my head but I have the a Ubuntu library book which I should get next week so I will have a go then. 

Roger

---

### Post by MadmanRB on 2012-05-23
Dial up?
Do you know Fred Flintstone? :lolflag:

Dial up last I checked was always a pain in Linux, its always worked better with a broadband connection

---

