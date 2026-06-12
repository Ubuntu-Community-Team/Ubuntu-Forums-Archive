---
title: "compile poedit 1.8.2 on ubuntu 14.04"
date: 2015-07-21
forum: Packaging and Compiling Programs
---

### Post by mickro on 2015-07-21
Hi folks!

I'm trying to compile poedit 1.8.2 on ubuntu 14.04

I try with both tar.gz source from official website and from the git repository: [EMAIL="git@github.com:vslavik/poedit.git"]git@github.com:vslavik/poedit.git[/EMAIL]

the compile phase sounds as going well. But the make is crashing and there is where I am stuck.

Sounds as something to do with Lucene which I compiled from the git repository.

Does someone can look at my log to drive me one the right way?

thanks!

```

~/devel/github/vslavik/poedit on master*
$ ./configure 
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether make supports nested variables... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking whether make supports nested variables... (cached) yes
checking for install location... /usr/local
checking for gawk... (cached) gawk
checking whether ln -s works... yes
checking for ranlib... ranlib
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking whether gcc understands -c and -o together... yes
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking whether g++ supports C++11 features by default... no
checking whether g++ supports C++11 features with -std=gnu++11... yes
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking cpprest/http_client.h usability... no
checking cpprest/http_client.h presence... no
checking for cpprest/http_client.h... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for wx-config... /usr/bin/wx-config
checking for wxWidgets version >= 3.0.0 (--unicode)... yes (version 3.0.2)
checking for wxWidgets static library... no
checking if wxWidgets includes XRC... yes
checking for wxrc... /usr/bin/wxrc
checking for mkdtemp... yes
checking for ICU... yes
checking if wxWidgets toolkit uses GTK+ 3... no
checking if wxWidgets toolkit uses GTK+ 2... yes
checking for GTKSPELL... yes
checking for LUCENE... yes
checking for Berkeley DB >= 4.7 (C++)... header db_cxx.h, library -ldb_cxx
checking for EXPAT... yes
checking cld2/public/compact_lang_det.h usability... no
checking cld2/public/compact_lang_det.h presence... no
checking for cld2/public/compact_lang_det.h... no
checking for a sed that does not truncate output... /bin/sed
checking whether the C++ compiler accepts the -Wall flag... yes
checking whether the C++ compiler accepts the -Wextra flag... yes
checking that generated files are newer than configure... done
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating artwork/Makefile
config.status: creating locales/Makefile
config.status: creating docs/Makefile
config.status: executing depfiles commands


Configured poedit-1.8.2 for x86_64-unknown-linux-gnu


Enabled features:


    * debug build:                    no
    * legacy (pre-1.6) TM migration:  yes
    * language detection:             no
    * crowdin integration:            no

```

```

~/devel/github/vslavik/poedit on master*$ make
Making all in src
make[1]: Entering directory `/home/mickro/devel/github/vslavik/poedit/src'
  CXX      attentionbar.o
  CXX      errorbar.o
  CXX      catalog.o
  CXX      edapp.o
  CXX      edframe.o
  CXX      fileviewer.o
  CXX      extractor.o
  CXX      prefsdlg.o
  CXX      propertiesdlg.o
  CXX      progressinfo.o
  CXX      digger.o
  CXX      gexecute.o
  CXX      summarydlg.o
  CXX      spellchecking.o
  CXX      findframe.o
  CXX      commentdlg.o
  CXX      tm/suggestions.o
  CXX      tm/transmem.o
  CXX      tm/tm_migrate.o
  CXX      manager.o
  CXX      chooselang.o
  CXX      export_html.o
  CXX      icons.o
  CXX      pluralforms/pl_evaluate.o
  CXX      edlistctrl.o
  CXX      cat_sorting.o
  CXX      utility.o
  CXX      concurrency.o
  CXX      language.o
  CXX      languagectrl.o
  CXX      welcomescreen.o
  CXX      syntaxhighlighter.o
  CXX      sidebar.o
  CXX      text_control.o
