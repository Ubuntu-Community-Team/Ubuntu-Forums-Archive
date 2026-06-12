---
title: "Problem installing Perl modules"
date: 2007-05-05
forum: Programming Talk
---

### Post by MitchCanuk on 2007-05-05
Hello,

I'm trying to install the Perl module Mail::Mailer but am getting a make error. Here is what I get;

[FONT="System"]:
:
Checking for IO::Handle...ok
Checking if your kit is complete...
Looks good
Writing Makefile for Mail
    -- NOT OK
Running make test
  Can't test without successful make
Running make install
  make had returned bad status, install seems impossible[/FONT]

I'm new to Linux and have just installed Ubuntu on my machine. This is the first time I try to run a Perl script on this machine.

Any ideas what might be missing or incorrectly configured?

Thanks,
Mitch

---

### Post by phossal on 2007-05-06
Probably your CPAN configuration. We've all been through it. ;) As a simple test, you can try using *sudo cpan*, in case it's a permissions error. But, when that doesn't work, open cpan, type *o conf*, and post the output. If you see fixable configuration errors, don't forget the *commit* command to save them.

---

### Post by MitchCanuk on 2007-05-06
Hello,

Thanks for your reply Phossal! You are right, I had omitted "sudo", unfortunately including it didn't change anything. I will include the output of "o conf" below but first I have a couple of questions.

Perl bundles can be installed using "aptitude". I've guessed that Mail::Mailer might be in libmail-sendmail-perl so I issued the command:
[FONT="System"]sudo aptitude install libmail-sendmail-perl[/FONT]
That command succeeded but my script still doesn't find Mail::Mailer. Here are my questions;
- would using both installation methods, CPAN and aptitude cause conflicts?
- how can you tell which modules are in which package e.g. where is Mail::Mailer? (Is it really in libmail-sendmail-perl?)

Thanks,
Mitch

[FONT="System"]cpan> o conf
CPAN::Config options and /home/mitch/.cpan/CPAN/MyConfig.pm:
    commit             Commit changes to disk
    defaults           Reload defaults from disk
    init               Interactive setting of all options

    build_cache        10
    build_dir          /home/mitch/.cpan/build
    cache_metadata     1
    cpan_home          /home/mitch/.cpan
    cpan_version_check 1
    dontload_hash
    ftp                /usr/bin/ftp
    ftp_proxy
    getcwd             cwd
    gpg                /usr/bin/gpg
    gzip               /bin/gzip
    histfile           /home/mitch/.cpan/histfile
    histsize           100
    http_proxy
    inactivity_timeout 0
    index_expire       1
    inhibit_startup_message 0
    keep_source_where  /home/mitch/.cpan/sources
    lynx
    make
    make_arg
    make_install_arg
    makepl_arg         INSTALLDIRS=site
    ncftp
    ncftpget
    no_proxy
    pager              /usr/bin/less
    prerequisites_policy ask
    scan_cache         atstart
    shell              /bin/bash
    tar                /bin/tar
    term_is_latin      1
    unzip              /usr/bin/unzip
    urllist
    wget               /usr/bin/wget


cpan>[/FONT]

---

### Post by pstracha on 2007-07-13
I realize this is an old post, but for anyone else looking for Mail::Mailer through aptitude, try:

```
sudo apt-get install libmail-perl
```

---

### Post by spatialguy on 2008-05-08
The module is called in 8.04:

libmailtools-perl 

Note: most modules you can find in the synaptic tool with search. However, not all modules include perfect descriptions of the classes the implement.
libmailtools-perl is one of those, it apparently implements Mail::Mailer

For example: IO::Compress::Gzip is undocumented, but implemented by 
libcompress-zlib-perl 

cheers,

Floris

---

