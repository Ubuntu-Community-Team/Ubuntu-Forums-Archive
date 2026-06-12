---
title: "Subversion 1.4.3 package"
date: 2007-03-08
forum: Programming Talk
---

### Post by gabrielsaldana on 2007-03-08
I use Subclipse to work with svn from my Eclipse IDE. I recently upgraded to subclipse 1.2 and now my repositories said that my svn client was too old.

So this brings me to the necesity of upgrading subversion, but given that on the repositories there is only version 1.3.2, I had to compile from source.

I made a package, but I'm a total newbie in this subject. I can't guarantee that it will work for you (help on this topic would be very well appreciated). 

[http://www.nethazard.net/subversion/subversion_1.4.3-1_i386.deb](http://www.nethazard.net/subversion/subversion_1.4.3-1_i386.deb)

So here I'll give you the instructions to get 1.4.3 from source in case my package didn't work.

Get subversion source:
```

wget [http://subversion.tigris.org/downloads/subversion-1.4.3.tar.gz](http://subversion.tigris.org/downloads/subversion-1.4.3.tar.gz)
wget [http://subversion.tigris.org/downloads/subversion-deps-1.4.3.tar.gz](http://subversion.tigris.org/downloads/subversion-deps-1.4.3.tar.gz)

```and extract the files:
```

tar xvzf subversion-1.4.3.tar.gz
tar xvzf subversion-deps-1.4.3.tar.gz

```Okay, now to the building process...

First, make sure you have all development tools

```

sudo aptitude install build-essential

```then install some dependencies
```

sudo aptitude install libapr1 libapr1-dev libaprutil1 libaprutil1-dev

``````

sudo apt-get install libneon25 libneon25-dev

``````

sudo apt-get install libdb4.3 libdb4.3-dev db4.3-util libdb4.3++c2 libdb4.3++-dev

``````

 sudo apt-get install checkinstall auto-apt

```Finally the compiling steps to build the package and install it:
```

auto-apt run ./configure --with-ssl --with-apr=/usr/bin/apr-config --with-apr-util=/usr/bin/apu-config 

``````

make

sudo checkinstall

```and you are done.

---

### Post by roboguy on 2007-03-21
If you are an amd64 user you might find the following helpful [http://jamesfitzsimons.blogspot.com/2007/03/subversion-143-on-ubuntu-edgy-amd64.html](http://jamesfitzsimons.blogspot.com/2007/03/subversion-143-on-ubuntu-edgy-amd64.html)

---

### Post by andrewroth on 2007-04-03
This post is literally a year old.  Why is there no 1.4 ubuntu subversion package?  This feels like debian!!  Everyone is compiling 1.4 themselves or using unofficial packages, someone who can should really put it in the official repository!

---

### Post by Co.Sinecure on 2007-04-04
Agreed...I've found myself in the same situation with the code base i share between windows and linux...Tortoise SVN has upgraded to 1.4, subclipse has upgraded...

---

### Post by WW on 2007-04-04
This is the nature of ubuntu.    If you need the latest version of a particular piece of software, you must compile it yourself. In some cases, the developers of the program or some third party may provide a binary package.  Or you can prod the backporters to backport the program to whatever version of ubuntu you are using: [http://ubuntuforums.org/showthread.php?t=40291](http://ubuntuforums.org/showthread.php?t=40291)

feisty has subversion 1.4.3, so in a few weeks, you can upgrade, and get *lots* of shiny new (well, relatively new) software.

---

### Post by jvc26 on 2007-04-04
The repos are not changed once the full release comes out except for security patches and bugfixes - its to make sure that all the packages work properly with that distro of ubuntu just in case a new version breaks your ubuntu install. When you upgrade to the new Ubuntu you then get all the new packages as new as when the release comes out.
Il

---

### Post by Tookelso on 2007-04-06
Thank you very much Gabrielsadana.

I didn't install your .deb package, I followed your compile instructions, and you saved me.

I've been using Eclipse, and upgraded to 1.4.3 in the Eclipse stuff.  This totally messed up my other projects that weren't using Eclipse, because my svn was on version 1.3.2

Now, I can check in / check out my non-Eclipse projects from the command line!

One note:  

Before you run this line

```
auto-apt run ./configure --with-ssl <snip>
```

You should cd into the subversion1.4.3 directory, because that's where the ./configure script is.  You might want to edit your original post to tell newbs that they need to cd to the directory where they un-tarred the files.

Thanks again!

--Took

---

### Post by 21croissants on 2007-04-11
I have adapted a script found on internet to install in one click subversion 1.4.2 on ubuntu Edgy
check out [http://21croissants.blogspot.com/2007/04/set-up-subversion-for-netbeans-on.html](http://21croissants.blogspot.com/2007/04/set-up-subversion-for-netbeans-on.html)

---

### Post by donjefe on 2007-04-30
I had no luck with the configure command, but this works for me:

```
apt-get install apache2-devel
```

```
auto-apt run ./configure --with-ssl --with-apxs=/usr/bin/apxs2
```

---

### Post by jespdj on 2007-05-01
I don't know which Ubuntu version you are all using, but I'm using 7.04 (64-bit) and installed Subversion via the package management system and got version 1.4.3.

So for Ubuntu 7.04 at least there is an up-to-date Subversion package.

---

### Post by deez0n on 2007-06-07
> **jespdj said:**
> I don't know which Ubuntu version you are all using, but I'm using 7.04 (64-bit) and installed Subversion via the package management system and got version 1.4.3.

So for Ubuntu 7.04 at least there is an up-to-date Subversion package.


This thread is for folks still using LTS (there are a few of us out here who can't do the upgrade to Fiesty for one reason or another)

Thanks
  ds

---

### Post by ssmohan on 2007-08-28
> **21croissants said:**
> I have adapted a script found on internet to install in one click subversion 1.4.2 on ubuntu Edgy
check out [http://21croissants.blogspot.com/2007/04/set-up-subversion-for-netbeans-on.html](http://21croissants.blogspot.com/2007/04/set-up-subversion-for-netbeans-on.html)

Greetings,
  Thank you!  I have an inspiron 1420 with triple boot of dapper/feisty/vista and all three need to use subversion to modify files in a shared partition.  The script saved me a lot of hassle to get 1.4.3 running on dapper.  I was trying to use prevu to accomplish the same task, but ran in to all kinds of dependency issues.    The above script worked without a hitch after changing all 1.4.2 occurences to 1.4.3.

  Thanks again!

---

### Post by honzik.nemec@seznam.cz on 2007-12-17
Thanks a lot! This howto saved the day for me :-)

---

### Post by antitalented on 2008-04-28
Hello,
I followed ur steps. everything worked fine until the make command. Below is the error log. Please help.

subversion/libsvn_subr/xml.c:34:19: error: expat.h: No such file or directory
subversion/libsvn_subr/xml.c:45: error: syntax error before 'XML_Parser'
subversion/libsvn_subr/xml.c:45: warning: no semicolon at end of struct or union
subversion/libsvn_subr/xml.c:61: error: syntax error before '}' token
subversion/libsvn_subr/xml.c:306: warning: type defaults to 'int' in declaration of 'XML_Char'
subversion/libsvn_subr/xml.c:306: error: syntax error before '*' token
subversion/libsvn_subr/xml.c: In function 'expat_start_handler':
subversion/libsvn_subr/xml.c:309: error: 'userData' undeclared (first use in this function)
subversion/libsvn_subr/xml.c:309: error: (Each undeclared identifier is reported only once
subversion/libsvn_subr/xml.c:309: error: for each function it appears in.)
subversion/libsvn_subr/xml.c:311: error: dereferencing pointer to incomplete type
subversion/libsvn_subr/xml.c:311: error: dereferencing pointer to incomplete type
subversion/libsvn_subr/xml.c:311: error: 'name' undeclared (first use in this function)
subversion/libsvn_subr/xml.c:311: error: 'atts' undeclared (first use in this function)
subversion/libsvn_subr/xml.c: At top level:
subversion/libsvn_subr/xml.c:314: warning: type defaults to 'int' in declaration of 'XML_Char'
subversion/libsvn_subr/xml.c:314: error: syntax error before '*' token
subversion/libsvn_subr/xml.c: In function 'expat_end_handler':
subversion/libsvn_subr/xml.c:316: error: 'userData' undeclared (first use in this function)
subversion/libsvn_subr/xml.c:318: error: dereferencing pointer to incomplete type
subversion/libsvn_subr/xml.c:318: error: dereferencing pointer to incomplete type
subversion/libsvn_subr/xml.c:318: error: 'name' undeclared (first use in this function)
subversion/libsvn_subr/xml.c: At top level:
subversion/libsvn_subr/xml.c:321: warning: type defaults to 'int' in declaration of 'XML_Char'
subversion/libsvn_subr/xml.c:321: error: syntax error before '*' token
subversion/libsvn_subr/xml.c: In function 'expat_data_handler':
subversion/libsvn_subr/xml.c:323: error: 'userData' undeclared (first use in this function)
subversion/libsvn_subr/xml.c:325: error: dereferencing pointer to incomplete type
subversion/libsvn_subr/xml.c:325: error: dereferencing pointer to incomplete type
subversion/libsvn_subr/xml.c:325: error: 's' undeclared (first use in this function)
subversion/libsvn_subr/xml.c:325: error: 'len' undeclared (first use in this function)
subversion/libsvn_subr/xml.c: In function 'svn_xml_make_parser':
subversion/libsvn_subr/xml.c:341: error: 'XML_Parser' undeclared (first use in this function)
subversion/libsvn_subr/xml.c:341: error: syntax error before 'parser'
subversion/libsvn_subr/xml.c:343: warning: implicit declaration of function 'XML_SetElementHandler'
subversion/libsvn_subr/xml.c:343: error: 'parser' undeclared (first use in this function)
subversion/libsvn_subr/xml.c:346: warning: implicit declaration of function 'XML_SetCharacterDataHandler'
subversion/libsvn_subr/xml.c:353: error: dereferencing pointer to incomplete type
subversion/libsvn_subr/xml.c:353: error: dereferencing pointer to incomplete type
subversion/libsvn_subr/xml.c:355: error: dereferencing pointer to incomplete type
subversion/libsvn_subr/xml.c:356: error: dereferencing pointer to incomplete type
subversion/libsvn_subr/xml.c:357: error: dereferencing pointer to incomplete type
subversion/libsvn_subr/xml.c:358: error: dereferencing pointer to incomplete type
subversion/libsvn_subr/xml.c:359: error: dereferencing pointer to incomplete type
subversion/libsvn_subr/xml.c:360: error: dereferencing pointer to incomplete type
subversion/libsvn_subr/xml.c:363: warning: implicit declaration of function 'XML_SetUserData'
subversion/libsvn_subr/xml.c: In function 'svn_xml_free_parser':
subversion/libsvn_subr/xml.c:374: warning: implicit declaration of function 'XML_ParserFree'
subversion/libsvn_subr/xml.c:374: error: dereferencing pointer to incomplete type
subversion/libsvn_subr/xml.c:377: error: dereferencing pointer to incomplete type
subversion/libsvn_subr/xml.c: In function 'svn_xml_parse':
subversion/libsvn_subr/xml.c:393: warning: implicit declaration of function 'XML_Parse'
subversion/libsvn_subr/xml.c:393: error: dereferencing pointer to incomplete type
subversion/libsvn_subr/xml.c:401: warning: implicit declaration of function 'XML_ErrorString'
subversion/libsvn_subr/xml.c:401: warning: implicit declaration of function 'XML_GetErrorCode'
subversion/libsvn_subr/xml.c:401: error: dereferencing pointer to incomplete type
subversion/libsvn_subr/xml.c:402: warning: implicit declaration of function 'XML_GetCurrentLineNumber'
subversion/libsvn_subr/xml.c:402: error: dereferencing pointer to incomplete type
subversion/libsvn_subr/xml.c:402: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
subversion/libsvn_subr/xml.c:410: error: dereferencing pointer to incomplete type
subversion/libsvn_subr/xml.c:412: error: dereferencing pointer to incomplete type
subversion/libsvn_subr/xml.c: In function 'svn_xml_signal_bailout':
subversion/libsvn_subr/xml.c:426: error: dereferencing pointer to incomplete type
subversion/libsvn_subr/xml.c:427: error: dereferencing pointer to incomplete type
subversion/libsvn_subr/xml.c:431: error: dereferencing pointer to incomplete type
make: *** [subversion/libsvn_subr/xml.lo] Error 1
anirudh@anirudh:~/subversion-1.4.3$

---

### Post by antitalented on 2008-04-28
a

---

