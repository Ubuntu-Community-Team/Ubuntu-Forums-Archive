---
title: "RMagick problem"
date: 2006-05-11
forum: Programming Talk
---

### Post by robtotheb on 2006-05-11
Im building a web app in Ubuntu Dapper using Ruby on Rails and need to use RMagick.  I can't seem to install it.

I get this error when installing the gem...

```
$ sudo gem install rmagick
Attempting local installation of 'rmagick'
Local gem file not found: rmagick*.gem
Attempting remote installation of 'rmagick'
Building native extensions.  This could take a while...
configure: WARNING: you should use --build, --host, --target
configure: WARNING: you should use --build, --host, --target
configure: error: Can't install RMagick. Can't find Magick-config or GraphicsMag ick-config program.
ERROR:  While executing gem ... (RuntimeError)
    ERROR: Failed to build gem native extension.
Gem files will remain installed in /usr/lib/ruby/gems/1.8/gems/rmagick-1.10.1 fo r inspection.
  ruby configure install rmagick\nConfiguring RMagick 1.10.1
checking for install-gcc... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for ruby... /usr/bin/ruby
checking for Magick-config... no
checking for GraphicsMagick-config... no


Results logged to /usr/lib/ruby/gems/1.8/gems/rmagick-1.10.1/gem_make.out

```

Any ideas?

---

### Post by jdonnell on 2006-05-18
I'm having teh same problem. Anyone have a solution?

---

### Post by asimon on 2006-05-18
You need to install libmagick9-dev.

---

### Post by jdonnell on 2006-05-18
thank you. I always forget the dev package :(

---

### Post by rogerdpack on 2009-05-18
> **asimon said:**
> You need to install libmagick9-dev.

sudo apt-get install libmagick-dev didn't seem to work but libmagick9-dev did.

Odd.

---

