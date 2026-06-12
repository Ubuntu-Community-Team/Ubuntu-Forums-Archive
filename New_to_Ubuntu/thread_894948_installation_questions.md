---
title: "installation questions"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by fignig on 2008-08-19
so i'm trying to install a couple of stuff: games, programs, and audio stuff.

to make this thread a little less complicated i'll go thru an example of one such program.

the program is called wondershaper, it is a bit torrent client and contains 6 files:

-copying              
-readme                
-todo                  
-version               
-wshaper
-wshaper.htb

the top 4 are txt files, whilst the other 2 are shell scripts

how exactly do i install something w/ these types of files. wtf are they, and how do i do it?

the readme directions for installation say:

If you dial in, you can copy the script to /etc/ppp/ip-up.d and it will be
run at each connect.

If you want to remove the shaper from an interface, run 'wshaper stop'. To
see status information, run 'wshaper status'.


each connect to what? when the computer restarts or when i want to download a torrent. what does this mean!?!?!

---

### Post by nicedude on 2008-08-19
I have no idea what this program is but I don't see make or configure files so maybe this is just a script based program and therefor does not need to be installed per se but insted you can just run it by opening a terminal in its directory and running the script.

i.e. do this inside the directory in a terminal window and see if it works.

./wshaper


PS you might also try reading the readme file as it more than likely will clue you in.

---

### Post by fignig on 2008-08-19
> **nicedude said:**
> I have no idea what this program is but I don't see make or configure files so maybe this is just a script based program and therefor does not need to be installed per se but insted you can just run it by opening a terminal in its directory and running the script.

i.e. do this inside the directory in a terminal window and see if it works.

./wshaper


PS you might also try reading the readme file as it more than likely will clue you in.

since being a smartass is common, here is the readme...

