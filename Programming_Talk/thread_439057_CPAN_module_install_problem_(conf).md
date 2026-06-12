---
title: "CPAN module install problem (conf?)"
date: 2007-05-10
forum: Programming Talk
---

### Post by paulshannon on 2007-05-10
I am trying to install Koha on Ubuntu 7.04 and am running into some problems installing some Perl modules that are required.

This is pretty much a clean install; nothing I think should effect Perl or CPAN has been added to the base install.

BASH results at: [http://paste.ubuntu-nl.org/20182/](http://paste.ubuntu-nl.org/20182/)

> Line 1: $ sudo cpan
CPAN throws some errors when it loads, but I did some googling and to fix those, it seems I need to install some things, which is the problem.

> Line 40: cpan[1]> o conf
Original conf (has failed similarly to this)

> Line 109: cpan[2]> o conf defaults
Reload defaults (I don't see a change

> Line 112: cpan[3]> o conf commit
Commit changes

> Line 115: cpan[4]> o conf
Reloaded Conf

> 
    applypatch         []
    auto_commit        [0]
    build_cache        [100]
    build_dir          [/root/.cpan/build]
    build_dir_reuse    [1]
    build_requires_install_policy [ask/yes]
    bzip2              [/bin/bzip2]
    cache_metadata     [1]
    check_sigs         [0]
    colorize_output    [0]
    commandnumber_in_prompt [1]
    cpan_home          [/root/.cpan]
    curl               []
    ftp                [/usr/bin/ftp]
    ftp_passive        [1]
    ftp_proxy          []
    getcwd             [cwd]
    gpg                [/usr/bin/gpg]
    gzip               [/bin/gzip]
    histfile           [/root/.cpan/histfile]
    histsize           [100]
    http_proxy         []
    inactivity_timeout [0]
    index_expire       [1]
    inhibit_startup_message [0]
    keep_source_where  [/root/.cpan/sources]
    lynx               [/usr/bin/lynx]
    make               [/usr/bin/make]
    make_arg           []
    make_install_arg   []
    make_install_make_command [/usr/bin/make]
    makepl_arg         []
    mbuild_arg         []
    mbuild_install_arg []
    mbuild_install_build_command [./Build]
    mbuildpl_arg       []
    ncftpget           [/usr/bin/ncftpget]
    no_proxy           []
    pager              [/usr/bin/less]
    patch              [/usr/bin/patch]
    prefer_installer   [EUMM]
    prefs_dir          [/root/.cpan/prefs]
    prerequisites_policy [ask]
    scan_cache         [atstart]
    shell              [/bin/bash]
    show_upload_date   [1]
    tar                [/bin/tar]
    term_is_latin      [1]
    term_ornaments     [1]
    test_report        [0]
    unzip              [/usr/bin/unzip]
    urllist           
        0 [[ftp://CPAN.mirror.rafal.ca/pub/CPAN/]](ftp://CPAN.mirror.rafal.ca/pub/CPAN/])
        1 [[ftp://cpan.sunsite.ualberta.ca/pub/CPAN/]](ftp://cpan.sunsite.ualberta.ca/pub/CPAN/])
        2 [[ftp://ftp.nrc.ca/pub/CPAN/]](ftp://ftp.nrc.ca/pub/CPAN/])
        3 [[ftp://ftp.yi.org/CPAN/]](ftp://ftp.yi.org/CPAN/])
        4 [[ftp://mirror.arcticnetwork.ca/pub/CPAN]](ftp://mirror.arcticnetwork.ca/pub/CPAN])
        5 [[ftp://theoryx5.uwinnipeg.ca/pub/CPAN/]](ftp://theoryx5.uwinnipeg.ca/pub/CPAN/])
    use_sqlite         [0]
    wget               [/usr/bin/wget]
    yaml_module        [YAML]


> Line: 185 cpan[5]> get Event
Event downloads correctly (save for a warning about SHA not being installed)

> Line 302: cpan[6]> make Event
Another SHA warning. Everything seems to start going funky around Line 410

```

 410: cp lib/Event/Watcher.pm blib/lib/Event/Watcher.pm
 411: cp lib/Event/type.pm blib/lib/Event/type.pm
 412: cp lib/Event/MakeMaker.pm blib/lib/Event/MakeMaker.pm
 413: /usr/bin/perl /usr/share/perl/5.8/ExtUtils/xsubpp  -typemap /usr/share/perl/5.8/ExtUtils/typemap -typemap ./lib/Event/typemap  Event.xs > Event.xsc && mv Event.xsc Event.c
cc -c  -Ic -Ilib/Event -D_REENTRANT -D_GNU_SOURCE -DTHREADS_HAVE_PIDS -DDEBIAN -fno-strict-aliasing -pipe -I/usr/local/include -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -O2   -DVERSION=\"1.08\" -DXS_VERSION=\"1.08\" -fPIC "-I/usr/lib/perl/5.8/CORE"   Event.c
 414: In file included from Event.xs:10:
 415: /usr/lib/perl/5.8/CORE/perl.h:420:24: error: sys/types.h: No such file or directory

```

Any ideas? Thanks for any help...

P

---

### Post by dafyre on 2007-05-11
I've begun to notice this problem as well.  Have you found a solution yet?

---

### Post by dafyre on 2007-05-11
Hey Paul:

Try this:

apt-get install libc6-dev

I found that on another thread here and it fixed my problem too! :)

See Ya!
~DaFyre

---

### Post by paulshannon on 2007-05-12
That seemed to fix the problem. I had to re- Get the module but it installed without incident.


Thanks for the help.

---

### Post by tr333 on 2007-05-13
installing the "build-essential" meta-package should install everything like that for you, including gcc, make and automake.

---

### Post by dafyre on 2007-05-14
Thanks, Tr333!

I got tired of having to load all the dev packages one at a time, lol.  (I've been loading Ubuntu a lot here lately! :O

See Ya!
~DaFyre

---

### Post by bo8ster on 2007-08-19
I am having trouble installing GD using /usr/bin/perl -MCPAN -e 'install GD' and it is not working (need it for bugzilla)
When installing it asks "Where is libgd installed? [/usr/lib] "
I cannot install it with apt-get, I do have libgba, is this the same?
Anyway the tar is extracted but the make fails giving heaps of error messages.

Any ideas?

/usr/bin/perl "-MExtUtils::MY" -e "MY->fixin(shift)" blib/script/bdf2gdfont.pl
cc -c  -I/usr/include -I/usr/include/gd -D_REENTRANT -D_GNU_SOURCE -DTHREADS_HAVE_PIDS -DDEBIAN -fno-strict-aliasing -pipe -
I/usr/local/include -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -O2   -DVERSION=\"2.35\" -DXS_VERSION=\"2.35\" -fPIC "-I/usr/
lib/perl/5.8/CORE"  -DHAVE_JPEG -DHAVE_FT -DHAVE_XPM -DHAVE_GIF -DHAVE_PNG -DHAVE_ANIMGIF GD.c
  /usr/bin/make -j3 -- NOT OK
Running make test
  Can't test without successful make
Running make install
  make had returned bad status, install seems impossible
GD.xs:1263: error: expected &#8216;;&#8217; before &#8216;gd_cloneDim&#8217;
GD.xs:1267: error: invalid lvalue in assignment
GD.xs:1267: error: invalid lvalue in assignment
GD.xs:1270: error: &#8216;RETVAL&#8217; undeclared (first use in this function)
GD.c: In function &#8216;XS_GD__Image_copyRotate270&#8217;:
GD.c:2037: error: &#8216;GD__Image&#8217; undeclared (first use in this function)
....and so on...

---

### Post by rowdog on 2007-08-19
bo8ster,

libgda is not the same as libgd. You can install the library and the perl module with 

sudo aptitude install libgd-gd2-perl

--rowdog

---

### Post by bo8ster on 2007-09-26
Thanks for that rowdog

I found that both libc6-dev and libgd-gd2-perl are needed to get GD running.

Note, I have also tried this in Centos and libc6-dev will does not work for some reason. I used "yum install gd-devel" instead and GD ran fine.

---

