---
title: "Tex Live 2009 --&gt; TeX Live 2013 update FAIL in Ubuntu 10.04 LTS"
date: 2014-03-26
forum: New to Ubuntu
---

### Post by xptional on 2014-03-26
"Ubuntu 10.04 LTS Lucid"
I have recently installed TeX Live 2013 from install-tl-unx.tar.gz downloaded from site. then running 
```
sudo ./install-tl
```
After that I have set the paths in ~/.bashrc file as below :
> # Path for TeX Live 2013
export PATH=$PATH:/usr/local/texlive/2013/bin/i386-linux
export INFOPATH=$INFOPATH:/usr/local/texlive/2013/texmf-dist/doc/info
export MANPATH=$MANPATH:/usr/local/texlive/2013/texmf-dist/doc/man
 I did ```
sudo texhash
``` I restarted the computer,
BUT VERSION OF TEXLIVE doesn't change.
```
 tex --version
```
> TeX 3.1415926 (TeX Live 2009/Debian)
kpathsea version 5.0.0
Copyright 2009 D.E. Knuth.
There is NO warranty.  Redistribution of this software is
covered by the terms of both the TeX copyright and
the Lesser GNU General Public License.
For more information about these matters, see the file
named COPYING and the TeX source.
Primary author of TeX: D.E. Knuth.

Anyhow, I can run .tex files, But I need the updated version. 
Any HELP Please ! 
Thanks in advance for you HELP.

---

### Post by grahammechanical on 2014-03-26
May be you also need an updated version of Ubuntu.

---

### Post by Impavidus on 2014-03-26
10.04 is end of life. A more recent Ubuntu may have the right version of TexLive. Note that 12.04 still has TexLive 2009, so you'd have to try Ubuntu 13.10. I still use TexLive 2009, but I manually updated the few packages of which I needed a more recent version, in addition to installing some home-made packages.

---

