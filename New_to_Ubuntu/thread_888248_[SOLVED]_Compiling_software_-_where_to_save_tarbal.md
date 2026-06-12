---
title: "[SOLVED] Compiling software - where to save tarball?"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by Chilli Bob on 2008-08-12
I'm trying my first compile from source (the latest version of Viking GPS software, newer than the one in the repositories).  I've read some tutorials and think I'm ready to go except for one thing that none of the how-to's make clear.  Do I have to save and extract the source code in any particular folder before I run ./configure etc?  Can I just put it in a /viking folder in my  home directory, or do I have to have it somewhere particular like /usr/local or something?

Thanks in advance for your help.

---

### Post by tuxxy on 2008-08-12
It maybe useful putting it in usr/lib/ or somewhere with the other apps but no it doesnt matter, if you want it in your /home then you can do :)

---

### Post by Chilli Bob on 2008-08-12
Thanks for that.  

Now I just need to sort out these dependencies.....[SIZE=1],,[/SIZE]

---

### Post by Rolcol on 2008-08-13
you can use apt-get to get the dependancies for it:  ```
sudo apt-get build-dep package-name
```

I always use build-dep when compiling from source.  The dependencies should be at OK versions to compile.

---

### Post by sdennie on 2008-08-13
> **Chilli Bob said:**
> I'm trying my first compile from source (the latest version of Viking GPS software, newer than the one in the repositories).  I've read some tutorials and think I'm ready to go except for one thing that none of the how-to's make clear.  Do I have to save and extract the source code in any particular folder before I run ./configure etc?  Can I just put it in a /viking folder in my  home directory, or do I have to have it somewhere particular like /usr/local or something?


No, you don't.  A relatively common place to put source code is in /usr/src but, for this kind of thing, I actually recommend making a ~/src directory, moving the file there and extracting it.  If you download source tarballs or grab things from svn or git, you can just lump it all in there and have it as an organized directory of all the packages you've compiled locally.  I personally also have an ~/src/orig directory where, after I untar, I move the tarball to so that I have a reference of what the original package was.

---

### Post by ramjet_1953 on 2008-08-13
You will also need to install [COLOR="Blue"]intltool[/COLOR] if you are compiling it yourself.

Also, it is a good idea to install a package called [COLOR="Blue"]checkinstall[/COLOR], as it lets you compile to a .deb package which can then be installed and un-installed using the package manager.

Regards,
Roger :cool:

---

