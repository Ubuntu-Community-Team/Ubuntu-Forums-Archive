---
title: "Firefox downloads stall -- permissions?"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by grikdog on 2008-04-26
I've just installed Hardy (been playing with it for a few hours), and suddenly Firefox 3 Beta 5 (or Firefox 2, for that matter) can't download a file anymore.

Have I screwed up permissions on my Desktop or Download folder?  Is there an encompassing shell/layer/userproofing/tamperproofing envelope that only sysadmins know about?  This should be obvious and straightforward, but I'm baffled.  What could be wrong?

Downloads begin, then hang with a small part-file and an empty name-file, just like normal, except that the part-file no longer increases in size, and the progress bar never advances beyond zero.

TIA.:confused:

---

### Post by Nano Geek on 2008-04-26
That's odd. It doesn't sound like a permissions problem to me. 

Is Firefox giving you any error messages, can you see the download speed decreasing while it's downloading, or is it just stopping suddenly?

---

### Post by grikdog on 2008-04-26
> **asjdfwejqrfjcvm msz34rq33 said:**
> That's odd. It doesn't sound like a permissions problem to me. 

Is Firefox giving you any error messages, can you see the download speed decreasing while it's downloading, or is it just stopping suddenly?
No, it just pops up the download window and stalls immediately.  If you quit Firefox, it reminds you that a download is in progress, but progress it does not.  Threadlock?  I've tried reinstalling.  No joy.

---

### Post by Nano Geek on 2008-04-26
Have you tried a different browser to see if it does the same thing?

---

### Post by grikdog on 2008-04-26
> **asjdfwejqrfjcvm msz34rq33 said:**
> Have you tried a different browser to see if it does the same thing?

Funny thing... :lolflag:  Not only that, I just pulled Ubuntu off this Dell Inspiron (uninstalled Wubi), and then did a hard partition and install on a brand new system.

First thing I tried was Firefox 3 downloading.  Stalled.

Loaded the Epiphany browser.  Same file, same address. Stalled.

](*,)

---

### Post by Nano Geek on 2008-04-27
Sorry for the slow reply. Here are the only things that I can think might held to diagnose the problem.

[LIST]
[*]Does the same thing happen with every file you try to download?
[*]Does it happen in Windows with FF3 too, or just in Linux?
[*]Can you download the file using **wget**?
[/LIST]

---

### Post by grikdog on 2008-05-23
Sorry for the delay.  The stall stopped.  I think it must have been newbie syndrome.  There has been no problem with Firefox here since then.  Thanks to everyone who replied and apologies for my late TY's.

---

