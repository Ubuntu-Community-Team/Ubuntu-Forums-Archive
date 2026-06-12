---
title: "tex-common (2.10): Package operation failed"
date: 2014-06-30
forum: New to Ubuntu
---

### Post by bekirs on 2014-06-30
Hi all,

since quite a long time, I receive the following error whenever I make an update. I probably deleted by mistake from tex-common folder, which I couldn't replace. Anyone has a solution?

```
installArchives() failed: Preconfiguring packages ...Preconfiguring packages ...
Preconfiguring packages ...
Preconfiguring packages ...
(Reading database ... 
(Reading database ... 5%%
(Reading database ... 10%%
(Reading database ... 15%%
(Reading database ... 20%%
(Reading database ... 25%%
(Reading database ... 30%%
(Reading database ... 35%%
(Reading database ... 40%%
(Reading database ... 45%%
(Reading database ... 50%%
(Reading database ... 55%%
(Reading database ... 60%%
(Reading database ... 65%%
(Reading database ... 70%%
(Reading database ... 75%%
(Reading database ... 80%%
(Reading database ... 85%%
(Reading database ... 90%%
(Reading database ... 95%%
(Reading database ... 100%%
(Reading database ... 1055037 files and directories currently installed.)
Preparing to replace libssl1.0.0 1.0.1-4ubuntu5.15 (using .../libssl1.0.0_1.0.1-4ubuntu5.16_amd64.deb) ...
De-configuring libssl1.0.0:i386 ...
Unpacking replacement libssl1.0.0 ...
Preparing to replace libssl1.0.0:i386 1.0.1-4ubuntu5.15 (using .../libssl1.0.0_1.0.1-4ubuntu5.16_i386.deb) ...
Unpacking replacement libssl1.0.0:i386 ...
Setting up libssl1.0.0 (1.0.1-4ubuntu5.16) ...
Setting up libssl1.0.0:i386 (1.0.1-4ubuntu5.16) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 
(Reading database ... 5%%
(Reading database ... 10%%
(Reading database ... 15%%
(Reading database ... 20%%
(Reading database ... 25%%
(Reading database ... 30%%
(Reading database ... 35%%
(Reading database ... 40%%
(Reading database ... 45%%
(Reading database ... 50%%
(Reading database ... 55%%
(Reading database ... 60%%
(Reading database ... 65%%
(Reading database ... 70%%
(Reading database ... 75%%
(Reading database ... 80%%
(Reading database ... 85%%
(Reading database ... 90%%
(Reading database ... 95%%
(Reading database ... 100%%
(Reading database ... 1055037 files and directories currently installed.)
Preparing to replace libwbclient0 2:3.6.3-2ubuntu2.10 (using .../libwbclient0_2%%3a3.6.3-2ubuntu2.11_amd64.deb) ...
Unpacking replacement libwbclient0 ...
Preparing to replace libsmbclient 2:3.6.3-2ubuntu2.10 (using .../libsmbclient_2%%3a3.6.3-2ubuntu2.11_amd64.deb) ...
Unpacking replacement libsmbclient ...
Preparing to replace gpgv 1.4.11-3ubuntu2.5 (using .../gpgv_1.4.11-3ubuntu2.6_amd64.deb) ...
Unpacking replacement gpgv ...
Processing triggers for man-db ...
Setting up gpgv (1.4.11-3ubuntu2.6) ...
(Reading database ... 
(Reading database ... 5%%
(Reading database ... 10%%
(Reading database ... 15%%
(Reading database ... 20%%
(Reading database ... 25%%
(Reading database ... 30%%
(Reading database ... 35%%
(Reading database ... 40%%
(Reading database ... 45%%
(Reading database ... 50%%
(Reading database ... 55%%
(Reading database ... 60%%
(Reading database ... 65%%
(Reading database ... 70%%
(Reading database ... 75%%
(Reading database ... 80%%
(Reading database ... 85%%
(Reading database ... 90%%
(Reading database ... 95%%
(Reading database ... 100%%
(Reading database ... 1055037 files and directories currently installed.)
Preparing to replace gnupg 1.4.11-3ubuntu2.5 (using .../gnupg_1.4.11-3ubuntu2.6_amd64.deb) ...
Unpacking replacement gnupg ...
Processing triggers for man-db ...
Processing triggers for install-info ...
Setting up gnupg (1.4.11-3ubuntu2.6) ...
(Reading database ... 
(Reading database ... 5%%
(Reading database ... 10%%
(Reading database ... 15%%
(Reading database ... 20%%
(Reading database ... 25%%
(Reading database ... 30%%
(Reading database ... 35%%
(Reading database ... 40%%
(Reading database ... 45%%
(Reading database ... 50%%
(Reading database ... 55%%
(Reading database ... 60%%
(Reading database ... 65%%
(Reading database ... 70%%
(Reading database ... 75%%
(Reading database ... 80%%
(Reading database ... 85%%
(Reading database ... 90%%
(Reading database ... 95%%
(Reading database ... 100%%
(Reading database ... 1055037 files and directories currently installed.)
Preparing to replace openssl 1.0.1-4ubuntu5.15 (using .../openssl_1.0.1-4ubuntu5.16_amd64.deb) ...
Unpacking replacement openssl ...
Preparing to replace wget 1.13.4-2ubuntu1 (using .../wget_1.13.4-2ubuntu1.1_amd64.deb) ...
Unpacking replacement wget ...
Preparing to replace gnupg2 2.0.17-2ubuntu2.12.04.3 (using .../gnupg2_2.0.17-2ubuntu2.12.04.4_amd64.deb) ...
Unpacking replacement gnupg2 ...
Preparing to replace gnupg-agent 2.0.17-2ubuntu2.12.04.3 (using .../gnupg-agent_2.0.17-2ubuntu2.12.04.4_amd64.deb) ...
Unpacking replacement gnupg-agent ...
Preparing to replace linux-firmware 1.79.15 (using .../linux-firmware_1.79.16_all.deb) ...
Unpacking replacement linux-firmware ...
Preparing to replace smbclient 2:3.6.3-2ubuntu2.10 (using .../smbclient_2%%3a3.6.3-2ubuntu2.11_amd64.deb) ...
Unpacking replacement smbclient ...
Preparing to replace samba-common 2:3.6.3-2ubuntu2.10 (using .../samba-common_2%%3a3.6.3-2ubuntu2.11_all.deb) ...
Unpacking replacement samba-common ...
Preparing to replace samba-common-bin 2:3.6.3-2ubuntu2.10 (using .../samba-common-bin_2%%3a3.6.3-2ubuntu2.11_amd64.deb) ...
Unpacking replacement samba-common-bin ...
Processing triggers for man-db ...
Processing triggers for install-info ...
Setting up tex-common (2.10) ...
Not replacing deleted config file /etc/texmf/texmf.d/05TeXMF.cnf
Not replacing deleted config file /etc/texmf/texmf.d/15Plain.cnf
Not replacing deleted config file /etc/texmf/texmf.d/45TeXinputs.cnf
Not replacing deleted config file /etc/texmf/texmf.d/55Fonts.cnf
Not replacing deleted config file /etc/texmf/texmf.d/65BibTeX.cnf
Not replacing deleted config file /etc/texmf/texmf.d/75DviPS.cnf
Not replacing deleted config file /etc/texmf/texmf.d/80DVIPDFMx.cnf
Not replacing deleted config file /etc/texmf/texmf.d/85Misc.cnf
Not replacing deleted config file /etc/texmf/texmf.d/90TeXDoc.cnf
Not replacing deleted config file /etc/texmf/texmf.d/95NonPath.cnf
Not replacing deleted config file /etc/texmf/updmap.d/00updmap.cfg
update-texmf: Basic configuration file /etc/texmf/texmf.d/05TeXMF.cnf missing.
Exiting.
dpkg: error processing tex-common (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up libwbclient0 (2:3.6.3-2ubuntu2.11) ...
Setting up libsmbclient (2:3.6.3-2ubuntu2.11) ...
Setting up openssl (1.0.1-4ubuntu5.16) ...
Setting up wget (1.13.4-2ubuntu1.1) ...
Setting up gnupg-agent (2.0.17-2ubuntu2.12.04.4) ...
Setting up gnupg2 (2.0.17-2ubuntu2.12.04.4) ...
Setting up linux-firmware (1.79.16) ...
Setting up samba-common (2:3.6.3-2ubuntu2.11) ...
Setting up smbclient (2:3.6.3-2ubuntu2.11) ...
Setting up samba-common-bin (2:3.6.3-2ubuntu2.11) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 tex-common
Error in function: 
Setting up tex-common (2.10) ...
Not replacing deleted config file /etc/texmf/texmf.d/05TeXMF.cnf
Not replacing deleted config file /etc/texmf/texmf.d/15Plain.cnf
Not replacing deleted config file /etc/texmf/texmf.d/45TeXinputs.cnf
Not replacing deleted config file /etc/texmf/texmf.d/55Fonts.cnf
Not replacing deleted config file /etc/texmf/texmf.d/65BibTeX.cnf
Not replacing deleted config file /etc/texmf/texmf.d/75DviPS.cnf
Not replacing deleted config file /etc/texmf/texmf.d/80DVIPDFMx.cnf
Not replacing deleted config file /etc/texmf/texmf.d/85Misc.cnf
Not replacing deleted config file /etc/texmf/texmf.d/90TeXDoc.cnf
Not replacing deleted config file /etc/texmf/texmf.d/95NonPath.cnf
Not replacing deleted config file /etc/texmf/updmap.d/00updmap.cfg
update-texmf: Basic configuration file /etc/texmf/texmf.d/05TeXMF.cnf missing.
Exiting.
dpkg: error processing tex-common (--configure):
 subprocess installed post-installation script returned error exit status 1
```

