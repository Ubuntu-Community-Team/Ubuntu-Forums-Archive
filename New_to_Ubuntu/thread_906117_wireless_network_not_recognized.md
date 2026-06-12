---
title: "wireless network not recognized"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by tbrownarcher on 2008-08-31
FInally!!!!!!! after 15 years i have an ubuntu install working.
I have been trying since Debian early in the 90's however it's not recognizing my wireless network which is

Linksys Wireless-G Broadband Router with SpeedBooster model # WRT54GS. 

This is connected to a Dell dimension 3000 with a 320 gig windows xp drive which i'm on right now, and 100 gig ubuntu drive which i cannot get to the internet with because it does not recognize my wireless network.  It recognizes the ethernet card but does not pick up the router which is hard wired to this computer and wirelessly connected to 2 other desktop computers which are all connected to a Cox cable modem.

Is it just that it needs to have the drivers installed where do I find Linux drivers for the router? or what else could be wrong?


Thanks very much, 
Nate (tbrownarcher)

---

### Post by tbrownarcher on 2008-08-31
Im Sorry  but for some reason it works now.  Still when i go into System>Administration>Network it is not in the display as recognized but i m on the internet now.. I sure i m not gonna go smoothly so anything you can tell me would be great.


Thanks,
Nate (tbrownarcher)

---

### Post by linuxlab on 2008-08-31
um, the router you are using will be connected to the dell via ethernet cable, yes?
so you will get a connection through the ethernet cable --> router/modem.
do you have a wireless PCI card in the Dell?
or are you asking about the other two PC's?
also why is the router/modem connected to the PC via Ethernet cable if you have a wireless network?

maybe I have not understood

---

### Post by Gone fishing on 2008-08-31
Have you tried setting it up using Network Manager?

Administration > Network

If you type "sudo ifconfig" does the Ethernet card have an appropriate IP address if yes can you ping the router? not Id try using a fixed IP address for e.g. 192.168.1.2 if you router uses 192.168.1.1 and seeing if you can ping the router from a terminal

---

### Post by tbrownarcher on 2008-08-31
Linux lab:

I just followed the instructions for the linksys wireless router.  They said the main computer needed to be connected to the router by wire .. the router connects tothe other 2 computers here so i guess it&#347; wireless.  I am on the internet now but it still does not recognize my wireless setup.  
Since i m coming from windows xp home and it does deal with the wireless that is what i was expecting.  I m betting that my other 2 computers are not connected though.  Will check that after while..

Thanks,
Nate

---

### Post by tbrownarcher on 2008-08-31
GoneFishing:

I would love to be GoneFishing... the Boat is broken.  Workin on it though.  LOL

Pasting here the line after the ping  
ping 198.168.1.1
PING 198.168.1.1 (198.168.1.1) 56(84) bytes of data.

and then the cursor just spun it&#347; (Blinking) wheels.

here is the ifconfig results 


