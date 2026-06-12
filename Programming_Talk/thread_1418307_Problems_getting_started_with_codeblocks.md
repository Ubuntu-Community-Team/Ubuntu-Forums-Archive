---
title: "Problems getting started with code::blocks"
date: 2010-02-28
forum: Programming Talk
---

### Post by lilezek on 2010-02-28
Hi everyone. Recently I changed to Linux, Ubuntu (9.10). I decided to try the Code::Blocks IDE here but I'm getting problems with it. I could run it once, but it closed when I was defining wx global variable (to start with wxWidgets). Next of that I can't run it again. I tryied with terminal and this is what it output:

```
...@...-desktop:~$ codeblocks
codeblocks: relocation error: /usr/lib/libcodeblocks.so.0: symbol _Z18wxSafeConvertWX2MBPKw, version WXU_2.8.2 not defined in file libwx_baseu-2.8.so.0 with link time reference

```

I have no idea about what that error means. So I posted here.

Thanks for read.

---

### Post by azagaros on 2010-02-28
what my experience with code blocks on Ubuntu 9.10 hasn't been favorable.  It seems to be a resource hog and I might go to codelite to fix the problem.

After looking at your error it says something isn't found in a library.  How did you install everything?  did you get the updates to the wxlib through the symantic package manager?

Hope this points you in the right direction..my guess is code:: blocks expects 2.8.2 min and what you have is 2.8.0 more or less.

---

### Post by lilezek on 2010-02-28
> **azagaros said:**
> Hope this points you in the right direction..my guess is code:: blocks expects 2.8.2 min and what you have is 2.8.0 more or less.

I think so:

```
sudo aptitude search libwx
p   libwx-perl                                             - interface to wxWidgets cross-platform GUI toolkit               
p   libwx-perl-dialog-perl                                 - abstract dialog class for simple dialog creation                
p   libwx-perl-processstream-perl                          - access IO of external processes via events (Wx::Perl module)    
i A libwxbase2.6-0                                         - wxBase library (runtime) - non-GUI support classes of wxWidgets 
i   libwxbase2.6-dbg                                       - wxBase library (debug) - non-GUI support classes of wxWidgets to
i A libwxbase2.6-dev                                       - wxBase library (development) - non-GUI support classes of wxWidg
i A libwxbase2.8-0                                         - wxBase library (runtime) - non-GUI support classes of wxWidgets 
i A libwxbase2.8-dbg                                       - wxBase library (debug) - non-GUI support classes of wxWidgets to
i A libwxbase2.8-dev                                       - wxBase library (development) - non-GUI support classes of wxWidg
i   libwxgtk2.6-0                                          - wxWidgets Cross-platform C++ GUI toolkit (GTK+ runtime)         
i   libwxgtk2.6-dbg                                        - wxWidgets Cross-platform C++ GUI toolkit (GTK+ development)     
i   libwxgtk2.6-dev                                        - wxWidgets Cross-platform C++ GUI toolkit (GTK+ development)     
i   libwxgtk2.8-0                                          - wxWidgets Cross-platform C++ GUI toolkit (GTK+ runtime)         
i   libwxgtk2.8-dbg                                        - wxWidgets Cross-platform C++ GUI toolkit (GTK+ debugging)       
i   libwxgtk2.8-dev                                        - wxWidgets Cross-platform C++ GUI toolkit (GTK+ development)     
i   libwxsmithlib0                                         - wxSmith shared library                                          
i   libwxsmithlib0-dev                                     - wxSmith development metapackage                                 
p   libwxsvg-dev                                           - C++ library to create, manipulate and render SVG files          
p   libwxsvg0                                              - C++ library to create, manipulate and render SVG files          

```

---

### Post by SledgeHammer_999 on 2010-02-28
I suppose you installed the nightly builds and the one that was in the official repository. These builds use a newer version of wxWidgets

Anywayz to get newest possible build of wxWidgets take a look here-->[http://wiki.wxpython.org/InstallingOnUbuntuOrDebian](http://wiki.wxpython.org/InstallingOnUbuntuOrDebian)

---

### Post by lilezek on 2010-03-01
> **SledgeHammer_999 said:**
> I suppose you installed the nightly builds and the one that was in the official repository. These builds use a newer version of wxWidgets

Anywayz to get newest possible build of wxWidgets take a look here-->[http://wiki.wxpython.org/InstallingOnUbuntuOrDebian](http://wiki.wxpython.org/InstallingOnUbuntuOrDebian)

Imposible obtener = Impossible to obtain

```
W: Imposible obtener http://apt.wxwidgets.org/dists/karmic-wx/main/binary-amd64/Packages.gz  404  Not Found

W: Imposible obtener http://apt.wxwidgets.org/dists/karmic-wx/main/source/Sources.gz  404  Not Found

```

---

### Post by SledgeHammer_999 on 2010-03-01
Yes it doesn't work for me either. I forgot to mention it. Use **jaunty-wx** instead of **karmic-wx**.

---

### Post by htrex on 2010-05-09
> **SledgeHammer_999 said:**
> Yes it doesn't work for me either. I forgot to mention it. Use **jaunty-wx** instead of **karmic-wx**.

I had the exact same problem on lucid 64.
Lucid repos are not there yet, anyway managed to solve the problem using jaunty repos:
deb [http://apt.wxwidgets.org/](http://apt.wxwidgets.org/) jaunty-wx main

the package there is just 2.8.10.1-1 instead of 2.8.10.1-0ubuntu1 but that seems enough....

---

### Post by Axilus on 2010-05-09
> **lilezek said:**
> Hi everyone. Recently I changed to Linux, Ubuntu (9.10). I decided to try the Code::Blocks IDE here but I'm getting problems with it. I could run it once, but it closed when I was defining wx global variable (to start with wxWidgets). Next of that I can't run it again. I tryied with terminal and this is what it output:

```
...@...-desktop:~$ codeblocks
codeblocks: relocation error: /usr/lib/libcodeblocks.so.0: symbol _Z18wxSafeConvertWX2MBPKw, version WXU_2.8.2 not defined in file libwx_baseu-2.8.so.0 with link time reference

```

I have no idea about what that error means. So I posted here.

Thanks for read.

I highly recommend using Netbeans instead (if you like me and love pretty GUI's and advanced features). I tried code::blocks in my earlier days, but it doesn't compare IMHO.

---

