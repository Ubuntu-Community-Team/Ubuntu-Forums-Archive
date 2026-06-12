---
title: "DLNA Server(mediatomb) &amp; android problem"
date: 2014-03-09
forum: New to Ubuntu
---

### Post by Erik_Moreno on 2014-03-09
I'm finishing my last year of Swedish high-school, as a project I decided to build my own fileserver from where I could access my series and movies from all my other media. ):P

I built a PC from spare parts and installed Ubuntu server (12.04 LTS). After installing some packages I installed the "synaptic package manager" and downloaded "mediatomb". So far so good, I can play media on my phone that is in the server, but for some reson almost all my video either cannot be played by my phone (Galaxy S3) or can only play auido. I've tried with diferent codecs and changing the trancoder lines in the mediatomb config (so that they trasform into mpeg), but my phone still wont play most videos. So far only the Wildlife.wmv plays, while an episode of Cosmos is only playing audio and an Archer episode wont play at all. I don't know where to go from here, but I'm enjoying working with Ubuntu (first time btw) and want to try and solve the issue before trying some other DLNA service like miniDLNA. Does anyone have any idea why they might not be playing correctly?

---

### Post by TheFu on 2014-03-09
Most newer playback devices require h.264 video and AAC audio inside either MP4 or MKV containers.  If you are transcoding to any other formats, then they will need to support the codecs you are sending. Some devices won't handle the higher resolutions either, so transcoding to 480p is the best answer.  Of course, transcoding anything on a weak system can take ... er ... days. I have a bunch of systems here and dno't bother transcoding on anything less than a Core i5. It just takes too long otherwise.  Once tried to transcode on a netbook and something that would be 20 minutes was going to take 18 hours on it.

I don't use mediatomb, so can't offer more help.  Might be worth changing the title for this post/thread to include it - since DLNA is generic.
I've used minidlna and plex and xbmc and Win7 Media Center.  On Android, I use BubbleDLNA as the controller for pretty much any DLNA device in the house.  For DLNA - I've found plex to be the most full featured. It doesn't get out of date more than a few minutes like the others.  Win7 is still showing media that was deleted last summer!

BTW, Cosmos hasn't aired here yet - not until this evening. I'm jealous!

---

### Post by Erik_Moreno on 2014-03-09
I've tried all the supported codecs for an S3, but most videos still wont play, I don't know if it's a problem on the server's part or on the S3's.
I'm going to fiddle with the mediatomb config a little bit more, see if I can find some more transcoding options, otherwise I will try out miniDLNA or plex. Why do you prefer Plex?
BubbleDNLA was much better controller than what I was using, so thanks for the tip.

BTW, I meant an original Cosmos episode, seemed fitting for testing the server today. I'm the one who gets to wait, until March 16!


EDIT: The error seemed to be on my S3's side. I could access the server after I factory retested my phone. Thanks for the help.

---

