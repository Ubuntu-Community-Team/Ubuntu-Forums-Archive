---
title: "installing dev lib in home dir"
date: 2007-06-27
forum: Programming Talk
---

### Post by Houman on 2007-06-27
hi there;

I am using a Linux box but unfortunately i dont have a root account on it. 
The problem is that I need to get a few libraries (some algebra libraries) for use with a few applications im writing with C/C++. 

My question is, how would I go about doing this? can i just download a library into my home directory, and just do a "make" without doing a make install and just somehow use it from that directory? I remember in windows you could leave your lib/dll files anywhere you wanted as long as you made sure Visual Studio had the right path for the include headers and the lib files, is the same thign possible in Linux? or do they libraries have to be installed in only a certain number of directories for the program to be able to find them?

regards

Houman

---

### Post by Ramses de Norre on 2007-06-27
You can perfectly store them in your home dir as long as your compiler knows where to find them :) (and the administrator didn't set "noexec" on the home partition as some do)

---

### Post by meatpan on 2007-06-27
This is definitely possible, and many applications are getting better at allowing users to build and administer software from their own directories.

Here is the approach I take to building programs under my home dir.  No doubt there are better ways, but this has worked well for me over the years.

I keep a folder named 'opt' under my home directory.  This folder is the install home of all programs I build from source that I need to run locally.  Sometimes I build something because it is faster and more convenient than asking tech support to perform a system-wide install.  Other times I just want to experiment with a cool new program, in an isolated sandbox-like environment.

Under ~/opt is a folder for each app, and under each of those folder is a 'BUILD' directory.  The BUILD directory is where I unpack, compile, and test/validate the source code.  If you are using the gnu autoconf/make system (which means you ran './configure'), you can specifty the '--prefix' option.  The location you supply to this option is where the resulting libraries, config files, docs, etc... will be installed when you run 'make install'.

Here's a quick summary.  You have downloaded a program 'hello-1.2.tar.gz'

1. create folders  ~/opt/hello/BUILD
2. Unpack tarball in BUILD
3. Run './configure --prefix=/home/$(whoami)/opt/hello'
4. run 'make'
5. run 'make check' (if available.  sometimes called 'make test')
6. run 'make install'

Once make  finishes (successfully), you can reference and link the libs  in ~/opt/hello/lib via the typical compiler options.

---

### Post by Houman on 2007-06-28
hi there;

Thanks Ramses and thank you meatpan for the detailed instructions. I did just that and the prefix option did it for me. Also i specified the paths to the local dev libs in my makefile, everything is working great now :)

thanks again guys;


Houman

---

