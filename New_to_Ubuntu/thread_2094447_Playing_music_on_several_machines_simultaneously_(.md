---
title: "Playing music on several machines simultaneously (no latency)"
date: 2012-12-13
forum: New to Ubuntu
---

### Post by zcacogp on 2012-12-13
Hello, 

I'm trying to play music on several machines simultaneously, with zero (or near-zero) latency, on a wireless network. The aim is to play music on three or four machines in different rooms in the same house, for a party. 

All the machines are running 12.10 Gnome-Remix. All of them are on a wireless network, with the music library being on a desktop machine. The other machines are laptops, two of which run 802.11b wireless (they are quite old) and the other of which runs 802.11g wireless. 

It seems that there are a number of ways of achieving this, and I've tried three, but all of them fail for one reason or another. 

1. Pulseaudio Device Chooser.

I've configured Pulseuadio Device Chooser, as per these instructions here: 

[http://www.unixmen.com/stream-music-wirelessely-using-pulseaudio-server-device-chooser/](http://www.unixmen.com/stream-music-wirelessely-using-pulseaudio-server-device-chooser/)

(using pavucontrol and paprefs). This seems like the most elegant solution, and I like it the most. It just about works with a single client on a wired network, but using a wireless network or more than one client and the network traffic load is too high and the sound is unacceptably choppy. (I posted about this [here (link)]("http://ubuntuforums.org/showthread.php?t=2071141"), but the response was simply that this is a limitation of wireless networks and they can't trasmit and recieve at the same time.)

2. Icecast2. 

I've installed Icecast2, and linked to it on the server using darkice. This works, and the sound is good, but the client machines all play a second or two behind the server. This means that the music in different rooms doesn't play simultaneously, which isn't good. (I have yet to try playing with MPD - is this likely to work any better?) 

3. Squeezebox.

I've installed Squeezebox Server, and configured client machines with softsqueeze, and this can play without latency (i.e. synchronised.) However it doesn't play smoothly (there are occasional gaps in playing), and I can't make it play in more than two places at one - it won't allow you to synchronise more than two machines. I don't know whether this is a limitation of the squeezebox/softsqueeze setup but I can't see how to get 'round it. 

It seems that these are the three main ways of doing what I am trying to achieve, but I haven't made any of them work. Am I trying to achieve the impossible? Are there other options I should try? Is there anything more I can do to make any of the above solutions work, by overcoming the problems with one of them? (I only need one of them to work!) 

All suggestions welcome - thank you. 


Oli.

---

### Post by tgalati4 on 2012-12-13
Put cable boxes in each room and tune to the same music channel.  

There is no zero-latency, IP/TCP protocol.  The nature of ethernet communication is latency (although small) and graceful degradation through packet retransmission and rerouting (which adds larger latency). 

There are dedicated music protocols that run over gigabit switches such as QSC's QSys network or CobraNet that can share traffic over high quality Cat6 networks, but they require expensive servers and endpoints.  For a home user, there is no simple way to drive a house party in multiple rooms and synchronize the acoustic delays so that you don't get weird phasing effects.

Each computer that is decoding the music stream has a slightly different quartz clock (to maintain the 44,100 kHz sampling frequency).  After a few minutes of several computers playing the same music, the clocks will drift apart and you will hear the latencies--this assumes zero network latency.  Add in network latency and you have an impossible situation.  You need a protocol that transmits a master clock and then synchronizes all playback based on that clock.

A better way acoustically to handle the situation is to have one primary sound system and use a 4-way line-out splitter and put some boom boxes around the house with cabling.  That way you have only one sound source and you are using analog amplification after that.  Keep the cable runs under 20' or you will get some acoustic delays (due to distance).

The most simple arrangement is to mix to mono and put 4 high-powered speakers in the center of the house pointed in 4 directions.  That will allow the sound to travel throughout the house without acoustic delays.

A more complicated arrangement is to use a 5.1 receiver and program your receiver to put 0 seconds delay on the front of house and a few milliseconds of delay on the back speakers and put those in a distant room.  You can tweak the delay such that the sound is coherent.  There are delay calculators on the web.

Linux has some wonderful tools and protocols to share music libraries and stream music and play to remote machines, but it can't play multiple locations with controlled delay.  What we need is a networked jackd protocol where xruns become network latency--yet another framework!

Or drop $50K and put in a real networked sound system:

[http://qscaudio.com/products/network/QSys/](http://qscaudio.com/products/network/QSys/)

(It actually runs a form of linux!)

---

### Post by zcacogp on 2012-12-14
tgalati4, 

Thanks - that's a pretty comprehensive reply. I get the impression that you may have looked into this area yourself, perhaps? 

So, I'm trying to acheve the impossible by doing it wirelessly. That's helpful as it means I won't spend any more time trying to make things happen that won't. Thank you. 

Laying cable is the obvious and simple solution (and what I have done in houses before). It's the sort of solution I like as it's something I understand (!) and it's very robust - once it's in, it's in, and very unlikely to suffer problems. Snag is that the architecture of our current house makes it difficult to do this and hence the desire for a wireless solution. 

Your explanation of the reasons for the latency was clear, thank you for that. I hadn't considered that two machines would 'drift' over time as the clocks move more and more out of sync. Running a network clock would be the solution, but surely that's not that hard to do? Once you have this, you could peg a lot of other stuff around it - and it would be useful for other network applications too; networked cinema (if such a thing exists) or networked data gathering for scientific purposes (again, I'm shooting in the breeze here!) 

Out of curiosity, how does the Apple Airport Express system work? Can't you play music from one machine to multiple Airport Express boxes? Does that have a system to overcome the latency issue? 

Thanks again. 


Oli.

ETA: That QSC system looks nice! Thanks for the link. I'm a little short on a spare $50k just at the moment tho', but I'll ask Santa nicely ... :)

---

### Post by tgalati4 on 2012-12-14
I do audio stuff as a day job, so I'm familiar with networked audio.

The last QSC audio system I commissioned had ~250 speakers, 36 amplifiers, and 90,000 watts covering 85,000 square feet.  It was networked with a combination of CAT6 and fiber optics.

[http://www.sheratonfairplexconferencecenter.com/](http://www.sheratonfairplexconferencecenter.com/)

I'm not familiar with Airport Express.  I've set up Apple TV and wireless transmission from iPads to Apple TV, but that is strictly point-to-point.

I have network time running on my home network using ntp with 2nd order drift corrections.  My server is accurate to within a few microseconds of national time sources.  This however doesn't correct for localized drift for audio sound cards--each card has it's own crystal so that it can decode 96 kHz super audio, 48 kHz audio, and more common, CD audio 44.1 kHz.  Network time will keep the machines in sync, but the music will still drift enough to be annoying.

Recording studios use master clocks to synchronize their 8 or 16-channel firewire input cards.  You could do the same with output cards and amplifiers and that will only set you back $10,000 or so.

Again, the easiest solution is one audio stream and high-quality, analog, 75 Ohm cable that can run 100 feet to your various output amplifiers.  If you have a decent sound card (M-Audio, PreSonus, etc) then you can use thinner, balanced microphone cable, or the thin, Honeywell signal wire to run around the house.

I use Gepco cable (now part of General Cable) for my installations:

[http://www.gepco.com/](http://www.gepco.com/)

Now there are a lot of bluetooth jam boxes that are available, but I'm not sure you can have one iphone or android phone stream bluetooth to multiple jam boxes.

I've played with multicast streaming (icecast and vlc) but again, you are at the mercy of network latency, Quality of Service, and sound card drift.  There are no cheap solutions.  There are several expensive solutions.  Digigram makes PC cards for radio stations and high-quality streaming:

[http://www.digigram.com/products/product_infos.php?prod_key=15000](http://www.digigram.com/products/product_infos.php?prod_key=15000)

---

