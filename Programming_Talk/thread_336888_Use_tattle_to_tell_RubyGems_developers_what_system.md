---
title: "Use tattle to tell RubyGems developers what systems you are using"
date: 2007-01-12
forum: Programming Talk
---

### Post by stoffe on 2007-01-12
[http://www.chadfowler.com/2007/1/8/tattle-the-ruby-census](http://www.chadfowler.com/2007/1/8/tattle-the-ruby-census)

The [RubyGems]("http://rubygems.org/") developers has released a small gem called [tattle]("http://tattle.rubygarden.org/"), that is meant to help them see what systems are being used and make gems (and other libs) work better on those platforms. If you are using gems and want them to work better on your preferred system(s), it's important that the devs know you are out there.

Tattle collects some non-personal info about what platform you are using and what path it uses, etc. On my Edgy system, the info sent looks like this:
```
prefix, /usr
ruby_version, 1.8.4
host_vendor, pc
ruby_install_name, ruby1.8
build, i686-pc-linux-gnu
target_cpu, i486
arch, i486-linux
rubygems_version, 0.9.0
SHELL, /bin/sh
host_os, linux-gnu
report_time, Fri Jan 12 14:49:42 CET 2007
host_cpu, i686
key, 2c09c8bceb87c43c85e364635f4bb89ce71c30c0a2e2296e0396958d6135aa12
LIBRUBY, libruby1.8.so.1.8.4
LIBRUBY_SO, libruby1.8.so.1.8.4
target, i486-pc-linux-gnu

```

To install:

[FONT="Courier New"]$ sudo gem install tattle[/FONT]

To submit your info:

[FONT="Courier New"]$ tattle[/FONT]

If you want to see what would be posted before posting, you can do:

[FONT="Courier New"]$ tattle report[/FONT]

If you are using gems, take a few seconds to help out. :)

---

