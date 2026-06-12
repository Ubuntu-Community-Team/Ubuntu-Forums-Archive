---
title: "Can't play videos on YouTube with Chromium"
date: 2013-06-12
forum: New to Ubuntu
---

### Post by gleedadswell on 2013-06-12
I'm having sort of the [opposite problem]("http://ubuntuforums.org/showthread.php?t=2123025").  Youtube seems to work just fine in Firefox.  In Chromium some videos will play but others give the 

"This video is currently unavailable
Learn more"

error message.  When that happens I can always play these videos in firefox, so it's not that the video itself is unavailable on YouTube.  Following the "Learn more" link tells me to try several things.

1. refresh the browser page (tried it)
2. change the video quality to lower in the YouTube settings (tried it)
3. close all other tabs (tried it)
4. upgrade browser (see below)
5. upgrade flash player (see below)
6. enable javascript (done)
7. clear cache and cookies (tried it)

Upgrade browser: I'm running a very fresh install of Ubuntu 12.04 with the chromium browser that comes up in the repository.  Shouldn't that be pretty up to date?
Upgrade flash player: if this was the problem wouldn't it fail in Firefox as well?

Any ideas?

---

### Post by Iowan on 2013-06-12
Moved to it's own thread.

---

### Post by craig10x on 2013-06-12
One suggestion: you might want to install Chrome instead (grab the deb file from google's site and then right click it and let ubuntu software center install it...
Chromium uses the adobe flash which ubuntu restricted extras gave you on your system...Adobe is no longer producing newer versions of flash for Linux, and all you get for that is security updates...
And that is a pretty old version...

Chrome, on the other end, comes with the "pepper flash plug in" built in (Google has a deal with adobe to provide the latest flash versions for it) so you would have a very up to date and current version...
Perhaps that will work better for you...

Chrome also comes with a neat built in pdf reader as well and also adds a ppa to your software sources to always get the latest version in your updates...

---

### Post by monkeybrain2012 on 2013-06-12
> **craig10x said:**
> One suggestion: you might want to install Chrome instead (grab the deb file from google's site and then right click it and let ubuntu software center install it...
Chromium uses the adobe flash which ubuntu restricted extras gave you on your system...Adobe is no longer producing newer versions of flash for Linux, and all you get for that is security updates...
And that is a pretty old version...

Chrome, on the other end, comes with the "pepper flash plug in" built in (Google has a deal with adobe to provide the latest flash versions for it) so you would have a very up to date and current version...
Perhaps that will work better for you...

Chrome also comes with a neat built in pdf reader as well and also adds a ppa to your software sources to always get the latest version in your updates...

Since it works on Firefox it has nothing to do with flash version.

---

### Post by JebusWankel on 2013-06-12
I don't know for sure that just because your flash works in Firefox that means it's not a flash issue. My understanding is that Chrome bundles its own flash. This may or may not be true for chromium as well.

Anyway, my suggestion is to try the HTML5 video player. You can enable it by setting a cookie here: [http://www.youtube.com/html5]("http://www.youtube.com/html5")

---

### Post by craig10x on 2013-06-13
Chromium doesn't bundle the flash plug in which is why i suggested he try Chrome instead of Chromium...nothing to lose and worth a try...
While i didn't have problems with that old adobe flash that ubuntu installs, it is getting kind of outdated...Chrome's flash is about 5 versions ahead already...
It may not solve his problem, but it is certainly worth a try...

---

### Post by sg_2342 on 2013-12-10
I have the same problem since a couple of days, and since I explicitly do not trust Google's binary version of Chrome, it is not an option for me to use Chrome instead of Chromium. Does anyone else have this problem as well, and how did you fix it?
I use Quantal (or to be more exact, the Linux Mint which is based on Quantal, the chromium browser comes from the Ubuntu repository).

Oh, I have another tip for everyone who does have this problem: replacing watch?v= with just v/ - so that the video link changes from youtube.com/watch?v=XXXXXXXXX to youtube.com/v/XXXXXXXXX will play the video, but it will be played in the "embed" player mode, so that it fills the whole screen and no video description or comments or anything else can be seen.

---

### Post by monkeybrain20122 on 2013-12-11
Does it only happen on Youtube? How about other sites that use flash such as vimeo? Clean your cookies and history and restart the browser and see what happens.

BTW, you don't even need flash to watch Youtube, many videos have html5 versions and you can use a greasemonkey script such as [http://userscripts.org/scripts/show/87011](http://userscripts.org/scripts/show/87011)

---

### Post by sg_2342 on 2013-12-11
Indeed, this also happens with Vimeo, where the error message is "This video can&#8217;t be played with your current setup." - However, I have completely re-built my browser profile in Chromium, when this problem first occured (deleted ~/.cache/chromium and ~/.config/chromium and started from scratch, except for exported/re-imported bookmarks) and it did not change anything. Deactivating my addons (Ghostery, AdBlockPlus and ProxTube) also did not change a thing.

As for HTML5, I activated this experiment, but in Chromium the problem *still* persists (it appears that this happens only when accessing the video takes a couple of milliseconds too long), plus other problems came on top of it (like a completely black player w/o any controls after changing into another tab and back, or sometimes even without that). It also seems to not happen any more, when the video had to have been reloaded (in the embed form, where it works except for the HTML5 problem/bug, which can only be fixed by reloading), so that it almost looks like it depends on whether a video is present on one of the Youtube content farms close to me, or something like that.

However, the fact that vimeo doesn't work either, is more pointing towards this hunch being wrong...I really don't know what's going on there...

---

### Post by monkeybrain20122 on 2013-12-11
If it works in firefox then there is a problem in Chromium rather than a flash problem or your system, since they use the same flash pliugin. Maybe a bug?

---

### Post by sg_2342 on 2013-12-12
It's even stranger, it doesn't seem to be a problem with Chromium vs. Chrome at all, it also must have something to do with youtube. When I play a supposedly "Unavailable" video in the embed player (with the altered link as described above), then afterwards, it also plays in the normal browser window where before it wasn't possible to watch it. Must have something to do with a timing issue and youtube distributing their videos on their server farms throughout the world...

But aside from that, the last update of Chromium and Flash created another issue (which is OT in this thread, but I'll still mention it) that blacks out the player when changing to another tab and back to the one where the video is being played or paused (or finished playing and showing thumbnail suggestions), or scrolling down while the video is played or paused etc... But I suspect that this quite obvious bug will be fixed in a future version of either chromium or the flash plugin.

---

### Post by monkeybrain20122 on 2013-12-12
> **sg_2342 said:**
> 
But aside from that, the last update of Chromium and Flash created another issue (which is OT in this thread, but I'll still mention it) that blacks out the player when changing to another tab and back to the one where the video is being played or paused (or finished playing and showing thumbnail suggestions), or scrolling down while the video is played or paused etc... But I suspect that this quite obvious bug will be fixed in a future version of either chromium or the flash plugin.
 
Do you have a nvidia card and use the proprietary driver?

---

### Post by sg_2342 on 2013-12-12
> **monkeybrain20122 said:**
> Do you have a nvidia card and use the proprietary driver?

Nope, it's happening on a Thinkpad T400 with the intel graphics. No proprietary drivers involved, as far as I know.

---

### Post by newb85 on 2013-12-12
The Adobe flash plugin and Chromium both received updates yesterday.  Does the problem persist?

---

### Post by sg_2342 on 2013-12-12
Actually, the problem with the video blacking out (but continuing to play the audio, just with no video or player controls) started occuring in a noticable way after these last updated of Chromium and the Adobe Flash plugin. The other problem, about which this thread initially was, has not been fixed by these updates either.

---

### Post by dikkjo on 2014-01-24
> **sg_2342 said:**
> Actually, the problem with the video blacking out (but continuing to play the audio, just with no video or player controls) started occuring in a noticable way after these last updated of Chromium and the Adobe Flash plugin. The other problem, about which this thread initially was, has not been fixed by these updates either.

I think the original problem may be solved by installing chromium-codecs-ffmpeg-extra.

---

