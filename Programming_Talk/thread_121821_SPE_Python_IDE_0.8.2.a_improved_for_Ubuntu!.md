---
title: "SPE Python IDE 0.8.2.a improved for Ubuntu!"
date: 2006-01-26
forum: Programming Talk
---

### Post by stani on 2006-01-26
News from [http://pythonide.stani.be](http://pythonide.stani.be)

This is an important a bugfix release for all platforms. Be sure to grab it when it comes out!! It has a new feature to customize your fonts and colors (styles). 

Thanks to Marco Ferreira there will be very soon a debian package to install SPE easily and create an entry in the start menu on debian based linux distro's such as Ubuntu.  I'm also in contact with Matthias Klose to make an updated SPE available with the Ubuntu Dapper Drake release.

:**New features**:

- Configurable style editor for fonts and colors (Idle, ...)
- Inspect interactively after running script in terminal
- Debian installer for Ubuntu, etc... by Marco Ferreira

:**Fixes**:

- dot bug after ')'
- prevent unsplitting by double clicking sidebar sash
- tar.gz archive shrinked to 65% of its original size (only 833kb!)
- Linux: fix for the Browser (tested on Ubuntu)
- Linux: added firefox to webbrowser list and is default browser if present
- Linux: run in terminal for konsole and gnome-terminal
- Linux: sidebar fits better around it contents
- Mac: sash is enlarged to 6 pixels
- Mac: new feature: browser in sidebar (for wxPython 2.6.2+)
- Linux &amp; Mac: a lot of visual glitches are fixed
- Windows: SPE shortcut in Windows start menu works again
- Windows: Run in terminal input
- Windows: NotebookCtrl fixed


:**Manual**:

- Installation: added section for Ubuntu and Debian systems.
- Tutorial: the SPE tutorial has been completely rewritten by Dimitri to be up to date with the latest version (review and leave your comments at [http://www.serpia.org/spe](http://www.serpia.org/spe) ...)
- global revision

:**Donations**:

- Marco Ferreira (Debian installers)

:**Donations**:

- Harry Miktarian (16.10 euro)
- Amit Antebi (10 euro)
- Steven Hepple (10 euro)

Each of these donators can request the manual.

---

### Post by rich on 2006-01-26
This is exciting news. 

I'm just about to begin coding under linux, and from the reviews SPE is good stuff. 

Do you have an estimate of how long the deb will take ? I'm not sure whether to jump in now or hold off for a few days.


cheers,
Rich

---

### Post by stani on 2006-01-26
[QUOTE=rich]This is exciting news. 

I'm just about to begin coding under linux, and from the reviews SPE is good stuff. 

Do you have an estimate of how long the deb will take ? I'm not sure whether to jump in now or hold off for a few days.


cheers,
Rich[/QUOTE]

Marco is packaging it and I expect that he can do it any moment. So probably not for a few days...

Stani

---

### Post by Se7h on 2006-01-26
Good afternoon stani and rich.

Rich, I expect the deb package to be ready today.
It's just the time to make some tests on the package and post the file on berlios:cool: 

Cumps

---

### Post by krypto_wizard on 2006-01-31
How to use this new version of Stani ? 

Is there a Ubuntu Build. I downloaded the .deb f```

```ile and tried to install using 

```
dpkg -i FileName.deb
```

```

and I got the following error
(Reading database ... 143454 files and directories currently installed.)
Unpacking python2.4-spe (from SPE_0.8.2.a-wx2.6.1.0-py2.4.deb) ...
dpkg: error processing SPE_0.8.2.a-wx2.6.1.0-py2.4.deb (--install):
 trying to overwrite `/usr/bin/spe', which is also in package spe
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 SPE_0.8.2.a-wx2.6.1.0-py2.4.deb

```

Please help

Thanks

[QUOTE=Se7h]Good afternoon stani and rich.

Rich, I expect the deb package to be ready today.
It's just the time to make some tests on the package and post the file on berlios:cool: 

Cumps[/QUOTE]

---

### Post by Se7h on 2006-01-31
[QUOTE=krypto_wizard]How to use this new version of Stani ? 

Is there a Ubuntu Build. I downloaded the .deb f```

```ile and tried to install using 

```
dpkg -i FileName.deb
```

```

and I got the following error
(Reading database ... 143454 files and directories currently installed.)
Unpacking python2.4-spe (from SPE_0.8.2.a-wx2.6.1.0-py2.4.deb) ...
dpkg: error processing SPE_0.8.2.a-wx2.6.1.0-py2.4.deb (--install):
 trying to overwrite `/usr/bin/spe', which is also in package spe
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 SPE_0.8.2.a-wx2.6.1.0-py2.4.deb

```

Please help

Thanks[/QUOTE]

Krypto, I don't know where Stani warned about that, but you have to remove that older version of SPE.
That older 'spe' was replaced with 'python2.X-spe', so for you to get the recent version on the roll, please do this:

dpkg -r spe
dpkg -i SPE_0.8.2.a-wx2.6.1.0-py2.4.deb

It'll all be already hopefully.

---

### Post by UbuWu on 2006-01-31
Looks like my bugreport stating that SPE was an old version was fixed just a few days too soon (it's 0.8.1.d now in dapper) :rolleyes:

---

### Post by Se7h on 2006-01-31
[QUOTE=UbuWu]Looks like my bugreport stating that SPE was an old version was fixed just a few days too soon (it's 0.8.1.d now in dapper) :rolleyes:[/QUOTE]

Oh thats good, lets just hope they used this already package thats been destributed (python2.3-spe and python2.4.spe)

Dapper is comin for ya :twisted:

---

### Post by kuerbt on 2006-06-07
which deb package should I install ?

apt-cache search spe | grep -i 'spe_' 

and I find nothing.

---

### Post by stani on 2006-06-07
You can download it here:
[http://prdownload.berlios.de/python/spe_0.8.2a-0ubuntu2_all.deb](http://prdownload.berlios.de/python/spe_0.8.2a-0ubuntu2_all.deb)

---

