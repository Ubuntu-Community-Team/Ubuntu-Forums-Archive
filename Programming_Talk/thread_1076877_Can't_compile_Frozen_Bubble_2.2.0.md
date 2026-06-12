---
title: "Can't compile Frozen Bubble 2.2.0"
date: 2009-02-21
forum: Programming Talk
---

### Post by dodle on 2009-02-21
I am trying to compile the newest version of Frozen Bubble.  The source is here: [http://www.frozen-bubble.org/]("http://www.frozen-bubble.org/data/frozen-bubble-2.2.0.tar.bz2")There is no configure file in the directory and when I run "make" I get the following output:```
echo 'package fb_config;' > c_stuff/lib/fb_config.pm
echo 'use vars qw(@ISA @EXPORT $FPATH $FLPATH);' >> c_stuff/lib/fb_config.pm
echo '@ISA = qw(Exporter);' >> c_stuff/lib/fb_config.pm
echo '@EXPORT = qw($FPATH $FLPATH);' >> c_stuff/lib/fb_config.pm
echo '$FPATH = "/usr/local/share/frozen-bubble";' >> c_stuff/lib/fb_config.pm
echo '$FLPATH = "/usr/local/lib/frozen-bubble";' >> c_stuff/lib/fb_config.pm
perl -ne "print \$1 if m|\\\$version = '(.*)';|" c_stuff/lib/fb_stuff.pm > VERSION
make[1]: Entering directory `/home/jordan/Development/frozen-bubble-2 (copy).2.0/c_stuff'
make -f Makefile_c
make[2]: Entering directory `/home/jordan/Development/frozen-bubble-2 (copy).2.0/c_stuff'
Skip blib/lib/fb_net_discover.pm (unchanged)
Skip blib/lib/fb_c_stuff.pm (unchanged)
Skip blib/lib/fb_stuff.pm (unchanged)
Skip blib/lib/fb_config.pm (unchanged)
Skip blib/lib/fb_net.pm (unchanged)
Skip blib/lib/FBLE.pm (unchanged)
Skip blib/lib/fbsyms.pm (unchanged)
make[2]: Leaving directory `/home/jordan/Development/frozen-bubble-2 (copy).2.0/c_stuff'
make[1]: Leaving directory `/home/jordan/Development/frozen-bubble-2 (copy).2.0/c_stuff'
make[1]: Entering directory `/home/jordan/Development/frozen-bubble-2 (copy).2.0/po'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/jordan/Development/frozen-bubble-2 (copy).2.0/po'
make[1]: Entering directory `/home/jordan/Development/frozen-bubble-2 (copy).2.0/server'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/jordan/Development/frozen-bubble-2 (copy).2.0/server'

```Can anyone help me compile it, I think it is written in Perl/SDL, which I have no experience with.

---

