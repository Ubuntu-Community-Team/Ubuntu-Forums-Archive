---
title: "TeXlive 2007 search path problem.  TeX cannot find the texlive directory!"
date: 2008-01-25
forum: Programming Talk
---

### Post by Trafferth on 2008-01-25
Hi all,

I have a problem with TeX Live 2007.  I am attempting to use the package "psfig.sty", so I have a "\includepackage{psfig}" statement at the start of my tex document.  However, when I then attempt to LaTeX the document, the error message "! LaTeX Error: File `psfig.sty' not found." appears.

I know that the file in question is located at "/usr/local/texlive/2007/texmf-dist/tex/generic/psfig/psfig.sty" although attempting to locate the file with ```
kpsewhich psfig.sty
``` drew a blank.  I found it instead by using: ```
locate psfig.sty
```

The issue here is probably a path problem, so  I took the following steps to try and point TeX in the right direction:

First, I set: ```
export TEXINPUTS="/usr/local/texlive"
```

I then rehash: ```
sudo texconfig rehash
```

Testing the configuration with: ```
texconfig conf
``` shows that the kpsearch "from environment" variable is set to "usr/local/texlive".  Now, of course I can locate the file by typing ```
kpsewhich psfig.sty
```

Maddeningly, while kpsearch now returns the desired path to psfig.sty, whenever I attempt to LaTeX the document, (either from gedit, TexMaker, or manually), I still get the "! LaTeX Error: File `psfig.sty' not found." error message.  As far as I understand it, TeX uses kpsearch to find files, so I am a bit confused as to why the file cannot be found when attempting to invoke LaTeX.

I have noticed that the TEXMFLOCAL parameter was set to "/usr/local/shar/texmf", which does not exist on my machine.  I therefore set TEXMFLOCAL to "/usr/local/texlive" as before, rehashed, and attempted to LaTeX my document.  Again, the error message appears.

As a temporary measure, I have copied psfig.sty into the same directory as the .tex files I am using (which allows the file to compile correctly).  However, since "/usr/local/texlive" is an installation directory, one would have thought TeX would be able to find it.  I am sure that I only need to set a search parameter and rehash, but I am apparently missing something obvious.  Any help would be greatly appreciated.

---

### Post by Trafferth on 2008-01-27
Okay, having tried setting the various parameters listed in texconfig without any joy, I am going to reinstall from the TeXlive 2007 iso.  I seem to remember that I might have changed an install directory from the defaults, so I shall run the installation script without changing anything this time, and will see if that works.  I can't think of what else to do at the moment... :confused:

---

### Post by meho_r on 2008-01-27
Why not install from Ubuntu repos? This way you don't need to configure anything by hand and texlive paths should be ok

---

### Post by Trafferth on 2008-01-27
Having reinstalled TeXlive 2007 using the defaults has made the problem worse.  Now texconfig cannot find *any* config file.  Here is the output from texconfig:

