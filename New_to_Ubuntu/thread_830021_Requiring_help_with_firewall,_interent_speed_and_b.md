---
title: "Requiring help with firewall, interent speed and bittorrent. I'm lost!"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by Tom--d on 2008-06-15
I've been using ubuntu for a while now and I love it. 
The only thing I've never got to grip was a firewall.

I have ufw enabled and port 80 and 22 are on 'allow' I know port 80 is for Internet and 22 for ssh. But really. I still dont know what allow means. 

Also, I think my internet is slow at responding. Not at downloading, once its downloading a file, the speeds are high. but Just general surfing the internet is slow. 

Many every link I click has a delay. Gnome-look.org is slow for me. Ubuntuforums can be slow. 
How can I speed things up?


Another thing, bittorent. Im using Transmission. It says that the port its using is closed. What does that mean? But then, i can still downlaod through transmission. Im lost :S
The most important thing is, how do I speed up torrents? 

And if ufw, if I deny port 80, I STILL can surf the web. Again, im lost.

but on shields up, they say that ALL my ports are stealth. And again, Im lost.

O yes, Firestarter doesnt work on my computer. it loads up on start up but with errors saying wlan0 is not there. then firewall turns off. then my ndiswrapper is loaded and then wlan0 is there. but firestarter doesnt see that anymore.

on the other hand, ufw enables the firewall at start up :)

Another thing, do I even need a firewall?

---

### Post by Tom--d on 2008-06-15
Please, anyone?

---

### Post by hyper_ch on 2008-06-15
(1) are you sure you need a firewall? Normally you don't any or rather you should configure the firewall on your router.

(2) if you only allow port 80 and port 22 then you can't use torrent as they use other ports and those are blocked - as you say...

---

### Post by Tom--d on 2008-06-15
I see..

I do not know about my router, at all. 

But I have now come into a problem, Transmission has said that all my ports are closed. I need one open for torrents?

---

### Post by Tom--d on 2008-06-15
Right, I know what the problem is with Transmission.

I need the port open for it, at the moment, its closed. I don't know what. And with ufw, that port is set to allow. but it is still closed :S

---

### Post by wariskampar on 2008-06-15
I dont know about Transmission because I use Deluge which I'm very much satisfy with the speed. Maybe you can try my setting though;
1) Setup Static IP (i use default Network Manager to do that) 
2) Create new policy for torrent in Firestarter (GUI for ufw) - the steps are pretty straight forward. 
3) Setup Router to open torrent port (as configured in Network Manager) and you will need to use Static IP here
4) Test open port in Deluge (in your case Transmission) 

I dont know these info help but hope it might shed some light. Success!

---

### Post by Tom--d on 2008-06-15
Firestarter is the GUI of iptables
Ufw (Ubuntufirewall) is the command line of iptables.

Firestarter doesnt work on my laptop very well.

---

### Post by wariskampar on 2008-06-16
oopp! i'm so newbie!:) BTW, i just found out that Deluge work perfectly without Static IP, Event Policy and Router Setup. Maybe you can try

---

### Post by hyper_ch on 2008-06-16
I would deactivate firestarter, uwf, ... completel and set iptables back to its original state. I doubt that you need to have a configured firewall.

---

### Post by Tom--d on 2008-06-16
> **hyper_ch said:**
> I would deactivate firestarter, uwf, ... completel and set iptables back to its original state. I doubt that you need to have a configured firewall.

Why?

---

### Post by hyper_ch on 2008-06-16
why do you think you need it?

---

### Post by Pjotr123 on 2008-06-16
> **Tom--d said:**
> Why?

