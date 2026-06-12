---
title: "Send a Fax using PHP"
date: 2010-10-13
forum: Programming Talk
---

### Post by CrusaderAD on 2010-10-13
Does anyone know if there's a way to send a fax with a Ubuntu Server running PHP?

---

### Post by Zugzwang on 2010-10-13
Should be no problem. Just run an external command line fax program using "exec" or the like: [http://www.linux.com/community/blogs/Hylafax-send-a-fax-from-the-command-line.html](http://www.linux.com/community/blogs/Hylafax-send-a-fax-from-the-command-line.html)

---

### Post by CrusaderAD on 2010-10-13
Thanks for the reply. When I try it, I get this:

```
textfmt: No font metric information found for "Courier-Bold".
Usage: textfmt [-1] [-2] [-B] [-c] [-D] [-f fontname] [-F fontdir(s)] [-m N] [-o #] [-p #] [-r] [-U] [-Ml=#,r=#,t=#,b=#] [-V #] files... >out.ps
Default options: -f Courier -1 -p 11bp -o 0
Error converting document; command was "textfmt -B -f Courier-Bold	-Ml=0.4in -p 11 -s default >'/tmp//sndfaxjh4now' <'test.ps'"

```

Any ideas?

---

### Post by s.fox on 2010-10-13
Hello,

Can you post the command you tried to run please :)

---

### Post by CrusaderAD on 2010-10-13
Sure:

```
sendfax -f "test@test.com" -R -r "This is a test" -c "This is a test comment." -x "Test Person" -d "Recipient@12223333" test.ps
```

I substituted the values in the comment. I did use valid info. I also tried with test.txt, but I read that I needed to convert to .ps, so I used text2ps.

---

### Post by CrusaderAD on 2010-10-28
Bump

---

