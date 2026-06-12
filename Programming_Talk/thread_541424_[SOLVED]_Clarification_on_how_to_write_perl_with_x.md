---
title: "[SOLVED] Clarification on how to write perl with xemacs"
date: 2007-09-02
forum: Programming Talk
---

### Post by eph1973 on 2007-09-02
I am currently trying to learn Perl, and would like to use xemacs to write the programs.
I've used xemacs to write C, and since it defaults with all the GNU style indentations and all that, I've never had to play with the init.el file.  At the moment I have virtually no knowledge of Lisp, but would like xemacs to behave with Perl, as far as indentation goes, like it does with C (shorter tabs, automatically tabbing things where they should be based on scope, etc).  I've done some searching on the Internet through Google, and I've seen that there's a mode called cperl-mode, but I am unclear how to make xemacs enter this mode.  I've also seen that there's lots of init.el files out there, but I really just want it to enter the cperl-mode without having to learn Lisp (which I will probably learn at a later time, but for now, I have the books to learn Perl, so I would like to try that first).
I saw something about (add-hook 'cperl-mode-hook) or something like that, but is there a control or meta key combination that puts you into cperl mode?  Any clarification to this end would be appreciated.

---

### Post by jpkotta on 2007-09-03
```
M-x  cperl-mode
```
I never had a problem with it not recognizing a Perl file (as long as it ended in ".pl", ".pm", etc).  You could add a pattern to auto-mode-alist for a specific directory or file extension as well.

```

(setq auto-mode-alist
       (cons '(".pl" . cperl-mode)
      auto-mode-alist))))
```

Personally, I like the BSD indent style better than GNU.  So I have the following in my init.el:

```
(add-hook 'cperl-mode-hook
	  (lambda ()
	    (cperl-set-style "BSD")
	    )
	  )
```

I could never figure out how to make the indent style setting persistent otherwise.

cperl-mode-hook is a function that gets run everytime you enter CPerl mode.  Just about every major mode has such a hook function.

---

### Post by jpkotta on 2007-09-03
As for learning Perl, I have some advice:

[http://www.ebb.org/PickingUpPerl/](http://www.ebb.org/PickingUpPerl/)
[http://www.rexswain.com/perl5.html](http://www.rexswain.com/perl5.html)

And I've found it very valuable to use the perl debugger to interactively run code to see what it does.

```
perl -e 0 -d
```

Then to run a line of code, prefix it with an 'x', like so:
```
x print "hello\n";
```

You will want some packages to make using the debugger bearable:
```
sudo aptitude install libterm-readkey-perl libterm-readline-perl-perl
```

(X)Emacs has a GUD (grand unified debugger) mode that can use the perl debugger and jump around in your source too.

---

### Post by eph1973 on 2007-09-03
When I hit M-x cperl-mode I get a message about cannot find load file: cus-face...but there is a cus-face.elc in /usr/share/xemacs-21.4.19/lisp.  I am not sure what directory xemacs is looking for it in, or else I'd probably put a copy there.  Really, my big beef with xemacs with a non C file, is the 8 space tabs, which, in my opinion, makes code a lot harder to read.

I guess I'll use vi to make my Perl files, as this is starting to consume way too much of my time at the moment.  Thank you very much for your response, it was exactly what I was looking for.  I installed the two libterm files you mentioned, and thanks for the resources, I'll check them out.

---

### Post by jpkotta on 2007-09-03
> **eph1973 said:**
> When I hit M-x cperl-mode I get a message about cannot find load file: cus-face...but there is a cus-face.elc in /usr/share/xemacs-21.4.19/lisp.  I am not sure what directory xemacs is looking for it in, or else I'd probably put a copy there.  

Weird.  Try adding that to the path:
```
(pushnew (expand-file-name "/usr/share/xemacs-21.4.19/lisp") load-path :test 'equal)
```

But it should really work out of the box.  Maybe reinstall XEmacs?  

> **eph1973 said:**
> Really, my big beef with xemacs with a non C file, is the 8 space tabs, which, in my opinion, makes code a lot harder to read.

Agreed.  But this can be set globally (Variable: tab-width).  See [http://www.emacswiki.org/cgi-bin/wiki/TabsAreEvil](http://www.emacswiki.org/cgi-bin/wiki/TabsAreEvil).

> **eph1973 said:**
> I guess I'll use vi to make my Perl files, as this is starting to consume way too much of my time at the moment.  Thank you very much for your response, it was exactly what I was looking for.  I installed the two libterm files you mentioned, and thanks for the resources, I'll check them out.

Vi is the dark side!  I used to use Nedit before I got into Emacs.  It's easy to use and has very nice syntax highlighting, but not all of the magic indent stuff that Emacs (and presumably Vi) have.

---

### Post by eph1973 on 2007-09-03
> **jpkotta said:**
> But it should really work out of the box.  Maybe reinstall XEmacs?  
w00t!
Apparently that was my problem, I went in and removed emacs and xemacs, and reinstalled them, now all works perfectly!  Thank you very much, and the TabsAreEvil link was quite interesting, gave me some food for thought.  I saw some pretty interesting init.el files on the web while I was googling around for a solution, maybe now they will work properly.

---

