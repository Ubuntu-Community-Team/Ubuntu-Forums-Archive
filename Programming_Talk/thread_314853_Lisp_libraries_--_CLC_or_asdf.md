---
title: "Lisp libraries -- CLC or asdf"
date: 2006-12-08
forum: Programming Talk
---

### Post by rickardg on 2006-12-08
I'd just like to pick your brains on what to use for lisp library management on Edgy.

Common-lisp-controller seems nice in theory, but I've heard that there used to be some issues with it, not sure if things are better now. A completely unsystematic check of the repositories also gives the impression that the packages are a bit old (e g cl-cffi is version 0.0.20051028-1) and that some stuff (like gtk bindings) are missing.

I'd like to just use the packages with clc and be done with it, but perhaps one is better off using asdf-install or even plain old asdf?

PS On a slightly related note: I tried to uninstall slime with ```
sudo apt-get remove slime
``` to use a slime in my $HOME, but apt didn't remove the slime references from the site-start.d emacs config files. Is that intended behaviour or a bug?

---

### Post by lnostdal on 2006-12-08
> **rickardg said:**
> 
I'd like to just use the packages with clc and be done with it, but perhaps one is better off using asdf-install or even plain old asdf?


I install both SBCL, Slime and Lisp-libraries in my home-folder "manually" because I've found this to be easier and more flexible to maintain anyways. This might sound clumsy but it works ok. :)

If I want to stay at a certain version/branch of something I use `cvs -up -r sbcl_1_0' for instance, and copy the result to a new directory and symlink to it.

Most Lisp-libraries are stored in a SCM-system like CVS, SVN or Darcs. Just check out the code and add a symlink from ~/.sbcl/systems/ to the .asd-file in the code-tree. This enables `asdf' to find your Lisp-libraries. If the directory ~/.sbcl/systems/ does not exist - just create it. After this you will be able to type `(require :some-lib)' in the REPL and have it compiled & loaded. It might complain about missing dependencies though, and you'll have to fix this as they happen - or take a peek in the .asd-files for `:depends-on' entries.

If you need "first hand" help with any of this I'm almost always to be found at the IRC-channel #programmering at freenode. :)

---

### Post by rickardg on 2006-12-08
Thanks for your quick reply!

> **lnostdal said:**
> I install both SBCL, Slime and Lisp-libraries in my home-folder "manually" because I've found this to be easier and more flexible to maintain anyways. This might sound clumsy but it works ok. :) 

I figured that would be the way to do it, particularly since I've already had one unpleasant experience with clc. Some of the libraries are under quite heavy development, so I'd probably just use the cvs version sooner or later anyway.  

> **lnostdal said:**
> After this you will be able to type `(require :some-lib)' in the REPL and have it compiled & loaded.
 This trick only work on sbcl, right? (Not, that (asdf: operate <...> ) would be a problem...) 

I haven't quite decided between sbcl and clisp, or even one of the commercial implementations yet, MacOS and, unfortunately, w32 are still in the picture, even as development systems.
> **lnostdal said:**
>  If you need "first hand" help with any of this I'm almost always to be found at the IRC-channel #programmering at freenode. :)

Cool, I'll see you there, and I've got a few other issues I'd like opinions on, if you don't mind... :-)

---

### Post by lnostdal on 2006-12-08
> **rickardg said:**
> Thanks for your quick reply!

 This trick only work on sbcl, right? (Not, that (asdf: operate <...> ) would be a problem...) 


Yes, 
```
(asdf:operate 'asdf:load-op 'foo)
```
...is the "portable" way to load a library.
[http://constantly.at/lisp/asdf/Using-asdf-to-load-systems.html#Using%20asdf%20to%20load%20systems](http://constantly.at/lisp/asdf/Using-asdf-to-load-systems.html#Using%20asdf%20to%20load%20systems)

But you can just do:

```

(defpackage :my-cl
  (:use cl)
  (:shadow :require))
(in-package :my-cl)

(defun require (lib-spec)
  asdf:operate 'asdf:load-op 'foo))
(export 'require)

```

Or something like that. Then use the library `my-cl' instead of `cl' when you create new packages. 


> **rickardg said:**
> 
I haven't quite decided between sbcl and clisp, or even one of the commercial implementations yet, MacOS and, unfortunately, w32 are still in the picture, even as development systems.


I think SBCL is supported under Mac also. [http://sbcl.sourceforge.net/platform-table.html](http://sbcl.sourceforge.net/platform-table.html) mentions "Darwin (Mac OS X)" as supported under x86 and PowerPC processors. There might be some issues with thread-support however; the manual states it as experimental under "Darwin (Mac OS X)": [http://www.sbcl.org/manual/Threading.html](http://www.sbcl.org/manual/Threading.html)

Win32 is still alphaish; but by the time you have your killer-app ready - SBCL will also be ready. :)

I know very little about CLISP; I've only used it for quick scripting/shell-tasks. It's portable, has a quick startup-time but lacks a native compiler and threading.


> **rickardg said:**
> 
Cool, I'll see you there, and I've got a few other issues I'd like opinions on, if you don't mind... :-)

Sure, no probs :)

---

