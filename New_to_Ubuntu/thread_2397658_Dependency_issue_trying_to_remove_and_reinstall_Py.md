---
title: "Dependency issue trying to remove and reinstall Python2.7.6 in Ubuntu 14.04"
date: 2018-08-01
forum: New to Ubuntu
---

### Post by johan855 on 2018-08-01
It all started with a security warning that I should update python from 2.7.6 to 2.7.9.
After running the following script:

[https://gist.github.com/Jimmy-Xu/f90b4bf466f53f116283](https://gist.github.com/Jimmy-Xu/f90b4bf466f53f116283)

I got an error saying it could not go ahead to to the existence of some folders, so 
I removed */usr/lib/python2.7* and */usr/local/lib/python2.7 *and re run the script.

After setting PYTHONHOME and PYTHONPATH to the correct values, I realized I wasn't able to import any libraries, so I Tried to remove my old installation of python and reinstall it again using:

```
sudo apt-get install --reinstall python2.7
```

but was faced with the following error:

```

js@dwh-01:~$ sudo apt-get install python2.7Reading package lists... Done
Building dependency tree
Reading state information... Done
python2.7 is already the newest version.
python2.7 set to manually installed.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 apport : Depends: python3-apport (>= 2.14.1-0ubuntu3.29) but it is not going to be installed
          Depends: python3-gi but it is not going to be installed
 python3 : Depends: dh-python but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).



```

I tried running ```
apt-get -f install
``` but I see there are still error dependencies showing up:

```

js@dwh-01:~$ sudo apt-get -f installReading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  aglfn chktex clisp cm-super cm-super-minimal context context-modules dvidvi
  dvipng fonts-cabin fonts-comfortaa fonts-font-awesome fonts-freefont-otf
  fonts-gfs-artemisia fonts-gfs-baskerville fonts-gfs-bodoni-classic
  fonts-gfs-complutum fonts-gfs-didot fonts-gfs-didot-classic fonts-gfs-gazis
  fonts-gfs-neohellenic fonts-gfs-olga fonts-gfs-porson fonts-gfs-solomos
  fonts-gfs-theokritos fonts-hosny-amiri fonts-inconsolata fonts-junicode
  fonts-lato fonts-liberation fonts-linuxlibertine fonts-lobster
  fonts-lobstertwo fonts-oflb-asana-math fonts-sil-gentium
  fonts-sil-gentium-basic fonts-stix imagemagick-common indicator-application
  ko.tex-extra-hlfont lacheck latex-cjk-all latex-cjk-chinese
  latex-cjk-chinese-arphic-bkai00mp latex-cjk-chinese-arphic-bsmi00lp
  latex-cjk-chinese-arphic-gbsn00lp latex-cjk-chinese-arphic-gkai00mp
  latex-cjk-common latex-cjk-japanese latex-cjk-japanese-wadalab
  latex-cjk-korean latex-cjk-thai latex-sanskrit latexdiff lcdf-typetools
  libappindicator3-1 libdbusmenu-glib4 libdbusmenu-gtk3-4 libffcall1
  libfftw3-double3 libfile-which-perl libindicator3-7 libintl-perl liblqr-1-0
  libmagick++5 libmagickcore5 libmagickwand5 libplot2c2 libpstoedit0c2a
  libpython-dev libsigsegv2 libtext-unidecode-perl libxml-libxml-perl
  libxml-namespacesupport-perl libxml-parser-perl libxml-sax-base-perl
  libxml-sax-expat-perl libxml-sax-perl m-tx musixtex pfb2t1c2pfb pmx
  preview-latex-style pstoedit purifyeps python-colorama-whl
  python-distlib-whl python-html5lib-whl python-requests-whl
  python-setuptools-whl python-six-whl python-urllib3-whl swath tex4ht
  tex4ht-common texinfo texlive-bibtex-extra texlive-fonts-extra
  texlive-fonts-extra-doc texlive-formats-extra texlive-games
  texlive-generic-extra texlive-humanities texlive-humanities-doc
  texlive-lang-african texlive-lang-arabic texlive-lang-cjk
  texlive-lang-cyrillic texlive-lang-czechslovak texlive-lang-english
  texlive-lang-european texlive-lang-french texlive-lang-german
  texlive-lang-greek texlive-lang-italian texlive-lang-other
  texlive-lang-polish texlive-lang-portuguese texlive-lang-spanish
  texlive-latex-extra texlive-latex-extra-doc texlive-math-extra
  texlive-metapost texlive-metapost-doc texlive-omega texlive-pictures
  texlive-pictures-doc texlive-plain-extra texlive-publishers
  texlive-publishers-doc texlive-science texlive-science-doc texlive-xetex
  ttf-adf-accanthis ttf-adf-gillius unzip xindy xindy-rules zip
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  dh-python lsb-release python3-apport python3-apt python3-gi
  python3-problem-report
Suggested packages:
  lsb python3-launchpadlib python3-apt-dbg python-apt-doc
Recommended packages:
  apport
The following NEW packages will be installed:
  dh-python lsb-release python3-apport python3-apt python3-gi
  python3-problem-report
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0 B/625 kB of archives.
After this operation, 2,512 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Selecting previously unselected package dh-python.
(Reading database ... 216575 files and directories currently installed.)
Preparing to unpack .../dh-python_1.20140128-1ubuntu8.2_all.deb ...
Unpacking dh-python (1.20140128-1ubuntu8.2) ...
Selecting previously unselected package python3-apt.
Preparing to unpack .../python3-apt_0.9.3.5ubuntu3_amd64.deb ...
Unpacking python3-apt (0.9.3.5ubuntu3) ...
Selecting previously unselected package python3-problem-report.
Preparing to unpack .../python3-problem-report_2.14.1-0ubuntu3.29_all.deb ...
Unpacking python3-problem-report (2.14.1-0ubuntu3.29) ...
Selecting previously unselected package lsb-release.
Preparing to unpack .../lsb-release_4.1+Debian11ubuntu6.2_all.deb ...
Unpacking lsb-release (4.1+Debian11ubuntu6.2) ...
Selecting previously unselected package python3-apport.
Preparing to unpack .../python3-apport_2.14.1-0ubuntu3.29_all.deb ...
Unpacking python3-apport (2.14.1-0ubuntu3.29) ...
Selecting previously unselected package python3-gi.
Preparing to unpack .../python3-gi_3.12.0-1ubuntu1_amd64.deb ...
Unpacking python3-gi (3.12.0-1ubuntu1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Setting up python-minimal (2.7.5-5ubuntu3) ...
Could not find platform independent libraries <prefix>
Could not find platform dependent libraries <exec_prefix>
Consider setting $PYTHONHOME to <prefix>[:<exec_prefix>]
ImportError: No module named site
dpkg: error processing package python-minimal (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up python3 (3.4.0-0ubuntu2) ...
running python rtupdate hooks for python3.4...
/usr/share/python3/runtime.d/dh-python.rtupdate: 5: /usr/share/python3/runtime.d/dh-python.rtupdate: py3clean: not found
error running python rtupdate hook dh-python
dpkg: error processing package python3 (--configure):
 subprocess installed post-installation script returned error exit status 4
dpkg: dependency problems prevent configuration of python3-apt:
 python3-apt depends on python3 (>= 3.4~); however:
  Package python3 is not configured yet.
 python3-apt depends on python3 (<< 3.5); however:
  Package python3 is not configured yet.


dpkg: error processing package python3-apt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-problem-report:
 python3-problem-report depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.


dpkg: error processing package python3-problem-report (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb-release:
 lsb-release depends on python3; however:
  Package python3 is not configured yet.
 lsb-release depends on python3:any (>= 3.3.2-2~); however:
  Package pythNo apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                                        No apport report written because MaxReports is reached already
                                                                                                                                                                                      No apport report written because MaxReports is reached already
                                                       No apport report written because MaxReports is reached already
                                                                                                                     No apport report written because MaxReports is reached already
                                                                                                                                                                                   No apport report written because MaxReports is reached already
                                                    No apport report written because MaxReports is reached already
                                                                                                                  on3 is not configured yet.


dpkg: error processing package lsb-release (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-apport:
 python3-apport depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.
 python3-apport depends on python3-apt (>= 0.7.9); however:
  Package python3-apt is not configured yet.
 python3-apport depends on python3-problem-report (>= 0.94); however:
  Package python3-problem-report is not configured yet.
 python3-apport depends on lsb-release; however:
  Package lsb-release is not configured yet.


dpkg: error processing package python3-apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-gi:
 python3-gi depends on python3 (<< 3.5); however:
  Package python3 is not configured yet.
 python3-gi depends on python3 (>= 3.4~); however:
  Package python3 is not configured yet.


dpkg: error processing package python3-gi (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport:
 apport depends on python3; however:
  Package python3 is not configured yet.
 apport depends on python3-apport (>= 2.14.1-0ubuntu3.29); however:
  Package python3-apport is not configured yet.
 apport depends on python3-gi; however:
  Package python3-gi is not configured yet.


dpkg: error processing package apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of dh-python:
 dh-python depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.


dpkg: error processing package dh-python (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-minimal
 python3
 python3-apt
 python3-problem-report
 lsb-release
 python3-apport
 python3-gi
 apport
 dh-python
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I tried removing manually and purging for all python folders I could find from the command:

```
which -a python
```

but am still getting the same errors from the install commands. Any ideas?

---

### Post by Topsiho on 2018-08-03
I don't get it.
The newest Python2 is, as far as I can tell, 2.7.15rc. So prompting you to install 2.7.9 seems a little weird, even if you now have a still older python2
I would think twice before installing from any other source than the Ubuntu repositories, as then you have the biggest chance that it just works on Ubuntu.
And in this case, if you don't want to use these repositories, why don't you use the original source for Python, on the Python website itself ?
There you can see for yourself how old 2.7.9 really is.

Just questions, and suggestions, I'm afraid. Sorry.

Topsiho

---

### Post by mörgæs on 2018-08-06
I have the same doubt as the poster above regarding age. Is it really worth the while to save an installation of 14.04 / 2.7.9? 

Is porting to Python 3 an option?

---

### Post by Impavidus on 2018-08-06
As for those security issues, Ubuntu 14.04 comes with python version 2.7.6-8ubuntu0.4, which means it's python 2.7.6 with some extra fixes as distributed through the Ubuntu repositories. I think it's supposed to be secure.

Messing with python is a bit tricky, as so many essential components of Ubuntu rely on python. Given the age of 14.04, it's also worth to consider a move to Ubuntu 18.04, which has both python 3.6.5 and 2.7.15rc1 available from the repositories. A move to 18.04 may not be convenient to you right now, but you'll have to move on (at least to 16.04, which has python 2.7.12) within the next 8 months. If you make it a clean install, it would clean up any mess you have now.

---

