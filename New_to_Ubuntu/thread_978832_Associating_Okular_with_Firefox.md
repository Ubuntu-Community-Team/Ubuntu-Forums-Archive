---
title: "Associating Okular with Firefox"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by scribbles on 2008-11-11
How do I add PDF/Okular associations in Firefox?

When I go to open a PDF and select the program to open it with, the only thing I can find is /usr/share/applications/kde4/okular.desktop ...

I'm tired of having to download first...

---

### Post by shoot2kill on 2008-11-11
open with... type in 'firefox'
if it opens firefox with a download file dialogue box, then you need to install an adobe reader plugin to firefox.

---

### Post by sarang on 2008-12-26
Me wants OKULAR waahh

acroread <<<< okular

---

### Post by Raviolios on 2009-03-30
Associate /usr/bin/okular. That will open a pdf link in firefox to a new okular window.

---

### Post by sarang on 2009-07-12
Another way: Using the mozplugger package. Install mozplugger, edit /etc/mozpluggerrc and comment out lines as required in the PDF mime-type section of the file.

---

### Post by bubbapete on 2009-12-17
So maybe this isn't a great workaround, but... Evince was always slow for me from the desktop, so I had uninstalled it and was trying to get ePDF or Okular to work. I landed at this: Use Okular on the desktop, use evince in Firefox. Okular doesn't seem to play nicely in Firefox, but evince is pretty speedy and works clean.

---

### Post by xeros on 2010-10-07
> **sarang said:**
> Another way: Using the mozplugger package. Install mozplugger, edit /etc/mozpluggerrc and comment out lines as required in the PDF mime-type section of the file.

Thanks, it's great advice!
I haven't thought that it will work so good.

Now I've completely removed Adobe Reader as it gives me many problems (with opening files, window decorations, security updates, html rendering, etc.).

Okular does meet my needs in 100%, it's so quick to run, load and render PDFs (I use Kubuntu), works will all PDFs I have found and has more usefull options than Adobe Reader.

---

### Post by beew on 2010-10-07
> **xeros said:**
> Thanks, it's great advice!
I haven't thought that it will work so good.

Now I've completely removed Adobe Reader as it gives me many problems (with opening files, window decorations, security updates, html rendering, etc.).

Okular does meet my needs in 100%, it's so quick to run, load and render PDFs (I use Kubuntu), works will all PDFs I have found and has more usefull options than Adobe Reader.


Okular is slow, though I am sure still faster than Adobe(it is a piece of bloated junk even in Windows) When it opens a document, the loading takes a long time. It may be because I use gnome or maybe because Okular uses gv as its backend. Evince used to be slow too, but by some unknown magic the 2.32 version is very fast and much faster and renders better than Okular. Unfortunately version 2.32 is only avaliable in Maverick (or if you compile from source I suppose). I raided the Maverick repo and installed it in my Lucid box. If it breaks the system, then so be it, the improvement from whatever version in Lucid to 2.32 is simply amazing. It has been working fine though I did get into some dependencies problems but I fixed them, everything works beautifully now.

---

