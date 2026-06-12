---
title: "Help Adding brand new packages to a ppa"
date: 2009-08-30
forum: Packaging and Compiling Programs
---

### Post by brennydoogles on 2009-08-30
Hey all, I am trying to set up a ppa with a few useful packages in it. All of the programs that I need to add are programs that are not compiled... either bash scripts or Java based apps launched via bash. Looking at the documentation on launchpad however, it seems that the instructions are geared toward compiled programs, and assume that the user is very familiar with several files that don't exist in my projects. I already have .debs that I have created for these programs... is there an easy way to just upload these .debs?

---

### Post by brennydoogles on 2009-08-31
Polite bump?

---

### Post by _sluimers_ on 2009-09-01
[EDIT] Oh wait, you want to add bash scripts and Java based apps launched via bash. I remember reading you STILL have to something very similair. So try to use debuild on them as it generates the files you need to upload to your PPA.
[/EDIT]

I'm pretty much a ppa newbie as well, though I have managed to have PPA accept my application.

(I came here as I have a question myself. I'm unable to tell PPA's packager to package my application into the package, leaving my repository package empty except for a changelog file)

As far as I know is that they are not satisfied with debian packages and instead want the source code and several file that tell them how to package it.

In order to do this you will need to use the following commands:

dh_make (although I managed to avoid using dh_make because I kept getting my source code rejected, as you need to remove and edit a couple of files after you've done this)
debuild -S (if you find out what -sa means please explain it to me.. I've seen it used in a youtube example, I also use -k<my key>)
and dput <ppa name> <app name>_<app version>_source.changes

This is how I do it. Well, I made a scons file that does it for me so when I type scons my app gets uploaded to the PPA.

---

### Post by Brandon Williams on 2009-09-01
Here is a _very_ brief rundown of what's required to make a debian source package that can be uploaded to launchpad. For more information about the steps involved, look [here](https://wiki.ubuntu.com/PackagingGuide/Complete).

First, you need a Makefile that will build your program from source (this is not necessary for precompiled java and scripts ... anything that is run via an interpreter). Your Makefile should include a clean target that will clean up any files that were compiled from source, and it should include an install target that will install all of the necessary files to the right places in the file system. Here is a very simple example:
```
hello-world: hello-world.o

install: hello-world
	install hello-world $(DESTDIR)/usr/bin

clean:
	rm -f hello-world hello-world.o
```
This idea is that if you were to run 'make install' in the directory containing the Makefile, all necessary compilation would be performed and all necessary files would be installed to the correct locations. Note that the installation target begins with $(DESTDIR). This is necessary in order to ensure that files can be installed to the right locations when the package is built.

Next, make sure that the base directory for your source tree is named correctly. It should be named <packagename>-<version> (e.g. helloworld-0.1). Then, create a ta ball of the source tree in the same directory that contains the bas directory of your source tree. The tarball should be named <packagename>_<version>.orig.tar.gz (e.g. tar zcf helloworld_0.1.orig.tar.gz).

Next, we have to prepare the debian files. cd back into the base directory of your source tree and run the following command: 'dh_make -e <your email address>'. This will create a directory called debian with all of the basic template files in it. You can probably 'rm -f debian/*.{ex,EX}', since you won't need any of those files in your first pass. You will have to edit the following files: changelog, control, copyright, and dirs. The dirs file should create a listing of all directories that you will be installing files into. All of the rest of the files give you hints about the expected content.

After editing all of those files, you can now attempt to build the binary package. Run 'debuild' from the base directory of your source tree. This will perform any necessary compilation, install the files to a temporary directory tree (you can find it under debian/<packagename>/), and create the debian package for your program. After it's done, you can verify that it worked correctly by running 'dpkg -c <debianfile>' (e.g. dpkg -c ../helloworld_0.1-1_i386.build) and verifying that the file listing includes all the files you expect to see.

Finally, after you know that everything is working to create binary packages, build the source package with 'debuild -S -sa'. This will create all the files that you need to have in order to upload to launchpad.

---

### Post by _sluimers_ on 2009-09-01
What does the -sa stand for in debuild -S -sa?

---

### Post by Brandon Williams on 2009-09-01
You can get information about the arguments to debuild -S can be found in the man page for dpkg-buildpackage. The -sa argument indicates that the original source should always be included, not just in version with 0 or 1 as the debian part of the version number.

---

### Post by brennydoogles on 2009-09-02
I'm getting a strange error when running dh_make:
```

dh_make -e <myemail@test.com>
bash: syntax error near unexpected token `newline'

```

Since I already have a DEBIAN/ directory with a control file, what would I need to put in the other files?

---

### Post by Brandon Williams on 2009-09-02
You didn't put the '<' and '>' characters around your e-mail address on the command line, did you? That's the most likely explanation for the bash syntax error message you're seeing.

For future reference, when someone specifies a command line argument as a tag with '<' and '>', they do not intend for you to include those two characters on the command line. Instead, replace the whole tag with the described argument. In this particular case, that would mean that you would enter:
```
dh_make -e myemail@test.com
```

---

### Post by _sluimers_ on 2009-09-02
Don't use greater/smaller than signs. They're used in bash for I/O. It's just a code convention in HOWTO's and manuals to highlight that you're not supposed to put in that piece of text literally. 
```

dh_make -n -e brennydoogles@test.com

```

Actually you don't really need dh_make, as you can make the files manually (or with a script which is what I do), but it gives you a good example of the files that you need, which are:

changelog
compat
control
copyright
docs
rules

Since I'm a beginner as well. I'm not sure if this is the minimum what is needed, but at the very least you need a rules and control file.

---

### Post by Brandon Williams on 2009-09-02
> **brennydoogles said:**
> Since I already have a DEBIAN/ directory with a control file, what would I need to put in the other files?

I forgot to respond to this part in my previous e-mail ... 

I recommend that you move your existing DEBIAN directory out of your base source directory and start from scratch with the files generated by dh_make. One reason for this, for example, is that your existing control file probably doesn't have the necessary section for generate a source package, and if it does, it's still probably not one that you've tested.

---

