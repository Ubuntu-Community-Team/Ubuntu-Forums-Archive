---
title: "Utility to compare two text files for changes?"
date: 2008-01-17
forum: Programming Talk
---

### Post by agibby5 on 2008-01-17
I was wondering if there was a utility to compare two text files and show the differences line by line?  This would be helpful for comparing changes in code from one version to another (like if someone emails me their changes, I'd like to see what they changed).

Let me know.
Thanks.

---

### Post by prkfriryce on 2008-01-17
```
$ diff filename1 filename2
```

---

### Post by DrMega on 2008-01-17
xdiff is good. It's in Synaptic.

---

### Post by ablegreen on 2008-01-17
WinMerge

[http://sourceforge.net/projects/winmerge/](http://sourceforge.net/projects/winmerge/)

---

### Post by geirha on 2008-01-17
> **prkfriryce said:**
> ```
$ diff filename1 filename2
```

Diff is the best tool I know of, but I prefer to use the -u option for better readabilty
```
diff -u file1 file2
```

---

### Post by engla on 2008-01-17
**meld** is a nice graphical display equivalent to diff (for gtk/gnome). For KDE there is a tool called something like "kdediff" that should do the same job there (search for it).

---

### Post by agibby5 on 2008-01-17
> **engla said:**
> **meld** is a nice graphical display equivalent to diff (for gtk/gnome). For KDE there is a tool called something like "kdediff" that should do the same job there (search for it).

Thats exactly what I was looking for... thanks a bunch!

---

### Post by AnRkey on 2008-07-24
> **engla said:**
> **meld** is a nice graphical display equivalent to diff (for gtk/gnome). For KDE there is a tool called something like "kdediff" that should do the same job there (search for it).

Shweet, thanks

---

### Post by The Cog on 2008-07-25
+1 for **meld**. 
It deserves more publicity than it seems to get.

---

### Post by dhwani on 2009-04-25
These folks who make these tools and make them available for all to use ...
are nothing but GOD to me ... 

AMEN ... and cheers.

---

### Post by babyfoxx on 2009-05-23
Meld is awesome!! It is better than Winmerge, IMHO.\\:D/

---

### Post by AnRkey on 2009-05-23
I have almost finished rolling out Ubuntu 8.04 to about 90+ pc's at a large company in my area. It's a large company with VPN via ADSL for it's WAN links between it's many branches.

We had loads of problems with printing during the testing phase. They use an old AS400 server and LPD/LPR queues for print jobs.

Anyhoo, I needed to trouble shoot some pretty hairy problems and Meld came through for me big time when it came to comparing outputted files.

So thumbs up for Meld from my side!

From the CLI it's still Diff or a super Cat and Grep combo.

R

---

### Post by sitthykun on 2010-05-12
Meld is very great. I like it

Thanks

 .... :)

---

### Post by mrkazoodle on 2010-06-28
another happy meld user :p

---

### Post by victor9098 on 2010-12-12
MELD is fantastic, having to convert everything to a text file is the only messy bit, but what a tool. Wish I had been turned onto this years ago. :)

---

### Post by tagnu on 2010-12-27
meld is fantastic :)

---

### Post by Liudwik on 2011-04-08
Great tool!!!

---

### Post by okaiji on 2011-04-09
> **tagnu said:**
> meld is fantastic :)

Using it now. to compare between two files of different editions...
docx and a later doc which is the same version of uploaded onto the server by the authoring user.

Just wondering why it wasn't found in the dash in unity?
Filed under office, or accessories... meld diff viewer:p

---

### Post by mrspronky on 2011-07-15
+1 for meld :D

---

### Post by bzd454 on 2011-11-22
Yeah, Meld is excellent.  i think i was using Notepad++ with some plugin on the windows side but Meld is much better.

---

### Post by COKEDUDE on 2012-03-17
Have any of you tried diffuse or kdiff3?

---

