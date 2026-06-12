---
title: "link error when making gedit in ubuntu 10.04"
date: 2011-03-06
forum: Programming Talk
---

### Post by shimmey on 2011-03-06
I have installed all the packages for making gedit already.
But when linking it, there are some errors:

  CCLD   gedit
/usr/lib/gcc/i486-linux-gnu/4.4.3/../../../../lib/libgtksourceview-2.0.so: undefined reference to `xmlTextReaderExpand@LIBXML2_2.5.7'
/usr/lib/gcc/i486-linux-gnu/4.4.3/../../../../lib/libgtksourceview-2.0.so: undefined reference to `xmlParseMemory@LIBXML2_2.4.30'
/usr/lib/gcc/i486-linux-gnu/4.4.3/../../../../lib/libgtksourceview-2.0.so: undefined reference to `xmlFree@LIBXML2_2.4.30'
/usr/lib/gcc/i486-linux-gnu/4.4.3/../../../../lib/libgtksourceview-2.0.so: undefined reference to `xmlStrcasecmp@LIBXML2_2.4.30'
/usr/lib/gcc/i486-linux-gnu/4.4.3/../../../../lib/libgtksourceview-2.0.so: undefined reference to `xmlNodeGetContent@LIBXML2_2.4.30'
/usr/lib/gcc/i486-linux-gnu/4.4.3/../../../../lib/libgtksourceview-2.0.so: undefined reference to `xmlStrdup@LIBXML2_2.4.30'
/usr/lib/gcc/i486-linux-gnu/4.4.3/../../../../lib/libgtksourceview-2.0.so: undefined reference to `xmlTextReaderRead@LIBXML2_2.4.30'
/usr/lib/gcc/i486-linux-gnu/4.4.3/../../../../lib/libgtksourceview-2.0.so: undefined reference to `xmlTextReaderConstName@LIBXML2_2.6.0'
/usr/lib/gcc/i486-linux-gnu/4.4.3/../../../../lib/libgtksourceview-2.0.so: undefined reference to `xmlTextReaderGetAttribute@LIBXML2_2.5.0'
/usr/lib/gcc/i486-linux-gnu/4.4.3/../../../../lib/libgtksourceview-2.0.so: undefined reference to `xmlGetProp@LIBXML2_2.4.30'
/usr/lib/gcc/i486-linux-gnu/4.4.3/../../../../lib/libgtksourceview-2.0.so: undefined reference to `xmlTextReaderValue@LIBXML2_2.4.30'
/usr/lib/gcc/i486-linux-gnu/4.4.3/../../../../lib/libgtksourceview-2.0.so: undefined reference to `xmlNodeListGetString@LIBXML2_2.4.30'
/usr/lib/gcc/i486-linux-gnu/4.4.3/../../../../lib/libgtksourceview-2.0.so: undefined reference to `xmlTextReaderSetStructuredErrorHandler@LIBXML2_2.6.6'
/usr/lib/gcc/i486-linux-gnu/4.4.3/../../../../lib/libgtksourceview-2.0.so: undefined reference to `xmlFreeDoc@LIBXML2_2.4.30'
/usr/lib/gcc/i486-linux-gnu/4.4.3/../../../../lib/libgtksourceview-2.0.so: undefined reference to `xmlTextReaderNodeType@LIBXML2_2.4.30'
/usr/lib/gcc/i486-linux-gnu/4.4.3/../../../../lib/libgtksourceview-2.0.so: undefined reference to `xmlTextReaderIsEmptyElement@LIBXML2_2.4.30'
/usr/lib/gcc/i486-linux-gnu/4.4.3/../../../../lib/libgtksourceview-2.0.so: undefined reference to `xmlGetLineNo@LIBXML2_2.4.30'
/usr/lib/gcc/i486-linux-gnu/4.4.3/../../../../lib/libgtksourceview-2.0.so: undefined reference to `xmlTextReaderName@LIBXML2_2.4.30'
/usr/lib/gcc/i486-linux-gnu/4.4.3/../../../../lib/libgtksourceview-2.0.so: undefined reference to `xmlKeepBlanksDefault@LIBXML2_2.4.30'
/usr/lib/gcc/i486-linux-gnu/4.4.3/../../../../lib/libgtksourceview-2.0.so: undefined reference to `xmlStrcmp@LIBXML2_2.4.30'
/usr/lib/gcc/i486-linux-gnu/4.4.3/../../../../lib/libgtksourceview-2.0.so: undefined reference to `xmlReaderForFd@LIBXML2_2.6.0'
/usr/lib/gcc/i486-linux-gnu/4.4.3/../../../../lib/libgtksourceview-2.0.so: undefined reference to `xmlDocGetRootElement@LIBXML2_2.4.30'
/usr/lib/gcc/i486-linux-gnu/4.4.3/../../../../lib/libgtksourceview-2.0.so: undefined reference to `xmlTextReaderRelaxNGValidate@LIBXML2_2.5.7'
/usr/lib/gcc/i486-linux-gnu/4.4.3/../../../../lib/libgtksourceview-2.0.so: undefined reference to `xmlTextReaderIsValid@LIBXML2_2.5.7'
/usr/lib/gcc/i486-linux-gnu/4.4.3/../../../../lib/libgtksourceview-2.0.so: undefined reference to `xmlLineNumbersDefault@LIBXML2_2.4.30'
/usr/lib/gcc/i486-linux-gnu/4.4.3/../../../../lib/libgtksourceview-2.0.so: undefined reference to `xmlTextReaderCurrentNode@LIBXML2_2.5.0'
/usr/lib/gcc/i486-linux-gnu/4.4.3/../../../../lib/libgtksourceview-2.0.so: undefined reference to `xmlFreeTextReader@LIBXML2_2.4.30'
/usr/lib/gcc/i486-linux-gnu/4.4.3/../../../../lib/libgtksourceview-2.0.so: undefined reference to `xmlSubstituteEntitiesDefault@LIBXML2_2.4.30'

