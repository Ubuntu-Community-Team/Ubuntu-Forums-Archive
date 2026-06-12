---
title: "[SOLVED] simple question low priority: music plays on hover over?"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by iansane on 2008-09-03
Hi, I was wondering if anyone knows what is playing music on my system when I hover over it. I read another post that says its vorbis-tools and mpg321 but that can't be because I checked and neither of them is installed.

I do however have every media player on the planet installed as none of them will play 100% everything no matter how many ubuntu extras and restricted codecs I install. If you say there is one, I'll send you a file that it won't play. Anyway no more ranting. Back to the question.

Anyone know?

---

### Post by tuxxy on 2008-09-03
> **iansane said:**
> Hi, I was wondering if anyone knows what is playing music on my system when I hover over it. I read another post that says its vorbis-tools and mpg321 but that can't be because I checked and neither of them is installed.

I do however have every media player on the planet installed as none of them will play 100% everything no matter how many ubuntu extras and restricted codecs I install. If you say there is one, I'll send you a file that it won't play. Anyway no more ranting. Back to the question.

Anyone know?

VLC never failed me =p

---

### Post by mc4man on 2008-09-03
> what is playing music on my system when I hover over it

Totem ( either gstreamer or xine depending on what you've set

---

### Post by t0p on 2008-09-03
> **tuxxy said:**
> vlc never failed me =p

+1.

---

### Post by kostkon on 2008-09-03
> **iansane said:**
> Hi, I was wondering if anyone knows what is playing music on my system when I hover over it. I read another post that says its vorbis-tools and mpg321 but that can't be because I checked and neither of them is installed.

I do however have every media player on the planet installed as none of them will play 100% everything no matter how many ubuntu extras and restricted codecs I install. If you say there is one, I'll send you a file that it won't play. Anyway no more ranting. Back to the question.

Anyone know?
For additional codecs try installing the Windows codecs package (called *w32codecs* for 32bit and *w64codecs* for 64bit systems) that is offered by the [*Medibuntu*]("http://medibuntu.org/") repository.

Also make sure that the package *gstreamer0.10-pitfdll* is installed (it allows Gstreamer-based media players to use the above codecs).

---

### Post by iansane on 2008-09-03
OK so maybe I should have left that part out about the media players. I wasn't looking for one. Like I said I have them all installed. If vlc, totem, mplayer, zine, or gstreamer never failed you it's cause you haven't tried playing every file type that exists. Sooner or later you'll come across something that won't play or won't play right.

Anyway, I just wanted to know which one is playing the mp3's when I hover over it since neither vorbis-tools, mpg321, or mpg123 is installed.

Just trying to figure out what's going on under the hood with this. It's a really cool function. I don't mess with music much but I don't think my system has been always doing this since I think I would have noticed it before.

---

### Post by iansane on 2008-09-03
> **kostkon said:**
> For additional codecs try installing the Windows codecs package (called *w32codecs* for 32bit and *w64codecs* for 64bit systems) that is offered by the [*Medibuntu*]("http://medibuntu.org/") repository.

Also make sure that the package *gstreamer0.10-pitfdll* is installed (it allows Gstreamer-based media players to use the above codecs).

OMG!! I appreciate the replys but like I said all of this is installed and none of them plays everything. **EVERYTHING**
I really shouldn't complain cause I was always having to add codecs to my clasic windows player for something and at least these players are provided for free on a free OS unlike windows. 

My fault for adding in the rant about the media players. I'm sorry I included that part.

---

### Post by Joeb454 on 2008-09-03
I think it's a nautilus plugin. It was added as standard from Ubuntu 7.10 I believe :)

Also, you need to change your previous post to [noparse]**EVERYTHING**[/noparse] if you want it to be **bold** ;)

---

### Post by kostkon on 2008-09-03
> **iansane said:**
> OMG!! I appreciate the replys but like I said all of this is installed and none of them plays everything. <b>EVERYTHING<b>
I really shouldn't complain cause I was always having to add codecs to my clasic windows player for something and at least these players are provided for free on a free OS unlike windows. 

My fault for adding in the rant about the media players. I'm sorry I included that part.
I use totem-xine and it plays everything I throw at it.

Could you give an example of a audio/video file/format/codec that you cannot play?

---

### Post by iansane on 2008-09-03
> **Joeb454 said:**
> I think it's a nautilus plugin. It was added as standard from Ubuntu 7.10 I believe :)

Also, you need to change your previous post to [noparse]**EVERYTHING**[/noparse] if you want it to be **bold** ;)

Thanks Joeb454, I'll look into that.

Kostkon, when I do a fresh install and don't have all these media players, I'll start with Totem-zine and when it doesn't play something, someone here on the forum will say intall gstreamer it plays everdything and then when it doesn't someone will say install w32 and 64 codecs, then someone will say install vlc and so on and so on until I have every player on the planet installed and can play anything.

I'll document next time I go through the whole long drawn out process so I can tell you which ones used to not play for me. I just didn't keep up this time.

Thank you for the help though.

---

### Post by t0p on 2008-09-03
> **iansane said:**
>  I don't think my system has been always doing this since I think I would have noticed it before.

The play-hover-over feature didn't exist in my gutsy install, I first encountered it after installing hardy.

---

### Post by kostkon on 2008-09-03
> **t0p said:**
> The play-hover-over feature didn't exist in my gutsy install, I first encountered it after installing hardy.
Actually, it is an old feature, I had it in 5.04. You needed to have *mpg321* installed for this to work. I remember that I could only preview mp3 files, not even oggs, really strange.

