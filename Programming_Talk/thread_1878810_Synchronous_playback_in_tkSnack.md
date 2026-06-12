---
title: "Synchronous playback in tkSnack"
date: 2011-11-10
forum: Programming Talk
---

### Post by Datweakfreak on 2011-11-10
I'm playing around with **tkSnack**, and I'm trying to get it to play two notes at the same time, synchronously.  I've changed the **blocking** argument in **snd.****play** to **False**, but that just seems to mute playback, as in, nothing plays. Also, changing the volume in **setVolume()** doesn't really seem to work, the volume remains the same unless I adjust it manually. Help would be much appreciated.

```
import Tkinter
import tkSnack

def setVolume(volume=50):
    if volume > 100:
        volume = 100
    elif volume < 0:
        volume = 0
    tkSnack.audio.play_gain(volume)

def playNote(freq, duration):
    snd = tkSnack.Sound()
    filt = tkSnack.Filter('generator', freq, 30000, 0.0, 'sine', int(11500 * duration))
    snd.stop()
    snd.play(filter=filt, **blocking=False**)

def soundStop():
    try:
        root = root.destroy()
        filt = None
    except:
        pass
    
    
root = Tkinter.Tk()
    
tkSnack.initializeSnack(root)
setVolume(30)
playNote(200, 1)
playNote(100, 1)
soundStop()
    
root.withdraw()
```

---

### Post by Datweakfreak on 2011-11-11
Hate to bump, but I couldn't' find help elsewhere, and I'm stuck, so...bump.

---

