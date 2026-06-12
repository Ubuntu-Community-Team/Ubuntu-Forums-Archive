---
title: "Music for a party - Simultaneous playback possible?"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by Ampulse on 2008-09-20
Hi there!

I'm having a party at my house in 2 weeks and I was wondering:

Is it possible to somehow play the music on my ubuntu pc and a windows pc more or less simultaneously?
The idea is to create the illusion of only one "stereo" playing.

PS: I tried to search, but due to my limited english I didn't find anything other than topics focused on hosting music.

Greetings,
Ampulse

---

### Post by jualin on 2008-09-20
Is all the music in the same PC?

---

### Post by Ampulse on 2008-09-20
Yes! You're fast!

---

### Post by 50words on 2008-09-20
Why? Can't you just run the music out of two or more sets of speakers from either computer? You can do it with or without wires, but it might require a trip to Radio Shack to get a cable splitter for doing it with wires.

---

### Post by Ampulse on 2008-09-20
@50-words

That is an option, of course. But i figured if I could somehow stream the music playing on the ubuntu machine via w-lan to the windows pc it would be a) cheaper and b) hassle-free.

Plus I thought I would maybe be able to control the playback via ssh or http with my cell-phone.

---

### Post by jualin on 2008-09-20
There is a program called Mixxx which you can find in the repositories and basically lets you play two or more songs at the same time. I am not sure if this is what you want, but you should give it a try. Hope this helps!

*edit

This is the command to install it using the terminal > sudo apt-get install mixxx

---

### Post by jualin on 2008-09-20
[This is the website]("http://www.mixxx.org/") and in there you have a direct download link for Ubuntu.

---

### Post by Ampulse on 2008-09-20
I think I might have to clarify what I'm searching:

I want to press "play" on my ubuntu box and have the playback of the same song starting at the same time on my ubuntu box AND my windows pc (which is located in another room).

Thanks for your support so far, but from what I can see Mixxx is some kind of DJ tool? Maybe i missed something.

Greetings,
Ampulse

---

### Post by dioltas on 2008-09-20
Maybe mpd could do this. Im think you can set it up as a music server, and then stream music to your windows pc.

Here's the site, [http://www.musicpd.org/](http://www.musicpd.org/).

Would probably be easier and more reliable to just run wires imho, or get wireless speakers I suppose, but then you'd have pay for them...

---

### Post by jualin on 2008-09-20
> **dioltas said:**
> Maybe mpd could do this. Im think you can set it up as a music server, and then stream music to your windows pc.

[Here is something that ]("http://www.engadget.com/2005/11/29/how-to-stream-almost-anything-using-vlc/")expands what dioltas suggested. Basically you would stream the music from your Windows PC to the network and then use VLC in Ubuntu to "listen" to that stream (this will play the Windows PC music on Ubuntu). Then just opening another music player in Ubuntu will be used to play the music on Ubuntu. Hope this helps!

---

### Post by Ampulse on 2008-09-20
Thank you all, I will look into that.

---

### Post by mc4100 on 2008-09-20
It might sound crazy, but could this be the first ever use for pulseaudio's networking features and an Ubuntu LiveCD? ;)

---

### Post by Ampulse on 2008-09-20
that sounds about right.

---

