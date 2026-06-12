---
title: "another error code"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by minibeardeath on 2008-04-29
whenever i attempt to install anything using synaptic i get the following error:
```

setting up msttcorefonts (2.4) ...


Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts:
   subprocess post-installation script returned error status 1
```

and when ever i try to un-check microsoft core fonts (the guilty app.) i get the following error:
```
E: msttcorefonts: subprocess pre-removal script returned error exit status 1

```

please advise as to what i should do, as far as i know, this error does not affect any of the other files that i am (un)installing, but it is very annoying to have the error occur every time.

thanks

---

### Post by Drone4four on 2008-04-29
If you open up a terminal window (Applications/Accessories/Terminal) and type "sudo apt-get update" and "sudo apt-get upgrade" without the quotes, what response do you get?

---

### Post by minibeardeath on 2008-04-30
```
Hit http://archive.canonical.com hardy Release.gpg
Ign http://archive.canonical.com hardy/partner Translation-en_US    
Hit http://security.ubuntu.com gutsy-security Release.gpg           
Ign http://security.ubuntu.com gutsy-security/main Translation-en_US 
Hit http://archive.ubuntu.com hardy Release.gpg                      
Ign http://archive.ubuntu.com hardy/main Translation-en_US           
Hit http://archive.canonical.com hardy Release                       
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_US
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_US
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_US
Hit http://security.ubuntu.com hardy-security Release.gpg            
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US
Ign http://security.ubuntu.com hardy-security/main Translation-en_US 
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US
Ign http://archive.ubuntu.com hardy/multiverse Translation-en_US     
Ign http://archive.ubuntu.com hardy/universe Translation-en_US
Ign http://archive.ubuntu.com hardy/restricted Translation-en_US
Hit http://archive.ubuntu.com hardy-updates Release.gpg
Ign http://archive.ubuntu.com hardy-updates/universe Translation-en_US
Ign http://archive.ubuntu.com hardy-updates/main Translation-en_US
Ign http://archive.ubuntu.com hardy-updates/multiverse Translation-en_US
Hit http://archive.canonical.com hardy/partner Packages
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US
Hit http://security.ubuntu.com gutsy-security Release
Ign http://archive.ubuntu.com hardy-updates/restricted Translation-en_US
Hit http://archive.ubuntu.com hardy Release                         
Hit http://security.ubuntu.com hardy-security Release                          
Hit http://archive.ubuntu.com hardy-updates Release                            
Hit http://archive.canonical.com hardy/partner Sources                         
Hit http://security.ubuntu.com gutsy-security/main Packages          
Hit http://security.ubuntu.com gutsy-security/restricted Packages
Hit http://security.ubuntu.com gutsy-security/universe Packages
Hit http://archive.ubuntu.com hardy/main Packages
Hit http://archive.ubuntu.com hardy/multiverse Packages
Hit http://archive.ubuntu.com hardy/universe Packages
Hit http://security.ubuntu.com gutsy-security/multiverse Packages
Hit http://security.ubuntu.com hardy-security/universe Packages
Hit http://security.ubuntu.com hardy-security/main Packages
Hit http://archive.ubuntu.com hardy/restricted Packages
Hit http://archive.ubuntu.com hardy-updates/universe Packages
Hit http://archive.ubuntu.com hardy-updates/main Packages
Hit http://security.ubuntu.com hardy-security/multiverse Packages
Hit http://archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://archive.ubuntu.com hardy-updates/restricted Packages
Hit http://security.ubuntu.com hardy-security/restricted Packages
Reading package lists... Done
patrick@seniorproject:~$ 


```

and
```
patrick@seniorproject:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up msttcorefonts (2.4) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Mogurijin on 2008-04-30
One thing I would do is take a look at your sources, or is it normal to be using Hardy and Gutsy repositories at the same time? :neutral:

---

### Post by minibeardeath on 2008-04-30
good point, how do i go about checking that?

---

