---
title: "Help Installng Synaptic"
date: 2013-12-22
forum: New to Ubuntu
---

### Post by Brendan.M.Gordy on 2013-12-22
I am trying to install Synaptic Package Manager but I am getting this:

ubuntu@ubuntu:~$ sudo apt-get install synaptic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package synaptic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'synaptic' has no installation candidate
ubuntu@ubuntu:~$ 


Any suggestions?

Thanks,
Brendan

---

### Post by deadflowr on 2013-12-22
Run this
```
sudo apt-get update
```
if any errors show post them.
If no errors run
```
sudo apt-get install synaptic
```

When installing, always run an update first.
1) to make sure the repositories you are hitting are correct and not broken.
2)to keep the package lists as up-to-date as possible.
Things can change and sometimes a dependency(or two) can change and the intended package can't install because of those changes.

---

### Post by Brendan.M.Gordy on 2013-12-23
I am still getting the same error:

ubuntu@ubuntu:~$ sudo apt-get update
Ign cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy InRelease
Ign cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy/main Translation-en_US
Ign cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy/main Translation-en
Ign cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy/restricted Translation-en_US
Ign cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security InRelease                   
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security Release.gpg [933 B]       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy InRelease              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates InRelease
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security Release [49.6 kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy Release.gpg [933 B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates Release.gpg [933 B]   
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy Release [49.6 kB]             
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main amd64 Packages [60.5 kB]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates Release [49.6 kB]    
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/main amd64 Packages [1,239 kB]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted amd64 Packages [14 B]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main Translation-en [29.0 kB] 
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted Translation-en [14 B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main Translation-en_US           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted Translation-en_US
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/restricted amd64 Packages [9,348 B]     
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/main Translation-en [711 kB]            
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/restricted Translation-en [2,686 B]     
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/main amd64 Packages [173 kB]    
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/restricted amd64 Packages [14 B]
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/main Translation-en [76.9 kB]   
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/restricted Translation-en [14 B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/main Translation-en_US                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/restricted Translation-en_US               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/main Translation-en_US             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/restricted Translation-en_US       
Fetched 2,453 kB in 35s (69.7 kB/s)                                            
Reading package lists... Done
ubuntu@ubuntu:~$ sudo apt-get install synaptic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package synaptic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'synaptic' has no installation candidate
ubuntu@ubuntu:~$

---

### Post by deadflowr on 2013-12-23
I see no reference to the universe repositories.
You need to enable those, as that is where synaptic is.
To do so, open the dash and type "software and updates".
Then, open that program.
Then check and mark the entry in the window that opens for Community maintained.
It should have a (universe) at the end.
It'll ask for a password.
when checked and marked, close the window and try running the update and then try installing.

---

### Post by grahammechanical on 2013-12-23
You could, of course, try installing Synaptic Package Manager using the Ubuntu Software Centre. Or go to System Settings>Software and Updates and make sure that the repository for Community-maintained free and open-source software (universe) is enabled. If it is not, then enable it and then run

```
sudo apt-get update
```
```
sudo apt-get install synaptic
```

and see what happens. Personally, I find the Software Centre method much easier.

Regards.

---

### Post by phoyce2 on 2013-12-23
I would advise you to go with what grahammechanical said; launch the Ubuntu Software Center and search for 'Synaptic.'  You'll see it there and can then install it.  Good luck!

---

### Post by mc4man on 2013-12-23
software-center will have no better luck...

You appear to be on a live session, not an actual  install. In a live session universe & multiverse aren't enabled & cdrom is.
So in that case open software & updates as mentioned, uncheck cdrom, check universe & if desired multiverse

---

