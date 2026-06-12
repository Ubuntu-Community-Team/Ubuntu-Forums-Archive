---
title: "why does purging Abiword refer me to LibreOffice packages?"
date: 2016-01-27
forum: New to Ubuntu
---

### Post by anotherChris on 2016-01-27
I purged Abiword, and I have a purely academic question about it...

When I purged, it told me about some packages related to LibreOffice that I might want to remove.  Why?

```
anotherChris@anotherPC:~$ sudo apt-get purge Abiword
[sudo] password for anotherChris: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  hyphen-en-us liblink-grammar4 libreoffice-help-en-gb libreoffice-help-en-us
  libreoffice-help-ja libreoffice-l10n-en-gb libreoffice-l10n-en-za
  libreoffice-l10n-ja link-grammar-dictionaries-en mythes-en-au mythes-en-us
  openoffice.org-hyphenation
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  abiword* abiword-plugin-grammar*
0 upgraded, 0 newly installed, 2 to remove and 1 not upgraded.
After this operation, 5,110 kB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 158520 files and directories currently installed.)
Removing abiword-plugin-grammar (3.0.1-4build2) ...
Removing abiword (3.0.1-4build2) ...
Purging configuration files for abiword (3.0.1-4build2) ...
Processing triggers for mime-support (3.58ubuntu1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu3) ...
Processing triggers for man-db (2.7.4-1) ...
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
anotherChris@anotherPC:~$ 

```

---

### Post by ian-weisser on 2016-01-27
The system is warning you about already-orphaned packages that are safe to autoremove, regardless of what you are doing with Abiword,
There is no causal relationship between AbiWord and those packages. That's a coincidence.

---

### Post by vasa1 on 2016-01-27
> **ian-weisser said:**
> The system is warning you about already-orphaned packages that are safe to autoremove, regardless of what you are doing with Abiword,
There is no causal relationship between AbiWord and those packages. That's a coincidence.
+1. Probably because of something else you've done and forgot to mention?

But one way to check would be to run **sudo apt-get autoremove** all by itself and see what the system suggests. You needn't proceed with the autoremove if you have doubts; just press `n` to exit.

---

### Post by anotherChris on 2016-01-28
Thanks.  I tried sudo apt-get autoremove as you suggested, and it told me about the same files.

Just before purging Abiword, I had installed LibreOffice.  I don't know why it would be recommending removing those files, but I decided to say no.

SOLVED!

---

