---
title: "Problems with Lisp/SLIME in Feisty"
date: 2007-04-24
forum: Programming Talk
---

### Post by erikcw on 2007-04-24
Hi all,

I'm trying to get cmucl + slime working under Feisty (worked great in Edgy).  I have everything installed, but it's not working correctly.

Under Edgy I had:
-Auto Indenting
-A SLIME drop down menu in Xemacs.
-A split frame would open for errors/debugging.
-A nice prompt to work from.

None of the above work with Feisty, I just have a 


My Emacs frame looks just like the one in this post:
[http://ubuntuforums.org/showthread.php?t=345468&highlight=slime](http://ubuntuforums.org/showthread.php?t=345468&highlight=slime)
(The Feisty dev forum was closed before he got a response)

> 
(load "/usr/share/common-lisp/source/slime/swank-loader.lisp" :verbose t)
(swank:start-server "/tmp/erik/slime.5652" :external-format :iso-latin-1-unix)

CMU Common Lisp CVS release-19a 19a-release-20040728 + minimal debian patches, running on turbo
With core: /usr/lib/cmucl/lisp.core
Dumped on: Mon, 2007-04-23 11:45:31-04:00 on turbo
For support see [http://www.cons.org/cmucl/support.html](http://www.cons.org/cmucl/support.html) Send bug reports to the debian BTS.
or to [email]pvaneynd@debian.org[/email]
type (help) for help, (quit) to exit, and (demo) to see the demos

Loaded subsystems:
    Python 1.1, target Intel x86
    CLOS based on Gerd's PCL 2004/04/14 03:32:47
* 
; Loading #p"/usr/share/common-lisp/source/slime/swank-loader.lisp".
;; Loading #p"/var/cache/common-lisp-controller/1000/cmucl/swank/fasl/cmu-cvs_release-19a_19a-release-20040728_+_minimal_debian_patches-linux-x86/swank-backend.x86f".
;; Loading #p"/var/cache/common-lisp-controller/1000/cmucl/swank/fasl/cmu-cvs_release-19a_19a-release-20040728_+_minimal_debian_patches-linux-x86/nregex.x86f".
;; Loading #p"/var/cache/common-lisp-controller/1000/cmucl/swank/fasl/cmu-cvs_release-19a_19a-release-20040728_+_minimal_debian_patches-linux-x86/swank-source-path-parser.x86f".
;; Loading #p"/var/cache/common-lisp-controller/1000/cmucl/swank/fasl/cmu-cvs_release-19a_19a-release-20040728_+_minimal_debian_patches-linux-x86/swank-source-file-cache.x86f".
;; Loading #p"/var/cache/common-lisp-controller/1000/cmucl/swank/fasl/cmu-cvs_release-19a_19a-release-20040728_+_minimal_debian_patches-linux-x86/swank-cmucl.x86f".
;; Loading #p"/var/cache/common-lisp-controller/1000/cmucl/swank/fasl/cmu-cvs_release-19a_19a-release-20040728_+_minimal_debian_patches-linux-x86/swank.x86f".
Warning:  These Swank interfaces are unimplemented:
 (CALLS-WHO RESTART-FRAME SLDB-STEP-INTO SLDB-STEP-NEXT SLDB-STEP-OUT)
T
* 
Unknown keyword: :EXTERNAL-FORMAT
   [Condition of type KERNEL:SIMPLE-PROGRAM-ERROR]

Restarts:
  0: [ABORT] Return to Top-Level.

Debug  (type H for help)

("DEFUN START-SERVER" "/tmp/erik/slime.5652" 268432262 2)[:OPTIONAL]
Source: 
; File: /usr/share/common-lisp/source/slime/swank.lisp
(DEFUN START-SERVER
       (PORT-FILE
        &KEY (STYLE *COMMUNICATION-STYLE*) (DONT-CLOSE *DONT-CLOSE*)
        (CODING-SYSTEM *CODING-SYSTEM*))
  "Start the server and write the listen port number to PORT-FILE.
This is the entry point for Emacs."
  (FLET (#)
    (IF # # #)))
0] 


Thanks for your help!

---

