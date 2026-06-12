---
title: "React-Rails 'Could not find json-1.8.1 in any of the sources'"
date: 2016-06-29
forum: Programming Talk
---

### Post by Crafty Kisses on 2016-06-29
I'm doing a project using react-rails but when I run

```
bundle install
```

I get

```

Could not find json-1.8.1 in any of the sources
```

Specifically, this is the entire error

```
Gem::Ext::BuildError: ERROR: Failed to build gem native extension.

    current directory: /Users/montana/.rvm/gems/ruby-2.3.0/gems/json-1.8.1/ext/json/ext/generator
/Users/montana/.rvm/rubies/ruby-2.3.0/bin/ruby -r ./siteconf20160629-5602-i1di2t.rb extconf.rb
creating Makefile

current directory: /Users/montana/.rvm/gems/ruby-2.3.0/gems/json-1.8.1/ext/json/ext/generator
make "DESTDIR=" clean

current directory: /Users/montana/.rvm/gems/ruby-2.3.0/gems/json-1.8.1/ext/json/ext/generator
make "DESTDIR="
compiling generator.c
In file included from generator.c:1:
./../fbuffer/fbuffer.h:175:47: error: too few arguments provided to function-like macro invocation
    VALUE result = rb_str_new(FBUFFER_PAIR(fb));
                                              ^
/Users/montana/.rvm/rubies/ruby-2.3.0/include/ruby-2.3.0/ruby/intern.h:797:9: note: macro 'rb_str_new' defined here
#define rb_str_new(str, len) __extension__ (    \
        ^
In file included from generator.c:1:
./../fbuffer/fbuffer.h:175:11: warning: incompatible pointer to integer conversion initializing 'VALUE' (aka 'unsigned long') with an expression of type 'VALUE (const char *, long)' (aka 'unsigned long (const char *, long)') [-Wint-conversion]
    VALUE result = rb_str_new(FBUFFER_PAIR(fb));
          ^        ~~~~~~~~~~
1 warning and 1 error generated.
make: *** [generator.o] Error 1
```

There's been various posts about this on stackoverflow, and have tried most "solutions' but none seem to work for me, I also ran

```
gem list | grep json

```

It says I have the json gem via

```
 json (1.8.3)
 multi_json (1.10.1)

```

I've tried to stop spring, updating the gems, & bundler. I've also ran

```
rbenv rehash
```

To no avail, still getting this error, any input would be highly appreciated.

---

### Post by Crafty Kisses on 2016-06-30
Solved by bumping down version of ruby/rails via running 
```
rvm install ruby-2.1.1
```
Then
```
 rvm use ruby-2.1.1
``` 
cd'd into directory and ran
```
bundle install
```
It worked perfectly. This specifically is the Mac OSX fix, the Ubuntu (or any other distribution) to my knowledge is running 
```
sudo apt-get install libgmp3-dev
```
Refer to this for more info: [https://github.com/flori/json/issues/229](https://github.com/flori/json/issues/229)

---

