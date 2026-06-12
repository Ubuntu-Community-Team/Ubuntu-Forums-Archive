---
title: "Auto-updating (the concept)"
date: 2008-05-10
forum: Programming Talk
---

### Post by POW R TOC H on 2008-05-10
I'm making a program, and I need to make an auto-updater, that will download and apply the patch. I was thinking of using wget, diff and patch, but my employer probably won't be releasing the program under GPL, so I can't :( 
So, I need to make my own system for auto updating, but I'm a little short on time, so I don't want to experiment much, I'd rather create something based on already-used-and-tested solutions :)

So, the purpose of this thread is this :
Can you please point me to some good articles which deal with this problem, or suggest which approach should I use on this?
And no, I don't expect anyone to do my work, I merely need someone to direct me, so I don't waste much time on wrong or bad solutions for the problem.

Thank you in advance, and sorry if my English is a bit rusty, it's not my native language...

---

### Post by WW on 2008-05-10
So you are saying that if you create, say, a bash script that uses wget, diff, and patch, the script must be GPL because the tools are?  I didn't think the "viral" aspect of the GPL was that strong, but I'm not a lawyer.

---

### Post by POW R TOC H on 2008-05-10
No, I'm saying that I can't create a script, nor use any Open Source (or any other) solutions. I must make my own solution, but it CAN be based on anything...

---

### Post by pmasiar on 2008-05-10
IANAL but I am pretty sure anyone can create custom tcl/tk or bash script to manage updates with wget, diff and patch. Functionality (API) is not under GPL, only concrete implementation, and if you don't change implementation, you can safely use utility's API. BTW, there are utilities under BSD license, which you can even modify and distribute without sources, if you want.

---

