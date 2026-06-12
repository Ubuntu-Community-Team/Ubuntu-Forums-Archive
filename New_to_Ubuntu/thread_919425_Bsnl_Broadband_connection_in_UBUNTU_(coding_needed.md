---
title: "Bsnl Broadband connection in UBUNTU (coding needed)"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by gopee1990 on 2008-09-14
Im a new user to ubuntu !!

I dont know how to connect to internet using linux terminal !
somebody said that i have to get coding for network connection !!

can you provid me coding for my specifications :
specifications in windows for bsnl broadband are:

[COLOR="Red"]Device Name :WAN miniport 
Device Type :PPPoE
Server Type :PPP
Transports :TCP/IP
Authentication :MD5 CHAP
PPP multilink framing :off
server ip :xx.xx.xxx.x
client ip :xx.xx.xxx.xx
Address type :Manually configured
ip address :xxx.xxx.x.x
subnet mask :255.255.255.0
Default Gateway :192.168.1.1[/COLOR]
Help me soon !!

:guitar:

---

### Post by Madman6510 on 2008-09-14
So, what are you trying to do?

---

### Post by tuxerman on 2008-09-14
open up a terminal.
Type **sudo pppoeconf**, entering your password when asked.
Follow the instructions. **When unsure, the default options are fine.**
You can either start it manually each time by entering **pon dsl-provider** at the terminal each time or have it set to connect automatically at boot time.

I had written a page on this in my blog.. you can visit this if you want more info[http://anotherbloggerbloke.blogspot.com/2008/07/broadband-in-ubuntu.html]("http://anotherbloggerbloke.blogspot.com/2008/07/broadband-in-ubuntu.html")

Good luck :)

PS: Oh, and tell the person who told you that coding is required, that a single, simple command entered in the terminal is not something I would call "coding"

---

### Post by gopee1990 on 2008-09-15
thank you guys i will try the one and reply u again !!!
:popcorn:

---

### Post by mailtwogopal on 2008-09-15
Hi gopee,

 Surely it will work. no doubts. I had same instruction from this forum and i went by defaults. It really went fine.

---

### Post by gopee1990 on 2008-09-17
Thank you guys it really worked for me !! now i m a part of open source operating system linux ubuntu !!

:popcorn:

---

### Post by gopee1990 on 2008-10-12
hey guys ,
can you tell me how can i connect with the same configuration as above with :

fedora 9 and
open suse ???? 

please help me out !
:lolflag:

---

### Post by urgu on 2009-06-06
My problem was that despite typing in all that code, what was supposed to happen didn't. Like, the IP address and stuff was supposed to appear, but it didn't. So, i configured my modem to automatically connect when switched on. No need to trigger the connection, just switch the modem on. This worked for me.

---

### Post by raj_guard on 2009-06-15
Hi,

I use BSNL Broadband using the modem SmartAX MT882 Huawei.

I tried to configure using the procedure outlined in the blogpost in one of the posts/ But the result was not desired. The message read

"Sorry, I scanned 1 interface, but the Access Concentrator of your provider did not respond. Please check your network and modem cables. Another reason  for the scan failure may also be another running pppoe process which controls the modem."

I guess it scanned 2 interfaces, eth0 and pan0.

Now how do i proceed, please help.

---

### Post by vijaybilgoji on 2009-07-26
Bsnl broadband settings for ubuntu 8.04-

1.Type 192.168.1.1 in your browser u will get the router page open.
Type username-admin and password-admin to open this page.
2.In WAN Settings Select- PPP
3.Type u r username and password given to u by Bsnl.
4.Select- Always on.
5.Select-Apply
Router will save u r settings and reboot.

Now select the option DHCP just below WAN Settings

6.IN DHCP-- Enable the DHCP Server and click Apply
Router will save u r settings and reboot at this stage.

Close the router page.

7.Now go to the Top pannel of your desktop in that
  i)click Network connection (At the right corner of ur pannel)
 ii)Mannual configuration
iii)Select your wired connetion 
 iv)Click on properties
  v)Select Automatic Configuration(DHCP)& Click on OK

Run your browser and enjoy the virus free browsing through ubuntu.

---

### Post by ashwinhgtx on 2009-11-12
> **vijaybilgoji said:**
> Bsnl broadband settings for ubuntu 8.04-

1.Type 192.168.1.1 in your browser u will get the router page open.
Type username-admin and password-admin to open this page.
2.In WAN Settings Select- PPP
3.Type u r username and password given to u by Bsnl.
4.Select- Always on.
5.Select-Apply
Router will save u r settings and reboot.

Now select the option DHCP just below WAN Settings

6.IN DHCP-- Enable the DHCP Server and click Apply
Router will save u r settings and reboot at this stage.

Close the router page.

7.Now go to the Top pannel of your desktop in that
  i)click Network connection (At the right corner of ur pannel)
 ii)Mannual configuration
iii)Select your wired connetion 
 iv)Click on properties
  v)Select Automatic Configuration(DHCP)& Click on OK

Run your browser and enjoy the virus free browsing through ubuntu.

This doesn't work if the modem is in bridging mode.

---

### Post by GIRI MURALI on 2010-05-16
i think some feels difficulty in connecting bsnl broadband in Ubuntu is because they need a dialer software.
This link will help you 
[http://www.beubuntu.co.cc/2010/03/connect-bsnl-broadband-in-ubuntu-hai.html](http://www.beubuntu.co.cc/2010/03/connect-bsnl-broadband-in-ubuntu-hai.html)

---

