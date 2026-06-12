---
title: "Manually set package dependencies"
date: 2011-11-21
forum: Packaging and Compiling Programs
---

### Post by San_SS! on 2011-11-21
I am trying to package a tool I'm developing. And I know it depends on python3 and python3-lxml.

Is it ok to put in the debian/control file this??

```

Source: xxx
Section: unknown
Priority: extra
Maintainer: xxx <xxx@xxx>
Build-Depends: debhelper (>= 7.0.50~)
Standards-Version: 3.8.4
Homepage: <insert the upstream URL, if relevant>


Package: xxx
Architecture: all
Depends: ${misc:Depends}, python3, python3-lxml
Description: <insert up to 60 chars description>

```

---

### Post by Bachstelze on 2011-11-21
It's okay if the package depends on Python to run but not build. Just try. If you can build and run your package with this debian/control, it means it is right. ;)

---

### Post by San_SS! on 2011-11-21
Basically, as my program is purely written in python, I don't need to build it actually. To install it, all I want is to copy the sources to /usr/share/myprogram and create a link in /usr/bin for the launcher.

This is the first time I'm trying to make a package and I don't know if i'm doing it well.

---

### Post by Bachstelze on 2011-11-21
What is your goal in making this package? If you want to just make it work, it's simple enough, but if you want to package stuff for the official repos, a Python app is probably not a good way to start.

---

### Post by San_SS! on 2011-11-21
I would like to make it to the official repos in the future. 

Why is a Python app not a good way to start?

---

### Post by Bachstelze on 2011-11-21
Beause the natural source to build a package from is C/C++ with an autotools-based build systems. There is a lot of things involved in making a package, so the learning curve is very steep. You don't want to make your life even harder by using something that requires unusual treatment at the same time you are learning the basic concepts of packaging.

---

### Post by San_SS! on 2011-11-21
Oh, I see. I thought that having a package for a python app was a bad idea. It is a bad idea to start learning packaging with it, right?

I based my solution on sqlmap's .deb package from the repos.

---

