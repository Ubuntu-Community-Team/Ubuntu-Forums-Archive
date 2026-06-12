---
title: "compiling Synfig"
date: 2006-01-10
forum: Programming Talk
---

### Post by viscount on 2006-01-10
This forum interface really annoys me because
it just doesnt work at times</offtopic-rant>

I would like to get synfig compiled from source
however it seems the build scripts require automake-1.6
but since Im on breezy and dont intent to upgrade until
dapper is actually released (and am not even sure
if dapper will have automake-1.6 by default)
was wondering what people suggest that I do?

Check out line 6 of the bootstrap output to see the problem.

```

svn co http://svn.voria.com/code/ETL/trunk/ ETL
cd ETL
$ ./bootstrap
bootstrap: Prepairing build environment for ETL-0.04.07...
bootstrap: Creating temporary file...
bootstrap: Using autoconf (GNU Autoconf) 2.59
bootstrap: Using automake (GNU automake) 1.4-p6
bootstrap: warning: Unexpected version of GNU Automake (expected 1.6)
bootstrap: warning: *** Bootstrap process may fail!
bootstrap: Creating doxygen.cfg...
bootstrap: Creating pkgconfig.pc...
bootstrap: Creating project.spec...
bootstrap: Renaming pkgconfig.pc to ETL.pc.in...
bootstrap: Renaming project.spec to ETL-0.04.07.spec...
bootstrap: Finishing up ETL-0.04.07.spec...
bootstrap: Creating configure.in from configure.ac...
bootstrap: Setting up build environment...
+ aclocal -I /home/viscount/work/synfig/ETL/config
+ autoheader
+ autoconf -o configure
+ automake --foreign --add-missing --copy --include-deps
automake: configure.in: installing `config/install-sh'
automake: configure.in: installing `config/mkinstalldirs'
automake: configure.in: installing `config/missing'
automake: configure.in: installing `config/config.guess'
automake: configure.in: installing `config/config.sub'
test/Makefile.am:23: invalid unused variable name: `value_SOURCES'
test/Makefile.am:21: invalid unused variable name: `spline_SOURCES'
+ set +x
bootstrap: Failure.
bootstrap: Cleaning up...

```

---

### Post by ape on 2006-01-10
Actually, automake 1.6 is already available on Breezy.  Just install the automake1.6 package.

---

### Post by viscount on 2006-01-11
[QUOTE=ape]Actually, automake 1.6 is already available on Breezy.  Just install the automake1.6 package.[/QUOTE]


Hmm.. thanks for that ape!
I've tried to rebuild however the bootstrap script for ETL does not
find automake1.6 and instead finds automake1.4-p6 and dies.

Is there something I can do so my system will start using 1.6?
I dont want to have to uninstall 1.4p6 because there are probably other apps
that need it to build or at least think that they do and removing it would make things messy.

..or would it? Not really sure.

---

### Post by ape on 2006-01-11
execute `sudo update-alternatives --config automake`

this will give you a list of the available automake versions on your box and what you want /usr/bin/automake to actually point to.  The other option would be to modify the Synfig automake script to look for automake1.6 rather than just automake.

Good luck.

---

### Post by viscount on 2006-01-11
Thanks again ape! :D 

However its proving to be a real pain, I guess automake version
was not the issue at all. 

test/Makefile.am:21: invalid unused variable name: `spline_SOURCES'
test/Makefile.am:23: invalid unused variable name: `value_SOURCES'
+ set +x
bootstrap: Failure.
bootstrap: Cleaning up...

---

### Post by theos on 2006-01-12
I compiled synfig without problems
I just untarred the archives and did a ./configure && make && sudo make install for all 3 packages.
for synfigstudio, you need to install a patch for gtkmm-2.8. You can find this patch here: [http://aur.archlinux.org/packages/synfigstudio/synfigstudio/synfigstudio-0.61.03-gtkmm-2.8.patch](http://aur.archlinux.org/packages/synfigstudio/synfigstudio/synfigstudio-0.61.03-gtkmm-2.8.patch)
Since gtkmm-2.8 the Gtk::Window::present function is overloaded. This patch just replaces some calls to sigc::mem_fun with sigc::mem_fun0.

Just install the patch with:
~/src/synfigstudio-0.61.03 $ patch -p1 < ~/synfigstudio-0.61.03-gtkmm-2.8.patch

If you want to use the bootstrap ( I used it for the svn-version), you can insert the following lines in bootstrap:
AUTOCONF=autoconf2.50
AUTOMAKE=automake-1.6
ACLOCAL=aclocal-1.6
AUTOHEADER=autoheader2.50

good luck

---

### Post by viscount on 2006-01-13
omg! Welcome to the forums Theos!

In hind sight I'm not really even sure why I was
trying to get the subversion copy to compile..
The tarballs worked, and I used the patch.
So far it runs, not sure how well it runs because I just finished 
compiling and starting it up for the first time.

Thanks again :)

EDIT: yep, did the knightrider thing from the wiki, pretty cool :D

Very happy now, new toyz, yay!

---

### Post by jr.gotti on 2006-02-19
When trying to compile synfigcore, i get this error:

```
/usr/local/include/ETL/_surface.h:277: error: no matching function for call to 'min(int&, long int)'
make[3]: *** [libsynfig_la-layer_shape.lo] Error 1
make[3]: Leaving directory `/home/jason/downloads/synfig-0.61.04/src/synfig'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/jason/downloads/synfig-0.61.04/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/jason/downloads/synfig-0.61.04'
make: *** [all] Error 2

```

anyone know how i can fix this? please? lol

thanks,
Gotti

---

### Post by kperkins on 2006-02-19
Did you install ETL first?

---

### Post by jr.gotti on 2006-02-19
yessir.

---

### Post by brianprogrammer on 2006-08-02
I know this thread is a little old, but I am also having trouble compiling synfig.

I installed etl by using sudo apt-get install etl (and it installed something)

Then I installed synfig by downloading the tarball and doing ./configure
make
make install

That appeared to work fine and without errors.

Then when I came to the synfig studio, I ran accross some problems. First I did ./configure
make
And when i did: make install ....I ran into some issues. It gave me the following error: "/usr/bin/ld: cannot find -lSM"

Thanks in advance for the help,
Brian

---

### Post by theos on 2006-08-02
It looks like you are missing a library
you can try to install it with 
apt-get install libsm-dev

---

