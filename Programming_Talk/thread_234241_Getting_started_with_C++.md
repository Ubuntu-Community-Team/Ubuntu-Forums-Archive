---
title: "Getting started with C++"
date: 2006-08-11
forum: Programming Talk
---

### Post by Jonas_Henricsson on 2006-08-11
I'm going to study a course in C++. Everyone assumes you use windows these days, so recommended programs seem to be for windows (CYGWIN and DJGPP). I'm using Ubuntu Dapper Drake. What programs should I use to program successfully in C++? I really just need to get started and I'm not sure were to begin.

Thanks for any help!

/Jonas

---

### Post by thumper on 2006-08-11
Use any good editor (emacs, vi, kate, et al) and g++.

Install the build-essential package to get the compiler and all its bits.

Then get yourself a copy of [accelerated c++](http://www.acceleratedcpp.com/).

---

### Post by badactress on 2006-08-11
Hi Jonas!

I'm in similar position. Recently moved from Windows & been looking around for C/C++ compilers/IDE's to use under Ubuntu.

After trying a few I'd recommend Anjuta IDE with the GNU G++/GCC compiler (part of the build-essential package).

[http://ubuntuguide.org/wiki/Dapper#How_to_install_Basic_Compilers_.28build-essential.29]("http://ubuntuguide.org/wiki/Dapper#How_to_install_Basic_Compilers_.28build-essential.29")

Anjuta is fairly basic, but on my system I've found it to be far more stable & reliable than other IDE's.

Also worth checking out are CODE::BLOCKS and Eclipse (with C++ plugin). They both seem more advanced than Anjuta, but CODE::BLOCKS crashes constantly on my setup, and Eclipse is really aimed toward Java development, though is apparently pretty impressive as a C++ IDE if you install the C++ plugins.

Hope this helps a little!

Cheers,
Norm

---

### Post by [h2o] on 2006-08-11
KDevelop is also available, but it did not really live up to my expectations.

---

### Post by GeoMX on 2006-08-11
I started with gedit and command line compiling through the terminal, learned some basics about makefiles. Then, I tried Anjuta but when creating a project it creates lots of directories and configuration options, and because I'm not creating Linux distributable software I feel I don't need all these features.

I'm giving Code::Blocks a try, and it seems quite good at the momento :).

Regards,
JJ Enríquez (GeoMX).

---

### Post by Jonas_Henricsson on 2006-08-11
A friend of mine recommended Eclipse, so I'm trying it out. Is it a good program?

/Jonas

---

