---
title: "HOW TO:  Connect T-Mobile Wireless Internet Through Your Cell Phone"
date: 2008-01-17
forum: Outdated Tutorials &amp; Tips
---

### Post by diablo75 on 2008-01-17
EDIT:  I've revised the below tutorial into an updated, short form as follows:

1.  In terminal:

```
sudo apt-get install wvdial
```

2.  In terminal (after you've attached your cell phone via usb or bluetooth):

```
sudo wvdialconf
```

3.  In terminal:

```
sudo gedit /etc/wvdial.conf
```

4.  Minimize Gnome Tex Editor containing the wvdial.conf file, and open a second terminal window.  Type in:

```
dmesg | fgrep acm
```

You should see something like this returned in the output:

**[ 9168.949496] cdc_acm 2-3:1.0: ttyACM0: USB ACM device**

This ACM device is your phone, and it is now an accessible piece of hardware. For wvdial to use it, you must make sure the above configuration file points wvdial to the right device name. If the above dmesg output produces a different ttyACM#, change it accordingly to match your PC. (Note, if you don&#8217;t get any dmesg results at all, try typing this in first:** sudo modprobe cdc_acm**).

After your wvdial.conf file is created and your sure your Modem = /dev/tty line is correct, save the file and close gedit. Then simply run wvdial from the terminal:

$ wvdial

That's pretty much it!  An older version of this guide is below:  It's written with T-mobile phones in mind.  Other carries work much in the same way, but their "phone numbers" vary, as well as username/password requirements.  The rest of the wvdial.conf file is pretty nicely auto-configured using wvdialconf in terminal.

-----------------


You can find a hardcopy of this walk through on my blog at [this location]("http://davestechsupport.com/blog/2008/01/18/how-to-connect-t-mobile-wireless-internet-in-linux/").

I recently took on the challenge of getting an old PC up and running with Xubuntu 7.10. My father recently purchased the T-Mobile Internet package, which allows him to connect his computer to unlimited mobile Internet for $20 a month. Setting this up proved to be easier than I anticipated.

   1. The first thing you need to do is change the USB configuration in your phone. On my phone (a Motorola K1) and many other T-Mobile phones, you have to change your USB configuration:** make your default USB connection a data connection**. By default, most phones are configured to be in &#8220;Memory Card&#8221; mode.
   2. Next, you need to install a piece of software in Ubuntu called &#8220;wvdial&#8221;. To do this, click on Applications>Accessories>Terminal. Once your terminal window is open, type in the following:
 ```
sudo apt-get install wvdial
```   3. Edit your wvdial.conf file. Type 
```
sudo gedit /etc/wvdial.conf
```in a terminal window to do this.


Once you have your wvdial.conf file open, paste in the following text over all the contents of the file:

```
[Dialer Defaults]
Init1 = AT+CGDCONT=1,&#8221;IP&#8221;,&#8221;internet2.voicestream.com&#8221;
Modem Type = USB Modem
Phone = *99***1#
Password = pass
Username = user
Modem = /dev/ttyACM0
Baud = 460800
```Take note of the &#8220;ttyACM0&#8243; part. This may not be the same on your PC. To find out what yours is, attach your phone to your PC, and then type the following into the terminal:

```
dmesg | fgrep acm
```You should see something like this returned in the output:

**[ 9168.949496] cdc_acm 2-3:1.0: ttyACM0: USB ACM device**

This ACM device is your phone, and it is now an accessible piece of hardware. For wvdial to use it, you must make sure the above configuration file points wvdial to the right device name. If the above dmesg output produces a different ttyACM#, change it accordingly to match your PC. (Note, if you don&#8217;t get any dmesg results at all, try typing this in first:** sudo modprobe cdc_acm**).

After your wvdial.conf file is created and your sure your Modem = /dev/tty line is correct, save the file and close gedit. Then simply run wvdial from the terminal:

$ wvdial

Wvdial will then access your phone as it is directed to do so by the wvdial.conf file, and essentially dial T-mobiles Internet Service Provider. No real username or password is required for this, so leave the user/pass in the above config file as it is written. You&#8217;ll see some output on the screen that looks like this:

user@user-desktop:~$ wvdial
WvDial<*1>: WvDial: Internet dialer version 1.56
WvModem<*1>: Cannot get information for serial port.
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: AT+CGDCONT=1,&#8221;IP&#8221;,&#8221;wap.voicestream.com&#8221;
WvDial Modem<*1>: AT+CGDCONT=1,&#8221;IP&#8221;,&#8221;wap.voicestream.com&#8221;
WvDial Modem<*1>: OK
WvDial<*1>: Modem initialized.
WvDial<*1>: Sending: ATDT*99#
WvDial<*1>: Waiting for carrier.
WvDial Modem<*1>: ATDT*99#
WvDial Modem<*1>: CONNECT
WvDial<*1>: Carrier detected. Waiting for prompt.

At this point, the program will pause as it handshakes and establishes a connection using PPP. After about 10 or 20 seconds, the output will continue on and look similar to this:

WvDial<Notice>: Don&#8217;t know what to do! Starting pppd and hoping for the best.
WvDial<Notice>: Starting pppd at Thu Jan 17 17:50:28 2008
WvDial<Err>: Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
WvDial<Err>: &#8211;> PAP (Password Authentication Protocol) may be flaky.
WvDial<Err>: Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
WvDial<Err>: &#8211;> CHAP (Challenge Handshake) may be flaky.
WvDial<Notice>: Pid of pppd: 13530
WvDial<*1>: Using interface ppp0
WvDial<*1>: pppd: ?06][08]?06][08]??[06][08]
WvDial<*1>: pppd: ?06][08]?06][08]??[06][08]
WvDial<*1>: pppd: ?06][08]?06][08]??[06][08]
WvDial<*1>: pppd: ?06][08]?06][08]??[06][08]
WvDial<*1>: pppd: ?06][08]?06][08]??[06][08]
WvDial<*1>: local IP address 10.38.225.200
WvDial<*1>: pppd: ?06][08]?06][08]??[06][08]
WvDial<*1>: remote IP address 192.168.100.101
WvDial<*1>: pppd: ?06][08]?06][08]??[06][08]
WvDial<*1>: primary DNS address 66.94.9.120
WvDial<*1>: pppd: ?06][08]?06][08]??[06][08]
WvDial<*1>: secondary DNS address 66.94.25.120
WvDial<*1>: pppd: ?06][08]?06][08]??[06][08]

