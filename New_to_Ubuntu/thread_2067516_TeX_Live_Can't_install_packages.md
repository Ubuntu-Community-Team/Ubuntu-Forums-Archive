---
title: "TeX Live: Can't install packages"
date: 2012-10-07
forum: New to Ubuntu
---

### Post by intercept on 2012-10-07
I'm new to both ubuntu and TeX. I'm trying to install the fourier package. Your help is very appreciated!

I've installed the 2012 version of TeXlive, and that software works. I can't use tlmgr to add packages though. 


```
adam@adam-PORTEGE-R705:~$ tlmgr install fourier
You don't have permission to change the installation in any way,
specifically, the directory /usr/local/texlive/2012/tlpkg/ is not writable.
Please run this program as administrator, or contact your local admin.
adam@adam-PORTEGE-R705:~$ sudo tlmgr install fourier
[sudo] password for adam: 
sudo: tlmgr: command not found
```

That's my original problem. So I downloaded update-tlmgr-latest. 

```

adam@adam-PORTEGE-R705:~/Downloads$ sh update-tlmgr-latest.sh
Verifying archive integrity... All good.
Uncompressing TeX Live Manager Updater..........................................................................................................................................................................
./runme.sh: Cannot find TeX Live root using kpsewhich --var-value=SELFAUTOPARENT.
./runme.sh: Please call update-tlmgr-latest.sh --noexec --keep
./runme.sh: and then call the runme.sh script in the unpacked directory
./runme.sh: with the directory root as the first argument, something like:
./runme.sh: sh runme.sh /path/to/your/texlive/installation/2010
```

So I do that:

```

adam@adam-PORTEGE-R705:~/Downloads$ sh update-tlmgr-latest.sh
Verifying archive integrity... All good.
Uncompressing TeX Live Manager Updater..........................................................................................................................................................................
./runme.sh: Cannot find TeX Live root using kpsewhich --var-value=SELFAUTOPARENT.
./runme.sh: Please call update-tlmgr-latest.sh --noexec --keep
./runme.sh: and then call the runme.sh script in the unpacked directory
./runme.sh: with the directory root as the first argument, something like:
./runme.sh: sh runme.sh /path/to/your/texlive/installation/2010
```

That suggests that the files are missing from .../2012. but:


```
adam@adam-PORTEGE-R705:/usr/local/texlive/2012$ ls
bin         install-tl.log  readme-html.dir      texmf         texmf-dist
doc.html    LICENSE.CTAN    readme-txt.dir       texmf.cnf     texmf-var
index.html  LICENSE.TL      README.usergroups    texmfcnf.lua  tlpkg
install-tl  README          release-texlive.txt  texmf-config
```

Same story if I use the parent folder as the argument:


```
adam@adam-PORTEGE-R705:~/Downloads/tmp.x1wSK2Rm2B$ sh runme.sh usr/local/texlive/2012
runme.sh: Cannot find TeX Live root using kpsewhich --var-value=SELFAUTOPARENT.
runme.sh: Please call update-tlmgr-latest.sh --noexec --keep
runme.sh: and then call the runme.sh script in the unpacked directory
runme.sh: with the directory root as the first argument, something like:
runme.sh: sh runme.sh /path/to/your/texlive/installation/2010
```

I want to be able to install packages using tlmgr. How can I do this?

---