But now in 8.04 it has become even better, I can preview almost any audio file, even wmas.

---

### Post by Joeb454 on 2008-09-03
I think the files you can preview depends on what codecs you have.

Personally all I ever need to install is [ubuntu-restricted-extras]("apt://ubuntu-restricted-extras") and [libxine1-all-plugins]("apt://libxine1-all-plugins") :)

They're apt links - click them to install the packages :)

---

### Post by Cope57 on 2008-09-03
It is **Nautilus** that has that capability.
It has always had it, it was just enabled by default in the newer Ubuntu distributions.

For those that are using a older version, or just want to know where the setting is, open the folder with the music files.
In the settings select _E_dit / Prefere_n_ces
Then click the tab **Preview**

You will find **Sound Files** with options of:
*Always*
*Local Files Only*
*Never*

**Edit:***You can also preview text, in the same settings tab.*

---

### Post by tuxxy on 2008-09-03
> If vlc, totem, mplayer, zine, or gstreamer never failed you it's cause you haven't tried playing every file type that exists. Sooner or later you'll come across something that won't play or won't play right.

I have tried an awful lot, can you give me an example of this filetype? 

Also its not the players fault if you dont install the codecs

---

### Post by iansane on 2008-09-03
Joeb454, OK I checked and didn't have the libzine1-all-plugins installed.
That might have helped before I installed other players.

Cope57, you actually answered my question and I feel like a dummy for not knowing my syetem better by now. I don't mess with music much on the computer other than burning a cd for in the car.

tuxxy, sorry but I can play everything now and can't remember everytime I had problems. I'll be doing a new install on VM soon so just for testing, I'll see what I can and can't play with one player at a time in a controlled experiment sorta way.
Last prob I had was rm files and I know I had to install real player for those. That's understandable. 
Think I had problems with podcasts needed quicktime capabilities.

avi's and mpg's played after installing the w32 and 64 codecs.

DVD played after installing libdvdcss2 but no tracks selection in mplayer and totem was buggy and chose wrong language track sometimes.

Finally installed libdvdcss and css2 dev packages vlc starts playing dvd's which it wouldn't before the dev packs were installed.

Now, VLC is freakin awsome!! It actually shows the menu screen and has all the options for zoom, speed, panning, aspect ratio, etc. Like a real dvd player or powerdvd in windows.

Like I said before, I got advice from different people that every player was awsome and played anything. "Use this, no use this, no use this". I know people are trying to help and I appreciate it but it gets hard to know who really knows and who is just blurting out a quick reply. Finally with all these players, I can't find anything that won't play.

I'll just start fresh, try each one and ask questions when I run into problems.

Thanks to all for your help

---

### Post by egalvan on 2008-09-03
First off, please don't feel like a dummy because you don't know everything.

Nobody knows everything. We all had to learn.

Next, I think part of the problem with all this may be that folks are 
confusing **players** with **codecs**.

I use AmaroK for music (because I like it)

I use VLC for video (because I like it)

I install codecs if either of these have problems playing something.

Now if the codec is not available for one or the other, then I may need to try another player.

---

### Post by fballem on 2008-09-03
I have subscribed to this thread, which is a pretty comprehensive thread on installing oddball stuff in ubuntu, kubuntu, et al.

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Usually, I will follow the instructions shortly after an install, and it's relatively simple for newbies to follow. It uses terminal a lot, but copy and paste works really well.

Just need to follow the instructions for the version of ubuntu that is installed.

The only problem that I have found is with easytag and easytag-aac. There are conflicting requirements, so I usually just install easytag-aac.

As I understand it - and I really could be wrong - most of the time there are two parts to playing media files. Part 1 is to have the codecs installed, Part 2 is to install a player that can play the codecs. I use VLC for video and Exaile for audio.

Hope this helps,

---

### Post by iansane on 2008-09-11
Thanks for the link fballem 

I'll be reading through it.

I didn't want to revisit the subject of media players until I regrouped and started fresh but just to let you guys know, I have a .wmv file that gives error, "required  video/X-asf- unknown decoder pludin which is not installed" 

Same with all the media players. This one might be altered cause it was intended only to play as embedded in a flash player but I'm thinking a wmv file is a wmv file and with w32 and w64 codecs installed it should play? I see that vlc claims to play wmv's but it won't play this one. Maybe the problems I've been having are because of windows not sticking to standards? Is one wmv not the same as the next? I'll have to go find some random wmv to download to find out if it's the file.

---

### Post by iansane on 2008-09-16
Thought I'd update on something here. I did a minimal install and am trying very hard not to install anything at all that is not needed. 

So I found that the preview option in nautilus wasn't working and I get error that "no application to play this media type" when I just click on the file (even with amarock installed, had to tell it to open with amarock). I look for the default music player in a fresh install and someone said it is totem so I install totem.

combination of totem with default gstreamer plugins and setting the preview option in nautilus made it work. Amarock doesn't get recognized by nautilus and used to play music even if it's the only player on the system. These are the kind of things I'm trying to learn about my system.

What I'm doing is adding apps one at a time to help me better understand what is doing what. So far so good.

---

### Post by Mornedhel on 2008-09-16
> **iansane said:**
> Is one wmv not the same as the next? I'll have to go find some random wmv to download to find out if it's the file.

I stopped keeping count of WMV versions at v9 or something, a few years ago.

You don't need both w32codecs and w64codecs. Instead, install non-free-codecs, which will pull the correct package (w32codecs, w64codecs or ppc-codecs) for your architecture.

---

