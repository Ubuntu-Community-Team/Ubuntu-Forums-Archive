---
title: "Problem compiling xmlcopyeditor-1.2.0.10"
date: 2014-03-26
forum: Packaging and Compiling Programs
---

### Post by Keith_Beef on 2014-03-26
The title says it all.

The version of xmlcopyeditor in the repositories does not work. The most recent source code requires a library that is not available for 12.04LTS, so I downloaded the source for version 1.2.0.10.

I had to install quite a few libraries to get the configure script to complete, but then make failed.

Details of the steps and the libraries I installed are below.

install libxslt1-dev
unpack the tarball to /usr/local/src
run configure script

```
checking for pcre.h... no
configure: error: PCRE headers not found
```


install libpcre++0

```
checking for pcre.h... no
configure: error: PCRE headers not found
```

install libpcre++-dev and libpcrecpp0
```

checking xercesc/util/PlatformUtils.hpp usability... no
checking xercesc/util/PlatformUtils.hpp presence... no
checking for xercesc/util/PlatformUtils.hpp... no
configure: error: Xerces-C headers not found
```


install libxerces-c-dev
```

checking for ENCHANT... no
checking aspell.h usability... no
checking aspell.h presence... no
checking for aspell.h... no
configure: error: Aspell headers not found
```


install libenchant-dev and libglib2.0-dev
install libaspell-dev

```
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: executing depfiles commands
config.status: executing libtool commands

***************************************

Debug               Disabled
```

looks like configure worked.

make ends with this:

```
wrapxerces.cpp: In static member function &#8216;static const wxMBConv& WrapXerces::getMBConv()&#8217;:
wrapxerces.cpp:214:52: error: &#8216;BOOST_STATIC_ASSERT_MSG&#8217; was not declared in this scope
make[1]: *** [wrapxerces.o] Error 1
make[1]: Leaving directory `/usr/local/src/xmlcopyeditor-1.2.0.10/src'
make: *** [all-recursive] Error 1

```

---

### Post by steeldriver on 2014-03-26
perhaps you're missing libboost-dev ?

---

### Post by Keith_Beef on 2014-03-27
> **steeldriver said:**
> perhaps you're missing libboost-dev ?

It's an idea&#8230; I'll try it in a couple of hours. But how could I have known from that message that missing libboost-dev might be the culprit? I would have expected the presence of required libraries to be verified during the configure step, not during make.

I think you might be right. Now that I've spent a good ten minutes searching for a list of dependencies, I've found [this page]("http://sourceforge.net/p/xml-copy-editor/code/ci/1.2.0.10/tree/INSTALL").

It lists:
> Dependencies (libraries that need to be present before the tarball compiles)
============================================================================

pcre-devel
aspell-devel
boost
boost-devel
xerces-c
xerces-c-devel
libxml-devel
libxslt-devel
expat-devel

Boost and boost-devel are listed, but they seem to have different names in Ubuntu.

I'm going to install  libboost-all-dev (this grabs a load of other packages as well) and try again.

Still fails, but with a different message, so boost was indeed one of the culprits.

```
wrapaspell.cpp: In constructor &#8216;WrapAspell::WrapAspell(wxString)&#8217;:
wrapaspell.cpp:43:51: error: no matching function for call to &#8216;enchant::Broker::request_dict(const wxString&)&#8217;
wrapaspell.cpp:43:51: note: candidate is:
/usr/include/enchant/enchant++.h:224:11: note: enchant::Dict* enchant::Broker::request_dict(const string&)
/usr/include/enchant/enchant++.h:224:11: note:   no known conversion for argument 1 from &#8216;const wxString&#8217; to &#8216;const string& {aka const std::basic_string<char>&}&#8217;
make[1]: *** [wrapaspell.o] Error 1
make[1]: Leaving directory `/usr/local/src/xmlcopyeditor-1.2.0.10/src'
make: *** [all-recursive] Error 1
```

So going back to that list I found, libxml-devel and libxslt-devel might correspond to libxml++2.6-dev (not yet installed) and libxslt1-dev (already installed).

---

