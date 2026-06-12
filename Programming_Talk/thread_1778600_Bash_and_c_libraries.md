---
title: "Bash and c libraries?"
date: 2011-06-09
forum: Programming Talk
---

### Post by vmonkey on 2011-06-09
Hi all,
I am not so experienced in programming nor in BASH, however I try to learn the most of it. I am currently scripting in BASH one "application" which should provide always working streams (I have a file with them...). But that is not so important.
To check rtsp, rtp, rtmp, udp, tcp and http I am currently using ffmpeg, which works perfectly. But is there any option to check mms or mmsh? How? I googled a bit and the only way I found was to use libmms libraries. But is it even possible to use compiled c++/c libraries in BASH? If so, how?
If the answer is no, then do you know any better way than ```
timeout 10 cvlc -v -vv --volume 0 --novideo --open "$1" --file-logging > vlc_output 2> ~/televize/$i.check
``` and then just grep the output? The problem with VLC is that it takes it too long to really "check" if the stream works (yes, I have to use timeout 10:( ). Actually, I am aiming to check about 80 streams, so it really matters how long it takes.
If you want to see my current script, it is available [HERE]("http://ubuntuone.com/p/yKR/") (sorry it is packaged in a *.deb package).

Yep and if you have any comments about the script, I would be really glad, because it is one of my first linux works :)

---

