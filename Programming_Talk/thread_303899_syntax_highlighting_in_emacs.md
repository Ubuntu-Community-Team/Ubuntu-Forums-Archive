---
title: "syntax highlighting in emacs"
date: 2006-11-21
forum: Programming Talk
---

### Post by grado on 2006-11-21
How do I enable syntax highlighting on my freshly installed xemacs?

I followed instructions in [http://www.math.umn.edu/~aoleg/emacs/syntax.shtml](http://www.math.umn.edu/~aoleg/emacs/syntax.shtml)

but did not help.

I get the following error when I open a c++ file.
"File mode Specification error (void-variable allow-remote-paths)"

Is there some option, as in gvim, to select syntax highlighting "themes"?

Thanks!

my init.el and custom.el look as follows:
-----------------------------------------
init.el:
(setq font-lock-auto-fontify t)
(require 'font-lock) ; enable syntax highlighting

custom.el:
empty

---

### Post by Arndt on 2006-11-21
> **grado said:**
> How do I enable syntax highlighting on my freshly installed xemacs?

I followed instructions in [http://www.math.umn.edu/~aoleg/emacs/syntax.shtml](http://www.math.umn.edu/~aoleg/emacs/syntax.shtml)

but did not help.

I get the following error when I open a c++ file.
"File mode Specification error (void-variable allow-remote-paths)"

Is there some option, as in gvim, to select syntax highlighting "themes"?

Thanks!

my init.el and custom.el look as follows:
-----------------------------------------
init.el:
(setq font-lock-auto-fontify t)
(require 'font-lock) ; enable syntax highlighting

custom.el:
empty

Since no one else has anything to say: I don't use xemacs (only normal emacs) and don't know anything about C++ syntax highlighting, but I've tinkered a bit with elisp. Maybe giving the variable it complains about a value helps. Put

```
(setq allow-remote-paths nil)
```

in your .emacs file and restart xemacs and see what happens.

---

### Post by grado on 2006-11-22
Thanks. I tried that but didn't help. After going through xemacs faq's I realized that I dont have prog-modes package installed. Since, I wasn't sure which ones to download, I got the xemacs-sumo package and untarred it in the xemacs install_dir/lib/xemacs

Now, I get a new error:

File mode specification error: (error cannot open doc string file "/usr/local/lib/xemacs-21.4.9/lib-src/DOC")

As expected, the DOC file was not there. I dont understand what this error means. Somebody help!!! ](*,) 

I cant see anything in my code because of the missing colors.
I would be eternally gratified if somebody makes the syntax-highlighting work for me. (I usually use C/C++/Java/Perl. If it works for these I would the happiest man!)

---

### Post by wesper on 2006-11-23
Hi,

Check the installed packages, on my gentoo system I have a package called "xemacs-packages-sumo" which includes all the "edit modes". I guess there exist a similar package for Ubuntu.

  BR / Per-Erik

---

### Post by grado on 2006-11-23
thanks everyone! As always, the right solution is obtained by banging head against the keyboard.

I figured there was some trouble ( I dont know what) with xemacs version 21.4.9. I just knocked off all xemacs installation from my system and freshly installed 21.4.19 (notice the newer version) with the sumo tarballs. Everything's working now!

I still haven't figured how to get smooth (antialiased) fonts. Would really appreciate if someone sheds light on it.

Thanks!

---

### Post by avallark on 2009-04-16
> ;; Enable syntax highlighting

(global-font-lock-mode t)
(setq font-lock-maximum-decoration t)


Please try this. Worked for me. 

> Ref: [http://www.emacswiki.org/emacs/AvallarkDotEmacs](http://www.emacswiki.org/emacs/AvallarkDotEmacs)

---

### Post by johnl on 2009-04-16
> **grado said:**
> thanks everyone! As always, the right solution is obtained by banging head against the keyboard.

I figured there was some trouble ( I dont know what) with xemacs version 21.4.9. I just knocked off all xemacs installation from my system and freshly installed 21.4.19 (notice the newer version) with the sumo tarballs. Everything's working now!

I still haven't figured how to get smooth (antialiased) fonts. Would really appreciate if someone sheds light on it.

Thanks!

I am also not very familiar with Xemacs, but I build my own emacs 23 from CVS to include anti-aliased fonts, since I don't think that it is enabled in the stable 22.x builds.  You would probably have to do the same for xemacs or find a pre-built package.

---

