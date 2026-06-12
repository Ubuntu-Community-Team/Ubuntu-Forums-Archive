---
title: "4 computers, and not one can do a simple task..."
date: 2008-09-03
forum: New to Ubuntu
---

### Post by hyperhopper on 2008-09-03
Hello again. I have successfully run an ethernet wire to one of my ubuntu machines and kubuntu machines, but whenever i go to play any online game,(cube2 wormux open arena scorched earth) it seems as if the game cannot connect to the internet. I either get server rejected connection (wormux) no servers found (open arena) many servers with incompatible version (scorched earth) or servers that i cannot connect to (sauerbaten).
can anybody help me? thank you in advance

p.s.

how come for so long nobody has andswered the other thread?

---

### Post by Whiffle on 2008-09-03
how are they connected to the internet?

---

### Post by hyperhopper on 2008-09-03
comp--->router--->modem--->internet


yes, I let the router access the correct ports....

---

### Post by nateperson on 2008-09-03
Are you accessing this forum from one of those 4 computers?

---

### Post by hyperhopper on 2008-09-03
yes, and all have the same problem

---

### Post by Joeb454 on 2008-09-03
> **hyperhopper said:**
> bump

Please don't bump so often. Despite how annoying your issue may be, other users want their problems solved too.

Just think what would happen if everybody bumped their threads every 6-8 minutes...As a general rule, we encourage bumping once every 24 hours at most

---

### Post by hyperhopper on 2008-09-03
whups---sorry

---

### Post by steveneddy on 2008-09-03
> **Joeb454 said:**
> Please don't bump so often. 

+1

I hate reading threads and seeing one or two bumps, but 6 in less than an hour?

Impatient?

---

### Post by hyperhopper on 2008-09-03
lol--sorry--ever since second grade doctor said I had off-the-chart adhd

200mg of adderal or riddalyn doesn't work on me

---

### Post by Joeb454 on 2008-09-03
It's fine, I'm moving your bumps to the [Bump Thread]("http://ubuntuforums.org/showthread.php?t=520091") :) Feel free to bump that as often as you like :)

---

### Post by hyperhopper on 2008-09-03
thanks!


*bump thread here I come!*

---

### Post by hyperhopper on 2008-09-04
can I bump or is it too soon?

---

### Post by Corrupt3d on 2008-09-04
What type of error message are you getting?
In Wormux, Do you get, 
"Error: Unable to contact index server to search an internet game"

I'm pretty sure its the server and that your internet-connection is fine.

---

### Post by halitech on 2008-09-04
> **hyperhopper said:**
> comp--->router--->modem--->internet


yes, I let the router access the correct ports....

I know you say you have let the router access to the correct ports but if all 4 systems have the same issue and you can get online with them and do other things, then it sounds to me like an issue with the router.

