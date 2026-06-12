---
title: "Windows .exe screensavers"
date: 2013-02-10
forum: New to Ubuntu
---

### Post by regice9 on 2013-02-10
Hello. I have a .exe (not .scr) screensaver for Windows, which I can't figure out how to use on Ubuntu. I have already tried running it with Wine, but it just slows down my laptop, with absolutely no response, and I have to restart to return to normal speed. Is there a special sort of procedure, or is it impossible, or something like that?

Thank you in advance to all that read this thread about such a trivial topic.

---

### Post by wildmanne39 on 2013-02-10
Hi, exe files do not work with ubuntu.
Thanks

---

### Post by zombifier25 on 2013-02-10
Not all Windows program will work with Ubuntu, especially really obscure ones that Wine's developers has yet to work around, which includes screensavers,

'sides, Linux already has a huge set of screensavers - xscreensaver.

---

### Post by Mark Phelps on 2013-02-11
It's not elegant, but if you run the screensaver on a Windows PC, the steps below show you how to extract the images into individual files:

[http://www.ehow.com/how_7266519_extract-images-screensavers.html]("http://www.ehow.com/how_7266519_extract-images-screensavers.html")

---

### Post by GameX2 on 2013-02-11
I would be interested in converting a screensaver into a video...
Actually, come to think of it, could we just use:

```
sleep 500
mplayer -fs -zoom /home/gamex/video.avi
```

That will run the video after 5 minutes (We would need to run the video in loop)!  I still don't know however how to reset the script.  It would also be needed to bring back the user to LightDM when the video exit.

Maybe you could record your screensaver on Windows, then try a similar script...

---

### Post by regice9 on 2013-02-11
> **GameX2 said:**
> I would be interested in converting a screensaver into a video...
Actually, come to think of it, could we just use:

```
sleep 500
mplayer -fs -zoom /home/gamex/video.avi
```

That will run the video after 5 minutes (We would need to run the video in loop)!  I still don't know however how to reset the script.  It would also be needed to bring back the user to LightDM when the video exit.

Maybe you could record your screensaver on Windows, then try a similar script...:confused:

Thanks, but I think that I should probably just pitch it.

---

### Post by GameX2 on 2013-02-12
> **regice9 said:**
> :confused:

Thanks, but I think that I should probably just pitch it.

That's not a complicated script, in fact (It's not complete).  You'll want to put it in your startup applications.

```
sleep 500
```
The script start, then count 500 seconds / 5 minutes.  Then:

```
mplayer -fs -zoom /home/path/to/video/screensaver.avi
```

MPlayer is a very fast and light video player, that can be used from command-line.  The -fs -zoom parameters display the video in full scren.

If you record your windows screensaver with a software (Might want to record a VirtualBox virtual machine, which you would run the screensaver on), we could probably do something interesting with this script.

If you want to, for sure.  The script is not complete, that's just a basic idea.

---

