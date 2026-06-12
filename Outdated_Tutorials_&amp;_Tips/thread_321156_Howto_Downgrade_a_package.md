---
title: "Howto: Downgrade a package"
date: 2006-12-18
forum: Outdated Tutorials &amp; Tips
---

### Post by Bigglez on 2006-12-18
Greetings.
I had one heck of a time today, trying to install something using apt-get while it complained * about "broken" packages and "unmet" dependencies. I thought I would share my experience and solution with you.
* To confess: I installed fancy 3d desktop stuff from repositories that were covered in "warning" signs, so it's all my fault anyway. :)

**Legend**
I will use [ ] brackets to show commands typed on the command-line.

**The situation**
I wanted to install a package. Let's call it **PackX** for argument's sake.
When I tried: [ sudo apt-get install PackX ] it came back and told me ( I'll use more example names ):```

The following packages have unmet dependencies:
  libAppA-dev: Depends: libAppA (= 6.4.1-0ubuntu8) but 6.5.1-cvs20060628 is installed.
Resolving dependencies...


```
So, I was trying to install **PackA,** but it needs **libAppA-dev** and that relies on **libAppA** - okay so far?
The problem is that libAppA is version 6.**5**.1.blah and the system *wants* version 6.**4**.1.blah ... we have to ***downgrade*** libAppA !

**The solution**
First we need to ensure that there *are* lower versions of libAppA. We use this:
[ apt-cache showpkg libAppA ]
And it will show a bunch of stuff, look towards the end for something like this:```

Provides:
6.5.1-cvs20060628 - libAppA
6.4.1-0ubuntu8 - libAppA

```
You should see the lower version there. If not, well, something else is going on; I advise panic.

Next we tell the system to install that package, but we will specify the lower version number, thus replacing the current version (the wrong one) with the older one:
[ sudo aptitude install libAppA**[SIZE="5"]=[/SIZE]**6.4.1-0ubuntu8 ]
Note the equals sign and then the version number we saw in the above output.

You should then see something like this:```

Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages will be DOWNGRADED:
  libappA
0 packages upgraded, 0 newly installed, 1 downgraded, 0 to remove and 0 not upgraded.
Need to get 223kB of archives. After unpacking 0B will be used.

blah blah blah ...


```

**The end**
After that has done, you should be able to go back to the start and [ sudo apt-get install PackX ]

I hope that helps someone out there in *buntu land.

/d

---

### Post by realflash on 2010-08-26
This also works using apt-get:

```
apt-get install pkg=version
```

---

