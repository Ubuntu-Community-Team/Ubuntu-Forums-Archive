---
title: "make: *** [install_config] Error 1"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by Lourie2 on 2008-06-01
I am trying to install an application (Sword) but am unable to continue.  At this stage, I am unable to proceed as the following error has occurred.

```
name@name-IBM:~/Desktop/sword/sword-1.5.11$ make install_config
/bin/bash: /etc/sword.conf: Permission denied
make: *** [install_config] Error 1
```

This happens after I failed the previous command:

```
name@name-IBM:~/Desktop/sword/sword-1.5.11$ sudo make install
[sudo] password for name: 
Making install in lib
make[1]: Entering directory `/home/name/Desktop/sword/sword-1.5.11/lib'
/bin/bash ../libtool --tag=CXX   --mode=compile g++ -DHAVE_CONFIG_H -I. -I../include  -I../include -DUSE_AUTOTOOLS -DUNIX -Dunix -D__unix__  -DSWICU_DATA=\"/usr/lib/sword/1.5.11_icu_2.1\"   -D_FTPLIB_NO_COMPAT -D_ICU_ -DUSBINARY -O2 -D_ICU_ -ftemplate-depth-25  -MT utilstr.lo -MD -MP -MF .deps/utilstr.Tpo -c -o utilstr.lo `test -f '../src/utilfuns/utilstr.cpp' || echo './'`../src/utilfuns/utilstr.cpp
 g++ -DHAVE_CONFIG_H -I. -I../include -I../include -DUSE_AUTOTOOLS -DUNIX -Dunix -D__unix__ -DSWICU_DATA=\"/usr/lib/sword/1.5.11_icu_2.1\" -D_FTPLIB_NO_COMPAT -D_ICU_ -DUSBINARY -O2 -D_ICU_ -ftemplate-depth-25 -MT utilstr.lo -MD -MP -MF .deps/utilstr.Tpo -c ../src/utilfuns/utilstr.cpp -o utilstr.o
../src/utilfuns/utilstr.cpp:9:28: error: unicode/utypes.h: No such file or directory
../src/utilfuns/utilstr.cpp:10:26: error: unicode/ucnv.h: No such file or directory
../src/utilfuns/utilstr.cpp:11:29: error: unicode/ustring.h: No such file or directory
../src/utilfuns/utilstr.cpp:12:27: error: unicode/uchar.h: No such file or directory
../src/utilfuns/utilstr.cpp:14:28: error: unicode/unistr.h: No such file or directory
../src/utilfuns/utilstr.cpp:15:30: error: unicode/translit.h: No such file or directory
make[1]: *** [utilstr.lo] Error 1
make[1]: Leaving directory `/home/name/Desktop/sword/sword-1.5.11/lib'
make: *** [install-recursive] Error 1
```

Should I "undo" the installation I have done so far and start over?  How would I do that, if I cannot proceed from here?

---

### Post by Joeb454 on 2008-06-01
Having had a quick look - unless you absolutely *need* to compile it from source - sword is in the repo's I think :)

---

### Post by Jive Turkey on 2008-06-01
I haven't used that app but I would approach it with these commands in the source's directory:

```
./configure
make
sudo make install
```

I don't think it will matter if you remove the directories and files created in the previous attempts or not, it hasn't for me in the past.  I could be wrong.

---

### Post by bumanie on 2008-06-01
Read the 'read me' text document in the extracted file. If you don't understand what it says, post it for some help.

---

### Post by Lourie2 on 2008-06-01
I found some Sword files but realised I needed the application and eventually found GnomeSword.  Thanks for pointing me in the right direction!

---

### Post by Joeb454 on 2008-06-01
Glad you found it :) Repo's are always easier than compiling - but at least you have the choice :)

---

