---
title: "How to read M4A tags?"
date: 2008-07-27
forum: Programming Talk
---

### Post by Anessen on 2008-07-27
I am in the process of writing a program in C++ that can read both MP3 and M4A tags and rename the files accordingly. 

I have no problems reading the IDV3 tags stored in the MP3 files, but I can't find any information anywhere about how tags work in M4A files. 

How can I find tag information in this format?

---

### Post by Mr.Macdonald on 2008-07-27
If i am right, then M4A is Apple format. Being a communist company they will probably not release the specifications.

I looked around and haven't found any programs (free world) that can play M4A.

If you can see the tags through the properties window (right-click properties) then some how you must be able to read and write tags, but ...

If i really comes to it you could use a hex editor and try and make your own tag writing algorithm. I wouldn't suggest it, its just way to much work.

It really kind of sucks but that is communism for you!

---

### Post by Anessen on 2008-07-28
So I may as well just convert them anyway.

...what the hell has Apple got to do with Communism?

---

### Post by StOoZ on 2008-07-29
what is a hex-editor and how can it help if I may ask?

---

### Post by Tim Sharitt on 2008-07-29
You may or may not find this useful
[http://atomicparsley.sourceforge.net/mpeg-4files.html]("http://atomicparsley.sourceforge.net/mpeg-4files.html")
Personally, I gave up on trying to read the tags myself and just let faad do it.

---

