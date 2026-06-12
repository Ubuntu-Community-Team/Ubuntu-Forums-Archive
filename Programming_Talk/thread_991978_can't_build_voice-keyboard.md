---
title: "can't build voice-keyboard"
date: 2008-11-24
forum: Programming Talk
---

### Post by Paul S on 2008-11-24
I can't build voice-keyboard ([http://ftp.heanet.ie/disk1/sourceforge/v/vo/voicekey/](http://ftp.heanet.ie/disk1/sourceforge/v/vo/voicekey/))
I'm running ubuntu and have tried on both 8.04.1 32-bit and 8.10 64-bit, with both gcc4.2 and gcc3.3, with both python2.5 and python2.4

First step works:
sphinxbase-0.4 ([http://superb-east.dl.sourceforge.net/sourceforge/cmusphinx/sphinxbase-0.4.tar.bz2](http://superb-east.dl.sourceforge.net/sourceforge/cmusphinx/sphinxbase-0.4.tar.bz2)) builds.

Second step fails:
sphinx3-0.7 ([http://internap.dl.sourceforge.net/sourceforge/cmusphinx/sphinx3-0.7.tar.gz](http://internap.dl.sourceforge.net/sourceforge/cmusphinx/sphinx3-0.7.tar.gz)) will configure but won't make, with this error:
 gcc -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"sphinx3\" -DVERSION=\"0.7\
" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DH
AVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DSTDC_HEADERS=1 -DHAVE_MEMMOVE=1 -DHAVE_BCOPY=1 -DRETSIGTYPE=void -DHAVE_DLFCN_H=1 -I. -I. -I../../.. -I../../../include -
I../../../include -I/usr/include/sphinxbase -I/usr/local/include/sphinxbase -g -O2 -Wall -ansi -MT gs.lo -MD -MP -MF .deps/gs.Tpo -c gs.c  -fPIC -DPIC -o .l
ibs/gs.o
gs.c: In function 'gs_fread_bitvec_t':
gs.c:85: warning: passing argument 1 of 'fread' makes pointer from integer without a cast
gs.c: In function 'gs_display':
gs.c:116: warning: implicit declaration of function 'bitvec_uint32size'
gs.c:120: warning: assignment makes integer from pointer without a cast
gs.c:137: error: subscripted value is neither array nor pointer
gs.c: In function 'gs_read':
gs.c:187: warning: assignment makes integer from pointer without a cast
gs.c:210: error: invalid type argument of 'unary *'
make[3]: *** [gs.lo] Error 1
make[3]: Leaving directory `/home/paul/voicekey.bld/sphinx3/src/libs3decoder/libam'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/paul/voicekey.bld/sphinx3/src/libs3decoder'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/paul/voicekey.bld/sphinx3/src'
make: *** [all-recursive] Error 1

Alternative older version of sphinx3 builds:
sphinx3-0.6.3 ([http://voxel.dl.sourceforge.net/sourceforge/cmusphinx/sphinx3-0.6.3.tar.gz](http://voxel.dl.sourceforge.net/sourceforge/cmusphinx/sphinx3-0.6.3.tar.gz)) builds

Next step works with alternative sphinx3:
lm3g2dmp ([http://cmusphinx.org/download/nightly/lm3g2dmp.nightly.tar.gz](http://cmusphinx.org/download/nightly/lm3g2dmp.nightly.tar.gz)) will build with sphinx3-0.6.3

Next step works with alternative sphinx3:
Sphinxtrain ([http://cmusphinx.org/download/nightly/SphinxTrain.nightly.tar.gz](http://cmusphinx.org/download/nightly/SphinxTrain.nightly.tar.gz)) will build with sphinx3-0.6.3

Next step fails with alternative sphinx3:
voicekey won't build with sphinx3-0.6.3:
~/voicekey.bld/voice-keyboard$ make
gcc sphinx3_livesegment.c -I/home/paul/voickey.bld/sphinxbase/include -I/home/paul/voicekey.bld/sphinx3/include -lsphinxad -ls3decoder -lm -o sphinx3_livese
gment
sphinx3_livesegment.c:67:23: error: s3_decode.h: No such file or directory
In file included from sphinx3_livesegment.c:70:
/home/paul/voicekey.bld/sphinx3/include/ad.h:133:21: error: ad_conf.h: No such file or directory
sphinx3_livesegment.c:85: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘decoder’
sphinx3_livesegment.c:86: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
sphinx3_livesegment.c: In function ‘reset_beam’:
sphinx3_livesegment.c:111: error: ‘decoder’ undeclared (first use in this function)
sphinx3_livesegment.c:111: error: (Each undeclared identifier is reported only once
sphinx3_livesegment.c:111: error: for each function it appears in.)
sphinx3_livesegment.c:122: error: ‘srch_t’ undeclared (first use in this function)
sphinx3_livesegment.c:122: error: expected expression before ‘)’ token
sphinx3_livesegment.c: In function ‘set_cmd’:
sphinx3_livesegment.c:134: error: ‘decoder’ undeclared (first use in this function)
sphinx3_livesegment.c: In function ‘utterance_loop’:
sphinx3_livesegment.c:347: error: ‘decoder’ undeclared (first use in this function)
sphinx3_livesegment.c:361: error: ‘fe’ undeclared (first use in this function)
sphinx3_livesegment.c: In function ‘main’:
sphinx3_livesegment.c:510: error: ‘S3_DECODE_ARG_DEFS’ undeclared (first use in this function)
sphinx3_livesegment.c:510: error: too many arguments to function ‘cmd_ln_parse’
sphinx3_livesegment.c:519: error: ‘fe’ undeclared (first use in this function)
sphinx3_livesegment.c:522: error: ‘decoder’ undeclared (first use in this function)
make: *** [sphinx3_livesegment] Error 1

Back to beginning to try svn version (11/24/08) of sphinxbase, which fails:
sphinxbase from svn ([http://sphinx.subwiki.com/sphinx/index.php/Main_Page](http://sphinx.subwiki.com/sphinx/index.php/Main_Page)) will autogen, make and make check,
but not install (tried both python2.4 and python2.5) with this error:
writing manifest file 'SphinxBase.egg-info/SOURCES.txt'
Traceback (most recent call last):
  File "setup.py", line 58, in ?
    cmdclass = {'bogus_uninstall' : bogus_uninstall}
  File "/usr/lib/python2.4/distutils/core.py", line 149, in setup
    dist.run_commands()
  File "/usr/lib/python2.4/distutils/dist.py", line 946, in run_commands
    self.run_command(cmd)
  File "/usr/lib/python2.4/distutils/dist.py", line 966, in run_command
    cmd_obj.run()
  File "/usr/lib/python2.4/site-packages/setuptools/command/install.py", line 76, in run
    self.do_egg_install()
  File "/usr/lib/python2.4/site-packages/setuptools/command/install.py", line 96, in do_egg_install
    self.run_command('bdist_egg')
  File "/usr/lib/python2.4/distutils/cmd.py", line 333, in run_command
    self.distribution.run_command(command)
  File "/usr/lib/python2.4/distutils/dist.py", line 966, in run_command
    cmd_obj.run()
  File "/usr/lib/python2.4/site-packages/setuptools/command/bdist_egg.py", line 167, in run
    self.run_command("egg_info")
  File "/usr/lib/python2.4/distutils/cmd.py", line 333, in run_command
    self.distribution.run_command(command)
  File "/usr/lib/python2.4/distutils/dist.py", line 966, in run_command
    cmd_obj.run()
  File "/usr/lib/python2.4/site-packages/setuptools/command/egg_info.py", line 171, in run
    self.find_sources()
  File "/usr/lib/python2.4/site-packages/setuptools/command/egg_info.py", line 252, in find_sources
    mm.run()
  File "/usr/lib/python2.4/site-packages/setuptools/command/egg_info.py", line 306, in run
    self.add_defaults()
  File "/usr/lib/python2.4/site-packages/setuptools/command/egg_info.py", line 333, in add_defaults
    rcfiles = list(walk_revctrl())
  File "/usr/lib/python2.4/site-packages/setuptools/command/sdist.py", line 45, in walk_revctrl
    for item in ep.load()(dirname):
  File "/usr/lib/python2.4/site-packages/setuptools/command/sdist.py", line 52, in _default_revctrl
    for path in finder(dirname,path):
  File "/usr/lib/python2.4/site-packages/setuptools/command/sdist.py", line 98, in entries_finder
    log.warn("unrecognized .svn/entries format in %s", dirname)
NameError: global name 'log' is not defined
make[2]: *** [install-exec-local] Error 1
make[2]: Leaving directory `/home/paul/voicekey.bld/sphinxbase/python'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/paul/voicekey.bld/sphinxbase/python'
make: *** [install-recursive] Error 1

I can't get any further.  Ideas?

---

### Post by motin on 2008-12-13
You need the python development files:

```
sudo apt-get install python-all-dev
```

That at least made it compile. 

Install using:
```
sudo checkinstall  --fstrans=no
```

---

