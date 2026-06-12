---
title: "Problem beginning with clisp, requiring packages"
date: 2009-02-17
forum: Programming Talk
---

### Post by Belerophon on 2009-02-17
Hi.

I'm having problems requiring packages in clisp. This is my very first approach to lisp!

I'm following an example of sockets in lisp:
[http://cl-cookbook.sourceforge.net/sockets.html](http://cl-cookbook.sourceforge.net/sockets.html)

So I copied the in the "Complete Example" section to two files, client and server and tried do open clisp, and load the server. I was faced with a problem right there: it could not find the "port" package. I googled it and found:
```
(in-package :port)
```
this should be replaced by:
```
(clc:clc-require :port)
```

But now I get some error about locked file or something
```
[1]> (load "socket_example_server.lsp")
;; Loading file socket_example_server.lsp ...
;;  Loading file /usr/share/common-lisp/systems/port.asd ...
;;  Loaded file /usr/share/common-lisp/systems/port.asd
;;  Loading file /var/cache/common-lisp-controller/1000/clisp/cl-port/ext.fas ...
;;  Loaded file /var/cache/common-lisp-controller/1000/clisp/cl-port/ext.fas
;;  Loading file /var/cache/common-lisp-controller/1000/clisp/cl-port/gray.fas ...
;;  Loaded file /var/cache/common-lisp-controller/1000/clisp/cl-port/gray.fas
;;  Loading file /var/cache/common-lisp-controller/1000/clisp/cl-port/path.fas ...
;;  Loaded file /var/cache/common-lisp-controller/1000/clisp/cl-port/path.fas
;;  Loading file /var/cache/common-lisp-controller/1000/clisp/cl-port/sys.fas ...
** - Continuable Error
INTERN("STRUCTURE-KCONSTRUCTOR"): #<PACKAGE SYSTEM> is locked
If you continue (by typing 'continue'): Ignore the lock and proceed
The following restarts are also available:
RETRY          :R1      
Retry performing #<ASDF:LOAD-OP NIL #x205053D6> on #<ASDF:CL-SOURCE-FILE "sys"
  #x204E6BF6>.
ACCEPT         :R2      
Continue, treating #<ASDF:LOAD-OP NIL #x205053D6> on #<ASDF:CL-SOURCE-FILE
  "sys" #x204E6BF6> as having been successful.
SKIP           :R3      skip (CLC-REQUIRE PORT)
STOP           :R4      stop loading file /home/belerophon/Desktop/PPRO/socket_example_server.lsp
ABORT          :R5      Abort main loop

```

So, can anyone help me here?

---