nate@nate-ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:20:09:f4:fd  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:20ff:fe09:f4fd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5854 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4074 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7596319 (7.2 MB)  TX bytes:388402 (379.2 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1180 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1180 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:59000 (57.6 KB)  TX bytes:59000 (57.6 KB)

---

### Post by porchrat on 2008-08-31
If I understand correctly then you can connect to the internet through the router when your Dell is connected via an ethernet cable, however you cannot connect when you try to use wireless on that same Dell computer.

If that is the case then you may need to get other drivers.

In that case you need to know what wireless card you are running.

To do that you type this:

```
sudo lshw -C network
```

hope that helps

---

### Post by tbrownarcher on 2008-08-31
Porchrat:
No, I guess i m ok here my wireless is not visibly recognized though.
I can actually connect to the internet.  I can actually see the other 2 computers.  since the other 2 computers are wirelessly connected to the router and to the main computer through the router then the wireless is recognized and everything works... however.. why do i not find anywhere that says it knows what router i m using and a way to configure it 
The only thing i seeing is the ethernet card but everything works.  I guess it&#347; ok until something happens and i have no idea how i will deal with it then since i can find any configuration files or utilities.

thanks,
Nate

---

### Post by hotrod6657 on 2008-08-31
I'm not totally clear on the last question.  Are you asking about configuring the router itself?  Like changing it's internal settings?

If so you need to "dial" in to the router.  For the Linksys i think this should work.  Open up your browser and type 192.168.1.1 for the URL.  It might prompt you for username and password.  The default username is blank and the password is admin.  At least on the Linksys routers I've used.  Yours might be different but you can google that.

That should open up the router's internal configurations and allow you to change settings like security and the login information.

hotrod

**EDIT:  ** By the default username is blank i mean the actual word "blank".

---

### Post by hotrod6657 on 2008-08-31
> **tbrownarcher said:**
> Porchrat:
why do i not find anywhere that says it knows what router i m using and a way to configure it 
The only thing i seeing is the ethernet card but everything works.  I guess it&#347; ok until something happens and i have no idea how i will deal with it then since i can find any configuration files or utilities.

thanks,
Nate

Do you mean that you don't see the router from the computer that is wired to it?  Does that one have a wireless card?

For the wired connection as far as your network card is concerned you're wired directly to the internet.  It's not going to show you the router because it's essentially the middle man and you pluging in to it is all that's needed.  You don't have to "connect" to your wired connection.

With the wireless you should see the router and be able to connect to it, because that's the way wireless works.  It's up to you to tell your computers with wireless to grab that signal, and it's up to the router to tell them that it has a signal.

Did that clear anything up or make it more confusing?  Hope it helped.

hotrod

---

### Post by tbrownarcher on 2008-08-31
Hotrod... that may be exactly what i 'm needing.  Are you saying that the only way i will see the router is to be wireless?  That if i'm wired to the router through the ethernet card all i'm going to see is the ethernet card ?

The other 2 computers work and i can see them.  This one works 2.  Lol but shame on me ... due to another configuration problem with my display (nvidia) I tried a second install which did not stop a thing.... now I have to go back and get everything i HAD working working again .. sigh.  I think the info i need is in this thread early on so i will go back and read that and try it .. for now i'm in windows trying to communicate.. 

If I interpreted you correctly then i will call this thread answered. 


Thanks,
Nate

---

### Post by tbrownarcher on 2008-09-01
ok!  I'm not sure why but I have a connection again.  After rebooting about the 4th time since the last post I have a connection but don't know what caused it 
Before when i booted up the network icon would spin and spin trying to make a connection. Finally it would go to the 2 computer icon which i thought would mean i had a connection but I did not.  then looking at connection information there was nothing in any of the lines.  
then this time after rebooting the network icon hardly spun at all and  turned to double computer icon and i have connection, and numbers in the lines of eh information window.

Don't know what's goin on but it's workin again.  I'm confused but happy lol.  Will write those numbers down and be off to solve my problems of the   display configuration.

how does the thanks icon in the right corner work?  does it end the thread or just thank the poster?  THANKS everyone!!!!!!!!

Thanks, 
Nate

---

### Post by hotrod6657 on 2008-09-01
The thanks thing just thanks the poster.  To mark it as solved you have to go to thread tools at the top of the page and as the original poster you should be able to "mark thread as solved."

I hope my info helped.  Unless you're connecting to the router wirelessly you won't know it's there.  All your computer will know is that there's something connected to it's NIC sending it information, no specifics about the device doing the sending.  Really its sole purpose in life is to split your single line-in into a handful of wired lines and however many wireless connections you want.

Did you try dialing in to the router?  I'm curious if that IP was right.  As for the connection just starting to work, that is strange.  You didn't happen to power cycle (turn off then back on) the router did you?  Sometimes that's all it takes to go from no connection to smooth sailing.

I hope it keeps working for you, and I'm glad that my info seemed to help a.

Hotrod

---

### Post by tbrownarcher on 2008-09-01
I have posted 2 times since hotrod posted his last and mine are not visible ?  What else am i doing wrong >? sigh!

thanks,
Nate

---

### Post by tbrownarcher on 2008-09-01
No I'm wrong the posts are there .. Ok Hotrod. It's working . NO i did not power down the router in fact some of these posts are through windows on another computer using that router.  I'm completely stumped and if I get no indications not to do so later I'm going to mark this as solved even though it is not actually solved just working.

Now i'm going to go try to get an almost as strange of a problem the display configuration.  So if you are into fixing display problems i have a thread started ont that too.  

Thanks,
Nate

---

### Post by hotrod6657 on 2008-09-01
haha, man, I don't know what to tell you then, maybe you're just lucky.  I'm glad it's working and I would say that unless the wired side has stopped working that you can go ahead and mark this one as solved.

Thanks for thanking me as well, i appreciate it!

hotrod

---

### Post by hotrod6657 on 2008-09-01
Oh, and i looked for your thread on the display thing but all i saw were a few from 2007, too old to post on.  I would try starting a new one (unless you have and i'm just missing it).  If you do start a new one let me know and I'll see what i can't come up with, i've had marginal success with graphic card drivers since coming over to Ubuntu, but as of late things have been going much more smoothly.

Best of luck on the display thing,

hotrod

---

