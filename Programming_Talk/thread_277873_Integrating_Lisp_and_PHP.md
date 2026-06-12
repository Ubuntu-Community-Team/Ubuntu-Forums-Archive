---
title: "Integrating Lisp and PHP?"
date: 2006-10-15
forum: Programming Talk
---

### Post by bieber on 2006-10-15
Okay, I've currently got a web server running on my computer with Apache and PHP5.  I've been getting into Lisp recently, and considered trying to get set up with mod-lisp and such, only to find that it's a massive pain to try actually setting up a server to use LISP.  So, is there some easy way I could integrate it with PHP?  Maybe passing data for processing to a seperate Lisp program, or even implementing Lisp in PHP?  I'm thinking the latter would be particularly interesting, but I've never tried to make an implementation of a programming language before; how difficult would it be?

---

### Post by slavik on 2006-10-16
you can make the php script execute the lisp code and then print the results

EDIT: I think.

---

### Post by lnostdal on 2006-11-29
If you want to go the PHP<->Lisp route the easyest thing to do would be to make PHP communicate with your Lisp-process using sockets.

  [http://php.net/manual/en/ref.sockets.php](http://php.net/manual/en/ref.sockets.php)
  [http://www.sbcl.org/manual/Networking.html](http://www.sbcl.org/manual/Networking.html) (my Lisp of coice)

It is an interesting way to do it; and it might be easier/better than mod_lisp in some ways because it means that other programmers can use your code and you can use their code.

If you want to go the mod_lisp route:
  [http://www.blaino.com/guide/modlisp-pcl-guide.html](http://www.blaino.com/guide/modlisp-pcl-guide.html)

There is a typo in that post by the way:
  "apxs2 -i -c /mod_lisp/mod_lisp2.c"

..should be..

  "apxs2 -i -c mod_lisp/mod_lisp2.c"


Lemme know if you need any help with any of this. :)

---

