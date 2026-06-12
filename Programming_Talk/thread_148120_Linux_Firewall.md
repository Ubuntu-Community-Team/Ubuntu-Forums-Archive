---
title: "Linux Firewall"
date: 2006-03-21
forum: Programming Talk
---

### Post by 4dz0 on 2006-03-21
I am currently planning my final year project at university and I'd like some opinions on my initial idea. I do have to stress that this idea is extremely primitive and I have barely begun, what I'd really like is to have some comments from you guys that I can use to decide whether to proceed.

I'm looking to create an interactive firewall, the exact nature of the firewall is yet to be determined but my main aim is to create a user friendly application that can help new users to Linux configure network access with maximum ease. By interactive I mean a firewall that is restrictive by default, allowing only those applications and services network access through interactively granting permissions.

What I'd really like at this initial stage is some opinions, on whether Linux actually needs another firewall, and some features that you'd like to see. I'd also like some advice on what is currently available, what firewall you use, and the things you like/dislike about it.

I'd really like people to be honest in there opinion, I'm not tied down to this application and I have pleanty of time, if the idea isn't required amongst Linux users then there is little point in proceeding.

I've asked a lot of questions here so comments on any would be great.

Thanks.

---

### Post by JamesNorris on 2006-03-21
Well considering that most distros want you to use iptables as your firewall, I can say that *another* firewall might not be a bad idea. 

I use firestarter, and it took me a whole ubuntu release cycle (if not more, cos I had this problem when I starter with Horay and all through Breezy) to figure out that firestarter was blocking incoming connections from my LAN.

DHCP won't run propperly on my network without firestarter running, so a nice, easy to configure firewall that will also run my DHCP server propperly would be nice, IMO

---

### Post by Stealth on 2006-03-21
Well, under Windows I've used Sygate Personal Firewall, and Kerio Personal Firewall. Main thing I like about them is the simplicity of their interfaces and such.

[LIST]
[*]When a new application wants to access the internet, ask me to allow, allow once, or not allow.
[*]If I'm getting some direct connection coming, ask me the same thing
[*]When I open the main interface, first thing I wanna see is a list of programs accessing the internet, and specific stats on their current upload and download.
[*]If I'm having too many problems, I want a right click menu to completely disable temporarily.
[*]Be smart, for instance, if I'm running a torrent, and I open main interface, don't show me or try to instantly display ALL the IPs of the people I'm connected to. (Kerio tries to do this, and freezes)
[*]Look good
[*]Work with my network. I should have an option to allow compelte incoming/outgoing connections within my trusted computers. Be it via range (192.168.x.x-y.y) or by specific IPs.
[/LIST]

---

### Post by 4dz0 on 2006-03-21
Thanks for the replies, much appreciated. I'm going to repost this thread in a less technical forum to hopefully guage a wider concensus.

---

### Post by joshuapurcell on 2006-03-22
If you were going to work on a firewall solution for Linux, I would limit it to making the frontend functional like the above recommendations while the backen being nothing but iptables. iptables would be very hard to improve on in the area of functionality, but ease of use (i.e. frontend) can definitely be improved upon, and I think that's pretty much what you are seeming to focus on anyway.

I like the idea of having a firewall GUI that is limited to the system tray default, and with a click of the icon you pull up the display showing information and config options. Firestarter goes a very long way in doing everything I want (including system tray functionality), but one thing it doesn't do is pop up a window (like ZoneAlarm does in Windows) telling you more information about what is going on and attempts to get some interaction if needed. That's a function that some people really like in a firewall, but at the same time some people like the simplicity of creating rules and having those rules followed without being asked if you want to break them whenever something new happens. I guess the best way to differentiate your frontend from others would be to have the pop-up windows and treat like a more complete ZoneAlarm-like replacement for Linux.

---

### Post by Darkness3477 on 2006-03-22
[QUOTE=Stealth]Well, under Windows I've used Sygate Personal Firewall, and Kerio Personal Firewall. Main thing I like about them is the simplicity of their interfaces and such.