Congrats! You are now connected to the Internet using your cellphone. And all you have to do to establish a connection is open a terminal window and type wvdial.

To end your connection, you can simply close the terminal window containing the above mess, or hit CTRL-C while the terminal window is open. So be careful and don&#8217;t close the window by accident, or your connection will be dropped and you&#8217;ll have to run wvdial all over again. Oh, the agony of typing that one command over again!!

Anyway, enjoy your T-Mobile Wireless Internet connection! You should see a steady downstream of about 20 to 30 KB per second, which is about 5 times faster than dial up. And it&#8217;s unlimited! It&#8217;s not DSL or Cable, but that&#8217;s still not a bad deal for 20 bucks a month.

[COLOR=Red]Additional Information for Sprint users:[/COLOR]

You may need to make your wvdial.conf file look more like this to get your phone to work:

[Dialer Defaults]
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Phone = #777
ISDN = 0
Username = NONE
Init1 = ATZ
Password = NONE
Modem = /dev/ttyACM0
Baud = 460800
Auto DNS = 1
Stupid Mode = 1

In addition, you will want to do a sudo gedit /etc/ppp/peers in a terminal window and add the following two lines to the file:

lcp-echo-failure 0
lcp-echo-interval 0

I do not have a Sprint phone, but according to [this guide]("http://wiki.howardforums.com/index.php/Tether_with_Linux") it is confirm to work on a Sprint Samsung MM-920.

---

### Post by wankel on 2008-01-21
When using this as  a regular internet connection, please be aware that most "unlimited" cell phone internet offers actually have a "fair use" of less than 200 MB. After that, regular data tariff plans apply, so that would be an expensive try-out of the latest 8.04 beta-iso ;-)

---

