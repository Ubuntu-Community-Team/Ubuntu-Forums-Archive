---
title: "[SOLVED] Install Perl module"
date: 2008-08-27
forum: Packaging and Compiling Programs
---

### Post by Nonno Bassotto on 2008-08-27
I'm not sure this is the right place to post. I need to run a [Perl script]("http://svn.gna.org/viewcvs/mpd-stats/trunk/") and the README says it requires the following modules:

```
- Audio::MPD
- Audio::MPD::Common
- File::HomeDir
- DBD::SQLite
```

I was able to install the first three adding the packages

```
libaudio-mpd-perl
libaudio-mpd-common-perl
libfile-homedir-perl
```

but there's no way I can get the last one. I tried adding

```

libdbd-sqlite3-perl
libdbd-sqlrelay-perl
libclass-dbi-perl
libclass-dbi-sqlite-perl
libcgi-session-perl
libdbd-sqlite3

```

but the script still couldn't run. When I launch I get
```

DBI connect('dbname=/home/andrea/.mpd-stats/mpd-stats','',...) failed: unable to open database file(1) at dbdimp.c line 94 at ./Extra/Scripts/MPD Stats/mpd-stats.pl line 28
Couldn't connect to database: unable to open database file(1) at dbdimp.c line 94 at ./Extra/Scripts/MPD Stats/mpd-stats.pl line 28.

```

So I went on [CPAN]("http://search.cpan.org/~msergeant/DBD-SQLite-1.14/lib/DBD/SQLite.pm") and searched for the DBD:SQLite module. It seems that this corresponds to the file lib/DBD/SQLite.pm so I [searched]("http://packages.ubuntu.com/search?searchon=contents&keywords=sqlite.pm&mode=exactfilename&suite=hardy&arch=any") packages.ubuntu.com for SQLite.pm. It seems that the package for me is libdbd-sqlite3-perl, but I already have that installed. Can anyone help me?

---

### Post by Nonno Bassotto on 2008-08-28
Solved, it was not a perl module problem. The script has some problems and couldn't create the ~/.mpd-stats directory. After creating the directory all went well. By the way, the right module was libdbd-sqlite3-perl.

---

