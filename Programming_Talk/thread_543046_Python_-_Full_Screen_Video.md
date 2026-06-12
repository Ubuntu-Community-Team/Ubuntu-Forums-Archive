---
title: "Python - Full Screen Video"
date: 2007-09-04
forum: Programming Talk
---

### Post by Kabatwa on 2007-09-04
Hi, I'm an Art Student and I'm hoping to mix my Arty stuff with some programming to produce some work.
I've got an idea for something and I've started to learn Python (Although still very beginner at the moment) what I'd like to do is output some video to fullscreen through VGA. I'd like to do this in Python as this is what I've been learning.
Could anyone please give me a hint at what my possibilities are? I'm thinking that maybe pyxine or pygame modules might be able to do this?

Thanks for any help anyone can give!

Tim

---

### Post by moephan on 2007-09-04
Tim,

It's hard to say, as I'm not 100% clear on what you are trying to do. A cheap and quick way to do this may be to pass the video off to totem or mplayer with the right command line switches to make it work the way you want. 

If this might work for you, first if you haven't used pipes, look up the "popen" method in the os module. Then to see how to control totem or mplayer, just open a terminal and type "totem --help" or "mplayer --help" to see what command line options to use.

Hope that makes sense. Good luck

Cheers, Rick

---

### Post by Kabatwa on 2007-09-04
Thanks Rick,
I'm looking into it right now. What I'm basically thinking of doing is displaying some video but at the same time use an arduino to run a motor for some things that will be synced to the video.
After looking at mplayer and totem. I found that myplayer can use the framebuffer. I think I'll use this approach as it's probably the quickest (doesn't use X) and I can hopefully lockout the possibility of anyone messing with my machine when it's being exhibited.

Once again,
thanks,
Tim

---

