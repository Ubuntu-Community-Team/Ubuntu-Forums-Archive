---
title: "Properly using clisp."
date: 2007-12-31
forum: Programming Talk
---

### Post by YourSurrogateGod on 2007-12-31
For lack of a better forum to put this topic in, I decided on this one.

Now, some know that clisp allows me to write some lisp apps and that I can start it up from the console, for example:
```
ysg@ysger:~$ clisp
  i i i i i i i       ooooo    o        ooooooo   ooooo   ooooo
  I I I I I I I      8     8   8           8     8     o  8    8
  I  \ `+' /  I      8         8           8     8        8    8
   \  `-+-'  /       8         8           8      ooooo   8oooo
    `-__|__-'        8         8           8           8  8
        |            8     o   8           8     o     8  8
  ------+------       ooooo    8oooooo  ooo8ooo   ooooo   8

Copyright (c) Bruno Haible, Michael Stoll 1992, 1993
Copyright (c) Bruno Haible, Marcus Daniels 1994-1997
Copyright (c) Bruno Haible, Pierpaolo Bernardi, Sam Steingold 1998
Copyright (c) Bruno Haible, Sam Steingold 1999-2000
Copyright (c) Sam Steingold, Bruno Haible 2001-2006

[1]>
```
This is swell and all. However, I was wondering if someone has a list of commands that this interpreter uses (similar to the list of Linux commands in my sig, that would be great.) Anyone?

The key things that I would love to be able to do is save functions in specific files and run programs that were already written in a bunch of files (and it would be even better if I could compile them.) There are also debug features that I would like to take advantage of.

---

### Post by wolfbone on 2008-01-01
List of commands? If you're trying to use CLISP as a shell, read the CLISP documentation on that subject available at the CLISP website.

Other than that, it's probably best to use SLIME for CL development.

---

### Post by YourSurrogateGod on 2008-01-01
I was hoping to avoid using emacs and stick to gEdit instead for text-editing.

And do you mean the [implementation notes](http://clisp.cons.org/impnotes.html) as the documentation? I wasn't sure what it was when I looked on their website :oops: .

---

### Post by maximinus_uk on 2008-01-11
Bite the bullet, and learn Emacs + Slime. You need to have an editor that can indent the parentheses automatically, Really. The pain of trying to use GEdit to program LISP would really be too much.

Also, you might want to try Steel Bank Common Lisp instead of CLisp. It has better debug information, for a start.

On the other hand, I've been coding for about 25 years or so, and Emacs + Slime together is the best coding enviroment I've ever seen. It helps that LISP is a pretty cool language, as well.

---

### Post by YourSurrogateGod on 2008-01-11
> **maximinus_uk said:**
> Bite the bullet, and learn Emacs + Slime. You need to have an editor that can indent the parentheses automatically, Really. The pain of trying to use GEdit to program LISP would really be too much.

If you don't mind me asking, but why do you think that gedit is so unsuitable for the job? It does parentheses matching :) .

And generally I've stayed away from emacs if only because I can't open multiple files in tabs.

---

### Post by wolfbone on 2008-01-11
> **YourSurrogateGod said:**
> If you don't mind me asking, but why do you think that gedit is so unsuitable for the job? It does parentheses matching :) .

And generally I've stayed away from emacs if only because I can't open multiple files in tabs.

There is almost nothing you *cannot* do in Emacs and usually you'll find someone else has already made something to do it:

[http://www.emacswiki.org/cgi-bin/wiki/TabBarMode](http://www.emacswiki.org/cgi-bin/wiki/TabBarMode)

However, though you can always adapt Emacs to the way you want it to work, it's best to try to adapt to the Emacs way at first. (Viper mode is shipped with Emacs as a warning - not as something you should actually use ;-) )

I haven't used gedit but parentheses matching is not the same thing as automatic indentation and there is much more than that to Emacs + Slime [+ paredit mode] anyway.

---

### Post by YourSurrogateGod on 2008-01-11
> **wolfbone said:**
> There is almost nothing you *cannot* do in Emacs and usually you'll find someone else has already made something to do it:

[http://www.emacswiki.org/cgi-bin/wiki/TabBarMode](http://www.emacswiki.org/cgi-bin/wiki/TabBarMode)

However, though you can always adapt Emacs to the way you want it to work, it's best to try to adapt to the Emacs way at first. (Viper mode is shipped with Emacs as a warning - not as something you should actually use ;-) )

I haven't used gedit but parentheses matching is not the same thing as automatic indentation and there is much more than that to Emacs + Slime [+ paredit mode] anyway.

Yes, I realize that. Perhaps I didn't word my sentence very well.

---

