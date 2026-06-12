---
title: "inotify"
date: 2008-09-02
forum: Programming Talk
---

### Post by mailforbiz on 2008-09-02
Hi all

I am relatively new to doing C programming for Linux so pardon my confusion but I was trying out a simple example of inotify and it doesn't seem to work. I get this:

open("/dev/inotify", O_RDONLY) = : No such file or directory

/dev/inotify is indeed non-existent. Doing some search about this, it seems that the way inotify works have changed in recent kernels with it no longer requiring a /dev device. Can someone point me to some information about how to go about using inotify as it exists now? The intended use is in an embedded system to detect changes in some status files. Any feedback about alternatives to inotify if they exist would be welcome too.

TIA,
HT
[Using Hardy 2.6.24.19 generic]

---

### Post by weresheep on 2008-09-02
Hello,

I've never used the inotify API myself, but a there are some man pages available. I would start with...

```

man 7 inotify

```

although, you may have to install the 'manpages-dev' package first.

Hope that helps.
-weresheep


PS:- You can use the 'apropos' command to search the man pages for relevant subjects.

---

### Post by mailforbiz on 2008-09-09
Thanks, I got a test program working fine. Now onto some more heady stuff :-)! BTW, is there a way to use inotify for monitoring processes?

---

