---
title: "ruby-opengl, gems can't build native extensions"
date: 2010-05-17
forum: Programming Talk
---

### Post by pswoo on 2010-05-17
When trying to install the ruby-opengl gem, gems aborts because it is unable to build the native extension extension. Running rake with --trace dumps the following to stderr
```
gcc  -fPIC -fno-strict-aliasing -g -g -O2  -fPIC    -Wall -DRUBY_VERSION=187  -I/usr/include -I/usr/lib/ruby/1.8/i486-linux -I/usr/local/lib/site_ruby/1.8 -I. -c gl-ext-gremedy.c
In file included from gl-ext-gremedy.c:16:
../common/common.h:25:18: error: ruby.h: No such file or directory
In file included from ../common/common.h:51,
                 from gl-ext-gremedy.c:16:
../common/gl-error.h:16: warning: parameter names (without types) in function declaration
../common/gl-error.h:18: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘error_checking’
../common/gl-error.h:19: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘inside_begin_end’
In file included from ../common/common.h:54,
                 from gl-ext-gremedy.c:16:
../common/conv.h: In function ‘num2double’:
../common/conv.h:55: error: expected declaration specifiers before ‘VALUE’
../common/conv.h:55: warning: implicit declaration of function ‘FIXNUM_P’
../common/conv.h:55: warning: implicit declaration of function ‘FIX2LONG’
../common/conv.h:55: warning: implicit declaration of function ‘TYPE’
../common/conv.h:55: error: ‘T_FLOAT’ undeclared (first use in this function)
../common/conv.h:55: error: (Each undeclared identifier is reported only once
../common/conv.h:55: error: for each function it appears in.)
../common/conv.h:55: warning: implicit declaration of function ‘RFLOAT’
../common/conv.h:55: error: invalid type argument of ‘->’ (have ‘int’)
...
```

Not sure what to do... maybe I'm using an incompatible C compiler? gcc --version yields 4.4.1-4ubuntu9

Also, after looking at that line which says "ruby.h: no such file or directory", I went into the ../common directory and ruby.h is, in fact, missing. Looked at the ruby-opengl .gem from rubyforge, and ruby.h is missing from /ext/common there as well which seems strange.

I'm not sure if this is the place to be asking, but hopefully some of you have installed this gem at some point.

---

