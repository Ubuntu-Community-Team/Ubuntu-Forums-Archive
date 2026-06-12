---
title: "Upgrading server hardware"
date: 2013-02-05
forum: New to Ubuntu
---

### Post by Craig71 on 2013-02-05
Hi guys, thanks to some very helpful people on here, I have recently managed to install Ubuntu server and use it to stream the media around my house. 

The server is running on some old hardware though, and can't play 1080p DTS files, is just keeps buffering. My question is this: If  upgrade the cpu/mobo/ram & just use the hard discs currently in the server, will all the setting etc remain the same, or will I have to install from scratch?

---

### Post by Cheesemill on 2013-02-05
It should 'just work'.

I've switched drives between different hardware plenty of times with no issues. The only time you may run into problems is if you have restricted graphics drivers installed, but as this is a Ubuntu Server machine then these shouldn't be installed anyway.

---

### Post by Craig71 on 2013-02-05
Cheers dude. I'd thought/hoped it would, but bitter experience with Windows upgrades makes me nervous.:D

---

### Post by Paqman on 2013-02-05
You should just be able to drop the old hard drive into the new machine and it'll work fine. Linux if good at that sort of thing.

Obviously if anything on your new mobo doesn't play nicely with Linux you could have trouble, but I'm assuming you're going to buy hardware that isn't known to have any Linux compatibility issues.

Are you sure it's the CPU/RAM/etc that causing the buffering? Not your network or something?

---

### Post by tgalati4 on 2013-02-05
Try taking a Windows disk out of one machine and place in another.  I would rather have a root canal.  Since linux detects hardware at boot time and loads appropriate drivers, you will be operational 90% of the time.  Any proprietary/non-open drivers will need to be loaded, but you will get messages to that effect in dmesg.

```
dmesg | more
```

Page through the entire boot dmesg and jot down any errors.  That's the quickest way to fix configuration on a new machine.

---

### Post by Craig71 on 2013-02-06
Thanks guys - all sounds good - it's off to the bay I go!

---

### Post by Cheesemill on 2013-02-06
As Paqman mentioned earlier, are you sure it is your current hardware that is the problem?

For example if you are using a wireless network then this may be causing the problem, no amount of money spent on a new CPU, RAM, etc will fix this.

What exactly is your current setup and what are the problems you are having?

---

### Post by Craig71 on 2013-02-06
Good point chaps.

My server is currently directly connected to the router, which services the rest of the network through a Homeplug system. Everything works fine until I try to stream a 1080p file encoded with DTS audio - then I get buffering issues. 

The media pc the server is streaming to can play these files fine though - it's a decent spec - Q6600 CPU 4gb etc. And it's been playing them fine through usb.

The server spec is - I think, just at work now - an old (like 8 yrs+) Celeron with 1gb memory.

---

### Post by Cheesemill on 2013-02-06
I'm pretty sure the bottleneck is going to be your homeplugs rather than your server. Even an old Celeron should have no problems saturating a 100Mb/s wired network.

Can you give us the bitrate of one of the problem files, ie its size divided by its duration in seconds. It may well be that this is higher than the network can handle in which case your only option would be to re-encode the files or switch to a proper wired network. No amount of money spent on a faster CPU or more RAM will change this.

Also the specs and make/model of the homeplugs would be useful.

---

### Post by Craig71 on 2013-02-06
Hmmm, interesting, I'll check when I get home then dude. Strange thing is, I could stream from the main pc to the media fine? Again using homeplugs.

---

### Post by Craig71 on 2013-02-06
Just had a look, its a 16gb file at 2hrs 22mins, which using an online bitrate calculator gives: 1934 kiloBytes/sec or 15473 kiloBites/sec.

I'm a little out of my depth here, but my homeplugs are 200mb ones. They should be ok I think?

---

### Post by Cheesemill on 2013-02-06
A couple of things for you try...

When you are trying to stream the problem files ssh into your server and run top or htop, this will let you know whether or not your CPU or RAM are being maxed out, if they are then an upgrade is in order, if not then upgrading wont make a difference.

Check the actual connection speed between the machines on your network, don't rely on the quoted speeds for your homeplugs as being accurate (these are theoretical maximum speeds after all).

The easiest way to do this is with iperf, on your media PC start the iperf server by typing...
```
iperf -s
```Now on your server machine type...
```
iperf -c 192.168.1.200
```replacing the IP address with the correct value for your media PC.

Iperf will then transfer data from your server to the media PC and give you an accurate measure of the transfer speed, for example...
```
rob@arch:~$ iperf -c 192.168.1.200
------------------------------------------------------------
Client connecting to 192.168.1.200, TCP port 5001
TCP window size: 22.9 KByte (default)
------------------------------------------------------------
[  3] local 192.168.1.150 port 58527 connected with 192.168.1.200 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.0 sec  2.00 GBytes  1.72 Gbits/sec
```If the resulting speed is less than the bitrate of your media files then your bottleneck is in the network somewhere.

