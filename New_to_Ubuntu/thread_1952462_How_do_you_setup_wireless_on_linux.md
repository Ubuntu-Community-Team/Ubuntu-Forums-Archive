---
title: "How do you setup wireless on linux?"
date: 2012-04-04
forum: New to Ubuntu
---

### Post by nsahawks7 on 2012-04-04
[FONT=Comic Sans MS]I have tried everything, i used ndiswrapper, windows driver thingy, and other distros but still no luck. I have tried Ubuntu 10.04, Linux Mint 12, and Ubuntu 11.10 and Linux Mint 11. I just cannot connect with my usb adapter, and yes it is compatible with Linux. I ordered it from Amazon.
[SIZE=2]
**[http://www.amazon.com/Wireless-802-11N-150Mbps-Network-Adapter/dp/B00333F2YU/ref=sr_1_5?ie=UTF8&qid=1333549055&sr=8-5](http://www.amazon.com/Wireless-802-11N-150Mbps-Network-Adapter/dp/B00333F2YU/ref=sr_1_5?ie=UTF8&qid=1333549055&sr=8-5)**[/SIZE]

I have used 64bit with all my distros, my specs are 4GB ram, Phenom Quad Core, 500GB. The usb works great with windows but I can't seem to get it to work with Linux. Maybe because I am using 64bit? IDK. Also, Mint 12 freezes after 20 minutes or so, so I am not going to use that-has a bug. What distro would you recommend for my card? And can you help me install it? Thanks.!:p

[COLOR=Red]
BTW, THIS IS MY FIRST TIME USING LINUX AS A PRIMARY OS, SO PLEASE GIVE ME SPECIFIC DIRECTIONS? PLEASE?? THANKS!!!(:[/COLOR]
[/FONT]

---

### Post by munezz on 2012-04-04
Let me guess you probably set up the USB adapter ..................it does show that it has accepted the drive...........you are able to open the drive and check the contents..............................but whatever it will not connect to the Internet right ;).I faced a similar problem too.......................this is what i did..................I manually set the mobile broadband connection.

1)Select the country.

2)when the list of service provider comes,**don't **select your provider, instead select the option "I can't find my provider................."

3)Type for eg.SERVICE PROVIDER **UMTS** (the name of your service provider is to be typed there)

4)then comes to select the APN,there type your service provider in small caps,also add 3g if that is what u r using

5)select apply and reboot

..............................hope this works):P

---

### Post by ccrs8 on 2012-04-04
munezz - I think nsahawks7 is trying to set up wifi, not mobile broadband.

nsahawks7 - a user in the Amazon reviews says he got it installed super easy in Ubuntu 10.10, so this should definitely work.  This user rebooted after plugging it in the first time, so maybe that is a step you need to take.  When it is plugged in, do you get a wireless icon showing up to indicate that a wireless card is installed?

Here are the comments on the Amazon page about the Linux user:
[http://www.amazon.com/review/R1YYKACFJN6COQ/ref=cm_cr_dp_cmt?ie=UTF8&ASIN=B00333F2YU&nodeID=172282&linkCode=#wasThisHelpful](http://www.amazon.com/review/R1YYKACFJN6COQ/ref=cm_cr_dp_cmt?ie=UTF8&ASIN=B00333F2YU&nodeID=172282&linkCode=#wasThisHelpful)

---

### Post by nsahawks7 on 2012-04-04
Well, in NDIS Window Wireless App it says that my hardware is installed but no wireless options show up, only an ethernet one.

---

### Post by nsahawks7 on 2012-04-04
> **ccrs8 said:**
> munezz - I think nsahawks7 is trying to set up wifi, not mobile broadband.

nsahawks7 - a user in the Amazon reviews says he got it installed super easy in Ubuntu 10.10, so this should definitely work.  This user rebooted after plugging it in the first time, so maybe that is a step you need to take.  When it is plugged in, do you get a wireless icon showing up to indicate that a wireless card is installed?

Here are the comments on the Amazon page about the Linux user:
[http://www.amazon.com/review/R1YYKACFJN6COQ/ref=cm_cr_dp_cmt?ie=UTF8&ASIN=B00333F2YU&nodeID=172282&linkCode=#wasThisHelpful](http://www.amazon.com/review/R1YYKACFJN6COQ/ref=cm_cr_dp_cmt?ie=UTF8&ASIN=B00333F2YU&nodeID=172282&linkCode=#wasThisHelpful)




Also I don't understand how he installed the usb when he replied to Dhiojeni. He was tlaking about 'modprobe' and other kernel stuff that I didnt understand. Help? Sorry, completely new to ubuntu.

---

### Post by wildmanne39 on 2012-04-04
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by nsahawks7 on 2012-04-04
[FONT=Comic Sans MS]> **wildmanne39 said:**
> Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a[/FONT] [FONT=Comic Sans MS]
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```by clicking on new reply and click # and paste the information between the brackets.
Thank you

Will do! Also, I found this wifi usb and it seems to work exclusively for Ubuntu. Should I order it? It seems to work out of the box.
[B]
_[SIZE=2]http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&item=220896374760[/SIZE]_[/B]

[/FONT]

---

### Post by wildmanne39 on 2012-04-04
Hi, wait on ordering the new adaptor until we see what is going on with this one.
Thanks

---

### Post by NikTh on 2012-04-04
[nsahawks7]("http://ubuntuforums.org/member.php?u=1602954") hello , 
my personal opinion is that [FONT=Comic Sans MS]ndiswrapper is the worst program ever to use with Ubuntu. Must be the last of last of last.... option. 

Just follow "the master of wireless" here ... [/FONT][wildmanne39]("http://ubuntuforums.org/member.php?u=508533") . I always follow-track-watching his posts.
:D

---

