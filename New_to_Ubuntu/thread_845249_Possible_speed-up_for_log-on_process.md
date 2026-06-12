---
title: "Possible speed-up for log-on process?"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by pete-the-meat on 2008-06-30
My friend was talking about a hack he implemented to speed up his log-on time. I think he uses Gentoo but I was wondering if there was a way of implementing the equivalent of this in Ubuntu. he says that he creates a script to start X and puts the command to lock the screen in xinitrc (I am not familiar with this file). Then put that script as the first as the first entry in inittab instead of the display manager or /sbin/login. The idea of all of this being to log into a password protected session instead of starting everything when logging on.

Is this possible in Ubuntu? I am interested in implementing this but am clueless as to where to start researching this. Any helps or explanation that anyone can provide would be great.

Thanks :)

---

### Post by bumanie on 2008-06-30
You can try this from softpedia. Careful, if you make a mistake, you may have to reinstall. Also it will probably only save a few seconds. [http://news.softpedia.com/news/Optimize-Ubuntu-8-04-for-Speed-86405.shtml](http://news.softpedia.com/news/Optimize-Ubuntu-8-04-for-Speed-86405.shtml)

---

### Post by pete-the-meat on 2008-06-30
I saw that article a while ago and implemented most of it. The hard-drive guide caused me some problems and I had to backtrack to get rid of what I added, which took a while, because it would keep mounting my filesystem as read-only so that X would never start. The only thing I didn't implement was the automatic log-in, I live in a family environment and I would be very wary of having my little sister poking about in my stuff.

You're right though, it didn't realy make any appreciable difference but my problem is not the boot speed of Ubuntu, it boots really quickly with which I'm happy. It's  typing in my password and then waiting for all my icons, panels, screenlets etc to appear before I can start. :(

---