---

### Post by Bashing-om on 2014-06-30
bekirs; Hi !

Try this and see what results:
```

sudo apt-get install --reinstall tex-common

```
If it fails to install, perhaps the package manager will give some hints of the nature of the problem.

[INDENT][INDENT]maybe yes,
[INDENT][INDENT][INDENT]maybe, not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by bekirs on 2014-06-30
Hi,

here is the output:

```
sudo apt-get install --reinstall tex-commonReading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up tex-common (2.10) ...
Not replacing deleted config file /etc/texmf/texmf.d/05TeXMF.cnf
Not replacing deleted config file /etc/texmf/texmf.d/15Plain.cnf
Not replacing deleted config file /etc/texmf/texmf.d/45TeXinputs.cnf
Not replacing deleted config file /etc/texmf/texmf.d/55Fonts.cnf
Not replacing deleted config file /etc/texmf/texmf.d/65BibTeX.cnf
Not replacing deleted config file /etc/texmf/texmf.d/75DviPS.cnf
Not replacing deleted config file /etc/texmf/texmf.d/80DVIPDFMx.cnf
Not replacing deleted config file /etc/texmf/texmf.d/85Misc.cnf
Not replacing deleted config file /etc/texmf/texmf.d/90TeXDoc.cnf
Not replacing deleted config file /etc/texmf/texmf.d/95NonPath.cnf
Not replacing deleted config file /etc/texmf/updmap.d/00updmap.cfg
update-texmf: Basic configuration file /etc/texmf/texmf.d/05TeXMF.cnf missing.
Exiting.
dpkg: error processing tex-common (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 tex-common
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

> **Bashing-om said:**
> bekirs; Hi !

Try this and see what results:
```

