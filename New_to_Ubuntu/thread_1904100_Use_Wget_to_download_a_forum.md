---
title: "Use Wget to download a forum?"
date: 2012-01-04
forum: New to Ubuntu
---

### Post by userub on 2012-01-04
Hello,

I have a forum my friends and I used to post in. It's a free Zetaboards forum, and I'd like to be able to download the threads and save them on my hard drive.

There are enough threads and replies-within-threads that it would be too much for a manual save.

Could I use Wget to archive the forum? What is the syntax for it?

Thank you.

---

### Post by mastablasta on 2012-01-04
here you go:
[http://www.gnu.org/software/wget/manual/wget.html](http://www.gnu.org/software/wget/manual/wget.html)
 
wow that was hard to find... :-)
 
anyway you can use 
 
man wget 
 
to see commands and instructions in terminal.

---

### Post by anewguy on 2012-01-04
Of course there are a couple of other things for you to consider:

- if you download the forum as a single file then you'll need whatever database they use, the scema, etc., so you can load it back into some form of the searchable original content.

- you have to have something to view the database with - like the same forum software


I'm running a little weird right now due to a medical procedure earlier, but I think these things are valid.

Either way, you've got a lot of work ahead of you - hope you're prepared for it!

Dave ;)

---

### Post by mastablasta on 2012-01-04
you are correct wget might actually not be the way to go.
 
i think you can export the database... usually in cpannel ypou go to database (mysql?!) and do the export there and alter import.
 
but if you just want to save it you can use wget.

---

### Post by userub on 2012-01-04
I'd like to use the Wget option instead of an export.

Would I need to install Wget?

What sort of commands would I use? I found a line that goes like this:
[FONT=monospace]
[/FONT]wget -k -m -E -p -np -R memberlist.php*,faq.php*,viewtopic.php*p=*,posting.php*,search.php*,ucp.php*,viewonline.php*,*sid*,*view=print*,*start=0* -o log.txt [http://www.example.com/forum/](http://www.example.com/forum/)

Will that work? I tried to enter that in Terminal but nothing happened.

---

### Post by userub on 2012-01-04
bump

---

### Post by userub on 2012-01-05
Okay, I used this code:

wget [-k -m -E -p -np -R] <url>

It worked wonderfully to save a website.

When I tried it on the forum, though, it didn't work. It only grabbed the index page and a .css file.

What I would like it to do is save the index page, sub forums, and threads.

Is this possible?

---

### Post by userub on 2012-01-05
No responses today.

Is there a better place to post questions about Wget?

---

### Post by userub on 2012-01-05
bump

Should I try posting about this in another forum? I'm not sure which one is best.

---

### Post by anewguy on 2012-01-05
Quit bumping your thread - forum rules -> wait 24 hours.  I realize this may be important to you, or perhaps you want to do it while you have time, but this is a volunteer forum - everyone's problems rate equally.  To be honest, you probably won't get much help here.  It's not an Ubuntu problem, it's not even really a problem of any sort.

My suggestion:  contact the maintainers of that forum directly for help.  And watch for copyright/privacy notices as you may not be allowed to do this.

In the mean time, I would just close this topic on this forum.

Dave ;)

---

### Post by lisati on 2012-01-05
It might be a good idea to seek the blessings of the board's hosts. Their [TOS]("http://www.zetaboards.com/tos/") mention excessive hotlinking: downloading an entire board might be misconstrued as "excessive hotlinking." There are also privacy issues to address such as [COPPA]("http://www.coppa.org/").

---

