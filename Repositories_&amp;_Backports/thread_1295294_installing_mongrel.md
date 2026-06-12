---
title: "installing mongrel"
date: 2009-10-19
forum: Repositories &amp; Backports
---

### Post by fcuk112 on 2009-10-19
when i do sudo gem install mongrel i get the following:
> 
Building native extensions.  This could take a while...
ERROR:  Error installing mongrel:
        ERROR: Failed to build gem native extension.

/usr/local/bin/ruby extconf.rb
checking for main() in -lc... yes
creating Makefile

make
gcc -I. -I/usr/local/include/ruby-1.9.1/i686-linux -I/usr/local/include/ruby-1.9.1/ruby/backward -I/usr/local/include/ruby-1.9.1 -I. -D_FILE_OFFSET_BITS=64  -fPIC  -O2 -g -Wall -Wno-parentheses  -o http11_parser.o -c http11_parser.c
gcc -I. -I/usr/local/include/ruby-1.9.1/i686-linux -I/usr/local/include/ruby-1.9.1/ruby/backward -I/usr/local/include/ruby-1.9.1 -I. -D_FILE_OFFSET_BITS=64  -fPIC  -O2 -g -Wall -Wno-parentheses  -o http11.o -c http11.c
http11.c: In function ‘http_field’:
http11.c:70: warning: format not a string literal and no format arguments
http11.c:71: warning: format not a string literal and no format arguments
http11.c:77: error: ‘struct RString’ has no member named ‘ptr’
http11.c:77: error: ‘struct RString’ has no member named ‘len’
http11.c:77: warning: left-hand operand of comma expression has no effect
http11.c: In function ‘request_uri’:
http11.c:102: warning: format not a string literal and no format arguments
http11.c: In function ‘fragment’:
http11.c:113: warning: format not a string literal and no format arguments
http11.c: In function ‘request_path’:
http11.c:124: warning: format not a string literal and no format arguments
http11.c: In function ‘query_string’:
http11.c:135: warning: format not a string literal and no format arguments
http11.c: In function ‘header_done’:
http11.c:172: error: ‘struct RString’ has no member named ‘ptr’
http11.c:172: error: ‘struct RString’ has no member named ‘ptr’
http11.c:172: error: ‘struct RString’ has no member named ‘ptr’
http11.c:174: error: ‘struct RString’ has no member named ‘ptr’
http11.c:176: error: ‘struct RString’ has no member named ‘ptr’
http11.c:177: error: ‘struct RString’ has no member named ‘len’
http11.c: In function ‘HttpParser_execute’:
http11.c:298: error: ‘struct RString’ has no member named ‘ptr’
http11.c:299: error: ‘struct RString’ has no member named ‘len’
http11.c:307: warning: format not a string literal and no format arguments
make: *** [http11.o] Error 1


Gem files will remain installed in /usr/local/lib/ruby/gems/1.9.1/gems/mongrel-1.1.5 for inspection.
Results logged to /usr/local/lib/ruby/gems/1.9.1/gems/mongrel-1.1.5/ext/http11/gem_make.out

any idea?

---

### Post by mfolnovic on 2009-12-31
fcuk112: have you found solution? I see it's 2 months old topic, and it's still not fixed... :S

---

### Post by Lavix on 2010-02-09
I got exactly the same error after upgrading to Ruby 1.9.1. First I believed that it was because of the Rails 3.0 beta version. But now I think it's a mongrel problem... Do you ?
I'm on Ubuntu 9.10 (installed inside Windows XP Pro), ruby 1.9.1., rails 3.0 beta.
Before upgrading to ruby 1.9.1 from 1.8.7 everything worked fine all gems (including mongrel) were installed without problems and the RoR environment was OK.

---

### Post by Lavix on 2010-02-09
I'va found some info here:

[http://blog.phusion.nl/2009/02/02/getting-ready-for-ruby-191/](http://blog.phusion.nl/2009/02/02/getting-ready-for-ruby-191/)

I haven't tried it yet. Hope it helps you.

---

### Post by Lavix on 2010-02-09
I got it working.

You should install mongrel gem as follows:

gem install mongrel --source [http://gems.rubyinstaller.org](http://gems.rubyinstaller.org)

---

### Post by rsrajesh on 2010-05-02
Lavix, 
Wow, great man!!!

After I added the source, now it is working like a charm...!!! What a simple and effective solution..

u saved my day!

---

### Post by ajeffri on 2011-04-25
I don't remember where I saw this, but I used:

```
sudo gem install mongrel --pre
```

This worked beautifully on Lucid, although be forewarned it is pre-release code.

---