```


=========================== version information ==========================
teTeX-src release:   (info not available)
teTeX-texmf release: (info not available)

==================== binaries found by searching $PATH ===================
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
kpsewhich: /usr/bin/kpsewhich
updmap: /usr/bin/updmap
fmtutil: /usr/bin/fmtutil
texconfig: /usr/bin/texconfig
tex: /usr/bin/tex
pdftex: /usr/bin/pdftex
mktexpk: /usr/bin/mktexpk
dvips: /usr/bin/dvips
dvipdfm: /usr/bin/dvipdfm

=========================== active config files ==========================
/usr/bin/texconfig: 1424: //texmf/texconfig/tcfmgr: not found
/usr/bin/texconfig: 1424: //texmf/texconfig/tcfmgr: not found
/usr/bin/texconfig: 1424: //texmf/texconfig/tcfmgr: not found
/usr/bin/texconfig: 1424: //texmf/texconfig/tcfmgr: not found
/usr/bin/texconfig: 1424: //texmf/texconfig/tcfmgr: not found
/usr/bin/texconfig: 1424: //texmf/texconfig/tcfmgr: not found
/usr/bin/texconfig: 1424: //texmf/texconfig/tcfmgr: not found
/usr/local/share/texmf/web2c/texmf.cnf
config: not found
config.ps: not found
fmtutil.cnf: not found
mktex.cnf: not found
pdftexconfig.tex: not found
updmap.cfg: not found
XDvi: not found

============================= font map files =============================
psfonts.map: 
pdftex.map: 
ps2pk.map: 
dvipdfm.map: 

=========================== kpathsea variables ===========================
TEXMFMAIN=//texmf
TEXMFDIST=//texmf-dist
TEXMFLOCAL=/usr/local/texlive/2007/texmf-local
TEXMFSYSVAR=//texmf-var
TEXMFSYSCONFIG=//texmf-config
TEXMFVAR=/home/richard/.texlive2007/texmf-var
TEXMFCONFIG=/home/richard/.texlive2007/texmf-config
TEXMFHOME=/home/richard/texmf
VARTEXFONTS=/home/richard/.texlive2007/texmf-var/fonts
TEXMF={/home/richard/.texlive2007/texmf-config,/home/richard/.texlive2007/texmf-var,/home/richard/texmf,!!//texmf-config,!!//texmf-var,!!//texmf,!!/usr/local/texlive/2007/texmf-local,!!//texmf-dist}
SYSTEXMF=/usr/local/texlive/2007/texmf-local://texmf://texmf-dist
TEXMFDBS={!!//texmf-config,!!//texmf-var,!!//texmf,!!/usr/local/texlive/2007/texmf-local,!!//texmf-dist}
WEB2C={/home/richard/.texlive2007/texmf-config,/home/richard/.texlive2007/texmf-var,/home/richard/texmf,!!//texmf-config,!!//texmf-var,!!//texmf,!!/usr/local/texlive/2007/texmf-local,!!//texmf-dist}/web2c
TEXPSHEADERS=.:{/home/richard/.texlive2007/texmf-config,/home/richard/.texlive2007/texmf-var,/home/richard/texmf,!!//texmf-config,!!//texmf-var,!!//texmf,!!/usr/local/texlive/2007/texmf-local,!!//texmf-dist}/{dvips,fonts/{enc,type1,type42,type3}}//
TEXCONFIG={/home/richard/.texlive2007/texmf-config,/home/richard/.texlive2007/texmf-var,/home/richard/texmf,!!//texmf-config,!!//texmf-var,!!//texmf,!!/usr/local/texlive/2007/texmf-local,!!//texmf-dist}/dvips//
ENCFONTS=.:{/home/richard/.texlive2007/texmf-config,/home/richard/.texlive2007/texmf-var,/home/richard/texmf,!!//texmf-config,!!//texmf-var,!!//texmf,!!/usr/local/texlive/2007/texmf-local,!!//texmf-dist}/fonts/enc//
TEXFONTMAPS=.:{/home/richard/.texlive2007/texmf-config,/home/richard/.texlive2007/texmf-var,/home/richard/texmf,!!//texmf-config,!!//texmf-var,!!//texmf,!!/usr/local/texlive/2007/texmf-local,!!//texmf-dist}/fonts/map/{kpsewhich,pdftex,dvips,}//

==== kpathsea variables (from environment only; ok if no output here) ====


```

Attempting to rehash doesn't help at all.  It would seem I have broken TeX quite comprehensively... :( 

Seeing as there's not that much on my linux box, I suppose I can reinstall Gutsy and try again.  Can anyone say if it would be better to install from the Gutsy repositories rather than the TeXlive 2007 ISO?  Does anyone have any experience with this?

---

### Post by Trafferth on 2008-01-27
Hi, meho_r!

Do you know if I can just install the repo version over my current mess of files, or should I go through the system and try and remove as much as possible beforehand? :S

---

### Post by Trafferth on 2008-01-27
I have now reinstalled Gutsy and used the texlive metapackage from the repos.  Runs perfectly.  Thanks, meho_r!

Guess this will teach me to check the repos first! :D

---

### Post by meho_r on 2008-01-27
You're welcome. Well, I learned it the same way you did;) Glad it works.

---