text_control.cpp:482:6: warning: unused parameter ‘isRTL’ [-Wunused-parameter]
 void AnyTranslatableTextCtrl::SetLanguageRTL(bool isRTL)
      ^
  CXX      customcontrols.o
  CXX      hidpi.o
  CXX      wx/main_toolbar.o
  CXX      wx_backports/wx_gtk_activityindicator.o
/usr/bin/wxrc -v -c -o compiled_xrc.cpp ./resources/menus.xrc ./resources/prefs.xrc ./resources/progress.xrc ./resources/properties.xrc ./resources/summary.xrc ./resources/toolbar.xrc ./resources/comment.xrc ./resources/manager.xrc
processing ./resources/menus.xrc...
processing ./resources/prefs.xrc...
processing ./resources/progress.xrc...
processing ./resources/properties.xrc...
processing ./resources/summary.xrc...
processing ./resources/toolbar.xrc...
processing ./resources/comment.xrc...
processing ./resources/manager.xrc...
creating C++ source file /home/mickro/devel/github/vslavik/poedit/src/compiled_xrc.cpp...
  CXX      compiled_xrc.o
  CXXLD    poedit
tm/transmem.o: In function `PerformSearchWithBlock<(anonymous namespace)::PerformSearch(Lucene::IndexSearcherPtr, Lucene::QueryPtr, Lucene::QueryPtr, const wstring&, Lucene::QueryPtr, SuggestionsList&, double, double)::__lambda5>':
/home/mickro/devel/github/vslavik/poedit/src/tm/transmem.cpp:297: undefined reference to `Lucene::BooleanQuery::add(boost::shared_ptr<Lucene::Query> const&, Lucene::BooleanClause::Occur)'
/home/mickro/devel/github/vslavik/poedit/src/tm/transmem.cpp:298: undefined reference to `Lucene::BooleanQuery::add(boost::shared_ptr<Lucene::Query> const&, Lucene::BooleanClause::Occur)'
/home/mickro/devel/github/vslavik/poedit/src/tm/transmem.cpp:299: undefined reference to `Lucene::BooleanQuery::add(boost::shared_ptr<Lucene::Query> const&, Lucene::BooleanClause::Occur)'
tm/transmem.o: In function `TranslationMemoryImpl::Search(Language const&, Language const&, std::basic_string<wchar_t, std::char_traits<wchar_t>, std::allocator<wchar_t> > const&)':
/home/mickro/devel/github/vslavik/poedit/src/tm/transmem.cpp:391: undefined reference to `Lucene::BooleanQuery::add(boost::shared_ptr<Lucene::Query> const&, Lucene::BooleanClause::Occur)'
/home/mickro/devel/github/vslavik/poedit/src/tm/transmem.cpp:392: undefined reference to `Lucene::BooleanQuery::add(boost::shared_ptr<Lucene::Query> const&, Lucene::BooleanClause::Occur)'
tm/transmem.o:/home/mickro/devel/github/vslavik/poedit/src/tm/transmem.cpp:407: more undefined references to `Lucene::BooleanQuery::add(boost::shared_ptr<Lucene::Query> const&, Lucene::BooleanClause::Occur)' follow
tm/transmem.o: In function `TranslationMemoryImpl::Search(Language const&, Language const&, std::basic_string<wchar_t, std::char_traits<wchar_t>, std::allocator<wchar_t> > const&)':
/home/mickro/devel/github/vslavik/poedit/src/tm/transmem.cpp:408: undefined reference to `Lucene::PhraseQuery::add(boost::shared_ptr<Lucene::Term> const&)'
tm/transmem.o: In function `PerformSearchWithBlock<TranslationMemoryImpl::Search(const Language&, const Language&, const wstring&)::__lambda6>':
/home/mickro/devel/github/vslavik/poedit/src/tm/transmem.cpp:297: undefined reference to `Lucene::BooleanQuery::add(boost::shared_ptr<Lucene::Query> const&, Lucene::BooleanClause::Occur)'
/home/mickro/devel/github/vslavik/poedit/src/tm/transmem.cpp:298: undefined reference to `Lucene::BooleanQuery::add(boost::shared_ptr<Lucene::Query> const&, Lucene::BooleanClause::Occur)'
/home/mickro/devel/github/vslavik/poedit/src/tm/transmem.cpp:299: undefined reference to `Lucene::BooleanQuery::add(boost::shared_ptr<Lucene::Query> const&, Lucene::BooleanClause::Occur)'
tm/transmem.o: In function `boost::detail::sp_if_not_array<Lucene::IndexSearcher>::type boost::make_shared<Lucene::IndexSearcher, boost::shared_ptr<Lucene::IndexReader> const&>(boost::shared_ptr<Lucene::IndexReader> const&)':
/usr/include/boost/smart_ptr/make_shared_object.hpp:218: undefined reference to `Lucene::IndexSearcher::IndexSearcher(boost::shared_ptr<Lucene::IndexReader> const&)'
tm/transmem.o: In function `boost::detail::sp_if_not_array<Lucene::TermQuery>::type boost::make_shared<Lucene::TermQuery, boost::shared_ptr<Lucene::Term> const&>(boost::shared_ptr<Lucene::Term> const&)':
/usr/include/boost/smart_ptr/make_shared_object.hpp:218: undefined reference to `Lucene::TermQuery::TermQuery(boost::shared_ptr<Lucene::Term> const&)'
tm/transmem.o: In function `boost::detail::sp_if_not_array<Lucene::PrefixQuery>::type boost::make_shared<Lucene::PrefixQuery, boost::shared_ptr<Lucene::Term> const&>(boost::shared_ptr<Lucene::Term> const&)':
/usr/include/boost/smart_ptr/make_shared_object.hpp:218: undefined reference to `Lucene::PrefixQuery::PrefixQuery(boost::shared_ptr<Lucene::Term> const&)'
tm/transmem.o: In function `TranslationMemoryWriterImpl::Insert(Language const&, Language const&, std::basic_string<wchar_t, std::char_traits<wchar_t>, std::allocator<wchar_t> > const&, std::basic_string<wchar_t, std::char_traits<wchar_t>, std::allocator<wchar_t> > const&)':
/home/mickro/devel/github/vslavik/poedit/src/tm/transmem.cpp:528: undefined reference to `Lucene::Document::add(boost::shared_ptr<Lucene::Fieldable> const&)'
/home/mickro/devel/github/vslavik/poedit/src/tm/transmem.cpp:530: undefined reference to `Lucene::Document::add(boost::shared_ptr<Lucene::Fieldable> const&)'
/home/mickro/devel/github/vslavik/poedit/src/tm/transmem.cpp:532: undefined reference to `Lucene::Document::add(boost::shared_ptr<Lucene::Fieldable> const&)'
/home/mickro/devel/github/vslavik/poedit/src/tm/transmem.cpp:534: undefined reference to `Lucene::Document::add(boost::shared_ptr<Lucene::Fieldable> const&)'
/home/mickro/devel/github/vslavik/poedit/src/tm/transmem.cpp:536: undefined reference to `Lucene::Document::add(boost::shared_ptr<Lucene::Fieldable> const&)'
tm/transmem.o:/home/mickro/devel/github/vslavik/poedit/src/tm/transmem.cpp:538: more undefined references to `Lucene::Document::add(boost::shared_ptr<Lucene::Fieldable> const&)' follow
tm/transmem.o: In function `boost::detail::sp_if_not_array<Lucene::MMapDirectory>::type boost::make_shared<Lucene::MMapDirectory, std::basic_string<wchar_t, std::char_traits<wchar_t>, std::allocator<wchar_t> > const&>(std::basic_string<wchar_t, std::char_traits<wchar_t>, std::allocator<wchar_t> > const&)':
/usr/include/boost/smart_ptr/make_shared_object.hpp:218: undefined reference to `Lucene::MMapDirectory::MMapDirectory(std::basic_string<wchar_t, std::char_traits<wchar_t>, std::allocator<wchar_t> > const&, boost::shared_ptr<Lucene::LockFactory> const&)'
tm/transmem.o: In function `boost::detail::sp_if_not_array<Lucene::IndexWriter>::type boost::make_shared<Lucene::IndexWriter, boost::shared_ptr<Lucene::MMapDirectory> const&, boost::shared_ptr<Lucene::Analyzer> const&, int const&>(boost::shared_ptr<Lucene::MMapDirectory> const&, boost::shared_ptr<Lucene::Analyzer> const&, int const&)':
/usr/include/boost/smart_ptr/make_shared_object.hpp:218: undefined reference to `Lucene::IndexWriter::IndexWriter(boost::shared_ptr<Lucene::Directory> const&, boost::shared_ptr<Lucene::Analyzer> const&, int)'
collect2: error: ld returned 1 exit status
make[1]: *** [poedit] Error 1
make[1]: Leaving directory `/home/mickro/devel/github/vslavik/poedit/src'
make: *** [all-recursive] Error 1

