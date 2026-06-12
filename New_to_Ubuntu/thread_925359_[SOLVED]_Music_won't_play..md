---
title: "[SOLVED] Music won't play."
date: 2008-09-20
forum: New to Ubuntu
---

### Post by msohn88 on 2008-09-20
Hello, I installed Ubuntu last night and people on here helped me get through play musics on Rhythmbox and Amarok even though I imported them from Windows.

When I played songs today, the songs won't play at all.

The scroll bar won't move; any help?

---

### Post by neurostu on 2008-09-20
Did you install support for MP3s? Try installing ubuntu-restricted-extras then see if that fixes the problem.

---

### Post by k33bz on 2008-09-20
I have never used Rhythmbox and I have had problems with Amarok before in the past. Have you tried Audacious. It is a much better program in my opinion. But everyone has their own taste.

---

### Post by msohn88 on 2008-09-20
How do I install that?

Do you mind if you show me the commands here? :)

---

### Post by k33bz on 2008-09-20
audacious is in your synaptic manager

---

### Post by msohn88 on 2008-09-20
I am downloading that right now.

Will this program play iTunes purchased songs?

---

### Post by k33bz on 2008-09-20
> **msohn88 said:**
> I am downloading that right now.

Will this program play iTunes purchased songs?

That I am not to sure, all my music that I have is either music I have created or music that I ripped from my CDs

---

### Post by msohn88 on 2008-09-20
Everytime I want to play a song, I have to import from my Windows partion.

I do not know where to find them.

It takes forever to find a folder to import.

Any suggestions?

---

### Post by msohn88 on 2008-09-20
Well, the program you introduced to me won't play songs either.

---

### Post by mc4100 on 2008-09-20
> **msohn88 said:**
> I am downloading that right now.

Will this program play iTunes purchased songs?

If you use rhythmbox (which uses gstreamer), then opening a terminal (Applications -> Accessories) and typing:
```
sudo apt-get install ubuntu-restricted-extras
```
Will install everything you need to play .mp3 files, etc., and if you download the [El Tunes]("http://www.el-tunes.com/") .debs, then you'll be able to playback (pre-Version 8 purchased) music from iTunes.

Hope that helps.

Edit: It seems ElTunes has stopped development, they don't even link to it on their website, but I suppose you can still find it on bittorrent.

---

### Post by msohn88 on 2008-09-20
Well... I restarted the ubuntu, and it plays... this is weird.

---

### Post by msohn88 on 2008-09-20
I get this message:

msttcorefonts uses defoma                                                 &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; Msttcorefonts uses the DEbian FOnt MAnager (defoma). If you wish to use   &#9474; 
 &#9474; the fonts provided by this package under the X Window System, you must    &#9474; 
 &#9474; configure it to use defoma fonts.                                         &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; The easiest way to do so is to use the x-ttcidfont-conf package. For      &#9474; 
 &#9474; more information, install the x-ttcidfont-conf package and consult its    &#9474; 
 &#9474; documentation under /usr/share/doc/x-ttcidfont-conf.                      &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; For uses of msttcorefonts not related to the X Window System (e.g.        &#9474; 
 &#9474; printing) this is not required.

---

### Post by neurostu on 2008-09-20
> **msohn88 said:**
> I am downloading that right now.

Will this program play iTunes purchased songs?


You cannot play itunes purchased music unless you buy the DRM free songs from iTunes.

---

### Post by mc4100 on 2008-09-20
> **msohn88 said:**
> Well... I restarted the ubuntu, and it plays... this is weird.

Sound to me like a perfect example of a PulseAudio crash; in the future, to kill a mis-behaving PulseAudio:
```
killall pulseaudio
```
Or simply start it up again:
```
pulseaudio
```

---

### Post by msohn88 on 2008-09-21
Thanks, it works now.

---

