---
title: "Where/how to install my spiffy new program"
date: 2006-10-16
forum: Programming Talk
---

### Post by Majaman on 2006-10-16
So I ported this windows program I made to linux. Well, ported, it actually compiled right off the bat... But being a total n00b on linux I have no idea how to access said program globally. It is a command line file utility so I need access it everywhere. So how do I do that in linux? I don't really want to create a complete .deb package. I just want to place the file where linux(bash?) can find it, or better, tell linux where to find it. Is there something like a PATH variable somewhere?

And also, I installed monodevelop and can't find how to insert breakpoints for debugging. Is it even possible?

Thanks,
Majaman

--------------------------------------------------------------------------
Upon seeing the package material of a new monitor.
Beginner geek:
"Who left the monitor packaging here?"
Intermediate geek:
"Looks like someone got a new 24" Mitsumi XLG/p 8ms monitor with antishading option."
Expert geek:
"That would make a wicked fort for my Lego men."
--------------------------------------------------------------------------
Above text remembered from a cartoon somewhere.

---

### Post by SoggyCornflake on 2006-10-16
Type path on a command line if you want to see the path.

If you want to add a program, there's lots of flexability.  You can use the path output to give you an idea where to look.

I think /usr/local/bin would be where I'd put a program I wrote assuming I'd want other users on my machine to be able to run it.

---

### Post by Majaman on 2006-10-16
Wow, that was quick. Thanks a lot.

Majaman

---

