---
title: "photo printing software"
date: 2008-10-27
forum: Programming Talk
---

### Post by gimmejimmy on 2008-10-27
Hello, I'm looking for free or low-cost open source photo printing software.  I can also try to write my own or hire/persuade someone to do it for me.  I've searched around the web but there isn't anything with everything I need.  Here's how it should work:
1.  The user selects a picture source (optical drive, flash drive, card reader, directory, etc.) to import pictures from.
2.  The next screen shows all the pictures and the user then selects which ones to work on.
3.  The user does some basic editing (zoom, brightness, contrast, autolevels, etc.) and selects from a few predefined layouts and paper sizes.
4.  User clicks "Print" and the job is spooled.  If there are no other pending jobs printing starts.
5.  When the job is finished the user has the option of accepting the result or reprinting some of the pictures (same layout and picture size).
6.  Details (date, job number, number of prints, layout. paper size) of each job is stored in a database.
7.  While a job is printing the user can process other pictures.

Is there anything like this in existence, or something like it I can study and modify?  If not, where should I start?  I have some experience in C from 10 years ago.  Can I do this myself in six months or should I just hire someone?  Thanks.

---

### Post by hod139 on 2008-10-27
This sounds a lot like GTHUMB, [http://gthumb.sourceforge.net](http://gthumb.sourceforge.net)

---

### Post by gimmejimmy on 2008-10-27
Thank you.  I'll check it out.

---

### Post by ssam on 2008-10-27
do mean something like the software that runs on the self service photo printers in a camera shop.

---

### Post by gimmejimmy on 2008-10-28
Something like that, yes.  I already have a commercial application but it would be too expensive to license it for multiple locations, not to mention it runs on Windows which brings security and cost issues of its own.

---

### Post by gimmejimmy on 2008-10-30
I've tried both f-spot and gthumb and I need a little of both.  It's not very clear to me though how to get involved in either project.  I don't even know what to download to get at the source code.  A little help for a newbie?

---

### Post by hod139 on 2008-10-30
To get the source of gthumb used in ubuntu (includes ubuntu's patches)
```
 apt-get source gthumb

```

To get the source direct from them, go to there home page: [http://gthumb.sourceforge.net/home.html](http://gthumb.sourceforge.net/home.html)
It is right there to download.  For getting involved, see their feedback page: [http://gthumb.sourceforge.net/feedback.html](http://gthumb.sourceforge.net/feedback.html)

---

### Post by gimmejimmy on 2008-10-30
Thanks again!

---

