---
title: "Cannot install skype.. lots of dependencies issues.."
date: 2013-06-12
forum: New to Ubuntu
---

### Post by taupaji on 2013-06-12
***Cannot install skype.. lots of dependencies issues.. Please help.... :( Aptitude shows this solution only.. My OS is Ubuntu 12.04 LTS***

 
```
tau@UBUNTU:~$ sudo aptitude install skype --without-recommends
The following NEW packages will be installed:
  libasound2:i386{a} libaudio2:i386{a} libc-bin:i386{ab} libc6:i386{ab} libdbus-1-3:i386{ab} libexpat1:i386{ab} libffi6:i386{a}

  libfontconfig1:i386{a} libfreetype6:i386{ab} libgcc1:i386{a} libglib2.0-0:i386{a} libice6:i386{a} libjpeg-turbo8:i386{a} libjpeg8:i386{a} 
  liblcms1:i386{a} libmng1:i386{a} libpcre3:i386{a} libpng12-0:i386{a} libqt4-dbus:i386{ab} libqt4-declarative:i386{ab} libqt4-network:i386{ab} 
  libqt4-script:i386{ab} libqt4-sql:i386{ab} libqt4-xml:i386{ab} libqt4-xmlpatterns:i386{ab} libqtcore4:i386{ab} libqtgui4:i386{ab} 
  libselinux1:i386{a} libsm6:i386{a} libstdc++6:i386{a} libtiff4:i386{ab} libuuid1:i386{a} libx11-6:i386{a} libxau6:i386{a} libxcb1:i386{a} 
  libxdmcp6:i386{a} libxext6:i386{a} libxi6:i386{a} libxrender1:i386{a} libxss1:i386{a} libxt6:i386{a} libxv1:i386{a} skype skype-bin:i386{a} 
  zlib1g:i386{a} 
The following packages are RECOMMENDED but will NOT be installed:
  libasound2-plugins:i386 libcups2:i386 libqt4-sql-mysql:i386 libqt4-sql-odbc:i386 libqt4-sql-psql:i386 libqt4-sql-sqlite:i386 qdbus:i386 
  sni-qt:i386 
0 packages upgraded, 45 newly installed, 0 to remove and 0 not upgraded.
Need to get 43.6 MB of archives. After unpacking 93.6 MB will be used.
The following packages have unmet dependencies:
 libc-bin : Conflicts: libc-bin:i386 but 2.15-0ubuntu10 is to be installed.
 libc-bin:i386 : Conflicts: libc-bin but 2.15-0ubuntu10.2 is installed.
 libqt4-declarative : Breaks: libqt4-declarative:i386 (!= 4:4.8.1-0ubuntu4.4) but 4:4.8.1-0ubuntu4.1 is to be installed.
 libqt4-declarative:i386 : Breaks: libqt4-declarative (!= 4:4.8.1-0ubuntu4.1) but 4:4.8.1-0ubuntu4.4 is installed.
 libdbus-1-3 : Breaks: libdbus-1-3:i386 (!= 1.4.18-1ubuntu1.3) but 1.4.18-1ubuntu1 is to be installed.
 libdbus-1-3:i386 : Breaks: libdbus-1-3 (!= 1.4.18-1ubuntu1) but 1.4.18-1ubuntu1.3 is installed.
 libqt4-script : Breaks: libqt4-script:i386 (!= 4:4.8.1-0ubuntu4.4) but 4:4.8.1-0ubuntu4.1 is to be installed.
 libqt4-script:i386 : Breaks: libqt4-script (!= 4:4.8.1-0ubuntu4.1) but 4:4.8.1-0ubuntu4.4 is installed.
 libqt4-network : Breaks: libqt4-network:i386 (!= 4:4.8.1-0ubuntu4.4) but 4:4.8.1-0ubuntu4.1 is to be installed.
 libqt4-network:i386 : Breaks: libqt4-network (!= 4:4.8.1-0ubuntu4.1) but 4:4.8.1-0ubuntu4.4 is installed.
 libqt4-dbus : Breaks: libqt4-dbus:i386 (!= 4:4.8.1-0ubuntu4.4) but 4:4.8.1-0ubuntu4.1 is to be installed.
 libqt4-dbus:i386 : Breaks: libqt4-dbus (!= 4:4.8.1-0ubuntu4.1) but 4:4.8.1-0ubuntu4.4 is installed.
 libfreetype6 : Breaks: libfreetype6:i386 (!= 2.4.8-1ubuntu2.1) but 2.4.8-1ubuntu2 is to be installed.
 libfreetype6:i386 : Breaks: libfreetype6 (!= 2.4.8-1ubuntu2) but 2.4.8-1ubuntu2.1 is installed.
 libexpat1 : Breaks: libexpat1:i386 (!= 2.0.1-7.2ubuntu1.1) but 2.0.1-7.2ubuntu1 is to be installed.
 libexpat1:i386 : Breaks: libexpat1 (!= 2.0.1-7.2ubuntu1) but 2.0.1-7.2ubuntu1.1 is installed.
 libqt4-xmlpatterns : Breaks: libqt4-xmlpatterns:i386 (!= 4:4.8.1-0ubuntu4.4) but 4:4.8.1-0ubuntu4.1 is to be installed.
 libqt4-xmlpatterns:i386 : Breaks: libqt4-xmlpatterns (!= 4:4.8.1-0ubuntu4.1) but 4:4.8.1-0ubuntu4.4 is installed.
 libqtcore4 : Breaks: libqtcore4:i386 (!= 4:4.8.1-0ubuntu4.4) but 4:4.8.1-0ubuntu4.1 is to be installed.
 libqtcore4:i386 : Breaks: libqtcore4 (!= 4:4.8.1-0ubuntu4.1) but 4:4.8.1-0ubuntu4.4 is installed.
 libqt4-sql : Breaks: libqt4-sql:i386 (!= 4:4.8.1-0ubuntu4.4) but 4:4.8.1-0ubuntu4.1 is to be installed.
 libqt4-sql:i386 : Breaks: libqt4-sql (!= 4:4.8.1-0ubuntu4.1) but 4:4.8.1-0ubuntu4.4 is installed.
 libqt4-xml : Breaks: libqt4-xml:i386 (!= 4:4.8.1-0ubuntu4.4) but 4:4.8.1-0ubuntu4.1 is to be installed.
 libqt4-xml:i386 : Breaks: libqt4-xml (!= 4:4.8.1-0ubuntu4.1) but 4:4.8.1-0ubuntu4.4 is installed.
 libtiff4 : Breaks: libtiff4:i386 (!= 3.9.5-2ubuntu1.5) but 3.9.5-2ubuntu1.1 is to be installed.
 libtiff4:i386 : Breaks: libtiff4 (!= 3.9.5-2ubuntu1.1) but 3.9.5-2ubuntu1.5 is installed.
 libqtgui4 : Breaks: libqtgui4:i386 (!= 4:4.8.1-0ubuntu4.4) but 4:4.8.1-0ubuntu4.1 is to be installed.
 libqtgui4:i386 : Breaks: libqtgui4 (!= 4:4.8.1-0ubuntu4.1) but 4:4.8.1-0ubuntu4.4 is installed.
 libc6 : Breaks: libc6:i386 (!= 2.15-0ubuntu10.2) but 2.15-0ubuntu10 is to be installed.
 libc6:i386 : Breaks: libc6 (!= 2.15-0ubuntu10) but 2.15-0ubuntu10.2 is installed.
Internal error: the solver Install(libc-bin:amd64 2.15-0ubuntu10 <libc6:i386 2.15-0ubuntu10 -> {libc-bin:amd64 2.15-0ubuntu10 libc-bin:i386 2.15-0ubuntu10}>) of a supposedly unresolved dependency is already installed in step 10
Internal error: the solver Install(libc-bin:amd64 2.15-0ubuntu10 <libc6:i386 2.15-0ubuntu10 -> {libc-bin:amd64 2.15-0ubuntu10 libc-bin:i386 2.15-0ubuntu10}>) of a supposedly unresolved dependency is already installed in step 17
Internal error: the solver Install(libc-bin:amd64 2.15-0ubuntu10 <libc6:i386 2.15-0ubuntu10 -> {libc-bin:amd64 2.15-0ubuntu10 libc-bin:i386 2.15-0ubuntu10}>) of a supposedly unresolved dependency is already installed in step 24
The following actions will resolve these dependencies:

      Keep the following packages at their current version:
1)      libasound2:i386 [Not Installed]                    
2)      libaudio2:i386 [Not Installed]                     
3)      libc-bin:i386 [Not Installed]                      
4)      libc6:i386 [Not Installed]                         
5)      libdbus-1-3:i386 [Not Installed]                   
6)      libexpat1:i386 [Not Installed]                     
7)      libffi6:i386 [Not Installed]                       
8)      libfontconfig1:i386 [Not Installed]                
9)      libfreetype6:i386 [Not Installed]                  
10)     libgcc1:i386 [Not Installed]                       
11)     libglib2.0-0:i386 [Not Installed]                  
12)     libice6:i386 [Not Installed]                       
13)     libjpeg-turbo8:i386 [Not Installed]                
14)     libjpeg8:i386 [Not Installed]                      
15)     liblcms1:i386 [Not Installed]                      
16)     libmng1:i386 [Not Installed]                       
17)     libpcre3:i386 [Not Installed]                      
18)     libpng12-0:i386 [Not Installed]                    
19)     libqt4-dbus:i386 [Not Installed]                   
20)     libqt4-declarative:i386 [Not Installed]            
21)     libqt4-network:i386 [Not Installed]                
22)     libqt4-script:i386 [Not Installed]                 
23)     libqt4-sql:i386 [Not Installed]                    
24)     libqt4-xml:i386 [Not Installed]                    
25)     libqt4-xmlpatterns:i386 [Not Installed]            
26)     libqtcore4:i386 [Not Installed]                    
27)     libqtgui4:i386 [Not Installed]                     
28)     libselinux1:i386 [Not Installed]                   
29)     libsm6:i386 [Not Installed]                        
30)     libstdc++6:i386 [Not Installed]                    
31)     libtiff4:i386 [Not Installed]                      
32)     libuuid1:i386 [Not Installed]                      
33)     libx11-6:i386 [Not Installed]                      
34)     libxau6:i386 [Not Installed]                       
35)     libxcb1:i386 [Not Installed]                       
36)     libxdmcp6:i386 [Not Installed]                     
37)     libxext6:i386 [Not Installed]                      
38)     libxi6:i386 [Not Installed]                        
39)     libxrender1:i386 [Not Installed]                   
40)     libxss1:i386 [Not Installed]                       
41)     libxt6:i386 [Not Installed]                        
42)     libxv1:i386 [Not Installed]                        
43)     skype [Not Installed]                              
44)     skype-bin:i386 [Not Installed]                     
45)     zlib1g:i386 [Not Installed]                        



Accept this solution? [Y/n/q/?] q
Abandoning all efforts to resolve these dependencies.
Abort
```

---

### Post by mastablasta on 2013-06-12
why --without-recommends ?

why nto just install it from software center as it is provided or use .deb file?

---

### Post by HermanAB on 2013-06-12
Howdy,

The main problem with Skype is that it is a 32 bit program and most Linux systems built this century are 64 bit.  So to make Skype work, you got to install a bunch of 32 bit libraries.

Your first choice for a program should always be the software centre, which will take care of all the dependencies automatically.  However, if you are a masochist, then you can get a 'static' linked version from the Skype web site, which includes most of the required libraries.

---

### Post by squakie on 2013-06-12
+1 on the software center or something like synaptic package manager.  I've installed Skype on several systems - including 64-bit systems - and never had a problem as long as I used the "normal" way to install.

---

### Post by slickymaster on 2013-06-12
> **HermanAB said:**
> ... Your first choice for a program should always be the software centre, which will take care of all the dependencies automatically...

A big +1 on always installing through the Software Center.

Here's a tutorial on how to do it via Ubuntu Software Center: [How do I install Skype?]("http://askubuntu.com/questions/7498/how-do-i-install-skype")

---

### Post by Lars Noodén on 2013-06-12
+1 for the suggestions to use the Software Center.  The value of using the repositories to manage software cannot be overstated.

Also while you're adding things you might look at adding an SIP client like Linphone.  It has better sound quality (last I checked) and is open source / open standard instead of completely proprietary like Skype is.

---

### Post by mastablasta on 2013-06-12
> **Lars Noodén said:**
> Also while you're adding things you might look at adding an SIP client like Linphone. It has better sound quality (last I checked) and is open source / open standard instead of completely proprietary like Skype is.

but what are the rates? internet->phone

---

### Post by Lars Noodén on 2013-06-12
> **mastablasta said:**
> but what are the rates? internet->phone

That depends on the SIP service you have signed up with.  I don't use dialout so I don't remember all the companies you can choose from.  The only one whose name I recall at the moment is Diamondcard.  There are a bunch others and the rates vary but I can't recall the names.  There might be a list somewhere.

---

### Post by kherring7383 on 2013-06-12
I don't know what video card you have installed, but there have been problems installing Skype with Nvidia and AMD. However, here's a link that may help. 

[http://linuxg.net/how-to-install-skype-on-ubuntu-13-04/](http://linuxg.net/how-to-install-skype-on-ubuntu-13-04/)

---