> Strange thing is, I could stream from the main pc to the media fine? Again using homeplugs.This doesn't really mean anything.

Homeplugs are funny things, they can be affected by all sorts of factors. Distance between sockets, localised interference, whether they are plugged into a socket that is directly attached to the ring main or just to a spur, the quality of your household wiring, a loose screw in one of your sockets etc. If you have a neighbour who has a ham radio hobby this will destroy the speed of your homeplug network (you can tell if you have by a 30ft aerial in their garden).

By testing transfer speeds between various machines you may find yourself in a situation where you can transfer at high speed between your main PC and the media PC, but only at a slow speed between the router homeplug and the other machines because of sub-standard wiring on the router part of the wiring circuit.

If this is the case then try the router homeplug in a different socket, it may make all the difference needed for uninterrupted streaming.

---

### Post by Cheesemill on 2013-02-06
> **Craig71 said:**
> Just had a look, its a 16gb file at 2hrs 22mins, which using an online bitrate calculator gives: 1934 kiloBytes/sec or 15473 kiloBites/sec.

I'm a little out of my depth here, but my homeplugs are 200mb ones. They should be ok I think?
Yep, thats a bitrate of about 1.9MB/s. Even an old server should have no problems at all sustaining this transfer rate.

Your homeplugs have a quoted speed of 25MB/s so you would *think* they should do the job without any problems.

However, this is an absolute theoretical maximum speed which will never be obtainable in the real world due to the factors I outlined in my previous post, you may find that they are not capable of transferring data at anywhere near this rate. I've had homeplugs that won't go any faster than 1MB/s.

Also the speed of your homeplugs is shared between all of the devices on your network, if you are doing anything else with the network at the same time this will eat into the bandwidth available for streaming.

Your best bet is to measure your actual network speed to give you some  real-world figures.

---

### Post by Craig71 on 2013-02-07
Cheers man, I tried that 'top' command, it seems the cpu & memory are only running at around 10%, so I think you're right. 

I didn't get chance to try the iperf thingy, as the tv was needed by the Mrs. One question - the media pc is running windows 7, can I still use that iperf command on that?

I have stopped looking at mobo upgrades now, and I am looking at 500mb homeplugs instead!:D

---

### Post by Craig71 on 2013-02-07
Hi again dude, just tried it, this is the message I get:  

[HTML]
craig@server:~$ iperf -c 192.168.1.7
------------------------------------------------------------
Client connecting to 192.168.1.7, TCP port 5001
TCP window size: 22.9 KByte (default)
------------------------------------------------------------
[  3] local 192.168.1.11 port 60225 connected with 192.168.1.7 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.0 sec  34.2 MBytes  28.6 Mbits/sec
craig@server:~$[/HTML]

I'm confused now, as this seems to suggest all should be ok?

---

### Post by Cheesemill on 2013-02-07
It looks like you've just got enough bandwidth available.

From the above numbers your network can transmit at 3.6MB/s and you need around 1.9MB/s to stream your media.

Are you doing anything else on the network at the same time? As I mentioned earlier this 3.6MB/s is the total bandwidth available for all of your machines, if you are using the internet or transferring any other files at the same time then this might not be enough. Also the iperf test is quite short, this 3.6MB/s may not be sustainable over a longer period of time.

I would still look at this as being a network issue rather than your server being underpowered, especially if your CPU and RAM usage is only around 10%.

Can you try temporarily connecting your media PC to the router directly with a network cable to see if it makes any difference?


PS - See what I mean about theoretical quoted speed and actual speed, your homeplugs say they are capable of 200Mb/s but are only actually working at 28.6Mb/s.

---

### Post by Craig71 on 2013-02-08
Thanks for your help dude. To do that iperf test, I plugged the homeplug directly into the wall socket - it had been in an extension lead.

I tried to stream the file after completing the iperf test, and it did work fine. I wasn't doing anything else at all on the network though. I do have a long cable to connect the media pc to the router, I'll give that a go & see what happens.

I do see what you mean about the 200mps speed though, I may have to invest in a set of 500 ones, to ensure we can stream to different devices at the same time.

---

### Post by Cheesemill on 2013-02-08
> **Craig71 said:**
> I do see what you mean about the 200mps speed though, I may have to invest in a set of 500 ones, to ensure we can stream to different devices at the same time.
Just make sure you buy them from somewhere you can take them back to. The speed you are getting at the moment may be at the limit of what you can achieve with your particular wiring. Don't be surprised if 500Mb/s plugs don't make any difference.

---

