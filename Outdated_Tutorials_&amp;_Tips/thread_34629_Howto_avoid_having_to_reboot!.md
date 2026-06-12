---
title: "Howto: avoid having to reboot!"
date: 2005-05-15
forum: Outdated Tutorials &amp; Tips
---

### Post by Heliode on 2005-05-15
I'm starting this howto because a lot of people seem to be under the impression that you have to reboot Ubuntu to get certain changes applied. However, when working with Ubuntu, or Linux in general, it is important to remember that rebooting is a Windows CrazyThing (TM). The only thing you should really have to reboot a Linux machine for is for changes to the kernel. All other things you can reload/restart/whatever at run-time. This is due to the modular nature of the Linux system. Why do you think Unix systems have the highest uptime?

Well anyway, lets get this started. I propose we make this kind of a collaborative effort since i'm by no means an expert (yet) and there's some stuff I don't know. So i'll just add what I do know and we can just add to each others knowledge, ok? Alright then.

**The graphical user interface**
As most of you know, you can refresh the gnome panel with the command:
```
killall gnome-panel
```

However, when screwing around with your Xorg.conf, you have to restart X in order to apply your changes. You can do this with the key combination:
```
 Ctrl+Alt+Backspace 
```
WARNING: This is a very powerful command! It won't ask you if you are sure, or if you would like to save anything you have running; it just shuts off everything in brute force. A more 'civilized' way might be to do '/etc/init.d/gdm restart', but i'm going to need confirmation on that.

**Services**
A default Ubuntu system has lots of services running. You can get a list of them with:
```
ls /etc/init.d
```

For example, lets say you have a samba server running, and you made a change to the samba config file. You can restart samba like this:
```
sudo /etc/init.d/samba restart
```

Or if a change has occurred in your network environment (new cable plugged in, interface removed, etc), you could do:
```
sudo /etc/init.d/networking restart
```

And so on..

This is all I can think of right now. I'm sure there's lots of other stuff, but in general just remember: rebooting in order to apply stuff is a Windows CrazyThing, and if you feel like you have to do it there is probably a better way.

I encourage anyone to add to this Howto!

Have fun!

---

### Post by Firetech on 2005-05-15
Some quick notes:

1. A lot of the init.d scripts also have a 'reload' action (e.g. "sudo /etc/init.d/samba reload") which just reloads the conf file. All of them doesn't work without restarting the program, but most do.

2. "/etc/init.d/gdm restart" is correct (if you run kubuntu, exchange gdm with kdm). Although, a good thing to do is to press ctrl+alt+backspace after you've logged out. "/etc/init.d/gdm restart" is mostly used for reloading gdm's config.

Anyway, it's a great howto. I would probably had written something like this if you hadn't ;)

---

### Post by Sam on 2005-05-15
Nice howto !

---

### Post by _Pete_ on 2005-05-17
Also good trick to really get everything restarted without rebooting is going
to the single user mode (init 1) and then back to the normal runlevel (init 2).

---

### Post by Rodrigo on 2005-05-18
[QUOTE=_Pete_]Also good trick to really get everything restarted without rebooting is going
to the single user mode (init 1) and then back to the normal runlevel (init 2).[/QUOTE]

Why Oh why I didnt think of THAT before ?!?!  ](*,) 

cool tip

---

### Post by Heliode on 2005-05-18
[QUOTE=_Pete_]Also good trick to really get everything restarted without rebooting is going
to the single user mode (init 1) and then back to the normal runlevel (init 2).[/QUOTE]

That's also a good one! Not recommended if you are running a server people depend upon, but great for workstation users who don't like to wait for their system to reboot!

---

### Post by mr_ed on 2005-05-20
There's one thing that I can't do without rebooting, so far:  If I'm connected to the 'net at work, and I pack up my laptop and go home without turning it off, I can't get access to the 'net until I reboot.  I've blown away my resolv.conf, did an /etc/init.d/____ restart on every system I could see that looked relevant, and I still can't.  Oh well.

---

### Post by Heliode on 2005-05-20
did you try;

sudo /etc/init.d/networking restart

sudo ifdown eth0

sudo ifup eth0

