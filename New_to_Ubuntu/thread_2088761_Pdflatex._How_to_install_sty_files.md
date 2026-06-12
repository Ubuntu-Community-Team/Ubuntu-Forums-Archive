---
title: "Pdflatex. How to install sty files?"
date: 2012-11-27
forum: New to Ubuntu
---

### Post by honeybear on 2012-11-27
Hi,

Pdflatex prompts me that sidecap.sty, wrapfig.sty, ... are missing.

Where should be installed these sty files?

I mean into the $HOME or ~/ directory. In the /usr/... share I know that it is possible. but I would rather it into $HOME or ~/ directory

Any ideas?

---

### Post by Bashing-om on 2012-11-27
honeybear; Hi !
I do not recognize the program pdflatex; Additional info is needed.
How did you install the program and why ?
Is this program a part of the package latex ?

installations: Ubuntu installs where each file needs to be (in the complete install picture). Some programs do not have GUI support (this is ubuntu, you can programingly make it so)...IF it is Gui enabled ..one might consider symbolic links from the desired directory to the application location.
[INDENT][INDENT]hth <== BDQ

[/INDENT][/INDENT]

---

### Post by LiamOS on 2012-11-27
Did you install a full latex distribution such as texlive? If so, I'm at a loss, not being much of a tex guru.

---

### Post by honeybear on 2012-11-28
my dpkg :

```


ii  abook                                0.5.6-7                            text-based ncurses address book application
ii  aumix                                2.9.1-1                            Simple text-based mixer control program
ii  aumix-common                         2.9.1-1                            Simple text-based mixer control program (common files)
ii  autopoint                            0.18.1.1-3                         The autopoint program from GNU gettext
ii  catdoc                               0.94.2-1.1                         MS-Word to TeX or plain text converter
ii  catdvi                               0.14-11+b1                         DVI to plain text translator
ii  centerim                             4.22.10-1                          A text-mode multi-protocol instant messenger client
ii  centerim-common                      4.22.10-1                          A text-mode multi-protocol instant messenger client (data files)
ii  dos2unix                             5.0-2                              convert text file line endings between CRLF and LF
ii  elinks                               0.12~pre5-2                        advanced text-mode WWW browser
ii  elinks-data                          0.12~pre5-2                        advanced text-mode WWW browser - data files
ii  gettext                              0.18.1.1-3                         GNU Internationalization utilities
ii  gettext-base                         0.18.1.1-3                         GNU Internationalization utilities for the base system
ii  groff-base                           1.20.1-10                          GNU troff text-formatting system (base system components)
ii  html2text                            1.3.2a-15                          advanced HTML to text converter
ii  latex-beamer                         3.07-2                             LaTeX class to produce presentations
ii  latex-xcolor                         2.11-1                             Easy driver-independent TeX class for color
ii  latex2rtf                            1.9.19-4.1                         Converts documents from LaTeX to RTF format
ii  latexmk                              1:4.13a-1                          Perl script for running LaTeX the correct number of times
ii  leafpad                              0.8.17-5                           GTK+ based simple text editor
ii  libalgorithm-merge-perl              0.08-2                             Perl module for three-way merge of textual data
ii  libdjvulibre-text                    3.5.23-3                           Linguistic support files for libdjvulibre
ii  libhtml-format-perl                  2.04-2                             format HTML syntax trees into text, PostScript or RTF
ii  libhtml-parser-perl                  3.66-1                             collection of modules that parse HTML text documents
ii  libitext-java                        2.1.7-2                            Java Library to create and manipulate PDF on the fly
ii  libitext-java-gcj                    2.1.7-2                            Java Library to create and manipulate PDF on the fly
ii  libkate1                             0.3.7-3                            Kate is a codec for karaoke and text encapsulation
ii  liblocale-gettext-perl               1.05-6                             Using libc functions for internationalization in Perl
ii  libnewt0.52                          0.52.11-1                          Not Erik's Windowing Toolkit - text mode windowing with slang
ii  libpango1.0-0                        1.28.3-1+squeeze2                  Layout and rendering of internationalized text
ii  libtext-charwidth-perl               0.04-6                             get display widths of characters on the terminal
ii  libtext-iconv-perl                   1.7-2                              converts between character sets in Perl
ii  libtext-wrapi18n-perl                0.06-7                             internationalized substitute of Text::Wrap
ii  libtextcat-data-utf8                 2.2-4                              Language detection library - data files
ii  libwps-0.1-1                         0.1.2-1                            Works text file format import filter library (shared library)
ii  luatex                               0.60.2-1                           next generation TeX engine
ii  mawk                                 1.3.3-15                           a pattern scanning and text processing language
ii  mutt                                 1.5.20-9+squeeze1                  text-based mailreader supporting MIME, GPG, PGP and threading
ii  nano                                 2.2.4-1                            small, friendly text editor inspired by Pico
ii  tex-common                           2.08.1                             common infrastructure for building and installing TeX
ii  texlive                              2009-11+squeeze1                   TeX Live: A decent selection of the TeX Live packages
ii  texlive-base                         2009-11+squeeze1                   TeX Live: Essential programs and files
ii  texlive-binaries                     2009-8                             Binaries for TeX Live
ii  texlive-common                       2009-11+squeeze1                   TeX Live: Base component
ii  texlive-doc-base                     2009-2                             TeX Live: TeX Live documentation
ii  texlive-extra-utils                  2009-10                            TeX Live: TeX auxiliary programs
ii  texlive-font-utils                   2009-10                            TeX Live: TeX and Outline font utilities
ii  texlive-fonts-recommended            2009-11+squeeze1                   TeX Live: Recommended fonts
ii  texlive-fonts-recommended-doc        2009-11+squeeze1                   TeX Live: Documentation files for texlive-fonts-recommended
ii  texlive-generic-recommended          2009-11+squeeze1                   TeX Live: Recommended generic packages
ii  texlive-latex-base                   2009-11+squeeze1                   TeX Live: Basic LaTeX packages
ii  texlive-latex-recommended            2009-11+squeeze1                   TeX Live: LaTeX recommended packages
ii  texlive-latex-recommended-doc        2009-11+squeeze1                   TeX Live: Documentation files for texlive-latex-recommended
ii  texlive-metapost                     2009-11+squeeze1                   TeX Live: MetaPost (and Metafont) drawing packages
ii  texlive-metapost-doc                 2009-11+squeeze1                   TeX Live: Documentation files for texlive-metapost
ii  texlive-pstricks                     2009-10                            TeX Live: PSTricks packages
ii  texlive-pstricks-doc                 2009-10                            TeX Live: Documentation files for texlive-pstricks



```

