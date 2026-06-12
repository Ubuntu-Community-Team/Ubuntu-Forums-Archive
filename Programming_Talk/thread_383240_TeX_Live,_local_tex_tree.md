---
title: "TeX Live, local tex tree"
date: 2007-03-13
forum: Programming Talk
---

### Post by Timtro on 2007-03-13
Hi All,

I was wondering if anyone could tell me how I can tell TeX Live that I want to have my own local tex tree, so that I don't modify the main tex tree in /etc.

For example, I want to have a directory called 'localtexmf' in my home, and I want this to be hashed so that all of my custom files are seen for me. This is default behavior of MiKTeX, which creates localtexmf.

Thanks!

---

### Post by Timtro on 2007-03-13
* bump *

---

### Post by rplantz on 2007-03-13
I'm still using tetex since it's the distro still "supported" by Ubuntu. (I use the quotes here because tetex is no longer supported, so ubuntu will eventually need to change to TeX Live.)

In tetex there is a file, README.Debian that describes where the various directories are. I had to use this in combination with TETEXDOC.pdf to figure out where to put things on my system.

I would like to migrate to TeX Live, so I'm curious to hear anything you learn about this.

---

### Post by Timtro on 2007-03-18
*bump*

I still haven't figured it out. I did a locate for README.Debian, and came up with MANY results.

If someone could point me to documentation, I would by happy.

Thanks!

---

### Post by jss43 on 2007-03-19
I don't use TeX Live, but that won't stop me having a stab in the dark (or at least, say what I did for a similar problem).

You need to rebuild TeX's filename database (ls-R): you can do this by running  

#texhash [directories]

(the man page is particularly unhelpful here!).  texhash might also be called mktexlsr.  

By default, TeX in Linux looks for texmf trees in /usr/share/texmf/, /usr/local/share/texmf/ and ~/texmf/, so you might want to try renaming ~/localtexmf/ to ~/texmf/ (my local texmf bumpf is at ~/texmf/), or run 

#texhash ~/localtexmf

The TeXLive documentation implies you can also do this by using the Manage the Installation tab (under windows, at least).

Hope this helps,

    --James

---

### Post by Timtro on 2007-03-19
> **jss43 said:**
> I don't use TeX Live, but that won't stop me having a stab in the dark (or at least, say what I did for a similar problem).

You need to rebuild TeX's filename database (ls-R): you can do this by running  

#texhash [directories]

(the man page is particularly unhelpful here!).  texhash might also be called mktexlsr.  

By default, TeX in Linux looks for texmf trees in /usr/share/texmf/, /usr/local/share/texmf/ and ~/texmf/, so you might want to try renaming ~/localtexmf/ to ~/texmf/ (my local texmf bumpf is at ~/texmf/), or run 

#texhash ~/localtexmf

The TeXLive documentation implies you can also do this by using the Manage the Installation tab (under windows, at least).

Hope this helps,

    --James

Thanks James :) The irony is that I figured this out on my own about an hour ago! :P

Actually, I figured out that texhas looks in $HOME/texmf. I found this out from

texconfig conf 

If it reads out too much, can pipe to more (texconfig conf | more).

Thanks all!

---

