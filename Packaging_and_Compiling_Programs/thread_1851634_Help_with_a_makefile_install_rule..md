---
title: "Help with a makefile install: rule."
date: 2011-09-28
forum: Packaging and Compiling Programs
---

### Post by MG&amp;TL on 2011-09-28
Right. (stupidly)-I've done this before, and know how much of a pain it can be- I volunteered to make a debian file out of someone's raw Java source code.

I had lots of help the previous time:

[http://ubuntuforums.org/showthread.php?t=1836028]("http://ubuntuforums.org/showthread.php?t=1836028")

And felt relatively well-equipped for the task. However: his source is a lot more than mine. The problem I have is that 

```
install
```

does not seem to have a --recursive or similiar option. Do I really have to catalogue EVERY single file in the (humungous) package?

So:

I have the following directory structure:

```
<package>
  <debian> (control files, etc. here)
  <src>
    <org>
      <lots of source code here>
  Makefile
  binaryfile
  graphic
  Javafile.jar
  system.properties

```

I've never programmed in Java, so it is a bit of an exercise.

I have the make: rule of the makefile figured out: I'm just struggling a bit with the install rule: how can I make it recursive; or is there a shortcut?

--directory treats filenames as directories, but will not install anything within said directories. I could use wildcards, but there is directories mixed in with source file and it throws a ```
***install: omitting directory xyz***
install failed.
```

Thanks for any help rendered. And to those who answered my older post, I'm sorry; one of these days I will get it. :)

---

### Post by MG&amp;TL on 2011-09-29
Never mind, I found a convenient way of doing it:

```
find -name "*" >> Makefile
vim Makefile
:%s/.\/src/$(DESTDIR)\/src/g
```

Thanks anyway.

---

### Post by SevenMachines on 2011-09-29
Bear in mind you could just use a 'cp' copy, which unlike 'install', does do recursive, you just need to check the permissions on files too. You could also generated install sources with 'find', think thats possible anyway although ive never tried it

---

### Post by MG&amp;TL on 2011-09-29
The original thread: bachstelze said not to use cp: can I? That would be way more convenient.

---

### Post by SevenMachines on 2011-09-29
'install' is much preferred to be sure, for source trees with lots of subdirectories I'd probably use Makefiles in each subdirectory and use 'install' in each of them. Actually, if things are that complicated I'd probably use a full build system like autotools, but thats another kettle of fish altogether! If your source tree is simple enough then you should get away with 'install' with pattern patching of some kind and one Makefile.

[EDIT] Just that 'cp' *can* be used if required, theres no law against it, its just not the best way but it's not a disaster either :*)

---

### Post by MG&amp;TL on 2011-09-29
I'm not against bending the rule if it means a one-statement install rule, rather than over 200.;)

---

### Post by MG&amp;TL on 2011-09-29
Errr....I used dh_make and it doesn't produce a orig.tar.gz, just .orig, which is fine until you run debuild:

```
dpkg-source: error: can't build with source format '3.0 (quilt)': no orig.tar file found
dpkg-buildpackage: error: dpkg-source -b passwordstore-0.2-stable gave error exit status 255
debuild: fatal error at line 1337:
dpkg-buildpackage -rfakeroot -D -us -uc failed

```

Any clues? Thanks, sevenmachines!

---

### Post by MG&amp;TL on 2011-09-29
Never mind. Got it with dh_make -f

---

