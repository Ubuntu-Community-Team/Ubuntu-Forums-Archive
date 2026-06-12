---
title: "[SOLVED] Compiling Fron Source"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by WorldTripping on 2008-06-03
Could someone just confirm how I would install this from source please. Is it something like this?

tar xvzf fsv-0.9.tar.gz
cd fsv-0.9
./configure
make
make install

Do I need to install any building tools before I can do this ?

---

### Post by sdennie on 2008-06-03
You'll probably have to:

```

sudo apt-get install build-essential

```

You'll also need to prefix "make install" with "sudo".  You may have other issues with dependencies as well but, that should get you going.  I'd also make sure the package you are trying to compile isn't already in the Ubuntu repos.

---

### Post by Cypher on 2008-06-03
Before you do that..do
```

sudo apt-get install build-essential checkinstall

```
Then follow that with
```

tar -zxvf fsv-0.9.tar.gz
cd fsv-0.9
./configure
make
sudo checkinstall

```
The last command will create a .DEB file from the package you just compiled. You can now safely install it using DPKG and remove it cleanly later on if you want..
```

sudo dpkg -i <package>.deb

```

---

### Post by sdennie on 2008-06-03
The checkinstall method is much better if it works.  Do that if possible.

---

### Post by WorldTripping on 2008-06-03
Cool,

Thanks for that.

I was getting errors on the './configure' bit, even though I had installed 'build-essential'.

I'll retry after getting 'checkinstall'.

And for anyone who is interested, 'fsv' is the file manager that was seen in Jurassic Park.

Link:[COLOR="DarkOrange"]_[http://fsv.sourceforge.net/]("http://fsv.sourceforge.net/")_[/COLOR]

Once again, thank you forums for the speedy response.

---

### Post by sdennie on 2008-06-03
checkinstall won't help with your ./configure problems.  You'll probably need to satisfy the dependencies that the package needs.

Also, are you talking about the "This is Unix.  I know this!" file manager when she apparently flies through a filesystem?  If so, that's hilarious.

---

### Post by Cypher on 2008-06-03
Haha..I remember that part of the movie and was quite amused by that...

Anyway..I'm going to take a stab in the dark and say that that ./configure is probably complaining about missing Mesa3d libraries. Post the result of you running the command and we can help further..

---

### Post by WorldTripping on 2008-06-03
Yep, that's the one.

From this thread:

[http://ubuntuforums.org/showthread.php?t=811209&page=2]("http://ubuntuforums.org/showthread.php?t=811209&page=2")

> **swoll1980 said:**
> [like this ]("fsv.sourceforge.net/")

I'll have to look at the dependency issues this evening.

Thanks.

---

### Post by Joeb454 on 2008-06-03
> **Cypher said:**
> 
The last command will create a .DEB file from the package you just compiled. You can now safely install it using DPKG and remove it cleanly later on if you want..
```

sudo dpkg -i <package>.deb

```

```
sudo checkinstall
``` Will also install the package, you would only need the .deb to remove it (this is where checkinstall is very useful). Which would be ```
sudo dpkg -r <package>
``` :)

---

### Post by WorldTripping on 2008-06-03
> **Joeb454 said:**
> ```
sudo checkinstall
``` Will also install the package, you would only need the .deb to remove it (this is where checkinstall is very useful). Which would be ```
sudo dpkg -r <package>
``` :)

That seems a bit easier than having to keep the makefile somewhere.

Cheers.

---

### Post by ibuclaw on 2008-06-03
I recommend that you set the install folder to your /usr/local directory, so the installation doesn't get mixed up with the main Ubuntu files.

```

./configure PREFIX=/usr/local/
make
sudo make install

```

Regards
Iain

---

### Post by WorldTripping on 2008-06-03
> **tinivole said:**
> I recommend that you set the install folder to your /usr/local directory, so the installation doesn't get mixed up with the main Ubuntu files.

```

./configure PREFIX=/usr/local/
make
sudo make install

```

Regards
Iain

Ah, OK, thanks.

I would never have considered doing this.

Cheers.

---

### Post by Joeb454 on 2008-06-03
I should note that it's a good idea to keep the .deb somewhere (I have ~/compiled for that). Just in case :)

---

### Post by WorldTripping on 2008-06-04
OK,

So here are the compile errors that I'm getting.

The missing dependency errors seem to be near the bottom of this log.

Can't figure this one out by myself !

