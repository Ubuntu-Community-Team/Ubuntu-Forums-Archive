---
title: "PPP connection"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by hellomoto on 2008-07-17
Hello, I have broadband which is great.

I have however set up a PPP connection via my mobile phone for when Im out and about with my laptop.

I got it all connected:

> 
--> WvDial: Internet dialer version 1.60
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT
~[7f]}#@!}!} } }2}#}$@#}!}$}%\}"}&} }*} } g}%~
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Thu Jul 17 15:55:43 2008
--> Pid of pppd: 6964
--> Using interface ppp0
--> pppd: &#65533;&#65533;[06][08]8&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]8&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]8&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]8&#65533;[06][08]
--> local  IP address 10.84.84.242
--> pppd: &#65533;&#65533;[06][08]8&#65533;[06][08]
--> remote IP address 10.6.6.6
--> pppd: &#65533;&#65533;[06][08]8&#65533;[06][08]
--> primary   DNS address 193.113.200.200
--> pppd: &#65533;&#65533;[06][08]8&#65533;[06][08]
--> secondary DNS address 193.113.200.201
--> pppd: &#65533;&#65533;[06][08]8&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]8&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]8&#65533;[06][08]
--> Connect time 8.0 minutes.
--> pppd: &#65533;&#65533;[06][08]8&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]8&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]8&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]8&#65533;[06][08]
--> Disconnecting at Thu Jul 17 16:03:53 2008


and my mobile phone said it was connected too. 
However I couldn't seam t0 access any internet pages (even after waiting 8 minutes) or download my mail, or connect to pidgin.

I know I am connected because I can see a PPP connection when I  run ifconfig. I also disabled network manager because the connection had been setup away from it. 

So how do I find out my connection speed because it must be insanely slow!

Or is there another reason why my connection isn't working?

---

### Post by t0p on 2008-07-17
What kind of phone is it? GPRS? 3G/UMTS? 

GPRS can be very slow - it can be as little as 2 KB/sec sometimes! 3G is much better - I make 40-100 KB/sec.

Show us your /etc/wvdial.conf file.  And look at the link in my sig.

---

### Post by hellomoto on 2008-07-17
hey thanks for the quick reply.


> **t0p said:**
> What kind of phone is it? GPRS? 3G/UMTS? 

GPRS can be very slow - it can be as little as 2 KB/sec sometimes! 3G is much better - I make 40-100 KB/sec.

Show us your /etc/wvdial.conf file.  And look at the link in my sig.