```

---

### Post by earruda on 2015-07-21
You could take the easy road and install POEdit from repository, with: ```
 # apt-get install poedit 
```  But if you want to compile it you'll have to know every POEdit's dependencies and it's dependencies' dependencies, and so on, and compile them all.  Have you ran configure, make and make install for Lucene? If yes, are you sure the Lucene lib can be found by POEdit source, to be included via #include? According to the log output, Lucene libs cannot be found.

---

### Post by steeldriver on 2015-07-21
If you want to build poedit from source WITHOUT needing to also build a newer version of liblucene++ yourself, the poedit author/maintainer appears to have provided a PPA that provides a suitable pre-built liblucene++-dev:

> 
Dependencies for building Poedit on older Ubuntu versions.

[https://launchpad.net/~vslavik/+archive/ubuntu/poedit]("https://launchpad.net/%7Evslavik/+archive/ubuntu/poedit")

```

sudo apt-add-repository ppa:vslavik/poedit

sudo apt-get update

```

You can check the newly available version using
```

sudo apt-cache policy liblucene++-dev
liblucene++-dev:
  Installed: 3.0.4-0ubuntu3
  Candidate: 3.0.6-4~ubuntu14.04.1~ppa1
  Version table:
     3.0.6-4~ubuntu14.04.1~ppa1 0
        500 http://ppa.launchpad.net/vslavik/poedit/ubuntu/ trusty/main amd64 Packages
 *** 3.0.4-0ubuntu3 0
        500 http://ca.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
        100 /var/lib/dpkg/status

