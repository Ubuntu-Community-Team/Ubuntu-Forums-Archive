---
title: "installation of scid"
date: 2012-07-13
forum: New to Ubuntu
---

### Post by linux002 on 2012-07-13
Hello. I am trying to install the chess database SCID ([http://scid.sourceforge.net/](http://scid.sourceforge.net/)).  Evidently, SCID uses LaTeX for some printing/displaying. I have LaTeX  installed on my system and installation of SCID will result in deletion  of hundreds of megabytes of my LaTeX distribution. I wanted to know if there is a better way to install without being compelled to make major alterations to LaTeX. I do not understand why the installation doesn't simply add the needed dependencies rather than deleting >740 MB of existing files. Thanks in advance.
 

Here is the output of an attempted installation:
 $ sudo apt-get install scid
 Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
   latex-xcolor libkpathsea6 libpoppler19 libptexenc1 libruby1.9.1  libsnack2 libtk-img libyaml-0-2 lmodern ruby ruby1.9.1 scid-data tcllib  tdom
  tex-common texlive-base texlive-binaries texlive-common  texlive-doc-base texlive-games texlive-generic-recommended  texlive-latex-base
  texlive-latex-recommended texlive-pstricks tipa tk8.5
Suggested packages:
   tk wish libsnack2-doc libtk-img-doc ri ruby-dev ruby1.9.1-examples  ri1.9.1 graphviz ruby1.9.1-dev ruby-switch toga2 phalanx glaurung crafty
  scid-spell-data scid-rating-data
The following packages will be REMOVED:
  feynmf purifyeps texlive-extra-utils texlive-font-utils texlive-fonts-extra texlive-fonts-extra-doc texlive-fonts-recommended
   texlive-fonts-recommended-doc texlive-latex-base-doc  texlive-latex-extra texlive-latex-extra-doc  texlive-latex-recommended-doc texlive-latex3
  texlive-luatex  texlive-metapost texlive-metapost-doc texlive-pictures  texlive-pictures-doc texlive-pstricks-doc texlive-publishers-doc
  texlive-science-doc texpower
The following NEW packages will be installed:
   libkpathsea6 libpoppler19 libptexenc1 libruby1.9.1 libsnack2 libtk-img  libyaml-0-2 ruby ruby1.9.1 scid scid-data tcllib tdom texlive-games  tk8.5
The following packages will be upgraded:
  latex-xcolor  lmodern tex-common texlive-base texlive-binaries texlive-common  texlive-doc-base texlive-generic-recommended texlive-latex-base
  texlive-latex-recommended texlive-pstricks tipa
12 upgraded, 15 newly installed, 22 to remove and 321 not upgraded.
Need to get 37.1 MB/113 MB of archives.
After this operation, 744 MB disk space will be freed.

---