sudo dhclient eth0    (if you're using DHCP)

---

### Post by testingubuntu on 2005-05-20
[QUOTE=mr_ed]There's one thing that I can't do without rebooting, so far:  If I'm connected to the 'net at work, and I pack up my laptop and go home without turning it off, I can't get access to the 'net until I reboot.  I've blown away my resolv.conf, did an /etc/init.d/____ restart on every system I could see that looked relevant, and I still can't.  Oh well.[/QUOTE]


sudo /sbin/service network restart   <-- Does that do it?

---

### Post by epb613 on 2005-06-07
Same things happens to me on my laptop.

sudo modprobe -r ipw2200
sudo modprobe ipw2200 
sudo dhclient eth1 (or whatever your interface is called)

fixes it though.

---

### Post by pdk001 on 2005-06-07
thanks a lot. i will try it right away

---

### Post by jerome bettis on 2005-06-08
[QUOTE=_Pete_]Also good trick to really get everything restarted without rebooting is going
to the single user mode (init 1) and then back to the normal runlevel (init 2).[/QUOTE]

what are the commands for #2?

i can get to single user mode with sudo /etc/init.d/single start but i can't figure out how to get back to normal mode ...

---

### Post by jerome bettis on 2005-06-08
also the ipw2200 card does have to be reloaded sometimes (this is a nasty bug that they've been trying to fix for a long time now .. sooner or later it will be gone).

to do this i wrote a simple shell script

sudo rmmod ipw2200
sudo modprobe ipw2200
sudo ifdown eth0
sudo rm /etc/network/interfaces
sudo ln -s /etc/network/interfaces.home /etc/network/interfaces
sudo ifup eth0

that just reloads the module, takes down the interface, and i use different /etc/network/interfaces.* files for the different network enviorments i'm in (have one for home, one for work etc etc) and the third and fourth command remove the symbolic link and link whatever interface file i need at the time.  then it brings the interface back up of course.

writing different etc/network/interface files and having different versions of a script like that is the easiest way i've found to manage wireless networks.  i can just type home or work or class and the network works great.

---

### Post by sickdude on 2005-06-08
[QUOTE=Heliode]did you try;

sudo /etc/init.d/networking restart

sudo ifdown eth0

sudo ifup eth0

sudo dhclient eth0    (if you're using DHCP)[/QUOTE]

k thnx dude

i was getting worried because the networking restart doesnt do anything, wel it doesnt refresh the dhcp lease but now i know how :D thnx

used to working with fedora core and red hat so i was typing "service network restart" more often because of frustration ](*,)

---

### Post by Heliode on 2005-06-08
Whoops... can a mod please change

Reload this Page  **Hotwo**: avoid having to reboot!

into

Reload this Page  **Howto**: avoid having to reboot!    

?

 ](*,)

---

### Post by Tobi Vollebregt on 2005-06-08
[QUOTE=jerome bettis]what are the commands for #2?

i can get to single user mode with sudo /etc/init.d/single start but i can't figure out how to get back to normal mode ...[/QUOTE]

sudo init 1
sudo init 2

to switch to runlevel 1 and 2 respectively

---

### Post by Ptero-4 on 2005-07-09
[QUOTE=Tobi Vollebregt]sudo init 1
sudo init 2

to switch to runlevel 1 and 2 respectively[/QUOTE]
 Actually you don't need to use sudo when going back to runlevel 2 'cause in singleuser you're actually in the root account.

---

### Post by PeteJ on 2005-08-23
Hi All,

I'm working on a ubuntu hoary 5.04, installed as server only, via ssh command line, with no gui available, on a remote machine, that I don't want to bug the locals to reboot.

3 Questions, if I may:

1)  does one _permanently_ set the default route by adding a gateway line to the /etc/networking/interfaces file?  ("sudo ip route add default via" wasn't permanent after reboot, ugh, and so my ssh access from the outside external network no longer worked...)

2)  /etc/init.d/networking restart drops my remote connection and doesn't bring the interfaces back up (so I have to ask the locals to reboot because I could no longer diagnose the problem).  What would cause the connection to permanently drop?   Could it be not having a gateway line in the interfaces file?  Is there something else wrong with "network restart" in hoary?  I'm I missing something else?  

3)  Is there a lighter way to simply "reload" the interfaces file besides "networking restart"?    Would something like "if-down && if-up" be lighter and do the job (remember, I'm working through a remote ssh terminal).  

Thanks!
Pete

---

### Post by xinel on 2005-08-26
[QUOTE=_Pete_]Also good trick to really get everything restarted without rebooting is going
to the single user mode (init 1) and then back to the normal runlevel (init 2).[/QUOTE]

How do you do that?

sorry didn't read above, please ignore

---

### Post by joshuapurcell on 2005-09-19
[QUOTE=PeteJ]Hi All,

I'm working on a ubuntu hoary 5.04, installed as server only, via ssh command line, with no gui available, on a remote machine, that I don't want to bug the locals to reboot.

3 Questions, if I may:

1)  does one _permanently_ set the default route by adding a gateway line to the /etc/networking/interfaces file?  ("sudo ip route add default via" wasn't permanent after reboot, ugh, and so my ssh access from the outside external network no longer worked...)

2)  /etc/init.d/networking restart drops my remote connection and doesn't bring the interfaces back up (so I have to ask the locals to reboot because I could no longer diagnose the problem).  What would cause the connection to permanently drop?   Could it be not having a gateway line in the interfaces file?  Is there something else wrong with "network restart" in hoary?  I'm I missing something else?  