[LIST]
[*]When a new application wants to access the internet, ask me to allow, allow once, or not allow.
[*]If I'm getting some direct connection coming, ask me the same thing
[*]When I open the main interface, first thing I wanna see is a list of programs accessing the internet, and specific stats on their current upload and download.
[*]If I'm having too many problems, I want a right click menu to completely disable temporarily.
[*]Be smart, for instance, if I'm running a torrent, and I open main interface, don't show me or try to instantly display ALL the IPs of the people I'm connected to. (Kerio tries to do this, and freezes)
[*]Look good
[*]Work with my network. I should have an option to allow compelte incoming/outgoing connections within my trusted computers. Be it via range (192.168.x.x-y.y) or by specific IPs.
[/LIST][/QUOTE]

I agree completely with alot of those dot points. Generally, firewalls for windows are alot easier to use, and seem to be very up-front with the information you are looking for. 

I've used three firewalls, Sygate (I loved it, as it was free and worked through a few hacking attempts -most likely script kiddies.), ZoneLabs and Norton Personal Fireall. I have liked all except for Norton, which didn't do any wonders for my PC. The reason why I have liked them, though, is that they do there job well (I find that most firewalls work fairly well), but more importantly they are EASY to configure, and are EASY to find all the information you would ever want. They have a list of all programs running, ask you when allows something, and are just user friendly in almost everyway.

If you could make a program that works nearly as well at representing the information about what is allowed and what isn't, easy configuration and everything the the user I qouted said, I would definately drop friestarter and change to your firewall.

So, in my most gracious opinion, there would be a few people (At least me, anyway) that would use your program. Also, I have always wanted to program a Firewall when I got good enough too, as I think it would be really cool. So, I think your teacher(s)/Professor(s), would love the idea.

Good luck, and I hope that whatever you chose to do, that you get good marks for it -at least the marks you deserve!

---

### Post by 4dz0 on 2006-03-22
> Originally Posted by **joshuapurcell**
iptables would be very hard to improve on in the area of functionality

This is true, it's something I need to consider, why reinvent the wheel if the required functionality is readily available in iptables.

---

### Post by StrikeRTM on 2006-03-22
I've been using Zone Alarm in windows ever since I first connected my computer to internet, wich was about 4 years ago.

What I liked about ZA:

1) Alerts can be turned off, so they do not bother me when watching fullscreen movies or playing games. I realy hate when alert pops out and game gets minimized and even more if it crashes afterwards.

2) ZA has an option to allow all outgoing connections without restrictions while blocking incoming hacks and stuff. This realy helps because again the alerts do not bug me as everything is allowed to go out. On windows some might find it troubling, but Linux is safer anyway and it is optional, so if you dotn want it, you dont have to use it.

*ZA doesnt have this option, but maybe it should be available in your firewall software -- bandwith limiter, something similar to that of the Netlimiter wich is available for windows users.

*Some good title, like PowerWall ;).

If something else some's in my mind I'll add it.

---

### Post by 4dz0 on 2006-03-22
bump

---

### Post by djlosch on 2006-04-04
my ubuntu box serves as a multifunction box (router, webserver, fileserver).  here's my setup:

internet
|
eth1 (dhcp from ISP)
|
ubuntubox
|
eth0 (static assigned)
|
switch
| | | | |
workstations (dchp assigned by ubuntubox)

for my routing, i use guidedog (frontend to route/iptables)
for my port blocking/firewall, i use guarddog (frontend to iptables)
for my dhcp/dns, i use dnsmasq (dchp assigner with dns forwarder)

i had been using firestarter for a little over a year before i set up the routing, but for some reason firestarter didnt like dnsmasq, and im not about to set up bind for this simple little network.

all 3 apps (guidedog, guarddog, dnsmasq) are in the repos listed on ubuntuguide (but for breezy).  guarddog is pretty intuitive (although firestarter made more sense at first).  i didn't realize i had to add the lan zone in guarddog which is why i couldnt figure out for the life of me the concept behind guarddog.  once i added the lan zone, it's SO intuitive.  apparently that was in the docs so i should have rtfm

---

