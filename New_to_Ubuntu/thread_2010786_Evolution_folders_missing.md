---
title: "Evolution folders missing"
date: 2012-06-26
forum: New to Ubuntu
---

### Post by Arachan on 2012-06-26
Hello,

I've been using Evolution for quite a while and I have it set up to download (and remove) all my emails from my external email account and store them locally.

Recently I opened Evolution and in the left pane none of my folders showed up. I did some research and found that they are stored in

```
/home/arachan/.local/share/evolution/mail/local
```How do I get import them back into Evolution?

Thanks,
arachan.

---

### Post by Arachan on 2012-07-14
bump... anyone know anything about this?

---

### Post by Andrew Mozilla rude on 2012-10-20
Here is one thread that give plenty of links for various solutions:
[http://ubuntuforums.org/showthread.php?t=1858475](http://ubuntuforums.org/showthread.php?t=1858475)

The link that pertains to you:
[http://ubuntuforums.org/showthread.php?t=1859630](http://ubuntuforums.org/showthread.php?t=1859630)
It suggests you switch to Mozilla (Thunderbird, ThunderFly, SeaMonkey).
That is if your mail files are still there not missing.

Perhaps Evolution is also based on Mozilla. Then there's very little difference.

If your **files** are **missing**, then you may have hit the greatest old **bug**. Many others hit it too. **Nobody bothered** to look for it. Only I did.

[https://bugzilla.mozilla.org/show_bug.cgi?id=674742](https://bugzilla.mozilla.org/show_bug.cgi?id=674742)
The **bug** of **compaction destroys mail**, if errors in file handling occur simultaneously.
The latest description of the bug, warning, tips on recovery, and **evil** behaviour of **Mozilla**:
[https://skydrive.live.com/redir?resid=4054B703688E4734!105]("https://skydrive.live.com/redir?resid=4054B703688E4734%21105")

Mozilla tries to **conceal** this bug, and remove any link to it. They urge users not to read it. And even lie to them that it is irrelevant.

Yet the public has to beware of the bug, and to learn hints on recovery as much, and as early as possible.
[B]
_Spread the word._
[/B]And help me **change *Mozilla***.****

---

### Post by newb85 on 2012-10-20
Evolution is *not* based on Mozilla.

---