3)  Is there a lighter way to simply "reload" the interfaces file besides "networking restart"?    Would something like "if-down && if-up" be lighter and do the job (remember, I'm working through a remote ssh terminal).  

Thanks!
Pete[/QUOTE]
I've never quite figured this one out, but I don't get disconnected from a server when issuing the network restart command (while connected through telnet or ssh). You would think you'd get disconnected... **ifdown eth0 && ifup eth0** should do the trick as well.

Also, I find myself using the networking gui front-end every day a couple of times (when coming and going from work/home). You get to it through this command:

**network-admin**

You are able to bring your network devices up/down, and change their configuration easily (almost as easily as editing the needed /etc/network/interfaces config file).

EDIT: Speaking of the init comman mentioned above, I've always used that to change the runlevel, but recently I've read about the **telinit** command. I've heard that it's better to use telinit, but I can't seem to find a difference between the two commands. Anyone have a clue?

---

### Post by doclivingston on 2005-09-20
[QUOTE=joshuapurcell]EDIT: Speaking of the init comman mentioned above, I've always used that to change the runlevel, but recently I've read about the **telinit** command. I've heard that it's better to use telinit, but I can't seem to find a difference between the two commands. Anyone have a clue?[/QUOTE]

"telinit N", where N is the runlevel to change to, is the canonical way - however "init N" works fine too (although there may be Unixes where it doesn't work).

---

### Post by zigford on 2005-09-27
[QUOTE=PeteJ]Hi All,

I'm working on a ubuntu hoary 5.04, installed as server only, via ssh command line, with no gui available, on a remote machine, that I don't want to bug the locals to reboot.

3 Questions, if I may:

1)  does one _permanently_ set the default route by adding a gateway line to the /etc/networking/interfaces file?  ("sudo ip route add default via" wasn't permanent after reboot, ugh, and so my ssh access from the outside external network no longer worked...)

2)  /etc/init.d/networking restart drops my remote connection and doesn't bring the interfaces back up (so I have to ask the locals to reboot because I could no longer diagnose the problem).  What would cause the connection to permanently drop?   Could it be not having a gateway line in the interfaces file?  Is there something else wrong with "network restart" in hoary?  I'm I missing something else?  

3)  Is there a lighter way to simply "reload" the interfaces file besides "networking restart"?    Would something like "if-down && if-up" be lighter and do the job (remember, I'm working through a remote ssh terminal).  

Thanks!
Pete[/QUOTE]

Pete,

1.  On my ubuntu setup I have a bridged network which the graphical utility cannot understand, so I am forced to use the /etc/network/interfaces file.  To add a default gateway in this is easy.

```

iface eth0 inet static 
address 192.168.1.2 
network 192.168.1.0 
netmask 255.255.255.0 
broadcast 192.168.1.255
**gateway 192.168.1.1 **

```

2.  When restarting network from remote I have also had the problem you describe.  I believe it is because when you loose connectivity, linux no longer can process the command because it looses its output.  

There is a handy program called "screen"  It acts like a buffer between your shell and the output display.  Think of it like VNC for ssh/telnet.  (You can disconnect from it and your application stays running.

This is how it works for me:
ssh -l user somewhere.com
# screen
# /etc/init.d/network restart

----Disconnected----
ssh -l user somewhere.com
# screen -r (This re-attaches me to a running screen)

---

### Post by _Pete_ on 2005-09-28
[QUOTE=Heliode]That's also a good one! Not recommended if you are running a server people depend upon, but great for workstation users who don't like to wait for their system to reboot![/QUOTE]

That's the reason for wall command:

# echo "piss off" | wall && init 1

:)

---

### Post by encompass on 2006-01-02
The tweak firefox link is down.  But there is another thread that does what you say... search for 'diggity' and find the firefox link.  Just trust me... that is how I remembered to find it.

---

### Post by jonrkc on 2006-05-24
If you make changes to /etc/fstab you can test or implement them right away without rebooting by simply doing:
```

sudo mount

```

---

### Post by Giga on 2006-06-27
First of all, thanks for the tips (the "HOWTO backup" is awesome).

Why both of the lines does not do the same job? 
I mean.. both of the lines should do the same thing, isnt it?

oem@ubuntu:/etc/init.d$ **sudo networking restart**
sudo: networking: command not found

and this dont:
oem@ubuntu:/etc/init.d$ **sudo /etc/init.d/networking restart**


I know its a tipic roockie question, but you know...:confused:

networking is a service running.. and Bash interprets like as a command, this is why i got command not found. Right?
But why bash does not interpret when i put all the path along with?

Thx

---

### Post by jonrkc on 2006-06-28
Networking isn't a command, but a service run at boot time.  The script for it is located in /etc/init.d, and the way to restart is it
```

sudo /etc/init.d/networking restart

```
This kind of "command" will work for any service, by the way...as far as I know.   It's handy to restart, or to stop, or start, a service sometimes as a way of troubleshooting--for example, when there's no sound.  (But this evening the main trouble was that I had my headphones plugged into the wrong outlet, and it took me an hour to find out.) :?

The "restart" isn't a command recognized by bash but a special function associated with the scripts in init.d.  With "sudo networking restart" bash interprets the word immediately after "sudo" as referring to a command--but that command doesn't exist.  When a PATH follows "sudo," bash knows something special's going on: Either a command is coming up that is executed out of the directory being stated, or a special function.  So there's no error message as long as either a command or a special function follows the path statement.

---

### Post by ethoslite on 2007-03-22
I have read through this thread and found the howto and follow up posts informative.  I do have a question regarding performance, relating to memory.  

I've noticed when I have multiple applications open, performance of course decreases somewhat because the available hardware memory is being minimized.  Ok, well if I close  many of these and leave a few open, will the memory being used from those programs be cleanly released back into availability?

As well, is it a good practice to periodically Ctrl-Alt-Backspace, just because, or is it only necessary after applied config or update changes?

Thanks ;)

