---
title: "zlib installs in conflict, can I force purge?"
date: 2016-03-10
forum: New to Ubuntu
---

### Post by colton4 on 2016-03-10
Hello,

I am trying to install Sass for work, but when I go to do the gem install I get the following message:
> colton@colton-dev:~/Downloads/sass-stable$ gem install sass
ERROR:  Loading command: install (LoadError)
    cannot load such file -- zlib
ERROR:  While executing gem ... (NoMethodError)
    undefined method `invoke_with_build_args' for nil:NilClass

After some googling around I found that the package I needed was some zlib1-dev package. So I manually downloaded this from ubuntu's website and installed with "dpkg -i". It said it had a dependency on zlib1:i386, so I downloaded and installed that in the same way. Apparently I now have conflicting versions of zlib that are screwing each other up, as you can see here:
> 
colton@colton-dev:~/Downloads/sass-stable$ sudo apt-get check
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 zlib1g : Breaks: zlib1g:i386 (!= 1:1.2.8.dfsg-2ubuntu1) but 1:1.2.8.dfsg-1ubuntu1 is installed
 zlib1g:i386 : Breaks: zlib1g (!= 1:1.2.8.dfsg-1ubuntu1) but 1:1.2.8.dfsg-2ubuntu1 is installed
E: Unmet dependencies. Try using -f.

:confused:
I figured "no big deal I'll just uninstall the one I just installed" which is zlib1g:i386. When I try to uninstall it with "sudo apt-get remove zlib1g:i386" it spits out  the following:

> 
colton@colton-dev:~/Downloads$ sudo apt-get remove -f zlib1g:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 gstreamer0.10-plugins-good:i386 : Depends: zlib1g:i386 (>= 1:1.1.4) but it is not going to be installed
 libcaca0:i386 : Depends: zlib1g:i386 (>= 1:1.1.4) but it is not going to be installed
 libcairo2:i386 : Depends: zlib1g:i386 (>= 1:1.1.4) but it is not going to be installed
 libcups2:i386 : Depends: zlib1g:i386 (>= 1:1.2.0) but it is not going to be installed
 libcurl3:i386 : Depends: zlib1g:i386 (>= 1:1.1.4) but it is not going to be installed
 libfreetype6:i386 : Depends: zlib1g:i386 (>= 1:1.1.4) but it is not going to be installed
 libgd2-xpm:i386 : Depends: zlib1g:i386 (>= 1:1.1.4) but it is not going to be installed
 libgd3:i386 : Depends: zlib1g:i386 (>= 1:1.1.4) but it is not going to be installed
 libglib2.0-0:i386 : Depends: zlib1g:i386 (>= 1:1.2.2) but it is not going to be installed
 libgnutls-deb0-28:i386 : Depends: zlib1g:i386 (>= 1:1.1.4) but it is not going to be installed
 libgstreamer-plugins-base0.10-0:i386 : Depends: zlib1g:i386 (>= 1:1.1.4) but it is not going to be installed
 libgstreamer-plugins-base1.0-0:i386 : Depends: zlib1g:i386 (>= 1:1.1.4) but it is not going to be installed
 libllvm3.6:i386 : Depends: zlib1g:i386 (>= 1:1.2.0) but it is not going to be installed
 libmng2:i386 : Depends: zlib1g:i386 (>= 1:1.1.4) but it is not going to be installed
 libmysqlclient18:i386 : Depends: zlib1g:i386 (>= 1:1.1.4) but it is not going to be installed
 libnss3:i386 : Depends: zlib1g:i386 (>= 1:1.1.4) but it is not going to be installed
 libpciaccess0:i386 : Depends: zlib1g:i386 (>= 1:1.2.3.3) but it is not going to be installed
 libpng12-0:i386 : Depends: zlib1g:i386 (>= 1:1.1.4) but it is not going to be installed
 libqt4-network:i386 : Depends: zlib1g:i386 (>= 1:1.1.4) but it is not going to be installed
 libqt4-svg:i386 : Depends: zlib1g:i386 (>= 1:1.1.4) but it is not going to be installed
 libqtcore4:i386 : Depends: zlib1g:i386 (>= 1:1.1.4) but it is not going to be installed
 libqtgui4:i386 : Depends: zlib1g:i386 (>= 1:1.1.4) but it is not going to be installed
 libqtwebkit4:i386 : Depends: zlib1g:i386 (>= 1:1.2.0) but it is not going to be installed
 librtmp1:i386 : Depends: zlib1g:i386 (>= 1:1.1.4) but it is not going to be installed
 libssl0.9.8:i386 : Depends: zlib1g:i386 (>= 1:1.1.4) but it is not going to be installed
 libtag1-vanilla:i386 : Depends: zlib1g:i386 (>= 1:1.1.4) but it is not going to be installed
 libtiff5:i386 : Depends: zlib1g:i386 (>= 1:1.1.4) but it is not going to be installed
 libxml2:i386 : Depends: zlib1g:i386 (>= 1:1.2.3.3) but it is not going to be installed
                Recommends: xml-core:i386 but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
colton@colton-dev:~/Downloads$ sudo apt-get check
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 zlib1g : Breaks: zlib1g:i386 (!= 1:1.2.8.dfsg-2ubuntu1) but 1:1.2.8.dfsg-1ubuntu1 is installed
 zlib1g:i386 : Breaks: zlib1g (!= 1:1.2.8.dfsg-1ubuntu1) but 1:1.2.8.dfsg-2ubuntu1 is installed
E: Unmet dependencies. Try using -f.


Where should I go from here? Should I force purge the package with dpkg?

---

### Post by colton4 on 2016-03-10
Quick update, I ran dpkg --list and saw these at the bottom:


> 
iF  zlib1g:amd64           1:1.2.8.dfsg-2ub amd64            compression library - runtime
iU  zlib1g:i386            1:1.2.8.dfsg-1ub i386             compression library - runtime


so it looks like both of them are kinda half installed?

Here is some more output that could help:
> colton@colton-dev:~/Downloads$ sudo dpkg --configure -a
dpkg: error processing package zlib1g:amd64 (--configure):
 package zlib1g:amd64 1:1.2.8.dfsg-2ubuntu1 cannot be configured because zlib1g:i386 is at a different version (1:1.2.8.dfsg-1ubuntu1)
dpkg: error processing package zlib1g:i386 (--configure):
 package zlib1g:i386 1:1.2.8.dfsg-1ubuntu1 cannot be configured because zlib1g:amd64 is at a different version (1:1.2.8.dfsg-2ubuntu1)
Errors were encountered while processing:
 zlib1g:amd64
 zlib1g:i386




---

