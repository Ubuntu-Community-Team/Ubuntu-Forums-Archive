---
title: "purge or just remove?"
date: 2012-08-30
forum: New to Ubuntu
---

### Post by rodtaylor on 2012-08-30
Hi, I'm quite a newbie in Ubuntu. Can anyone please explain to me what the difference is between purge and remove in sudo apt-get command?

I read in one of the postings that purge gets rid of the config files as well while remove just the binaries. What does it mean? And most of all, when should we use purge or remove?

Thanks before!

---

### Post by cortman on 2012-08-30
> **rodtaylor said:**
> I read in one of the postings that purge gets rid of the config files as well while remove just the binaries. 

You've stated the difference between purge and remove.
Config files include any preferences you have changed or parameters the program has been given post installation to work with your computer and your needs.
If you want to completely remove a program, use purge. If you may want to install it again later and keep your settings, use remove.

---

### Post by rodtaylor on 2012-08-30
Nice and concise answer!! Thanks Cortman! :)

---

### Post by cortman on 2012-08-30
> **rodtaylor said:**
> Nice and concise answer!! Thanks Cortman! :)

No problem. :) Mark the thread [SOLVED] if it's a sufficient answer, with the thread tools in the upper right.

---

### Post by vasa1 on 2012-08-30
One more point ...
There may still be files in your home folder that are unaffected by **purge**. For example, Firefox stores user-specific data in ~/.mozilla and Google Chrome stores user-specific data in ~/.config/google-chrome.
Depending on your intentions, you may want to delete those folders as well.

---

### Post by rodtaylor on 2012-08-30
Good tips! Thanks a lot!

---