### Post by Kevbert on 2008-01-26
Hi. If you use the phone number *99***1# as the call number instead of *99# you can have several Access Point Names (APN)  in your phone.  By using AT+CGDCONT=1... you are entering that address into the phone at position 1 and then by using *99***1# you actually connect to the address located at position 1.  With this idea in mind you can then enter some additional APNs in the phone which  can be useful when you need to travel abroad and the local service provider has roaming agreement with your home phone provider.  The next initialization string would then be AT+CGDCONT=2... and the number to dial would be *99***2#  Don't forget that the user name and password may be different.
Another thing to bear in mind is that the data transfer speed depends on the number of people accessing the network at any one time.
:)

---

### Post by atupeck on 2008-04-20
Every time i try to dial with wvdial with my Motorola V3xx I get this:

```
tupeck@atupeck-laptop:~$ wvdial
WvDial<*1>: WvDial: Internet dialer version 1.56
WvModem<*1>: Cannot get information for serial port.
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: AT+CGDCONT=1,”IP”,”internet2.voicestream.com”
WvDial Modem<*1>: AT+CGDCONT=1,b [1d]IPb [1d],b [1d]internet2.voicestream.comb [1d]
WvDial Modem<*1>: ERROR
WvDial<Err>: Bad init string.
WvModem<*1>: Cannot get information for serial port.
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: AT+CGDCONT=1,”IP”,”internet2.voicestream.com”
WvDial Modem<*1>: AT+CGDCONT=1,b [1d]IPb [1d],b [1d]internet2.voicestream.comb [1d]
WvDial Modem<*1>: ERROR
WvDial<Err>: Bad init string.
WvModem<*1>: Cannot get information for serial port.
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: AT+CGDCONT=1,”IP”,”internet2.voicestream.com”
WvDial Modem<*1>: AT+CGDCONT=1,b [1d]IPb [1d],b [1d]internet2.voicestream.comb [1d]
WvDial Modem<*1>: ERROR
WvDial<Err>: Bad init string.

```

also, the contents of my wvdial.conf are:
```
[Dialer Defaults]
Init1 = AT+CGDCONT=1,”IP”,”internet2.voicestream.com”
Modem Type = USB Modem
Phone = *99#
Password = pass
Username = user
Modem = /dev/ttyACM0
Baud = 460800
```
Just like in the previous post, however..the wvdial.conf that wvdial automatically created for me, with minor adjustments for the dialing number are:
```
[Dialer Defaults]
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
; Phone = *99***1#
ISDN = 0
; Username = user
Init1 = ATZ
; Password = pass
Modem = /dev/ttyACM0
Baud = 460800
```

Any help would be appreciated...Im trying to make the break from Windows, but i can't do it without my wireless internet.

---

### Post by diablo75 on 2008-04-20
> **atupeck said:**
> 
Just like in the previous post, however..the wvdial.conf that wvdial automatically created for me, with minor adjustments for the dialing number are:
```
[Dialer Defaults]
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
; Phone = *99***1#
ISDN = 0
; Username = user
Init1 = ATZ
; Password = pass
Modem = /dev/ttyACM0
Baud = 460800
```



Try this:

```
[Dialer Defaults]
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Phone = *99#
ISDN = 0
Username = user
Init1 = ATZ
Password = pass
Modem = /dev/ttyACM0
Baud = 460800
```

---

### Post by ronnie666 on 2009-10-15
Thanks for the info.
--------------------------------
WirelessPhoneGallery | The best source of all [FONT=&quot][cell phone accessories]("http://www.wirelessphonegallery.com/phoneaccessories.aspx").[/FONT]

---

### Post by jarviser on 2010-12-21
> **Kevbert said:**
> Hi. If you use the phone number *99***1# as the call number instead of *99# you can have several Access Point Names (APN)  in your phone.  By using AT+CGDCONT=1... you are entering that address into the phone at position 1 and then by using *99***1# you actually connect to the address located at position 1.  With this idea in mind you can then enter some additional APNs in the phone which  can be useful when you need to travel abroad and the local service provider has roaming agreement with your home phone provider.  The next initialization string would then be AT+CGDCONT=2... and the number to dial would be *99***2#  Don't forget that the user name and password may be different.
Another thing to bear in mind is that the data transfer speed depends on the number of people accessing the network at any one time.
:)

Just like to say THANKS for explaining that - I had been wondering why there were two numbers that seemed to do the same thing!

---

