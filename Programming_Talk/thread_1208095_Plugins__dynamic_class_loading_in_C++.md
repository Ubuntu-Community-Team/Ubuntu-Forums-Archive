---
title: "Plugins / dynamic class loading in C++"
date: 2009-07-08
forum: Programming Talk
---

### Post by stair314 on 2009-07-08
Does anyone have any recommendations for making a c++ program that can use "plugins"? By a plugin, I mean I would like to be able to define a base class and let 3rd party developers write subclasses of it that my program can load out of a file and use.
I've looked into ways of doing this and it looks like I could write something myself with dlopen/dlsym, or I could use a library like Loki, "C++ Dynamic Class Loader", or libfactory++. Does anyone have any experience with these, or advice on which way would be best to do it?
Thanks!

---

### Post by dwhitney67 on 2009-07-08
I've attached an example program that loads a DLL.

To build the DLL and the test program, run this command within the dlopen directory that is created after you un-tar the attached file:
```

make

```

To run the app:
```

./dltest

```

---

### Post by stair314 on 2009-07-09
Thanks dwhitney. I'm looking for something for loading C++ classes (not just C functions) conveniently.

Do you think my best bet is to just roll my own following this tutorial?

[http://www.linuxjournal.com/article/3687]("http://www.linuxjournal.com/article/3687")

---

### Post by issih on 2009-07-09
Now I've only skimmed that article very loosely, but it seems like an awful lot of complication to me.

Is there some reason why you couldn't just ship all the seperately compiled files for your main program in one directory, say "main", and all extra .o files in a "plugins" directory. 

launch the program from a little script which relinks the program when the contents of the plugins directory changes (e.g. keep a hold of the latest timestamp for the files in the plugins directory, and relink if theres a newer one in there), that will give you the ability to extend the program without needing to recompile, merely relinking.

You'd need to ship the linker too I guess, but that seems less painful and restrictive to me at first glance, but maybe you absolutely must have live loading to allow plugins to be loaded at runtime.

Anyway I'll stop whittering now.

---

### Post by stair314 on 2009-07-09
This is for a machine learning / computer vision research library. The basic idea is that it provides a common interface for machine learning / computer vision algorithms to run on a few different kinds of data, but the end users will probably be using a lot of algorithms they developed themselves. I'd like for people to be able to install it to /usr/local/lib or used a shared install of the library on the network, but still be able to load their research code as plugins, so that kind of precludes re-linking it every time an individual user updates one of their plugins.

---

### Post by Zugzwang on 2009-07-09
> **stair314 said:**
> This is for a machine learning / computer vision research library. The basic idea is that it provides a common interface for machine learning / computer vision algorithms to run on a few different kinds of data, but the end users will probably be using a lot of algorithms they developed themselves. I'd like for people to be able to install it to /usr/local/lib or used a shared install of the library on the network, but still be able to load their research code as plugins, so that kind of precludes re-linking it every time an individual user updates one of their plugins.

But where's the need for dynamic linking here? The application using a plug-in can simply include the source code of the plug-in in its project and link against the library itself the usual way such that it is loaded when the program starts. Nothing dynamic here.

---

### Post by stair314 on 2009-07-09
Sorry, left out an important detail. The library also includes executables for training and evaluating different algorithms. These would ideally go in /usr/local/bin or possibly in a shared network installation.
Right now, people have to make their own local copies of those executables and patch them to include their 3rd party classes, which is a bit of a pain.

---

### Post by Zugzwang on 2009-07-09
> **stair314 said:**
> Sorry, left out an important detail. The library also includes executables for training and evaluating different algorithms. These would ideally go in /usr/local/bin or possibly in a shared network installation.
Right now, people have to make their own local copies of those executables and patch them to include their 3rd party classes, which is a bit of a pain.

You could put most of the code of the executable into a library as well and add some macros to instantiate the application with a custom set of plugins. Then the students could write their plugins, add 5 lines of code for the main application and they are done.

---

### Post by issih on 2009-07-09
Again..just have the helper apps be called by a script, have that script look for plugins in the users home directory (probably in a dot file somewhere e.g. ".myapp/plugins") using ~ in the script so it will link to the current users plugins.

If there are any new plugins in the directory relink the program against the plugins and output the program to the same local .directory.

Once any relinking is done have the script load the version in the users home directory if one exists, and load the generic one otherwise.

all done.

If you want to get fancy you can have a global plugins directory in /etc somewhere which is linked to for all users, and separate local ones for each user under their home directories. This will enable a base site load of plugins, that all users get by default and then any extra customisation beyond that is local.

Dynamic loading just isn't needed.

Hope that helps

---

### Post by stair314 on 2009-07-09
I know it's not strictly needed, but I'm trying to make this a fairly slick and professional library. Ideally someone would be able to read a journal article, get interested in trying out the algorithm, and then if the author releases their code for this library, anyone who has read the paper could just download the plugin and run it. Firefox doesn't require you to use g++/ld to install a plugin, so why should this?

---

### Post by issih on 2009-07-09
Well, its up to you, but I'd say that this article:

[http://www.ddj.com/cpp/184401900](http://www.ddj.com/cpp/184401900)

has done more of the donkey work for you if you do choose to go down this route

Hope that helps

---

