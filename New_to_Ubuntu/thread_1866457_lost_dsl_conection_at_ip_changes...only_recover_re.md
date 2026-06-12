---
title: "lost dsl conection at ip changes...only recover restarting"
date: 2011-10-21
forum: New to Ubuntu
---

### Post by freedback on 2011-10-21
Hello everyone, 

well, my first post so no mystery Im a newbie..although I have some common sense and Im willing to work and learn ;)


As title shows, I am conecting to internet through a wired dsl conection using it perfectly, and all of a sudden (not frequently) I lose conection. I relate it to the disconect-reconect cycle once each 12hrs due to dynamic IP changes from my ISP.


Thing is Ive set it to conect automatically and it doesnt reconect, but also it DISAPPEAR my network from the map...

Ive tried obviously to turn off my modem and restarting it, as well, i tried to disconect manually and in such cases, my network is still there and asks me to conect again...all right there.


Now the icon on the "top menu" of my desktop (the one refered to networks) at that instances shows this options (or similar cause mine in spanish) :


- no network devices available (this option in grey, like "unmarkable" or non-selectable)
 
- VPN conections - markable

- activate network (markable, and - actually - marked)

- not information of conections (grey/unmarkable)

- edit conections (markable)

and in the icon itself is a "empty triangle" with the sharp side pointing down


Ive tried everything I humbly know.....(ok, Im coming from a O.S. where everything is done without your knowledge awareness or authorization..and I also confess, I used to prefer watching TV before reading at some point in time)

Only solution (but not ideal) has been to restart system, after which I authenticate and Im conected again, the icon appears now with the two opposite arrows (conected)

and now the contextual menu from it reads:


- "wired network" (in grey non-markable ...where it used to say no network devices available) 

- DSL conection (thats my internet conection) - markable

- disconect - selectable, I tried as I said above already, and it disconects and reconects perfectly.

- VPN conections - markable

- activate network (marked)

- info of the conection ...now markable! and I checked in there and at ipv4 it has all settings coresponding to my conection/isp all perfect..as well has this information:



DSL conection (default):

General:
Interface:   Ethernet (eth0)
hardware adress: 00:1F:C6:A2:A6: D7
driver: forcedeth
Speed: 100 Mb/s

- finally:edit conections - markable



Im sorry if post long, but tried to give as much info as posible, right?
Please, any idea of what can be wrong, or what can I do to not have this issue? 
Thousand thank yous ;)

---

### Post by duke.tim on 2011-10-21
Try running

```
sudo ifconfig eth0 down
sudo ifconfig eth0 up
sudo dhclient eth0
```

If that doesn't work try 

```
/etc/init.d/networking restart
```

---

### Post by freedback on 2011-10-21
Thanks a lot for answer

You know Ive just tried deleting conection and made it with pppoeconf as I read somewhere here too, I dont know, hope it works, I will know soon cause everyday I had this trouble.

About these comands, I tried them at terminal, but didnt give me any answer. What should it reply? 

Ill write back soon to say if it worked.
Thanks!!

---

### Post by duke.tim on 2011-10-21
the first set of commands (ifconifg dhclient)
won't send any feedback to the terminal

/etc/init.d/networking restart

Will respond with something like this, except this is without using sudo, which means it is reporting a "[fail]"
> /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                             ifdown: failed to open statefile /var/run/network/ifstate: Permission denied
ifup: failed to open statefile /var/run/network/ifstate: Permission denied
[fail]

---

### Post by freedback on 2011-10-21
Hello again 
Thanks!

I tried now that line in terminal and this is what happens:

> 
sudo /etc/init.d/networking restart
[sudo] password for nicotriv: 
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...       
Plugin rp-pppoe.so loaded.
PPP session is 1907
Connected to 00:30:88:11:4e:76 via interface eth0
Using interface ppp1
Connect: ppp1 <--> eth0
PAP authentication failed
Connection terminated.

PPP session is 1576
Connected to 00:30:88:11:4e:76 via interface eth0
Using interface ppp1
Connect: ppp1 <--> eth0
PAP authentication failed
Connection terminated.


and then millions of times the same last paragraph, only changing everytime the number of PPPsesion

..then finally:
> 
PPP session is 129
Connected to 00:30:88:11:4e:76 via interface eth0
Using interface ppp1
Connect: ppp1 <--> eth0
PAP authentication failed
Connection terminated.
Failed to bring up dsl-provider.


Do you think theres smth wrong in there? 
I dont really know..but lets see hows it going with this pppoeconf 
Ill tell you tomorrow, so far is working fine, but asit used to work some hours, I have no choice but to wait and see..

Thousands of Thanks ;)

---

### Post by duke.tim on 2011-10-21
PAP authentication failed

means that the password is not being accepted (or there is some sort of configuration problem)

I'm afraid I don't know what to do if your configuration is wrong.

If it is working, don't try and fix it ;)

---

### Post by freedback on 2011-10-23
Hi, 

sorry to bring it back but found it important to stablish it clarified for if in case anyone comes with the same trouble and this can help:

My problem was that, while I used the "authomatic detection" conection to internet (wired) ..the one that appears as to be conected and set-up from the icon at the top-right of your screen, each time that I had a cut/break in my conection due to change of dynamic IP from my ISP, I "lost" my conection from the contextual menu coming from the icon to conect. I couldnt but restart pc and conected again.

SOLUTION- In case that happens to anyone out there, this is what I did to solve: 

*Went within that contextual menu (clicking on triangle icon at top-right of screen) to edit conections, and once found mine (in this case DSL tag), delete/remove it.

*Now went to terminal (if youre newbie like me, you can access it from the dash, just typing terminal...btw recomnded to keep it in the launcher, cause looks like we will need it a lot ;) ) and once there typed 
```
sudo pppoeconf
```...will ask you for password and after that for your user and password (the one to authenticate with your ISP)

*then will authomatically check for your hubs/devices and can ask you if you want it to change somethings in to configuration, thats ok, can say yes :) Also, will make you a question regarding "noauth" and "defaultroute" and if you want to remove "nodetach", you can say yes there :)

*Theres an option that appears to make it automatically connected everytime you start system (in case its what you want, like I did) 
If that doesnt suit you, and prefer to conect when you want to, you can not select that option and then you can use the command 

```
pon dsl-provider
```
everytime you want to connect, and then, when you want to disconect again:
```
poff dsl-provider
```

If it did work? In my case...I had trouble everyday with disconections and losing my conection from the icon to conect; now I did never have to worry again :) It stays conected.

Hope it helps!
:)

(sorry, I dont know how to select it "solved" )

---

