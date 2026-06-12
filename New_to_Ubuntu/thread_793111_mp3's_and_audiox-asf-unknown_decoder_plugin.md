---
title: "mp3's and audio/x-asf-unknown decoder plugin"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by animalprimate on 2008-05-13
After downloading some mp3's from Fr*s*w*re I attempt to play them and they aren't supported.

Totem Movie Player gives the message:

**An error occurred**

The playback of this movie requires a audio/x-asf-unknown decoder plugin which is not installed.  What should I do?:confused:

---

### Post by shinobitux on 2008-05-13
Yeah, I've seen this.

From what I understand, most (if not all) distros of Ubuntu lack non-free codecs for things such as DVD Movies and MP3. This is to avoid legal issues.

While this is unfortunate, it doesn't prevent you from doing so.

First question: Do you like Totem player?

I have never actually used it so I can't advise you regarding it. If you go to their homepage they should provide instructions for installing an MP3 codec for your music.

Here's what I do: I use either VLC or MPlayer. Both are free downloads and should be available in your repositories. The advantage to these players is that the audio and video codecs are already compiled into the players so you don't have to worry about it.

Start out with VLC (Video Lan Client). It has versions for linux, windows, OSX, etc and is already pretty much set up and ready to go.

I prefer MPlayer, but you need a custom configuration file to have it run best and I don't have mine on hand at the moment.

So, from Ubuntu, install vlc and try opening your music with it. See how you like it.

---

