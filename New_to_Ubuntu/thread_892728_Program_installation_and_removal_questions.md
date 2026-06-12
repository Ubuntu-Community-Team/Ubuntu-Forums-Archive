---
title: "Program installation and removal questions"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by goldenbough on 2008-08-17
I just installed ImageMagick and would like to remove it entirely and reinstall.  The instruction files says:

 * Remove everything in the build directory created by 'configure' and 'make'.
    This is useful if you want to start over from scratch.

        make distclean

I assume that I run
cd ImageMagick-6.4.2
make distclean

This give the error: make: *** No rule to make target `distclean'.  Stop.


Then later when I install it again I want to put it in a specific directory, usr/local/lib.  I don't understand how to format it in the installation.  It says:


If you are willing to accept configure's default options, and build from
within the source directory, type:

    ./configure

and watch the configure script output to verify that it finds everything
that you think it should.  If it does not, then adjust your environment
so that it does.

By default,

    make install

will install the package's files in `/usr/local/bin', `/usr/local/lib', etc..
You can specify an installation prefix other than `/usr/local' by giving
`configure' the option `--prefix=PATH'.  This is valuable in case you don't
have privileges to install under the default paths or if you want to install
in the system directories instead.


so I assume it would be ./configure the path.  But how do I write this out?
I don't understand the --prefix=PATH thing.

---

### Post by meanburrito920 on 2008-08-18
Did you install this package from source, or from a repository?

---

### Post by nicedude on 2008-08-18
Ok you obviously installed this from source, so go back into the source directory and try "sudo make uninstall" as that is the common make file uninstallation command. sudo make distclean only strips the source of any kernel specific changes and must be done if you update the kernel and want to install again from that source ( first you would clean it so anything that might be different do to a new kernel version will be undone and then you must use make again to rebuild )

You can always look in the makefile ( it is just a textfile ) and see what are the various options. I always do that now since some program developers are so lazy they don't have uninstall commands just install.

But try "sudo make uninstall" and see if that doesn't just do it for you.

Goodluck

---

### Post by meanburrito920 on 2008-08-18
Yeah... I guess I did ask a stupid question...

---

### Post by hyper_ch on 2008-08-18
or you could use "checkinstall" install of "sudo make install" when you compile from source. Checkinstall will create a .deb file. If you then run the .deb file you can then remove it with synaptic/adept/apt-get/aptitude...

---

### Post by nicedude on 2008-08-18
Hey hyper_ch does checkinstall have to be an option in the makefile or is that a separate app that does the Deb creation for you ?

---

### Post by hyper_ch on 2008-08-18
it's a seperate app.

---

### Post by mcduck on 2008-08-18
Since nobody has mentioned ithis yet, Imagemagick is in Ubuntu's repositories and can be installed with Ubuntu's own package management tools. So there's no need to compile it from source code..

---

### Post by nicedude on 2008-08-18
He might just want a newer version than the one in the repositories.

And thanks hyper-ch as I think I will start using that myself, got burned once on a makefile with no uninstall and didn't like it :-)

---

### Post by hyper_ch on 2008-08-18
checkinstall isn't the "proper" way to create .debs and distribute them... but for own personal use it should be sufficient.

---

