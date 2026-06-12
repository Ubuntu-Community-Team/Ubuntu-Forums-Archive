---
title: "Hardware recommendations for new sytems"
date: 2014-06-02
forum: New to Ubuntu
---

### Post by gabriel23 on 2014-06-02
I'm having trouble deciding what CPU/Video Card/Tuner I need to build a new system. Here is what I need the new system to do:

1) Record up to 2 channels (ATSC) at a time from an antenna.
A Hauppauge 2250 or HDHomeRun will do the trick. How do I chose between the two? The location of the antenna will be next to the HDTV. Are there better options than these two listed?

2) Handle commercial flagging and live HD TV.

3) One PC as the frontend/backend.

I'm having trouble trying to decide between buying an Nvidia card like a fanless GT430 from Zotac with a low end modern CPU (like a 4th generation Celeron or better) or an i3. The price would be similar, so which is the better option?

Since the system will be in my living room, I do care about noise and thus heat.

Thank you.

---

### Post by TheFu on 2014-06-02
Why put a noisy computer in the same room with the TV? Put it in a closet or "server room" elsewhere and just stream the content over a low cost playback device like a WD-TV Live or Chromecast or Roku.

There are some considerations you seem to have missed (at least from here).  
* commercial locating is non-trivial and requires processing. I do this as part of a complicated process that most people wouldn't like.
* Antennas really work best when placed higher - it is amazing the difference that 10ft can make in reception. I moved the antenna here from a 2nd story bedroom to the attic and added 30 more channels.
* I have 2 HDHR3s - LOVE THEM!  It also means that my TV recording system can run "inside" a virtual machine - I didn't need any new hardware at all.
* If the antenna is next to the TV, for live TV watching, just use the TV ATSC tuner. Much easier than going through a PC, streamer, and extra crap.

It seems you've already decided on MythTV.  When picking hardware for that system - the best/only resource is really the MythTV HCL.

Have you considered just buying a $50 DVR from Amazon and adding USB storage to it? I think you'll find it is much less hassle, unless you are already completely addicted to channel guides, season pass recordings and that stuff.

So, I should admit ... I've tried to get mythtv working a few times and always failed. That was long ago.  About 3-4 yrs ago, I finally setup Win7 media center to record stuff. It runs inside a virtual machine, as I said before. At the time, that meant no PCI/PCIe/x adapter could be used - I didn't want to dedicate an entire PC just for this.  

A few blog articles I've written on recording TV and antennas:
* [http://blog.jdpfu.com/2012/08/03/diy-hdtv-antenna-deployment-and-results](http://blog.jdpfu.com/2012/08/03/diy-hdtv-antenna-deployment-and-results)
* [http://blog.jdpfu.com/2012/02/06/running-windows7-media-center-inside-a-kvm-vm](http://blog.jdpfu.com/2012/02/06/running-windows7-media-center-inside-a-kvm-vm) records 4 streams concurrently, no problem.
* [http://blog.jdpfu.com/2011/10/20/commercial-removal-from-wtv-recordings](http://blog.jdpfu.com/2011/10/20/commercial-removal-from-wtv-recordings) (I think mythtv has this built-in)
* [http://blog.jdpfu.com/2011/02/21/xbmc-tips](http://blog.jdpfu.com/2011/02/21/xbmc-tips) - XBMC rocks.  With Plex added as the media manager/server is is the perfect playback solution for stored media for the entire house. However, Live TV needs something else.

Oh and if you plan to transcode from MPEG2 into something 3x more efficient like h.264, then you'll want a Core i5 or better CPU. That means more noise and provides more of a reason to put this PC in a different room.

My $150 XBMC box is silent, fanless, but so are the roku, chromecast, and WDTV devices. With a strong machine as the "server" that is capable of on-the-fly transcoding based on the rendering device, you don't need much of a playback device at all - provided plex server (best DLNA server I've found) is running. Plex works with roku, chromecast, etc ...

---