---

### Post by amd-64 on 2007-06-07
These do the job for me

```
sudo modprobe --force ndiswrapper

sudo ifup --force eth1
```
no need to unload and reload.

---

### Post by Greedo on 2008-06-17
After reading this thread, somebody might have a solution for one of the reasons I reboot my hardy workstation almost once a day. 

It seems like if I ever watch a video which is flash encoded then all my sound drivers are messed up except those for real player until I reboot. Totem will no longer play any sounds, nor will VLC until I restart my system. Does some body have a command line that could fix my sound issue(s) without rebooting?

---

### Post by dragoonx on 2008-07-23
> **Greedo said:**
> After reading this thread, somebody might have a solution for one of the reasons I reboot my hardy workstation almost once a day. 

It seems like if I ever watch a video which is flash encoded then all my sound drivers are messed up except those for real player until I reboot. Totem will no longer play any sounds, nor will VLC until I restart my system. Does some body have a command line that could fix my sound issue(s) without rebooting?

I don't know if it is the same case but what I do when this happens, I just type in terminal:

```
killall pulseaudio
```

Somehow, pulseaudio interferes with my Rhythmbox, Totem, and all the other multimedia stuff I run that needs sounds.

Again, I'm not sure if we have the same case.

---

### Post by TravisNewman on 2008-07-23
> **Heliode said:**
> Whoops... can a mod please change

Reload this Page  **Hotwo**: avoid having to reboot!

into

Reload this Page  **Howto**: avoid having to reboot!    

?

 ](*,)
Yep! Although this is over a year late.

---

### Post by Unanimated on 2008-11-04
Pretty nice guide - I'll probably have to use it every once in a while.

---

### Post by halovivek on 2008-12-19
Thanks for posting

---

### Post by H4F on 2009-03-29
Thanks nice posts.
How do I avoid rebooting because of changes to the config files of kernel modules ?
Ex. after changind /etc/modprobe/alsa* I have to restart .
trying to reload snd_hda_intel

modprobe -r snd_hda_intel
FATAL: Module snd_hda_intel is in use.

??

---

### Post by Skip Da Shu on 2009-05-22
> **panickedthumb said:**
> Yep! Although this is over a year late.

Yea but it got thousands of hit from folks looking for Hotwomen... LOL

---

### Post by learning_ on 2010-05-15
> **_Pete_ said:**
> Also good trick to really get everything restarted without rebooting is going
to the single user mode (init 1) and then back to the normal runlevel (init 2).

how do you do this? im just starting out, learning as i go along. that seems very very usefull, but i dont know how to do it.

also didnt read above. just ignore this please

---

### Post by Nicholas Buckner on 2010-05-17
meh, my ubuntu boots up so fast that this doesn't really bother me :) beats windows 7  booting up in 1 min:mad:

---

### Post by srnissen on 2010-08-29
There is a thing I have to reboot for, actually: Every so often, my keyboard stops responding.  ...  yeah.

---

### Post by d3v1150m471c on 2011-03-29
lol i'd never reboot this machine if it wasn't for kernel updates. I've been wanting to see if i could leave it running for over a month total time but those horrible developers keep making my system better. :)

---

