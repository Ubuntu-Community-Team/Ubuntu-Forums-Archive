---
title: "Wine wrongly converts unix path to Windows"
date: 2014-04-12
forum: New to Ubuntu
---

### Post by RobotOfBarr on 2014-04-12
This is my first serious attempt at programming under linux. I am converting a Windows program, that uses Apple's QAAC encoder to encode a wav file, to run under Ubuntu. QAAC needs to run under Wine. (Wine is V 1.4 from the Software Centre, Ubuntu is 12.04 LTS).
Running the original Windows program under Wine works fine.
From the terminal, launching Wine with the parameters for QAAC and the target file in one line works fine.
From my program, when launching Wine with a call to posix_spawn(...), the path to the target file is corrupted: the path passed as a parameter is (for example): "\"/home/r/Music/Beethoven Symphony no. 1.wav\""  but the error message out of QAAC says "Invalid name" for obvious reasons: "ERROR: **H:\**"\home\r\Music\Beethoven Symphony no. 1.wav": Invalid name."
How do I prevent Wine from prepending "H:\" to the path? (If I remove the Wine mapping for Drive H, it uses Z instead, and if I remove that, it prepends "unix\").

---

### Post by monkeybrain20122 on 2014-04-12
well you can just use ffmpeg to convert the file. For a gui frontend get winff as well. Not sure why you need to involve wine.

Edited: what is the windows name for /home/r/Music? it is probably just My Music. Checkout the Desktop integration tab in configure wine.

---

### Post by 3rdalbum on 2014-04-12
Sounds like an odd thing to do, because FFMPEG or SOX can do the conversion natively.

Anyway, Windows programs don't understand Unix paths, which is why Wine attempts the conversion of the path. I suggest you send Wine a Windows path to begin with, using the Z drive letter followed by the Unix path (changing slashes to backslashes). For instance, Z:\home\me\file.wav.

---

### Post by RobotOfBarr on 2014-04-13
Thank you both for the suggestions. I was using QAAC because it's reputed to be the best encoder. The problem with using a Windows path is, because of the embedded spaces, it needs to be quoted and there appears to be no way of doing that - because the "H:\" or "Z:" is prepended without a leading quote. But I'm puzzled because both from the terminal and when running the Windows version under Wine, it accepts and passes the Linux path through without a problem.
I did wonder whether posix_spawn was the source, but for that to be the case it would need to know about the Wine configuration.

---

