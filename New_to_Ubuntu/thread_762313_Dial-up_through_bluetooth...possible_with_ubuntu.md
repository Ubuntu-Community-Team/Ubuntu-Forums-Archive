---
title: "Dial-up through bluetooth...possible with ubuntu?"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by socialistic on 2008-04-22
Ok...so I decided to give ubuntu a try, installed it on my main hard drive and am dual booting that and win xp pro.

My internet connection relies on my usb adapter and software, which lets me connect my cell phone to my computer via bluetooth...then I "dialup" through my phone from the software to access my cellular provider's data network.  Basically I'm connectined through my phone as (user: my number, pass: none, number dialed: #777) and it connects to the net.

Can I do this with ubuntu?  This will make or break the deal of me continuing to use this OS...as this is my only way to connect to the internet.  I tried messing with the built in ubuntu bluetooth...but when I try to access my phone from the bluetooth dialog(which it automatically found I guess), it says "invalid address" or something of the sort.

Any help is greatly appreciated.

---

### Post by socialistic on 2008-04-22
A friend found this link for me...

[http://learningcomputer.info/2007/11/25/how-to-connect-to-the-internet-using-bluetooth-cellphone-on-ubuntu/](http://learningcomputer.info/2007/11/25/how-to-connect-to-the-internet-using-bluetooth-cellphone-on-ubuntu/)

I tried that...but at step 2 (install gnome-ppp), I got stuck. There is no gnome-ppp in the package list.

Basically that link seems like it covers the exact problem I need addressed...but I am a BRAND NEW user to this OS, never touched anything other than windows.  So I could use some help accomplishing this task...as that link's info gets pretty complicated from what I can see.

Thanks!

EDIT:  Found some more possibly related links.

[http://medien.informatik.uni-ulm.de/~frank/bluetooth/bluetooth-howto.html](http://medien.informatik.uni-ulm.de/~frank/bluetooth/bluetooth-howto.html)

[http://www.bluez.org/faq.html](http://www.bluez.org/faq.html)

I honestly don't have any idea what to do...I have bluez-gnome installed, can't find gnome-ppp, ubuntu recognizes when I plug in my usb bluetooth adapter, but I can't connect to my phone in order to dial-up to the net!

---

### Post by socialistic on 2008-04-22
I posted this problem in the correct section(networking&wireless), and I'm hoping it gets some hits in there because not having internet on my desktop is a HUGE problem for me right now and needs to be fixed immediately...this win xp laptop can only hold me over for so long.

I apologize if I was in the wrong for posting this thread in the beginner's section...I'm a newb to both ubuntu and the forums. :(

New thread-
[http://ubuntuforums.org/showthread.php?t=762467](http://ubuntuforums.org/showthread.php?t=762467)

---

### Post by rbcl15 on 2008-05-01
I managed to connect to internet I think through wvdial. How do I engage firefox though, the browser is saying "no data".

---

### Post by pseudo-random on 2008-05-01
Could you post the result of ifconfig and route.
I used to use my old Nokia over bluetooth. Here's a little reminder I knocked up to help me. 
```

GPRS over bluetooth HOWTO: REVISED 8/12/07 for Gutsy.

1)Enable BT on both
2) Ensure dev's are paired (sudo hcitool auth 00:0E:6D:07:60:BE)
3) sudo l2ping 00:0E:6D:07:60:BE
4) set up rfcomm: sudo rfcomm bind rfcomm0 00:0E:6D:07:60:BE 1
5) type rfcomm: should get rfcomm0:00:0E:6D:07:60:BE channel1 clean.
6) call chat script: sudo pppd noccp call gprs (esnure other ifaces are down)
7) Check routing table and cat /var/log/syslog | grep pppd
8) ifconfig should have: PPP0 with 10.*.*.* IP.
Done!

On error:
Remove all rfcomm bindings, kill all pppd processes.
Run GPRS. Then Connect GUI. ifconfig should give ppp0...
```
Sorry if some of thats confusing. I didn't intend to publish it.
My gprs ppp script:
```
/dev/rfcomm0
115200
connect 'chat -f /etc/ppp/chat/gprs'
defaultroute
usepeerdns
debug
noauth
nomagic
```

---