> simon@laptop-dell:~/fsv-0.9$ ./configure
loading cache ./config.cache
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... yes
checking for working aclocal... found
checking for working autoconf... found
checking for working automake... found
checking for working autoheader... found
checking for working makeinfo... missing
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking how to run the C preprocessor... gcc -E
checking for ranlib... ranlib
checking for POSIXized ISC... no
checking for dirent.h that defines DIR... yes
checking for opendir in -ldir... no
checking for ANSI C header files... yes
checking whether time.h and sys/time.h may both be included... yes
checking for strings.h... yes
checking for sys/time.h... yes
checking for unistd.h... yes
checking for working const... yes
checking for mode_t... yes
checking for uid_t in sys/types.h... yes
checking for pid_t... yes
checking for size_t... yes
checking for comparison_fn_t... yes
checking for st_blocks in struct stat... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking for working alloca.h... yes
checking for alloca... yes
checking for working fnmatch... yes
checking for strftime... yes
checking for getcwd... yes
checking for gettimeofday... yes
checking for mktime... yes
checking for strcspn... yes
checking for strdup... yes
checking for strspn... yes
checking for strtod... yes
checking for strtoul... yes
checking for scandir... yes
checking for inline... inline
checking for off_t... yes
checking for unistd.h... (cached) yes
checking for getpagesize... yes
checking for working mmap... yes
checking for argz.h... yes
checking for limits.h... yes
checking for locale.h... yes
checking for nl_types.h... yes
checking for malloc.h... yes
checking for string.h... yes
checking for unistd.h... (cached) yes
checking for sys/param.h... yes
checking for getcwd... (cached) yes
checking for munmap... yes
checking for putenv... yes
checking for setenv... yes
checking for setlocale... yes
checking for strchr... yes
checking for strcasecmp... yes
checking for strdup... (cached) yes
checking for __argz_count... yes
checking for __argz_stringify... yes
checking for __argz_next... yes
checking for stpcpy... yes
checking for LC_MESSAGES... yes
checking whether NLS is requested... yes
checking whether included gettext is requested... no
checking for libintl.h... yes
checking for gettext in libc... yes
checking for msgfmt... no
checking whether catgets can be used... no
checking for msgfmt... (cached) no
checking for gmsgfmt... no
checking for xgettext... :
checking for gtk-config... no
checking for GTK - version >= 1.2.1... no
*** The gtk-config script installed by GTK could not be found
*** If GTK was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GTK_CONFIG environment variable to the
*** full path to gtk-config.
configure: error: Cannot find proper GTK+ version

Thanks.

---

### Post by sdennie on 2008-06-04
You may run into more of these problems but, this one can probably fixed with:

```

sudo apt-get install libgtk2.0-dev

```

---

### Post by WorldTripping on 2008-06-04
Cool, 

Thanks.

I'll try it in a bit.

---

### Post by sdennie on 2008-06-04
I find the easiest way to solve this sort of problem when configure complains about stuff is to go to System->Administration->Synaptic Package Manager and search for the thing you are missing.  You'll likely need to just install the -dev package.  If you are just compiling a custom package that already exists in the Ubuntu repos, this is a fantastic command:

```

sudo apt-get build-dep name_of_the_package

```

---

### Post by ramjet_1953 on 2008-06-04
Another thing that is often overlooked is that if you are "rolling your own" package, you will also need to download the .dev packages for many of the dependencies.
i.e. If the package you want to compile requires the [COLOR="Blue"]afflib[/COLOR] package, it will also almost certainly need the [COLOR="Blue"]afflib.dev[/COLOR] package.

Regards,
Roger :cool:

---

### Post by WorldTripping on 2008-06-05
> **vor said:**
> You may run into more of these problems but, this one can probably fixed with:

```

sudo apt-get install libgtk2.0-dev

```

Turns out that I needed libgtk1.2-dev due to an incompatability.

I'm now getting Mesa errors, even though I installed all of the relevant libraries.

This eye candy is taking up too much of my time, so I'm giving up.

Thanks for everyones help.

Cheers.

---

### Post by WorldTripping on 2008-06-11
For anyone interested this was resolved by adding;

```
gtkglarea
```

This site had the answer, and it also has a couple of other rather cool 3D file visualisers.

[http://w3.linux-magazine.com/issue/77/3D_File_Browsers.pdf]("http://w3.linux-magazine.com/issue/77/3D_File_Browsers.pdf")

---

