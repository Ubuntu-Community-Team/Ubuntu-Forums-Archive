---
title: "easy gprs/umts connection"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by steccia on 2008-06-25
Hi everybody

while I read some forums I noticed that many people fail to connect their mobile phone to PC for browsing the Internet.
I realized this small program as a wvdial front-end and that automatically sets the apn and parameters for the connection. It is also a charge counter. Someone would be kind enough to try it and tell me if it works? I have only been able to prove with my phone (Motorola v3i) and my operator (italian vodafone).
Thanks to all.

[http://sourceforge.net/projects/contascattiumts/](http://sourceforge.net/projects/contascattiumts/)

official project 3d at [http://forum.ubuntu-it.org/index.php/topic,196709.msg1307581.html#msg1307581](http://forum.ubuntu-it.org/index.php/topic,196709.msg1307581.html#msg1307581) (italian language)

---

### Post by steccia on 2008-06-25
release 0.2.3

added Spanish and French translation (Thanks to Giulia Pellecchia)

known bugs: some GUI imperfections depending on system configuration

---

### Post by steccia on 2008-06-26
nobody? :(

---

### Post by steccia on 2008-06-26
release 0.2.4

Added KDE support
Gui corrections

---

### Post by phoenix42 on 2008-06-30
Nice program, it works with some problems.

I have a Samsung F480 and my service provider is Mobitel (Slovenija)
After running Modem configuration wizard I had to add the following line to /etc/wvdial.conf to get wvdial working:

```
Init3 = at+cgdcont=1,"ip","internet"
```

Now the problem is that after connecting, Contascatti freezes. I think that if you use a new process/thread to run wvdial it would solve this issue.

Some suggestions:
- My SP charges by kB, so it would be nice if you added per kB charge display.
- there is only one decimal place in the charge settings, so in my case, where the charge is 0,00042 &#8364;/ kB, I cannot set it.
- this is just cosmetic, but do the fonts it charge settings realy need to be this large?

BTW, gnome-ppp has similar functionality but without the charge calculation.

Again, nice program, it just needs some improvements.

/etc/wvdial.conf
```

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2
Init3 = at+cgdcont=1,"ip","internet"
Modem Type = USB Modem
Baud = 460800
New PPPD = yes
Modem = /dev/ttyACM0
ISDN = 0
Stupid Mode = on
Phone = *99***1#
Username = mobitel
Password = internet
```

Contascattiumts outputs
```
user@laptop:~$ contascattiumts.gambas 
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2
ATQ0 V1 E1 S0=0 &C1 &D2
OK
--> Sending: at+cgdcont=1,"ip","internet"
at+cgdcont=1,"ip","internet"
OK
--> Modem initialized.
--> Sending: ATDT*99***1#
--> Waiting for carrier.
ATDT*99***1#
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Mon Jun 30 21:13:41 2008
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> Pid of pppd: 5501
--> Using interface ppp0
--> pppd: &#65533;&#65533;[06][08]`&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]`&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]`&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]`&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]`&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]`&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]`&#65533;[06][08]&#65533;&#65533;[06][08]
--> local  IP address 10.203.6.160
--> pppd: &#65533;&#65533;[06][08]`&#65533;[06][08]&#65533;&#65533;[06][08]
--> remote IP address 10.64.64.64
--> pppd: &#65533;&#65533;[06][08]`&#65533;[06][08]&#65533;&#65533;[06][08]
--> primary   DNS address 213.229.249.161
--> pppd: &#65533;&#65533;[06][08]`&#65533;[06][08]&#65533;&#65533;[06][08]
--> secondary DNS address 193.189.160.13
--> pppd: &#65533;&#65533;[06][08]`&#65533;[06][08]&#65533;&#65533;[06][08]
```

---

### Post by steccia on 2008-07-02
thankyou very much, now I'll look for init3 string correct generation. What version have you tested? New versions have profile setting, that will configure init3 string.

I'll adding counter for kb charge, adding front-end form for vnstat. When I'll complete it, maybe you can test it?

thankyou again

---

### Post by steccia on 2008-07-02
[B]know bug in actual version

Wrong use of decimal value in charge form

If you set 5 cents, the program set 50 cents[/B]

New release before 18.00 in italy

---

### Post by steccia on 2008-07-02
version 0.2.5

fix bug with decimals value

---

### Post by steccia on 2008-07-02
> **phoenix42 said:**
> 

Now the problem is that after connecting, Contascatti freezes. 



I found the error.
Contascatti freezes if unit leght is set to 0

I'm adding traffic counter mode and a control to prevent setting 0 unit lenght in time mode

---

### Post by steccia on 2008-07-02
version 0.2.6

fix bug with unit length = 0 

If you do an update, i suggest you to delete hidden file .contascatti.ini in your home dir

---

### Post by mptpro on 2008-07-02
I installed it fine.
When I click to run it, nothing happens

---

### Post by steccia on 2008-07-03
> **mptpro said:**
> I installed it fine.
When I click to run it, nothing happens

thankyou very much for your test
I need some information
What is your desktop?
What version are you testing? (actual is 0.2.6)
The primary dependences are gambas2-gb-form (> = 1.9.48 ), gambas2-gb-form (<< 2.1), gambas2-gb-gui (> = 1.9.48 ), gambas2-gb-gui (<< 2.1), gambas2-runtime (> = 1.9.48 ), gambas2-runtime (<< 2.1), are they satisfied?
thankyou

---

### Post by mptpro on 2008-07-03
Thanks for the response

Linux Ubunut 8.04 Hardy
Gnome2.22.2

I don't have the version number but installed the newest one.

I do not know how to check if the dependences are satisfield, sorry?

thanks.

---

### Post by steccia on 2008-07-04
if you use ubuntu, you dont need to control dependencies. I'm looking for a possible cause of your problem

---

### Post by steccia on 2008-07-04
**Version 0.3.1**

Added traffic mode for MB charge display

This is one of the last feature I'll tinking to put in this utility.

Plese, help me with bugs discover

---

### Post by steccia on 2008-07-07
i'm adding new translation, someone can help me with German and Portuguese?

---

### Post by steccia on 2008-07-14
> **mptpro said:**
> I installed it fine.
When I click to run it, nothing happens

I found the problem.

You must install gambas2-gb-gtk package (if you use gnome) or gambas2.gb.qt package (if you use KDE)

---

### Post by steccia on 2008-07-16
Version 0.3.2

new logo and icon
smaller gui

---

### Post by steccia on 2008-07-17
version 0.3.3

bug fix in statistics
minor gui correction

---

### Post by Stunts on 2008-07-17
Hi steccia!
I'd love to give you a hand with a Portuguese translation and some bug hunting, but I'm kind of tight in time right now.
Maybe next week or something?
I've got a Nokia 6330 to test with your application in Portuguese Vodafone BTW.

---

### Post by steccia on 2008-07-17
tankyou very much :)

send me a message when you may, i'll send you an e-mail with all the text

thankyou again

---

### Post by mptpro on 2008-07-24
ok, I got the program working... I installed the missing gambas2-gb-gtk, and installed the newest version.

However, when I click "Start Connection" I get the message...

The modem = Yes is not connected.


Perhaps I need drivers for my modem?

I have the Merlin X950D 3G 7.2 ExpressCard.

[http://www.novatelwireless.com/index.php?option=com_content&view=article&id=7:merlin-x950d-3g-72-expresscard-hsupahsdpa-networks&catid=1:merlin-pc-cards&Itemid=8](http://www.novatelwireless.com/index.php?option=com_content&view=article&id=7:merlin-x950d-3g-72-expresscard-hsupahsdpa-networks&catid=1:merlin-pc-cards&Itemid=8)

---

### Post by steccia on 2008-07-24
Hi,

You must click on "modem" in counter menu.
This starts configuration wizard, you do not need driver.

---

### Post by steccia on 2008-08-01
Version 0.3.4

Gui correction: font size fixed

---

### Post by steccia on 2008-08-28
**Version 0.4.1**

- added multiple configuration loader
- added 3G restriction for compatible mobiles

---

### Post by Stunts on 2008-08-28
Hi!
Sorry I remained silent for so long.
I've been much busier than usual (and still am) but I haven't forgotten your program.
I'll PM you when I have a bit more free time in my hands. =-)

---

### Post by steccia on 2008-09-15
Version 0.4.2

Fix bug with traffic counter.
Now the MB counter works

---

### Post by steccia on 2008-10-06
version 0.4.4

bug fix in counter.
Ignore version 0.4.3, use version 0.4.4

---

