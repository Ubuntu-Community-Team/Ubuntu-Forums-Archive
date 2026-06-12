---
title: "Help getting ruby and mongrel to work"
date: 2010-05-07
forum: Programming Talk
---

### Post by nikhilbhardwaj on 2010-05-07
i've installed ruby 1.9.1-full package from the repos
when i try to install mongrel i get this error
```

make: *** [http11.o] Error 1


Gem files will remain installed in /usr/lib/ruby1.9.1/gems/1.9.1/gems/mongrel-1.1.5 for inspection.
Results logged to /usr/lib/ruby1.9.1/gems/1.9.1/gems/mongrel-1.1.5/ext/http11/gem_make.out


```

and here's the log file

```

/usr/bin/ruby1.9.1 extconf.rb
checking for main() in -lc... yes
creating Makefile

make
gcc -I. -I/usr/include/ruby-1.9.1/i486-linux -I/usr/include/ruby-1.9.1/ruby/backward -I/usr/include/ruby-1.9.1 -I. -D_FILE_OFFSET_BITS=64  -fPIC -fno-strict-aliasing -g -g -O2 -O2 -g -Wall -Wno-parentheses  -fPIC  -o http11_parser.o -c http11_parser.c
gcc -I. -I/usr/include/ruby-1.9.1/i486-linux -I/usr/include/ruby-1.9.1/ruby/backward -I/usr/include/ruby-1.9.1 -I. -D_FILE_OFFSET_BITS=64  -fPIC -fno-strict-aliasing -g -g -O2 -O2 -g -Wall -Wno-parentheses  -fPIC  -o http11.o -c http11.c
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

```

what am i doing wrong

i plan to learn sinatra development framework
when i run this simple file
```

require 'rubygems'
require 'sinatra'
get '/hi' do
  "Hello World"
end
    

```
i get
```

nikhil@ubuntu:~/Documents/sinatra$ ruby1.9.1 test.rb test.rb:2:in `require': no such file to load -- sinatra (LoadError)
    from test.rb:2:in `<main>'


```
am i missing some packages

---

