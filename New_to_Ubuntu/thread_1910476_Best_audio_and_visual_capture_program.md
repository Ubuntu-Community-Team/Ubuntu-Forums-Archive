---
title: "Best audio and visual capture program?"
date: 2012-01-17
forum: New to Ubuntu
---

### Post by cliveT on 2012-01-17
Hi guys
 
What would be the best program to use for capturing audio and visual of my screen for later playback - to be used for uploading to a website for short "tutorials" etc.?

---

### Post by Raff1 on 2012-01-17
> **cliveT said:**
> Hi guys
 
What would be the best program to use for capturing audio and visual of my screen for later playback - to be used for uploading to a website for short "tutorials" etc.?

I am not completely sure about Unity, but with Gnome3 you can press Ctrl+Alt+Shift+R to start recording a movie file to your home folder :-) It's an integrated feature.

---

### Post by carl4926 on 2012-01-17
```
ffmpeg -f x11grab -s `xdpyinfo | grep 'dimensions:'|awk '{print $2}'` -r 25 -i :0.0 -sameq output.mkv
```

Produces a nice video and not too big either

Just paste that in a terminal and hit enter
You need ffmpeg installed

---

### Post by Double.J on 2012-01-17
Hi there, can't say I've tried many - I just grabbed xvidcap from the software centre and does the job for me - lets you select the area to capture which I like - if you're just doing a clip about nautilus or terminal, no point capturing the whole desktop!

Only thing I didn't like - I couldn't work out how to change it from saving in the /home/user/videos directory, and it can't play back on my hardware - I have to find the avi and play back in vlc, but other than that it does well - achieves 89% frame rate on my netbook and doesn't slow down at all :)

Hope it helps!

---

### Post by cliveT on 2012-01-17
thanks guys I`ll have a look at some of those you`ve mentioned, all I want is a simple program to capture audio/visual for making "how to"  videos for teaching people basic CAD principles etc.
 
Then I can upload them to either youtube or other website!

---

### Post by Double.J on 2012-01-17
> **cliveT said:**
> thanks guys I`ll have a look at some of those you`ve mentioned, all I want is a simple program to capture audio/visual for making "how to"  videos for teaching people basic CAD principles etc.
 
Then I can upload them to either youtube or other website!

I think any of those choices should meet your needs! Might I suggest also looking into GUVCVideo or Cheese to capture your smiling face? I think it always helps people follow tutorials if they can see your expressions as you describe things :)

---

