---
title: "Just the source code"
date: 2010-09-30
forum: Programming Talk
---

### Post by Dragonbite on 2010-09-30
There are some open source programs out there I would like to just look through the code for learning purposes. 

A number of them, though, are using Git and I just want to download the source code. I don't know much about Git, but I just want to look through the code, not necessarily get involved with development at this time.

For example, I have been wanting to look at the code for F-Spot and I haven't found any non-Git methods of doing that (short of emailing the developer which is my next step if nobody knows of any other way).

Eventually I am going to be looking into Git, and it's possibility of being used at work to make things easier, but not yet.

Anybody have any ideas or suggestions, or do I need to suck it up and figure out how to use Git?

Thanks

---

### Post by sharathcshekhar on 2010-09-30
Is apt-get source fspot 
what you are looking at?

---

### Post by Bachstelze on 2010-09-30
As sharathcshekhar said, if the package is in Ubuntu, [font=monospace]apt-get source <package name>[/font] will give you the source from which the Ubuntu package was compiled.

If you want the latest source, you can use [font=monospace]git clone[/font] or [font=monospace]svn checkout[/font] to get it, depending on the VCS the project use. They will probably have instructions about how to get it on their website, and maybe even snapshot tarballs.

---

### Post by Dragonbite on 2010-09-30
I thought apt-get source <program> would install it from source, not give me the source code! (sorry.. guess that's a flashback from my Gentoo days ;)).  

Where does it put the code, or does it ask?

---

### Post by schauerlich on 2010-09-30
> **Dragonbite said:**
> I thought apt-get source <program> would install it from source, not give me the source code! (sorry.. guess that's a flashback from my Gentoo days ;)).  

Where does it put the code, or does it ask?

from "man apt-get":

> source causes apt-get to fetch source packages. APT will examine the available packages to decide which source package to fetch. It will then find and download into the current directory the newest available version of that source package. 

---

### Post by Dragonbite on 2010-09-30
Thanks!

I'll take a look at it tonight when I'm sitting in front of (one of) my Ubuntu boxes.

This could get dangerous too, since I'm toying between focusing on C# (Mono), Java, Python and PHP!
:guitar:

---

### Post by eeperson on 2010-09-30
> **Dragonbite said:**
> There are some open source programs out there I would like to just look through the code for learning purposes. 

A number of them, though, are using Git and I just want to download the source code. I don't know much about Git, but I just want to look through the code, not necessarily get involved with development at this time.

For example, I have been wanting to look at the code for F-Spot and I haven't found any non-Git methods of doing that (short of emailing the developer which is my next step if nobody knows of any other way).

Eventually I am going to be looking into Git, and it's possibility of being used at work to make things easier, but not yet.

Anybody have any ideas or suggestions, or do I need to suck it up and figure out how to use Git?

Thanks

You only need one git command to get a copy of the repository:

```

git clone <put-repository-url-here>

```

Also projects using git generally have a gitweb interface that lets you browse code without checking anything out.

Edit: The gitweb interface for F-Spot is here: [http://git.gnome.org/browse/f-spot/](http://git.gnome.org/browse/f-spot/)

---

### Post by Dragonbite on 2010-09-30
> **eeperson said:**
> You only need one git command to get a copy of the repository:

```

git clone <put-repository-url-here>

```

Also projects using git generally have a gitweb interface that lets you browse code without checking anything out.

Edit: The gitweb interface for F-Spot is here: [http://git.gnome.org/browse/f-spot/](http://git.gnome.org/browse/f-spot/)

I'm kinda thick.. I did run into this page but don't know how to use it.  I'm looking for .cs files!

---

### Post by eeperson on 2010-09-30
> **Dragonbite said:**
> I'm kinda thick.. I did run into this page but don't know how to use it.  I'm looking for .cs files!
If you click the 'tree' link in the upper left you can look at the source code.  That link will take you root directory of the source code.

---

