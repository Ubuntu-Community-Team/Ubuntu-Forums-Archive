---
title: "How to update C++ header files?"
date: 2014-04-24
forum: Programming Talk
---

### Post by Riothamus on 2014-04-24
I'm running Ubuntu 12.04 LTS with the build-essentials package installed. But programming in C++, I see the header files are outdated and haven't been updated since about 2011 (version 4.6.3). Is there any mechanism for updating them, or do you just download them from somewhere and put them in a new folder under /usr/include/c++? If so, can someone tell me where I download them from, and how I tell g++ which version to use? Thanks.

---

### Post by ofnuts on 2014-04-24
The header files should be coherent with the libraries they represent. So they usually come with a new release of the compiler (runtime support libraries) or with new version of independently installed libraries (or their corresponding -dev packages). There is no point in upgrading only the header files.

For most purposes a distribution release freezes the levels of the package it includes(*). Running a LTS release and upgrading only when the support ends exposes to running rather back-level software. Of course you can upgrade specific packages via PPA or else but sooner or later you get hit by a dependency avalanche and it becomes simpler to upgrade to the next version.


(*) at work I use RHEL servers, installed in 2011 using a 2010 RHEL that contains code frozen in... 2005. Even a mere "find" command I can use on my 12.10 Ubuntu is not guaranteed to work on them.

---

### Post by Riothamus on 2014-04-24
Okay, then can you tell me how to upgrade the compiler and all that? I've been running updates regularly, and I tried sudo apt-get upgrade build-essentials and that still doesn't work. I just want to be able to use the newer functions like to_string and so on.

---

### Post by ofnuts on 2014-04-24
Looks like everything is answered here: [http://askubuntu.com/questions/113291/how-do-i-install-gcc-4-7](http://askubuntu.com/questions/113291/how-do-i-install-gcc-4-7)

---

### Post by steeldriver on 2014-04-24
You should be able to install g++-4.8 (and gcc-4.8) from the standard repository on 12.04

You will need to invoke it explicitly (i.e. as g++-4.8) unless you either modify the /usr/bin/g++ symlink manually or put it under the control of the update-alternatives mechanism. Are you *sure* you need a newer version though? to_string should compile fine under g++-4.6 provided you set the appropriate std flag i.e.

```

$ cat to_string.cpp
// to_string example from www.cplusplus.com
#include <iostream>   // std::cout
#include <string>     // std::string, std::to_string

int main ()
{
  std::string pi = "pi is " + std::to_string(3.1415926);
  std::string perfect = std::to_string(1+2+4+7+14) + " is a perfect number";
  std::cout << pi << '\n';
  std::cout << perfect << '\n';
  return 0;
}

```

```

$ g++-4.6 **-std=c++0x** -o to_string to_string.cpp
$ ./to_string
pi is 3.141593
28 is a perfect number

```

---

### Post by Riothamus on 2014-04-24
Thanks, I guess that is all I needed after all. I wasn't aware it was just a command-line issue. I searched all of the string header file for to_string and didn't see it there, so thought it was an issue of the headers being outdated.

---

