---
title: "[SOLVED] Open Office Writer Problem To Install"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by luckylucky on 2008-08-22
I did a fresh install of Ubuntu 8.04.1 which has OOo 2.4.1.  As usual, one of the first things I do in a fresh install is I install the dictionaries (US English) in Open Office Writer using the standard wizard (file > wizard > install new dictionaries) so I know what to typically expect (I've done it dozenS of times) but this time the window that pops up is too small and it can't be resized. I am unable to complete the process because I can't see what I am doing.

Is there another way to install the dictionaries (including thesaurus, etc...) other than the standard wizard way?

Is there a way for me to uninstall OOo 2.4.1 and somehow revert to an older version that might perhaps work?

Is there another option to make this work that perhaps I haven't considered?

---

### Post by Elfy on 2008-08-22
First - have you got all the updates installed, I do remember this being a problem when hardy first released, or it might even have been 7.10. But I've just had a look on mine and the windows are ok there. I'm not sure of another way to installe them - but there are some threads here on it.

Second you can uninstall all the ubuntu openoffice and install the openoffice version - [http://download.openoffice.org/](http://download.openoffice.org/)

it should be debs once it's been extracted - this should help install it
[http://ubuntuforums.org/showpost.php?p=5616155&postcount=2](http://ubuntuforums.org/showpost.php?p=5616155&postcount=2)

---

### Post by luckylucky on 2008-08-22
> **forestpixie said:**
> First - have you got all the updates installed, I do remember this being a problem when hardy first released, or it might even have been 7.10. But I've just had a look on mine and the windows are ok there. I'm not sure of another way to installe them - but there are some threads here on it.

Second you can uninstall all the ubuntu openoffice and install the openoffice version - [http://download.openoffice.org/](http://download.openoffice.org/)

it should be debs once it's been extracted - this should help install it
[http://ubuntuforums.org/showpost.php?p=5616155&postcount=2](http://ubuntuforums.org/showpost.php?p=5616155&postcount=2)


Yes, the system is full "updated".  Just checked to be sure.  Tried again in OO, and same problem.  I guess I shall now try uninstalling OO then downloading direct from OO.

---

### Post by Elfy on 2008-08-22
Found a couple of bugs - try turning compiz off if it is on

[https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/222376](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/222376)

[https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/222902](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/222902)

---

### Post by luckylucky on 2008-08-23
re-installed OO and turned off compiz.  Worked to install dics.  I later tried with compiz on but it still worked.

Issue resolved - my solution = reinstalled full package of OO office & tried again.

---

