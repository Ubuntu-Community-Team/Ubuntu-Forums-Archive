---
title: "CPU at full blast... any tweaking possible ?"
date: 2013-08-14
forum: New to Ubuntu
---

### Post by Innernet on 2013-08-14
Hi.
Sometimes, not necessarily when watching television streamed news, the System Monitor reports no operational headroom on CPU, running at 100% capability.
(It is a Compaq Presario CQ60, running 12.04 + Gnome)

Is there any tweaks to provide some 'relief'; or, is it normal, or is it wrong, or will the compfuser 'explode' :o at any moment ?
Attached screenshot.
[ATTACH=CONFIG]245367[/ATTACH]

---

### Post by lukeiamyourfather on 2013-08-14
Use the top command or another processes monitor to see what's using all of the resources. There might be a rogue process, but my guess is you're simply at the limits of the hardware since it's a lower end processor from a few generations ago.

---

### Post by Innernet on 2013-08-14
Thanks.
The processes show
Gnome-system monitor ~15% to 22%
Firefox ~2%
Plugin container ~50% to 65%
Pulse audio ~3%
Metacity ~1%
All others 0%

Does it mean if I close the 'System monitor' the CPU will have some headroom ? (but unable to tell exactly how much?)
Any way to tweak something for some relief ?

Partial 'Resources' attached
[ATTACH=CONFIG]245370[/ATTACH]

---

### Post by lukeiamyourfather on 2013-08-14
The "plugin container" makes me think the video decoding is the culprit because that's Firefox's way of saying a plugin (like a video decoder) is using resources. Modern video codecs like H.264 are decoded on the graphics card if the graphics card and drivers support it, given the high processor usage I'm guessing your setup doesn't support decoding the video on the graphics card. Or the videos are encoded using a less popular codec that doesn't get decoded on the graphics card. Either way the answer probably isn't what you're looking for. It looks like you're at the max of what the hardware can do.

---

### Post by 3rdalbum on 2013-08-14
The CPU is designed to happily run at 100% day in and day out for years. Your computer wont be damaged.

Things like video, games, file compression, etc will use 100% CPU power, and that is normal and absolutely fine. If CPU monitor is using 3% CPU and your video playback is using the other 97%, closing System Monitor will just cause the video playbaack to attempt to run a little smoother by using the newly-freed 3%.

You should only be concerned if you are still at 100% with no programs running.

---

### Post by lukeiamyourfather on 2013-08-15
> **3rdalbum said:**
> The CPU is designed to happily run at 100% day in and day out for years. Your computer wont be damaged.


Yes, to clarify, it won't damage the hardware if everything is working as it should (no blocked vents, fans work, etc.). I was just pointing out the processor was 100% utilized because that task requires every last bit of performance the machine has to offer.

---

