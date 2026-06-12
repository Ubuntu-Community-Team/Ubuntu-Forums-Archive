---
title: "how to install texworks-0.4.4"
date: 2012-11-04
forum: New to Ubuntu
---

### Post by bekirs on 2012-11-04
Hi,

as an absolute beginner, I need some instructions to install the latest stable version of **texworks-0.4.4**, that I downloaded from [http://tug.org/texworks/]("http://tug.org/texworks/").

I have xubuntu 12.04 installed in my laptop.

Thanks in advance,

---

### Post by Impavidus on 2012-11-04
Texworks is in the repository, so the easy way is going to the software centre, searching for texworks and clicking "install". However, this seems to be version 0.5. It probably works fine, else it wouldn't be in the repository, but you can install the older version as well if you really need it.

It depends on which file you downloaded, but the easy way is using one of the .deb files (the one matching your computer/operating system). Just download, double click and it should work. I haven't tried it myself, though.

---

### Post by newb85 on 2012-11-04
Hmm...it does seem odd that the version mentioned on their website and included in their PPA is older than the one in the main repositories.

Rather than downloading and installing from the .deb, I would add their PPA:
```
sudo add-apt-repository ppa:texworks/stable
sudo apt-get update
```

[s](If you're using 12.10, that command is apt-add-repository.)[/s]

---

### Post by bekirs on 2012-11-04
I tried to install with the codes you provided but I couldn't see TeXworks in my "applications menu". It doesn't seem to be installed.

---

### Post by bekirs on 2012-11-04
When I install the version that is available in the repository, I get the following the message "Package operation failed" and "The installation or removal of a software package failed."

More frustrating message under the details is the following:
```
installArchives() failed: Selecting previously unselected package texworks.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 328954 files and directories currently installed.)
Unpacking texworks (from .../texworks_0.5~svn952-1_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Setting up tex-common (2.10) ...
Error: The new file /usr/share/tex-common/05TeXMF.cnf does not exist!
dpkg: error processing tex-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of texlive-pstricks:
 texlive-pstricks depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
dpkg: error processing texlive-pstricks (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of asymptote:
 asymptote depends on texlive-pstricks; however:
  Package texlive-pstricks is not configured yet.
 asymptote depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
dpkg: error processing asymptote (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of preview-latex-style:
 preview-latex-style depends on tex-common; however:
  Package tex-common is not configured yet.
dpkg: error processing preview-latex-style (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of auctex:
 auctex depends on preview-latex-style; however:
  PaNo apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
ckage preview-latex-style is not configured yet.
dpkg: error processing auctex (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hevea:
 hevea depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
dpkg: error processing hevea (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of jadetex:
 jadetex depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
dpkg: error processing jadetex (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of pgf:
 pgf depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
dpkg: error processing pgf (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of latex-beamer:
 latex-beamer depends on pgf (>= 1.00-1); however:
  Package pgf is not configured yet.
dpkg: error processing latex-beamer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of latex-sanskrit:
 latex-sanskrit depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
dpkg: error processing latex-sanskrit (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of prosper:
 prosper depends on texlive-pstricks; however:
  Package texlive-pstricks is not configured yet.
 prosper depends on tex-common (>= 1.10); however:
  Package tex-common is not configured yet.
dpkg: error processing prosper (--configure):
 dependency problems - leaving unconfigured
Setting up tex4ht-common (20090611-1.1) ...
texhash: /usr/share/texmf not a directory.
texhash: Done.
cp: cannot stat `/usr/share/tex-common/texmf.cnf.md5sum.d/': No such file or directory
dpkg: error processing tex4ht-common (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of tex4ht:
 tex4ht depends on tex4ht-common (= 20090611-1.1); however:
  Package tex4ht-common is not configured yet.
dpkg: error processing tex4ht (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of texlive-bibtex-extra:
 texlive-bibtex-extra depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
dpkg: error processing texlive-bibtex-extra (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of texlive-doc-en:
 texlive-doc-en depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
dpkg: error processing texlive-doc-en (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of texlive-doc-tr:
 texlive-doc-tr depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
dpkg: error processing texlive-doc-tr (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of texlive-pictures:
 texlive-pictures depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
dpkg: error processing texlive-pictures (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of texlive-latex-extra:
 texlive-latex-extra depends on preview-latex-style; however:
  Package preview-latex-style is not configured yet.
 texlive-latex-extra depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
 texlive-latex-extra depends on texlive-pictures (>= 2009-1); however:
  Package texlive-pictures is not configured yet.
dpkg: error processing texlive-latex-extra (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of texlive-latex-extra-doc:
 texlive-latex-extra-doc depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
dpkg: error processing texlive-latex-extra-doc (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of texlive-pictures-doc:
 texlive-pictures-doc depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
dpkg: error processing texlive-pictures-doc (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
Setting up texworks (0.5~svn952-1) ...
Errors were encountered while processing:
 tex-common
 texlive-pstricks
 asymptote
 preview-latex-style
 auctex
 hevea
 jadetex
 pgf
 latex-beamer
 latex-sanskrit
 prosper
 tex4ht-common
 tex4ht
 texlive-bibtex-extra
 texlive-doc-en
 texlive-doc-tr
 texlive-pictures
 texlive-latex-extra
 texlive-latex-extra-doc
 texlive-pictures-doc
Error in function: 
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1)
Setting up tex4ht-common (20090611-1.1) ...
texhash: /usr/share/texmf not a directory.
texhash: Done.
cp: cannot stat `/usr/share/tex-common/texmf.cnf.md5sum.d/': No such file or directory
dpkg: error processing tex4ht-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of tex4ht:
 tex4ht depends on tex4ht-common (= 20090611-1.1); however:
  Package tex4ht-common is not configured yet.
dpkg: error processing tex4ht (--configure):
 dependency problems - leaving unconfigured
Setting up tex-common (2.10) ...
Error: The new file /usr/share/tex-common/05TeXMF.cnf does not exist!
dpkg: error processing tex-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of texlive-latex-extra-doc:
 texlive-latex-extra-doc depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
dpkg: error processing texlive-latex-extra-doc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of prosper:
 prosper depends on tex-common (>= 1.10); however:
  Package tex-common is not configured yet.
dpkg: error processing prosper (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of jadetex:
 jadetex depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
dpkg: error processing jadetex (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-pictures:
 texlive-pictures depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
dpkg: error processing texlive-pictures (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of preview-latex-style:
 preview-latex-style depends on tex-common; however:
  Package tex-common is not configured yet.
dpkg: error processing preview-latex-style (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-pictures-doc:
 texlive-pictures-doc depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
dpkg: error processing texlive-pictures-doc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of pgf:
 pgf depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
dpkg: error processing pgf (--configure):
 dependency problems - leaving unconfigured
```

---

### Post by bryncoles on 2012-11-04
Hi bekirs.  

Well, I can't help with your specific problem (yay me!), but I can suggests some alternatives.  I started learning LaTeX using [TeXmaker](http://www.xm1math.net/texmaker/), which I liked because it is cross-platform, so it's available whatever system you end up using.  

I eventually just ended up using leafpad and the terminal though!

Some useful resources to help you progress in your LaTeXing (Which I presume you have already found, but it wouldn't hurt for me to repeat them here) are [the not so short guide to LaTeX](http://tobi.oetiker.ch/lshort/lshort.pdf) along with the [LaTeX wikibook](http://en.wikibooks.org/wiki/LaTeX)

Hopefully that'll be of some use to you...

---

### Post by newb85 on 2012-11-04
Please give the output of
```
ls /usr/share/tex-common
```

---

### Post by bekirs on 2012-11-05
here is the output

```
ls /usr/share/tex-common

ls: cannot access /usr/share/tex-common: No such file or directory

```

---

### Post by Abhinav Kumar on 2012-11-05
> **bryncoles said:**
> Hi bekirs.  

Well, I can't help with your specific problem (yay me!), but I can suggests some alternatives.  I started learning LaTeX using [TeXmaker]("http://www.xm1math.net/texmaker/"), which I liked because it is cross-platform, so it's available whatever system you end up using.  

I eventually just ended up using leafpad and the terminal though!

Some useful resources to help you progress in your LaTeXing (Which I presume you have already found, but it wouldn't hurt for me to repeat them here) are [the not so short guide to LaTeX]("http://tobi.oetiker.ch/lshort/lshort.pdf") along with the [LaTeX wikibook]("http://en.wikibooks.org/wiki/LaTeX")

Hopefully that'll be of some use to you...
You can also try Kile.

---

### Post by newb85 on 2012-11-05
> **bekirs said:**
> here is the output

```
ls /usr/share/tex-common

ls: cannot access /usr/share/tex-common: No such file or directory

```

Well, I don't know if this will work, but I would try
```
sudo mkdir /usr/share/tex-common
sudo touch /usr/share/tex-common/05TeXMF.cnf
sudo apt-get install texworks
```

---

### Post by bekirs on 2012-11-05
> **newb85 said:**
> Well, I don't know if this will work, but I would try
```
sudo mkdir /usr/share/tex-common
sudo touch /usr/share/tex-common/05TeXMF.cnf
sudo apt-get install texworks
```

here is the output:

```
 sudo apt-get install texworks

Reading package lists... Done
Building dependency tree       
Reading state information... Done
texworks is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 texlive-base : Depends: tex-common (>= 3) but 2.10 is to be installed
 texlive-binaries : Depends: tex-common (>= 3) but 2.10 is to be installed
                    Recommends: ruby
 texlive-common : Depends: tex-common (>= 3) but 2.10 is to be installed
 texlive-doc-base : Depends: tex-common (>= 3) but 2.10 is to be installed
 texlive-fonts-recommended : Depends: tex-common (>= 3) but 2.10 is to be installed
                             Recommends: texlive-fonts-recommended-doc but it is not going to be installed
                             Recommends: tex-gyre but it is not going to be installed
 texlive-generic-recommended : Depends: tex-common (>= 3) but 2.10 is to be installed
 texlive-latex-base : Depends: tex-common (>= 3) but 2.10 is to be installed
                      Recommends: texlive-latex-base-doc but it is not going to be installed
 texlive-latex-recommended : Depends: tex-common (>= 3) but 2.10 is to be installed
                             Recommends: texlive-latex-recommended-doc but it is not going to be installed
                             Recommends: prosper (>= 1.00.4+cvs.2006.10.22) but it is not going to be installed
 tipa : Depends: tex-common (>= 3) but 2.10 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


```

---

### Post by newb85 on 2012-11-05
Try the suggestion:
```
sudo apt-get -f install
```

---

### Post by bekirs on 2012-11-05
> **newb85 said:**
> Try the suggestion:
```
sudo apt-get -f install
```

output:

```

sudo apt-get -f install

[sudo] password for ******: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libreoffice-help-en-gb libreoffice-help-en-us libunistring0 mythes-en-au
  mythes-en-us libqt4-test language-pack-kde-zh-hans-base hyphen-en-us
  po-debconf intltool-debian firefox-locale-zh-hans libgconf2-4:i386 gettext
  libqt4-help python-qt4 python-sip kde-l10n-engb libqtassistantclient4
  libgettextpo0 language-pack-zh-hans-base libreoffice-l10n-zh-cn
  kde-l10n-zhcn language-pack-zh-hans language-pack-kde-zh-hans
  libmail-sendmail-perl libreoffice-help-zh-cn libsys-hostname-long-perl
  libnss3-1d:i386 libreoffice-l10n-en-gb openoffice.org-hyphenation
  libreoffice-l10n-en-za
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  jadetex latex-sanskrit tex-common
Suggested packages:
  docbook-dsssl debhelper
The following packages will be upgraded:
  jadetex latex-sanskrit tex-common
3 upgraded, 0 newly installed, 0 to remove and 18 not upgraded.
20 not fully installed or removed.
Need to get 0 B/1,981 kB of archives.
After this operation, 600 kB disk space will be freed.
Do you want to continue [Y/n]? y
Setting up tex-common (2.10) ...
Replacing config file /etc/texmf/texmf.d/05TeXMF.cnf with new version
Error: The new file /usr/share/tex-common/15Plain.cnf does not exist!
dpkg: error processing tex-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of texlive-common:
 texlive-common depends on tex-common (>= 3); however:
  Version of tex-common on system is 2.10.
dpkg: error processing texlive-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-binaries:
 texlive-binaries depends on texlive-common (>= 2011); however:
  Package texlive-common is not configured yet.
 texlive-binaries depends on tex-common (>= 3); however:
  Version of tex-common on system is 2.10.
dpkg: error processing texlive-binaries (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-doc-base:
 texlive-doc-base depends on texlive-common (>= 2012.20120516); however:
  Package texlive-common is not configured yet.
 texlive-doc-base depends on tex-common (>= 3); however:
  Version of tex-common on system is 2.10.
dpkg: error processing texlive-doc-base (--configure):
 dependency problemNo apport report written because the error message indicates its a followup error from a previous failure.
                                             No apport report written because the error message indicates its a followup error from a previous failure.
                                                                       No apport report written because MaxReports is reached already
                                                     No apport report written because MaxReports is reached already
                                   No apport report written because MaxReports is reached already
                 No apport report written because MaxReports is reached already
                                                                               No apport report written because MaxReports is reached already
                                                             No apport report written because MaxReports is reached already
                                           No apport report written because MaxReports is reached already
                         No apport report written because MaxReports is reached already
       No apport report written because MaxReports is reached already
                                                                     No apport report written because MaxReports is reached already
                                                   No apport report written because MaxReports is reached already
                                 s - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-base:
 texlive-base depends on texlive-doc-base (>= 2012.20120516); however:
  Package texlive-doc-base is not configured yet.
 texlive-base depends on texlive-binaries (>= 2012.20120516); however:
  Package texlive-binaries is not configured yet.
 texlive-base depends on texlive-common (>= 2012.20120516); however:
  Package texlive-common is not configured yet.
 texlive-base depends on tex-common (>= 3); however:
  Version of tex-common on system is 2.10.
dpkg: error processing texlive-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-base:
 texlive-latex-base depends on texlive-binaries (>= 2012-0); however:
  Package texlive-binaries is not configured yet.
 texlive-latex-base depends on texlive-common (>= 2012.20120516); however:
  Package texlive-common is not configured yet.
 texlive-latex-base depends on tex-common (>= 3); howNo apport report written because MaxReports is reached already
                                   No apport report written because MaxReports is reached already
                 No apport report written because MaxReports is reached already
                                                                               No apport report written because MaxReports is reached already
                                                             No apport report written because MaxReports is reached already
                                           No apport report written because MaxReports is reached already
                         ever:
  Version of tex-common on system is 2.10.
 texlive-latex-base depends on texlive-base (>= 2012.20120516); however:
  Package texlive-base is not configured yet.
dpkg: error processing texlive-latex-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-fonts-recommended:
 texlive-fonts-recommended depends on texlive-common (>= 2012.20120516); however:
  Package texlive-common is not configured yet.
 texlive-fonts-recommended depends on tex-common (>= 3); however:
  Version of tex-common on system is 2.10.
 texlive-fonts-recommended depends on texlive-base (>= 2012.20120516); however:
  Package texlive-base is not configured yet.
dpkg: error processing texlive-fonts-recommended (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-recommended:
 texlive-latex-recommended depends on texlive-binaries (>= 2012-0); however:
  Package texlive-binaries is not configured yet.
 texlive-latex-recommended depends on texlive-latex-base (>= 2012.20120516); however:
  Package texlive-latex-base is not configured yet.
 texlive-latex-recommended depends on texlive-common (>= 2012.20120516); however:
  Package texlive-common is not configured yet.
 texlive-latex-recommended depends on tex-common (>= 3); however:
  Version of tex-common on system is 2.10.
dpkg: error processing texlive-latex-recommended (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-generic-recommended:
 texlive-generic-recommended depends on texlive-common (>= 2012.20120516); however:
  Package texlive-common is not configured yet.
 texlive-generic-recommended depends on tex-common (>= 3); however:
  Version of tex-common on system is 2.10.
 texlive-generic-recommended depends on texlive-base (>= 2012.20120516); however:
  Package texlive-base is not configured yet.
dpkg: error processing texlive-generic-recommended (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of tipa:
 tipa depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.
 tipa depends on texlive-base-bin; however:
  Package texlive-base-bin is not installed.
  Package texlive-binaries which provides texlive-base-bin is not configured yet.
 tipa depends on tex-common (>= 3); however:
  Version of tex-common on system is 2.10.
dpkg: error processing tipa (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of jadetex:
 jadetex depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
 jadetex depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.
 jadetex depends on texlive-fonts-recommended; however:
  Package texlive-fonts-recommended is not configured yet.
 jadetex depends on texlive-latex-recommended; however:
  Package texlive-latex-recommended is not configured yet.
 jadetex depends on tipa; however:
  Package tipa is not configured yet.
dpkg: error processing jadetex (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of latex-sanskrit:
 latex-sanskrit depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
 latex-sanskrit depends on texlive-base; however:
  Package texlive-base is not configured yet.
dpkg: error processing latex-sanskrit (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of preview-latex-style:
 preview-latex-style depends on tex-common; however:
  Package tex-common is not configured yet.
dpkg: error processing preview-latex-style (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of auctex:
 auctex depends on preview-latex-style; however:
  Package preview-latex-style is not configured yet.
dpkg: error processing auctex (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hevea:
 hevea depends on texlive-base; however:
  Package texlive-base is not configured yet.
 hevea depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
dpkg: error processing hevea (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of pgf:
 pgf depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
 pgf depends on texlive-latex-recommended; however:
  Package texlive-latex-recommended is not configured yet.
dpkg: error processing pgf (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of latex-beamer:
 latex-beamer depends on pgf (>= 1.00-1); however:
  Package pgf is not configured yet.
 latex-beamer depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.
dpkg: error processing latex-beamer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of tex4ht-common:
 tex4ht-common depends on texlive-base-bin; however:
  Package texlive-base-bin is not installed.
  Package texlive-binaries which provides texlive-base-bin is not configured yet.
dpkg: error processing tex4ht-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of tex4ht:
 tex4ht depends on texlive-base-bin; however:
  Package texlive-base-bin is not installed.
  Package texlive-binaries which provides texlive-base-bin is not configured yet.
 tex4ht depends on tex4ht-common (= 20090611-1.1); however:
  Package tex4ht-common is not configured yet.
dpkg: error processing tex4ht (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive:
 texlive depends on texlive-latex-base (>= 2012.20120516); however:
  Package texlive-latex-base is not configured yet.
 texlive depends on texlive-fonts-recommended (>= 2012.20120516); however:
  Package texlive-fonts-recommended is not configured yet.
 texlive depends on texlive-latex-recommended (>= 2012.20120516); however:
  Package texlive-latex-recommended is not configured yet.
dpkg: error processing texlive (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 tex-common
 texlive-common
 texlive-binaries
 texlive-doc-base
 texlive-base
 texlive-latex-base
 texlive-fonts-recommended
 texlive-latex-recommended
 texlive-generic-recommended
 tipa
 jadetex
 latex-sanskrit
 preview-latex-style
 auctex
 hevea
 pgf
 latex-beamer
 tex4ht-common
 tex4ht
 texlive
E: Sub-process /usr/bin/dpkg returned an error code (1

```

---

