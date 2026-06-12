---
title: "lubuntu freezes after starting spotify"
date: 2013-05-09
forum: New to Ubuntu
---

### Post by wim12 on 2013-05-09
Fornewly I installed Lubuntu, and am very happy for it. I can see live tv in chromium with flash
But after starting spotify up my pc freezes
I found two links regarding this problem:
[http://ubuntuforums.org/showthread.php?t=2104226](http://ubuntuforums.org/showthread.php?t=2104226)   Installed [COLOR=#000000]libruby, but this didn't help
[/COLOR][http://ubuntuforums.org/showthread.php?t=1974984](http://ubuntuforums.org/showthread.php?t=1974984)  Couldn't find [COLOR=#000000]~/.cache/Spotify, but deleted spotify on my desktop and installed spotify once more with wine. My pc still freezes so that I can't use spotify

[/COLOR][COLOR=#000000]My pc: desktop, fujitsu-siemens, 7 years old, intell pentium 4 cpu, 2,6 ghz, 1,5 gb ram, radeon 9200 sec[/COLOR][COLOR=#000000]

any suggestions?



[/COLOR]

---

### Post by DuckHook on 2013-05-09
I don't use Spotify so am only researching on your behalf, but [Wikipedia]("http://en.wikipedia.org/wiki/Spotify") states:> As of version 0.4.3, it is possible to also play back local MP3 and AAC files, though this does not work in Linux using Wine because Spotify is "...blocking codecs with the identifier "WINE-MPEG3&#8243; until the Wine system works satisfactorily."[79] However, the native Linux version supports local files.Further Googling reveals that Linux port is in "preview" stage--don't know whether this means alpha or beta, but instructions for installing are [here]("https://www.spotify.com/int/download/previews/").

Again, noting that I know nothing specifically about Spotify, WINE is hit or miss with many Windows apps. It's the nature of WINE. WineHQ.AppDB has mixed reports about compatibility depending on Wine version and Spotify version. Results [here]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=8514"). Have you tried the native Linux port?

---

### Post by 25tom on 2013-05-09
Welcome to Ubuntu Forums!

As a Spotify/Ubuntu user, I have avoided installing the app, as I find that the new web player at [http://play.spotify.com](http://play.spotify.com) is much smoother and requires no installation. This is even though my computer is 8 years old and usually rather slow! Try it out, and if it works OK for you, uninstall the Spotify app. Happy Spotifying! :)

---

### Post by DuckHook on 2013-05-09
> **25tom said:**
> As a Spotify/Ubuntu user, I have avoided installing the app, as I find that the new web player at [http://play.spotify.com](http://play.spotify.com) is much smoother and requires no installation.

+1

Simple is always best.

---

### Post by ikt on 2013-05-09
> **DuckHook said:**
> I don't use Spotify so am only researching on your behalf, but [Wikipedia]("http://en.wikipedia.org/wiki/Spotify") states:Further Googling reveals that Linux port is in "preview" stage--don't know whether this means alpha or beta

It be 'google beta' or Ubuntu LTS quality. Been running the spotify preview and it has improved a lot recently.

---

### Post by wim12 on 2013-05-12
Play.spotify plays smoothly, and is very easy compared to the troubles I had with installing spotify.
I am only a beginner in Lubuntu -linux, but I get the impression that my pc has problems with the cache. Lubuntu sometime comes with the message: waiting for cache, and than sometimes freezes. Could there be solutions for that: change the amount of memory that gets used to cache?

---

### Post by wim12 on 2013-06-16
I succeeded installing spottify after installing PlayOnLinux. It works fine now.

---