sudo apt-get install --reinstall tex-common

```
If it fails to install, perhaps the package manager will give some hints of the nature of the problem.
[INDENT][INDENT]maybe yes,[INDENT][INDENT][INDENT]maybe, not so yes
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


---

### Post by Bashing-om on 2014-06-30
bekirs; Humm:
> 
update-texmf: Basic configuration file /etc/texmf/texmf.d/05TeXMF.cnf [color=red]missing[/color].
Exiting.


See if the application can be removed, and then (RE-)install ?
```

sudo apt-get remove tex-common
sudo apt-get install tex-common

```

[INDENT][INDENT]maybe now yes
[/INDENT][/INDENT]

---

### Post by bekirs on 2014-07-01
here is the first output:

```
sudo apt-get remove tex-commonReading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  tex-common
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 1,589 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 1055031 files and directories currently installed.)
Removing tex-common ...
Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 2 removed doc-base files...
Registering documents with scrollkeeper...

```

...and the second:

```
sudo apt-get install tex-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  debhelper
The following NEW packages will be installed:
  tex-common
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 709 kB of archives.
After this operation, 1,589 kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu/ precise/main tex-common all 2.10 [709 kB]
Fetched 709 kB in 2s (297 kB/s)     
Preconfiguring packages ...
Selecting previously unselected package tex-common.
(Reading database ... 1054917 files and directories currently installed.)
Unpacking tex-common (from .../tex-common_2.10_all.deb) ...
Processing triggers for doc-base ...
Processing 2 added doc-base files...
Registering documents with scrollkeeper...
Processing triggers for man-db ...
Setting up tex-common (2.10) ...
Not replacing deleted config file /etc/texmf/texmf.d/05TeXMF.cnf
Not replacing deleted config file /etc/texmf/texmf.d/15Plain.cnf
Not replacing deleted config file /etc/texmf/texmf.d/45TeXinputs.cnf
Not replacing deleted config file /etc/texmf/texmf.d/55Fonts.cnf
Not replacing deleted config file /etc/texmf/texmf.d/65BibTeX.cnf
Not replacing deleted config file /etc/texmf/texmf.d/75DviPS.cnf
Not replacing deleted config file /etc/texmf/texmf.d/80DVIPDFMx.cnf
Not replacing deleted config file /etc/texmf/texmf.d/85Misc.cnf
Not replacing deleted config file /etc/texmf/texmf.d/90TeXDoc.cnf
Not replacing deleted config file /etc/texmf/texmf.d/95NonPath.cnf
Not replacing deleted config file /etc/texmf/updmap.d/00updmap.cfg
update-texmf: Basic configuration file /etc/texmf/texmf.d/05TeXMF.cnf missing.
Exiting.
dpkg: error processing tex-common (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 tex-common
E: Sub-process /usr/bin/dpkg returned an error code (1)



```


> **Bashing-om said:**
> bekirs; Humm:


See if the application can be removed, and then (RE-)install ?
```

sudo apt-get remove tex-common
sudo apt-get install tex-common

```
[INDENT][INDENT]maybe now yes
[/INDENT]
[/INDENT]


---

### Post by Bashing-om on 2014-07-01
bekirs; Yuk,

Appears then that " /etc/texmf/texmf.d/05TeXMF.cnf " is not a part of 'tex-common'. Let's see if we can find what package contains that file !
```

dpkg -S /etc/texmf/texmf.d/05TeXMF.cnf

```

Might prove relative in this case.
Find the correct package and
[INDENT][INDENT]get it installed
[/INDENT][/INDENT]

---

### Post by steeldriver on 2014-07-01
I notice that **/usr/share/tex-common/**05TeXMF.cnf appears to have been part of tex-common up to and including 12.04 though

[http://packages.ubuntu.com/precise/all/tex-common/filelist](http://packages.ubuntu.com/precise/all/tex-common/filelist)

and without delving into the postinst script closely my guess is that it  copies the file(s) to /etc/texmf/texmf.d as a post install step.

OP, what version of Ubuntu are you running please? Do you have those .cnf files in /usr/share/tex-common? if so you may be able to manually re-copy them to the correct location and hopefully make dpkg happy again

---

### Post by sandyd on 2014-07-01
Those files are not managed by ubuntu, they are managed by UCF.

1. Find the latest tex-common file you have
```

ls -l /var/cache/apt/archives/tex-common*
```
Choose the newest one.

2. Force UCE to regen it
```

UCF_FORCE_CONFFMISS=yes dpkg -i --force-confmiss /var/cache/apt/archives/_name_here
```
where _name_here is the name of the deb file.

---

### Post by bekirs on 2014-07-01
```
dpkg -S /etc/texmf/texmf.d/05TeXMF.cnf
dpkg-query: no path found matching pattern /etc/texmf/texmf.d/05TeXMF.cnf.
```

> **Bashing-om said:**
> bekirs; Yuk,

Appears then that " /etc/texmf/texmf.d/05TeXMF.cnf " is not a part of 'tex-common'. Let's see if we can find what package contains that file !
```

dpkg -S /etc/texmf/texmf.d/05TeXMF.cnf

```

Might prove relative in this case.
Find the correct package and[INDENT][INDENT]get it installed
[/INDENT]
[/INDENT]


---

### Post by bekirs on 2014-07-01
1.
```
ls -l /var/cache/apt/archives/tex-common
ls: cannot access /var/cache/apt/archives/tex-common: No such file or directory
```


> **sandyd said:**
> Those files are not managed by ubuntu, they are managed by UCF.

1. Find the latest tex-common file you have
```

ls -l /var/cache/apt/archives/tex-common
```
Choose the newest one.

2. Force UCE to regen it
```

UCF_FORCE_CONFFMISS=yes dpkg -i --force-confmiss /var/cache/apt/archives/_name_here
```
where _name_here is the name of the deb file.

---

### Post by sandyd on 2014-07-02
> **bekirs said:**
> 1.
```
ls -l /var/cache/apt/archives/tex-common
ls: cannot access /var/cache/apt/archives/tex-common: No such file or directory
```

typo - fixed :oops:

---

### Post by bekirs on 2014-07-02
1st step

```
ls -l /var/cache/apt/archives/tex-common*
-rw-r--r-- 1 root root 709050 Jun 27  2011 /var/cache/apt/archives/tex-common_2.10_all.deb

```

2nd step

```

UCF_FORCE_CONFFMISS=yes dpkg -i --force-confmiss /var/cache/apt/archives/tex-common_2.10_all.deb
dpkg: error: requested operation requires superuser privilege

```

3rd step

```

UCF_FORCE_CONFFMISS=yes dpkg -i --force-confmiss /var/cache/apt/archives/tex-common_2.10_all.deb
(Reading database ... 1055032 files and directories currently installed.)
Preparing to replace tex-common 2.10 (using .../tex-common_2.10_all.deb) ...
Unpacking replacement tex-common ...
Setting up tex-common (2.10) ...


Recreating deleted config file /etc/texmf/texmf.d/05TeXMF.cnf with new version, as asked


Recreating deleted config file /etc/texmf/texmf.d/15Plain.cnf with new version, as asked


Recreating deleted config file /etc/texmf/texmf.d/45TeXinputs.cnf with new version, as asked


Recreating deleted config file /etc/texmf/texmf.d/55Fonts.cnf with new version, as asked


Recreating deleted config file /etc/texmf/texmf.d/65BibTeX.cnf with new version, as asked


Recreating deleted config file /etc/texmf/texmf.d/75DviPS.cnf with new version, as asked


Recreating deleted config file /etc/texmf/texmf.d/80DVIPDFMx.cnf with new version, as asked


Recreating deleted config file /etc/texmf/texmf.d/85Misc.cnf with new version, as asked


Recreating deleted config file /etc/texmf/texmf.d/90TeXDoc.cnf with new version, as asked


Recreating deleted config file /etc/texmf/texmf.d/95NonPath.cnf with new version, as asked


Recreating deleted config file /etc/texmf/updmap.d/00updmap.cfg with new version, as asked


Recreating deleted config file /etc/texmf/texmf.cnf with new version, as asked
Processing triggers for doc-base ...
Processing 2 changed doc-base files...
Registering documents with scrollkeeper...
Processing triggers for man-db ...

```

> **sandyd said:**
> typo - fixed :oops:

---

### Post by sandyd on 2014-07-02
Is it all working now?

---

### Post by bekirs on 2014-07-06
I think it works now. At least no error message appear after I run sudo apt-get update...

Thanks for great support!

---

