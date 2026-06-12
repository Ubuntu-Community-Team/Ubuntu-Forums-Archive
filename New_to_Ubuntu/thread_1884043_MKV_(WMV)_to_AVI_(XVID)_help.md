---
title: "MKV (WMV) to AVI (XVID) help"
date: 2011-11-20
forum: New to Ubuntu
---

### Post by maja_ldm on 2011-11-20
Hello Everyone,

I'm totally new and I basicallu need a mencoder GUI with enough options to do what I want or someone to help me with the mencoder command line.

I want to convert an MKV file (WMV+AAC) with subs to an AVI file (XVID&MP3) with a separated file for the subs.
I'd just want "about the same size wmv to xvid".


I already extracted and converted the subs to what I wanted.

I tried a Kommander script called MKV2AVI that does the job but leaves the subs as hardsubs even when told not to do it.

I tried avidemux but it doesn't read WMV, kdenlive crashes when I try to open the sourcefile, other apps I found here ([http://forum.doom9.org/showthread.php?t=89543](http://forum.doom9.org/showthread.php?t=89543)) aren't compatible with 64-bit.


could you please help me?

---

### Post by ron999 on 2011-11-20
> **maja_ldm said:**
> ... need a mencoder GUI with enough options to do what I want... 
Hi
DivXConverter is a GUI for MEncoder, maybe it will be OK for your job.
[http://code.google.com/p/foxoman/wiki/DivXConverter]("http://code.google.com/p/foxoman/wiki/DivXConverter")

---

### Post by SeijiSensei on 2011-11-20
Off the top of my head, I think you want something like:

```
mencoder -o file.avi -ovc xvid -xvidencopts pass=1 -oac mp3lame -sid 99 file.wmv
```

Setting the -sid to a high number will suppress the subtitles.  This does single-pass encoding.  If you want double-pass encoding you'd need something like:

```
mencoder -o /dev/null -ovc xvid -xvidencopts pass=1 -oac mp3lame -sid 99 file.wmv
mencoder -o file.avi -ovc xvid -xvidencopts pass=2:bitrate=1200 -oac mp3lame -sid 99 file.wmv
```

The first pass writes a file that the second pass uses to improve the quality of the encoding.  I'd take a look at the video bitrate mencoder reports for the first pass to determine what value to set for this in the second pass.  1200 might be higher than the source material supports; 800 gives pretty decent results as I recall.  (I don't re-encode anything these days; I just watch H.264-encoded .mkv's with smplayer.)

I recommend this document for using mencoder: [http://en.gentoo-wiki.com/wiki/Mencoder](http://en.gentoo-wiki.com/wiki/Mencoder)

---

### Post by Jacobonbuntu on 2011-11-20
> **maja_ldm said:**
> Hello Everyone,

I'm totally new and I basicallu need a mencoder GUI with enough options to do what I want or someone to help me with the mencoder command line.

I want to convert an MKV file (WMV+AAC) with subs to an AVI file (XVID&MP3) with a separated file for the subs.
I'd just want "about the same size wmv to xvid".


I already extracted and converted the subs to what I wanted.

I tried a Kommander script called MKV2AVI that does the job but leaves the subs as hardsubs even when told not to do it.

I tried avidemux but it doesn't read WMV, kdenlive crashes when I try to open the sourcefile, other apps I found here ([http://forum.doom9.org/showthread.php?t=89543](http://forum.doom9.org/showthread.php?t=89543)) aren't compatible with 64-bit.


could you please help me?

I am not sure I understand exactly what you want, but you might also want to check out Arista, which is a feature-rich converter, not very well-known, but it works perfectly.
[http://www.transcoder.org/](http://www.transcoder.org/)
also in the repository...

---

### Post by maja_ldm on 2011-11-20
thank you all for your replies.

in the end I used the mencoder command line and had what I wanted, nice quality e no subs. I could have never imagined the right command, thanks SeijiSensei.

DivXConverter is nice but to use it I should have demuxed the file stripped it of the subs and remuxed it. with avidemux blocked by the combination of mkw&wmv I was a bit at a loss.

Arista seems to have profiles a bit too simple for what I had in mind. anyways I have it installed and maybe I'll use it for my phone videos when I'll need it.

thank you all again :)

---

### Post by maja_ldm on 2011-11-21
I have another doubt:

for batching a whole folder I can use:
for i in /var/media/*.avi; do mencoder -ovc XXX $i -o $i.output; done

which is one command, but if I want to do a 2pass xvid how should I write it? can I do all the first passes then all the second passes?

---

### Post by SeijiSensei on 2011-11-21
```

for f in /var/media/*.avi
do
mencoder ... -xvidencopts pass=1 $f
mencoder ... -xvidencopts pass=2:bitrate=1200 $f
done

```

If you want to get fancy, you can use sed to strip the extension and create output files with matching names like this:

```

for f in /var/media/*.mkv
do
NEWNAME=$(echo $f | sed 's/\.mkv$//g')
mencoder -o $NEWNAME.avi ... -xvidencopts pass=1 $f
mencoder -o $NEWNAME.avi ... -xvidencopts pass=2:bitrate=1200 $f
done

```

---

### Post by maja_ldm on 2011-11-21
unfortunately I noticed the files have different bitrates thus I'll have to check the first pass one by one. anyways thank you again SeijiSensei.

---

