---
title: "Transmission 2.82 problems"
date: 2013-10-24
forum: New to Ubuntu
---

### Post by nLpPyXR on 2013-10-24
I posted earlier on the "Networking and Wireless" board but I've gotten zero responses so far so I thought I'd try here as well. My apologies if doing that is not kosher.

I'm on Lubuntu 13.10 (32bit), I don't have a router, just a regular SB5102 Cable  Modem by Motorola hooked directly to my PC, I have completely disabled  the firewall (and made sure of it with sudo ufw status verbose). I can  download and browse perfectly fine through Firefox, however all my torrents appear to be seeding yet  there are no peers, as in, Transmission says "0 peers of 0 peers  connected", and when I go to Trans' settings any and all ports I've tried are closed.

Any other info you guys need I'd be more than happy to give, just let me know what I can do.

---

### Post by Johan De Cauwer on 2013-10-24
Well, I suppose you want to make a torrent seed server in order to make content available. I looked that up and found [http://ubuntuforums.org/showthread.php?t=1371265](http://ubuntuforums.org/showthread.php?t=1371265) Or did you mean leeching, with other words do you have problems downloading?

---

### Post by nLpPyXR on 2013-10-24
I have no problems downloading; and thanks for the reply but that thread doesn't help me, or at least I'm too much of a noob to know how it would.

From my understanding, once Transmission (or any torrent client for that matter) is up and running, and downloads are done, you should automatically start seeding which is to say you become a seeding server. The problem is that without an open listening port (which is my problem, I think) you can't really seed anything.

---

### Post by nLpPyXR on 2013-10-26
Please excuse the bump but I'm inches away from switching back to Windows XP merely because I can't seed on Lubuntu and the private trackers I'm in might ban me. I've been to the official Transmission forums and IRC channel over at Freenode and no one has been able to pin point what's wrong despite several suggestions and tests.

This HAS to be something in Lubuntu acting up due to the fact that everything was working for me a few days ago when I was still on MS Win and running utorrent. PLEASE, HELP ME! I don't wanna have to go back to my old OS after I've discovered the wonders of Ubunutu and LXDE.

---

### Post by LuvLinuxOS on 2013-10-26
Have you set your seeding preferences?

[> ~LuvLinuxOS~]("http://luvlinuxos.blogspot.com")

---

### Post by nLpPyXR on 2013-10-26
> **LuvLinuxOS said:**
> Have you set your seeding preferences?

[IMG]http://i.imgur.com/AMzT8xH.png[/IMG]

I guess so; I've tweaked the Transmission settings if that's what you mean.

---

### Post by v1k1ng1001 on 2013-10-26
You could try another bittorrent client like qbittorrent and see if you have the same difficulties.  That way you'll know whether or not the problem is with transmission or with something else.

---

### Post by nLpPyXR on 2013-10-26
I just got done trying both kTorrent and qBitTorrent; both have the same issues.

---

### Post by nLpPyXR on 2013-11-02
My ISP changed every client's IP  address to a dynamic one by default, so without calling them and asking  to get a static IP (which comes with every port open by default)  there's just nothing you can do, regardless of wether or not you have a  router and no matter what amount of tweaking or trouble-shooting you go through.

Many thanks to everyone who  offered suggestions, both here and in the official Ubuntu IRC channel. Sorry for wasting everyone's time.

---

