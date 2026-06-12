---
title: "c/c++: wprintf, wcout for different locales"
date: 2010-10-10
forum: Programming Talk
---

### Post by japcrword on 2010-10-10
I've got problems when working with wide char strings. 

[PHP]#include <stdio.h>
#include <iostream>

int main (int argc, char * argv []) {
  const char * HelloWorld_char = "&#1042;&#1110;&#1090;&#1072;&#1102;, &#1096;&#1072;&#1085;&#1086;&#1118;&#1085;&#1099; &#1089;&#1087;&#1072;&#1076;&#1072;&#1088;!";
  const wchar_t * HelloWorld_wchar_t = L"&#1042;&#1110;&#1090;&#1072;&#1102;, &#1096;&#1072;&#1085;&#1086;&#1118;&#1085;&#1099; &#1089;&#1087;&#1072;&#1076;&#1072;&#1088;!";

  /* 
   * 1. Test c-style localization & printing 
   */
  printf("Testing printf...\n");
  /* set locale */
  setlocale (LC_ALL, "be_BY.utf8");
  /* print */
  printf("printf char*: '%s'\n", HelloWorld_char); /* ok */
  wprintf(L"wprintf wchar_t*: '%s'\n", HelloWorld_wchar_t); /* ???: prints nothing (as if wprintf not called at all) */
  printf("printf wchar_t*: '%S'\n", HelloWorld_wchar_t); /* ok */
  wprintf(L"wprintf char*: '%S'\n", HelloWorld_char);  /* ???: prints nothing (as if wprintf not called at all) */

  /*
   * 2. Test c++-style localization & printing
   */
  std::cout << "Testing cout..." << std::endl;
  /* set locale */
  std::locale loc("be_BY.utf8");
  std::cout.imbue(loc);
  std::wcout.imbue(loc);
  /* print */
  std::cout << "cout char*: '" << HelloWorld_char << "'" << std::endl; /* ok */
  std::wcout << "wcout wchar_t: '" << HelloWorld_wchar_t << std::endl; /* ???: prints rubbish */
  std::cout << "cout wchar_t*: '" << HelloWorld_wchar_t << "'" << std::endl; /* ok, prints address */
  std::wcout << "wcout char*: '" << HelloWorld_char << "'" << std::endl; /* ???: prints ',  !' */

  return 0;
}

[/PHP]

Can anyone explain why wprintf/wcout don't work as intended? The source file is utf8-encoded and "be_BY.utf8" is among strings which printed by 'locale -a' command. I've checked this code on MS Visual C++ 2008 (with the difference of the source file encoding - win1251 instead of utf8, and locale - "russian_belarus.1251" instead of "be_BY.utf8"). I'm using Ubuntu 10.04 Lucid Lynx 64 bit and g++ (Ubuntu 4.4.3-4ubuntu5) 4.4.3. 

Thank you.

---

### Post by dwhitney67 on 2010-10-10
Please recompile your program with the -pedantic compiler option.  Note that the %S format is not supported in the printf().

Also, consider placing a try/catch around the C++ code.  Unfortunately I do not have the locale you are using; on my system, an exception is thrown.

---

### Post by Npl on 2010-10-10
not sure why wprintf prints nothing at all, but this```
L"&#1042;&#1110;&#1090;&#1072;&#1102;, &#1096;&#1072;&#1085;&#1086;&#1118;&#1085;&#1099; &#1089;&#1087;&#1072;&#1076;&#1072;&#1088;!"
```
is totally wrong, the L operator doesnt correctly encode into UTF16 or whatever encoding you expect, it merely converts char to wchar **numerically**. You should only use it for ascii -> UTF16 conversion, cause thats all thats guaranteed to work.

source-files should always be ascii anyway if you want anything portable.

---

### Post by japcrword on 2010-10-11
> **dwhitney67 said:**
> Please recompile your program with the -pedantic compiler option.  Note that the %S format is not supported in the printf().

Also, consider placing a try/catch around the C++ code.  Unfortunately I do not have the locale you are using; on my system, an exception is thrown.