### Post by Ampulse on 2008-09-20
Wait -  is it possible to receive a pulseaudio stream in windows? Because the windows machine (=laptop :(  )would have to be set up using ndiswrapper which is pretty fiddly on that laptop if I recall it right.

---

### Post by jualin on 2008-09-20
You don't need to run Ubuntu in both computers. You can stream the music from your Windows computer using VLC for Windows. And pick up the network stream using VLC in Ubuntu. Hope this makes it a bit clear.

---

### Post by mc4100 on 2008-09-20
You could be in luck:
> PulseAudio has been tested on Linux, Solaris, FreeBSD, Windows 2000 and Windows XP. It should also run on all other POSIX and Windows systems, but may require new backends to handle their sound systems. 

---

### Post by Ampulse on 2008-09-20
Yay! Great. Thank's for the professional and quick help.

---

### Post by markbuntu on 2008-09-21
Be aware that streaming through a network will cause delays. The two computers will not be totally in sync but if they are far enough apart, two or three rooms, not many people will notice. If you had a third computer that streamed to both....

But then again, I have notice that when two applications like rythmbox and xmms are playing the same internet radio stream on the same machine playback is not totally in sync, there is a slight to large delay effect depending on the buffer size in the players and the start up sequence. You may be able to get better synchronization of playback streams by adjusting the buffers and startup sequence in the players.

Anyway, give it a try and be sure to come back here and let us know how it worked out.

---

### Post by Ampulse on 2008-09-22
Ok, I tried streaming it via vlc from the ubuntu box to the windows pc and *surprise* there was a small but clearly notable latency. I'm gonna play around with the cache settings a bit, but I'm convinced that's not gonna do it. Next stop: Using a third computer to stream to the other two. 

Greetings

---

### Post by markbuntu on 2008-09-22
I have heard that using netjack through jack can sync sound cards in different machines but I have no idea how to set that up but there is some vague info here:

[http://netjack.sourceforge.net/](http://netjack.sourceforge.net/)

But the you could use djplay, even better.

---

### Post by tcrichton on 2008-11-26
Hi Ampulse,

Did you get anywhere with this?

I've got the same concept this weekend, couple of laptops dotted around the house, one PC (linux/windows) acting as the server...

Was planning on using VLC to multicast the stream across the network, setting the cache on each machine to the same...

Did you find another solution? I tried this before with Winamp and Shoutcast but the delay was too obvious...

Tristan.

---

### Post by billgoldberg on 2008-11-26
If the two pc's in the same network (connected to the same router), this can be done.

There could be better ways to do this, but this is how i would do it.

First make sure SAMBA is installed and works:

[http://linuxowns.wordpress.com/2008/10/28/share-ubuntu-folders-with-windows-samba/](http://linuxowns.wordpress.com/2008/10/28/share-ubuntu-folders-with-windows-samba/)

Then just play the playlist you made before the party on the Windows pc.

Go to your Ubuntu pc, play the same playlist and make sync them, so the songs run at the same time.

However, when someone asks for a song or something, you are screwed.

--

A more difficult way, but better, is to use shoutcast.

This is sort of a guide (a bit outdated) but it should get you started.

[http://cowboyfrank.net/real/RadioStation.htm](http://cowboyfrank.net/real/RadioStation.htm)

After you installed it, let the stream play on both computers.

Then if you change the song on the server (Ubuntu pc), the Vista pc will change with it.

I haven't actually done this, but it should work.

---

### Post by tcrichton on 2008-11-26
Thanks Bill,

I've used shoutcast before but there was an unfortunate delay.

I was hoping to be able to cater for those asking for specific tracks :-/

Running VLC in multicast and turning off the cache seems to be working ok at the moment... (until I involve the wifi network... hmm... ) another bonus of being able to control VLC from my iPhone will make it easier too.

Thanks for your advice,

Tristan.

---

### Post by porteclefs on 2008-11-26
you could sit at your ubuntu computer and have a friend at your windows computer and you could count out loud "1, 2, 3" and then click play!!
:)

---

### Post by Ampulse on 2008-11-26
I gave up... pulse audio was way above my head and vlc was too laggy :(

---

### Post by tcrichton on 2008-11-27
I've managed to get VLC in sync over LAN by setting the cache to 0ms using multicast, but not over wifi... it just chops up... I assume this is down to the multicast traffic being sent to each wifi client therefore saturating the wifi bandwidth...

Will try specifying IPs...

PulseAudio looks like it also uses multicast or unicast so I guess in essence its the same principles...

I'll have another crack using unicast on VLC and see how I get on...

Thanks for the advice everyone!

Tris.

---

### Post by nothingspecial on 2008-11-27
Try squeezecenter with soffsqueeze.

It is actually software to use with a streaming device but there is a java app you can put on both desktops that will sync quite happily

[http://www.slimdevices.com/pi_features.html](http://www.slimdevices.com/pi_features.html)

---

### Post by tcrichton on 2008-11-27
> **nothingspecial said:**
> Try squeezecenter with soffsqueeze.

It is actually software to use with a streaming device but there is a java app you can put on both desktops that will sync quite happily

[http://www.slimdevices.com/pi_features.html](http://www.slimdevices.com/pi_features.html)

That looks ace! Thanks so much for posting! How did I not know about this... now I want some of those slim devices!

Tris.

---

### Post by nothingspecial on 2008-11-27
> **tcrichton said:**
> That looks ace! Thanks so much for posting! How did I not know about this... now I want some of those slim devices!

Tris.

Watch out, it could cost you. I`ve got 3.

---

### Post by tcrichton on 2008-11-27
> **nothingspecial said:**
> Watch out, it could cost you. I`ve got 3.

And you can get the same music to play on all 3 in sync?

Oh and just incase you have an iPhone/iPod touch, I've seen this: [http://penguinlovesmusic.de/](http://penguinlovesmusic.de/)

There's the App Store one or there's the files for a web interface, app store = £5.99, web interface = free.

Thanks again!!

Tris.

---

### Post by nothingspecial on 2008-11-27
> **tcrichton said:**
> And you can get the same music to play on all 3 in sync?

Oh and just incase you have an iPhone/iPod touch, I've seen this: [http://penguinlovesmusic.de/](http://penguinlovesmusic.de/)

There's the App Store one or there's the files for a web interface, app store = £5.99, web interface = free.

Thanks again!!

Tris.

You can sync all 3, or 2 and have the other one play something else. You can also sync all 3 with the softsqueeze applet on your pc and have the same music in four different rooms.

As for the iphone app (and I don`t have one - not into drm) I would recommend squidgy.
[http://www.apptism.com/apps/squidgy](http://www.apptism.com/apps/squidgy)

I have to declare an interest though. My brother-in-law is the dev and my 6 year old son named it. He`s the one who got me started on this whole linux thing in the first place.

(brother in law that is, not 6yr old son)

---

### Post by tcrichton on 2008-11-27
> **nothingspecial said:**
> You can sync all 3, or 2 and have the other one play something else. You can also sync all 3 with the softsqueeze applet on your pc and have the same music in four different rooms.

As for the iphone app (and I don`t have one - not into drm) I would recommend squidgy.
[http://www.apptism.com/apps/squidgy](http://www.apptism.com/apps/squidgy)

I have to declare an interest though. My brother-in-law is the dev and my 6 year old son named it. He`s the one who got me started on this whole linux thing in the first place.

(brother in law that is, not 6yr old son)

Wicked, thanks for the tip, I'll take a look at the app!

Thanks again for your help and advice!

Tristan.

---

