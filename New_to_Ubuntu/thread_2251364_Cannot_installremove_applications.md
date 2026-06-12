---
title: "Cannot install/remove applications"
date: 2014-11-03
forum: New to Ubuntu
---

### Post by nu2u904 on 2014-11-03
I was using Software Center to install MatLab; install froze; sc said applying install. I couldn't find an option in SC to cancel and/or remove the install. Freeze blocks all subsequent installs. sudo apt-get remove started then said matlab was not installed so could not remove it. I tried to install aptitude, install blocked, could not unlock file. How do I remove matlab so I can proceed.

```

Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty/universe libgdf-dev i386 0.1.2-2build3
Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty/multiverse matlab-gdf all 0.1.2-2build3
Could not resolve 'us.archive.ubuntu.com'
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/suitesparse/libamd2.3.1_4.2.1-3ubuntu1_i386.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/suitesparse/libcamd2.3.1_4.2.1-3ubuntu1_i386.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/suitesparse/libccolamd2.8.0_4.2.1-3ubuntu1_i386.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/suitesparse/libcholmod2.1.2_4.2.1-3ubuntu1_i386.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/suitesparse/libumfpack5.6.2_4.2.1-3ubuntu1_i386.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/f/freemat/freemat-data_4.0-5build1_all.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/f/freemat/freemat_4.0-5build1_i386.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/f/freemat/freemat-help_4.0-5build1_all.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/g/genius/genius-common_1.0.16-0ubuntu1_i386.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/g/genius/genius_1.0.16-0ubuntu1_i386.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/libg/libgdf/libgdf0_0.1.2-2build3_i386.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/libg/libgdf/libgdf-dev_0.1.2-2build3_i386.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/multiverse/libg/libgdf/matlab-gdf_0.1.2-2build3_all.deb  Could not resolve 'us.archive.ubuntu.com'

E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
donald@donald-AOD255:~$ sudo apt-get install genius spyder science-numericalcomputations
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package science-numericalcomputations
donald@donald-AOD255:~$ sudo apt-get install genius spyder 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  kde-l10n-engb
Use 'apt-get autoremove' to remove it.
The following extra packages will be installed:
  docutils-common docutils-doc g++ g++-4.8 genius-common git git-core git-man
  ipython ipython-qtconsole libamd2.3.1 libapr1 libaprutil1 libcamd2.3.1
  libccolamd2.8.0 libcholmod2.1.2 liberror-perl libexpat1-dev libpgm-5.1-0
  libpython-dev libpython2.7-dev libserf-1-1 libstdc++-4.8-dev libsvn1
  libumfpack5.6.2 libzmq3 mercurial mercurial-common pep8 pyflakes pylint
  python-astroid python-decorator python-dev python-docutils
  python-egenix-mxdatetime python-egenix-mxtools python-jinja2
  python-logilab-common python-markupsafe python-matplotlib
  python-matplotlib-data python-psutil python-roman python-rope python-scipy
  python-setuptools python-simplegeneric python-sphinx python-spyderlib
  python-svn python-tk python-tz python-zmq python2.7-dev sphinx-common
  sphinx-doc
Suggested packages:
  g++-multilib g++-4.8-multilib gcc-4.8-doc libstdc++6-4.8-dbg git-daemon-run
  git-daemon-sysvinit git-doc git-el git-email git-gui gitk gitweb git-arch
  git-bzr git-cvs git-mediawiki git-svn ipython-doc ipython-notebook
  libstdc++-4.8-doc qct vim emacs kdiff3 kdiff3-qt kompare meld tkcvs mgdiff
  python-mysqldb texlive-lang-french fonts-linuxlibertine ttf-linux-libertine
  python-egenix-mxdatetime-dbg python-egenix-mxdatetime-doc
  python-egenix-mxtools-dbg python-egenix-mxtools-doc python-jinja2-doc pyro
  python-unittest2 dvipng inkscape python-excelerator python-matplotlib-doc
  python-nose python-tornado python-traits texlive-latex-extra ttf-staypuft
  jsmath texlive-fonts-recommended tortoisehg python-svn-dbg tix python-tk-dbg
The following NEW packages will be installed:
  docutils-common docutils-doc g++ g++-4.8 genius genius-common git git-core
  git-man ipython ipython-qtconsole libamd2.3.1 libapr1 libaprutil1
  libcamd2.3.1 libccolamd2.8.0 libcholmod2.1.2 liberror-perl libexpat1-dev
  libpgm-5.1-0 libpython-dev libpython2.7-dev libserf-1-1 libstdc++-4.8-dev
  libsvn1 libumfpack5.6.2 libzmq3 mercurial mercurial-common pep8 pyflakes
  pylint python-astroid python-decorator python-dev python-docutils
  python-egenix-mxdatetime python-egenix-mxtools python-jinja2
  python-logilab-common python-markupsafe python-matplotlib
  python-matplotlib-data python-psutil python-roman python-rope python-scipy
  python-setuptools python-simplegeneric python-sphinx python-spyderlib
  python-svn python-tk python-tz python-zmq python2.7-dev sphinx-common
  sphinx-doc spyder
0 upgraded, 59 newly installed, 0 to remove and 27 not upgraded.
Need to get 55.4 MB of archives.
After this operation, 182 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Err http://us.archive.ubuntu.com/ubuntu/ trusty/main libamd2.3.1 i386 1:4.2.1-3ubuntu1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty/main libapr1 i386 1.5.0-1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty/main libaprutil1 i386 1.5.3-1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty/main libcamd2.3.1 i386 1:4.2.1-3ubuntu1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty/main libccolamd2.8.0 i386 1:4.2.1-3ubuntu1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty/main libcholmod2.1.2 i386 1:4.2.1-3ubuntu1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty/universe libpgm-5.1-0 i386 5.1.118-1~dfsg-0.1ubuntu3
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty/main libexpat1-dev i386 2.1.0-4ubuntu1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty/main libpython2.7-dev i386 2.7.6-8
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libserf-1-1 i386 1.3.3-1ubuntu0.1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty/main libumfpack5.6.2 i386 1:4.2.1-3ubuntu1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty/universe libzmq3 i386 4.0.4+dfsg-2
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty/main docutils-common all 0.11-3
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty/main docutils-doc all 0.11-3
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty/main libstdc++-4.8-dev i386 4.8.2-19ubuntu1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty/main g++-4.8 i386 4.8.2-19ubuntu1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty/main g++ i386 4:4.8.2-1ubuntu6
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty/universe genius-common i386 1.0.16-0ubuntu1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty/universe genius i386 1.0.16-0ubuntu1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty/main liberror-perl all 0.17-1.1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty/main git-man all 1:1.9.1-1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty/main git i386 1:1.9.1-1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty/main git-core all 1:1.9.1-1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty/main python-decorator all 3.4.0-2build1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty/main python-simplegeneric all 0.8.1-1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty/universe ipython all 1.2.1-2
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty/universe python-zmq i386 14.0.1-1build2
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty/universe ipython-qtconsole all 1.2.1-2
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty/main libpython-dev i386 2.7.5-5ubuntu3
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty/universe mercurial-common all 2.8.2-1ubuntu1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty/universe mercurial i386 2.8.2-1ubuntu1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty/main python-setuptools all 3.3-1ubuntu1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty/main pep8 all 1.4.6-1.1build1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty/main pyflakes all 0.8.1-1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty/main python-logilab-common all 0.61.0-1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty/main python-astroid all 1.0.1-1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty/main pylint all 1.1.0-1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty/main python2.7-dev i386 2.7.6-8
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty/main python-dev i386 2.7.5-5ubuntu3
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty/main python-roman all 2.0.0-1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty/main python-docutils all 0.11-3
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty/main python-egenix-mxtools i386 3.2.7-1build1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty/main python-egenix-mxdatetime i386 3.2.7-1build1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty/main python-markupsafe i386 0.18-1build2
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty/main python-jinja2 all 2.7.2-2
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty/universe python-matplotlib-data all 1.3.1-1ubuntu5
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty/main python-tz all 2012c-1build1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty/universe python-matplotlib i386 1.3.1-1ubuntu5
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty/main python-psutil i386 1.2.1-1ubuntu2
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty/universe python-rope all 0.9.2-2ubuntu1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main sphinx-common all 1.2.2+dfsg-1ubuntu1.1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main python-sphinx all 1.2.2+dfsg-1ubuntu1.1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty/main python-svn i386 1.7.8-0.2
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty/main python-tk i386 2.7.5-1ubuntu1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main sphinx-doc all 1.2.2+dfsg-1ubuntu1.1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty/universe python-scipy i386 0.13.3-1build1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty/universe python-spyderlib all 2.2.5+dfsg-1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty/universe spyder all 2.2.5+dfsg-1
  Could not resolve 'us.archive.ubuntu.com'
Err http://security.ubuntu.com/ubuntu/ trusty-security/main libserf-1-1 i386 1.3.3-1ubuntu0.1
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com/ubuntu/ trusty-security/main libsvn1 i386 1.8.8-1ubuntu3.1
  Could not resolve 'security.ubuntu.com'
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/suitesparse/libamd2.3.1_4.2.1-3ubuntu1_i386.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/a/apr/libapr1_1.5.0-1_i386.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/a/apr-util/libaprutil1_1.5.3-1_i386.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/suitesparse/libcamd2.3.1_4.2.1-3ubuntu1_i386.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/suitesparse/libccolamd2.8.0_4.2.1-3ubuntu1_i386.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/suitesparse/libcholmod2.1.2_4.2.1-3ubuntu1_i386.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/libp/libpgm/libpgm-5.1-0_5.1.118-1~dfsg-0.1ubuntu3_i386.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/e/expat/libexpat1-dev_2.1.0-4ubuntu1_i386.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/python2.7/libpython2.7-dev_2.7.6-8_i386.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/s/serf/libserf-1-1_1.3.3-1ubuntu0.1_i386.deb  Could not resolve 'security.ubuntu.com'

E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/s/subversion/libsvn1_1.8.8-1ubuntu3.1_i386.deb  Could not resolve 'security.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/suitesparse/libumfpack5.6.2_4.2.1-3ubuntu1_i386.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/z/zeromq3/libzmq3_4.0.4+dfsg-2_i386.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/python-docutils/docutils-common_0.11-3_all.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/python-docutils/docutils-doc_0.11-3_all.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.8/libstdc++-4.8-dev_4.8.2-19ubuntu1_i386.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.8/g++-4.8_4.8.2-19ubuntu1_i386.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-defaults/g++_4.8.2-1ubuntu6_i386.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/g/genius/genius-common_1.0.16-0ubuntu1_i386.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/g/genius/genius_1.0.16-0ubuntu1_i386.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libe/liberror-perl/liberror-perl_0.17-1.1_all.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/git/git-man_1.9.1-1_all.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/git/git_1.9.1-1_i386.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/git/git-core_1.9.1-1_all.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/python-decorator/python-decorator_3.4.0-2build1_all.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/simplegeneric/python-simplegeneric_0.8.1-1_all.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/i/ipython/ipython_1.2.1-2_all.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/p/pyzmq/python-zmq_14.0.1-1build2_i386.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/i/ipython/ipython-qtconsole_1.2.1-2_all.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/python-defaults/libpython-dev_2.7.5-5ubuntu3_i386.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/m/mercurial/mercurial-common_2.8.2-1ubuntu1_all.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/m/mercurial/mercurial_2.8.2-1ubuntu1_i386.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/python-setuptools/python-setuptools_3.3-1ubuntu1_all.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/pep8/pep8_1.4.6-1.1build1_all.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/pyflakes/pyflakes_0.8.1-1_all.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/l/logilab-common/python-logilab-common_0.61.0-1_all.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/a/astroid/python-astroid_1.0.1-1_all.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/pylint/pylint_1.1.0-1_all.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/python2.7/python2.7-dev_2.7.6-8_i386.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/python-defaults/python-dev_2.7.5-5ubuntu3_i386.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/python-roman/python-roman_2.0.0-1_all.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/python-docutils/python-docutils_0.11-3_all.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/e/egenix-mx-base/python-egenix-mxtools_3.2.7-1build1_i386.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/e/egenix-mx-base/python-egenix-mxdatetime_3.2.7-1build1_i386.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/m/markupsafe/python-markupsafe_0.18-1build2_i386.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/j/jinja2/python-jinja2_2.7.2-2_all.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/m/matplotlib/python-matplotlib-data_1.3.1-1ubuntu5_all.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/python-tz/python-tz_2012c-1build1_all.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/m/matplotlib/python-matplotlib_1.3.1-1ubuntu5_i386.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/python-psutil/python-psutil_1.2.1-1ubuntu2_i386.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/r/rope/python-rope_0.9.2-2ubuntu1_all.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/sphinx/sphinx-common_1.2.2+dfsg-1ubuntu1.1_all.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/sphinx/python-sphinx_1.2.2+dfsg-1ubuntu1.1_all.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/pysvn/python-svn_1.7.8-0.2_i386.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/python-stdlib-extensions/python-tk_2.7.5-1ubuntu1_i386.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/sphinx/sphinx-doc_1.2.2+dfsg-1ubuntu1.1_all.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/p/python-scipy/python-scipy_0.13.3-1build1_i386.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/s/spyder/python-spyderlib_2.2.5+dfsg-1_all.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/s/spyder/spyder_2.2.5+dfsg-1_all.deb  Could not resolve 'us.archive.ubuntu.com'

E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
donald@donald-AOD255:~$ sudo apt-get update
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
donald@donald-AOD255:~$ sudo apt-get updateE: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
donald@donald-AOD255:~$ sudo apt-get install genius  
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  kde-l10n-engb
Use 'apt-get autoremove' to remove it.
The following extra packages will be installed:
  genius-common
The following NEW packages will be installed:
  genius genius-common
0 upgraded, 2 newly installed, 0 to remove and 27 not upgraded.
Need to get 756 kB of archives.
After this operation, 4,474 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Err http://us.archive.ubuntu.com/ubuntu/ trusty/universe genius-common i386 1.0.16-0ubuntu1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty/universe genius i386 1.0.16-0ubuntu1
  Could not resolve 'us.archive.ubuntu.com'
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/g/genius/genius-common_1.0.16-0ubuntu1_i386.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/g/genius/genius_1.0.16-0ubuntu1_i386.deb  Could not resolve 'us.archive.ubuntu.com'

E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
donald@donald-AOD255:~$ locate matlab
/usr/share/app-install/desktop/matlab-support:matlab.desktop
/usr/share/app-install/icons/_usr_share_icons_hicolor_48x48_apps_matlab.png
/usr/share/geany/filetypes.matlab
/usr/share/gtksourceview-3.0/language-specs/matlab.lang
/usr/share/kde4/apps/katepart/syntax/matlab.xml
/usr/share/mime/text/x-matlab.xml
/var/cache/apt/archives/matlab-support_0.0.19_all.deb
donald@donald-AOD255:~$ sudo apt-get update
[sudo] password for donald: 
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
donald@donald-AOD255:~$ ^C
donald@donald-AOD255:~$ 


```

