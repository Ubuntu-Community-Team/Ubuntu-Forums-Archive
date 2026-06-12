---
title: "[Rant] Dear maintainers: stop the avconv-nonsense"
date: 2015-02-19
forum: Recurring Discussions
---

### Post by sgofferj on 2015-02-19
As an 18+ years Linux user, I'm really REALLY used to problems, incompatibilities and stuff, but now I've really had it with avconv. Switching from ffmpeg to avconv was about the stupidest idea any Linux distribution maintainers possibly could have made...
I changed from Opensuse to Ubuntu less than a year ago and I had nothing but problems with the avconv stuff. Segfaults, enconding artefacts, more segfaults, more encoding artefacts and - guess what - more segfaults. Just today - again - when trying to encode a DVD - an important DVD with demo material... Avconv segfaults... great - now I can possibly spend hours on testing and fixing and might still miss the deadline and can trash 4 months of preparation work...

Dear maintainers: Some people are actually trying to do something productive with their Linux boxes and Linux SHOULD be out of the experiment-and-fix-state for at least 10 years, so PLEASE stop using unstable and experimental software just because some of the distro-maintainers are also libav-coders...! Really!
Distro decisions should be made solely based on functionality and stability and not based on some politics.

---

### Post by Bucky Ball on 2015-02-19
*Thread moved to **Ubuntu, Linux and OS Chat**.*

Not a support request.

If you wish to communicate with maintainers you won't have much luck here as Canonical staff do not frequent these forums. I suggest you contact Canonical directly to find the proper channels to communicate with the Canonical staff you wish to complain to.

Good luck.

---

### Post by sffvba[e0rt on 2015-02-19
*Thread moved to **Recurring Discussions**.*

Sorry Bucky Ball didn't see you already moving the thread but this issue has come up before and if someone starts a thread with a [Rant] tag then they can rant away in Recurring IMO...

---

### Post by andrew.46 on 2015-02-19
I believe that FFmpeg is on the way back to Ubuntu but for the moment you have this:

[https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu](https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu)

But indeed there would be few that have not tired of the fork and* all *of its consequences...

---

### Post by FakeOutdoorsman on 2015-02-19
> **sgofferj said:**
> ...just because some of the distro-maintainers are also libav-coders...! Really!
You hit the nail on the head here, but unfortunately this same reason makes the particular maintainer unreasonable.

Although it was a lot of work to get FFmpeg to get back into Debian and Ubuntu it will be returning in 15.04 I believe (or maybe 15.10, I forgot) as Andrew mentioned. Confusion will of course continue due to the legacy of the fork's naming choice shenanigans, the various misleading and confusing "deprecated" messages, and the fact that the ffmpeg version of the libraries will be named such as libavcodec-ffmpeg56, etc., while the fork's versions will be simply named libavcodec56, etc., so it is clear which will be the default libraries.

> **Bucky Ball said:**
> 
If you wish to communicate with maintainers you won't have much luck here as Canonical staff do not frequent these forums. I suggest you contact Canonical directly to find the proper channels to communicate with the Canonical staff you wish to complain to.


I do not believe that most package maintainership has anything to do with Canonical staff.

---

### Post by QIII on 2015-02-19
The MOTUs (who are volunteers) and their contributors (who are also volunteers) - the people who work on the Universe and Multiverse repos - may come here from time to time.  But they don't just decide willy-nilly to add stuff without coordinating with Canonical.

How many maintainers of packages in the main repos do you suppose come here and for whom do they work?

The fact remains that these forums are not a good place to get the attention requested.

---

