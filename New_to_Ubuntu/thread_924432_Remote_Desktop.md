---
title: "Remote Desktop??"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by faraz_k86 on 2008-09-19
I want to connect to my friends computer via the remote desktop. i.e. I want to control his desktop.

How do I do it? Where do I enter the information and where can I get that information?

---

### Post by bodhi.zazen on 2008-09-19
you can use several programs to do this, easiest is via vnc.

[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

---

### Post by acidsolution on 2008-09-19
If your computer has miscrosoft windows than you can use 

rdesktop ip_address_of fren

type this command in terminal 

if your frens computer is in linux than he must have vncserver running in his computer

install vncserver in frens computer and than use vncviewer to control his desktop

---

### Post by holiday on 2008-09-19
MainMenu.Internet.Remote Desktop Viewer? I haven't tried it lately so don't remember if it was a trouble or not, but I remember it working.

---

### Post by halitech on 2008-09-19
> **faraz_k86 said:**
> I want to connect to my friends computer via the remote desktop. i.e. I want to control his desktop.

How do I do it? Where do I enter the information and where can I get that information?

what operating system on your friends computer? Also, is he behind a router on highspeed or on dialup?

If he's on windows with highspeed and a router, I'd recommend logmein ([www.logmein.com](www.logmein.com)) which will work with a router much easier then trying to configure a router to forward the correct ports.

---

### Post by faraz_k86 on 2008-09-19
Thx for the replies.

My friend is using Linux Mint. I have windows as well as Linux Mint.

K so Ill download the VNC client, but then what should i enter, what info do i need? My friend is using a router, her ip address is 192.168.0.98

but im sure this will not work, like there can be thousands of people with this ip.

i read the vnc help document linked above but could not find anything about this

---

### Post by faraz_k86 on 2008-09-19
bump :)

---

### Post by k33bz on 2008-09-19
> **faraz_k86 said:**
> Thx for the replies.

My friend is using Linux Mint. I have windows as well as Linux Mint.

K so Ill download the VNC client, but then what should i enter, what info do i need? My friend is using a router, her ip address is xxx.xxx.xx.xxx

but im sure this will not work, like there can be thousands of people with this ip.

i read the vnc help document linked above but could not find anything about this
I am not sure how you would go about this, but as a kind reminder for your freind. I would edit that post and take her IP address off.

---

### Post by howefield on 2008-09-19
> **k33bz said:**
> I am not sure how you would go about this, but as a kind reminder for your freind. I would edit that post and take her IP address off.]

I'm not sure that it matters, looks more like a lan address rather than an internet ip.

---

### Post by nkri on 2008-09-19
Yeah, you're taking a pretty big risk posting her IP.  And it can't hurt too much to edit it, can it?

Good luck!
-nkri

---

### Post by howefield on 2008-09-19
Help me understand the risk ? 

I have the same ip, am I at risk now ? :)

---

### Post by bodhi.zazen on 2008-09-19
LOL

In a nut shell, you have more then 1 IP address. If you are on a router, you IP address will be something like :

192.168.1.19

Since you are behind a router, this does not matter.

Your router serves several functions and one is to NAT, or direct (network) traffic between all the computers on your LAN and between your LAN and the Internet. You are assigned a public ip address by your IP provider. You can see your public IP address here :

[http://showip.net/](http://showip.net/)

Your router also acts a a firewall, so you can not directly access your computer from outside your LAN.

In order to access your computer on your LAN you must configure your router to forward the traffic to your computer on your LAN, This is called 

[Port Forwarding]("http://portforward.com/routers.htm")

So to access your friends box s/he will need to forward port 5900.

Hiding your ip address is security by obscurity and really is no security at all, IMO.

See: [Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812")

---

### Post by faraz_k86 on 2008-09-20
yeah i knew about the ip. thats why i posted it. its no security threat as its a local ip and hundreds or thousands of users may have the same ip.

but this still does not help me connet to her computer.

help me out here plz.

---

### Post by styfle on 2008-09-20
Do you need to know your friend's IP? Tell him to go to [www.whatsmyip.org](www.whatsmyip.org)
Then connect to hisIP:5900

---

### Post by quinnten83 on 2008-09-20
> **styfle said:**
> Do you need to know your friend's IP? Tell him to go to [www.whatsmyip.org](www.whatsmyip.org)
Then connect to hisIP:5900

Well that will not work is the friends router is not set to forward the ports.
you can find more information on how to do that here:
[http://portforward.com/routers.htm]("http://portforward.com/routers.htm")
once that is set up,use the public IP adres to connect to her computer.

also I just installed crossloop ([www.crossloop.com](www.crossloop.com)) using wine. I managed to start the program, but i never connected to anyone, it might actually work (wouldn't that be cool?).

---

### Post by faraz_k86 on 2008-09-20
k so what i can gather now is that i have to know her real ip from showip.net.

and that is all i need to connect to her pc?

also as for port forwarding she uses torrents and i followed the guide at portforward.com and opened the port [33457](not exat)

so will this work?

---

### Post by bodhi.zazen on 2008-09-21
nope

you need to forward port 5900

If you are going over the internet, and not a LAN, you should look at securing the connection either by tunneling over ssh or FreeNX

[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

---

### Post by faraz_k86 on 2008-09-26
what about this option.

when i went to remote descktop there is an option saying.

> Users can view your desktop by using this command

-vncviewer XXXX-laptop-0


so my friend is also using linux so if i find out this command of hers, where should i enter it? in the terminal?

---

### Post by anewguy on 2008-09-26
Follow Bohdi's advice - she must set port forwarding on port 5900 on her router.  Then, doing as he also suggested, install vnc or tinyvnc.  there is a readme file with that package that explains everything you need to do.  I have done this myself with no problems, so just download/install vnc or tinyvnc and follow the readme.  Unless you have administrative access to her router (and assuming you are both adults and the router is hers, not something like her Dad's) you could set the port forwarding for port 5900 but remember it MUST be on her router.

---

### Post by Peter09 on 2008-09-26
there is a way to do it that does not require your friend to open his/her ports, but you will need to open yours.

She/He will need to issue the command in a terminal (you can make a launcher for it)

```
x11vnc -noxdamage -connect <your ip address> -bg
```

Before that command, you have to issue the command on your machine

```
vncviewer -listen
```

You will need to open your router port to forward 5500 to your machine.

This is a handy way of doing it because the person that you are supporting does not need to have an open firewall port.

---

### Post by I Use Dial on 2008-09-26
There must be a Linux equivalent to Windows Remote Connection.  If you haven't used Remote Connection, it's really a dream.  You create a file on the host computer using the program (it's a standard Windows program) and send it to the (Windows) client.  The client opens the program and logs into your computer.  It has time limits, passwords, and access limitations, so it's really quite safe.

I tried googling to find a Linux equivalent with no success.

---

### Post by Gabix on 2008-09-27
And what about a much simpler thing, just having the remote desktop activated ONLY (and I want ONLY) in my lan, How can I do that?

---

### Post by Peter09 on 2008-09-27
To do that you make sure that your router does not pass the protocol for the remote desktop, block the port that your going to use for remote desktop from passing through your router.

---

