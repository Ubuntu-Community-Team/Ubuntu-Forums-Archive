---
title: "[SOLVED] php-java extension"
date: 2008-07-04
forum: Programming Talk
---

### Post by koba101 on 2008-07-04
Hi,

Can anyone help me configure php to read java methods on ubuntu...I used to be able to do it on windows; but i'm having a problem here

---

### Post by henchman on 2008-07-04
well, could you please specify your problem a bit more? Iam sure someone will be able to help you :)

---

### Post by jamesstansell on 2008-07-04
Please tell us more about what you've tried so far.

---

### Post by koba101 on 2008-07-05
ok...i've got php installed and it's up and running.

I've got the JDK installed as well (even if i have a problem selecting the 1.6 version as the default, but that's a different story)

now i'm stuckenabling the php-java extension.  I was able to do it on widnows because it only needed a few steps.  (uncomment the extension assignment in the php.ini file, list the appropriate paths in the .ini and that's it.

Here, first of all i don't see any php_java extension....nor do i see the php_java.jar file in the JDK (i'm not sure if it's supposed to be there, nor do i see any commented statements applicable to a jave extension.)  i've read somewhere that i could do something like say ./configure -with-java=[java-path], but i don't know where the configure file is to run it

nor does phpize work 


that's how lost i am

---

### Post by jamesstansell on 2008-07-05
The ./configure command is typically part of a project's source code.  I don't know for sure but my guess is that the ubuntu php package was configured --without-java when it was built.  Which means you would need to build it yourself but with the configuration you want.  Or perhaps find a copy that someone else has built the way you need.  Once again, I'm just guessing here.

---

### Post by koba101 on 2008-07-05
i think i'll install everything from scracth...problem is i don't even know where the php files are (in windows they're just at c:/php)

i'll keep you posted

---

### Post by koba101 on 2008-07-05
The link below was excellent

[http://blogs.vinuthomas.com/2007/11/22/installing-the-php-java-bridge-in-ubuntu-gutsy-gibbon/](http://blogs.vinuthomas.com/2007/11/22/installing-the-php-java-bridge-in-ubuntu-gutsy-gibbon/)

Though I regret to say I don't know exactly what it did..but it worked

---

### Post by jamesstansell on 2008-07-05
That's great to know.

This php/java bridge seems a little more advanced than the one I read about years ago (and that one sounded good.)

---

