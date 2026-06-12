---
title: "Evolution crashes when saving an attachment"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by ctn03 on 2008-05-30
I'm running Evolution on Hardy.  Evolution crashes every time I try to save an attachment (jpeg, pdf etc.)

Don't know if this is related but Firefox also cannot save files (the Save File window pops up but nothing is downloaded).  However firefox does not crash...Thanks.

---

### Post by spiderbatdad on 2008-05-30
I was having a similar problem with another mozilla browser. I went to about:config (in the address bar) and scrolled to the line: **ui.allow_platform_file_picker** right click on the value 'true' and select 'toggle' to change the value to false. This solved my browser-file-saving problem. I don't think it is associated with evolution in anyway, but I can't say for sure.

---

### Post by ctn03 on 2008-05-30
Thanks Spider.  Changed ui.allow_platform_file_picker to FALSE but Firefox still unable to save files. What does that function do anyway?

---

### Post by spiderbatdad on 2008-05-30
When you tried to test it, had you closed and restarted the browser?
To answer the question, it appears to use the browser file saving tool vs. your platform's...ie, nautilus. I can't say for sure. It solved the problem for me of the browser crashing on the first attempt to save some file types. I could re-open and return to the site...usually saved on the second attempt...but a very annoying process.
Making that change eliminated the problem.

---

### Post by ctn03 on 2008-05-30
Hey Spider, I tried it again.  Restart firefox as well as ubuntu but still doesn't work.

---