---

### Post by Bashing-om on 2012-11-28
Not knowing what has been done or the status of texlive (?)....=>
Let's clean the system up and establish a firm foundation from which to work from:
#oldfred's methology for restoring
#houseclean
```
sudo apt-get autoclean
``` # only removes files that cannot be downloaded anymore (obsolete)
```
sudo apt-get clean
```#refresh
```
sudo apt-get update
``` #resync package index
```
sudo apt-get upgrade
``` #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required/and install held back packages.
```
sudo apt-get dist-upgrade
``````
apt-get -f install
``````
dpkg --configure -a
```All that does is update it again.

now that all is a clean as can be-> now lets look for any errors;
once again do:
```
sudo apt-get update
sudo apt-get upgrade

```post any errors generated by the two above commands[INDENT][INDENT]try'n to help <== BDQ

[/INDENT][/INDENT]

---

### Post by frisket on 2012-12-11
> **honeybear said:**
> Hi,

Pdflatex prompts me that sidecap.sty, wrapfig.sty, ... are missing.

Where should be installed these sty files?

I mean into the $HOME or ~/ directory. In the /usr/... share I know that it is possible. but I would rather it into $HOME or ~/ directory

Any ideas?

There is only one place: in your personal TeX tree.
This is ~/texmf, so create it now, and install packages that didn't come with your distribution in there, in the right subdirectories. TeX will automatically check ~/texmf before anything else.

.sty files go in ~/texmf/tex/latex/xxxxx where xxxxx is the name of the package, so sidecap.sty goes in ~/texmf/tex/latex/sidecap, etc. 

Don't put add-on files anywhere else, because they won't be found.

///Peter

---

### Post by honeybear on 2012-12-12
> **frisket said:**
> There is only one place: in your personal TeX tree.
This is ~/texmf, so create it now, and install packages that didn't come with your distribution in there, in the right subdirectories. TeX will automatically check ~/texmf before anything else.

.sty files go in ~/texmf/tex/latex/xxxxx where xxxxx is the name of the package, so sidecap.sty goes in ~/texmf/tex/latex/sidecap, etc. 

Don't put add-on files anywhere else, because they won't be found.

///Peter



Thank you . ... ! this reply is of quality.

THis is hte infroamtion that I needed for $HOME i.e.:


```
.sty files go in ~/texmf/tex/latex/xxxxx where xxxxx is the name of the package, so sidecap.sty goes in ~/texmf/tex/latex/sidecap, etc. 
```

---

### Post by Impavidus on 2012-12-12
> **frisket said:**
> There is only one place: in your personal TeX tree.
This is ~/texmf, so create it now, and install packages that didn't come with your distribution in there, in the right subdirectories. TeX will automatically check ~/texmf before anything else.

.sty files go in ~/texmf/tex/latex/xxxxx where xxxxx is the name of the package, so sidecap.sty goes in ~/texmf/tex/latex/sidecap, etc. 

Don't put add-on files anywhere else, because they won't be found.

///Peter
Any latex files you install manually have to be installed in subdirectories in either ~/texmf or /usr/local/share/texmf. Installation in the latter makes them available to all users of the system. After copying the files there, make sure you use "sudo texhash" so that latex will find the files.

---

