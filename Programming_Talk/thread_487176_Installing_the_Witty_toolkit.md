---
title: "Installing the Witty toolkit????"
date: 2007-06-28
forum: Programming Talk
---

### Post by ewtesterman@cox.net on 2007-06-28
I have found this toolkit called [witty]("http://www.webtoolkit.eu/wt/"). I have followed the wiki for installing it in Ubuntu/Debian as best I could. The good news is its almost there the bad news is I have no idea how to resolve the final dependencies and environmental variables. I think this toolkit has a lot of potential seeing how it allows one to make an ajax interface by compiling c++. Anyway any help here would be great.
```

eric@eric-laptop:~/wt-2.0.1/build$ sudo cmake ../
** Disabling FastCGI.
** Enabling built-in httpd.
-- ** Serverpush example needs boost with thread support... Skipping.
-- ** hangman example needs mysql++-2.x library... Skipping.
CMake Error: This project requires some variables to be set,
and cmake can not find them.
Please set the following variables:
OPENSSL_INCLUDE
OPENSSL_LIB

-- Configuring done
eric@eric-laptop:~/wt-2.0.1/build$ 


```

---

### Post by richsewell on 2007-11-29
Check out, I just had the same problem and got around it, so posted it on the Wiki here..

[http://www.webtoolkit.eu/wt/wiki/index.php/Installing_Wt_on_Ubuntu](http://www.webtoolkit.eu/wt/wiki/index.php/Installing_Wt_on_Ubuntu)

---

