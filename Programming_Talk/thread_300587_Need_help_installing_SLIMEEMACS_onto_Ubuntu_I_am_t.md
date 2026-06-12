---
title: "Need help installing SLIME/EMACS onto Ubuntu? I am trying to learn LISP."
date: 2006-11-15
forum: Programming Talk
---

### Post by ichben on 2006-11-15
Hello I am trying to learn a programing language called lisp. To do that I need to be able to run and operate a program called SLIME. How would I go about downloading and installing the program called SLIME 2.0 onto Ubuntu? Here is the website I am using to retreive the program ([http://common-lisp.net/project/slime/)](http://common-lisp.net/project/slime/)). I already have emacs downloaded and installed all I need is SLIME. Any help would be greatly appreciated.

Ichben Einberliner

---

### Post by po0f on 2006-11-15
ichben,

[Please don't double post](http://www.ubuntuforums.org/showthread.php?t=300585).  You didn't even give someone enough time to answer your first post.

[Did you try reading their docs](http://common-lisp.net/project/slime/doc/html/Installation.html#Installation)?

---

### Post by ichben on 2006-11-15
> **po0f said:**
> ichben,

[Please don't double post](http://www.ubuntuforums.org/showthread.php?t=300585).  You didn't even give someone enough time to answer your first post.

[Did you try reading their docs](http://common-lisp.net/project/slime/doc/html/Installation.html#Installation)?

Sorry about that Poof. I figured this question would be more appropiate in this section of the forum since it dealt with programing. Once again I apologize.

---

### Post by po0f on 2006-11-15
ichben,

I'm not trying to be mean, it's just netiquette.  Did the solution work for you?

---

### Post by hearnden on 2006-11-15
Is it an Emacs package?  If so, then I think all you need is to extract the package into somewhere like /usr/local/share/emacs/site-lisp.  Is there a README in the archive you downloaded?

---

### Post by ichben on 2006-11-16
I just want to let you all know that my problem has been solved. Thanks again for your help.

---

### Post by futileissue on 2007-10-28
I posted the correct paths for a standard Ubuntu Slime package installation here in my blog:

[http://akoumjian.blogspot.com/2007/10/clisp-in-emacs-using-slime-on-ubuntu.html](http://akoumjian.blogspot.com/2007/10/clisp-in-emacs-using-slime-on-ubuntu.html)

---

### Post by thearthur on 2007-10-31
sudo apt-get install slime

---

### Post by halizah on 2007-12-06
Hi,
  I've installed cmucl19a, emacs, and slime. It works well when I access cmucl19a and slime from emacs. Then I install different version of cmucl19b, change the path to run cmucl19b in .emacs. But when I access slime from emacs, the following errors issued:

(progn (load "/usr/share/common-lisp/source/slime/swank-loader.lisp" :verbose t) (funcall (read-from-string "swank:start-server") "/tmp/slime.8847" :coding-system "iso-latin-1-unix"))

CMU Common Lisp 19b (19B), running on ***********
With core: /home/******/cmucl19b/lib/cmucl/lib/lisp.core
Dumped on: Tue, 2005-06-28 12:09:58+12:00 on lorien
See <http://www.cons.org/cmucl/> for support information.
Loaded subsystems:
    Python 1.1, target Intel x86
    CLOS based on Gerd's PCL 2004/04/14 03:32:47
* 
; Loading #P"/usr/share/common-lisp/source/slime/swank-loader.lisp".

Reader error at 5382 on #<Stream for file "/usr/share/common-lisp/source/slime/swank-loader.lisp">:
package "CLC" not found
   [Condition of type LISP::READER-PACKAGE-ERROR]

Restarts:
  0: [CONTINUE] Return NIL from load of "/usr/share/common-lisp/source/slime/swank-loader.lisp".
  1: [ABORT   ] Return to Top-Level.

Debug  (type H for help)

(LISP::READ-TOKEN
 #<Stream for file "/usr/share/common-lisp/source/slime/swank-loader.lisp">
 #\c)
Source: Error finding source: 
Error in function DEBUG::GET-FILE-TOP-LEVEL-FORM:  Source file no longer exists:
  target:code/reader.lisp.
0] 

Please help!

---

### Post by tchotchke on 2007-12-11
Hi, i cannot seem to find slime on synaptic,Those of you who have installed slime, how did you do it?

thanks

---

### Post by [h2o] on 2007-12-12
> **tchotchke said:**
> Hi, i cannot seem to find slime on synaptic,Those of you who have installed slime, how did you do it?

thanks
Make sure you have the universe and multiverse repositories checked in the repositories menu.
The package name is "slime" (Ubuntu 7.10).

---

### Post by GSBoomer on 2008-05-05
OK, I need some help. I did a clean install of Hardy and now I can't get my Emacs/Lisp/Slime setup correct.

I installed Emacs-22, slime, sbcl, asdf, and a bunch of pacakges using synaptic. I put:

```

(setq inferior-lisp-program "/usr/bin/sbcl")
(add-to-list 'load-path "/usr/share/common-lisp/source/slime/")
(require 'slime)
(slime setup)

```

in my .emacs.

Slime starts fine. If I try this:

```

(defpackage :mystuff
   (:use :cl :cl-who))

```

I get this despite having installed cl-who:

```

Backtrace:
  0: (SB-INT:%FIND-PACKAGE-OR-LOSE "CL-WHO")
  1: (SB-INT:FIND-UNDELETED-PACKAGE-OR-LOSE "CL-WHO")
  2: (SB-IMPL::%DEFPACKAGE
      "MYSTUFF"
      NIL
      NIL
      NIL
      NIL
      #<unavailable argument>
      NIL
      NIL
      NIL ..)
  3: (SB-INT:SIMPLE-EVAL-IN-LEXENV
      (SB-IMPL::%DEFPACKAGE "MYSTUFF" 'NIL 'NIL 'NIL 'NIL '("CL" "CL-WHO")
                            'NIL 'NIL 'NIL ...)
      #<NULL-LEXENV>)
  4: (SB-INT:SIMPLE-EVAL-IN-LEXENV
      (DEFPACKAGE :MYSTUFF (:USE :CL :CL-WHO))
      #<NULL-LEXENV>)

```

Help! I need my setup back so I can continue to learn lisp!

I thought the whole purpose of (defpackage ...) was to NOT have to input (require 'cl-who) and the like. Using require solves the problem temporarily.

---

### Post by maximinus_uk on 2008-05-17
I get the same thing as well. It's not like you can't work around it but I would essentially say that the SLIME install via synaptic is broken - the last thing a user wants to see is an error message when they run the software.

---

### Post by skalter on 2008-10-07
I've found that the synaptic package for slime does not work well with sbcl under hardy (I was getting the cannot load swank-loader.lisp error).  It was much simpler to fetch the latest tarball from [http://common-lisp.net/project/slime/](http://common-lisp.net/project/slime/) 

Unpack this and specify the new location in your .emacs slime configuration.

Good luck,

-sdk

---

### Post by GSBoomer on 2008-10-07
I'm running Hardy and managed to botch my lisp installation by loading a few packages via synaptic AND via asdf-install; big mistake. So, this past weekend I uninstalled all synaptic packages and completely deleted my entire lisp install. 

My strategy now is to install everything through synaptic and only use asdf-install for packages that are either local or not in the Ubuntu repositories.

So far everything works fine, including emacs, slime, slime-connect, and swank.

---

