---
title: "How to run run mplayer from SubDownloader?"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by santiagorf on 2008-10-27
Hi,
I'm trying to watch movies from SubDownloader using mplayer, but I don't know how to configure SubDownloader in order to use use mplayer as a video player.

In Settings->Others there are two fields to be completed in order to configure the video player: Video Player & Parameters. I think for the first one I should put "/usr/bin/gmplayer", but I have no idea what should I put in the second one.

Any ideas??
Thanks in advance!!

---

### Post by Kaerukh on 2009-02-18
You should put the parameters your viedo player needs. I.e. the path of the video file ({0}) and the option to call the subtitle and the path to the subtitle ({1})

I think with gmplayer the secon field will be: {0} -sub {1}

---