I am connecting via GPRS in a sketchy reception area at the mo :P (hence why I think its probs just like you say 1 - 2KB/sec

Here is my wvdial.conf file:

> 


[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Baud = 230400
New PPPD = yes
Modem = /dev/ttyUSB0
ISDN = 0
Phone = *99#
Password = <mypassword>
Username = <myusername>
Stupid Mode = 1



I was thinking about getting a 3G usb stick to go into my computer. But if you know any 3G phones that connect well with ubuntu via cable. I would be interested to hear.

---

### Post by t0p on 2008-07-17
I connect via USB cable to a Sony Ericsson K800i.  It's on Tmobile. Nice and fast.

I think you're trying to connect via a BT mobile phone? At least, your DNS servers are owned by BT.  Do you know if it's possible to connect to the internet via their phones?  Reason I ask, your remote IP address was listed as 10.6.6.6, which is a "black hole", ie a reserved number that isn't meant to link to the net.  My remote IP addy is always a regular number.

---

### Post by hellomoto on 2008-07-17
> **t0p said:**
> I connect via USB cable to a Sony Ericsson K800i.  It's on Tmobile. Nice and fast.

I think you're trying to connect via a BT mobile phone? At least, your DNS servers are owned by BT.  Do you know if it's possible to connect to the internet via their phones?  Reason I ask, your remote IP address was listed as 10.6.6.6, which is a "black hole", ie a reserved number that isn't meant to link to the net.  My remote IP addy is always a regular number.

ahhh i did think that IP looked odd. 

I read the link in your sig, did u write that article? Its great!... (i used  it to setup my PPP connection in the first place).

Im also based in the UK and im with O2 on a pay monthly plan. The phone is a nokia 6822 connecting via data cable. Im not sure how 02 stand on this tbh, I will give them a ring now. But how would they tell if my phone is being used as a modem or just accessing a wap page on it?

I need a reliable internet connection when I go to uni in september. I like the idea of being able to plug in a 3G phone and use it, but what do you surgest? 

When using a mobile broadband USB stick do you still connect via a PP connection?

---

### Post by t0p on 2008-07-17
> **hellomoto said:**
>  
I read the link in your sig, did u write that article? Its great!... (i used  it to setup my PPP connection in the first place).

Thanks!  :)  Yep, all my own work!

> **hellomoto said:**
>  
Im also based in the UK and im with O2 on a pay monthly plan. The phone is a nokia 6822 connecting via data cable. Im not sure how 02 stand on this tbh, I will give them a ring now. But how would they tell if my phone is being used as a modem or just accessing a wap page on it?

I'm not sure if they can tell really. I connect with Tmobile, and their terms & conditions for pay as you go state that I'm not allowed to use my phone as a modem! So maybe they can't tell, I just don't know.

> **hellomoto said:**
>  
I need a reliable internet connection when I go to uni in september. I like the idea of being able to plug in a 3G phone and use it, but what do you surgest? 


I don't use wvdial anymore, cos I bought this Sony Ericsson K800i, and it connects as a modem in a different way.  It automagically detects when a USB cable is plugged into it, and links to the internet itself, creating a usb0 (ethernet) link. If you revisit my tutorial and scroll to the end, you'll see I've added info about this.

> **hellomoto said:**
> 
When using a mobile broadband USB stick do you still connect via a PP connection?

I haven't used a USB stick myself.  But ppl I've talked to on the internet have said they have followed my tutorial.

---

### Post by hellomoto on 2008-07-17
> **t0p said:**
> 

I don't use wvdial anymore, cos I bought this Sony Ericsson K800i, and it connects as a modem in a different way.  It automagically detects when a USB cable is plugged into it, and links to the internet itself, creating a usb0 (ethernet) link. If you revisit my tutorial and scroll to the end, you'll see I've added info about this.



ahhh, well i should imagin that a mobile broadband stick works in a similar way. ending up with a usb0 connection.

I just got off the phone to 02. Poor girl on the phone didn't know what i was on about (i only said i want to know if i can use my mobile as a modem). After putting me on hold for 5 mins. The answer was:

"No" lol.

"your not allowed to use your mobile phone as a modem on your current price plan sir. We can  enable it  for an extra £30 per month!"
 
so obviously my phone is detected for what ever reason and not allowed to connect.I will go down the usb mobile broadband route.

I am really worried about taking out a contract and only to find that the usb dongle won't work with ubuntu.

thank you for your help :)

PS your blog is saved in my favs! :P

---

### Post by c2olen on 2008-07-28
For your information,
I am using an UMTS/3G expresscard (not an usb stick but works exactly the same) on my Ubuntu laptop since 07.04. Linux first detects it as a storage device, so you have to do a icon_switch on it first. This flips it to be a modem device.

I am using Tmobile too, using a data-only contract (59euro/month). Works like a charm. I do not always get a nice connection right away. I had to restart the pppd daemon a couple of times the past year. Depending on coverage, I get a steady 60KB downstream. I've been working in the train during comute, and this too worked (although not as steady).

I used several configuration scripts to set up the link, but now i've got it running using udev. It's a shame the online-state-signal isn't announced on DBUS yet, so the network manager isn't aware of the connection. Firefox now always starts in offline mode.
NetworkManager 0.7 is said to have more UMTS/3G support builtin. I'm anctious to try it.

Here are some links I used:
[http://ubuntuforums.org/archive/index.php/t-494953.html](http://ubuntuforums.org/archive/index.php/t-494953.html)
[http://www.pharscape.org/content/blogsection/4/53/](http://www.pharscape.org/content/blogsection/4/53/)

---