---

### Post by sandyd on 2014-11-03
Ive adjusted your post above to be a more readable and updated your post title

> Could not resolve 'us.archive.ubuntu.com'

This looks like a DNS lookup error, can you post the output of
```

ifconfig
ping -c10 8.8.8.8


```

Side Note:
If the ifconfig output contains an IP Address that doesn't start with the following, please remove before posting
- 192.168.
- 10.
- 172.16. - 172.31.

---

### Post by nu2u904 on 2014-11-03
```

Thank you sandye; here's the code.

donald@donald-AOD255:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 88:ae:1d:9d:b1:95  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::8aae:1dff:fe9d:b195/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1334828 errors:0 dropped:0 overruns:0 frame:0
          TX packets:392871 errors:0 dropped:0 overruns:0 carrier:8
          collisions:0 txqueuelen:1000 
          RX bytes:1892604770 (1.8 GB)  TX bytes:32886351 (32.8 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:43817 errors:0 dropped:0 overruns:0 frame:0
          TX packets:43817 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3796066 (3.7 MB)  TX bytes:3796066 (3.7 MB)

wlan0     Link encap:Ethernet  HWaddr 00:26:c7:8e:f1:72  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



donald-AOD255:~$ ping -c10 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=250 time=22.7 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=250 time=22.9 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=250 time=22.5 ms
64 bytes from 8.8.8.8: icmp_seq=4 ttl=250 time=23.5 ms
64 bytes from 8.8.8.8: icmp_seq=5 ttl=250 time=22.2 ms
64 bytes from 8.8.8.8: icmp_seq=7 ttl=250 time=22.3 ms
64 bytes from 8.8.8.8: icmp_seq=8 ttl=250 time=21.3 ms
64 bytes from 8.8.8.8: icmp_seq=9 ttl=250 time=22.3 ms
64 bytes from 8.8.8.8: icmp_seq=10 ttl=250 time=21.4 ms

--- 8.8.8.8 ping statistics ---
10 packets transmitted, 9 received, 10% packet loss, time 9016ms
rtt min/avg/max/mdev = 21.394/22.398/23.578/0.655 ms


```

---

### Post by sandyd on 2014-11-04
Yeah, definitely a DNS issue, your internet is working fine.

Can you run
```

sudo nano /etc/NetworkManager/NetworkManager.conf

```
Place a pound sign '#' in front of the line that says
```
dns=dnsmasq
```
so that it looks like
```
#dns=dnsmasq
```

Press control+x to exit (press y to save)

Run
```
sudo restart network-manager
```

If that still doesn't work, post the output of
```

cat /etc/resolv.conf
```

Side Note, if you absolutely have to have the computer working (and probably your internet back too), run

```

sudo nano /etc/resolv.conf"
```

Paste in
```

nameserver 8.8.8.8
nameserver 8.8.4.4

```
and save the file.

However that is _not_ the way to fix it, that is honestly a workaround as it is lost on reboot.

---

### Post by nu2u904 on 2014-11-05
Thank you sandyd. After I sent my previous reply the computer ran at a long crawl. I thought it might be bcause I had been suspending and never rebooting. So I shutdown and rebooted to no avail; nor would usb live boot and this after I wrote solved to my thread boot repair. What do I do now? I would like to try your fix.

---

