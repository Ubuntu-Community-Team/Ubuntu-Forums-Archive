---
title: "Is it possible to show the paths that are affected before apt-get install starts?"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by Asham on 2008-10-24
I have installed the Sun Java source code, 
[INDENT]sudo apt-get install sun-java6-source[/INDENT]

I got the location for *this particular installation* (/usr/lib/jvm/java-6-sun-1.6.0.10) after performing a search.

**The question is: ** how do I find out the paths for different apt-get install commands that might put files into different places? (I'm using the terminal by the way)

/Adam

---

### Post by em4r1z on 2008-10-24
I just checked the apt-get entry in the manual pages and I didn't find an option to do what you're looking for. In Synaptic, you can see the location of all files installed by a package in the information tabs.

---

### Post by sdennie on 2008-10-24
After installing a package you can see what files have been installed by the package with:

```

dpkg -L name_of_package

```

Before installation, I'm not sure.  One thing you could do would be to download like:

```

sudo apt-get install -d name_of_package

```

That will download but not install the package.  The downloaded package should be in /var/cache/apt/archives.  You can navigate to there via nautilus and then double click the file to see what things it will install.  To then install it, it's a simple:

```

sudo apt-get install name_of_package

```

---

### Post by Asham on 2008-10-25
@em4r1z,
Yeah, I think adept in KDE also gave you that information but I can't find the same information in the 8.10 RC any more.

@vor,
Thanks! The procedure is a unnecessarily complicated but it will do, I guess. 


I'm thinking of requesting it as a wanted feature at brainstorm.ubuntu site and see what other people think about it.

---