```

Then install it

```

sudo apt-get install liblucene++-dev

```

---

### Post by mickro on 2015-07-22
verton_Arruda this version in repository of Ubuntu 14.04 is the 1.5.4. It is not the one I want.

> [COLOR=#000000]According to the log output, Lucene libs cannot be found.[/COLOR]

Yes it is what I figured out.

> [COLOR=#000000]Have you ran configure, make and make install for Lucene?[/COLOR]
As I wrote in my question, I did compile Lucene from the git repository. And the different log was clear.

> [COLOR=#000000] If yes, are you sure the Lucene lib can be found by POEdit source,[/COLOR]
the first log is the ```
./configure
``` output.
```
[COLOR=#000000][FONT=Ubuntu Mono]checking for LUCENE... yes[/FONT][/COLOR]
```
I believe poedit found it. Before I compile Lucene I had an exit at that point.

---

### Post by mickro on 2015-07-22
> **steeldriver said:**
> If you want to build poedit from source WITHOUT needing to also build a newer version of liblucene++ yourself, the poedit author/maintainer appears to have provided a PPA that provides a suitable pre-built liblucene++-dev:


[https://launchpad.net/~vslavik/+archive/ubuntu/poedit]("https://launchpad.net/%7Evslavik/+archive/ubuntu/poedit")

```

sudo apt-add-repository ppa:vslavik/poedit

sudo apt-get update

```

You can check the newly available version using
```

sudo apt-cache policy liblucene++-dev
liblucene++-dev:
  Installed: 3.0.4-0ubuntu3
  Candidate: 3.0.6-4~ubuntu14.04.1~ppa1
  Version table:
     3.0.6-4~ubuntu14.04.1~ppa1 0
        500 http://ppa.launchpad.net/vslavik/poedit/ubuntu/ trusty/main amd64 Packages
 *** 3.0.4-0ubuntu3 0
        500 http://ca.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
        100 /var/lib/dpkg/status

```

Then install it

```

sudo apt-get install liblucene++-dev

```


Exactly what I needed. Dankje wel!

---

