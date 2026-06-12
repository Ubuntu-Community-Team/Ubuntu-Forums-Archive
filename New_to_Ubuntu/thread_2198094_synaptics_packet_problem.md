---
title: "synaptics packet problem"
date: 2014-01-06
forum: New to Ubuntu
---

### Post by Vagelism_Meintasis on 2014-01-06
Hello to all, I get this error on upgrade my ubuntu:

```
sudo apt-get upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-image-generic-lts-quantal : Depends: linux-image-3.5.0-44-generic but it is not installed
E: Unmet dependencies. Try using -f.


```

Any one can help?
Thank you.

---

### Post by claracc on 2014-01-07
Have you tried to run the advised command?, in a xterm:

```
sudo apt-get -f install
```

Your paassword will be required, you enter it and see if problem is fixed

---

### Post by Bucky Ball on 2014-01-07
You must update first.

Try this:

```
sudo apt-get update
sudo apt-get upgrade
```

If still errors, try claracc's command.

ALWAYS run the update command before upgrade. ;)

---

### Post by Vagelism_Meintasis on 2014-01-07
Yes this dont work...

---

### Post by Vagelism_Meintasis on 2014-01-07
This is the output of the command.

```
diaxeiristis@diaxeiristis-ThinkPad-X31:~$ LC_ALL=C bash
diaxeiristis@diaxeiristis-ThinkPad-X31:~$ sudo apt-get -f install            
[sudo] password for diaxeiristis: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  thunderbird-globalmenu gir1.2-ubuntuoneui-3.0 libavahi-ui-gtk3-0
  guile-1.8-libs firefox-globalmenu libgdu-gtk0 libubuntuoneui-3.0-1
  librhythmbox-core5 libmusicbrainz3-6
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-image-3.5.0-45-generic linux-image-generic-lts-quantal
Suggested packages:
  fdutils linux-lts-quantal-doc-3.5.0 linux-lts-quantal-source-3.5.0
  linux-lts-quantal-tools linux-headers-3.5.0-45-generic
The following NEW packages will be installed:
  linux-image-3.5.0-45-generic
The following packages will be upgraded:
  linux-image-generic-lts-quantal
1 upgraded, 1 newly installed, 0 to remove and 44 not upgraded.
3 not fully installed or removed.
Need to get 0 B/40.3 MB of archives.
After this operation, 119 MB of additional disk space will be used.
Do you want to continue [Y/n]? yes
(Reading database ... 178525 files and directories currently installed.)
Unpacking linux-image-3.5.0-45-generic (from .../linux-image-3.5.0-45-generic_3.5.0-45.68~precise1_i386.deb) ...
This kernel does not support a non-PAE CPU.
dpkg: error processing /var/cache/apt/archives/linux-image-3.5.0-45-generic_3.5.0-45.68~precise1_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-45-generic /boot/vmlinuz-3.5.0-45-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-45-generic /boot/vmlinuz-3.5.0-45-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.5.0-45-generic_3.5.0-45.68~precise1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by Bucky Ball on 2014-01-07
This looks like your problem:

```
This kernel does not support a non-PAE CPU.
```

I know nothing of PAE and non-PAE kernels and/or CPUs, unfortunately. You might need to research it. Just put that bit of code in a search engine followed by 'ubuntu' and see what comes up.

---

### Post by mörgæs on 2014-01-07
Here's a guide about non-PAE solutions / workarounds:
[https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)

---

### Post by sudodus on 2014-01-07
... or go directly to [https://help.ubuntu.com/community/Lubuntu-fake-PAE](https://help.ubuntu.com/community/Lubuntu-fake-PAE)

What computer is it? Please specify the brand name, model, CPU and RAM (size) and you can get more relevant advice. See also the following link
[URL="http://ubuntuforums.org/showthread.php?t=2130640"]
Old hardware brought back to life[/URL]

---

