---
title: "Trying to play a video in Firefox"
date: 2012-02-07
forum: New to Ubuntu
---

### Post by napakettu on 2012-02-07
Hi all,

First of all, sorry if I'm posting this in the wrong section, but I'm  new to both this forum and Ubuntu and hence thought that the beginners  section should be right.

I am using Firefox10 in Ubuntu 11.10 and I have been trying to watch the  EU plenary debates on the official website. Apparently, users of the  site can choose between using Windows Media Player or Quicktime. No  matter which one I select, all I see is a black rectangle where the  player is. I see all the controls, but nothing happens when I click  play.

I have done some research on these forums and found some similar posts,  but nothing seemed to work for me. I think that my problem is a  different one (and probably a very basic beginner thing) because I  actually do see a player ... only the video won't play. But there's no  message telling me I needed a certain player or plug-in or something.

Here's the video:
[http://www.europarl.europa.eu/ep-live/sv/plenary/search-by-date?start-date=20120202&end-date=20120203&date=20120202&format=wmv&askedDiscussionNumber=3](http://www.europarl.europa.eu/ep-live/sv/plenary/search-by-date?start-date=20120202&end-date=20120203&date=20120202&format=wmv&askedDiscussionNumber=3)

Can you play it in Ubuntu? If so, what plugin/player are you using?

I would really like to play the video in the browser rather than  download it because I want to be able to switch between the different  languages by clicking on the little boxes there. If I downloaded it, I  would only get one language at a time.

I have installed the mplayer and VLC plugins as well Totem. According to  the FF settings (settings, software tab), Windows Media Video is linked  to the Windows Media Plugin 10 (totem), and QuickTime video is linked  to the QuickTime Plug-in 7.6.6.

The video works fine in Windows, by the way (on the same machine)
Thank you for your help!

---

### Post by trozamon on 2012-02-07
Both windows media player plugin and quicktime plugin are from Gecko Media Player on my system. Just install the package gecko-mediaplayer and restart firefox. You might have to unistall totem, etc. to make sure gecko is the default.

---

### Post by Frogs Hair on 2012-02-07
I can't seem to interact with the player at all in Firefox even with Quicktime and Windows media compatible plug-in  installed .  :confused:

---

### Post by napakettu on 2012-02-08
Thank you for your replies. I did as you suggested, installed gecko, restarted FF and tried to play back the video - no success. As all other videos play just fine in Firefox, I suppose it's something specific to this website. It's a shame though, as Firefox plays these videos in Windows. Strange.

Any ideas?

---

### Post by philinux on 2012-02-08
> **napakettu said:**
> Hi all,

First of all, sorry if I'm posting this in the wrong section, but I'm  new to both this forum and Ubuntu and hence thought that the beginners  section should be right.

I am using Firefox10 in Ubuntu 11.10 and I have been trying to watch the  EU plenary debates on the official website. Apparently, users of the  site can choose between using Windows Media Player or Quicktime. No  matter which one I select, all I see is a black rectangle where the  player is. I see all the controls, but nothing happens when I click  play.

I have done some research on these forums and found some similar posts,  but nothing seemed to work for me. I think that my problem is a  different one (and probably a very basic beginner thing) because I  actually do see a player ... only the video won't play. But there's no  message telling me I needed a certain player or plug-in or something.

Here's the video:
[http://www.europarl.europa.eu/ep-live/sv/plenary/search-by-date?start-date=20120202&end-date=20120203&date=20120202&format=wmv&askedDiscussionNumber=3](http://www.europarl.europa.eu/ep-live/sv/plenary/search-by-date?start-date=20120202&end-date=20120203&date=20120202&format=wmv&askedDiscussionNumber=3)

Can you play it in Ubuntu? If so, what plugin/player are you using?

I would really like to play the video in the browser rather than  download it because I want to be able to switch between the different  languages by clicking on the little boxes there. If I downloaded it, I  would only get one language at a time.

I have installed the mplayer and VLC plugins as well Totem. According to  the FF settings (settings, software tab), Windows Media Video is linked  to the Windows Media Plugin 10 (totem), and QuickTime video is linked  to the QuickTime Plug-in 7.6.6.

The video works fine in Windows, by the way (on the same machine)
Thank you for your help!

Nope not working here. It's trying to use the totem plugin. It wont work if right click open with totem it displays an error. Using right click and copy then paste the url into VLC produces this error.

> Your input can't be opened:
VLC is unable to open the MRL 'rtsp://vodwms.europarl.europa.eu/wmv/nas/nasvod02/vod0602/2012/wm/VODChapter_20120202_10180100_10385000_3a70ff31135260744e570e7.wmv?wmcache=0'. Check the log for details.



---

### Post by klytu on 2012-02-08
> **napakettu said:**
> Hi all,

First of all, sorry if I'm posting this in the wrong section, but I'm  new to both this forum and Ubuntu and hence thought that the beginners  section should be right.

I am using Firefox10 in Ubuntu 11.10 and I have been trying to watch the  EU plenary debates on the official website. Apparently, users of the  site can choose between using Windows Media Player or Quicktime. No  matter which one I select, all I see is a black rectangle where the  player is. I see all the controls, but nothing happens when I click  play.

I have done some research on these forums and found some similar posts,  but nothing seemed to work for me. I think that my problem is a  different one (and probably a very basic beginner thing) because I  actually do see a player ... only the video won't play. But there's no  message telling me I needed a certain player or plug-in or something.

Here's the video:
[http://www.europarl.europa.eu/ep-live/sv/plenary/search-by-date?start-date=20120202&end-date=20120203&date=20120202&format=wmv&askedDiscussionNumber=3](http://www.europarl.europa.eu/ep-live/sv/plenary/search-by-date?start-date=20120202&end-date=20120203&date=20120202&format=wmv&askedDiscussionNumber=3)

Can you play it in Ubuntu? If so, what plugin/player are you using?

I would really like to play the video in the browser rather than  download it because I want to be able to switch between the different  languages by clicking on the little boxes there. If I downloaded it, I  would only get one language at a time.

I have installed the mplayer and VLC plugins as well Totem. According to  the FF settings (settings, software tab), Windows Media Video is linked  to the Windows Media Plugin 10 (totem), and QuickTime video is linked  to the QuickTime Plug-in 7.6.6.

The video works fine in Windows, by the way (on the same machine)
Thank you for your help!

Weird. I can play this video in Firefox with the Gecko plugin running Kubuntu; but it doesn't play at all in Firefox with the same plugin running Ubuntu. I tried turning off Compiz in Ubuntu and using several different players, but no joy. Could it be that the issue is some odd interaction with the Gnome desktop environment?

---

### Post by HiImTye on 2012-02-08
make sure you remove the totem plugin
```
sudo apt-get remove totem-mozilla
```

---

### Post by napakettu on 2012-02-08
Thank you all!

> **HiImTye said:**
> make sure you remove the totem plugin
```
sudo apt-get remove totem-mozilla
```

It's sort of half-working now: The video plays, but I cannot interact with it, i.e. I cannot jump to specific time or switch the language.

---

### Post by wolfen69 on 2012-02-08
> **HiImTye said:**
> make sure you remove the totem plugin
```
sudo apt-get remove totem-mozilla
```

Thanks for the helpful tip. Video now works. I didn't realize I had totem-mozilla installed. Then again, it was never a problem for me before.

---

### Post by KillianO92 on 2012-02-08
Just kind of piggy backing his post, I was trying to play this video __[http://www.wimp.com/performancegoosebumps/](http://www.wimp.com/performancegoosebumps/) and others on that site but was unable to do so. It would show it perpetually loading but it had the player. Any ideas?

---

### Post by uRock on 2012-02-08
> **KillianO92 said:**
> Just kind of piggy backing his post, I was trying to play this video __[http://www.wimp.com/performancegoosebumps/](http://www.wimp.com/performancegoosebumps/) and others on that site but was unable to do so. It would show it perpetually loading but it had the player. Any ideas?

Plays fine here. Use FlashAid plugin to get the proper flash for your system. [https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

---

### Post by KillianO92 on 2012-02-08
> **uRock said:**
> Plays fine here. Use FlashAid plugin to get the proper flash for your system. [https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

Alright, I tried that and still no luck. Any other ideas?

--EDIT--

Wait I retract that statement, I get an error when I try to download the plugin. It says there is an error connecting to addons.mozilla.org

---

