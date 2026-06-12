---
title: "/usr/bin/ld: cannot find -lz"
date: 2016-08-15
forum: Packaging and Compiling Programs
---

### Post by alexey-7 on 2016-08-15
Ubuntu 16.04.1 LTS
I'm trying to install lxml v3.4.4, which I need for running w3af.
By the way, I had lxml-3.5.0 installed, but w3af didn't accept it somehow and needed v3.4.4 exactly.
So, I used the command
```
sudo pip install lxml==3.4.4
```
with the following output:
```
sudo -H pip install lxml==3.4.4Collecting lxml==3.4.4
  Downloading lxml-3.4.4.tar.gz (3.5MB)
    100% |&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;| 3.5MB 175kB/s 
Building wheels for collected packages: lxml
  Running setup.py bdist_wheel for lxml ... error
  Complete output from command /usr/bin/python -u -c "import setuptools, tokenize;__file__='/tmp/pip-build-6c2Jyo/lxml/setup.py';exec(compile(getattr(tokenize, 'open', open)(__file__).read().replace('\r\n', '\n'), __file__, 'exec'))" bdist_wheel -d /tmp/tmpl7fuhipip-wheel- --python-tag cp27:
  Building lxml version 3.4.4.
  Building without Cython.
  Using build configuration of libxslt 1.1.28
  /usr/lib/python2.7/distutils/dist.py:267: UserWarning: Unknown distribution option: 'bugtrack_url'
    warnings.warn(msg)
  running bdist_wheel
  running build
  running build_py
  creating build
  creating build/lib.linux-x86_64-2.7
  creating build/lib.linux-x86_64-2.7/lxml
  copying src/lxml/builder.py -> build/lib.linux-x86_64-2.7/lxml
  copying src/lxml/pyclasslookup.py -> build/lib.linux-x86_64-2.7/lxml
  copying src/lxml/usedoctest.py -> build/lib.linux-x86_64-2.7/lxml
  copying src/lxml/_elementpath.py -> build/lib.linux-x86_64-2.7/lxml
  copying src/lxml/__init__.py -> build/lib.linux-x86_64-2.7/lxml
  copying src/lxml/doctestcompare.py -> build/lib.linux-x86_64-2.7/lxml
  copying src/lxml/ElementInclude.py -> build/lib.linux-x86_64-2.7/lxml
  copying src/lxml/cssselect.py -> build/lib.linux-x86_64-2.7/lxml
  copying src/lxml/sax.py -> build/lib.linux-x86_64-2.7/lxml
  creating build/lib.linux-x86_64-2.7/lxml/includes
  copying src/lxml/includes/__init__.py -> build/lib.linux-x86_64-2.7/lxml/includes
  creating build/lib.linux-x86_64-2.7/lxml/html
  copying src/lxml/html/ElementSoup.py -> build/lib.linux-x86_64-2.7/lxml/html
  copying src/lxml/html/builder.py -> build/lib.linux-x86_64-2.7/lxml/html
  copying src/lxml/html/usedoctest.py -> build/lib.linux-x86_64-2.7/lxml/html
  copying src/lxml/html/formfill.py -> build/lib.linux-x86_64-2.7/lxml/html
  copying src/lxml/html/__init__.py -> build/lib.linux-x86_64-2.7/lxml/html
  copying src/lxml/html/_html5builder.py -> build/lib.linux-x86_64-2.7/lxml/html
  copying src/lxml/html/_diffcommand.py -> build/lib.linux-x86_64-2.7/lxml/html
  copying src/lxml/html/soupparser.py -> build/lib.linux-x86_64-2.7/lxml/html
  copying src/lxml/html/html5parser.py -> build/lib.linux-x86_64-2.7/lxml/html
  copying src/lxml/html/clean.py -> build/lib.linux-x86_64-2.7/lxml/html
  copying src/lxml/html/defs.py -> build/lib.linux-x86_64-2.7/lxml/html
  copying src/lxml/html/diff.py -> build/lib.linux-x86_64-2.7/lxml/html
  copying src/lxml/html/_setmixin.py -> build/lib.linux-x86_64-2.7/lxml/html
  creating build/lib.linux-x86_64-2.7/lxml/isoschematron
  copying src/lxml/isoschematron/__init__.py -> build/lib.linux-x86_64-2.7/lxml/isoschematron
  copying src/lxml/lxml.etree.h -> build/lib.linux-x86_64-2.7/lxml
  copying src/lxml/lxml.etree_api.h -> build/lib.linux-x86_64-2.7/lxml
  copying src/lxml/includes/htmlparser.pxd -> build/lib.linux-x86_64-2.7/lxml/includes
  copying src/lxml/includes/xinclude.pxd -> build/lib.linux-x86_64-2.7/lxml/includes
  copying src/lxml/includes/schematron.pxd -> build/lib.linux-x86_64-2.7/lxml/includes
  copying src/lxml/includes/relaxng.pxd -> build/lib.linux-x86_64-2.7/lxml/includes
  copying src/lxml/includes/xmlparser.pxd -> build/lib.linux-x86_64-2.7/lxml/includes
  copying src/lxml/includes/dtdvalid.pxd -> build/lib.linux-x86_64-2.7/lxml/includes
  copying src/lxml/includes/uri.pxd -> build/lib.linux-x86_64-2.7/lxml/includes
  copying src/lxml/includes/xmlerror.pxd -> build/lib.linux-x86_64-2.7/lxml/includes
  copying src/lxml/includes/config.pxd -> build/lib.linux-x86_64-2.7/lxml/includes
  copying src/lxml/includes/c14n.pxd -> build/lib.linux-x86_64-2.7/lxml/includes
  copying src/lxml/includes/tree.pxd -> build/lib.linux-x86_64-2.7/lxml/includes
  copying src/lxml/includes/etreepublic.pxd -> build/lib.linux-x86_64-2.7/lxml/includes
  copying src/lxml/includes/xslt.pxd -> build/lib.linux-x86_64-2.7/lxml/includes
  copying src/lxml/includes/xpath.pxd -> build/lib.linux-x86_64-2.7/lxml/includes
  copying src/lxml/includes/xmlschema.pxd -> build/lib.linux-x86_64-2.7/lxml/includes
  copying src/lxml/includes/lxml-version.h -> build/lib.linux-x86_64-2.7/lxml/includes
  copying src/lxml/includes/etree_defs.h -> build/lib.linux-x86_64-2.7/lxml/includes
  creating build/lib.linux-x86_64-2.7/lxml/isoschematron/resources
  creating build/lib.linux-x86_64-2.7/lxml/isoschematron/resources/rng
  copying src/lxml/isoschematron/resources/rng/iso-schematron.rng -> build/lib.linux-x86_64-2.7/lxml/isoschematron/resources/rng
  creating build/lib.linux-x86_64-2.7/lxml/isoschematron/resources/xsl
  copying src/lxml/isoschematron/resources/xsl/RNG2Schtrn.xsl -> build/lib.linux-x86_64-2.7/lxml/isoschematron/resources/xsl
  copying src/lxml/isoschematron/resources/xsl/XSD2Schtrn.xsl -> build/lib.linux-x86_64-2.7/lxml/isoschematron/resources/xsl
  creating build/lib.linux-x86_64-2.7/lxml/isoschematron/resources/xsl/iso-schematron-xslt1
  copying src/lxml/isoschematron/resources/xsl/iso-schematron-xslt1/iso_schematron_skeleton_for_xslt1.xsl -> build/lib.linux-x86_64-2.7/lxml/isoschematron/resources/xsl/iso-schematron-xslt1
  copying src/lxml/isoschematron/resources/xsl/iso-schematron-xslt1/iso_schematron_message.xsl -> build/lib.linux-x86_64-2.7/lxml/isoschematron/resources/xsl/iso-schematron-xslt1
  copying src/lxml/isoschematron/resources/xsl/iso-schematron-xslt1/iso_svrl_for_xslt1.xsl -> build/lib.linux-x86_64-2.7/lxml/isoschematron/resources/xsl/iso-schematron-xslt1
  copying src/lxml/isoschematron/resources/xsl/iso-schematron-xslt1/iso_dsdl_include.xsl -> build/lib.linux-x86_64-2.7/lxml/isoschematron/resources/xsl/iso-schematron-xslt1
  copying src/lxml/isoschematron/resources/xsl/iso-schematron-xslt1/iso_abstract_expand.xsl -> build/lib.linux-x86_64-2.7/lxml/isoschematron/resources/xsl/iso-schematron-xslt1
  copying src/lxml/isoschematron/resources/xsl/iso-schematron-xslt1/readme.txt -> build/lib.linux-x86_64-2.7/lxml/isoschematron/resources/xsl/iso-schematron-xslt1
  running build_ext
  building 'lxml.etree' extension
  creating build/temp.linux-x86_64-2.7
  creating build/temp.linux-x86_64-2.7/src
  creating build/temp.linux-x86_64-2.7/src/lxml
  x86_64-linux-gnu-gcc -pthread -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -fno-strict-aliasing -Wdate-time -D_FORTIFY_SOURCE=2 -g -fstack-protector-strong -Wformat -Werror=format-security -fPIC -I/usr/include/libxml2 -I/tmp/pip-build-6c2Jyo/lxml/src/lxml/includes -I/usr/include/python2.7 -c src/lxml/lxml.etree.c -o build/temp.linux-x86_64-2.7/src/lxml/lxml.etree.o -w
  x86_64-linux-gnu-gcc -pthread -shared -Wl,-O1 -Wl,-Bsymbolic-functions -Wl,-Bsymbolic-functions -Wl,-z,relro -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -Wdate-time -D_FORTIFY_SOURCE=2 -g -fstack-protector-strong -Wformat -Werror=format-security -Wl,-Bsymbolic-functions -Wl,-z,relro -Wdate-time -D_FORTIFY_SOURCE=2 -g -fstack-protector-strong -Wformat -Werror=format-security build/temp.linux-x86_64-2.7/src/lxml/lxml.etree.o -lxslt -lexslt -lxml2 -lz -lm -o build/lib.linux-x86_64-2.7/lxml/etree.so
  /usr/bin/ld: cannot find -lz
  collect2: error: ld returned 1 exit status
  error: command 'x86_64-linux-gnu-gcc' failed with exit status 1
  
  ----------------------------------------
  Failed building wheel for lxml
  Running setup.py clean for lxml
Failed to build lxml
Installing collected packages: lxml
  Found existing installation: lxml 3.5.0
    Uninstalling lxml-3.5.0:
      Successfully uninstalled lxml-3.5.0
  Running setup.py install for lxml ... error
    Complete output from command /usr/bin/python -u -c "import setuptools, tokenize;__file__='/tmp/pip-build-6c2Jyo/lxml/setup.py';exec(compile(getattr(tokenize, 'open', open)(__file__).read().replace('\r\n', '\n'), __file__, 'exec'))" install --record /tmp/pip-fupdoY-record/install-record.txt --single-version-externally-managed --compile:
    Building lxml version 3.4.4.
    Building without Cython.
    Using build configuration of libxslt 1.1.28
    /usr/lib/python2.7/distutils/dist.py:267: UserWarning: Unknown distribution option: 'bugtrack_url'
      warnings.warn(msg)
    running install
    running build
    running build_py
    creating build
    creating build/lib.linux-x86_64-2.7
    creating build/lib.linux-x86_64-2.7/lxml
    copying src/lxml/builder.py -> build/lib.linux-x86_64-2.7/lxml
    copying src/lxml/pyclasslookup.py -> build/lib.linux-x86_64-2.7/lxml
    copying src/lxml/usedoctest.py -> build/lib.linux-x86_64-2.7/lxml
    copying src/lxml/_elementpath.py -> build/lib.linux-x86_64-2.7/lxml
    copying src/lxml/__init__.py -> build/lib.linux-x86_64-2.7/lxml
    copying src/lxml/doctestcompare.py -> build/lib.linux-x86_64-2.7/lxml
    copying src/lxml/ElementInclude.py -> build/lib.linux-x86_64-2.7/lxml
    copying src/lxml/cssselect.py -> build/lib.linux-x86_64-2.7/lxml
    copying src/lxml/sax.py -> build/lib.linux-x86_64-2.7/lxml
    creating build/lib.linux-x86_64-2.7/lxml/includes
    copying src/lxml/includes/__init__.py -> build/lib.linux-x86_64-2.7/lxml/includes
    creating build/lib.linux-x86_64-2.7/lxml/html
    copying src/lxml/html/ElementSoup.py -> build/lib.linux-x86_64-2.7/lxml/html
    copying src/lxml/html/builder.py -> build/lib.linux-x86_64-2.7/lxml/html
    copying src/lxml/html/usedoctest.py -> build/lib.linux-x86_64-2.7/lxml/html
    copying src/lxml/html/formfill.py -> build/lib.linux-x86_64-2.7/lxml/html
    copying src/lxml/html/__init__.py -> build/lib.linux-x86_64-2.7/lxml/html
    copying src/lxml/html/_html5builder.py -> build/lib.linux-x86_64-2.7/lxml/html
    copying src/lxml/html/_diffcommand.py -> build/lib.linux-x86_64-2.7/lxml/html
    copying src/lxml/html/soupparser.py -> build/lib.linux-x86_64-2.7/lxml/html
    copying src/lxml/html/html5parser.py -> build/lib.linux-x86_64-2.7/lxml/html
    copying src/lxml/html/clean.py -> build/lib.linux-x86_64-2.7/lxml/html
    copying src/lxml/html/defs.py -> build/lib.linux-x86_64-2.7/lxml/html
    copying src/lxml/html/diff.py -> build/lib.linux-x86_64-2.7/lxml/html
    copying src/lxml/html/_setmixin.py -> build/lib.linux-x86_64-2.7/lxml/html
    creating build/lib.linux-x86_64-2.7/lxml/isoschematron
    copying src/lxml/isoschematron/__init__.py -> build/lib.linux-x86_64-2.7/lxml/isoschematron
    copying src/lxml/lxml.etree.h -> build/lib.linux-x86_64-2.7/lxml
    copying src/lxml/lxml.etree_api.h -> build/lib.linux-x86_64-2.7/lxml
    copying src/lxml/includes/htmlparser.pxd -> build/lib.linux-x86_64-2.7/lxml/includes
    copying src/lxml/includes/xinclude.pxd -> build/lib.linux-x86_64-2.7/lxml/includes
    copying src/lxml/includes/schematron.pxd -> build/lib.linux-x86_64-2.7/lxml/includes
    copying src/lxml/includes/relaxng.pxd -> build/lib.linux-x86_64-2.7/lxml/includes
    copying src/lxml/includes/xmlparser.pxd -> build/lib.linux-x86_64-2.7/lxml/includes
    copying src/lxml/includes/dtdvalid.pxd -> build/lib.linux-x86_64-2.7/lxml/includes
    copying src/lxml/includes/uri.pxd -> build/lib.linux-x86_64-2.7/lxml/includes
    copying src/lxml/includes/xmlerror.pxd -> build/lib.linux-x86_64-2.7/lxml/includes
    copying src/lxml/includes/config.pxd -> build/lib.linux-x86_64-2.7/lxml/includes
    copying src/lxml/includes/c14n.pxd -> build/lib.linux-x86_64-2.7/lxml/includes
    copying src/lxml/includes/tree.pxd -> build/lib.linux-x86_64-2.7/lxml/includes
    copying src/lxml/includes/etreepublic.pxd -> build/lib.linux-x86_64-2.7/lxml/includes
    copying src/lxml/includes/xslt.pxd -> build/lib.linux-x86_64-2.7/lxml/includes
    copying src/lxml/includes/xpath.pxd -> build/lib.linux-x86_64-2.7/lxml/includes
    copying src/lxml/includes/xmlschema.pxd -> build/lib.linux-x86_64-2.7/lxml/includes
    copying src/lxml/includes/lxml-version.h -> build/lib.linux-x86_64-2.7/lxml/includes
    copying src/lxml/includes/etree_defs.h -> build/lib.linux-x86_64-2.7/lxml/includes
    creating build/lib.linux-x86_64-2.7/lxml/isoschematron/resources
    creating build/lib.linux-x86_64-2.7/lxml/isoschematron/resources/rng
    copying src/lxml/isoschematron/resources/rng/iso-schematron.rng -> build/lib.linux-x86_64-2.7/lxml/isoschematron/resources/rng
    creating build/lib.linux-x86_64-2.7/lxml/isoschematron/resources/xsl
    copying src/lxml/isoschematron/resources/xsl/RNG2Schtrn.xsl -> build/lib.linux-x86_64-2.7/lxml/isoschematron/resources/xsl
    copying src/lxml/isoschematron/resources/xsl/XSD2Schtrn.xsl -> build/lib.linux-x86_64-2.7/lxml/isoschematron/resources/xsl
    creating build/lib.linux-x86_64-2.7/lxml/isoschematron/resources/xsl/iso-schematron-xslt1
    copying src/lxml/isoschematron/resources/xsl/iso-schematron-xslt1/iso_schematron_skeleton_for_xslt1.xsl -> build/lib.linux-x86_64-2.7/lxml/isoschematron/resources/xsl/iso-schematron-xslt1
    copying src/lxml/isoschematron/resources/xsl/iso-schematron-xslt1/iso_schematron_message.xsl -> build/lib.linux-x86_64-2.7/lxml/isoschematron/resources/xsl/iso-schematron-xslt1
    copying src/lxml/isoschematron/resources/xsl/iso-schematron-xslt1/iso_svrl_for_xslt1.xsl -> build/lib.linux-x86_64-2.7/lxml/isoschematron/resources/xsl/iso-schematron-xslt1
    copying src/lxml/isoschematron/resources/xsl/iso-schematron-xslt1/iso_dsdl_include.xsl -> build/lib.linux-x86_64-2.7/lxml/isoschematron/resources/xsl/iso-schematron-xslt1
    copying src/lxml/isoschematron/resources/xsl/iso-schematron-xslt1/iso_abstract_expand.xsl -> build/lib.linux-x86_64-2.7/lxml/isoschematron/resources/xsl/iso-schematron-xslt1
    copying src/lxml/isoschematron/resources/xsl/iso-schematron-xslt1/readme.txt -> build/lib.linux-x86_64-2.7/lxml/isoschematron/resources/xsl/iso-schematron-xslt1
    running build_ext
    building 'lxml.etree' extension
    creating build/temp.linux-x86_64-2.7
    creating build/temp.linux-x86_64-2.7/src
    creating build/temp.linux-x86_64-2.7/src/lxml
    x86_64-linux-gnu-gcc -pthread -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -fno-strict-aliasing -Wdate-time -D_FORTIFY_SOURCE=2 -g -fstack-protector-strong -Wformat -Werror=format-security -fPIC -I/usr/include/libxml2 -I/tmp/pip-build-6c2Jyo/lxml/src/lxml/includes -I/usr/include/python2.7 -c src/lxml/lxml.etree.c -o build/temp.linux-x86_64-2.7/src/lxml/lxml.etree.o -w
    x86_64-linux-gnu-gcc -pthread -shared -Wl,-O1 -Wl,-Bsymbolic-functions -Wl,-Bsymbolic-functions -Wl,-z,relro -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -Wdate-time -D_FORTIFY_SOURCE=2 -g -fstack-protector-strong -Wformat -Werror=format-security -Wl,-Bsymbolic-functions -Wl,-z,relro -Wdate-time -D_FORTIFY_SOURCE=2 -g -fstack-protector-strong -Wformat -Werror=format-security build/temp.linux-x86_64-2.7/src/lxml/lxml.etree.o -lxslt -lexslt -lxml2 -lz -lm -o build/lib.linux-x86_64-2.7/lxml/etree.so
    /usr/bin/ld: cannot find -lz
    collect2: error: ld returned 1 exit status
    error: command 'x86_64-linux-gnu-gcc' failed with exit status 1
    
    ----------------------------------------
  Rolling back uninstall of lxml
Command "/usr/bin/python -u -c "import setuptools, tokenize;__file__='/tmp/pip-build-6c2Jyo/lxml/setup.py';exec(compile(getattr(tokenize, 'open', open)(__file__).read().replace('\r\n', '\n'), __file__, 'exec'))" install --record /tmp/pip-fupdoY-record/install-record.txt --single-version-externally-managed --compile" failed with error code 1 in /tmp/pip-build-6c2Jyo/lxml/



```

What could be that "-lz", which package it may be in?

---

### Post by steeldriver on 2016-08-15
Hello and welcome to the forums

It is in package **zlib1g-dev** iirc

---

### Post by alexey-7 on 2016-08-15
Thank you very much, it helped!

---

