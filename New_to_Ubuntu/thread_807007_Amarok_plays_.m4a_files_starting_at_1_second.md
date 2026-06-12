---
title: "Amarok plays .m4a files starting at 1 second"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by Gepetto on 2008-05-25
I used to have this problem, and I thought upgrading from Gutsy to Hardy would fix it, but so far, no good. 

When playing Apple ACC files in a playlist, when the previous song finishes, the next song will start at the 1 second mark, cutting out the first second of the song. This only happens with .m4a files, and as far as I can tell, only in Amarok (1.4.9.1). 

The weird thing is, I reinstalled Hardy last night, and my playback was flawless, for about 15 songs, then it reverted back to this skipping thing. Most of my music is in mp3 format, but I have a good chunk in m4a and this issue is so annoying, I can't stand listening to those cd's. Any help would be much appreciated, Thanks in advance.

---

### Post by Joeb454 on 2008-05-25
Check the amarok settings. Make sure there's no crossfade playback enabled etc. It sounds like that could be the issue here :)

---

### Post by Gepetto on 2008-05-25
Nope =\ The issue acctually occurs whether or not crossfading is on or not. Oddly enough, this issue can be bypassed if set it to insert a 1000ms (1second) gap in between the songs. Any shorter, it shows up again, same with longer.

---

### Post by Joeb454 on 2008-05-25
Strange. I guess you could just use that little workaround, and submit a bug to the amarok dev's (I've never noticed this by the way - 99.9% of my music is in AAC encoded audio as well)

---

### Post by chr1sh on 2008-11-14
> **Gepetto said:**
> I used to have this problem, and I thought upgrading from Gutsy to Hardy would fix it, but so far, no good. 

When playing Apple ACC files in a playlist, when the previous song finishes, the next song will start at the 1 second mark, cutting out the first second of the song. This only happens with .m4a files, and as far as I can tell, only in Amarok (1.4.9.1). 

The weird thing is, I reinstalled Hardy last night, and my playback was flawless, for about 15 songs, then it reverted back to this skipping thing. Most of my music is in mp3 format, but I have a good chunk in m4a and this issue is so annoying, I can't stand listening to those cd's. Any help would be much appreciated, Thanks in advance.
I had the same issue and contacted the Amarok team.  They suggested the issue may be that if you use a computer with on-board audio, that mixing may not be working - without "dmix" operating Amarok will cut off the first bit of songs as they would normally be mixed in.

A bit more googling and I found this blog: [http://buglandia.blogspot.com/2007/08/howto-software-audio-mixing-in-ubuntu.html](http://buglandia.blogspot.com/2007/08/howto-software-audio-mixing-in-ubuntu.html)

I followed the instructions there to create /etc/asound.conf with contents as given in the blog, and it's fixed the problem.

It will be good to know if that works for you too.

---

