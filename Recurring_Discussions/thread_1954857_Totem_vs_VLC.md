---
title: "Totem vs VLC?"
date: 2012-04-08
forum: Recurring Discussions
---

### Post by Trixsey on 2012-04-08
As a follow-up to my "Rhythmbox vs Tomahawk"-thread ([http://ubuntuforums.org/showthread.php?t=1953498](http://ubuntuforums.org/showthread.php?t=1953498)) I have started thinking broader, and the fact that Totem is the default player in Ubuntu rather than VLC (which feels like the number one open source video player) seems like a mystery to me.

Are there any obvious reasons?

---

### Post by PhantomTurtle on 2012-04-08
It's because VLC ships with codecs that Ubuntu is not allowed to ship with. That is why Totem is used. I'm sure there are other reasons as well, but this is one of the main reasons it's not shipped with Ubuntu

---

### Post by xebian on 2012-04-08
It's not difficult to replace default totem with vlc after installation.

---

### Post by jpeddicord on 2012-04-08
PhantomTurtle's got it for the most part (however VLC *is* in universe now), but there are some other reasons:

* Totem is a part of GNOME, so it makes sense to use it as it's already integrated with many things.
* VLC is not a GNOME app; it is Qt. However, Qt is being shipped on the default install now, so this may be a moot point.
* Totem uses GStreamer, the main/default multimedia framework, which is also used by Rhythmbox and some other built-ins. VLC ships its own framework, which would take up space on-disc.
* VLC + data is nearly 30 MB, while Totem is ~4 MB. Note that this doesn't include GStreamer, but even counting that in it isn't very large.

There have been efforts to make VLC default in the past (it seems to come up every cycle, but maybe I'm exaggerating) and they have largely failed due to the above issues. I really do love VLC, it's my video player of choice, but I don't see it happening.

---

### Post by xyzzyman on 2012-04-08
For 'everyday use' Totem works. VLC has too many options in the menus to necessarily be a good fit for installing for your parents. Doesn't mean all parents, but in general. That said I have both installed.

---

### Post by jbicha on 2012-04-08
Also VLC's UI doesn't match the rest of Ubuntu very well.

---

### Post by devinwhite717 on 2012-04-10
With VLC I can play everything

---

### Post by TenPlus1 on 2012-04-10
Personally I use UMPlayer which in my opinion beats even VLC, and is open-source like Totem...

---

### Post by ewangr on 2012-04-10
Most of what I watch is Anime MKVs which are either 720 or 1080 with 10-bit encoding and embedded subtitles. Running the default player (which I gather is Totem), I get buttery smooth playback. Past experience (granted we're talking over a year ago) was that to get the same out of VLC took a fair bit of tweaking and configuring.

So I vote for the lazy option :-)

---

### Post by Trixsey on 2012-04-10
> **TenPlus1 said:**
> Personally I use UMPlayer which in my opinion beats even VLC, and is open-source like Totem...

MPlayer (which UMPlayer is built on) used to be my player of choice but I have a pretty weak computer and lately I find that VLC has caught up to and even passed MPlayer in terms of performance and support for various formats.

---

### Post by Trixsey on 2012-04-10
> **ewangr said:**
> Most of what I watch is Anime MKVs which are either 720 or 1080 with 10-bit encoding and embedded subtitles. Running the default player (which I gather is Totem), I get buttery smooth playback. Past experience (granted we're talking over a year ago) was that to get the same out of VLC took a fair bit of tweaking and configuring.

So I vote for the lazy option :-)

Maybe optimum performance is architecture-specific. I don't have extensive experience with Totem but I always had the feeling that VLC (and in the past MPlayer) beat most stuff out there in terms of what they play and how well they play it.

---

### Post by philinux on 2012-04-10
Moved to recurring discussions.

---

### Post by rima on 2012-04-12
I personally use VLC, I found Totem/Rhythmbox/Banshee extremaly frustrating.
VLC plays my MP3s and more, without me messing around looking for codecs. *yes, I'm lazy like that*:p

---

### Post by wolfen69 on 2012-04-12
I have used vlc since its inception for all of my media needs, and find it to be very, very good. I like that it's simple looking, yet is extremely powerful for advanced users.

---

### Post by devinwhite717 on 2012-04-14
With VLC you can play almost anything

---

### Post by Bandit on 2012-04-14
VLC without a doubt. Simple clean UI and extremely in depth preferences for advanced users. Its probably the most versatile media player across all platforms.

---

