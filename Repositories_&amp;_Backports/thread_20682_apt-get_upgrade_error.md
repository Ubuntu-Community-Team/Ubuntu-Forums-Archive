---
title: "apt-get upgrade error"
date: 2005-03-17
forum: Repositories &amp; Backports
---

### Post by i3dmaster on 2005-03-17
I did apt-get upgrade today and it has an error like this:

Setting up fontconfig (2.2.3-4ubuntu5) ...
dpkg: error processing fontconfig (--configure):
 subprocess post-installation script returned error exit status 10
Errors were encountered while processing:
 fontconfig
E: Sub-process /usr/bin/dpkg returned an error code (1)

dpkg -l fontconfig shows:

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                      Version                   Description
+++-=========================-=========================-==================================================================
iF  fontconfig                2.2.3-4ubuntu5            generic font configuration library


What should I do about this fontconfig package? Thanks for help

---

### Post by rolo on 2005-03-17
remove the troubling package and the reinstall (just that package.)

Hope it may help.

---

### Post by telmo on 2005-03-18
nop!
Try this... [http://ubuntuforums.org/showthread.php?t=20659](http://ubuntuforums.org/showthread.php?t=20659)

I bet next time your gonna seach for it!  \\:D/

---

### Post by bored2k on 2005-03-18
[QUOTE=telmo]nop!
Try this... [http://ubuntuforums.org/showthread.php?t=20659](http://ubuntuforums.org/showthread.php?t=20659)

I bet next time your gonna seach for it!  \\:D/[/QUOTE]
 The website could use a 22 bold sized sparkling search button :roll: .

---

