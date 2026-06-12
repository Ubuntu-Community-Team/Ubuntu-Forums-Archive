---
title: "Myspace music player issue"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by huviduc on 2008-12-01
I am having trouble using the myspace music player on band websites. I like to check out new bands and this music player will not play. It loads but just sits there. I have tried it in firefox and Opera and i have java and flash installed. Any help would be great, thanks.

---

### Post by huviduc on 2008-12-01
bump up, someone has to know

---

### Post by luceerose on 2008-12-01
I am having the same issue.
Would anybody know whether this is a java or flash issue ?

java -version
```
java version "1.6.0_0"
OpenJDK  Runtime Environment (build 1.6.0_0-b11)
OpenJDK 64-Bit Server VM (build 1.6.0_0-b11, mixed mode)
```

about: plugins```

    File name: npwrapper.libflashplayer.so
    Shockwave Flash 9.0 r124

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
```

Using Ubuntu Hardy, Gnome 2.22.3, Firefox 3.0.4, 64-bit

---

### Post by luceerose on 2008-12-01
I just checked my laptop, and it doesn't have this issue.
laptop has same flash, different java;
```

java version "1.6.0_07"
Java(TM) SE Runtime Environment (build 1.6.0_07-b06)
Java HotSpot(TM) Client VM (build 10.0-b23, mixed mode, sharing)

```

The major difference here to note is my laptop is 32-bit, whilst my main pc is 64-bit.

So, i am going to go ahead and blame the 64-bit version plugins.
Strangely enough, I didn't have this issue a couple of months ago.
And I don't remember doing a manual update on either java or flash.

---

### Post by huviduc on 2008-12-03
I removed Sun java and reinstalled the open jre packages and the same thing happens. I also have the shockwave flash installed. It seems as if its an issue with something else, any ideas?

---

### Post by perlluver on 2008-12-03
> **huviduc said:**
> I removed Sun java and reinstalled the open jre packages and the same thing happens. I also have the shockwave flash installed. It seems as if its an issue with something else, any ideas?

What version of Ubuntu are you using?  Hardy, Intrepid, Gutsy?  And what version of flash are you using?  9.0.24 or 10?

---

### Post by huviduc on 2008-12-03
I am running 8.04 hardy and about plugins shows that i have shockwave 9 and 10 installed

About:Plugins  

```
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 9.0 r124

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 10.0 r12

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
```

---

### Post by perlluver on 2008-12-03
I may recommend removing Flash 9.0.24, and leaving flash 10 installed, as they may be conflicting.  Also, install Sun Java, not OpenJRE.

---

### Post by huviduc on 2008-12-03
How do i remove just flash 9? if i go into tools-add ons- plugins, it only shows flash 9 which is also strange. I had sun java installed but i switched to see if that was the issue. I will switch back though

---

### Post by huviduc on 2008-12-03
I got flash 9 removed and only flash 10 is installed as well as Sun java 1.6. Still same isssue :|

```
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 10.0 r12

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
```

I dont get why it loads but just wont play, makes me think its something else causing the issue

---

### Post by huviduc on 2008-12-06
anyone have any ideas?

---

### Post by andydread on 2009-01-01
Did you get this figured out?  I have the same problem with 3 different PCs here running Gutsy, Hardy and Intrepid.  Is there ANYONE using Ubuntu and are able to play music on myspace? Anyone?

---

### Post by Trithious on 2009-01-03
This would be awesome if someone could figure this out, because I'm a musician and I installed Ubuntu 8.10 on my leading laptop and I really don't want to use my Mac to view simple content on the internet but if I have to I will for the specific reason to watch youtube and listen to music via streaming. 

Thanks to the person who figures that out cuz that would be metal if someone did figure it out lol!

---

### Post by Shmeegs2001 on 2009-01-28
I've got the same issue!!!! Some help!!!

---

### Post by panaut0lordv on 2009-02-01
Youtube, vimeo and so on works. But why myspace doesn't? flash 10, java 6jre. 8.10, architecture i386

Lol got it working! myspace uses strange codecs

sudo apt-get install ubuntu-restricted-extras gstreamer0.10-fluendo-mp3

---

### Post by sonicb00m on 2009-02-03
my problem is myspace just shows the "get flash" logo when it's isntalled and working perfectly on youtube.

---

### Post by afbase on 2009-02-21
I've had this problem for about a month now.  In Firefox 3, try this addon: [MediaWrap]("https://addons.mozilla.org/en-US/firefox/search?q=MediaWrap")

I don't know if this is will solve every problem with the myspace music player for everbody.  It just did for me. I hope it solves things for others. :popcorn:

---

### Post by cooberfield on 2009-07-18
[SIZE=4]simply use the epiphany web browser (it is quick and easy to install from ubuntu's package manager) and
myspace music will play just fine!

possibly, any linux browser that can handle flash that *ISN'T* firefox would also work, but i'm not going to bother testing them all. :popcorn:
[/SIZE]

---

### Post by y-lee on 2009-07-18
This is an old thread and I don't know if this issue was ever resolved, but for the record myspaces music player has always worked fine for me using firefox.

---

### Post by Shane-o on 2009-07-27
> **afbase said:**
> I've had this problem for about a month now.  In Firefox 3, try this addon: [MediaWrap]("https://addons.mozilla.org/en-US/firefox/search?q=MediaWrap")

I don't know if this is will solve every problem with the myspace music player for everbody.  It just did for me. I hope it solves things for others. :popcorn:
Thankyou so very much afbase. I was going bonkers trying to work out why MySpace music player was asking me for a Flash 9 upgrade when I have Flash 10 already

MediaWrap fixed it, no problems  :P

---

