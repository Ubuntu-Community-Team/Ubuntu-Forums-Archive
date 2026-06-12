---
title: "Am I running 32bit or 64bit, and how do I convert?"
date: 2012-01-01
forum: New to Ubuntu
---

### Post by xlucidreamx on 2012-01-01
I ran uname -m and the result was i686 so I assume that is 64 bit.
How do I, if possible, to convert to 32bit software. Thanks.

---

### Post by Elfy on 2012-01-01
Try -a 

Anyway I am 32bit

3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:34:47 UTC 2011 i686 athlon i386 GNU/Linux

---

### Post by 1clue on 2012-01-01
If you have multilib or 64-bit and want to convert to 32-bit then your only option is to reinstall from scratch.  You can make a backup of your data but that's about it.

i686 is not 64-bit.  You would need to see x86_64 or ia64 on Intel platforms.

---

### Post by xlucidreamx on 2012-01-01
Okay, I did that and the result: 
Linux user-desktop 2.6.27-7-generic #1 SMP Fri Oct 24 06:42:44 UTC 2008 i686 GNU/Linux.

So I'm running 64bit?
I really appreciate the help. I'm lost.

---

### Post by 1clue on 2012-01-01
That's a 32-bit kernel and if you're using that then there is no possibility of using 64-bit software that I know of.

---

### Post by xlucidreamx on 2012-01-01
That's all I needed to know. Thanks!

---