go here: [http://portforward.com/routers.htm](http://portforward.com/routers.htm)

find your router and see if it can help you set everything up correctly

---

### Post by hyperhopper on 2008-09-04
> **halitech said:**
> I know you say you have let the router access to the correct ports but if all 4 systems have the same issue and you can get online with them and do other things, then it sounds to me like an issue with the router.

go here: [http://portforward.com/routers.htm](http://portforward.com/routers.htm)

find your router and see if it can help you set everything up correctly
I tried already, and the error for wormux is (server rejected connection)

but it seems odd that EVERY online game has a problem, I doubt that sauerbaten or schorched 3d would have problems....

---

### Post by halitech on 2008-09-04
> **hyperhopper said:**
> I tried already, and the error for wormux is (server rejected connection)

but it seems odd that EVERY online game has a problem, I doubt that sauerbaten or schorched 3d would have problems....

seems odd that all 4 of your systems do the same thing as well. to eliminate the router as a possible problem, can you hook 1 computer direct to your modem and see if you can play the game that way?

---

### Post by hyperhopper on 2008-09-04
tried that already, and it didnt play... meaning the problem is the modem---is it just me or did I say that already?

---

### Post by halitech on 2008-09-04
sorry, I misread the part about running the line to the computers, thought you meant you had gone wired instead of wireless. Are all of the using the same version with different desktops installed or are some 7.10, 8.04, 7.04?

---

### Post by hyperhopper on 2008-09-04
ummmmmmmmmmmmmmmmmmmmmmmmmmmm
I AM WIRED!!!!!
LOL

sorry, all are 8.04 but one of them is Kubuntu

---

### Post by hyperhopper on 2008-09-05
bump-- ok I need to try any new Ideas


I am desperate

---

### Post by alzie on 2008-09-05
I think this may be the soloution : [http://www.wormux.org/blog/index.php](http://www.wormux.org/blog/index.php)

Don"t panic... after the first paragraph it turns to english.

I hope this helps.

---

### Post by hyperhopper on 2008-09-05
I installed it- but where is it and how can I run it--- the new final version I mean--I deleted the old one first

---

### Post by Shazaam on 2008-09-05
Try...
```
wormux
```
in the terminal.

---

### Post by hyperhopper on 2008-09-05
I did lol---that would be for the one you would get from synaptic---it said try sudo aptget install wormux--because here I manually downloaded a different file and installed it with gdebi

---

### Post by crjackson on 2008-09-05
Have you installed Firestarter or any other type of firewall configuration packages?

---

### Post by hyperhopper on 2008-09-05
nope--havent touched any settings.....
no firewalls- portblockers--nada

---

### Post by crjackson on 2008-09-05
Can you play networked games under windows?

---

### Post by hyperhopper on 2008-09-05
I dont know!

---

### Post by crjackson on 2008-09-05
Well, if you installed some older versions of the games, I would enable all the repositories (including backports) update everything and try again.

---

### Post by hyperhopper on 2008-09-05
tried that already----no go

---

### Post by wolfen69 on 2008-09-05
did you try simply resetting the router? unplug it for a minute and try again. i would also do the same to the modem. if it is a cable modem, unplug *everything* from it.

---

### Post by Shazaam on 2008-09-05
I think wolfen69 just gave us a hint.
Hyperhopper...
Your modem, is it an ethernet type with multiple ports? If it is, have you set up any port-forwarding in the setup page?

---

### Post by hyperhopper on 2008-09-06
OK--- I treid reseting everything, no go----



UPDATE!!!!!!!!

network games work on windows!

Idont know exactly which ones but warsaw does!!!!

---

### Post by alzie on 2008-09-07
I'm still searching, (I'm not a gamer).  I did find a post regarding "ut2004 connection problems".  Anyhow, the solution in that thread was to set the permissions on the game folder (ut2004 in this case) to read/write and it solved his problem.

It might be worth checking your permissions.

---

### Post by hyperhopper on 2008-09-07
where do I find the folder fo rthe game?

---

### Post by starcannon on 2008-09-07
If your modem is also a router, and your pushing it through a router:

modem/router-->router-->computers 

It may be possible your dealing with double nat, and ports being forwarded on one router but not the other.

Most router/modem combo units have an ability to be bridged, this pretty much turns it into a straight up modem, and then let your router do nat and routing.

What Brand/Model is your modem, what Brand/Model is your router? I'll look up the manuals on them and see if there is anything there.

---

### Post by hyperhopper on 2008-09-07
the router is linksys model # WRT54GS version 6 wireless g broadband adapter 2.4 ghz

Ill check modem

---

### Post by hyperhopper on 2008-09-07
sbv1520 motorola surfboard cable modem

---

### Post by hyperhopper on 2008-09-07
p.s.--im a linux noob---any good games that are non-multiplayer that I can play while trying to resolve this problem that make me think?

---

### Post by hyperhopper on 2008-09-09
bump

---

### Post by hyperhopper on 2008-09-09
bump

---

### Post by steveneddy on 2008-09-09
Stop bumping the thread please.

---

### Post by hyperhopper on 2008-09-09
I have had this problem for two weeks, yet I havent made any progress!!!!!


what am I supposed to do?????

---

### Post by Ripfox on 2008-09-09
Reinstall Ubuntu and dont mess with the defaults. If network games work in Windows and not Ubuntu, sounds like you fiddled around too much with Ubuntu install. Just a guess.

---

### Post by billgoldberg on 2008-09-09
> **hyperhopper said:**
> comp--->router--->modem--->internet


yes, I let the router access the correct ports....

It must be the router or the modem.

Try connecting to the internet via the router without the modem and visa verse.

--

Make sure all the ports are open on the router.

Also install firefaster or ufw (download gufw gui for ufw from internet if you need) too see if your iptables are set up fine (they are by default).

---

### Post by halitech on 2008-09-09
> **hyperhopper said:**
> sbv1520 motorola surfboard cable modem

if that is supposed to be the sbv5120, then it is not a router, it is a cable modem only, specs here: [http://broadband.motorola.com/consumers/products/sb5120/default.asp](http://broadband.motorola.com/consumers/products/sb5120/default.asp)

I have a similar one (sbv5101) and I find occasionally I have to power it completely down, disconnect the ethernet AND the cable wire from it, wait 1 minute then connect the cable wire first, then the power. After I have a connection I then connect the ethernet cable to my router and wait for it to sync up then restart the computers.

Now, not saying this is the problem because you say it does work when you are in windows. I wish I had another answer to help you out but beyond this I don't know.

---

### Post by halitech on 2008-09-09
> **billgoldberg said:**
> It must be the router or the modem.

Try connecting to the internet via the router without the modem and visa verse.

he says he's tried that and it didn't work (if I remember all his posts about this issue)

---

### Post by alzie on 2008-09-09
To check the permissions,click places>computer>filesystem>usr>games

When I check the properties on my games (permissions) it shows the owner as root with read and write access (all the games are the same this way)

I don't know if this is any help to you.

You mention you've had this problem for two weeks,  can you remember anything you may have installed/uninstalled/changed just before your games stopped working properly?

I might give a clue to a game player (sorry I'm, not a gamer)

---

### Post by billgoldberg on 2008-09-09
> **hyperhopper said:**
> I have had this problem for two weeks, yet I havent made any progress!!!!!


what am I supposed to do?????

Do you have any other Operating systems lying around (other linux distro's, windows, mac osx, ...).

See if you can play games online using those OSs. If you can you can be sure it's Ubuntu.

---

Edit: have your tried a hard reset on your router?

I had problems accessing the internet with mine yesterday and only a hard reset fixed the problem.

*(usually you take a pencil or something and press a tiny button on the back for 10-20 seconds, then turn it off and on again. You'll need to enter you ISP details by hand to get an internet connection (usually you can access your routers web interface from [http://192.168.1.1](http://192.168.1.1)))*

---

### Post by halitech on 2008-09-09
> **hyperhopper said:**
> OK--- I treid reseting everything, no go----



UPDATE!!!!!!!!

network games work on windows!

Idont know exactly which ones but warsaw does!!!!

> **billgoldberg said:**
> Do you have any other Operating systems lying around (other linux distro's, windows, mac osx, ...).

See if you can play games online using those OSs. If you can you can be sure it's Ubuntu.



says they work in Windows from a previous post

I can't see it being 4 different computers all at the exact same time having the exact same problem unless he fiddled with the same settings on all 4 systems the exact same way (which is possible I guess)

---

### Post by wolfen69 on 2008-09-09
> **ripfox said:**
> reinstall ubuntu and dont mess with the defaults. If network games work in windows and not ubuntu, sounds like you fiddled around too much with ubuntu install. Just a guess.

+1

---

### Post by halitech on 2008-09-09
hate to say it and I'll probably get flamed for saying it but reinstalling to fix a problem sounds like a windows suggestion to me and I thought we were above windows and windows users mentality. 

Does anyone know what ports are used in the network games? Is there anyway of trying to telnet or ping out through those ports to see if it is the firewall causing the problems? Come on, we are supposed to be better the windows and microsoft, there has to be a way of fixing this problem without a reinstall.

---

### Post by Ripfox on 2008-09-09
> **halitech said:**
> hate to say it and I'll probably get flamed for saying it but reinstalling to fix a problem sounds like a windows suggestion to me and I thought we were above windows and windows users mentality. 

Does anyone know what ports are used in the network games? Is there anyway of trying to telnet or ping out through those ports to see if it is the firewall causing the problems? Come on, we are supposed to be better the windows and microsoft, there has to be a way of fixing this problem without a reinstall.

I respect what you are saying but in this case I get a gut feeling based on the information that I have it seems like a screwed up install. Since when, btw, is reinstalling a "Windows" answer? If thats the case then either I have OCD or I'm a Windows expert because I reinstall Ubuntu ALL THE TIME :lolflag::lolflag::lolflag:

Guess I just need it perfect...I know from another thread I'm not the only one!

---

### Post by halitech on 2008-09-10
> **Ripfox said:**
> I respect what you are saying but in this case I get a gut feeling based on the information that I have it seems like a screwed up install. Since when, btw, is reinstalling a "Windows" answer? If thats the case then either I have OCD or I'm a Windows expert because I reinstall Ubuntu ALL THE TIME :lolflag::lolflag::lolflag:

Guess I just need it perfect...I know from another thread I'm not the only one!

I guess I just think back to when I was using windows and in most cases, it was easier to reinstall then fix things because we couldn't see the code and windows being what it was, reinstalls were faster (except for the 5000 updates you needed to grab). Personally I've only reinstalled ubuntu twice since I started using it and that was when I first started cause I was still in windows mode and hadn't really been on the forum much so didn't know how to search properly (that and it was my only computer so when you can't get online, makes it hard to search answers ~L~). I know in some cases there is no other option but I still find it hard to believe that he could have 4 systems all with the except same problem of not being able to connect to game servers.

---

