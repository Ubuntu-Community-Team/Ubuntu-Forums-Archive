---
title: "SSH through the internet"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by RavUn on 2008-07-09
I'm able to ssh into a computer that's on the same network. I'd like to know what IP address to use when doing SSH over the internet.  I want to be able to access files while I'm at work.

Do I use the IP address shown in ifconfig (192.xxx.xxx.xxx) or do I use the one that shows at [www.whatismyipaddress.com?](www.whatismyipaddress.com?)  The address from whatismyipaddress.com takes me to my router.. I figured this is the one I want to use and I set up my router to listen on port 22 and forward to my 192.xxx.xxx.xxx IP address.

I can use the 192.x.x.x address when I'm on the same network but I haven't been able to test outside of the network yet.  I tried using my external IP address and it just says "connection refused".



Also, when I ssh in I try to run vncviewer and it says "unable to open display""".  Does anyone know what causes this?  I type vncviewer when I'm ssh'd in and it says that instantly.  If I'm not ssh'd in and type vncviewer it'll ask for the host and act like it'll connect but then says unable to open display.  I am able to use vncviewer to view my own computer (it just opens multiple instances of itself over and over) so I figure vncviewer is working.  Do I have some X configuration screwed or not installed, possibly?

Thanks for any info.  I've been working on this and searching for a couple of days now and this is as far as I've gotten.  I went to work this morning thinking I'd be able to ssh in only to realize I hadn't done the port forwarding.  Now I want to make sure I can do it tomorrow.

---

### Post by iansane on 2008-07-09
do you have a static ip? I think you would have to have that or a dyndns address so dns servers can find your home computer on the internet

yeah you'll need to set up dyndns on your router if it is capable and then forward the port from it to your 192.xxx.xxx.xxx

---

### Post by llamakc on 2008-07-09
> **iansane said:**
> do you have a static ip? I think you would have to have that or a dyndns address so dns servers can find your home computer on the internet

yeah you'll need to set up dyndns on your router if it is capable and then forward the port from it to your 192.xxx.xxx.xxx

If the OP wants to connect via IP they'll not have to worry about DNS at all, unless their IP regularly rotates. In that case, dyndns is a wonderful suggestion.

OP: dependent on your router, you want to 'port forward' port 22 to your 192.xxx IP address USING THE ROUTER'S configuration page. Then from outside the home LAN you should be able to ssh into your machine.

---

### Post by cariboo on 2008-07-09
You have to know your router ip address, and then setup port fowarding to your computer. You should setup a static ip address for the computer you forwarding a port to. See this for running graphical apps with ssh:

