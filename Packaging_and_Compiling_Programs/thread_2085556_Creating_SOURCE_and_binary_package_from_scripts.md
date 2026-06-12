---
title: "Creating SOURCE and binary package from scripts"
date: 2012-11-18
forum: Packaging and Compiling Programs
---

### Post by bronkeydain on 2012-11-18
Hi there people,

I am trying to work out a procedure to create both source and binary packages for one or more shell scripts. I am being asked by a client of mine who wants this. They just want to package scripts for internal use. 

Creating binary (.deb) packages is quite easy but I am a bit lost on the source package. Every tutorial is assuming I am downloading an upstream tarball. Do I need to create one myself? Do I create the ./debian file structure inside the tarball? 

I supspect I am just thinking in the wrong direction or just not getting the concept... Hopefully a little push in the right one will put me on track. 

Any help would be appreciated.

---

### Post by bronkeydain on 2012-11-21
OK I have sorted it out. The thing that was putting me off was the upstream tarball part.

All you do is:
1. Create project directory say ~/packagename/packagename-1.0
2. Copy your script files to that directory
3. create tar: 
# cd ~/packagename
# tar czf packagename_1.0.orig.tar.gz packagename-1.0 (watch hyphens and underscores)

4. Create your package as you would with a downloaded upstream tarball.

Any questions? PM me..

---

### Post by bronkeydain on 2012-11-22
I still have questions about creating an upstream tarball. I was gonna re-open this thread but I decided to make a new one instead:

[http://ubuntuforums.org/showthread.php?t=2086936http://]("http://ubuntuforums.org/showthread.php?t=2086936http://")

---

