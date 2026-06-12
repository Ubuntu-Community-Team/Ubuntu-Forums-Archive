---
title: "The best IDE for Fortran?"
date: 2007-01-15
forum: Programming Talk
---

### Post by hopestorm on 2007-01-15
I have been using Fortran under window for few years and the MS Developer Studio is pretty convenient. 
Now I decide to be more linux-ed in my research. Could you please recommend me some IDEs are good for Fortran coding, compiling and debugging?

Thanks,

---

### Post by neoflight on 2007-01-15
> **hopestorm said:**
> I have been using Fortran under window for few years and the MS Developer Studio is pretty convenient. 
Now I decide to be more linux-ed in my research. Could you please recommend me some IDEs are good for Fortran coding, compiling and debugging?

Thanks,

i would say any text editor. + command line compiling.....thts much nicer since there is much greater flexibility in using the 'switches' while compiling....

---

### Post by Vikstar on 2008-07-21
Don't know if it is the best or not, haven't even ever used Fortran, but once I stumbled upon [Photran]("http://www.eclipse.org/photran/").

---

### Post by rchrd on 2008-07-22
Try Sun Studio. It has its own f95 compiler and IDE. [http://developers.sun.com/sunstudio](http://developers.sun.com/sunstudio)

---

### Post by akikidis on 2008-12-17
> **rchrd said:**
> Try Sun Studio. It has its own f95 compiler and IDE. [http://developers.sun.com/sunstudio](http://developers.sun.com/sunstudio)

Can you give me any instructions on how to install it on Ubuntu 8.10?

Thank you in advance!

---

### Post by rchrd on 2008-12-17
go to [http://developers.sun.com/sunstudio/downloads/express/index.jsp](http://developers.sun.com/sunstudio/downloads/express/index.jsp) and read the readme, register, and download the tar-ball (also called the product installer).

There may be some limitations on Ubuntu but they are probably pretty obscure. For the most part it should work. This is an "Express" release, sorta like a beta. The compilers can be accessed via the Sun Studio IDE or from the command line.  

The IDE editor itself is not as Fortran-friendly as one would like .. it's based on NetBeans 6.5, but it is certainly quite usable. It also is makefile-aware, so you can also import any makefile you are using.

More information here

[http://wikis.sun.com/display/SunStudio/Installing+Sun+Studio+on+Different+Linux+Distros](http://wikis.sun.com/display/SunStudio/Installing+Sun+Studio+on+Different+Linux+Distros)

and here:

[http://wikis.sun.com/display/SunStudio/Sun+Studio+Linux+Platform+FAQ](http://wikis.sun.com/display/SunStudio/Sun+Studio+Linux+Platform+FAQ)

---

### Post by darmarLT on 2010-05-14
Hello

I would suggest to try Code::Blocks IDE with the FortranProject plugin. I am developing this plugin. With this plugin C::B is full featured IDE for Fortran programmers with code-browser, code-completion etc. Precompiled versions can be downloaded from my site [http://darmar.vgtu.lt](http://darmar.vgtu.lt)

---

### Post by mervart on 2013-01-13
I have tried to work with a relatively large Fortran project (1000+ source files). Eclipse with Photran was not able to resolve the dependencies and without a prepared makefile was useless. Code::Blocks seems to work fine.

---

