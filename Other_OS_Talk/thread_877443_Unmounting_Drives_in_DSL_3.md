---
title: "Unmounting Drives in DSL 3"
date: 2008-08-01
forum: Other OS Talk
---

### Post by Bungo Pony on 2008-08-01
...and don't tell me to switch to DSL 4 because I don't like it :)

I've written some scripts for mounting and unmounting DVD drives at the click of an icon. Here's the problem...

If I shut down DSL with the DVD drives mounted, DSL ejects ALL of them. I would modify the shutdown script if I knew where it was located.

Now, to attempt getting around this, I wrote a script to shut down the music player and unmount the 4 DVD drives. When DSL shuts down, it ejects only ONE of the DVD drives, even though they've been unmounted through my script. I tried unmounting them three times in my script, and I'm having the same problem. It seems to eject the last drive that was being accesses before I killed the music player (xmms).

Could it be possible that the drive is still busy by the time DSL is killed?

---

