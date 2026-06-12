---
title: "LISP Question"
date: 2008-02-10
forum: Programming Talk
---

### Post by dstein on 2008-02-10
Hi, I am beginning to learn Common LISP. I will be using it for an Artificial Intelligence course. I downloaded clisp and cmucl, but I am not sure which one to use. Also, I will be using an ACL socket package called acl-socket. I believe that acl stands for Allegro Common LISP. Is there anyway to access this package without using Allagro. For example, how would I go about using ( in-package :acl-socket ) from clisp or cmucl, or even Emacs and Slime. Right now it doesn't work in any of them. Basically, how do I tell these programs to use Allegro packages? Thanks.

---

### Post by lnostdal on 2008-02-10
edit: by the way .. it is Common Lisp .. and/or just Lisp .. not LISP in any way or form

> **dstein said:**
> Hi, I am beginning to learn Common LISP. I will be using it for an Artificial Intelligence course. I downloaded clisp and cmucl, but I am not sure which one to use. 

ok, about clisp vs. cmucl .. replace cmucl with sbcl instead

..then we have either clisp or sbcl .. i'd go with sbcl in most cases because it is currently the most used implementation atm. -- i'm asuming you do also here


> Also, I will be using an ACL socket package called acl-socket. I believe that acl stands for Allegro Common LISP. 

yes

> 
Is there anyway to access this package without using Allagro. 

yes, there is a library (acl-compat is the name) that creates a wrapper around your implementations socket interface making it "look like" the socket interface Allegro has .. basically the library is a compatibility layer (hence the name acl-compat)

> 
For example, how would I go about using ( in-package :acl-socket ) from clisp or cmucl, or even Emacs and Slime.

right, you never use any lisp implementation "directly" in your terminal .. you will always use it via an interface like for instance emacs+slime

>  Basically, how do I tell these programs to use Allegro packages? Thanks.

here is what i do to download, install and use acl-compat:

i find acl-compat via the cl-user site: [http://www.cl-user.net/asp/libs/acl-compat](http://www.cl-user.net/asp/libs/acl-compat)

i download and extract it:

```

lars@ibmr52:~/programming/lisp$ wget http://constantly.at/lisp/acl-compat.tar.gz
...
lars@ibmr52:~/programming/lisp$ tar -xvzf acl-compat.tar.gz 
...

```

i find the .asd files and create symlinks to them so asdf can find them:

```

lars@ibmr52:~/programming/lisp$ ls acl-compat/*.asd
acl-compat/acl-compat.asd
lars@ibmr52:~/programming/lisp$ ln -s /home/lars/programming/lisp/acl-compat/acl-compat.asd /home/lars/.sbcl/systems/
lars@ibmr52:~/programming/lisp$ file ~/.sbcl/systems/acl-compat.asd 
/home/lars/.sbcl/systems/acl-compat.asd: symbolic link to `/home/lars/programming/lisp/acl-compat/acl-compat.asd'

```


i start emacs+slime (and thus sbcl ofc), and do:

```

(require :acl-compat)

```

i now have *acl-socket* available in SBCL .. :)

---

### Post by lnostdal on 2008-02-10
and here is an "hello world" using acl-compat under SBCL ... :)

```

(eval-when (:execute :load-toplevel :compile-toplevel)
  (require :acl-socket))


(defpackage :acl-socket-test
  (:use :cl :acl-socket))
(in-package :acl-socket-test)


(defun acl-test ()
  (let ((socket (make-socket :remote-host "nostdal.org"
                             :remote-port 80)))
    (write-line "GET / HTTP/1.0" socket)
    (terpri socket) (terpri socket)
    (finish-output socket)
    (loop
       (write-line (read-line socket))
       (finish-output))))

```

..trying it:
```

ACL-SOCKET-TEST> (acl-test)
HTTP/1.0 200 OK
Content-type: text/html
Date: Sun, 10 Feb 2008 23:00:57 GMT
Connection: close
Last-Modified: Sat, 01 Jan 2000 00:35:01 GMT
Content-length: 50

<html>
<body>
<h1>Hello World</h1>
</body>
</html>
; Evaluation aborted.
ACL-SOCKET-TEST> 

```

it interrupts with a condition *end of file on #<SB-SYS:FD-STREAM for "a socket" {C0BCF39}>* of course, but it is working

---

### Post by dstein on 2008-02-10
lnostdal, thank you so much for the thorough response. I have not had the chance to try your suggestions yet, but I would like to thank you for the detailed and quick reply. I hope to one day provide others with such knowledgeable responses. I'll reply if I have any further questions. Thanks again!

---

### Post by dstein on 2008-02-11
I have a few more LISP related questions. I installed SBCL and I do not have the ~/.sbcl directory, even when viewing hidden entries. When I load Slime in emacs, it says CMU Common Lisp, and I am unsure how to change it. Lastly, how come you "never use any lisp implementation "directly" in your terminal". Is it a bad idea to run sbcl from the terminal? I guess that I am really a newbie at LISP. If you have any suggested tutorial websites, that would be great. I actually just learned emacs yesterday, so I am truly a beginner. Thank you for the help though.

---

### Post by dstein on 2008-02-11
I forgot to mention that I found cl-acl-compat in the Ubuntu repositories. Would this suffice. However, I am unsure where it installs to.

---

### Post by lnostdal on 2008-02-11
ok, i'm not using ubuntu's package manager to install lisp software at the moment because i like to be able to use the newest possible versions of lisp implementations and libraries -- so i might not be able to help you with this exact problem

however if you do *sudo aptitude remove sbcl cmucl cl-acl-compat* i can guide you through how to install sbcl and acl-compat "manually"

i've put togheter a quck writing or guide here: [http://common-lisp.net/~lnostdal/writings/sbcl.html](http://common-lisp.net/~lnostdal/writings/sbcl.html)

..if you follow that you should get a setup similar to the one i use .. after that you should be able to follow what was mentioned in my post above to get *acl-compat* up and running 

at this point the writing was done in a hurry .. if you encounter any problems, just ask and i'll try to help .. if you want you can contact me on msn/jabber (see my signature) and we can work this out faster and i'll update the guide/writing as we go

---

### Post by lnostdal on 2008-02-11
> **dstein said:**
> Lastly, how come you "never use any lisp implementation "directly" in your terminal". Is it a bad idea to run sbcl from the terminal?

try it if you want .. it is very uncomfortable .. lisp is meant to be an interactive language *and* environment .. slime provides the environment part .. while sbcl provides the compiler or the language, if you will

there are other front-ends that support sbcl, but i haven never tried them and i do not remember their names at the moment

---

### Post by dstein on 2008-02-11
Thanks again. I started reading Practical Common Lisp, so for now I am using an integrated package of emacs, slime, and allegro, provided by the author (he calls it "Lisp in a box"). When I am a little more familiar with Common LISP, I am going to switch to my own version of Emacs, sbcl, slime, and the ACL wrapper used in the way you suggested.

---

### Post by lnostdal on 2008-02-11
great .. good luck .. PCL is a great book btw. .. chapter 4 and out is where the intresting stuff starts

i found chapter 3 a bit offputting i remember .. i was worried that he'd continue with that same style without explaining the smallish details etc. .. but stick with it and he'll come to it

---

### Post by dstein on 2008-03-08
Hi Inostdal, I believe that you may be able to help me with another Common Lisp question. So I am now using SBCL, as you suggested. I would like to use this Production System program called LISA, so I downloaded the lisa asd files and created a symbolic link in the manner you suggested. However, when I typed (require :lisa) I got a bunch of compilation errors I believe. I just kept pressing '0'. Now when I type (require :lisa), the REPL returns NIL. I would like to repeat the process to figure out what the errors were. Where did SBCL compile these files to? How can I start over. Thanks. Also, for other Common Lisp versions (such as cmucl or acl), where do they look for asd files? Would cmucl look in ~/.cmucl/systems?

---

### Post by lnostdal on 2008-03-08
hi there

```

lars@ibmr52:~$ cat ~/bin/rmfasl
#!/bin/bash
find -regex ".*fasl" | xargs rm -f

lars@ibmr52:~$ chmod +x ~/bin/rmfasl

```

when i run rmfasl it removes all the .fasl files in the current working directory and below it

hopefully the errors you saw was just messages about missing dependencies (needed lisp libraries) .. i haven't tried (compiling) LISA

edit:
by default the .fasl files are placed among the source files .. this can be changed ( [http://common-lisp.net/project/cl-containers/asdf-binary-locations/](http://common-lisp.net/project/cl-containers/asdf-binary-locations/) )

i don't know where other lisps look for .asd files .. you could have a common place for them and use symlinks if you want

---

### Post by dstein on 2008-03-08
Hi Inostdal, I actually have one more question. Do you know how to ignore pack lock errors in SBCL. I am trying to load an ASD and I keep getting Package lock errors. Thanks.

---

### Post by lnostdal on 2008-03-08
maybe  the condition restart:

```
1: [IGNORE-ALL] Ignore all package locks in the context of this operation.
```

..or..

```
2: [UNLOCK-PACKAGE] Unlock the package.
```

..will do.. but you can also turn off package locks "globally", if you want

..but well, there is a reason these package locks exist..

edit: i see you're cross-posting to comp.lang.lisp btw. ... it would be better if you just posted a link to the discussion there - then i'd answer there instead

---

### Post by dstein on 2008-03-09
Hi Inostdal. I see on your site and on your prior post that you suggest the creation of symlinks so that you can change versions of SBCL when necessary, "just by changing the symlink". How can symlinks be changed? Thanks again.

---

### Post by lnostdal on 2008-03-09
i just delete (rm sbcl) the symlink then create a new one pointing to a different sbcl-installation-directory

(maybe another method of "repointing" the symlink is possible? anyone?)

---

