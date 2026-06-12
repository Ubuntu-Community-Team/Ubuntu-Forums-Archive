---
title: "sendfax error"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by mamut0o1 on 2008-07-22
hello; I have installed hylafax server and I'm getting the following error:

/usr/sbin/textfmt: No font metric information found for "Courier-Bold".
Usage: /usr/sbin/textfmt [-1] [-2] [-B] [-c] [-D] [-f fontname] [-F fontdir(s)]
[-m N] [-o #] [-p #] [-r] [-U] [-Ml=#,r=#,t=#,b=#] [-V #] files... >out.ps
Default options: -f Courier -1 -p 11bp -o 0
Error converting data; command was "/usr/sbin/textfmt -B -f Courier-Bold -Ml=0.4
in -p 11 -s default >/tmp//sndfaxKOU8AP </home/markw/test_mw.txt"

I'm sure I have ghostscript installed and I dont understand why I'm getting this error. is there a "fonts" package that I might be missing?

Let me know; thanks:guitar:

---

### Post by a0u on 2008-07-22
Admittedly, I have no experience with Hylafax Server or Ghostscript, but a [quick search]("http://www.google.com/search?hl=en&rls=com.microsoft%3Aen-us&q=%2Fusr%2Fsbin%2Ftextfmt%3A+No+font+metric+information+found+for+%22Courier-Bold%22") suggests an improperly configured Ghostscript as one possibility.
 
> **mamut0o1 said:**
> is there a "fonts" package that I might be missing?
On the other hand, try installing [ttf-liberation]("http://packages.ubuntu.com/hardy/ttf-liberation") if you do not already have a Courier font.

---

### Post by mamut0o1 on 2008-07-22
I was going to try that tonight but I though someone might have a different solution.
Thanks for the reply

---

### Post by mamut0o1 on 2008-07-23
OK; if anybody has the same problem here is how I fixed it;
under /etc/hylafax/hylafax.conf 
There was an entry for FontMap that was invalid so I edited this file and point it at the right direction; in my case it was here:
/usr/share/ghostscript/8.61/lib
I added that at the end of the file and it works now.
thanks!

---

