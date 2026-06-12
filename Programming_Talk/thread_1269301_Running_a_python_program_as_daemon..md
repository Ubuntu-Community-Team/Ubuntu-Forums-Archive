---
title: "Running a python program as daemon."
date: 2009-09-18
forum: Programming Talk
---

### Post by dchurch24 on 2009-09-18
Hi,

I have a TCP/IP listener that runs on my Xubuntu box, and waits for instructions from any of my clients. Basically the box has ADU units and USB relays plugged into it. When the 'listener' gets a command, it turns on lights, starts up my beer fridge, opens the window, unlocks the front door etc...

The box also runs as a MythFrontend. Sometimes, I need to reboot the box as Myth is sometimes a little unstable and this sorts it out (it's not a problem, it happens very infrequently).

....but once I reboot, I often forget to start the python IP listener, meaning that my lights don't come on/go off, as per the scheduler, and I can't turn on my TV etc... until I pull out the wireless keyboard and mess about to get it up and running.

Is there a way in which I can run this python program as a daemon that starts in the background?

---

### Post by fishy6969 on 2009-09-18
I had a similar problem for a temperature monitoring system I set up. Eventually I adapted the examples found in this article [http://www.pyzine.com/Issue007/Section_Articles/article_MobileDataCollection.html](http://www.pyzine.com/Issue007/Section_Articles/article_MobileDataCollection.html)

Hope it helps

---

### Post by dchurch24 on 2009-09-18
Hi, thanks for that - looks like an interesting read!

---

### Post by unutbu on 2009-09-18
Maybe make a script like this:

/root/bin/ip_listener_daemon.sh:
[PHP]
#!/bin/sh
until ip_listener.py; do
    echo "Server 'ip_listener.py' crashed with exit code $?.  Respawning.." >&2
    sleep 1
done[/PHP]

Then add to /etc/rc.local:
```

/root/bin/ip_listener_daemon.sh &
```

(above the exit 0 line).

That way, every time you boot the ip_listener_daemon.sh will be started in the background.
ip_listener_daemon.sh will launch your python listener, and if for any reason the python listener process ends, ip_listener_daemon.sh will restart it.

The shell script daemon code comes from [http://stackoverflow.com/questions/696839/how-do-i-write-a-bash-script-to-restart-a-process-if-it-dies](http://stackoverflow.com/questions/696839/how-do-i-write-a-bash-script-to-restart-a-process-if-it-dies)


PS. What are ADU units? (couldn't find it with Google...).
Are they like[ X10 devices]("http://en.wikipedia.org/wiki/X10_(industry_standard)")? Where can I learn more about them and how to use them with linux?

---

### Post by dchurch24 on 2009-09-18
That, Sir, is absolutely spot on! 

Thank you very much.

The ADU unit is this:

[http://www.ontrak.net/ADU200.htm](http://www.ontrak.net/ADU200.htm)

There's a little app that can be downloaded for Linux that enables you to send commands like: ./adu K0

That would switch 'switch K' off, 1 for on etc... You simply wire in the live/return and out the other side and you can control devices through the command line (or any other way).

I thought about the X10 stuff, but it's simply wouldn't have been satisfying enough to just buy it off the shelf.

Currently, I have two touchscreens (rescued from a skip - there were four. Two with damaged screens, and two with PSUs that had gone - a simple swap and I have two working touchscreens) - both of these machines are running WinXP. 

[http://www.imagebam.com/image/0e53ab46083938](http://www.imagebam.com/image/0e53ab46083938)

When you click on a button, it goes to a MySQL database and queries like this:


select ... where room='front' and object='mainlamp' and action='on';

...this will return the command to send and the IPaddress of the machine that has an ADU or relay in and sends the command to the listener.

The listener (python), sends the command to the shell and viola! the lights/beer fridge/amplifier etc... turn on (or off).

I have also written a scheduler for it, so that if I forget to turn something off, then it does it for me. I have also created a 'holiday mode' where it will randomize lights between pre-defined hours. Say somewhere in between 7pm and 8pm, turn on a random light. Leave it on for 2 hours, and then turn off. The next day, the sequence will be different of course, giving the impression that someone is in the house and not 'on holiday' ;-)

I then bought (for £10) 4 wireless radio controlled power-plugs. I stripped the board out of the remote control, and shorted the switches, wiered them into a relay, wrote scripts to turn on/off, and now I can control the lamps in all four bedrooms wirelessly and/or the Python listener from anywhere in the world.

It's far more satifying to have made it myself than buying off the shelf stuff.

Anyway, I'll stop rambling now!

---

### Post by fishy6969 on 2009-09-18
Cool stuff. I hadn't come across the the ADU before. I have been hacking around with the Dallas 1-wire stuff quite a bit though and have managed to setup a temperature/moisture sensitive plant irrigation system that sometimes works. Foxes are a real problem here and like to eat through cables - unfortunately not high voltage ones though!

---

### Post by fishy6969 on 2009-09-18
....forgot to ask - the control interface looks good. What did you use to write it?

---

### Post by dchurch24 on 2009-09-18
It's actually come on considerably since I took that picture - it also controls the TV (and can set reminders that pop up over the top of Myth using MythTVOSD, send SMS and/or email), as well as a whole host of other things (I simply can't stop programming it).

It's written in VB.Net, but I just started (last night in fact) to re-write it for Ubuntu in Mono (c# with GTK#) as a sort of tutorial to myself - sadly though, I think this may mean that the voice activation stuff will have to take a back seat. Currently, I'm using the M$ Speech SDK, so I can literally say "front room, lights on" and on they come (most of the time ;-) ). 

When I saw this: [http://gadgetynews.com/jedi-force-trainer-buy-it-and-gain-mind-control/](http://gadgetynews.com/jedi-force-trainer-buy-it-and-gain-mind-control/) you can imagine my excitement. I just need to get hold of one to hack around with, and I think I'll be able to 'think' my lights on and off!

PS. Can you not put the cables in small drain pipes?

---

### Post by fishy6969 on 2009-09-18
> PS. Can you not put the cables in small drain pipes?

Yeah I probably should do that...but it's been such a wet summer here in the UK I've not had mush use for an automatic irrigation system!

---

### Post by dchurch24 on 2009-09-18
I know the feeling. My garden is overrun with weeds!

All I need now is to invent a Linux based automatic weeding machine, and I'm in!

PS. Incidently, and slighly on topic, you can create a weather predicting system using old drainpipes and coax, pick up the polar orbit NOAA sats, and use WXtoImg (linux version) to decode the signals, like so (here's one I made earlier):

[http://photos-e.ak.fbcdn.net/photos-ak-sf2p/v208/114/99/577405151/n577405151_1230740_2625.jpg](http://photos-e.ak.fbcdn.net/photos-ak-sf2p/v208/114/99/577405151/n577405151_1230740_2625.jpg)

I predicted that storm, and it was a blinder!

I don't think there's anything you can't do in Ubuntu you know ;-)

PPS. Where in the UK are you? I'm obviously where the yellow cross is on the picture.

---

### Post by fishy6969 on 2009-09-18
I'm in South London. 
> S. Incidently, and slighly on topic, you can create a weather predicting system using old drainpipes and coax, pick up the polar orbit NOAA sats, and use WXtoImg (linux version) to decode the signals, like so (here's one I made earlier):
I've found the WXtoImg site, but have you any links for the 'drainpipes and coax' stuff?

---

### Post by dchurch24 on 2009-09-19
Have a look here:

[http://www.g4ilo.com/qfh.html](http://www.g4ilo.com/qfh.html)

You'll need a receiver of some sort. I use the ICOM PCR1000, which can be found on ebay for around 90 quid, although you could probably make or buy a better receiver for the 137 band.

---

### Post by unutbu on 2009-09-20
Thank you for the links and info, dchurch24. :)

---

### Post by dchurch24 on 2009-09-20
No problem. If you want to set that up (the weather sats thing) and need a hand, PM me.

In fact, if you want to borrow my antenna and are prepared to drive to the South Coast (Folkestone), then you would be welcome.

---

### Post by unutbu on 2009-09-20
Don't tempt me to break out the submarine :)

---

### Post by saeed kouchaki on 2011-07-30
[FONT=Times New Roman][SIZE=4]ThanX in advance to developer ...i should run a python program as daemon..got my answer..
[/SIZE][/FONT]

---

