---
title: "Is streaming data to a TV, as easy as this?"
date: 2011-12-23
forum: New to Ubuntu
---

### Post by mikodo on 2011-12-23
Would this be a simple solution:

Ubuntu DE -> Samba -> Wired Connection -> Commercial Media Player -> TV?

I was entertaining dual-booting with Windows, to share from my computer, our pictures and video, from a NTFS data partition, to our living-room TV ->... then I thought, why!

Thanks.

---

### Post by diablo75 on 2011-12-23
I use PS3MediaServer, available here:

[http://code.google.com/p/ps3mediaserver/](http://code.google.com/p/ps3mediaserver/)

It requires Java to be installed.  Once you have java installed, you'll run the pms.sh file which will execute the java app.  You can use the Startup Application setting to auto-run the program to start every time the computer logs in to that users account.  It is a media server.  I can't say how well this works with other "commercial media players" but a majority of them are comparable with DLNA so it's worth a shot.

Here's a video I made about how to install it:

[http://www.youtube.com/watch?v=bvmlTpUXJBM](http://www.youtube.com/watch?v=bvmlTpUXJBM)

---

### Post by mikodo on 2011-12-24
Thanks diablo75, for your reply. As, it should be apparent from my post, I am just starting to think of ways to network. Yours' looks good, as does your video. 

Thanks, for the information.

---

### Post by Bucky Ball on 2011-12-24
If you just want to look at stuff on your local hard drive (this is not streaming) then why not just plug in a VGA cable if your TV can act as a monitor? That simple. 

You are also not talking about networking really as you are just plugging one machine into another to get the signal to where you want it. LAN (local area network) would have computer and media player communicating through your router, but of course you need a network-capable media player do this.

But, if you are suggesting plugging the computer into the media player via an ethernet cable you have that. Network through the router and then just connect to the computer (any computer on the network) through the media player (you should be able to work that out from the media player menu which appears on your TV and its manual). Having static IP addresses is the easiest way to do this as then they are permanent connections and you don't have to fish for the new IP and set up the network connection on the media player everytime you switch your computer off and on (DHCP served IP will change everytime you reboot).


Might help to provide the exact media player make and model and what it is actually capable of. Same with TV. ;)

---

### Post by mikodo on 2011-12-24
Thank you too, Bucky Ball. Even more information!

As to your explanations and question(s), about our hardware (T.V.; router; media player), we are buying our First LED big-screen TV; next year and I want to be able to connect to it from my computer, to share stuff with. I have no need, or at least not up until now, for a router, having just the one desktop computer.

So, I am a little confused as to what to do, to show binaries and pics on our new TV. I do know, I do not want to use wi-fi; we have very close neighbors, and we live in a two storey-home and basement where, I am not sure wi-fi would cover everywhere, adequately.

Your ideas, are helpful... food for thought and also give me some direction, for investigation.

:)

---

### Post by mikodo on 2011-12-24
I wish I could find someone in Saskatoon, that didn't use Microsoft software and Microsoft enabled hardware, to do this. I don't have a lot of time to learn how to use XBMC or Mythbuntu, while being a perennial noob, or so it seems.

---

### Post by mikodo on 2011-12-24
Good night!

---

### Post by Bucky Ball on 2011-12-24
VGA cable is easiest (just about all new LEDs have VGA plug so they can be used as monitor). Other options totally depend on the capabilities of your media player.

If you don't have a static IP set on your computer I would look into setting one up in preparation if you are going the network route. I would also look at how the media player deals with IPs and networking generally (if it's capable).

Regardless of the screen (new LED or old tele) you can start now with the networking and set it up then just replace the TV when you get the new one. Monitor makes no difference so start experimenting now. With the computer plugged into the media player you should be able to at least see it, probably under 'Network' on the media player menu. You will need to install Samba (probably, again depending on the capabilities of the media player) on your computer but that is easy enough. Good luck.

---

### Post by mikodo on 2011-12-25
double post

---

### Post by mikodo on 2011-12-25
> **Bucky Ball said:**
> VGA cable is easiest (just about all new LEDs have VGA plug so they can be used as monitor). Other options totally depend on the capabilities of your media player.

If you don't have a static IP set on your computer I would look into setting one up in preparation if you are going the network route. I would also look at how the media player deals with IPs and networking generally (if it's capable).

Regardless of the screen (new LED or old tele) you can start now with the networking and set it up then just replace the TV when you get the new one. Monitor makes no difference so start experimenting now. With the computer plugged into the media player you should be able to at least see it, probably under 'Network' on the media player menu. You will need to install Samba (probably, again depending on the capabilities of the media player) on your computer but that is easy enough. Good luck.

I think I have decided on using Samba with a media player. Samba doesn't look too hard (as you have said). I have started reading about different media players and their functions.

What you have given me, has taken me from a sense of hopelessness, to excitement about a new project, that seems plausible. I needed some general understanding of what to do. 

@ diablo75,

Your suggestion of PS3, would be a doable thing for me too! Your video explains installation well, and it would be fine. I just can't see my 65 year old wife, sitting in the living room with a PS3 controller though :>). But as you said, I could try using the software with another commercial media player.... hmmm.

Thank you, guys.

---

