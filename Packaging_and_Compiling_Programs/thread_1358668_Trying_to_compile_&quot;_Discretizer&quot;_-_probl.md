---
title: "Trying to compile &quot; Discretizer&quot; - problem with FXruby &quot;fox16&quot;"
date: 2009-12-18
forum: Packaging and Compiling Programs
---

### Post by abunti on 2009-12-18
Hello,
I'm trying to compile Discretizer. It took around two afternoons and evenings until now to search and get all packages required. But there is "require 'fox16' in the discretizer.rb file. 
```
require 'fox16'
require 'fox16/responder'
```But if I trust my information, this means, that it refers to FXruby (which is also said by the installation instructions of Discretizer). I can't find any file named "fox16.rb". So I installed FXruby, and during installation no error occured. But when I try to compile discretizer.rb there is an error. The console looks like this:
```
andreas@andreas-laptop:~/discretizer/discretizer$ ruby discretizer.rb
/home/andreas/discretizer/discretizer/dialogs.rb:24:in `require': no such file to load -- fox16 (LoadError)
    from /home/andreas/discretizer/discretizer/dialogs.rb:24:in `<top (required)>'
    from discretizer.rb:33:in `require'
    from discretizer.rb:33:in `<main>'
andreas@andreas-laptop:~/discretizer/discretizer$ 
```I installed the FXruby by using

```
wget [http://rubyforge.org/frs/download.php/39358/fxruby-1.6.16.gem](http://rubyforge.org/frs/download.php/39358/fxruby-1.6.16.gem)
 sudo gem install fxruby-1.6.16.gem 

```With FXruby wasn't working, I was trying to compile it. But then there was an error, here the console:

```
andreas@andreas-laptop:~/Discretizer/FXRuby-1.6.4$ sudo ruby install.rb setup
install.rb: entering setup phase...
---> lib
---> lib/fox16
<--- lib/fox16
<--- lib
---> ext
---> ext/fox16
make 
g++ -I. -I/usr/local/include/ruby-1.9.1/x86_64-linux -I/usr/local/include/ruby-1.9.1/ruby/backward -I/usr/local/include/ruby-1.9.1 -I/home/andreas/Discretizer/FXRuby-1.6.4/ext/fox16 -DHAVE_SYS_TIME_H -DHAVE_SIGNAL_H -I/usr/local/include/fxscintilla -I/usr/local/include/fox-1.6    -I/usr/include/fox-1.6 -fPIC  -O2 -g -Wall -Wno-parentheses -O0 -Iinclude    -o treelist_wrap.o -c treelist_wrap.cpp
In file included from include/FXRuby.h:825,
                 from include/FXRbCommon.h:93,
                 from treelist_wrap.cpp:553:
include/inlinestubs.h: In function &#8216;void FXApp_init(FX::FXApp*, VALUE, bool)&#8217;:
include/inlinestubs.h:20: error: &#8216;struct RArray&#8217; has no member named &#8216;len&#8217;
include/inlinestubs.h:20: warning: deprecated conversion from string constant to &#8216;char*&#8217;
include/inlinestubs.h:20: error: &#8216;struct RArray&#8217; has no member named &#8216;len&#8217;
treelist_wrap.cpp: In function &#8216;void FXFoldingList_setHeaders(FX::FXFoldingList*, VALUE, FX::FXint)&#8217;:
treelist_wrap.cpp:619: error: &#8216;struct RArray&#8217; has no member named &#8216;len&#8217;
treelist_wrap.cpp: In function &#8216;VALUE _wrap_FXFoldingList_fillItems(int, VALUE*, VALUE)&#8217;:
treelist_wrap.cpp:1389: error: &#8216;struct RArray&#8217; has no member named &#8216;len&#8217;
treelist_wrap.cpp:1390: error: &#8216;struct RArray&#8217; has no member named &#8216;len&#8217;
treelist_wrap.cpp:1391: error: &#8216;struct RArray&#8217; has no member named &#8216;len&#8217;
treelist_wrap.cpp: In function &#8216;VALUE _wrap_FXTreeList_fillItems(int, VALUE*, VALUE)&#8217;:
treelist_wrap.cpp:2596: error: &#8216;struct RArray&#8217; has no member named &#8216;len&#8217;
treelist_wrap.cpp:2597: error: &#8216;struct RArray&#8217; has no member named &#8216;len&#8217;
treelist_wrap.cpp:2598: error: &#8216;struct RArray&#8217; has no member named &#8216;len&#8217;
treelist_wrap.cpp: At global scope:
treelist_wrap.cpp:547: warning: &#8216;void SWIG_AsVal(VALUE, int*)&#8217; defined but not used
include/inlinestubs.h:20: warning: &#8216;void FXApp_init(FX::FXApp*, VALUE, bool)&#8217; defined but not used
treelist_wrap.cpp:1007: warning: &#8216;void free_FXFoldingItem(FX::FXFoldingItem*)&#8217; defined but not used
treelist_wrap.cpp:1853: warning: &#8216;void free_FXFoldingList(FX::FXFoldingList*)&#8217; defined but not used
treelist_wrap.cpp:2301: warning: &#8216;void free_FXTreeItem(FX::FXTreeItem*)&#8217; defined but not used
treelist_wrap.cpp:3050: warning: &#8216;void free_FXTreeList(FX::FXTreeList*)&#8217; defined but not used
treelist_wrap.cpp:3407: warning: &#8216;void free_FXDirItem(FX::FXDirItem*)&#8217; defined but not used
treelist_wrap.cpp:3830: warning: &#8216;void free_FXDirList(FX::FXDirList*)&#8217; defined but not used
make: *** [treelist_wrap.o] Fehler 1
setup failed
'system make ' failed
Try 'ruby install.rb --help' for detailed usage
```After that hasn't worked too, I found another download. Then I tried to install this download by using
./configure
make
sudo make install
Again no error occured, but again the same error was displayed after I tried to compile Discretizer.rb
Has anyone an idea, why FXruby doesn't work? Or am I wrong and the error isn't caused by FXruby. 
I would be thankful for any answer!

---

