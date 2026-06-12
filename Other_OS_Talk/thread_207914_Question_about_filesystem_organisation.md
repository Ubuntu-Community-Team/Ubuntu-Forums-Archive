---
title: "Question about filesystem organisation"
date: 2006-07-02
forum: Other OS Talk
---

### Post by Tortanick on 2006-07-02
I've never been able to understand the logic behind the way programs are stored in the file system. I understand why /bin and /sbin are seprate from /usr but why split it into /opt /usr and /usr/local

Could someone explain to me the underlying logic please

---

### Post by 23meg on 2006-07-02
[http://techrepublic.com.com/5102-10877-5960961.html](http://techrepublic.com.com/5102-10877-5960961.html)
[http://ubuntuforums.org/showthread.php?t=126107](http://ubuntuforums.org/showthread.php?t=126107)

---

### Post by Tortanick on 2006-07-03
You seem to have missunderstood my question, I know how the file system works, and I know what each part of the tree is used for, I just don't know why /opt even exists, or why /usr contains programs and /usr/local as opposed to /usr containing only /usr/shared & /usr/local

I was asking for the explanations on why this perticular organisational structure was chosen

---

### Post by az on 2006-07-03
Debian (and so ubuntu) does not use /opt or /usr/local.  You are not encouraged to use them.  However, some esoteric applications may install stuff there, if you compile them from source.

---

### Post by Tortanick on 2006-07-03
Now that makes sense :D

---

