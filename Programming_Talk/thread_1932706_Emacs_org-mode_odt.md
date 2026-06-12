---
title: "Emacs org-mode odt"
date: 2012-02-27
forum: Programming Talk
---

### Post by jldoll on 2012-02-27
I've been using emacs org-mode for a brief period, and have just about everything working the way I want except one thing. I can't open links to odt files with libreoffice.  I've been able to link all other file types of interest with my favorite program, but with odt it seems my org-file-apps override gets overwritten by some other default which tries to open the file in emacs as xml.  Is there any way to block the default behavior for odt. A last resort is to rename/resave all of my files as doc. I renamed one as a test and it worked, but I really don't like these kind of workarounds.

---

### Post by jldoll on 2012-02-27
> **jldoll said:**
> I've been using emacs org-mode for a brief period, and have just about everything working the way I want except one thing. I can't open links to odt files with libreoffice.  I've been able to link all other file types of interest with my favorite program, but with odt it seems my org-file-apps override gets overwritten by some other default which tries to open the file in emacs as xml.  Is there any way to block the default behavior for odt. A last resort is to rename/resave all of my files as doc. I renamed one as a test and it worked, but I really don't like these kind of workarounds.

Not sure what my typo was. I checked and rechecked, but didn't see anything wrong. However I had a different error about ini not finishing loading. Since adding odt override was the last thing I changed I removed it. Ini problem fixed. Re-keyed in odt override from memory. Everything works.

---

