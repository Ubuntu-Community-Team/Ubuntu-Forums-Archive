---
title: "problem with installing programs in ubuntu"
date: 2007-06-12
forum: Programming Talk
---

### Post by diamantis13 on 2007-06-12
Hi everyone,

I recently started using Ubuntu and found some problems while trying to install some applications in the way I knew (configure, make, make install e.t.c.). Since I had no free time I gave up and used Synaptic instead. Everything was easily and fast installed, but now, a few months after passed I have to face the problem.
I think I have what is necessary:

[FONT="Courier New"] sudo apt-get install build-essential
 sudo apt-get install make
[/FONT] 
What test can I do in order to find more information on the source of my problem? I am running Ubuntu 6.10.
Thank you in advance

---

### Post by Hendrixski on 2007-06-12
Hey, it's really easy
you can use apt-cache search to look for whatever you need, then apt-get install to install it
you need to be superuser to install stuff... so just run it under sudo

If you try compiling something and it tells you that you're missing something it'll tell you

Here's the thing though.  Don't compile stuff from source.  Turn it into a .deb and THEN install it.  Because that way uninstalling it is really simple, and doesn't leave your system all cluttered.

If you want to do development, make sure you ahve the language you need... like for java just install the java6 from apt-get  or for python, get the one you need...  Qt can be a tough one to figure out... just apt-cache search for it.  :-)

hope that helps

---

### Post by diamantis13 on 2007-06-12
To be more specific, I am trying to install some perl modules [PP]("http://search.cpan.org/~smueller/PAR-Packer-0.975/lib/pp.pm") and [PAM]("http://search.cpan.org/~smueller/PAR-0.973/lib/PAR.pm")) and an application [sdist]("http://sourceforge.net/projects/sdist").
The only way I know to do this is either download and install from source or perl -MCPAN -e "install ...."
In either way I get an error message about make.
I just want to test them to see if I can package an application I am making, should I first make them as a .deb package? Do I have to do the same with everything else I wish to install?
Thank you very much.

---

### Post by Soybean on 2007-06-12
If you've installed build-essential (as you mentioned above), make is *supposed* to work, just like you're used to from other systems. If it's not working, it's because something went wrong, not because Ubuntu's trying to force you to always use .debs and aptitude. ;)

What is the error message you're getting?

---

### Post by diamantis13 on 2007-06-13
I managed to install PAR, but I have still problems with the rest.

1) sdist
[FONT="Courier New"]$ perl Makefile.PL 
Checking if your kit is complete...
Looks good
Can't install directory 'etc/sdist.conf' unless overwrite=1[/FONT]

2) for PP, I downloaded PAR-Packer-0.975.tar.gz from CPAN
did perl Makefile.PL and when I type make I get the following:

[FONT="Courier New"]make[1]: Entering directory `/home/bonobo/Desktop/PAR-Packer-0.975/myldr'
cc main.o my_par_pl.o  -s -Wl,-E  -L/usr/local/lib /usr/lib/perl/5.8.8/auto/DynaLoader/DynaLoader.a -L/usr/lib/perl/5.8/CORE -lperl -ldl -lm -lpthread -lc -lcrypt --output ./par
/usr/bin/ld: cannot find -lperl
collect2: ld returned 1 exit status
make[1]: *** [par] Error 1
make[1]: Leaving directory `/home/bonobo/Desktop/PAR-Packer-0.975/myldr'
make: *** [subdirs] Error 2
[/FONT]
and I do not know what is going wrong!:(

---

### Post by Soybean on 2007-06-13
Well, my perl experience is minimal, and I don't know anything about that first error. The second one looks more familiar, though.
> **diamantis13 said:**
> /usr/bin/ld: cannot find -lperl

Your linker is looking for a perl-related shared library that doesn't seem to be installed. I haven't used it myself, but I would guess that you need to install one or both of "libperl5.8" and "libperl-dev" using synaptic or aptitude, then try that one again.

---

### Post by sachill on 2007-06-13
Hi

I have a problem where when I try to login in as superuser on my personal computer by typing 'su', it rejects my administration password, saying "su: Authentication failure".  How can this be??  Only I use this PC and it is the same password I use to log in!!  Please help!!!:(

---

