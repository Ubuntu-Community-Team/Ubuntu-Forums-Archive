---
title: "How to access to a MPC enabled Linux PC with another Windows based PC?"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by D.Sync on 2008-06-03
Any ideas for doing so?

I'm currently have 399+ albums resident on my laptop running on Ubuntu 8.04 and I really want to playback those albums through my main computer which running on Windows XP user.

I had installed both MPC in my laptop and the song playback run smoothly on GMPC.

What client should I used for accessing the music database on my laptop? Is there any easy setup guide for the client for Windows XP?

---

### Post by mbarak on 2008-06-03
Here's what you want:
[http://mpd.wikia.com/wiki/Windows_Compatibility](http://mpd.wikia.com/wiki/Windows_Compatibility)

Even if you connect to MPD on your laptop, the musif will play on your laptop speakers.  Look at "Streaming" your music (near the bottom)

---

### Post by cariboo on 2008-06-03
I use gnump3d works quite well on my 10,000+ collection of tracks.

Jim

---

### Post by D.Sync on 2008-06-03
> **mbarak said:**
> Here's what you want:
[http://mpd.wikia.com/wiki/Windows_Compatibility](http://mpd.wikia.com/wiki/Windows_Compatibility)

Even if you connect to MPD on your laptop, the musif will play on your laptop speakers.  Look at "Streaming" your music (near the bottom)

So by using IceCast, I can use my desktop PC to stream music from my laptop via LAN? Does it works on WAN too?

---

### Post by mbarak on 2008-06-03
Although I'm not at all familiar with icecast server I don't see why it shouldn't
All you would really need is your IP (or...dyndns ;)) and to make sure your icecast server accepts connections from outsite your network

You can combine both windows mpd clients with the icecast server
that way you can get winamp/itunes/whatever to just constantly play your icecast stream, and get a windows mpd client to manipulate the stream (ex: change songs)

---

