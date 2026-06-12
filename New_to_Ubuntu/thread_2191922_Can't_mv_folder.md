---
title: "Can't mv folder"
date: 2013-12-05
forum: New to Ubuntu
---

### Post by squakie on 2013-12-05
I have a folder that now has a question mark at the end created by me in I don't how know how way:

```
davePi:/var/media/xbmc-shares/VIDEOS/ANIMATED/holdit # ls
Gulliver's.Travels(1939)?
davePi:/var/media/xbmc-shares/VIDEOS/ANIMATED/holdit # 
davePi:/var/media/xbmc-shares/VIDEOS/ANIMATED/holdit # mv Gulliver\'s.Travels\(1
939\)\? Gulliver\'s.Travels\(1939\)
mv: can't rename 'Gulliver's.Travels(1939)?': No such file or directory
davePi:/var/media/xbmc-shares/VIDEOS/ANIMATED/holdit # 


```

I thought I was escaping things correctly, but it's not working.  I also can't set my working directory to it with the same string.

I know I've done SOMETHING stupid - can anyone help a dumb guy out?

Thanks.

[COLOR=#0000ff]EDIT:  Just if it helps:  I know it got this way when I did the following:

mv "Gulliver's.Travels(1939(" "Gulliver's.Travels(1930)

and forgot the ending quiote.  It came up with the continuations ">" to whcih I *thought* I just put a quote.
[/COLOR]

---

### Post by childsey01 on 2013-12-05
I don't think you need to escape the ? and move does work, i.e. if it really is a question mark. More likely you've gotten some nonprintable character in there that the shell has just gone stuff it I'll just print '?' If you want to find out what it is try: ls -b
Of course only having one file there, you can always use a wildcard *

---

### Post by squakie on 2013-12-05
Well, I finally got around it:

davePi:/var/media/xbmc-shares/VIDEOS/ANIMATED/holdit # cp Gulliver\'s.Travels.*/*.* ..

Tried everything else I could think of, but this at least let me copy the files out of the bad folder so I can create a new one with the right name and move the files there.  Now I can delete the folder, I hope.

I'm doing this over ssh from ubuntu to a Raspberry Pi (still linux).

---

### Post by squakie on 2013-12-05
> **childsey01 said:**
> I don't think you need to escape the ? and move does work, i.e. if it really is a question mark. More likely you've gotten some nonprintable character in there that the shell has just gone stuff it I'll just print '?' If you want to find out what it is try: ls -b
Of course only having one file there, you can always use a wildcard *

Yep - that would be thanks to me pressing enter, getting the continuation prompt ">" and finishing the command - the imbed return (or lf or cr/lf or what ever is generated) stuck a non-prinitable character in there.  Ijust don't understand why it didn't work on the folder when I put an * in place of the ?.  Oh well - it's fixed.

---

