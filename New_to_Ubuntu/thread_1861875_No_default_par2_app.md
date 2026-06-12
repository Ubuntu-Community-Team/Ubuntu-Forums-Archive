---
title: "No default par2 app"
date: 2011-10-16
forum: New to Ubuntu
---

### Post by ricardisimo on 2011-10-16
Up until the very moment I upgraded to 11.10, either pypar2 or gpar2 could and would open my par2 parity files. Now not only do they not do it, there doesn't appear to be any way to set them as the defaults. "Show Other Applications" doesn't show either of them (even thought they're installed). and the only other option is now, evidently - to search for them online (which also doesn't work, by the way.)

How do I set one or the other as the default? Thanks.

---

### Post by ricardisimo on 2011-10-17
It would appear that the upgrade to 11.10 removed both gpar2 and pypar2 from my system. Why? Doesn't make any sense. Had to reinstall pypar2, but gpar2 no longer seems to be in any of the repos.

Anyhow, even though pypar2 is installed, nautilus (or the system in general) won't allow me to set it as the default app for par2 files. This is frustrating.

---

### Post by csarchet on 2011-10-19
For gpar2:

1.) Download the appropriate .deb file:

[http://launchpadlibrarian.net/14173229/gpar2_0.3-2.3_i386.deb](http://launchpadlibrarian.net/14173229/gpar2_0.3-2.3_i386.deb)
[https://launchpad.net/ubuntu/+source/gpar2/0.3-2.3/+build/580399/+files/gpar2_0.3-2.3_amd64.deb](https://launchpad.net/ubuntu/+source/gpar2/0.3-2.3/+build/580399/+files/gpar2_0.3-2.3_amd64.deb)

2.) Right click the file name in Nautilus and select 'Open with Ubuntu Software Center'

I haven't tested the i386 version but the amd64 version worked perfectly for me.  This process should work for most Debian libraries but they won't necessarily get updates.

---

### Post by ricardisimo on 2011-10-20
That solves half of the problem, namely finding gpar2. Thank you!

And I just noticed that it is the default application. Fantastic!

I'm still very much concerned that I cannot browse applications and set whatever default I want for certain types of files. Why has that option been taken away? It seems like we're in a slow, steady process of taking good options away from people? What gives?

---

### Post by SushiR on 2011-10-22
Dumb question: How exactly do I get the files out of par2 files?

---

### Post by gsmanners on 2011-10-22
I don't know about those front ends, but from a command line you just:

```
par2 r something.par2 *
```

And that recovers your archive (assuming you have just that one set in the folder).

---

### Post by SushiR on 2011-10-22
Thanks a lot!

---

### Post by BCtom on 2011-10-24
...and a big Thank You to you _[csarchet]("http://ubuntuforums.org/member.php?u=1474751")_. I can't believe how many of my favourite programs are missing from the Apps in 11.10 right now? Slowly, but surly, I'm getting my machine back to normal. Thanks for the quick fix! :)

---

### Post by pt123 on 2012-05-19
[http://pypar2.silent-blade.org/](http://pypar2.silent-blade.org/)

---

### Post by ricardisimo on 2012-05-30
> **pt123 said:**
> [http://pypar2.silent-blade.org/](http://pypar2.silent-blade.org/)

Doesn't work with special characters, which is the point of this thread.

P.S. - Sorry! My bad. I was confusing this with my other par2 thread. My apologies.

---

### Post by ricardisimo on 2012-10-29
Installed 12.10 fresh and it's happened yet again. I still don't understand why nautilus won't let me search for the appropriate app myself, as it always used to do. gpar2 is no longer in the repositories, and quite honestly I'm starting to like pypar2 better anyways. So how do I make it the default when opening files in nautilus?

---

### Post by pt123 on 2012-10-29
right click on a par file -- open with tab and add /usr/bin/pypar2

---

### Post by ricardisimo on 2012-11-01
> **pt123 said:**
> right click on a par file -- open with tab and add /usr/bin/pypar2

That's my point... there's no longer any place to enter a customized default program to open files in nautilus. See attached.

---

### Post by pt123 on 2012-11-02
Yes that sucks, maybe you could try tinkering with mime types
[https://help.ubuntu.com/community/AddingMimeTypes](https://help.ubuntu.com/community/AddingMimeTypes)

[http://askubuntu.com/questions/16580/where-are-file-associations-stored](http://askubuntu.com/questions/16580/where-are-file-associations-stored)

---

### Post by ricardisimo on 2012-11-03
I'm going to try assogiate file types editor (from the repos), as well as writing an email to [email]mime-support@packages.debian.org[/email] asking them to restore the mime type. The more emails the better, folks. Thanks!

---

### Post by ricardisimo on 2012-11-25
Still no love. Any way to get attention from mimetypes folks?

---