[http://www.cyberciti.biz/tips/running-x-window-graphical-application-over-ssh-session.html](http://www.cyberciti.biz/tips/running-x-window-graphical-application-over-ssh-session.html)

They use a sever as an example on this page, but it will work for any computer.

Jim

---

### Post by framinglory on 2008-07-09
use the ip address from [http://www.whatismyipaddress.com/](http://www.whatismyipaddress.com/)
that is your external ip, and if you are outside of your network you will need to use that to connect to your computer at home. You can only use a local ip (the 192.xxx.xxx.xxx) if you are on the same network as the machine you wish to connect to. 

And like Cariboo mentioned above, you should set your router to always give your machine at home the same ip. (you'll want to use dhcp reservation most likely)

As for not being able to connect to your machine by using your external ip while on the same network, i have heard that some routers don't like something on the network trying to connect to the same network externally (i.e through the ip from [http://www.whatismyipaddress.com/](http://www.whatismyipaddress.com/)), so if you need to connect while on the same network, do what you're doing now and just use the 192.xxx.xxx.xxx address, otherwise you need the external ip.

Next time you get a chance, try to connect using your external ip while on another network. If you can't connect, then there is something wrong with your port forwarding rules most likely.

---

### Post by issih on 2008-07-09
Your internal IP addresses (192.xxxxxxxxxxx) are just that, internal to your network, every pc on your network then connects to the router, which bridges your internal network to the internet. It does this by maintaining two ip addresses an internal one and an external one. The external one is the only one accessible from the internet.

If that external address is assigned via dhcp by your ISP, it can change regularly, and you won't be able to guess it. In that case you need to set up a dynamic dns service like dyndns which is basically a web service that keeps track of this changing ip address so you can access it more easily. If your ISP has given you a static IP (rare) then this isn't necessary.

You will need to set up port forwarding (22 for ssh) so that the router knows where to send the incoming connection.

That should be about all that is necessary to be able to ssh into your box from the internet, just make sure you have a reasonably strong password set up...

Now the vnc issue, I think you may be trying to do things a bit wrong here.

The "could not open display" message appears ebcause you are logged in to a terminal which doesn't have an associated X display. When you open a terminal from the gui, the X display (your screen) is automatically associated with it, so any X programs run from that terminal open on your screen.

If instead you use a proper console (e.g. hit ctrl alt F1) or ssh in then the display isn't associated with the terminal, and the computer doesn't know where to try and run the X program. There are ways around this, but that doesn't matter right now.

Plain ssh is intended for console use. if instead you use "ssh -X" then the system tries to use X11 forwarding. For example I could ssh -X into my desktop box from my laptop then run rhythmbox in the terminal, and the gui would appear on my laptop screen. however, I am still controlling the desktop's hardware, so the sound will come from the desktop speakers. I hope that makes sense. Being able to do this requires the computer you are working at to have an X server (i.e. be a linux or mac computer).

So that is why you get can't open display, the terminal has no idea where to open the program. I am however not sure you have quite understood how vncviewer is meant to be used however....

sshing into a box and then running vncviewer seems very odd.

Normally the setup would be to have one box running vncserver, and another running vncviewer which connects to the server, ssh isn't required at all.

The common usage of ssh in relation to vnc is to make the connection secure, as the vnc protocol is easily eavesdropped upon.

A typical scenario would be like this:

Server box set up with vncserver running and outputting on a known port (e.g. if vnc desktop is 0, port is 5900, 1 -> 5901 etc). The machine is however set up so the only port open to the outside world is 22 (ssh).

Remote pc then ssh's into server, and forwards the port to a local one, assuming the vnc desktop was 45 you'd use something like:

```
ssh -L 5901:serverName:5945 RoutersIPAddress
``` 

this step can also be achieved using something like putty in a windows environment.

This now tunnels all data coming out of port 5945 on the server through the ssh tunnel to port 5901 on the connecting machine.

You then run vncviewer connecting to 5901 on localhost and you will have a secure connection to your remote desktop.

Hope you followed all that :s

---

### Post by kevdog on 2008-07-10
If you cut and paste the following into the terminal it will show you your external IP address that the "rest of the world" sees:

```
wget -q -O - http://showmyip.com | grep -m 1 'IP' | awk '{ print $8 }'
```

---

### Post by txcrackers on 2008-07-10
Actually, you might want to use a different port on your router and redirect that to port 22 on your internal machine. There's a bunch of brute-force SSH attack scripts floating around and they all just hammer away at port 22, hoping you're an absolute idiot and have one of the username/password combinations embedded in the script(s). Doing this also keeps your security log files cleaner and easier to detect a *real* attempt at breaking and entering.

```
ssh -p 12345 111.222.333.444
``` where "12345" is the port number you've chosen.

You can also set up a DynDNS "freebie" account so you don't have to keep remembering your external IP address.

---

### Post by RavUn on 2008-07-10
Ok... I have the DynDNS setup.  I added a host and clicked the "use auto-detected address" and saved that.  I'm at work and tried to connect and it tries to connect for a while then says "connection timed out".

I assume it's an issue with the router.  I'll check my log in /var/log but I have to wait until I get home... 8 more hours.

---

### Post by kevdog on 2008-07-10
Is your router or computer using a client to update your dynamic dns address?  You might want to dns lookup to see the ip address associated with your dyndns name, and then try to ping the machine by ip address rather than name, in case there is some dns lookup issue. Likely however your server ip address has changed.

---

### Post by RavUn on 2008-07-10
Ahh.. I didn't realize you had to use an update client to update the address... I thought I just put it in dyndns and it somehow did it with magic.  I tried pinging it and it times out.  I'll have to setup the update client when I get home.

I did the dns lookup and the IP address I put into dyndns is associated with the domain.  The server IP must have changed.  I'll check it out.

Thanks a lot.  I'm taking baby steps but hopefully will figure it out.

---

### Post by issih on 2008-07-10
Make sure to check your router config first, some of them have dynamic dns clients built in, which means you don't have to fiddle with getting the linux client running on your pc...It's worth looking first.

---

### Post by RavUn on 2008-07-10
Well, my external IP address is still the same as it was yesterday.  I don't know why I couldn't ping or reach it.  Could it be something at work?  I should be able to still ping it from work I imagine.

---

### Post by Xerp on 2008-07-10
Ping and SSH are different. A firewall will most likely stop ping, but may not stop SSH. So, if you can't ping a host it doesn't mean you can't SSH to it. How is your remote firewall configured? Which firewall is it (iptables)? How specifically have you set up NAT? Connection timeout errors normally mean your packets aren't getting through :)

---

### Post by Inxsible on 2008-07-10
I am currently having the same issue in that, that I am able to ssh when on my own network. But cannot connect over the internet.

I get the same connection timed out error. 

Watching this thread for additional replies and solutions.

---

### Post by RavUn on 2008-07-11
hmmmm... I forgot I installed ipblock a long time ago.  I checked the status and it's running, so maybe that's it.  I've never messed with iptables before, though.  Networking is not something I'm too familiar with.  I was just hoping to access files from work.

---

### Post by RavUn on 2008-07-11
I have 2 computers on my network running Ubuntu and they both have the same IP address in ifconfig.  How can I change this?  The windows computer has a different IP address but these 2 have the same address.

EDIT: never mind, I'm an idiot.  I was ssh'd in at the time :P

---

### Post by RavUn on 2008-07-14
I've tried sshing into both of my linux computers from an out-of-network windows laptop.  I tried from work and on a laptop using someone else's wireless in the neighborhood.  In all instances it says "connection timed out".  

One of my linux computers I just installed Ubuntu to test it but I don't remember configuring anything on it so it shouldn't be setup like my other computer as far as network settings would go.  This leads me to believe there's an issue with the router.  It's a linksys 54G wireless router.  I've done the port forwarding and I even tried disabling the firewall on the router setup screen.  There's also a box to block anonymous requests that I unchecked and it still didn't work.

I tried connecting without the router but for some reason that wouldn't work.  I plug the ethernet cable straight into my cable modem and on my computer it says sending/receiving packets but I cannot connect to skype or internet.  This is turning into a mess!  Does it seem like a router issue?

---