The Wonder Shaper		1.0
bert hubert <ahu@ds9a.nl>
[http://lartc.org/wondershaper](http://lartc.org/wondershaper)
(c) Copyright 2002 
Licenced under the GPL - see 'COPYING'

This document is a bit long, I'll split it up later.
The very short summary is: edit the first few lines of 'wshaper' and run it.

GOALS
-----

I attempted to create the holy grail:

	* Maintain low latency for interfactive traffic at all times

This means that downloading or uploading files should not disturb SSH or
even telnet. These are the most important things, even 200ms latency is
sluggish to work over.

	* Allow 'surfing' at reasonable speeds while up or downloading

Even though http is 'bulk' traffic, other traffic should not drown it out
too much.

	* Make sure uploads don't harm downloads, and the other way around

This is a much observed phenomenon where upstream traffic simply destroys
download speed. It turns out that all this is possible, at the cost of a
tiny bit of bandwidth. The reason that uploads, downloads and ssh hurt
eachother is the presence of large queues in many domestic access devices
like cable or DSL modems.

The next section explains in depth what causes the delays, and how we can
fix them. You can safely skip it and head straight for the script if you
don't care how the magic is performed.

Why it doesn't work well by default
-----------------------------------

ISPs know that they are benchmarked solely on how fast people can download.
Besides available bandwidth, download speed is influenced heavily by packet
loss, which seriously hampers TCP/IP performance. Large queues can help
prevent packetloss, and speed up downloads. So ISPs configure large queues.

These large queues however damage interactivity. A keystroke must first
travel the upstream queue, which may be seconds (!) long and go to your
remote host. It is then displayed, which leads to a packet coming back,
which must then traverse the downstream queue, located at your ISP, before
it appears on your screen.

This HOWTO teaches you how to mangle and process the queue in many ways, but
sadly, not all queues are accessible to us. The queue over at the ISP is
completely off-limits, whereas the upstream queue probably lives inside your
cable modem or DSL device. You may or may not be able to configure it. Most
probably not.

So, what next? As we can't control either of those queues, they must be
eliminated, and moved to your Linux router. Luckily this is possible.

Limit upload speed somewhat
---------------------------

By limiting our upload speed to slightly less than the truly available rate,
no queues are built up in our modem. The queue is now moved to Linux. 

Limit download speed
--------------------

This is slightly trickier as we can't really influence how fast the internet
ships us data. We can however drop packets that are coming in too fast,
which causes TCP/IP to slow down to just the rate we want. Because we don't
want to drop traffic unnecessarily, we configure a 'burst' size we allow at
higher speed.

Now, once we have done this, we have eliminated the downstream queue totally
(except for short bursts), and gain the ability to manage the upstream queue
with all the power Linux offers.

Let interactive traffic skip the queue
--------------------------------------

What remains to be done is to make sure interactive traffic jumps to the
front of the upstream queue. To make sure that uploads don't hurt downloads,
we also move ACK packets to the front of the queue. This is what normally
causes the huge slowdown observed when generating bulk traffic both ways.
The ACKnowledgements for downstream traffic must compete with upstream
traffic, and get delayed in the process.

Results
-------

If we do all this we get the following measurements using an excellent ADSL
connection from xs4all in the Netherlands:

Baseline latency:
round-trip min/avg/max = 14.4/17.1/21.7 ms

Without traffic conditioner, while downloading:
round-trip min/avg/max = 560.9/573.6/586.4 ms

Without traffic conditioner, while uploading:
round-trip min/avg/max = 2041.4/2332.1/2427.6 ms

With conditioner, during 220kbit/s upload:
round-trip min/avg/max = 15.7/51.8/79.9 ms

With conditioner, during 850kbit/s download:
round-trip min/avg/max = 20.4/46.9/74.0 ms

When uploading, downloads proceed at ~80% of the available speed. Uploads
at around 90%. Latency then jumps to 850 ms, still figuring out why.

What you can expect from this script depends a lot on your actual uplink
speed. When uploading at full speed, there will always be a single packet
ahead of your keystroke. That is the lower limit to the latency you can
achieve - divide your MTU by your upstream speed to calculate. Typical
values will be somewhat higher than that. Lower your MTU for better effects!

A small table:

Uplink speed   |  Expected latency due to upload
--------------------------------------------------
32             |  234ms
64             |  117ms
128            |  58ms
256            |  29ms

So to calculate your effective latency, take a baseline measurement (ping on
an unloaded link), and look up the number in the table, and add it. That is
about the best you can expect. This number comes from a calculation that
assumes that your upstream keystroke will have at most half a full sized
packet ahead of it.

This boils down to:

   mtu * 0.5 * 10
   --------------  + baseline_latency
       kbit

The factor 10 is not quite correct but works well in practice.

Your kernel
-----------

If you run a recent distribution, everything should be ok. You need 2.4 with
QoS options turned on. 

If you compile your own kernel, it must have some options enabled. Most
notably, in the Networking Options menu, QoS and/or Fair Queueing, turn at
least CBQ, PRIO, SFQ, Ingress, Traffic Policing, QoS support, Rate
Estimator, QoS classifier, U32 classifier, fwmark classifier.

In practice, I (and most distributions) just turn on everything.

The scripts
-----------

The script comes in two versions, one which works on standard kernels and is
implemented using CBQ. The other one uses the excellent HTB qdisc which is
not in the default kernel. The CBQ version is more tested than the HTB one!

See 'wshaper' and 'wshaper.htb'. 

Tuning
------

These scripts need to know the 'real' rate of your ISP connection. This is
hard to determine upfront as different ISPs use different kinds of bits it
appears. People report success using the following technique:

Estimate both your upstream and downstream at half the rate your ISP
specifies. Now verify if the script is functioning - check interactivity
while uploading and while downloading. This should deliver the latency as
calculated above. If not, check if the script executed without errors.

Now slowly increase the upstream & downstream numbers in the script until
the latency comes back. This way you can find optimum values for your
connection. If you are happy, please report to me so I can make a list of
numbers that work well. Please let me know which ISP you use and the name of
your subscription, and its reputed specifications, so I can list you here
and save others the trouble.

Installation
------------

If you dial in, you can copy the script to /etc/ppp/ip-up.d and it will be
run at each connect.

If you want to remove the shaper from an interface, run 'wshaper stop'. To
see status information, run 'wshaper status'.

Known Shortcomings
------------------

Most windows SSH clients do not set TOS flags, so the wondershaper has a
hard time recognizing interactive ssh traffic from 'putty'. This appears to
be due to a shortcoming in windows.

The solution is to 'putty' to your linux gateway and ssh onwards from there.

There is another solution (prioritize small ssh packets) but that is for a
later version.

PROBLEMS
--------

If you get errors, add an -x to the first line, as follows:

#!/bin/bash -x

And retry. This will show you which line gives an error. Before contacting
me, make sure that you are running a recent version of iproute!

Recent versions can be found at your Linux distributor, or if you prefer
compiling, here: [ftp://ftp.inr.ac.ru/ip-routing/iproute2-current.tar.gz](ftp://ftp.inr.ac.ru/ip-routing/iproute2-current.tar.gz)

More information
----------------

Information on how this all works can be found on [http://lartc.org](http://lartc.org)
The Linux Advanced Routing & Traffic Control HOWTO site.

---

### Post by fignig on 2008-08-19
+ DOWNLINK=800
+ UPLINK=220
+ DEV=eth0
+ '[' '' = status ']'
+ tc qdisc del dev eth0 root
+ tc qdisc del dev eth0 ingress
+ '[' '' = stop ']'
+ tc qdisc add dev eth0 root handle 1: cbq avpkt 1000 bandwidth 10mbit
RTNETLINK answers: Operation not permitted
+ tc class add dev eth0 parent 1: classid 1:1 cbq rate 220kbit allot 1500 prio 5 bounded isolated
RTNETLINK answers: Operation not permitted
+ tc class add dev eth0 parent 1:1 classid 1:10 cbq rate 220kbit allot 1600 prio 1 avpkt 1000
RTNETLINK answers: Operation not permitted
+ tc class add dev eth0 parent 1:1 classid 1:20 cbq rate 198kbit allot 1600 prio 2 avpkt 1000
RTNETLINK answers: Operation not permitted
+ tc qdisc add dev eth0 parent 1:10 handle 10: sfq perturb 10
RTNETLINK answers: Operation not permitted
+ tc qdisc add dev eth0 parent 1:20 handle 20: sfq perturb 10
RTNETLINK answers: Operation not permitted
+ tc filter add dev eth0 parent 1:0 protocol ip prio 10 u32 match ip tos 0x10 0xff flowid 1:10
RTNETLINK answers: Operation not permitted
We have an error talking to the kernel
+ tc filter add dev eth0 parent 1:0 protocol ip prio 11 u32 match ip protocol 1 0xff flowid 1:10
RTNETLINK answers: Operation not permitted
We have an error talking to the kernel
+ tc filter add dev eth0 parent 1: protocol ip prio 12 u32 match ip protocol 6 0xff match u8 0x05 0x0f at 0 match u16 0x0000 0xffc0 at 2 match u8 0x10 0xff at 33 flowid 1:10
RTNETLINK answers: Operation not permitted
We have an error talking to the kernel
+ tc filter add dev eth0 parent 1: protocol ip prio 13 u32 match ip dst 0.0.0.0/0 flowid 1:20
RTNETLINK answers: Operation not permitted
We have an error talking to the kernel
+ tc qdisc add dev eth0 handle ffff: ingress
RTNETLINK answers: Operation not permitted
+ tc filter add dev eth0 parent ffff: protocol ip prio 50 u32 match ip src 0.0.0.0/0 police rate 800kbit burst 10k drop flowid :1
What is "flowid"?
Illegal "police"





is what arises as i tried to run the script from the folder it lies within.

---

### Post by fignig on 2008-08-20
anyone?

---

### Post by Elfy on 2008-08-20
There is a version in the repo

[http://packages.ubuntu.com/hardy/wondershaper](http://packages.ubuntu.com/hardy/wondershaper)

Assuming you have the repo set up you could install from synaptic or the terminal

```
sudo apt-get install wondershaper
```

---

