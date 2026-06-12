---
title: "chome  will not install in ubuntu 12.04.4 under virtualbox on imac"
date: 2014-03-22
forum: New to Ubuntu
---

### Post by wn1ytw on 2014-03-22
this is the error I get in Terminal trying to install chrome on my imac running ubuntu 12.04.4 in VirtualBox. Can anyone help me out? Pardon the newbee stuff please.
In terminal I typed "google-chrome-stable" I  tried with sudo first - it said not to install that way.. 
scott

[0322/110921:ERROR:nss_util.cc(92)] Failed to create /home/scott/.pki/nssdb directory.
[0322/110921:ERROR:nss_util.cc(92)] Failed to create /home/scott/.pki/nssdb directory.
[1985:2014:0322/110924:ERROR:nss_util.cc(92)] Failed to create /home/scott/.pki/nssdb directory.
[1985:1985:0322/110924:ERROR:process_singleton_linux.cc(390)] readlink failed: Permission denied
[1985:1985:0322/110924:ERROR:process_singleton_linux.cc(236)] readlink(/home/scott/.config/google-chrome/SingletonLock) failed: Permission denied
[1985:1985:0322/110924:ERROR:process_singleton_linux.cc(236)] readlink(/home/scott/.config/google-chrome/SingletonLock) failed: Permission denied
[1985:1985:0322/110924:ERROR:process_singleton_linux.cc(260)] Failed to create /home/scott/.config/google-chrome/SingletonLock: Permission denied
[1985:1985:0322/110924:ERROR:process_singleton_linux.cc(390)] readlink failed: Permission denied
[1985:1985:0322/110924:ERROR:process_singleton_linux.cc(236)] readlink(/home/scott/.config/google-chrome/SingletonLock) failed: Permission denied
[1985:1985:0322/110924:ERROR:chrome_browser_main.cc(1211)] Failed to create a ProcessSingleton for your profile directory. This means that running multiple instances would start multiple browser processes rather than opening a new window in the existing process. Aborting now to avoid profile corruption.
scott@scott-VirtualBox:~$ ^C
scott@scott-VirtualBox:~$

---

### Post by kc1di on 2014-03-22
Go to googles chrome page and make sure you download the right one for Ubuntu 32 or 64 bit.

in a terminal install gdebi  like this:
```
sudo apt-get install gdebi
```
it may already be installed.

go to where you down loaded Chrome, right click on the Icon and tell it to install with gdebi.

Follow the instructions on the box when it comes up.
you'll have to give your password when asked.
That should do it. 
look for chrome in the dash.

Also Google Chromium is in the Repositories.  It's the open source version of chrome and can be install via Software center or Synaptic. look for chromium-browser.

Good luck

---

### Post by wn1ytw on 2014-03-22
Thanks Dave, 
Interesting, chrome installed fine - no error messages your way, but when clicked it does nothing... it shows in 'installed apps' and 'recent apps'. I checked all 4 work spaces, what am I missing NOW? Thanks for the quick reply.
scott
(wa1ytw, lived in SW NH and spent lots of time in Lebanon ME)
ps: it is 64 bit, so is computer and VB

---

### Post by kc1di on 2014-03-22
Ok let's try this then Go to your home folder click on view hiddenfiles look for the following folder

```
.config
``` click on it and find the folder```
 google-chrome
``` now look for two files,

```
SingletonLock
```  & ```
SingletonSocket
```

Delete them both or rename them if you like SingltonSocket_bak and SingltonLock_bak

Chrome will recreate them when it runs again. 

See if that solves the problem.

---

### Post by sandyd on 2014-03-22
> **wn1ytw said:**
> this is the error I get in Terminal trying to install chrome on my imac running ubuntu 12.04.4 in VirtualBox. Can anyone help me out? Pardon the newbee stuff please.
In terminal I typed "google-chrome-stable" I  tried with sudo first - it said not to install that way.. 
scott

[0322/110921:ERROR:nss_util.cc(92)] Failed to create /home/scott/.pki/nssdb directory.
[0322/110921:ERROR:nss_util.cc(92)] Failed to create /home/scott/.pki/nssdb directory.
[1985:2014:0322/110924:ERROR:nss_util.cc(92)] Failed to create /home/scott/.pki/nssdb directory.
[1985:1985:0322/110924:ERROR:process_singleton_linux.cc(390)] readlink failed: Permission denied
[1985:1985:0322/110924:ERROR:process_singleton_linux.cc(236)] readlink(/home/scott/.config/google-chrome/SingletonLock) failed: Permission denied
[1985:1985:0322/110924:ERROR:process_singleton_linux.cc(236)] readlink(/home/scott/.config/google-chrome/SingletonLock) failed: Permission denied
[1985:1985:0322/110924:ERROR:process_singleton_linux.cc(260)] Failed to create /home/scott/.config/google-chrome/SingletonLock: Permission denied
[1985:1985:0322/110924:ERROR:process_singleton_linux.cc(390)] readlink failed: Permission denied
[1985:1985:0322/110924:ERROR:process_singleton_linux.cc(236)] readlink(/home/scott/.config/google-chrome/SingletonLock) failed: Permission denied
[1985:1985:0322/110924:ERROR:chrome_browser_main.cc(1211)] Failed to create a ProcessSingleton for your profile directory. This means that running multiple instances would start multiple browser processes rather than opening a new window in the existing process. Aborting now to avoid profile corruption.
scott@scott-VirtualBox:~$ ^C
scott@scott-VirtualBox:~$
Dont run applications with sudo - it messes up the permissions.
Try
```

sudo chown -R scott:scott /home/scott/.pki
sudo chown -R scott:scott /home/scott/.config/google-chrome
```

---

### Post by wn1ytw on 2014-03-22
Dave, 
> **kc1di said:**
> Ok let's try this then Go to your home folder click on view hiddenfiles look for the following folder

```
.config
``` click on it and find the folder```
 google-chrome
``` now look for two files,

```
SingletonLock
```  & ```
SingletonSocket
```

Delete them both or rename them if you like SingltonSocket_bak and SingltonLock_bak

Chrome will recreate them when it runs again. 

See if that solves the problem.

I don't have permission to open google-chrome folder, so nothing further... tring to remember the other ways. I tried via the terminal.... I was stopped froom opening the folder there too... guess I go read about permissions again...

I guess I messed up permissions early on!
scott
EDIT no files except . and .. in ~/.cache/google-chrome
hmph.
EDIT 2: it worked after restart Dave, TNX es 73 de 'ytw

---

### Post by kc1di on 2014-03-22
try sandyd's solution some how your (Home) folder has the wrong owner or permissions.

---

### Post by wn1ytw on 2014-03-22
I was just returning to report the permissions were root:root and I had changed them and then it was fine, it is now my default browser. Thanks Dave AND Sandyd!!

scott

---

### Post by kc1di on 2014-03-22
Glad you got it sorted and welcome to Ubuntu ;)

---

### Post by wn1ytw on 2014-03-22
> **kc1di said:**
> try sandyd's solution some how your (Home) folder has the wrong owner or permissions.
 only the chrome folder, must have been sandyd's thing- not intentional, my ignorance. thanx, been trying off and on 4 6 months with ubuntu. 2 windows machines dual-booted, 1 laptop only ubuntu and this imac, the hardest of the bunch- but i love it 
73
scott

---

