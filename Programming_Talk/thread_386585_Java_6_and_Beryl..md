---
title: "Java 6 and Beryl."
date: 2007-03-17
forum: Programming Talk
---

### Post by Rizado on 2007-03-17
So I'm trying to get swing applications to work properly with beryl. I found this great [guide.](http://wiki.beryl-project.org/wiki/Java) Problem is, the patch is not working. 

```
$ cat patch | patch -p1 --dry-run
patching file j2se/src/solaris/classes/sun/awt/X11/XDecoratedPeer.java
Hunk #1 succeeded at 692 with fuzz 2.
patch: **** malformed patch at line 18: {
```

Any ideas?

---

### Post by diafanos on 2007-03-17
I used a similar guide too (i can't remember now where i found it ) and i got the same type of error. 
I found out that it was just a copy-paste problem.

Check if the text you paste is identical to the one of the online guide (any wrong line brake maybe).

If I find the guide I used, I'll post it...

P.S. It's better (for me at least) to use a graphic text editor (gedit) than nano or vi.

---

### Post by Rizado on 2007-03-17
> **diafanos said:**
> I used a similar guide too (i can't remember now where i found it ) and i got the same type of error. 
I found out that it was just a copy-paste problem.

Check if the text you paste is identical to the one of the online guide (any wrong line brake maybe).

If I find the guide I used, I'll post it...

P.S. It's better (for me at least) to use a graphic text editor (gedit) than nano or vi.Nope, that's not the problem. I opened the html source and copied. I also used kate. If my patch isn't working the one in the guide isn't working either. I wouldn't be surprised if it's ****** up, it's not the first time and won't be the last. People just don't understand html fucks everything up. It's better to link to a regular text document.

I'm pissed right now. No swing applications work as they should and the solution is just one crappy patch away.

---

### Post by diafanos on 2007-03-17
this is the patch file i used and everything went fine. Just rename it to "patch" (without the .txt suffix)

I hope will solve the problem...

---

### Post by Rizado on 2007-03-18
That patch had two linebreaks that should not be there around line 67. I removed thoose and patching went great.

Thanks! Now I can run my java apps with beryl!

---

### Post by diafanos on 2007-03-18
> **Rizado said:**
> That patch had two linebreaks that should not be there around line 67. I removed thoose and patching went great.

Thanks! Now I can run my java apps with beryl!

Oh, yes, my fault....

I fixed it and i uploaded again, in case anyone wants it

---

### Post by faical117 on 2008-01-08
thanks work for me :)

---

