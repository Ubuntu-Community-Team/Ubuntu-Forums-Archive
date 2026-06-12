---
title: "Perl: problem building a cpan module"
date: 2008-03-24
forum: Programming Talk
---

### Post by bs0d on 2008-03-24
Hello

I am trying to install a module from CPAN 
[http://search.cpan.org/~richdawe/File-ExtAttr-1.07/](http://search.cpan.org/~richdawe/File-ExtAttr-1.07/)
but if I run 
>cpan install File::ExtAttr I got error:

 failed: Operation not supported - perhaps the extended attribute's name needs a "user." prefix? at /home/user/.cpan/build/File-ExtAttr-1.07/blib/lib/File/ExtAttr.pm line 266

I can build with force install but then if I run the test script I get this error again.

any ideas?

---

### Post by slavik on 2008-03-24
does this module exist in the repository?

---

### Post by bs0d on 2008-03-24
> **slavik said:**
> does this module exist in the repository?

yes, but compiling stops because of testing errors.

try in console:

$cpan
>install File::ExtAttr

---

### Post by unutbu on 2008-04-23
Did you run cpan *before* installing the build-essential package? According to
jerovich this can cause cpan to fail even after you install build-essential.

See [http://ubuntuforums.org/showthread.php?t=240923&page=2](http://ubuntuforums.org/showthread.php?t=240923&page=2)

---

