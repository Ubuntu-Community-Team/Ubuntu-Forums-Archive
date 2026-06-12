---
title: "Is blu-ray playback possible?"
date: 2011-12-16
forum: New to Ubuntu
---

### Post by guyver_dio on 2011-12-16
Thinking about installing ubuntu on my htpc which has a blu-ray reader. Are there any native linux video players that will play blu-ray movies or will I have to try installing something like powerDVD in wine?

---

### Post by mastablasta on 2011-12-16
Does this help? : [https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD](https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD)
 
also see here for additional solutions: [http://ubuntuforums.org/showthread.php?t=1755829](http://ubuntuforums.org/showthread.php?t=1755829)

---

### Post by 3rdalbum on 2011-12-16
Basically, it involves ripping the contents of the disc first.

It's a bit of a "chicken and egg" scenario. The DRM on Blu-ray discs is distasteful, so fewer Linux users bought Blu-ray drives. Because few Linux users have Blu-ray drives, not many people have been working on a good way of playing back BDs, so development has been slow, and because of the poor support not many Linux users have bought Blu-ray drives...

---

### Post by guyver_dio on 2011-12-16
yeh thanks but not good enough, i'm not ripping blu-rays just to watch them. I want the htpc to be like any other hi-fi appliance, pop it in and it just works. 

That was the solution on windows too if you didn't have the money to buy one of the few media players licensed to support them. Maybe I'll give powerDVD a trial on this computer through wine first to see how it runs before deciding whether to change the htpc over.

Thanks again.

---

### Post by Basher101 on 2011-12-16
> **guyver_dio said:**
> yeh thanks but not good enough, i'm not ripping blu-rays just to watch them. I want the htpc to be like any other hi-fi appliance, pop it in and it just works. 

That was the solution on windows too if you didn't have the money to buy one of the few media players licensed to support them. Maybe I'll give powerDVD a trial on this computer through wine first to see how it runs before deciding whether to change the htpc over.

Thanks again.

curious to see if it works. I have a Samsung Blu-ray drive in my custom built PC...tho i do not own any blu-rays...i just bought and installed it to make it somewhat "future-proof" (if you see my specs below i think i did make quite the future proof system. It is just great to have made your own pc, espacially if linux runs better than windoze on it :3)

---

### Post by RomeReactor on 2011-12-16
Don't know how viable this is at the moment, but [libbluray]("http://www.videolan.org/developers/libbluray.html") (via this [Phoronix]("http://www.phoronix.com/scan.php?page=news_item&px=MTAyNjQ") article) might be worth a shot.

EDIT: Looks like it's not there yet.
> NB: Most commercial Blu-Ray are protected by AACS or BD+ technologies and this library is not enough to playback those discs.

---

### Post by mastablasta on 2011-12-19
powerDVD seems to have garbage rating with wine so no luck there i would guess.

---

### Post by jps1369 on 2012-02-20
Yes, it's possible. No, it's not perfect. 

The only way I've ever been able to do it was with a combination of XBMC and MakeMKV. It won't give you full menu functionality, but it will let you drop in a disc, and play the film.

This link is basically how I did it: 
[http://lifehacker.com/5621471/how-to-enable-blu+ray-playback-in-xbmc](http://lifehacker.com/5621471/how-to-enable-blu+ray-playback-in-xbmc)

This is kind of old, but it does work, or at least it did when I tried it. There's been a lot of progress since then, and with the release of VLC 2.0, and the impending release of XBMC Eden, there may be a simpler way. That libbluray that was mentioned above looks promising but I don't know much about it. 

It would be worth doing some digging in the XBMC forums for more current information. 

I've been able to play my previously decrypted blu-ray backup .iso's in VLC 2.0 on windows, but again, no menus. I don't know how it will handle a non-decrypted source, and I don't have a BD drive here to test. 

GOOD LUCK!

---

### Post by jps1369 on 2012-02-20
Found this today for playing encrypted blu-ray with VLC 2.0 

[http://forum.videohelp.com/threads/343705-VLC-Blu-ray-plugin-Watch-encrypted-Blu-rays-directly-in-VLC-2-0](http://forum.videohelp.com/threads/343705-VLC-Blu-ray-plugin-Watch-encrypted-Blu-rays-directly-in-VLC-2-0)

---

### Post by andrew.46 on 2012-04-24
Playback from the new vlc has consistently failed for me, fortunately makemkv is working well. Bit of a hassle but hopefully things will improve soon...

---

### Post by ubuntukid on 2012-04-28
> **andrew.46 said:**
> Playback from the new vlc has consistently failed for me, fortunately makemkv is working well. Bit of a hassle but hopefully things will improve soon...

Have you downloaded the KEYDB.cfg file for libaacs? If not it is easy to find on google by searching vlc aacs keys. Another possible problem is that vlc is choking on the bd menu on the disc. BD menu support is still very buggy in VLC, but if you check the no menu checkbox, it should work quite well. Discs protected with bd+ wont work.

---

### Post by andrew.46 on 2012-05-05
Indeed I finally have it working :). My preferred media player is actually MPlayer and some might find this useful in getting bluray playback with MPlayer under Precise Pangolin:

Howto: Build the svn MPlayer under the latest release version of Ubuntu
[http://www.andrews-corner.org/mplayer.html](http://www.andrews-corner.org/mplayer.html)

Works nicely with non bd+ disks and also is a great tool to receive the streams generated by makemkv.

---

