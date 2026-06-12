---
title: "How to setup a Gnome/Nautilus development environment ?"
date: 2008-12-29
forum: Programming Talk
---

### Post by cudjoe on 2008-12-29
Hi all,

I am familiar with C and GTK and already hacked small softwares.

Many times I tried to setup a Nautilus development environment to patch or add new features. It always ended up with frustation and renunciation during compilation.

 
- The Gnome Developer Kit
[http://live.gnome.org/GnomeDeveloperKit](http://live.gnome.org/GnomeDeveloperKit)
I could not cook the nautilus recipe because of missing dependencies.

- jhbuild
[http://live.gnome.org/JhbuildOnUbuntu](http://live.gnome.org/JhbuildOnUbuntu)
This one went quite far, but could never go until the end neither.

I already talked to the Gnome hackers on IRC, and they were all using different aproaches...

What is your preferred method ? 
Should I insist with jhbuild and post details of compilation problems here ?


Thanks

---

### Post by cudjoe on 2008-12-30
Can somebody help to select the minimal subsets of jhbuild modules to develop on Nautilus ?


BTW I notice automake1.8 was not alvailable in Intrepid repositories...

---

### Post by m8n on 2009-01-20
First I'd download the latest release and try to build it using the regular autoconf tools: 

[FONT="Courier New"]
~/gnome/nautilus $ configure
...
~/gnome/nautilus $ make
...
[/FONT]

When needed install the package the builder requires.  Things like eel*-dev.deb and such might not be installed on your system.  Do so using the apt-get install command.

Then use the Ajnuta IDE (it is in the repo) and click New -> Project from existing sources.  Select the nautilus source directory and ready you are!

Happy coding!

---

### Post by cudjoe on 2009-01-21
Indeed, this would work in a regular project.

But Gnome or Nautilus have a lot of dependencies. Jhbuild was made with that objective.

---

### Post by bruce89 on 2009-01-21
I have a working jhbuild installation. Here's my ~/.jhbuildrc.

```

# -*- mode: python -*-

# edit this file to match your settings and copy it to ~/.jhbuildrc

# if you have a GNOME svn account, uncomment this line
#repos['svn.gnome.org'] = 'svn+ssh://user@svn.gnome.org/svn/'

# what module set should be used.  The default at the moment is 'gnome-2.26',
# but it can be any of the files in the modulesets directory, or even
# the URL of a module set file on a web server.
moduleset = 'gnome-2.26'

# A list of the modules to build.  Defaults to the Gnome Desktop and
# developer platform.
modules = [ 'meta-gnome-desktop' ]

# what directory should the source be checked out to?
checkoutroot = os.path.expanduser('~/Downloads/gnome2')

# the prefix to configure/install modules to (must have write access)
prefix = '/opt/gnome2'

# extra arguments to pass to all autogen.sh scripts
# to speed up builds of gnome2, try '--disable-static --disable-gtk-doc'
# it is also possible to set CFLAGS this way, 'CFLAGS="-g -O2"' for example
#autogenargs=''

# On SMP systems you may use something like this to improve compilation time:
# be aware that not all modules compile correctly with make -j2
# makeargs = '-j2'

# a alternative install program to use.
# The included install-check program won't update timestamps if the
# header hasn't changed
os.environ['INSTALL'] = os.path.expanduser('~/bin/install-check')

# skip some modules
skip = [ 'mozilla' ]

# extra flags for modules
#module_autogenargs['gtk+'] = autogenargs + ' --enable-gtk-doc '
#module_autogenargs['anjuta'] = autogenargs + ' --disable-plugin-devhelp '

```

Those last few lines are my custom arguments, but they might be useful to see.

I just checked out jhbuild into my gnome checkout directory (~/Downloads/gnome2/), made the output directory (/opt/gnome2/), changed its owner to me (sudo chown bruce:bruce /opt/gnome2), and I was halfway there.

You should create a new user to run the new programs in unless you want your settings to be messed up (version issues perhaps). This means you have to checkout jhbuild in that user's home directory as well.

I'd be happy to help if you need any specific advice at any point.

---