Because in a default installation of Ubuntu, there are no listening services. An attacker can't do anything with an open port, when there's no listening service behind it.
[http://ubuntutip.googlepages.com/security](http://ubuntutip.googlepages.com/security)

---

### Post by cariboo on 2008-06-16
In a bone stock installation the only port that is open is 631 which is used by cups. Cups is the print server.

Jim

---

### Post by Tom--d on 2008-06-16
> **hyper_ch said:**
> why do you think you need it?

I don't know really.
Should I have one?

I have something which is listening on a port and i dont know what it is. 
How can i find out what it is?

Edit: Sorted that.


I have no firewall running. 
And bittorrent has stopped working :(
This is what it says:

"Problem connecting to tracker - <urlopen error (111, 'Connection refused')>

How do i sort that out and what happened?

---

### Post by Tom--d on 2008-06-16
> **cariboo907 said:**
> In a bone stock installation the only port that is open is 631 which is used by cups. Cups is the print server.

Jim


Just found that out ;)
Thanks :)

---

### Post by ChildOfMana on 2008-06-16
Hi,

I'm not going to get into the whole firewalling debate as I know very little about that myself.

As for your question regarding ports though I may be able to help.

Transmission requires port 51413 to be open. In order to 'open' this port (make it available to the application) you need to forward it through your router.

The type of router you're using will very much determine how you go about this, but generally speaking you need to log in to your router's configuration page by typing something along the lines of 192.168.1.1 into the address bar of your web browser (again, this will vary depending on your router but most default to 192.168.1.1). Then you need to find the section for "Port Range Forwarding" and tell the router to forward port 51413 to the IP address of your computer.

If you have more than one device connected to your router then it help to set up a static IP for your computer.

For a more comprehensive overview of all things port related go to [www.portforward.com](www.portforward.com)

They also have a large range of router-specific tutorials to help you.

If you need help with setting up a static IP post back here and I'll see if I can help you.

---

### Post by Tom--d on 2008-06-16
Yeah, but torrents use to work all the time. Now its just stopped! wHy?

---

### Post by ChildOfMana on 2008-06-16
Is it just one torrent in particular that has stopped working or have they ALL stopped?

Are all the torrents from the same tracker, or from a range of trackers?

---

### Post by Tom--d on 2008-06-16
A range of trackers. 

Its just stopped. 
No firewall loaded either (that i know of)

---

### Post by ChildOfMana on 2008-06-16
Strange. Have you tried using different clients?

---

### Post by Tom--d on 2008-06-16
Yep.

Still nothing.
I dont know what wrong with it

---

### Post by ChildOfMana on 2008-06-16
Can you think of anything you've done in between your torrents working and not working?

Any hardware/software you've installed for example?

You mention you've used Firestarter - was this in between your torrents working and not?

---

### Post by Tom--d on 2008-06-16
No, but I have found something.

I disabled ufw. but when starting up it says its enabled :s 
maybe thats it. 
I will uninstall ufw and see what happenes then.

---

### Post by ChildOfMana on 2008-06-16
Like I said originally I don't know much about firewalling in Linux but, as far as I understand it (which isn't very far), using Firestarter or ufw writes rules for the underlying iptables.

If you uninstall them I'm not sure if that reverts the iptables rules back to default or not.

If it doesn't then that could be your problem.

But that's just a wild shot in the dark - you're probably better off taking advice from someone far more experienced/knowledgeable about Linux firewalling than me!

---

### Post by Pjotr123 on 2008-06-16
> **cariboo907 said:**
> In a bone stock installation the only port that is open is 631 which is used by cups. Cups is the print server.

Jim

My previous post wasn't entirely accurate: in a default installation, there are no listening services behind those ports that are exposed to the internet.  :-)

---

### Post by hyper_ch on 2008-06-17
uninstallation of firestarter won't reverse rules back to their original state.

---

### Post by Tom--d on 2008-06-17
I found out it is a tracker problem. Not me. 

I have solved this problem. 

But, do I need a firewall enabled (ufw) when using bittorrent as it listens on a port?
Is it advised to?

---

