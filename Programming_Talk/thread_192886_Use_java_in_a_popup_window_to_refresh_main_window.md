---
title: "Use java in a popup window to refresh main window"
date: 2006-06-09
forum: Programming Talk
---

### Post by damianubuntu on 2006-06-09
Hi,
I have mainly PHP and Mysql skills, and am struggling with introducing javascripts into my pages!  Can someone suggest what I might do with this scenario?  (Bear in mind that all my programming is selftaught, and probably full of errors and holes!)

I have a main window that opens a popup (for a calculator).  The popup has a form on it, the submit button calls the page again, but thsi tiem executes some mysql instead of displaying the form, and then uses onload=self.close() to get rid of itself and return the focus to the main window. 

I'm sure this is crude, but it works!  What I can't get to happen is for the main window to refresh after the mysql has been executed (i.e. to show some updated data)  I've wondered whether I might do a document.reload() on the main window, also as part of the onload=self.close() script.  BUT I don't know how to a) point it at the main window, and b) can I have two methods on one event?

Or am I going about this completely the wrong way!

Thanks for your help guys

Edit: I know this isnt too close to the real purpose of this forum, but I've had so much better help in the Ubuntu forums than elsewhere that I thought I'd take the liberty, in case someone can help me!!

---

### Post by hagen00 on 2006-06-09
Hi

A couple of things to start off with...Big difference between java and javascript...just for future reference.

> Edit: I know this isnt too close to the real purpose of this forum, but I've had so much better help in the Ubuntu forums than elsewhere that I thought I'd take the liberty, in case someone can help me!!This is definitely the purpose of this forum. I too have had better responses here than when going to language specific forums.

Anyway...try this piece of code on your popup window. Or just whack it into google and find out a bit more about it. 

```
window.opener.location.reload();
```

Cheers

---

### Post by damianubuntu on 2006-06-09
Thanks, just the job.

And, thanks for the encouragement to post!  I always feel such a noob with coding, so many forums seem full of stuff that I have no idea about, and my code always looks so clunky and longwinded by comparison - to me at least!!

---

### Post by jvictor on 2006-06-10
Java is ****NOT**** JS !

> A couple of things to start off with...Big difference between java and javascript...just for future reference.


---

### Post by damianubuntu on 2006-06-11
[QUOTE=jvictor]Java is ****NOT**** JS ![/QUOTE]

Sorry, like I said, bit of a noob really (and lazy in my definitions and semantics to boot!)

keep your hair on, mind ;-)

---