I got the exception either until I generated the locale be_BY with ```
locale-gen be_BY.utf8
```I compiled it with -pedantic option. Still output is the same. As for %S flag -- I wasn't sure myself, it's Microsoft convention (it's used for printing wchar_t* with printf and char with wprintf*). But printf ate it.

> **Npl said:**
> not sure why wprintf prints nothing at all, but this```
L"&#1042;&#1110;&#1090;&#1072;&#1102;, &#1096;&#1072;&#1085;&#1086;&#1118;&#1085;&#1099; &#1089;&#1087;&#1072;&#1076;&#1072;&#1088;!"
```
is totally wrong, the L operator doesnt correctly encode into UTF16 or whatever encoding you expect, it merely converts char to wchar **numerically**.Then why does[PHP]printf("printf wchar_t*: '%S'\n", HelloWorld_wchar_t); /* ok */[/PHP]work?

---

### Post by Npl on 2010-10-11
> **japcrword said:**
> Then why does[PHP]printf("printf wchar_t*: '%S'\n", HelloWorld_wchar_t); /* ok */[/PHP]work?just because it works for you doesnt mean its standard or will work under other compilers or OSes.

oh, and I got wprintf to output by uncommenting all printf functions, seems as you cant mix them easily. if you call a wprintf function first then printf wont work and vice versa.

[PHP]int main (int argc, char * argv []) { 
  const char * HelloWorld_char = "foobar char"; 
  const wchar_t * HelloWorld_wchar_t = L"foobar wchar";
// if you want some non-ascii stuff you need to initialise with the unicodes
  // const wchar_t HelloWorld_wchar_t[] = {0x0412, 0x0456, 0x0442, 0x0430, 0x044E, 0}; // = "&#1042;&#1110;&#1090;&#1072;&#1102;" in Unicode16

  /*  
   * 1. Test c-style localization & printing  
   */ 
  //printf("Testing printf...\n"); 
  /* set locale */ 
  setlocale (LC_ALL, "utf-16"); 
  /* print */ 
  //printf("printf char*: '%s'\n", HelloWorld_char); /* ok */ 
  wprintf(L"wprintf wchar_t*: '%ls'\n", HelloWorld_wchar_t); /* ???: prints nothing (as if wprintf not called at all) */ 
  printf("printf wchar_t*: '%ls'\n", HelloWorld_wchar_t); /* ok */ 
  wprintf(L"wprintf char*: '%s'\n", HelloWorld_char);  /* ???: prints nothing (as if wprintf not called at all) */ 
}[/PHP]

This still doesnt work with non-ascii stuff in Linux. I guess this is because Linux uses UTF-8 and thus using widechars wont work. might be possible to boot a terminal into UTF16 mode but I wouldnt know how.

Windows uses Unicode16 so the natural fit would be wchars there (and likely the program would work fine)

---

### Post by japcrword on 2010-10-11
> **Npl said:**
> just because it works for you doesnt mean its standard or will work under other compilers or OSes.
Yes, this is true. And I'd like my program to work for any standard compiler. That's why I try to find out the **standard** way of doing things. This is the reason I've started this thread. 

I've experimented a little with streams. The results seem very strange to me. The standard streams look very fragile. For example
this works:[PHP]#include <stdio.h>
#include <iostream>

int main (int argc, char * argv []) {
  const wchar_t * HelloWorld_wchar_t = L"&#1042;&#1110;&#1090;&#1072;&#1102;, &#1096;&#1072;&#1085;&#1086;&#1118;&#1085;&#1099; &#1089;&#1087;&#1072;&#1076;&#1072;&#1088;!";

  setlocale (LC_ALL, "be_BY.utf8");
  wprintf(L"Testing printf...\n");
  std::wcout << "wcout wchar_t: '" << HelloWorld_wchar_t << "'" << std::endl; /* ok */

  return 0;
}[/PHP]But this doesn't:[PHP]#include <stdio.h>
#include <iostream>

int main (int argc, char * argv []) {
  const wchar_t * HelloWorld_wchar_t = L"&#1042;&#1110;&#1090;&#1072;&#1102;, &#1096;&#1072;&#1085;&#1086;&#1118;&#1085;&#1099; &#1089;&#1087;&#1072;&#1076;&#1072;&#1088;!";

  wprintf(L"Testing printf...\n");
  setlocale (LC_ALL, "be_BY.utf8");
  std::wcout << "wcout wchar_t: '" << HelloWorld_wchar_t << "'" << std::endl; /* prints question marks */

  return 0;
}[/PHP]Still this works[PHP]#include <stdio.h>
#include <iostream>

int main (int argc, char * argv []) {
  const wchar_t * HelloWorld_wchar_t = L"&#1042;&#1110;&#1090;&#1072;&#1102;, &#1096;&#1072;&#1085;&#1086;&#1118;&#1085;&#1099; &#1089;&#1087;&#1072;&#1076;&#1072;&#1088;!";

  setlocale (LC_ALL, "be_BY.utf8");
  std::wcout << "wcout wchar_t: '" << HelloWorld_wchar_t << "'" << std::endl; /* ok */

  return 0;
}[/PHP]And this doesn't:[PHP]#include <stdio.h>
#include <iostream>

int main (int argc, char * argv []) {
  const wchar_t * HelloWorld_wchar_t = L"&#1042;&#1110;&#1090;&#1072;&#1102;, &#1096;&#1072;&#1085;&#1086;&#1118;&#1085;&#1099; &#1089;&#1087;&#1072;&#1076;&#1072;&#1088;!";

  std::locale loc("be_BY.utf8");
  std::wcout.imbue(loc);
  std::wcout << "wcout wchar_t: '" << HelloWorld_wchar_t << "'" << std::endl; /* prints question marks */

  return 0;
}[/PHP]I don't think it's a good idea to provide all the code samples I've tried as they were many and not systematic. But I concluded that:

[LIST=1]
[*]setting locale should be done **before** calling any printing functions;
[*]w- and non-w functions/classes should never be mixed together, i.e. you shouldn't use cout and wcout, or printf and wcout (though you probably can use cout with printf, or wcout with wprintf);
[*] and one more piece of advice: global setlocale is sometimes preferable to basic_ios::imbue (especially, like in my case, when basic_ios::imbue doesn't work for some reason).
[/LIST]
 I emphasize that these statements are based on my experiments rather than on my knowledge or c/c++ standards. So if anyone can comment on them I'd appreciate it.

I also would like to thank everyone who found time to discuss my questions.

---

### Post by SledgeHammer_999 on 2010-10-11
I haven't any knowledge on the subject but I am intrigued by it and I want to know more on it. Especially in the C++ way. So I googled "std::locale" and I found a pretty good guide IMHO. Also check it's contents, especially chapters 23-26.

link->[http://stdcxx.apache.org/doc/stdlibug/24-3.html](http://stdcxx.apache.org/doc/stdlibug/24-3.html)

---

### Post by japcrword on 2010-10-11
Thanx for the link. I understand the basic concepts. I agree that setting global locale ain't nice. But, as I said, for some reason using imbue doesn't work for my be_BY.utf8 locale, though std::setlocale does. 
I wonder if this behaviour (of imbue) is specific only to my system or anyone else has similar symptoms?

---

### Post by worksofcraft on 2010-10-11
> **japcrword said:**
> ... But I concluded that:

[LIST=1]
[*]setting locale should be done **before** calling any printing functions;
[*]w- and non-w functions/classes should never be mixed together, i.e. you shouldn't use cout and wcout, or printf and wcout (though you probably can use cout with printf, or wcout with wprintf);
[*] and one more piece of advice: global setlocale is sometimes preferable to basic_ios::imbue (especially, like in my case, when basic_ios::imbue doesn't work for some reason).
[/LIST]
 I emphasize that these statements are based on my experiments rather than on my knowledge or c/c++ standards. So if anyone can comment on them I'd appreciate it.

I also would like to thank everyone who found time to discuss my questions.

I agree with your point of view. I posted something similar regarding wchars and my conclusion was that both standard and the implementation are not useable.

Also I discovered that the ANSI C/C++ standards say you can't expect to use anything other than ASCII in your source code :shock: Fortunately as implemented in gcc, as long as you compile with a UTF-8 locale you can run it on any other utf-8 locale and as far as I'm concerned non utf-8 locales are simply "deprecated" :D

My choice has been to adopt Glib::ustring class which handles utf-8 very nicely and is otherwise a plugin replacement for the STL string class. I avoid wchar and use gunichar which unklike the wchar IS guaranteed to work with unicode :guitar:


p.s. a word of caution: If you plan to internationalize your software and use the gettext package to implement multiple locales I discovered that when used from some languages (e.g. Python) it flatly refuses to translate strings that have non ascii codes in the original although it works ok for C++. Also I don't think gettext works at all with wchars and I really hope they don't waste their time implementing it ;)

while I'm at it here is the code to see what I mean:
```

#!/usr/bin/python
# -*- coding: UTF-8 -*-
# file: uber.py
import gettext
gettext.bindtextdomain('uber', '')
gettext.textdomain('uber')
print gettext.gettext('UTF-8 Über Ascii')
print gettext.gettext('UTF-8 Uber Ascii')

```
here is translation file uber.po
```

# English translations for uber package.
# Copyright (C) 2010 public domain
# This file is distributed under the same license as the PACKAGE package.
# cjs 2010.
#
msgid ""
msgstr ""
"Project-Id-Version: PACKAGE VERSION\n"
"Report-Msgid-Bugs-To: \n"
"POT-Creation-Date: 2010-10-12 11:36+1300\n"
"PO-Revision-Date: 2010-10-12 11:38+1300\n"
"Last-Translator: cjs\n"
"Language-Team: English\n"
"MIME-Version: 1.0\n"
"Content-Type: text/plain; charset=UTF-8\n"
"Content-Transfer-Encoding: 8bit\n"
"Plural-Forms: nplurals=2; plural=(n != 1);\n"

#: uber.py:6
msgid "UTF-8 Über Ascii"
msgstr "Non ascii original"

#: uber.py:7
msgid "UTF-8 Uber Ascii"
msgstr "translated ascii"

```
here are commands to install translation and sample output
```

$> msgfmt -o uber.mo uber.po
$> sudo cp uber.mo /usr/share/locale/en/LC_MESSAGES
$> ./uber.py
UTF-8 Über Ascii
translated

```
... hum, lol... it seems to have left out part of the ascii string translation as well... but anyway I think it does show there are problems with writing programs that are not native ascii :shock: My most trusted solution is to write only ascii in the source and use gettext to generate utf-8 and don't touch wchar with a barge-pole even if have you have one handy!

---

