---
title: "Convert MS Word doc into plain ASCII"
date: 2012-05-09
forum: New to Ubuntu
---

### Post by funops on 2012-05-09
Hi Folks. I have resurrected an older laptop (Toshiba Satellite A25-S279) that has Windows XP and I installed Ubuntu 12.04 the other day. Installation went smooth, fast, and I'm enjoyably cruising in Linuxville. :) While new to Linux, I have experience with UNIX (BSD) from years ago and to some extent via my iMac and the Terminal respectively.

Not wishing to replicate Windows, of course, but I have this one issue at the moment. I receive report documents written in MS Word. Unfortunately it has typographical formatting that interferes with my need to convert the docs into plain ASCII; such as so-called Smart Quotes, em/en dashes, ellipsis, and so forth. I wish they would turn such off when writing their docs but I have no control over that.

So I'm looking for a means or program/editor that can simply convert the doc to ASCII. I installed and tried catdoc but that doesn't do the trick (Smart Quotes and so forth are still there, etc.) LibreOffice Writer can read the file fine but even if I save it as a .txt file, I'm still stuck with those formatted characters rather than plain ASCII (such as straight quotes, etc.)

I am wondering if you have any suggestion on how to deal with this. 

Thank you. All told I'm totally enjoying Ubuntu 12.04 as my first foray into Linux. :)

Bob

---

### Post by iMurshaq on 2012-05-09
If you have a MS Office CD available, then you can install Office via Wine which is a program that will run many Windows programs on Linux. Good Luck.

---

### Post by funops on 2012-05-09
I do have the MS Office CD, as well as a few other Windows programs that can read the docs and do the plain ASCII conversion. I will give Wine a go. Thank you, and for the speedy reply.

---

### Post by lykwydchykyn on 2012-05-09
I usually have good luck with antiword, it's in the repositories.  Haven't tried it with "problem" documents that you describe, though.

---

### Post by funops on 2012-05-10
Success! Thought I'd report back. So I installed Wine (gosh that was easy), loaded two legacy Windows programs that I've used for this task and voila, all went perfect.

By way of workflow, I run the MS Word doc through 

catdoc -a >new.txt

Does a fine job albeit the typographical characters remain as previously noted. So I load new.txt into my Windows editor via Wine, use the editor's option to convert all to ASCII, which it does, and I have what I want (straight quotes, etc.)

I might be able to fine-tune that when I give it more thought but for now I easily have what I want and that's a keeper.

Thank you for your input,

Bob

---

### Post by Utkarsh Ray on 2012-05-10
There's a PERL script I had come across. It straightway replaces all Microsoft's unique characters by ASCII characters.
demoroniser.pl
It is at fourmilab.ch and also at cpan

---

### Post by funops on 2012-05-10
Oh cool, I'll give that script a try. Thanks!

Bob

---

