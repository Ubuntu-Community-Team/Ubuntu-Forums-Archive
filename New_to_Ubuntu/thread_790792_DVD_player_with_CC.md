---
title: "DVD player with CC?"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by kshsj777 on 2008-05-11
I right now have totem installed, which won't play DVDs even though I've installed the gstreamer codecs.  VLC works but I have to manually type in media/cdrom0 instead of the default location.  Even though VLC supports subtitles, it doesn't support closed caption (CC).

Is there a DVD player that won't require me to manually type in the location each time and that will have CC support?  Some DVDs do not have subtitles, but will have CC.  By the way Windows Media Player supports both subtitles and closed captions, so I know it's possible to support them.

Thanks.

---

### Post by nowshining on 2008-05-11
does this DVD show CC in WMP as well?

---

### Post by kshsj777 on 2008-05-11
Yes, most of the DVDs have CC, and WMP has CC support.

---

### Post by nowshining on 2008-05-12
my Question was the DVD u were trying to play have CC support & did it work with WMP with CC before?

---

### Post by kshsj777 on 2008-05-12
Yes.

---

### Post by nowshining on 2008-05-12
Thanks for answering my Question.

Try going into add/remove and install restricted-codecs, etc.. + totem won't play a DVD when going into the menu - DVD, etc.. it's widely known.

---

### Post by kshsj777 on 2008-05-13
I did add the codecs, only VLC works so far.  I've heard the Totem doesn't support closed captions anyway.  I'm just looking for one that will.

---

### Post by SunnyRabbiera on 2008-05-13
I think xine and smplayer support closed captioning and subtitles too.

---

### Post by kshsj777 on 2008-05-13
Do you mean gxine?  I could not get DVD to play on there.

Totem wasn't working under Gutsy, but apparently it now works under Hardy.  However, I cannot access the DVD menu and I can't get subtitles, let alone closed caption on it.

VLC player does support subtitles, but I don't know how to set it as the default player so that when I pop in a DVD it starts up.

I cannot get smplayer to play DVDs either.

Maybe if Totem has an add on for accessing menus and displaying closed captions?

---

### Post by nowshining on 2008-05-14
u can try kaffeine in the repos...

---

### Post by stchman on 2008-05-14
> **kshsj777 said:**
> I right now have totem installed, which won't play DVDs even though I've installed the gstreamer codecs.  VLC works but I have to manually type in media/cdrom0 instead of the default location.  Even though VLC supports subtitles, it doesn't support closed caption (CC).

Is there a DVD player that won't require me to manually type in the location each time and that will have CC support?  Some DVDs do not have subtitles, but will have CC.  By the way Windows Media Player supports both subtitles and closed captions, so I know it's possible to support them.

Thanks.

You need to first install the proper CODECs then install the libdvdcss software.

[http://www.stchman.com/codecs.html](http://www.stchman.com/codecs.html)
[http://www.stchman.com/dvd_rip.html](http://www.stchman.com/dvd_rip.html)

This will get you going.

---

### Post by alex_anthony on 2008-05-14
And to set the default program btw, its in Settings>>Preferences>>Removable Drives and Media (or at least it was)

---

### Post by kshsj777 on 2008-05-17
stchman, I did both of those things, but I still cannot access the DVD menu on totem to enable subtitles

I still don't know how to enable another player besides totem as default.

Does Kaffiene have closed caption support? 

Thanks

---

### Post by kshsj777 on 2008-05-17
I found that mplayer supports closed captions according its site.  How do I get that to work? 

When I tell it to open a disk, it says:  

no stream found to handle url dvd://1

---

### Post by kshsj777 on 2008-05-17
Okay, I think maybe this all has to do with not being able to connect to my DVD drive.

In order to get it working on VLC, every time I start the program, I have to open from disk and change

dvd:///dev/scd0

to

dvd:///media/cdrom0 

and everything works including subtitles, but no CC (since VLC does not have support for them yet).

Is there anyway to change it permanently either on VLC or on something in my computer, so that all DVD players will work?

---

