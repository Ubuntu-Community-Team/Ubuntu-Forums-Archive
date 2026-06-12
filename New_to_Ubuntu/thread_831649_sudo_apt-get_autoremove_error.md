---
title: "sudo apt-get autoremove error"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by AnLGP on 2008-06-17
This is the start of the output error.  It's kinda long.  When I try and remove packages in synaptic it does an error as well.  I can post that in another thread.

steve@debian:~$ sudo apt-get autoremove

------------------------------- Easy_e17.sh 1.1.7.1 ---------------------------
--
  Developers:      Brian 'morlenxus' Miculcy
                   David 'onefang' Seikel
  Contributors:    Tim 'amon' Zebulla
                   Daniel G. '_ke' Siegel
                   Stefan 'slax' Langner
                   Massimiliano 'Massi' Calamelli
                   Thomas 'thomasg' Gstaedtner
                   Roberto 'rex' Sigalotti

----------------------------- Current Configuration ---------------------------
  Install path:    /opt/e17
  CVS path:        /root/.e17_cvs
  CVS server:      :pserver:anonymous@anoncvs.enlightenment.org:/var/cvs/e
  Logs path:       /tmp/easy_e17/install_logs


  Script action:   update
-------------------------------------------------------------------------------

-------------------------------- Build phase 1/3 ------------------------------
- running some basic system checks
- pre cleaning
- cvs checkout/update
-------------------------------------------------------------------------------


------------------------------- Basic system checks ---------------------------
- cvs-dir .................... ok
- creating script dirs ....... ok
- 'cvs' available ............ ok
- 'gcc' available ............ ok
- 'make' available ........... ok
- build-user ................. root
- adding path to env ......... ok
- checking lib-path in ldc ... ok (/etc/ld.so.conf.d/e17.conf)
- setting compile options .... ok
-------------------------------------------------------------------------------

------------------------------- CVS checkout/update ---------------------------
- updating source of repo 'e17/apps' (please wait, this won't output much) ...
? e/enlightenment.pc
M e/po/bg.po
M e/po/ca.po
M e/po/de.po
M e/po/eo.po
M e/po/es.po
M e/po/fi.po
M e/po/fr.po
M e/po/fr_CH.po
M e/po/hu.po
M e/po/it.po
M e/po/ja.po
M e/po/ko.po

---

and I'm not actually sure if it removes anything or not.

---

### Post by Ripfox on 2008-06-17
Did you try to look for broken packages in Synaptic? There is a option called "fix broken packages" under "edit" in Synaptics toolbar. Try that first, it may work...

---

### Post by AnLGP on 2008-06-17
more errors.

cat: /etc/environment: No such file or directory
sed: can't read /etc/environment: No such file or directory
dpkg: error processing e17-cvs (--configure):
 subprocess post-installation script returned error exit status 2

W: GPG error: [http://cafelinux.org](http://cafelinux.org) tinwoodman Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5814BA8970484670
W: You may want to run apt-get update to correct these problems

That last one occured after I did apt-get update.

---

### Post by Ripfox on 2008-06-17
You are trying to install E-17 correct? I think you need to remove the repos you added and start over with a different tutorial. Sounds like the repo is outdated...

---

### Post by AnLGP on 2008-06-17
er how do I do that?  Is there a way I could just update them without removing them?

---

### Post by Ripfox on 2008-06-22
sudo gedit /etc/apt/sources.list

---

