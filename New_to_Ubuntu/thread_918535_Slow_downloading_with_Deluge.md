---
title: "Slow downloading with Deluge"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by Wonslung on 2008-09-13
I'm not sure if this is the right forum or not but i just wanted to share my story.

I've recently put ubuntu 8.04 on my laptop, along with one of my older pc's, about a year ago or so i tried ubuntu and loved it but i still used so many windows programs and it was pretty daunting to learn a new os.  I'm now ready to make the switch and so so, i've been using lots of different programs playing with settings and learning the os.

The torrent program that comes with ubuntu is pretty bad if you ask me, i did some forum browsing and ended up settling on Deluge....i've been using it for maybe 3-4 days and no matter what i've done with settings, i've had lots of issues....i'd either have horribly slow downloads, or mediocre downloads but horrible browsing while downloading....i figured it was settings but i gotta tell ya, i just switched to ktorrent and it's like night and day, i'm now getting downloads of 400-500 Kb/s with no slow down to my browser....

the settings are identical, it's just bizarre if you ask me....

what would cause this? i really liked the look of deluge, could it just be writen that badly?  is it perhaps a compatibility issue?  :lolflag:

do some trackers not like some programs?

---

### Post by swoll1980 on 2008-09-13
Sound like a firewall issue to me. Install the port forwarding plugin (if it's not allready) then forward the ports

---

### Post by RomeReactor on 2008-09-13
> **swoll1980 said:**
> Sound like a firewall issue to me. Install the port forwarding plugin (if it's not allready) then forward the ports

I haven't used either Deluge or Ktorrent for a while so I don't remember if Ktorrent by default uses different ports than Deluge, but this might just be the case. They also behave slightly different, so similar settings on both produce different results. Remember to open the correct ports on your firewall (in case you're using Firestarter, UFW, or any other) and on your modem/router. And setting upload speeds to around 90% of your total uplaod also helps.

---

### Post by Wonslung on 2008-09-13
> **RomeReactor said:**
> I haven't used either Deluge or Ktorrent for a while so I don't remember if Ktorrent by default uses different ports than Deluge, but this might just be the case. They also behave slightly different, so similar settings on both produce different results. Remember to open the correct ports on your firewall (in case you're using Firestarter, UFW, or any other) and on your modem/router. And setting upload speeds to around 90% of your total uplaod also helps.



i had it setup correctly, i'm sure of it.

all the ports were set correctly, i tried it with upnp AND manual port forwarding to see if it would make any difference.

like i said, i have virtually the same settings in ktorrent and it works like a charm.....i triple checked all settings, checked forums, did google searches.....it's just odd...when using deluge, i had one of 2 choices, i could get mediocre download speeds and slow browsing, i could get normal browsing and terrible torrent speeds....

no matter what i did i was suffering,...i was starting to think it was a linux issue but it's obviously not because when i use ktorrent, i get 300 Kb/s averages and i've seen it spike up to 800, while maintaining good browsing....

it was very strange, if i throttled my uploading speed in deluge, my browsing got slightly better but my downloads slowed way down...and what's even more odd, is i'm seeing much higher upload speeds now on my torrents with no loss in browser speed...

anything above 50kb/s in deluge and pages would load 30-45 seconds late, i'm doing 400kb/s right now up and it's not even noticeable....

---

### Post by RomeReactor on 2008-09-13
Well, as I said, even with similar settings clients behave differently. As an example, Deluge was my preferred client before Hardy, and now I'm using Transmission; in my case it works very well, and lets me browse adequately. The number of seeders/leechers per torrent is also something to take into account.

---

### Post by Wonslung on 2008-09-13
> **RomeReactor said:**
> Well, as I said, even with similar settings clients behave differently. As an example, Deluge was my preferred client before Hardy, and now I'm using Transmission; in my case it works very well, and lets me browse adequately. The number of seeders/leechers per torrent is also something to take into account.
yah, it's just amazing how ktorrent gives me such a drastic change....i tried some of the same exact torrents, and the difference is astonishing.

---

