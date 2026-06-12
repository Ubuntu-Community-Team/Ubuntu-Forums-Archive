---
title: "Do libraries I use need to be installed on every computer?"
date: 2012-08-13
forum: Programming Talk
---

### Post by mishathegoat on 2012-08-13
Hey everyone,

Sorry in advance for this noobish question. 

Let's say I install the C++ boost libraries (or whatever library) and use them in an application I'm developing. I compile the code and distribute it online (or wherever). Would computers running my application also need to have the boost libraries installed?

Thanks

---

### Post by dwhitney67 on 2012-08-13
Only if you link your application with the shared-object version of a particular library.  If you link with the static library, then you would not.

Shared-object libraries typically have a .so extension; static libraries have a .a extension (the 'a' denotes 'archive').

---

### Post by mishathegoat on 2012-08-13
That's actually incredibly helpful, thanks a bunch!

---

### Post by dwhitney67 on 2012-08-13
> **mishathegoat said:**
> That's actually incredibly helpful, thanks a bunch!

Things to keep in mind...

1) Not every library has a static version; you may have a shared-object version, but not a static version.

2) Linking a static library to your application will increase its "footprint"; in other words, the byte-size of the application will be larger than if merely linking against shared-object libraries.  You probably will not see any difference with trivial/simple applications.

---

### Post by mishathegoat on 2012-08-13
Hmmm, I see. Well, I would think the 'footprint' would be worth the extra size, this way the user could simply run the application without having to download any additional files. I don't normally (in Windows) download and run an application, only to have to go back online to download additional libraries.

---

### Post by trent.josephsen on 2012-08-13
> **mishathegoat said:**
> I don't normally (in Windows) download and run an application, only to have to go back online to download additional libraries.

That may be true for Windows, but in Ubuntu you do that all the time. Well, except for the "and run" part. It looks like this:

```
sudo apt-get install <package>
```

apt-get automatically looks up the dependencies for <package>, including any runtime shared libraries it uses, and installs them for you. That's the primary advantage of using package managers.

Even in Windows, many application installers automatically download and install some dependencies if they're not already available. DirectX comes to mind, although that's a terrible example because DirectX lives in its own little world of DLL hell.

I'd advise going the dynamic (shared-object) route unless you have a compelling reason to link statically.

---

### Post by mishathegoat on 2012-08-13
Thanks, trent.josephsen

I already understood this was the case with most package managers. What makes these package managers so great, is the automatic resolving of dependencies.. But you're  right, Windows doesn't work this way. I guess it would've been helpful to mention I prefer to make my applications cross-platform.

I'm branching away from Java and I'd like to still easily "write once, run everywhere." I'm sure users wouldn't mind having a version of my application for each major OS

Also, more people are likely to have DirectX, Flash, etc installed than some of the other *incredibly-obscure* packages I've seen some Linux applications require.

Sorry for getting slightly off-topic, heh heh.

---

### Post by durdenstationer on 2012-08-13
Then just statically link when you build for Windows and dynamically link when building for Linux.

---

### Post by trent.josephsen on 2012-08-13
> **durdenstationer said:**
> Then just statically link when you build for Windows and dynamically link when building for Linux.

This is a viable and common solution.

---

### Post by mishathegoat on 2012-08-13
Thanks guys, I'll keep that mind!

---

### Post by satsujinka on 2012-08-13
Personally, I'd just as soon you statically link everywhere. Dynamic linking is a plague.

EDIT: I should probably mention I meant plague in a very metaphorical sense. Using dynamic linking encourages other people to do so (and to create dlls which in turn makes dynamic linking more attractive.) However, dynamic linking does have actual harmful effects. Most of them are negligible and/or solved by some system we currently have. I'd just as soon people use static linking because the world would be simpler for it... but it's not really necessary that it happen.

If you'd like [http://harmful.cat-v.org/software/dynamic-linking/](http://harmful.cat-v.org/software/dynamic-linking/)

---

### Post by trent.josephsen on 2012-08-13
Post was hastily written and not nice. Please ignore.

---

### Post by vexorian on 2012-08-13
dynamic linking works well, and allows users to need less download space and have less redundant code. It also happens that this way a distribution can modify a library to work better with it and your program will use the library installed instead of something you are bringing with it. It is also the way things are done in Linux/GNU systems.

---

### Post by satsujinka on 2012-08-13
> **vexorian said:**
> dynamic linking works well, and allows users to need less download space and have less redundant code. It also happens that this way a distribution can modify a library to work better with it and your program will use the library installed instead of something you are bringing with it. It is also the way things are done in Linux/GNU systems.

Dynamic linking **usually** works well, however, it can and does screw things up. For example, if a library changes the way a function is called (or the way it returns values.) Dynamic linking means that your program will no longer run (correctly) without an edit + recompile (assuming you have the source and assuming you have the ability to make the edit.) If you'd statically linked your program this wouldn't have been an issue (because the version of the code you're using is fixed at compile time.)

Statically linked binaries don't require significantly more space or bandwidth to download. In fact, as the number of libraries used increases the chances improve that static linking will **reduce** the necessary bandwidth + space.

There's no need for a distro to modify a statically linked program. If you're binary compatible everything should "just work." There are exceptions to this, some of which are introduced by platforms that expect dynamic linking and of course you have IPC issues.

Just because the Romans do it doesn't make it a good idea. Even if you are in Rome.

---