I did download the source code of libxml2.0, and made it then installed it. why is there also errors?
What should I do to solve it?
Thanks very much for all...

---

### Post by gmargo on 2011-03-06
You probably need to install the **libxml2-dev** package to gedit to link properly.

To make sure all the build dependencies of **gedit** are installed, use the build-dep function of **apt-get** or** aptitude**:
```

sudo apt-get build-dep gedit

```

---

### Post by shimmey on 2011-03-06
Yeah, thanks for your answer!

I downloaded the source code of libxml2.
And then make installed it successfully.
Your command was ran already.
But the problem still unsolved.
Is there anythiing more I need to do before make gedit?

Maybe I install libxml by source, this caused the library of system problem.
If so, how could uninstall the libxml, and then reinstall it by apt-get?
thanks!

---

### Post by shimmey on 2011-03-06
Yeah, thanks for your answer!

I downloaded the source code of libxml2.
And then make installed it successfully.
Your command was ran already.
But the problem still unsolved.
Is there anythiing more I need to do before make gedit?

Maybe I install libxml by source, this caused the library of system problem.
If so, how could uninstall the libxml, and then reinstall it by apt-get?
thanks!

---

### Post by shimmey on 2011-04-01
Well, I did all as you said exactly.
But, what did ubuntu installed? And where are the installed source code and documents?
After I executed your command, then, could I download the source code of gedit and make them directly?
Thanks very much!

---

### Post by shimmey on 2011-04-01
Well, I did all as you said exactly.
But, what did ubuntu installed? And where are the installed source code and documents?
After I executed your command, then, could I download the source code of gedit and make them directly?
Thanks very much!

---

### Post by gmargo on 2011-04-01
Here's a simple set of steps that will compile **gedit** under [COLOR=Magenta]10.04 Lucid[COLOR=Black].  If you have installed any libraries manually, you should remove them or take steps to avoid them.  The following does everything from the Lucid repositories.

```

sudo apt-get build-dep gedit
apt-get source gedit
cd gedit-2.30.3/
dpkg-buildpackage -b -us -uc

```which compiles gedit and results in:
```

$ cd .. ; ls -lgG
total 11912
drwxr-xr-x 15    4096 2011-04-01 13:07 gedit-2.30.3
-rw-r--r--  1    1750 2011-04-01 13:08 gedit_2.30.3-0ubuntu0.1_amd64.changes
-rw-r--r--  1  577268 2011-04-01 13:08 gedit_2.30.3-0ubuntu0.1_amd64.deb
-rw-r--r--  1   18471 2010-06-24 14:06 gedit_2.30.3-0ubuntu0.1.diff.gz
-rw-r--r--  1    1969 2010-06-24 14:06 gedit_2.30.3-0ubuntu0.1.dsc
-rw-r--r--  1 7036397 2010-06-21 07:05 gedit_2.30.3.orig.tar.gz
-rw-r--r--  1 4421056 2011-04-01 13:08 gedit-common_2.30.3-0ubuntu0.1_all.deb
-rw-r--r--  1  123466 2011-04-01 13:08 gedit-dev_2.30.3-0ubuntu0.1_all.deb

```[/COLOR][/COLOR]

---

### Post by shimmey on 2011-04-02
Great! I've done all successfully!
Thanks a lot for all your help!

---

