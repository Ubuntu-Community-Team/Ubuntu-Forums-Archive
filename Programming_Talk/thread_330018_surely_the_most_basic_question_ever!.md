---
title: "surely the most basic question ever!"
date: 2007-01-02
forum: Programming Talk
---

### Post by damianubuntu on 2007-01-02
Hi, and apologies for this incredibly simple question!

Believe it or not, I have looked for a while now, but cannot find how you execute a perl script!  I downloaded Gtkmp3burn to dump mp3 files onto audio cd, and have a perl script.  If I double click it, nothing happens, if I type it in a terminal: bash: command not found,  - what do I do with it!!!

SHould anyone happen to know - this is my third option, the first was to try mp3burn from the comand line, but I kept getting unrecognised file errors, and was unable to solve those, so I thought I would try a GUI. Second option was to try Xmp3burn, but first it required xlibs-dev which I eventually worked out, and installed, now it also wants Qt2.02, which seems to be part of KDE???  (I'm on Xubuntu 6.06)  So I gave up and tried this Gtk mp3burner instead, but I just have this Perl script.....

Thanks for any answers advice, or slaps around the head!

---

### Post by phossal on 2007-01-02
If you have a perl script named script.pl, then you execute via bash like so:
```

perl script.pl

```

---

### Post by damianubuntu on 2007-01-02
Thanks for the quick reply!

This is what I got, any suggestions?

damian@damian:~/Desktop/GtkMp3Burn-0.2$ perl gtkmp3burn
Can't locate Gtk.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at gtkmp3burn line 22.
BEGIN failed--compilation aborted at gtkmp3burn line 22.

---

### Post by phossal on 2007-01-02
Your perl script uses a module that isn't present on your system. Get it. Check out this site for help. [http://www.cyberciti.biz/faq/how-do-i-install-a-perl-module/](http://www.cyberciti.biz/faq/how-do-i-install-a-perl-module/)

---

### Post by damianubuntu on 2007-01-02
??

Sorry, you'll have to bear in mind that you're dealing wiht someone who should only be allowed to post in the beginner's forum, but felt that he ought to put this here!  How do I know what the module is (guess - gtk.pm?  gtk.pm@INC? )googling either doesn't immediately give any suggestions for where to download from, but I guess I can find that in the end.  What do I do with it when I download it?

Sorry if I'm asking really basic stuff here.....

---

### Post by phossal on 2007-01-02
Back before Python was the fad it is, perl was king. perl has personality. perl has culture. In fact, the perl culture was a precursor to the way of Ubuntu.

Anyway, back to your problem... 

You search for and download modules from: [http://cpan.org](http://cpan.org), the perl module repository.

Gtk: [http://search.cpan.org/~mlehmann/Gtk-Perl-0.7009/Gtk/objects.pod](http://search.cpan.org/~mlehmann/Gtk-Perl-0.7009/Gtk/objects.pod)
Here is how you install them: [http://cpan.org/modules/INSTALL.html](http://cpan.org/modules/INSTALL.html)

---

### Post by pmasiar on 2007-01-02
To make script react on double-click (or run when you type it's name), it must be (1) executable (2) have a "shebang" as first line, like "#!/usr/bin/perl" or wherever your perl lives.

---

### Post by damianubuntu on 2007-01-02
Thanks for the info.....I like your enthusiasm ;-)
I followed your first link and managed to get a CPAN shell (?) and run through the configuration stuff OK.  on trying to follow the 

cpan> install gtk.pm

I had a report that it couldn't install it, it didn't know what it was.

Further reading seems to suggest that all the modules are in the foo::bar format, but my origianl error message refers to Gtk.pm and other googled articles also refer to Gtk.pm

Looking at the search.cpan.org site you suggested leaves me with the impression that there are hundreds of GTK modules for different (Gnome!, am I even on the right path here given I'm using Xubuntu?) modules.

Thanks for the info, but still feeling a bit stuck, and not a little out of my depth, (not an unfamiliar feeling, most of my learning seems to come about on the basis of throwing enough incomprehensible mud onto a wall in the hope that some kind of interrelation and comprehension eventually occurs, but boy, are there some mis assumptions on the way!)

---

### Post by phossal on 2007-01-02
> **pmasiar said:**
> To make script react on double-click (or run when you type it's name), it must be (1) executable ...

The typical bash invocation works without a chmod call.
```

perl <name>.pl

```

Python does that too, doesn't it? Or do you chmod all your scripts? lol

---

### Post by Houman on 2007-01-02
Hi there;

You need the gtk module, but you dont have to use CPAN to install it, a lot of the perl modules are in the ubuntu repositories. To install the gtk module open a terminal and type this:

sudo aptitude install libgtk-perl

then run your script again, hopefully this will have resolved your module dependency problems.

take care and happy new year

Houman

---

### Post by damianubuntu on 2007-01-02
Houman:
what a ray of light and a lifebelt you are (if the two things can mix!) for briniging me in from my foundering depths to some kind of terra firma that I recognise - problem solved with apt-get, what a lovely simple solution, thanks a lot.

HNY to you too.

---

### Post by borris.morris on 2007-01-02
> **Houman said:**
> Hi there;

You need the gtk module, but you dont have to use CPAN to install it, a lot of the perl modules are in the ubuntu repositories. To install the gtk module open a terminal and type this:

sudo aptitude install libgtk-perl

then run your script again, hopefully this will have resolved your module dependency problems.

take care and happy new year

Houman

good job. wasn't sure which package it was. oh, and a happy new year to you too.

---

### Post by Houman on 2007-01-02
NO problem :D

for future, remember you can always search in the repository for the module before heading over CPAN. This is what i do to search for a module in the repositiries, lets say youre using the X modules, if you run the perl script without having installed the X module, youll get an error saying there is no X.pm file. In this case you will have to search the repositories for these:  "perl" and "lib" and "X". So in your case I searched for these three words, gtk, perl, and lib. 

And check to see which files are installed by a module (right click and say properties and installed files). This way you can be sure the X.pm file was installed. So in your case there was a libgtk2-perl package also, but i knew thats the wrong one because when i looked at the files its installing i saw "gtk2.pm" instead of "gtk.pm".

hopefully my post makes sense :D

take care

Houman

---

### Post by phossal on 2007-01-02
Downloading a module directly from cpan is always an option if you know how to do it.

Once you've downloaded the <module>.gz file, you simply extract it. And then you compile it, if you have to by:
```

sudo -s
perl Makefile.pl
make
make test

```

Why would you ever want to do that? Because you might browse CPAN's complete list of modules and find something useful - and then find it isn't available in the repositories.

---

### Post by pmasiar on 2007-01-02
> **phossal said:**
> Back before Python was the fad it is, perl was king. perl has personality. perl has culture. In fact, the perl culture was a precursor to the way of Ubuntu.

Phossal, for a smart guy you certainly are, you *really* like drive-by smear.

Certainly perl has own culture - I was regular on perlmonks for some time and I never completely liked the way newbies were ridiculed. Perl is more like debian. Python has own culture - which is much more like ubuntu culture, more friendly to newbies (as language is too). 

Python being fad? LOL! Google is biggest corporate supporter of python, you may as well say Google is just a fad to be more funny. Perl 6 is a flop, overcomplicated and nobody knows when will arrive if ever. I like to read Larry's talks etc, but you must admit he lacks language taste - he is very smart but his education as anthropologist sometimes takes over. Google pays Guido to release Python 3K in 2007.

---

### Post by aysiu on 2007-01-02
Let's keep it clean, folks. I've moved some of the fighting posts to [the Jail](http://ubuntuforums.org/showthread.php?t=330313). One of those posts was in blatant violation of the forum guidelines.

---

