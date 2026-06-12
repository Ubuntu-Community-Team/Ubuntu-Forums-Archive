---
title: "Rhythmbox problem"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by Plur na mBan on 2008-08-31
I'm trying to run Rhythmbox to play my music in Ubuntu 8.04, and play songs off of my iPod in it; but whenever I push Play it says it's playing, but the slider doesn't move. It does it both with songs on the iPod and songs on the computer.

I already had a lot of problems with this installation (which I've been using since May) . . . such as, for example, and possibly for relevance (? I have no clue), I had no sound because any time it downloaded and installed an update or something in the auto-updater, it installed it to a different kernal (I believe) than the one it boots from. 

Last thing to mention, I don't know a lot of the terminology for working with Ubuntu yet. I mean, feel free to use it, because I want to learn, but please explain what everything is . . . Thanks.

-Plur

---

### Post by Redache on 2008-08-31
Have you got the Correct GStreamer plugins installed? it could be that it's not finding the codecs, but typically it'll mark each song with an x by them. Are the songs on the Ipod from the Itunes store? Rythmbox won't play DRM'd AAC files.

The Gstreamer plugins can be installed from Add/Remove in the applications menu, there's a drop down menu where you choose what it shows you, click on "All Available Programs" and search for Ubuntu Restricted Extras and download that.

If the Files are Digital Rights Managed AAC files then you'll need either [El Tunes]("http://www.el-tunes.com/")  or to find a way to bypass the Rights Management (I Can't actually tell you how to do that though, sorry).

I hope this helps a little.

---

### Post by Plur na mBan on 2008-09-01
So I'd installed all of the GStreamer plugins except for the Restricted Extras, but I just got those and it still doesn't work. 

Nope, none of my songs are from iTunes, so I don't think that's it, either. But thank you.

---