### Post by ChildOfMana on 2008-06-17
I don't know if you *need* to or not, but I suppose it can't hurt (as long as you don't mess with the rules too much).

I've been using ufw for a while now across two Ubuntu installations and I've never had a problem.

---

### Post by hyper_ch on 2008-06-17
> **ChildOfMana said:**
> I don't know if you *need* to or not, but I suppose it can't hurt (as long as you don't mess with the rules too much)
enabling it does hurt too much... it blocks just about everything ;)

---

### Post by bodhi.zazen on 2008-06-17
> **Tom--d said:**
> I found out it is a tracker problem. Not me. 

I have solved this problem. 

But, do I need a firewall enabled (ufw) when using bittorrent as it listens on a port?
Is it advised to?

> **ChildOfMana said:**
> I don't know if you *need* to or not, but I suppose it can't hurt (as long as you don't mess with the rules too much).

I've been using ufw for a while now across two Ubuntu installations and I've never had a problem.

I think it is best to stop a minute and ask yourself, what is it you are expecting a firewall to do for you ? :lolflag:

---

### Post by Tom--d on 2008-06-17
> **bodhi.zazen said:**
> I think it is best to stop a minute and ask yourself, what is it you are expecting a firewall to do for you ? :lolflag:

Well, I came from Windows. And I'm use to having a Firewall xD

I found out the problem now.
Also, yeah, it won't hurt to have one running, will it?

Like, ufw, its simple. I know what I'm doing :)

---

### Post by ChildOfMana on 2008-06-17
> I think it is best to stop a minute and ask yourself, what is it you are expecting a firewall to do for you ?

Good point.

Yeah I came from Windows too. Only been using Linux about a year or so but think I've just got that whole 'Windows NEEDS security... and lots of it' thing ingrained into me.

---

### Post by Tom--d on 2008-06-17
> **ChildOfMana said:**
> Good point.

Yeah I came from Windows too. Only been using Linux about a year or so but think I've just got that whole 'Windows NEEDS security... and lots of it' thing ingrained into me.

Same.


I'm just not used to having no firewall. 

I've got used to no anti-virus now :D

But after all, it won't hurt having a firewall there.

---

### Post by bodhi.zazen on 2008-06-17
LOL, that is why I asked. On Windows there are a number of servers running in the background waiting to accept connections.

This is NOT true of a default Ubuntu installation.

In addition most people use routers nowadays, so your router also acts as a firewall.

In the case of torrents, you are installing a server and you want it to connect to peers (this is how torrents work). Yes, torrents are thus a (small) security risk ...

Knowing what you want from a firewall helps configure it (ie allowing public servers and protecting private servers for example).

As you may be new to Ubuntu you may want to look here :

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812")

---

### Post by hyper_ch on 2008-06-17
> **bodhi.zazen said:**
> In addition most people use routers nowadays, so your router also acts as a firewall.

Don't forget that on windows you don't only want to protect you from incoming connections but also from outgoing (malware, adware, secret transmissions to software producers, ....)

---

### Post by Tom--d on 2008-06-17
> **bodhi.zazen said:**
> On Windows there are a number of servers running in the background waiting to accept connections.

Out of interest, do you know what kind of services these are?

---

### Post by bodhi.zazen on 2008-06-17
> **Tom--d said:**
> Out of interest, do you know what kind of services these are?

Depends on version of windows, search with google ...

[http://www.jasonn.com/turning_off_unnecessary_services_on_windows_xp](http://www.jasonn.com/turning_off_unnecessary_services_on_windows_xp)

[http://www.ss64.com/ntsyntax/services.html](http://www.ss64.com/ntsyntax/services.html)

As you can see, long, long list. This is why you *need* a firewall on Windows.

---

### Post by bodhi.zazen on 2008-06-17
> **hyper_ch said:**
> Don't forget that on windows you don't only want to protect you from incoming connections but also from outgoing (malware, adware, secret transmissions to software producers, ....)

Good points. I lump those issues into "malware" rather then "firewall" as most people set up their firewall to allow all outgoing connections (and block unwanted incoming connections). Routers, for example, act this way by default.

---

