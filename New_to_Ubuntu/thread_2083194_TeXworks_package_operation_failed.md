---
title: "TeXworks: package operation failed"
date: 2012-11-11
forum: New to Ubuntu
---

### Post by bekirs on 2012-11-11
Hi,

I receive the following message when I try to install TeXworks from the repository:

"Package operation failed
The installation or removal of a software package failed."

and the details are the following:

```

installArchives() failed: Preconfiguring packages ...
Preconfiguring packages ...
Preconfiguring packages ...
Selecting previously unselected package tex-common.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 315556 files and directories currently installed.)
Unpacking tex-common (from .../tex-common_2.10_all.deb) ...
Selecting previously unselected package lmodern.
Unpacking lmodern (from .../lmodern_2.004.1-3.1ubuntu1_all.deb) ...
Selecting previously unselected package texlive-common.
Unpacking texlive-common (from .../texlive-common_2009-15_all.deb) ...
Selecting previously unselected package texlive-doc-base.
Unpacking texlive-doc-base (from .../texlive-doc-base_2009-2_all.deb) ...
Selecting previously unselected package texlive-binaries.
Unpacking texlive-binaries (from .../texlive-binaries_2009-11ubuntu2_amd64.deb) ...
Selecting previously unselected package texlive-base.
Unpacking texlive-base (from .../texlive-base_2009-15_all.deb) ...
Selecting previously unselected package texlive-latex-base.
Unpacking texlive-latex-base (from .../texlive-latex-base_2009-15_all.deb) ...
Selecting previously unselected package texlive-latex-base-doc.
Unpacking texlive-latex-base-doc (from .../texlive-latex-base-doc_2009-15_all.deb) ...
Selecting previously unselected package texworks.
Unpacking texworks (from .../texworks_0.5~svn952-1_amd64.deb) ...
Selecting previously unselected package texworks-help-en.
Unpacking texworks-help-en (from .../texworks-help-en_0.5~svn952-1_all.deb) ...
Processing triggers for doc-base ...
Processing 2 added doc-base files...
Registering documents with scrollkeeper...
Processing triggers for man-db ...
Processing triggers for fontconfig ...
Processing triggers for install-info ...
Processing triggers for desktop-file-utils ...
Setting up tex-common (2.10) ...

Creating config file /etc/texmf/texmf.d/05TeXMF.cnf with new version

Creating config file /etc/texmf/texmf.d/15Plain.cnf with new version

Creating config file /etc/texmf/texmf.d/45TeXinputs.cnf with new version

Creating config file /etc/texmf/texmf.d/55Fonts.cnf with new version

Creating config file /etc/texmf/texmf.d/65BibTeX.cnf with new version

Creating config file /etc/texmf/texmf.d/75DviPS.cnf with new version

Creating config file /etc/texmf/texmf.d/80DVIPDFMx.cnf with new version

Creating config file /etc/texmf/texmf.d/85Misc.cnf with new version

Creating config file /etc/texmf/texmf.d/90TeXDoc.cnf with new version

Creating config file /etc/texmf/texmf.d/95NonPath.cnf with new version

Creating config file /etc/texmf/updmap.d/00updmap.cfg with new version

Creating config file /etc/texmf/texmf.cnf with new version
Running mktexlsr. This may take some time... done.
texlive-base is not ready, delaying updmap-sys call
texlive-base is not ready, skipping fmtutil-sys --all call
Setting up lmodern (2.004.1-3.1ubuntu1) ...
Setting up texlive-common (2009-15) ...
Setting up texlive-doc-base (2009-2) ...
Setting up texlive-binaries (2009-11ubuntu2) ...
update-alternatives: using /usr/bin/xdvi-xaw to provide /usr/bin/xdvi.bin (xdvi.bin) in auto mode.
update-alternatives: using /usr/bin/bibtex.original to provide /usr/bin/bibtex (bibtex) in auto mode.
mktexlsr: Updating /var/lib/texmf/ls-R-TEXMFMAIN... 
mktexlsr: Updating /var/lib/texmf/ls-R-TEXLIVE... 
mktexlsr: Updating /var/lib/texmf/ls-R... 
mktexlsr: Done.
Building format(s) --refresh.
	This may take some time... done.
Setting up texlive-latex-base-doc (2009-15) ...
Setting up texworks (0.5~svn952-1) ...
Setting up texworks-help-en (0.5~svn952-1) ...
Processing triggers for tex-common ...
Running mktexlsr. This may take some time... done.
texlive-base is not ready, delaying updmap-sys call
Setting up texlive-base (2009-15) ...
mktexlsr: Updating /var/lib/texmf/ls-R-TEXLIVE... 
mktexlsr: Updating /var/lib/texmf/ls-R-TEXMFMAIN... 
mktexlsr: Updating /var/lib/texmf/ls-R... 
mktexlsr: Done.
Not replacing deleted config file /etc/texmf/dvips/config/config.ps
Not replacing deleted config file /etc/texmf/tex/generic/config/pdftexconfig.tex
Not replacing deleted config file /etc/texmf/dvipdfmx/dvipdfmx.cfg
Not replacing deleted config file /etc/texmf/xdvi/XDvi
dpkg: error processing texlive-base (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of texlive-latex-base:
 texlive-latex-base depends on texlive-base (>= 2009-1); however:
  Package texlive-base is not configured yet.
dpkg: error processing texlive-latex-base (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
Errors were encountered while processing:
 texlive-base
 texlive-latex-base
Error in function: 
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1)
Setting up texlive-base (2009-15) ...
mktexlsr: Updating /var/lib/texmf/ls-R-TEXLIVE... 
mktexlsr: Updating /var/lib/texmf/ls-R-TEXMFMAIN... 
mktexlsr: Updating /var/lib/texmf/ls-R... 
mktexlsr: Done.
Not replacing deleted config file /etc/texmf/dvips/config/config.ps
Not replacing deleted config file /etc/texmf/tex/generic/config/pdftexconfig.tex
Not replacing deleted config file /etc/texmf/dvipdfmx/dvipdfmx.cfg
Not replacing deleted config file /etc/texmf/xdvi/XDvi
dpkg: error processing texlive-base (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of texlive-latex-base:
 texlive-latex-base depends on texlive-base (>= 2009-1); however:
  Package texlive-base is not configured yet.
dpkg: error processing texlive-latex-base (--configure):
 dependency problems - leaving unconfigured

```

Would be great if someone can help...

---

### Post by Bashing-om on 2012-11-12
bekirs; Hi !

Seems a config file to set up the configs is messed up for some reason. Not sure if this will work but worth a try to see if apt-get is able to pull in the config file.
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get -f install
dpkg --configure -a

```Post back with any errors generated; may consider removal/re-install of the package.
[INDENT]just try'n to help < == BDQ

[/INDENT]

---

### Post by bekirs on 2012-11-12
> **Bashing-om said:**
> bekirs; Hi !

Seems a config file to set up the configs is messed up for some reason. Not sure if this will work but worth a try to see if apt-get is able to pull in the config file.
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get -f install
dpkg --configure -a

```Post back with any errors generated; may consider removal/re-install of the package.
[INDENT]just try'n to help < == BDQ

[/INDENT]

Hi,

thank you for the help. I paste the output:

```

sudo apt-get update
[sudo] password for bekirsalgin: 
Ign http://extras.ubuntu.com precise InRelease
Ign http://security.ubuntu.com precise-security InRelease                      
Ign http://archive.canonical.com precise InRelease                             
Ign http://dl.google.com stable InRelease                                      
Get:1 http://security.ubuntu.com precise-security Release.gpg [198 B]          
Get:2 http://extras.ubuntu.com precise Release.gpg [72 B]                      
Hit http://archive.canonical.com precise Release.gpg                           
Hit http://dl.google.com stable Release.gpg                                    
Get:3 http://security.ubuntu.com precise-security Release [49.6 kB]            
Get:4 http://extras.ubuntu.com precise Release [11.9 kB]                       
Hit http://archive.canonical.com precise Release                               
Hit http://dl.google.com stable Release                                        
Hit http://archive.canonical.com precise/partner amd64 Packages                
Hit http://archive.canonical.com precise/partner i386 Packages                 
Ign http://archive.canonical.com precise/partner TranslationIndex              
Hit http://dl.google.com stable/main amd64 Packages                            
Get:5 http://security.ubuntu.com precise-security/restricted Sources [1,950 B] 
Get:6 http://extras.ubuntu.com precise/main amd64 Packages [9,815 B]           
Hit http://dl.google.com stable/main i386 Packages                             
Ign http://dl.google.com stable/main TranslationIndex                          
Get:7 http://security.ubuntu.com precise-security/main Sources [54.6 kB]       
Get:8 http://extras.ubuntu.com precise/main i386 Packages [9,829 B]            
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Get:9 http://security.ubuntu.com precise-security/multiverse Sources [1,392 B] 
Get:10 http://security.ubuntu.com precise-security/universe Sources [15.8 kB]  
Get:11 http://security.ubuntu.com precise-security/main amd64 Packages [196 kB]
Get:12 http://security.ubuntu.com precise-security/restricted amd64 Packages [3,969 B]
Get:13 http://security.ubuntu.com precise-security/universe amd64 Packages [54.7 kB]
Get:14 http://security.ubuntu.com precise-security/multiverse amd64 Packages [2,189 B]
Get:15 http://security.ubuntu.com precise-security/main i386 Packages [201 kB] 
Ign http://archive.canonical.com precise/partner Translation-en_US             
Ign http://archive.canonical.com precise/partner Translation-en                
Get:16 http://security.ubuntu.com precise-security/restricted i386 Packages [3,968 B]
Get:17 http://security.ubuntu.com precise-security/universe i386 Packages [54.9 kB]
Get:18 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,388 B]
Ign http://dl.google.com stable/main Translation-en_US                         
Get:19 http://security.ubuntu.com precise-security/main TranslationIndex [73 B]
Get:20 http://security.ubuntu.com precise-security/multiverse TranslationIndex [71 B]
Get:21 http://security.ubuntu.com precise-security/restricted TranslationIndex [71 B]
Get:22 http://security.ubuntu.com precise-security/universe TranslationIndex [73 B]
Ign http://extras.ubuntu.com precise/main Translation-en_US                    
Get:23 http://security.ubuntu.com precise-security/main Translation-en [96.7 kB]
Ign http://dl.google.com stable/main Translation-en                            
Ign http://extras.ubuntu.com precise/main Translation-en                       
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Get:24 http://security.ubuntu.com precise-security/universe Translation-en [33.2 kB]
Ign http://de.archive.ubuntu.com precise InRelease                             
Ign http://de.archive.ubuntu.com precise-updates InRelease
Ign http://de.archive.ubuntu.com precise-proposed InRelease
Hit http://de.archive.ubuntu.com precise Release.gpg
Get:25 http://de.archive.ubuntu.com precise-updates Release.gpg [198 B]
Get:26 http://de.archive.ubuntu.com precise-proposed Release.gpg [198 B]
Hit http://de.archive.ubuntu.com precise Release
Get:27 http://de.archive.ubuntu.com precise-updates Release [49.6 kB]
Get:28 http://de.archive.ubuntu.com precise-proposed Release [49.6 kB]
Hit http://de.archive.ubuntu.com precise/restricted Sources  
Hit http://de.archive.ubuntu.com precise/main Sources
Hit http://de.archive.ubuntu.com precise/multiverse Sources
Hit http://de.archive.ubuntu.com precise/universe Sources
Hit http://de.archive.ubuntu.com precise/main amd64 Packages
Hit http://de.archive.ubuntu.com precise/restricted amd64 Packages
Hit http://de.archive.ubuntu.com precise/universe amd64 Packages
Hit http://de.archive.ubuntu.com precise/multiverse amd64 Packages
Hit http://de.archive.ubuntu.com precise/main i386 Packages
Hit http://de.archive.ubuntu.com precise/restricted i386 Packages
Hit http://de.archive.ubuntu.com precise/universe i386 Packages
Hit http://de.archive.ubuntu.com precise/multiverse i386 Packages
Hit http://de.archive.ubuntu.com precise/main TranslationIndex
Hit http://de.archive.ubuntu.com precise/multiverse TranslationIndex
Hit http://de.archive.ubuntu.com precise/restricted TranslationIndex
Hit http://de.archive.ubuntu.com precise/universe TranslationIndex
Get:29 http://de.archive.ubuntu.com precise-updates/restricted Sources [4,419 B]
Get:30 http://de.archive.ubuntu.com precise-updates/main Sources [188 kB]
Get:31 http://de.archive.ubuntu.com precise-updates/multiverse Sources [4,241 B]
Get:32 http://de.archive.ubuntu.com precise-updates/universe Sources [61.1 kB]
Get:33 http://de.archive.ubuntu.com precise-updates/main amd64 Packages [426 kB]
Get:34 http://de.archive.ubuntu.com precise-updates/restricted amd64 Packages [8,366 B]
Get:35 http://de.archive.ubuntu.com precise-updates/universe amd64 Packages [152 kB]
Get:36 http://de.archive.ubuntu.com precise-updates/multiverse amd64 Packages [8,677 B]
Get:37 http://de.archive.ubuntu.com precise-updates/main i386 Packages [433 kB]
Get:38 http://de.archive.ubuntu.com precise-updates/restricted i386 Packages [8,374 B]
Get:39 http://de.archive.ubuntu.com precise-updates/universe i386 Packages [153 kB]
Get:40 http://de.archive.ubuntu.com precise-updates/multiverse i386 Packages [9,661 B]
Get:41 http://de.archive.ubuntu.com precise-updates/main TranslationIndex [3,564 B]
Get:42 http://de.archive.ubuntu.com precise-updates/multiverse TranslationIndex [2,605 B]
Get:43 http://de.archive.ubuntu.com precise-updates/restricted TranslationIndex [2,461 B]
Get:44 http://de.archive.ubuntu.com precise-updates/universe TranslationIndex [2,850 B]
Get:45 http://de.archive.ubuntu.com precise-proposed/restricted amd64 Packages [1,972 B]
Get:46 http://de.archive.ubuntu.com precise-proposed/main amd64 Packages [37.1 kB]
Get:47 http://de.archive.ubuntu.com precise-proposed/multiverse amd64 Packages [14 B]
Get:48 http://de.archive.ubuntu.com precise-proposed/universe amd64 Packages [16.6 kB]
Get:49 http://de.archive.ubuntu.com precise-proposed/restricted i386 Packages [1,960 B]
Get:50 http://de.archive.ubuntu.com precise-proposed/main i386 Packages [39.0 kB]
Get:51 http://de.archive.ubuntu.com precise-proposed/multiverse i386 Packages [14 B]
Get:52 http://de.archive.ubuntu.com precise-proposed/universe i386 Packages [16.8 kB]
Get:53 http://de.archive.ubuntu.com precise-proposed/main TranslationIndex [3,564 B]
Get:54 http://de.archive.ubuntu.com precise-proposed/multiverse TranslationIndex [2,605 B]
Get:55 http://de.archive.ubuntu.com precise-proposed/restricted TranslationIndex [2,461 B]
Get:56 http://de.archive.ubuntu.com precise-proposed/universe TranslationIndex [2,850 B]
Hit http://de.archive.ubuntu.com precise/main Translation-en                   
Hit http://de.archive.ubuntu.com precise/multiverse Translation-en             
Hit http://de.archive.ubuntu.com precise/restricted Translation-en             
Hit http://de.archive.ubuntu.com precise/universe Translation-en               
Get:57 http://de.archive.ubuntu.com precise-updates/main Translation-en [210 kB]
Hit http://de.archive.ubuntu.com precise-updates/multiverse Translation-en     
Hit http://de.archive.ubuntu.com precise-updates/restricted Translation-en     
Get:58 http://de.archive.ubuntu.com precise-updates/universe Translation-en [91.4 kB]
Get:59 http://de.archive.ubuntu.com precise-proposed/main Translation-en [19.5 kB]
Hit http://de.archive.ubuntu.com precise-proposed/multiverse Translation-en    
Hit http://de.archive.ubuntu.com precise-proposed/restricted Translation-en    
Get:60 http://de.archive.ubuntu.com precise-proposed/universe Translation-en [10.3 kB]
Fetched 2,828 kB in 7s (379 kB/s)                                              
Reading package lists... Done
bekirsalgin@bekirsalgin:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  indicator-messages indicator-messages-gtk2 indicator-status-provider-mc5
  indicator-status-provider-pidgin libavcodec53 libavformat53 libavutil51
  libindicator-messages-status-provider1 libpostproc52 libproxy1
  libproxy1:i386 libswscale2 make mountall xfce4-settings
15 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 4,507 kB of archives.
After this operation, 5,120 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://de.archive.ubuntu.com/ubuntu/ precise-proposed/main mountall amd64 2.36.1 [68.1 kB]
Get:2 http://de.archive.ubuntu.com/ubuntu/ precise-updates/main libpostproc52 amd64 4:0.8.4-0ubuntu0.12.04.1 [63.5 kB]
Get:3 http://de.archive.ubuntu.com/ubuntu/ precise-updates/main libswscale2 amd64 4:0.8.4-0ubuntu0.12.04.1 [92.3 kB]
Get:4 http://de.archive.ubuntu.com/ubuntu/ precise-updates/main libavformat53 amd64 4:0.8.4-0ubuntu0.12.04.1 [495 kB]
Get:5 http://de.archive.ubuntu.com/ubuntu/ precise-updates/main libavcodec53 amd64 4:0.8.4-0ubuntu0.12.04.1 [2,916 kB]
Get:6 http://de.archive.ubuntu.com/ubuntu/ precise-updates/main libavutil51 amd64 4:0.8.4-0ubuntu0.12.04.1 [63.2 kB]
Get:7 http://de.archive.ubuntu.com/ubuntu/ precise-updates/main libproxy1 i386 0.4.7-0ubuntu4.1 [56.0 kB]
Get:8 http://de.archive.ubuntu.com/ubuntu/ precise-updates/main libproxy1 amd64 0.4.7-0ubuntu4.1 [56.1 kB]
Get:9 http://de.archive.ubuntu.com/ubuntu/ precise-proposed/universe indicator-messages-gtk2 amd64 0.6.0-0ubuntu2 [11.6 kB]
Get:10 http://de.archive.ubuntu.com/ubuntu/ precise-proposed/main libindicator-messages-status-provider1 amd64 0.6.0-0ubuntu2 [5,862 B]
Get:11 http://de.archive.ubuntu.com/ubuntu/ precise-proposed/main indicator-messages amd64 0.6.0-0ubuntu2 [69.9 kB]
Get:12 http://de.archive.ubuntu.com/ubuntu/ precise-proposed/main indicator-status-provider-mc5 amd64 0.6.0-0ubuntu2 [6,236 B]
Get:13 http://de.archive.ubuntu.com/ubuntu/ precise-proposed/main indicator-status-provider-pidgin amd64 0.6.0-0ubuntu2 [6,740 B]
Get:14 http://de.archive.ubuntu.com/ubuntu/ precise-proposed/main make amd64 3.81-8.1ubuntu1.1 [119 kB]
Get:15 http://de.archive.ubuntu.com/ubuntu/ precise-proposed/universe xfce4-settings amd64 4.8.3-1ubuntu3.1 [477 kB]
Fetched 4,507 kB in 3s (1,272 kB/s)  
(Reading database ... 321177 files and directories currently installed.)
Preparing to replace mountall 2.36 (using .../mountall_2.36.1_amd64.deb) ...
Unpacking replacement mountall ...
Preparing to replace libpostproc52 4:0.8.3-0ubuntu0.12.04.1 (using .../libpostproc52_4%3a0.8.4-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement libpostproc52 ...
Preparing to replace libswscale2 4:0.8.3-0ubuntu0.12.04.1 (using .../libswscale2_4%3a0.8.4-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement libswscale2 ...
Preparing to replace libavformat53 4:0.8.3-0ubuntu0.12.04.1 (using .../libavformat53_4%3a0.8.4-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement libavformat53 ...
Preparing to replace libavcodec53 4:0.8.3-0ubuntu0.12.04.1 (using .../libavcodec53_4%3a0.8.4-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement libavcodec53 ...
Preparing to replace libavutil51 4:0.8.3-0ubuntu0.12.04.1 (using .../libavutil51_4%3a0.8.4-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement libavutil51 ...
Preparing to replace libproxy1:i386 0.4.7-0ubuntu4 (using .../libproxy1_0.4.7-0ubuntu4.1_i386.deb) ...
De-configuring libproxy1 ...
Unpacking replacement libproxy1:i386 ...
Preparing to replace libproxy1 0.4.7-0ubuntu4 (using .../libproxy1_0.4.7-0ubuntu4.1_amd64.deb) ...
Unpacking replacement libproxy1 ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up libproxy1:i386 (0.4.7-0ubuntu4.1) ...
Setting up libproxy1 (0.4.7-0ubuntu4.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 321177 files and directories currently installed.)
Preparing to replace indicator-messages-gtk2 0.6.0-0ubuntu1 (using .../indicator-messages-gtk2_0.6.0-0ubuntu2_amd64.deb) ...
Unpacking replacement indicator-messages-gtk2 ...
Preparing to replace libindicator-messages-status-provider1 0.6.0-0ubuntu1 (using .../libindicator-messages-status-provider1_0.6.0-0ubuntu2_amd64.deb) ...
Unpacking replacement libindicator-messages-status-provider1 ...
Preparing to replace indicator-messages 0.6.0-0ubuntu1 (using .../indicator-messages_0.6.0-0ubuntu2_amd64.deb) ...
Unpacking replacement indicator-messages ...
Preparing to replace indicator-status-provider-mc5 0.6.0-0ubuntu1 (using .../indicator-status-provider-mc5_0.6.0-0ubuntu2_amd64.deb) ...
Unpacking replacement indicator-status-provider-mc5 ...
Preparing to replace indicator-status-provider-pidgin 0.6.0-0ubuntu1 (using .../indicator-status-provider-pidgin_0.6.0-0ubuntu2_amd64.deb) ...
Unpacking replacement indicator-status-provider-pidgin ...
Preparing to replace make 3.81-8.1ubuntu1 (using .../make_3.81-8.1ubuntu1.1_amd64.deb) ...
Unpacking replacement make ...
Preparing to replace xfce4-settings 4.8.3-1ubuntu3 (using .../xfce4-settings_4.8.3-1ubuntu3.1_amd64.deb) ...
Unpacking replacement xfce4-settings ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Setting up texlive-base (2009-15) ...
mktexlsr: Updating /var/lib/texmf/ls-R-TEXLIVE... 
mktexlsr: Updating /var/lib/texmf/ls-R-TEXMFMAIN... 
mktexlsr: Updating /var/lib/texmf/ls-R... 
mktexlsr: Done.
Not replacing deleted config file /etc/texmf/dvips/config/config.ps
Not replacing deleted config file /etc/texmf/tex/generic/config/pdftexconfig.tex
Not replacing deleted config file /etc/texmf/dvipdfmx/dvipdfmx.cfg
Not replacing deleted config file /etc/texmf/xdvi/XDvi
dpkg: error processing texlive-base (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of texlive-latex-base:
 texlive-latex-base depends on texlive-base (>= 2009-1); however:
  Package texlive-base is not configured yet.
dpkg: error processing texlive-latex-base (--configure):
 dependency problems - leaving unconfigured
Setting up mountall (2.36.1) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          Setting up libavutil51 (4:0.8.4-0ubuntu0.12.04.1) ...
Setting up libpostproc52 (4:0.8.4-0ubuntu0.12.04.1) ...
Setting up libswscale2 (4:0.8.4-0ubuntu0.12.04.1) ...
Setting up libavcodec53 (4:0.8.4-0ubuntu0.12.04.1) ...
Setting up libavformat53 (4:0.8.4-0ubuntu0.12.04.1) ...
Setting up libindicator-messages-status-provider1 (0.6.0-0ubuntu2) ...
Setting up indicator-messages (0.6.0-0ubuntu2) ...
Setting up indicator-messages-gtk2 (0.6.0-0ubuntu2) ...
Setting up indicator-status-provider-mc5 (0.6.0-0ubuntu2) ...
Setting up indicator-status-provider-pidgin (0.6.0-0ubuntu2) ...
Setting up make (3.81-8.1ubuntu1.1) ...
Setting up xfce4-settings (4.8.3-1ubuntu3.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 texlive-base
 texlive-latex-base
E: Sub-process /usr/bin/dpkg returned an error code (1)
bekirsalgin@bekirsalgin:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libreoffice-help-en-gb libreoffice-help-en-us mythes-en-au mythes-en-us
  language-pack-kde-zh-hans-base hyphen-en-us firefox-locale-zh-hans
  libgconf2-4:i386 python-qt4 python-sip kde-l10n-engb libqtassistantclient4
  language-pack-zh-hans-base libreoffice-l10n-zh-cn kde-l10n-zhcn
  language-pack-zh-hans language-pack-kde-zh-hans libreoffice-help-zh-cn
  libnss3-1d:i386 libreoffice-l10n-en-gb openoffice.org-hyphenation
  libreoffice-l10n-en-za
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up texlive-base (2009-15) ...
mktexlsr: Updating /var/lib/texmf/ls-R-TEXLIVE... 
mktexlsr: Updating /var/lib/texmf/ls-R-TEXMFMAIN... 
mktexlsr: Updating /var/lib/texmf/ls-R... 
mktexlsr: Done.
Not replacing deleted config file /etc/texmf/dvips/config/config.ps
Not replacing deleted config file /etc/texmf/tex/generic/config/pdftexconfig.tex
Not replacing deleted config file /etc/texmf/dvipdfmx/dvipdfmx.cfg
Not replacing deleted config file /etc/texmf/xdvi/XDvi
dpkg: error processing texlive-base (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of texlive-latex-base:
 texlive-latex-base depends on texlive-base (>= 2009-1); however:
  Package texlive-base is not configured yet.
dpkg: error processing texlive-latex-base (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 texlive-base
 texlive-latex-base
E: Sub-process /usr/bin/dpkg returned an error code (1)
bekirsalgin@bekirsalgin:~$ dpkg --configure -a
dpkg: error: requested operation requires superuser privilege
bekirsalgin@bekirsalgin:~$ sudo su
root@bekirsalgin:/home/bekirsalgin# dpkg --configure -a
Setting up texlive-base (2009-15) ...
mktexlsr: Updating /var/lib/texmf/ls-R-TEXLIVE... 
mktexlsr: Updating /var/lib/texmf/ls-R-TEXMFMAIN... 
mktexlsr: Updating /var/lib/texmf/ls-R... 
mktexlsr: Done.
Not replacing deleted config file /etc/texmf/dvips/config/config.ps
Not replacing deleted config file /etc/texmf/tex/generic/config/pdftexconfig.tex
Not replacing deleted config file /etc/texmf/dvipdfmx/dvipdfmx.cfg
Not replacing deleted config file /etc/texmf/xdvi/XDvi
dpkg: error processing texlive-base (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of texlive-latex-base:
 texlive-latex-base depends on texlive-base (>= 2009-1); however:
  Package texlive-base is not configured yet.
dpkg: error processing texlive-latex-base (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 texlive-base
 texlive-latex-base

```

---

### Post by Bashing-om on 2012-11-12
Well, not totally surprised ....OK unless others have a better option, I opt to remove the package and its config files:
```
sudo apt-get remove --purge texworks
``` note lower case is what I see the package name as, in synaptic.
and install from terminal:
```
sudo apt-get install texworks
```[INDENT]see what haps ==> BDQ

[/INDENT]

---

### Post by newb85 on 2012-11-12
Similar issues in this other thread were caused by repository issues:
[http://ubuntuforums.org/showthread.php?t=2082215](http://ubuntuforums.org/showthread.php?t=2082215)

Please give the output of
```
ls /etc/apt/sources.list.d
```

---

### Post by bekirs on 2012-11-13
> **Bashing-om said:**
> Well, not totally surprised ....OK unless others have a better option, I opt to remove the package and its config files:
```
apt-get remove --purge texworks
``` note lower case is what I see the package name as, in synaptic.
and install from terminal:
```
apt-get install texworks
```[INDENT]see what haps ==> BDQ

[/INDENT]

this is what I get after I tried the first command:

```

apt-get remove --purge texworks
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
bekirsalgin@bekirsalgin:~$ sudo apt-get remove --purge texworks
[sudo] password for bekirsalgin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libreoffice-help-en-gb libreoffice-help-en-us mythes-en-au mythes-en-us
  language-pack-kde-zh-hans-base hyphen-en-us firefox-locale-zh-hans
  libgconf2-4:i386 python-qt4 python-sip kde-l10n-engb libqtassistantclient4
  language-pack-zh-hans-base libreoffice-l10n-zh-cn kde-l10n-zhcn
  language-pack-zh-hans language-pack-kde-zh-hans libreoffice-help-zh-cn
  libnss3-1d:i386 libreoffice-l10n-en-gb openoffice.org-hyphenation
  libreoffice-l10n-en-za
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  texworks*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 3,617 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 321176 files and directories currently installed.)
Removing texworks ...
Processing triggers for desktop-file-utils ...
Processing triggers for man-db ...
Setting up texlive-base (2009-15) ...
mktexlsr: Updating /var/lib/texmf/ls-R-TEXLIVE... 
mktexlsr: Updating /var/lib/texmf/ls-R-TEXMFMAIN... 
mktexlsr: Updating /var/lib/texmf/ls-R... 
mktexlsr: Done.
Not replacing deleted config file /etc/texmf/dvips/config/config.ps
Not replacing deleted config file /etc/texmf/tex/generic/config/pdftexconfig.tex
Not replacing deleted config file /etc/texmf/dvipdfmx/dvipdfmx.cfg
Not replacing deleted config file /etc/texmf/xdvi/XDvi
dpkg: error processing texlive-base (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of texlive-latex-base:
 texlive-latex-base depends on texlive-base (>= 2009-1); however:
  Package texlive-base is not configured yet.
dpkg: error processing texlive-latex-base (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 texlive-base
 texlive-latex-base
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by bekirs on 2012-11-13
> **newb85 said:**
> Similar issues in this other thread were caused by repository issues:
[http://ubuntuforums.org/showthread.php?t=2082215](http://ubuntuforums.org/showthread.php?t=2082215)

Please give the output of
```
ls /etc/apt/sources.list.d
```

here is the output:

```

ls /etc/apt/sources.list.d
google-chrome.list                  texlive-backports-ppa-precise.list.save
google-chrome.list.save             texworks-stable-precise.list
texlive-backports-ppa-precise.list  texworks-stable-precise.list.save


```

---

### Post by Bashing-om on 2012-11-13
bekirs;

I did oops--- my last did not advise to use sudo for those terminal commands- corrected my entry-
bk
And newb85 appears to have the correct slant on this situation, in accordance with the content of the sources.list.d file. Deleting that file in all likely hood will permit removal/reinstall of the texworks package.(sudo !)
```
sudo rm /etc/apt/sources.list.d/
```[INDENT]processing fault isolation ==> BDQ

[/INDENT]

---

### Post by bekirs on 2012-11-13
> **Bashing-om said:**
> bekirs;

I did oops--- my last did not advise to use sudo for those terminal commands- corrected my entry-
bk
And newb85 appears to have the correct slant on this situation, in accordance with the content of the sources.list.d file. Deleting that file in all likely hood will permit removal/reinstall of the texworks package.(sudo !)
```
sudo rm /etc/apt/sources.list.d
```[INDENT]processing fault isolation ==> BDQ

[/INDENT]

I guess I have to provide you the final output
```

sudo rm /etc/apt/sources.list.d
[sudo] password for bekirsalgin: 
rm: cannot remove `/etc/apt/sources.list.d': Is a directory


```

---

### Post by newb85 on 2012-11-13
Actually, sources.list.d is a directory, and I wouldn't advise removing the entire directory.  (The above command won't work without the -r option, but that's a little beside the point.)  For now, I would open Software Sources (from the Software Center, Edit>Software Sources), go to the Other Software tab, and un-check all entries for texlive-backports and texworks-stable.  Then try reinstalling with

```
sudo apt-get update
sudo apt-get purge texworks
sudo apt-get autoremove
sudo apt-get install texworks
```

---

### Post by Bashing-om on 2012-11-13
Again Not pay proper attention ... amended ...
```
sudo rm /etc/apt/sources.list.d/
```looks much better.
and info from the manual:
> 
The /etc/apt/sources.list.d directory provides a way to add sources.list entries in separate files. The format is the same as for the regular sources.list file.[INDENT]out to lunch ==> BDQ

[/INDENT]

---

### Post by newb85 on 2012-11-13
Again, please do not remove all the contents of the sources.list.d directory.  That will remove other PPAs you've added to your system, including the one for Chrome.

---

### Post by bekirs on 2012-11-13
> **newb85 said:**
> Actually, sources.list.d is a directory, and I wouldn't advise removing the entire directory.  (The above command won't work without the -r option, but that's a little beside the point.)  For now, I would open Software Sources (from the Software Center, Edit>Software Sources), go to the Other Software tab, and un-check all entries for texlive-backports and texworks-stable.  Then try reinstalling with

```
sudo apt-get update
sudo apt-get purge texworks
sudo apt-get autoremove
sudo apt-get install texworks
```

In "Software Sources>Other Software", entries you mentioned are already unchecked? Should I go on with the codes you wrote?

---

### Post by newb85 on 2012-11-13
Yes.

---

### Post by Bashing-om on 2012-11-13
thanks to newb85 for catching my error //

[INDENT]again to myself, slow down and focus !
[/INDENT]

---

### Post by bekirs on 2012-11-14
> **newb85 said:**
> Actually, sources.list.d is a directory, and I wouldn't advise removing the entire directory.  (The above command won't work without the -r option, but that's a little beside the point.)  For now, I would open Software Sources (from the Software Center, Edit>Software Sources), go to the Other Software tab, and un-check all entries for texlive-backports and texworks-stable.  Then try reinstalling with

```
sudo apt-get update
sudo apt-get purge texworks
sudo apt-get autoremove
sudo apt-get install texworks
```

Here is the output after each command:

```

sudo apt-get update
[sudo] password for bekirsalgin: 
Ign http://dl.google.com stable InRelease
Ign http://archive.canonical.com precise InRelease                             
Ign http://extras.ubuntu.com precise InRelease                                 
Ign http://de.archive.ubuntu.com precise InRelease                             
Ign http://de.archive.ubuntu.com precise-updates InRelease                     
Ign http://security.ubuntu.com precise-security InRelease            
Ign http://de.archive.ubuntu.com precise-proposed InRelease                    
Hit http://dl.google.com stable Release.gpg                                    
Hit http://archive.canonical.com precise Release.gpg                           
Hit http://de.archive.ubuntu.com precise Release.gpg                           
Get:1 http://extras.ubuntu.com precise Release.gpg [72 B]                      
Get:2 http://security.ubuntu.com precise-security Release.gpg [198 B]          
Get:3 http://de.archive.ubuntu.com precise-updates Release.gpg [198 B]         
Hit http://dl.google.com stable Release                              
Hit http://archive.canonical.com precise Release                     
Hit http://extras.ubuntu.com precise Release                                   
Get:4 http://de.archive.ubuntu.com precise-proposed Release.gpg [198 B]        
Get:5 http://security.ubuntu.com precise-security Release [49.6 kB]   
Hit http://de.archive.ubuntu.com precise Release                              
Get:6 http://de.archive.ubuntu.com precise-updates Release [49.6 kB]           
Get:7 http://de.archive.ubuntu.com precise-proposed Release [49.6 kB]          
Hit http://dl.google.com stable/main amd64 Packages                          
Hit http://dl.google.com stable/main i386 Packages                             
Ign http://dl.google.com stable/main TranslationIndex                          
Hit http://archive.canonical.com precise/partner amd64 Packages                
Hit http://extras.ubuntu.com precise/main amd64 Packages                       
Hit http://archive.canonical.com precise/partner i386 Packages                 
Ign http://archive.canonical.com precise/partner TranslationIndex              
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Hit http://de.archive.ubuntu.com precise/restricted Sources                    
Get:8 http://security.ubuntu.com precise-security/restricted Sources [1,950 B] 
Hit http://de.archive.ubuntu.com precise/main Sources                          
Hit http://de.archive.ubuntu.com precise/multiverse Sources                    
Hit http://de.archive.ubuntu.com precise/universe Sources                      
Hit http://de.archive.ubuntu.com precise/main amd64 Packages                   
Hit http://de.archive.ubuntu.com precise/restricted amd64 Packages             
Hit http://de.archive.ubuntu.com precise/universe amd64 Packages               
Hit http://de.archive.ubuntu.com precise/multiverse amd64 Packages             
Hit http://de.archive.ubuntu.com precise/main i386 Packages                    
Hit http://de.archive.ubuntu.com precise/restricted i386 Packages              
Hit http://de.archive.ubuntu.com precise/universe i386 Packages                
Hit http://de.archive.ubuntu.com precise/multiverse i386 Packages              
Get:9 http://security.ubuntu.com precise-security/main Sources [54.6 kB]       
Hit http://de.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://de.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://de.archive.ubuntu.com precise/restricted TranslationIndex           
Hit http://de.archive.ubuntu.com precise/universe TranslationIndex             
Get:10 http://de.archive.ubuntu.com precise-updates/restricted Sources [4,419 B]
Get:11 http://de.archive.ubuntu.com precise-updates/main Sources [187 kB]      
Get:12 http://security.ubuntu.com precise-security/multiverse Sources [1,392 B]
Get:13 http://security.ubuntu.com precise-security/universe Sources [15.8 kB]  
Get:14 http://security.ubuntu.com precise-security/main amd64 Packages [196 kB]
Ign http://dl.google.com stable/main Translation-en_US                         
Get:15 http://de.archive.ubuntu.com precise-updates/multiverse Sources [4,241 B]
Get:16 http://de.archive.ubuntu.com precise-updates/universe Sources [61.6 kB] 
Ign http://dl.google.com stable/main Translation-en                            
Get:17 http://de.archive.ubuntu.com precise-updates/main amd64 Packages [426 kB]
Get:18 http://security.ubuntu.com precise-security/restricted amd64 Packages [3,969 B]
Get:19 http://security.ubuntu.com precise-security/universe amd64 Packages [54.7 kB]
Get:20 http://security.ubuntu.com precise-security/multiverse amd64 Packages [2,189 B]
Get:21 http://security.ubuntu.com precise-security/main i386 Packages [201 kB] 
Ign http://archive.canonical.com precise/partner Translation-en_US             
Ign http://extras.ubuntu.com precise/main Translation-en_US                    
Ign http://archive.canonical.com precise/partner Translation-en                
Get:22 http://de.archive.ubuntu.com precise-updates/restricted amd64 Packages [8,366 B]
Ign http://extras.ubuntu.com precise/main Translation-en                       
Get:23 http://de.archive.ubuntu.com precise-updates/universe amd64 Packages [153 kB]
Get:24 http://security.ubuntu.com precise-security/restricted i386 Packages [3,968 B]
Get:25 http://de.archive.ubuntu.com precise-updates/multiverse amd64 Packages [8,677 B]
Get:26 http://de.archive.ubuntu.com precise-updates/main i386 Packages [433 kB]
Get:27 http://security.ubuntu.com precise-security/universe i386 Packages [54.9 kB]
Get:28 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,388 B]
Hit http://security.ubuntu.com precise-security/main TranslationIndex          
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex    
Hit http://security.ubuntu.com precise-security/universe TranslationIndex      
Hit http://security.ubuntu.com precise-security/main Translation-en            
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Get:29 http://de.archive.ubuntu.com precise-updates/restricted i386 Packages [8,374 B]
Get:30 http://de.archive.ubuntu.com precise-updates/universe i386 Packages [153 kB]
Get:31 http://de.archive.ubuntu.com precise-updates/multiverse i386 Packages [9,661 B]
Get:32 http://de.archive.ubuntu.com precise-updates/main TranslationIndex [3,564 B]
Get:33 http://de.archive.ubuntu.com precise-updates/multiverse TranslationIndex [2,605 B]
Get:34 http://de.archive.ubuntu.com precise-updates/restricted TranslationIndex [2,461 B]
Get:35 http://de.archive.ubuntu.com precise-updates/universe TranslationIndex [2,850 B]
Get:36 http://de.archive.ubuntu.com precise-proposed/restricted amd64 Packages [1,972 B]
Get:37 http://de.archive.ubuntu.com precise-proposed/main amd64 Packages [37.9 kB]
Hit http://security.ubuntu.com precise-security/universe Translation-en       
Get:38 http://de.archive.ubuntu.com precise-proposed/multiverse amd64 Packages [14 B]
Get:39 http://de.archive.ubuntu.com precise-proposed/universe amd64 Packages [16.3 kB]
Get:40 http://de.archive.ubuntu.com precise-proposed/restricted i386 Packages [1,960 B]
Get:41 http://de.archive.ubuntu.com precise-proposed/main i386 Packages [39.2 kB]
Get:42 http://de.archive.ubuntu.com precise-proposed/multiverse i386 Packages [14 B]
Get:43 http://de.archive.ubuntu.com precise-proposed/universe i386 Packages [16.5 kB]
Get:44 http://de.archive.ubuntu.com precise-proposed/main TranslationIndex [3,564 B]
Get:45 http://de.archive.ubuntu.com precise-proposed/multiverse TranslationIndex [2,605 B]
Get:46 http://de.archive.ubuntu.com precise-proposed/restricted TranslationIndex [2,461 B]
Get:47 http://de.archive.ubuntu.com precise-proposed/universe TranslationIndex [2,850 B]
Hit http://de.archive.ubuntu.com precise/main Translation-en
Hit http://de.archive.ubuntu.com precise/multiverse Translation-en
Hit http://de.archive.ubuntu.com precise/restricted Translation-en
Hit http://de.archive.ubuntu.com precise/universe Translation-en
Hit http://de.archive.ubuntu.com precise-updates/main Translation-en
Hit http://de.archive.ubuntu.com precise-updates/multiverse Translation-en
Hit http://de.archive.ubuntu.com precise-updates/restricted Translation-en
Hit http://de.archive.ubuntu.com precise-updates/universe Translation-en
Get:48 http://de.archive.ubuntu.com precise-proposed/main Translation-en [20.4 kB]
Hit http://de.archive.ubuntu.com precise-proposed/multiverse Translation-en
Hit http://de.archive.ubuntu.com precise-proposed/restricted Translation-en
Get:49 http://de.archive.ubuntu.com precise-proposed/universe Translation-en [11.0 kB]
Fetched 2,368 kB in 2s (828 kB/s)                                   
Reading package lists... Done


```

```

sudo apt-get purge texworks
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package texworks is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libreoffice-help-en-gb libreoffice-help-en-us mythes-en-au mythes-en-us
  language-pack-kde-zh-hans-base hyphen-en-us firefox-locale-zh-hans
  libgconf2-4:i386 python-qt4 python-sip kde-l10n-engb libqtassistantclient4
  language-pack-zh-hans-base libreoffice-l10n-zh-cn kde-l10n-zhcn
  language-pack-zh-hans language-pack-kde-zh-hans libreoffice-help-zh-cn
  libnss3-1d:i386 libreoffice-l10n-en-gb openoffice.org-hyphenation
  libreoffice-l10n-en-za
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up texlive-base (2009-15) ...
mktexlsr: Updating /var/lib/texmf/ls-R-TEXLIVE... 
mktexlsr: Updating /var/lib/texmf/ls-R-TEXMFMAIN... 
mktexlsr: Updating /var/lib/texmf/ls-R... 
mktexlsr: Done.
Not replacing deleted config file /etc/texmf/dvips/config/config.ps
Not replacing deleted config file /etc/texmf/tex/generic/config/pdftexconfig.tex
Not replacing deleted config file /etc/texmf/dvipdfmx/dvipdfmx.cfg
Not replacing deleted config file /etc/texmf/xdvi/XDvi
dpkg: error processing texlive-base (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of texlive-latex-base:
 texlive-latex-base depends on texlive-base (>= 2009-1); however:
  Package texlive-base is not configured yet.
dpkg: error processing texlive-latex-base (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 texlive-base
 texlive-latex-base
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

```

sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  firefox-locale-zh-hans hyphen-en-us kde-l10n-engb kde-l10n-zhcn
  language-pack-kde-zh-hans language-pack-kde-zh-hans-base
  language-pack-zh-hans language-pack-zh-hans-base libgconf2-4:i386
  libnss3-1d:i386 libqtassistantclient4 libreoffice-help-en-gb
  libreoffice-help-en-us libreoffice-help-zh-cn libreoffice-l10n-en-gb
  libreoffice-l10n-en-za libreoffice-l10n-zh-cn mythes-en-au mythes-en-us
  openoffice.org-hyphenation python-qt4 python-sip
0 upgraded, 0 newly installed, 22 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 164 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 321166 files and directories currently installed.)
Removing firefox-locale-zh-hans ...
Removing hyphen-en-us ...
Removing kde-l10n-engb ...
Removing kde-l10n-zhcn ...
Removing libgconf2-4:i386 ...
Removing libnss3-1d:i386 ...
Removing python-qt4 ...
Removing libqtassistantclient4 ...
Removing libreoffice-help-en-gb ...
Removing libreoffice-help-en-us ...
Removing libreoffice-help-zh-cn ...
Removing libreoffice-l10n-en-gb ...
Removing libreoffice-l10n-en-za ...
Removing libreoffice-l10n-zh-cn ...
Removing mythes-en-au ...
Removing mythes-en-us ...
Removing openoffice.org-hyphenation ...
Removing python-sip ...
Removing language-pack-zh-hans-base ...
Removing language-pack-kde-zh-hans-base ...
Removing language-pack-kde-zh-hans ...
Removing language-pack-zh-hans ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for software-center ...
INFO:softwarecenter.db.update:no translation information in database needed
Setting up texlive-base (2009-15) ...
mktexlsr: Updating /var/lib/texmf/ls-R-TEXLIVE... 
mktexlsr: Updating /var/lib/texmf/ls-R-TEXMFMAIN... 
mktexlsr: Updating /var/lib/texmf/ls-R... 
mktexlsr: Done.
Not replacing deleted config file /etc/texmf/dvips/config/config.ps
Not replacing deleted config file /etc/texmf/tex/generic/config/pdftexconfig.tex
Not replacing deleted config file /etc/texmf/dvipdfmx/dvipdfmx.cfg
Not replacing deleted config file /etc/texmf/xdvi/XDvi
dpkg: error processing texlive-base (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of texlive-latex-base:
 texlive-latex-base depends on texlive-base (>= 2009-1); however:
  Package texlive-base is not configured yet.
dpkg: error processing texlive-latex-base (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 texlive-base
 texlive-latex-base
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

```

sudo apt-get install texworks
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  texlive-xetex texworks-scripting-lua texworks-scripting-python
The following NEW packages will be installed:
  texworks
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0 B/2,360 kB of archives.
After this operation, 3,617 kB of additional disk space will be used.
Selecting previously unselected package texworks.
(Reading database ... 318899 files and directories currently installed.)
Unpacking texworks (from .../texworks_0.5~svn952-1_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Setting up texlive-base (2009-15) ...
mktexlsr: Updating /var/lib/texmf/ls-R-TEXLIVE... 
mktexlsr: Updating /var/lib/texmf/ls-R-TEXMFMAIN... 
mktexlsr: Updating /var/lib/texmf/ls-R... 
mktexlsr: Done.
Not replacing deleted config file /etc/texmf/dvips/config/config.ps
Not replacing deleted config file /etc/texmf/tex/generic/config/pdftexconfig.tex
Not replacing deleted config file /etc/texmf/dvipdfmx/dvipdfmx.cfg
Not replacing deleted config file /etc/texmf/xdvi/XDvi
dpkg: error processing texlive-base (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of texlive-latex-base:
 texlive-latex-base depends on texlive-base (>= 2009-1); however:
  Package texlive-base is not configured yet.
dpkg: error processing texlive-latex-base (--configure):
 dependency problems - leaving unconfigured
Setting up texworks (0.5~svn952-1) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 texlive-base
 texlive-latex-base
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by newb85 on 2012-11-14
The issue seems to stem from this.

> **bekirs said:**
> 
```

sudo apt-get install texworks
...
Setting up texlive-base (2009-15) ...
mktexlsr: Updating /var/lib/texmf/ls-R-TEXLIVE... 
mktexlsr: Updating /var/lib/texmf/ls-R-TEXMFMAIN... 
mktexlsr: Updating /var/lib/texmf/ls-R... 
mktexlsr: Done.
[B]Not replacing deleted config file /etc/texmf/dvips/config/config.ps
Not replacing deleted config file /etc/texmf/tex/generic/config/pdftexconfig.tex
Not replacing deleted config file /etc/texmf/dvipdfmx/dvipdfmx.cfg
Not replacing deleted config file /etc/texmf/xdvi/XDvi
dpkg: error processing texlive-base (--configure):
 subprocess installed post-installation script returned error exit status 1[/B]
dpkg: dependency problems prevent configuration of texlive-latex-base:
 texlive-latex-base depends on texlive-base (>= 2009-1); however:
  Package texlive-base is not configured yet.
dpkg: error processing texlive-latex-base (--configure):
 dependency problems - leaving unconfigured
Setting up texworks (0.5~svn952-1) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 texlive-base
 texlive-latex-base
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

Seems to me that those deleted config files need to be replaced.  I'm just not sure how to force dpkg to do that...

Edit: please give the output of
```
ls /etc/texmf
```

---

### Post by bryncoles on 2012-11-14
Hi all!  

Googling the error code "Not replacing deleted config file ubuntu" lead me to [this page](http://blog.novirusthanks.org/2009/02/not-replacing-deleted-config-file-etcphpmyadminapacheconf/), which suggests the solution should be to run the commands (one at a time):

```
apt-get remove texworks
dpkg -P texworks
apt-get install texworks
```

Might have to sudo those commands though heh heh heh!  I have checked the thread, and I didn't see the dpkg -P step anywhere.  

Good luck!

---

### Post by bekirs on 2012-11-14
> **newb85 said:**
> The issue seems to stem from this.



Seems to me that those deleted config files need to be replaced.  I'm just not sure how to force dpkg to do that...

Edit: please give the output of
```
ls /etc/texmf
```

here is the output:

```

ls /etc/texmf
dvipdfm   dvips  hyphen.d    metafont  texdoc    texmf.cnf  updmap.d  xdvi
dvipdfmx  fmt.d  language.d  tex       texdoctk  texmf.d    web2c


```

---

### Post by bekirs on 2012-11-14
> **bryncoles said:**
> Hi all!  

Googling the error code "Not replacing deleted config file ubuntu" lead me to [this page](http://blog.novirusthanks.org/2009/02/not-replacing-deleted-config-file-etcphpmyadminapacheconf/), which suggests the solution should be to run the commands (one at a time):

```
apt-get remove texworks
dpkg -P texworks
apt-get install texworks
```

Might have to sudo those commands though heh heh heh!  I have checked the thread, and I didn't see the dpkg -P step anywhere.  

Good luck!

OK, I give you the results:

```
apt-get remove texworks
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
bekirsalgin@bekirsalgin:~$ sudo apt-get remove texworks
[sudo] password for bekirsalgin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  texworks
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 3,617 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 318908 files and directories currently installed.)
Removing texworks ...
Processing triggers for desktop-file-utils ...
Processing triggers for man-db ...
Setting up texlive-base (2009-15) ...
mktexlsr: Updating /var/lib/texmf/ls-R-TEXLIVE... 
mktexlsr: Updating /var/lib/texmf/ls-R-TEXMFMAIN... 
mktexlsr: Updating /var/lib/texmf/ls-R... 
mktexlsr: Done.
Not replacing deleted config file /etc/texmf/dvips/config/config.ps
Not replacing deleted config file /etc/texmf/tex/generic/config/pdftexconfig.tex
Not replacing deleted config file /etc/texmf/dvipdfmx/dvipdfmx.cfg
Not replacing deleted config file /etc/texmf/xdvi/XDvi
dpkg: error processing texlive-base (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of texlive-latex-base:
 texlive-latex-base depends on texlive-base (>= 2009-1); however:
  Package texlive-base is not configured yet.
dpkg: error processing texlive-latex-base (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 texlive-base
 texlive-latex-base
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

```
dpkg -P texworks
dpkg: error: requested operation requires superuser privilege
bekirsalgin@bekirsalgin:~$ sudo dpkg -P texworks
dpkg: warning: there's no installed package matching texworks

```

```
sudo apt-get install texworks
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  texlive-xetex texworks-scripting-lua texworks-scripting-python
The following NEW packages will be installed:
  texworks
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0 B/2,360 kB of archives.
After this operation, 3,617 kB of additional disk space will be used.
Selecting previously unselected package texworks.
(Reading database ... 318899 files and directories currently installed.)
Unpacking texworks (from .../texworks_0.5~svn952-1_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Setting up texlive-base (2009-15) ...
mktexlsr: Updating /var/lib/texmf/ls-R-TEXLIVE... 
mktexlsr: Updating /var/lib/texmf/ls-R-TEXMFMAIN... 
mktexlsr: Updating /var/lib/texmf/ls-R... 
mktexlsr: Done.
Not replacing deleted config file /etc/texmf/dvips/config/config.ps
Not replacing deleted config file /etc/texmf/tex/generic/config/pdftexconfig.tex
Not replacing deleted config file /etc/texmf/dvipdfmx/dvipdfmx.cfg
Not replacing deleted config file /etc/texmf/xdvi/XDvi
dpkg: error processing texlive-base (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of texlive-latex-base:
 texlive-latex-base depends on texlive-base (>= 2009-1); however:
  Package texlive-base is not configured yet.
dpkg: error processing texlive-latex-base (--configure):
 dependency problems - leaving unconfigured
Setting up texworks (0.5~svn952-1) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 texlive-base
 texlive-latex-base
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by newb85 on 2012-11-14
Yeah, that dpkg command won't work without sudo, but I don't think it will do any more than apt-get purge.

Try this:
```
sudo apt-get purge texworks
ls /etc/texmf
```

If it has successfully emptied the /etc/texmf directory (with the exception maybe of fmt.d directory), then I'm stumped.  If all the same files are there as before, proceed like this:

```
sudo cp -rp /etc/texmf /etc/texmf.old
sudo rm -r /etc/texmf/*
sudo cp -rp /etc/texmf.old/fmt.d /etc/texmf/fmt.d
sudo apt-get install texworks
```

---

### Post by bekirs on 2012-11-14
> **newb85 said:**
> Yeah, that dpkg command won't work without sudo, but I don't think it will do any more than apt-get purge.

Try this:
```
sudo apt-get purge texworks
ls /etc/texmf
```

If it has successfully emptied the /etc/texmf directory (with the exception maybe of fmt.d directory), then I'm stumped.  If all the same files are there as before, proceed like this:

```
sudo cp -rp /etc/texmf /etc/texmf.old
sudo rm -r /etc/texmf/*
sudo cp -rp /etc/texmf.old/fmt.d /etc/texmf/fmt.d
sudo apt-get install texworks
```

I think it didn't work:
```

sudo apt-get purge texworks
[sudo] password for bekirsalgin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  texworks*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 3,617 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 318908 files and directories currently installed.)
Removing texworks ...
Processing triggers for desktop-file-utils ...
Processing triggers for man-db ...
Setting up texlive-base (2009-15) ...
mktexlsr: Updating /var/lib/texmf/ls-R-TEXLIVE... 
mktexlsr: Updating /var/lib/texmf/ls-R-TEXMFMAIN... 
mktexlsr: Updating /var/lib/texmf/ls-R... 
mktexlsr: Done.
Not replacing deleted config file /etc/texmf/dvips/config/config.ps
Not replacing deleted config file /etc/texmf/tex/generic/config/pdftexconfig.tex
Not replacing deleted config file /etc/texmf/dvipdfmx/dvipdfmx.cfg
Not replacing deleted config file /etc/texmf/xdvi/XDvi
dpkg: error processing texlive-base (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of texlive-latex-base:
 texlive-latex-base depends on texlive-base (>= 2009-1); however:
  Package texlive-base is not configured yet.
dpkg: error processing texlive-latex-base (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 texlive-base
 texlive-latex-base
E: Sub-process /usr/bin/dpkg returned an error code (1)


```
```
ls /etc/texmf
dvipdfm   dvips  hyphen.d    metafont  texdoc    texmf.cnf  updmap.d  xdvi
dvipdfmx  fmt.d  language.d  tex       texdoctk  texmf.d    web2c

```

```
sudo cp -rp /etc/texmf /etc/texmf.old
bekirsalgin@bekirsalgin:~$ sudo rm -r /etc/texmf/*
bekirsalgin@bekirsalgin:~$ sudo cp -rp /etc/texmf.old/fmt.d /etc/texmf/fmt.d
bekirsalgin@bekirsalgin:~$ sudo apt-get install texworks
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  texlive-xetex texworks-scripting-lua texworks-scripting-python
The following NEW packages will be installed:
  texworks
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0 B/2,360 kB of archives.
After this operation, 3,617 kB of additional disk space will be used.
Selecting previously unselected package texworks.
(Reading database ... 318899 files and directories currently installed.)
Unpacking texworks (from .../texworks_0.5~svn952-1_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Setting up texlive-base (2009-15) ...
mktexlsr: Updating /var/lib/texmf/ls-R-TEXLIVE... 
mktexlsr: Updating /var/lib/texmf/ls-R-TEXMFMAIN... 
mktexlsr: Updating /var/lib/texmf/ls-R... 
mktexlsr: Done.
warning: kpathsea: configuration file texmf.cnf not found in these directories: /usr/share/texmf/web2c:/usr/share/texmf-texlive/web2c:/usr/local/share/texmf/web2c.
warning: kpathsea: configuration file texmf.cnf not found in these directories: /usr/share/texmf/web2c:/usr/share/texmf-texlive/web2c:/usr/local/share/texmf/web2c.
warning: kpathsea: configuration file texmf.cnf not found in these directories: /usr/share/texmf/web2c:/usr/share/texmf-texlive/web2c:/usr/local/share/texmf/web2c.
warning: kpathsea: configuration file texmf.cnf not found in these directories: /usr/share/texmf/web2c:/usr/share/texmf-texlive/web2c:/usr/local/share/texmf/web2c.
Not replacing deleted config file /etc/texmf/dvips/config/config.ps
Not replacing deleted config file /etc/texmf/tex/generic/config/pdftexconfig.tex
Not replacing deleted config file /etc/texmf/dvipdfmx/dvipdfmx.cfg
Not replacing deleted config file /etc/texmf/xdvi/XDvi
warning: kpathsea: configuration file texmf.cnf not found in these directories: /usr/share/texmf/web2c:/usr/share/texmf-texlive/web2c:/usr/local/share/texmf/web2c.
dpkg: error processing texlive-base (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of texlive-latex-base:
 texlive-latex-base depends on texlive-base (>= 2009-1); however:
  Package texlive-base is not configured yet.
dpkg: error processing texlive-latex-base (--configure):
 dependency problems - leaving unconfigured
Setting up texworks (0.5~svn952-1) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 texlive-base
 texlive-latex-base
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by Bashing-om on 2012-11-14
Hey guys, looking in synaptic package manager ->
both texlive-base and texlive-latex-base are listed as individual packages.

How about remove (re)install just these two dependencies ?
[INDENT]think'n and look'n ==> BDQ

[/INDENT]

---

### Post by bekirs on 2012-11-15
> **Bashing-om said:**
> Hey guys, looking in synaptic package manager ->
both texlive-base and texlive-latex-base are listed as individual packages.

How about remove (re)install just these two dependencies ?
[INDENT]think'n and look'n ==> BDQ

[/INDENT]

The following message showed up when I wanted to remove both packages from synaptic:

```

E: tex-common: subprocess installed post-installation script returned error exit status 1

```

---

### Post by Bashing-om on 2012-11-15
How about we try and get some more information. As I still look at the dependencies having the config problems. What results with terminal command:
```
sudo dpkg-reconfigure texlive-base 
```[INDENT]hope 'n ==> BDQ

[/INDENT]

---

### Post by bekirs on 2012-11-16
> **Bashing-om said:**
> How about we try and get some more information. As I still look at the dependencies having the config problems. What results with terminal command:
```
sudo dpkg-reconfigure texlive-base 
```[INDENT]hope 'n ==> BDQ

[/INDENT]

This is what I get after typing your suggestion:

```
sudo dpkg-reconfigure texlive-base
[sudo] password for bekirsalgin: 
/usr/sbin/dpkg-reconfigure: texlive-base is broken or not fully installed

```

Then, I tried to reinstall **texlive-base** from Synaptic. The following two messages appeared:

```
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
dpkg: dependency problems prevent configuration of texlive-base:
 texlive-base depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
dpkg: error processing texlive-base (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 tex-common
 texlive-base
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
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
dpkg: dependency problems prevent configuration of texlive-base:
 texlive-base depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
dpkg: error processing texlive-base (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 tex-common
 texlive-base
```

```
E: tex-common: subprocess installed post-installation script returned error exit status 1
E: texlive-base: dependency problems - leaving unconfigured
```

I then tried again with your first command and here is the result:

```
sudo dpkg-reconfigure texlive-base
/usr/sbin/dpkg-reconfigure: texlive-base is broken or not fully installed

```

---

### Post by Bashing-om on 2012-11-16
Two packages with configuration errors, pointing to "tex-common". As smp also shows "tex-common" as an individual package -> let's tackle em one at a time, and perhaps "tex-common" is common to both. First with:
```
sudo dpkg-reconfigure tex-common
```Getting deeper and deeper into texworks !
[INDENT]hope we are getting somewhere <== BDQ
 
[/INDENT]

---

### Post by bekirs on 2012-11-16
> **Bashing-om said:**
> Two packages with configuration errors, pointing to "tex-common". As smp also shows "tex-common" as an individual package -> let's tackle em one at a time, and perhaps "tex-common" is common to both. First with:
```
sudo dpkg-reconfigure tex-common
```Getting deeper and deeper into texworks !
[INDENT]hope we are getting somewhere <== BDQ
 
[/INDENT]

Output:

```
sudo dpkg-reconfigure tex-common
[sudo] password for bekirsalgin: 
/usr/sbin/dpkg-reconfigure: tex-common is broken or not fully installed

```

---

### Post by Bashing-om on 2012-11-16
ok, let's take dpkg's advise and (re)install the package:
```
sudo apt-get --reinstall tex-common
```[INDENT]are we there yet ? ==> BDQ

[/INDENT]

---

### Post by bekirs on 2012-11-16
> **Bashing-om said:**
> ok, let's take dpkg's advise and (re)install the package:
```
sudo apt-get --reinstall tex-common
```[INDENT]are we there yet ? ==> BDQ

[/INDENT]

Output:

```
sudo apt-get --reinstall tex-common
[sudo] password for bekirsalgin: 
E: Invalid operation tex-common

```

---

### Post by Bashing-om on 2012-11-16
That makes me question that the package is even installed ! Let's look.
```
sudo dpkg --list tex-common
sudo dpkg --status tex-common
sudo dpkg --audit

```[INDENT]What is we will see ==> BDQ

[/INDENT]

---

### Post by bekirs on 2012-11-16
> **Bashing-om said:**
> That makes me question that the package is even installed ! Let's look.
```
sudo dpkg --list tex-common
sudo dpkg --status tex-common
sudo dpkg --audit

```[INDENT]What is we will see ==> BDQ

[/INDENT]

```
sudo dpkg --list tex-common
[sudo] password for bekirsalgin: 
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
iF  tex-common     2.10           common infrastructure for building and insta

```

```
sudo dpkg --status tex-common
Package: tex-common
Status: install ok half-configured
Priority: optional
Section: tex
Installed-Size: 1552
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: all
Version: 2.10
Config-Version: 2.10
Replaces: dvipdfmx, tetex-base (<= 3.0-10)
Depends: debconf (>= 0.5) | debconf-2.0, ucf, debconf (>= 1.4.69) | cdebconf (>= 0.39), dpkg (>= 1.14.18)
Suggests: debhelper (>= 7.0.8)
Conflicts: tetex-base (<< 2007), texlive-common (<< 2009)
Conffiles:
 /etc/texmf/fmt.d/00tex.cnf 968f2b29eb4089534b9625cd181c25e3
 /etc/texmf/hyphen.d/00tex.cnf 1d7236736c45d5df1422091b1dc1e7f9
 /etc/texmf/web2c/mktex.cnf 9c342b3465afe4c13049c55218e23eaf
Description: common infrastructure for building and installing TeX
 This package contains a number of scripts and common configuration
 files that are needed to install a TeX System.
 .
 It also contains debhelper-like programs useful for building TeX
 packages.
Original-Maintainer: Debian TeX maintainers <debian-tex-maint@lists.debian.org>

```

```
sudo dpkg --audit
The following packages are only half configured, probably due to problems
configuring them the first time.  The configuration should be retried using
dpkg --configure <package> or the configure menu option in dselect:
 texlive-base         TeX Live: Essential programs and files
 tex-common           common infrastructure for building and installing TeX

```

---

### Post by newb85 on 2012-11-16
> **bekirs said:**
> Output:

```
sudo apt-get --reinstall tex-common
[sudo] password for bekirsalgin: 
E: Invalid operation tex-common

```

Okay, so it looks like we need a quick primer on the apt-get command.

The apt-get command can be run in several modes, including install, remove, purge, update, upgrade, etc.  Whenever the apt-get command is issued, one (and only one) of those modes must be included.  Some modes can also be used as options with other modes.  Options are preceded by a double dash (single dash for one-letter options), while modes are preceded by no dashes.So, for example
```
sudo apt-get remove --purge *package*
```
and
```
sudo apt-get purge *package*
```
would be equivalent, but
```
sudo apt-get --purge *package*
```
would give an invalid operation error message because "--purge" would be interpreted as an option, and because *package* would be the first thing after apt-get to not be interpreted as an option, it would be interpreted as the mode.

In the case at hand, the command

```
sudo apt-get --reinstall tex-common
```
was incorrect because the user didn't include the mode and thus, *tex-common* was interpreted as the mode.  Reinstall is not a mode; it can only be used as an option with another mode.  So, the command should be
```
sudo apt-get install --reinstall tex-common
```

---

### Post by Bashing-om on 2012-11-16
does not tell us nothing we do not already know. --yeah bad english-> the way I feel--Except the package is installed and NOT configured ....shheeesshh// let's try again as suggested.
```
dpkg --configure tex-common
```[INDENT]once again with feeling <== BDQ

[/INDENT]

---

### Post by bekirs on 2012-11-16
> **newb85 said:**
> Okay, so it looks like we need a quick primer on the apt-get command.

The apt-get command can be run in several modes, including install, remove, purge, update, upgrade, etc.  Whenever the apt-get command is issued, one (and only one) of those modes must be included.  Some modes can also be used as options with other modes.  Options are preceded by a double dash (single dash for one-letter options), while modes are preceded by no dashes.So, for example
```
sudo apt-get remove --purge *package*
```
and
```
sudo apt-get purge *package*
```
would be equivalent, but
```
sudo apt-get --purge *package*
```
would give an invalid operation error message because "--purge" would be interpreted as an option, and because *package* would be the first thing after apt-get to not be interpreted as an option, it would be interpreted as the mode.

In the case at hand, the command

```
sudo apt-get --reinstall tex-common
```
was incorrect because the user didn't include the mode and thus, *tex-common* was interpreted as the mode.  Reinstall is not a mode; it can only be used as an option with another mode.  So, the command should be
```
sudo apt-get install --reinstall tex-common
```

the output with the correct command:

```
sudo apt-get install --reinstall tex-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
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
dpkg: dependency problems prevent configuration of texlive-base:
 texlive-base depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
dpkg: error processing texlive-base (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
              Errors were encountered while processing:
 tex-common
 texlive-base
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by bekirs on 2012-11-16
> **Bashing-om said:**
> does not tell us nothing we do not already know. --yeah bad english-> the way I feel--Except the package is installed and NOT configured ....shheeesshh// let's try again as suggested.
```
dpkg --configure tex-common
```[INDENT]once again with feeling <== BDQ

[/INDENT]

```
sudo dpkg --configure tex-common
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

```

---

### Post by Bashing-om on 2012-11-16
well that is something to work with at last ...Now to find what package the file belongs to.
Right off the top of my head I do not recall how...will have to research it and find the method.
[INDENT]I'll Be Back ==> BDQ

[/INDENT]

---

### Post by Bashing-om on 2012-11-16
bekirs; Let's see what this returns:
```
sudo dpkg -S /etc/texmf/texmf.d/05TeXMF.cnf
 
```Hopefully we get the parent package.

@newb85 Thanks again for the tutorial. Reinforcement does help, -> learning to read a commands output.
[INDENT]Still learning ==> BDQ

[/INDENT]

---

### Post by bekirs on 2012-11-17
> **Bashing-om said:**
> bekirs; Let's see what this returns:
```
sudo dpkg -S /etc/texmf/texmf.d/05TeXMF.cnf
 
```Hopefully we get the parent package.

@newb85 Thanks again for the tutorial. Reinforcement does help, -> learning to read a commands output.
[INDENT]Still learning ==> BDQ

[/INDENT]

```
sudo dpkg -S /etc/texmf/texmf.d/05TeXMF.cnf
[sudo] password for bekirsalgin: 
dpkg-query: no path found matching pattern /etc/texmf/texmf.d/05TeXMF.cnf.
```

---

### Post by newb85 on 2012-11-17
Sorry, that's probably my fault.  You may recall (or you can just go back and look), I had you move (not delete, as that's less reversible) all the contents of /etc/texmf back in post #21.  You can copy them back thus:

```
sudo cp -rp /etc/texmf.old /etc/texmf
```

Then you can proceed with BDQ's suggestion in post #39.

---

### Post by bekirs on 2012-11-17
> **newb85 said:**
> Sorry, that's probably my fault.  You may recall (or you can just go back and look), I had you move (not delete, as that's less reversible) all the contents of /etc/texmf back in post #21.  You can copy them back thus:

```
sudo cp -rp /etc/texmf.old /etc/texmf
```

Then you can proceed with BDQ's suggestion in post #39.

I think it does not change the output

```
sudo cp -rp /etc/texmf.old /etc/texmf
bekirsalgin@bekirsalgin:~$ sudo dpkg -S /etc/texmf/texmf.d/05TeXMF.cnf
dpkg-query: no path found matching pattern /etc/texmf/texmf.d/05TeXMF.cnf.

```

---

### Post by Bashing-om on 2012-11-17
Apparently that file is required, and is missing-> gotta find the package that the file belongs to.
let's approach location from the top rather than the bottom, see what results:
```
dpkg -L tex-common
```if that also fails I suugest we use apt-file utility:
```
sudo apt-get install apt-file
sudo apt-file update
apt-file search /etc/texmf/texmf.d/05TeXMF.cnf
```which will search for a potentially uninstalled package providing a certain file.

Not at all certain what will result from the above, what else can we do to identify the package ?
[INDENT]keep swimming 'till we make butter <== BDQ

[/INDENT]

---

### Post by bekirs on 2012-11-18
> **Bashing-om said:**
> Apparently that file is required, and is missing-> gotta find the package that the file belongs to.
let's approach location from the top rather than the bottom, see what results:
```
dpkg -L tex-common
```if that also fails I suugest we use apt-file utility:
```
sudo apt-get install apt-file
sudo apt-file update
apt-file search /etc/texmf/texmf.d/05TeXMF.cnf
```which will search for a potentially uninstalled package providing a certain file.

Not at all certain what will result from the above, what else can we do to identify the package ?
[INDENT]keep swimming 'till we make butter <== BDQ

[/INDENT]

How do we get sure whether it worked or not?

```
dpkg -L tex-common
/.
/usr
/usr/sbin
/usr/sbin/update-texmf
/usr/sbin/update-texmf-config
/usr/bin
/usr/bin/dh_installtex
/usr/bin/update-fontlang
/usr/share
/usr/share/debhelper
/usr/share/debhelper/autoscripts
/usr/share/debhelper/autoscripts/postrm-tex
/usr/share/debhelper/autoscripts/postinst-tex
/usr/share/tex-common
/usr/share/tex-common/05TeXMF.cnf
/usr/share/tex-common/15Plain.cnf
/usr/share/tex-common/45TeXinputs.cnf
/usr/share/tex-common/55Fonts.cnf
/usr/share/tex-common/65BibTeX.cnf
/usr/share/tex-common/75DviPS.cnf
/usr/share/tex-common/80DVIPDFMx.cnf
/usr/share/tex-common/85Misc.cnf
/usr/share/tex-common/90TeXDoc.cnf
/usr/share/tex-common/95NonPath.cnf
/usr/share/tex-common/00updmap.cfg
/usr/share/tex-common/00updmap.cfg.md5sum
/usr/share/tex-common/05TeXMF.cnf.md5sum
/usr/share/tex-common/15Plain.cnf.md5sum
/usr/share/tex-common/45TeXinputs.cnf.md5sum
/usr/share/tex-common/55Fonts.cnf.md5sum
/usr/share/tex-common/65BibTeX.cnf.md5sum
/usr/share/tex-common/75DviPS.cnf.md5sum
/usr/share/tex-common/80DVIPDFMx.cnf.md5sum
/usr/share/tex-common/85Misc.cnf.md5sum
/usr/share/tex-common/90TeXDoc.cnf.md5sum
/usr/share/tex-common/95NonPath.cnf.md5sum
/usr/share/tex-common/texmf.cnf.md5sum.d
/usr/share/tex-common/texmf.cnf.md5sum.d/2.0.2-13
/usr/share/tex-common/texmf.cnf.md5sum.d/1.0.7+20011202-7.1
/usr/share/tex-common/tpm2licenses
/usr/share/tex-common/tpm2licenses.README
/usr/share/tex-common/Tpm.pm
/usr/share/tex-common/FileUtils.pm
/usr/share/tex-common/debianize-updmap
/usr/share/tex-common/mktex.cnf
/usr/share/tex-common/language.def.header
/usr/share/tex-common/language.dat.header
/usr/share/texmf
/usr/share/texmf/web2c
/usr/share/doc
/usr/share/doc/texmf
/usr/share/doc/tex-common
/usr/share/doc/tex-common/Debian-TeX-Policy.pdf.gz
/usr/share/doc/tex-common/TeX-on-Debian.txt.gz
/usr/share/doc/tex-common/Debian-TeX-Policy.html
/usr/share/doc/tex-common/Debian-TeX-Policy.html/index.html
/usr/share/doc/tex-common/Debian-TeX-Policy.html/ch1.html
/usr/share/doc/tex-common/Debian-TeX-Policy.html/ch2.html
/usr/share/doc/tex-common/Debian-TeX-Policy.html/ch3.html
/usr/share/doc/tex-common/Debian-TeX-Policy.html/ch4.html
/usr/share/doc/tex-common/Debian-TeX-Policy.html/ch5.html
/usr/share/doc/tex-common/Debian-TeX-Policy.html/ch6.html
/usr/share/doc/tex-common/Debian-TeX-Policy.html/apA.html
/usr/share/doc/tex-common/Debian-TeX-Policy.html/footnotes.html
/usr/share/doc/tex-common/TeX-on-Debian.pdf.gz
/usr/share/doc/tex-common/tds.pdf.gz
/usr/share/doc/tex-common/TeX-on-Debian.html
/usr/share/doc/tex-common/TeX-on-Debian.html/index.html
/usr/share/doc/tex-common/TeX-on-Debian.html/ch1.html
/usr/share/doc/tex-common/TeX-on-Debian.html/ch2.html
/usr/share/doc/tex-common/TeX-on-Debian.html/ch3.html
/usr/share/doc/tex-common/TeX-on-Debian.html/ch4.html
/usr/share/doc/tex-common/TeX-on-Debian.html/ch5.html
/usr/share/doc/tex-common/TeX-on-Debian.html/footnotes.html
/usr/share/doc/tex-common/tds.dvi.gz
/usr/share/doc/tex-common/changelog.gz
/usr/share/doc/tex-common/NEWS.Debian.gz
/usr/share/doc/tex-common/tds.html
/usr/share/doc/tex-common/copyright
/usr/share/doc/tex-common/Debian-TeX-Policy.txt.gz
/usr/share/doc/tex-common/obsolete-tex-files.txt.gz
/usr/share/bug
/usr/share/bug/tex-common
/usr/share/bug/tex-common/control
/usr/share/lintian
/usr/share/lintian/overrides
/usr/share/lintian/overrides/tex-common
/usr/share/perl5
/usr/share/perl5/Debian
/usr/share/perl5/Debian/Debhelper
/usr/share/perl5/Debian/Debhelper/Sequence
/usr/share/perl5/Debian/Debhelper/Sequence/tex.pm
/usr/share/doc-base
/usr/share/doc-base/debian-tex-policy
/usr/share/doc-base/tex-on-debian
/usr/share/man
/usr/share/man/man8
/usr/share/man/man8/update-texmf.8.gz
/usr/share/man/man8/update-texmf-config.8.gz
/usr/share/man/man1
/usr/share/man/man1/dh_installtex.1.gz
/usr/share/man/man1/update-fontlang.1.gz
/etc
/etc/texmf
/etc/texmf/fmt.d
/etc/texmf/fmt.d/00tex.cnf
/etc/texmf/hyphen.d
/etc/texmf/hyphen.d/00tex.cnf
/etc/texmf/texmf.d
/etc/texmf/updmap.d
/etc/texmf/language.d
/etc/texmf/web2c
/etc/texmf/web2c/mktex.cnf
/var
/var/lib
/var/lib/texmf
/var/lib/texmf/web2c
/var/lib/texmf/tex
/var/lib/texmf/tex/generic
/var/lib/texmf/tex/generic/config
/var/lib/tex-common
/var/lib/tex-common/fontmap-cfg
/var/lib/tex-common/hyphen-cnf
/var/lib/tex-common/fmtutil-cnf
/var/cache
/var/cache/fonts
/usr/sbin/update-language-dat
/usr/sbin/update-language-def
/usr/sbin/update-language
/usr/sbin/update-fmtutil
/usr/sbin/update-updmap
/usr/bin/update-language-dat
/usr/bin/update-language-def
/usr/bin/update-language
/usr/bin/update-fmtutil
/usr/bin/update-updmap
/usr/share/texmf/web2c/texmf.cnf
/usr/share/texmf/doc
/usr/share/texmf/ls-R
/usr/share/doc/tex-common/README.Debian.txt.gz
/usr/share/doc/tex-common/README.Debian.pdf.gz
/usr/share/doc/tex-common/README.Debian.html
/usr/share/man/man1/update-updmap.1.gz
/usr/share/man/man1/update-language-dat.1.gz
/usr/share/man/man1/update-language-def.1.gz
/usr/share/man/man1/update-language.1.gz
/usr/share/man/man1/update-fmtutil.1.gz

```

---

### Post by Bashing-om on 2012-11-18
I am at this time not sure how to proceed. The file that I expect to be in the /etc/ directory appears to exist in the /share/ directory ! Is this a bug ? If so why are not others having a problem ?
 
I do not know what effect it would have if the desired file were to be moved to the referenced directory.

As such -> Let's look at what "apt-file" tells us. See if we can gain more info before proceeding.

Now, wiser heads my prevail ==> BDQ

---

### Post by bekirs on 2012-11-18
> **Bashing-om said:**
> I am at this time not sure how to proceed. The file that I expect to be in the /etc/ directory appears to exist in the /share/ directory ! Is this a bug ? If so why are not others having a problem ?
 
I do not know what effect it would have if the desired file were to be moved to the referenced directory.

As such -> Let's look at what "apt-file" tells us. See if we can gain more info before proceeding.

Now, wiser heads my prevail ==> BDQ

```
sudo apt-get install apt-file
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  build-essential curl dpkg-dev fakeroot g++ g++-4.6 libalgorithm-diff-perl
  libalgorithm-diff-xs-perl libalgorithm-merge-perl libapt-pkg-perl
  libconfig-file-perl libdpkg-perl liblist-moreutils-perl
  libregexp-assemble-perl libstdc++6-4.6-dev
Suggested packages:
  debian-keyring g++-multilib g++-4.6-multilib gcc-4.6-doc libstdc++6-4.6-dbg
  libstdc++6-4.6-doc
The following NEW packages will be installed:
  apt-file build-essential curl dpkg-dev fakeroot g++ g++-4.6
  libalgorithm-diff-perl libalgorithm-diff-xs-perl libalgorithm-merge-perl
  libapt-pkg-perl libconfig-file-perl libdpkg-perl liblist-moreutils-perl
  libregexp-assemble-perl libstdc++6-4.6-dev
0 upgraded, 16 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 9,825 kB of archives.
After this operation, 29.8 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://de.archive.ubuntu.com/ubuntu/ precise/main curl amd64 7.22.0-3ubuntu4 [138 kB]
Get:2 http://de.archive.ubuntu.com/ubuntu/ precise/universe libconfig-file-perl all 1.50-2 [10.1 kB]
Get:3 http://de.archive.ubuntu.com/ubuntu/ precise/main libapt-pkg-perl amd64 0.1.25build2 [82.9 kB]
Get:4 http://de.archive.ubuntu.com/ubuntu/ precise/main liblist-moreutils-perl amd64 0.33-1build1 [49.1 kB]
Get:5 http://de.archive.ubuntu.com/ubuntu/ precise/universe libregexp-assemble-perl all 0.35-2 [87.5 kB]
Get:6 http://de.archive.ubuntu.com/ubuntu/ precise/universe apt-file all 2.5.0ubuntu1 [25.6 kB]
Get:7 http://de.archive.ubuntu.com/ubuntu/ precise/main libstdc++6-4.6-dev amd64 4.6.3-1ubuntu5 [1,660 kB]
Get:8 http://de.archive.ubuntu.com/ubuntu/ precise/main g++-4.6 amd64 4.6.3-1ubuntu5 [6,954 kB]
Get:9 http://de.archive.ubuntu.com/ubuntu/ precise/main g++ amd64 4:4.6.3-1ubuntu5 [1,442 B]
Get:10 http://de.archive.ubuntu.com/ubuntu/ precise/main libdpkg-perl all 1.16.1.2ubuntu7 [181 kB]
Get:11 http://de.archive.ubuntu.com/ubuntu/ precise/main dpkg-dev all 1.16.1.2ubuntu7 [468 kB]
Get:12 http://de.archive.ubuntu.com/ubuntu/ precise-updates/main build-essential amd64 11.5ubuntu2.1 [5,816 B]
Get:13 http://de.archive.ubuntu.com/ubuntu/ precise/main fakeroot amd64 1.18.2-1 [87.2 kB]
Get:14 http://de.archive.ubuntu.com/ubuntu/ precise/main libalgorithm-diff-perl all 1.19.02-2 [50.7 kB]
Get:15 http://de.archive.ubuntu.com/ubuntu/ precise/main libalgorithm-diff-xs-perl amd64 0.04-2build2 [12.4 kB]
Get:16 http://de.archive.ubuntu.com/ubuntu/ precise/main libalgorithm-merge-perl all 0.08-2 [12.7 kB]
Fetched 9,825 kB in 1min 30s (108 kB/s)                                        
Selecting previously unselected package curl.
(Reading database ... 343965 files and directories currently installed.)
Unpacking curl (from .../curl_7.22.0-3ubuntu4_amd64.deb) ...
Selecting previously unselected package libconfig-file-perl.
Unpacking libconfig-file-perl (from .../libconfig-file-perl_1.50-2_all.deb) ...
Selecting previously unselected package libapt-pkg-perl.
Unpacking libapt-pkg-perl (from .../libapt-pkg-perl_0.1.25build2_amd64.deb) ...
Selecting previously unselected package liblist-moreutils-perl.
Unpacking liblist-moreutils-perl (from .../liblist-moreutils-perl_0.33-1build1_amd64.deb) ...
Selecting previously unselected package libregexp-assemble-perl.
Unpacking libregexp-assemble-perl (from .../libregexp-assemble-perl_0.35-2_all.deb) ...
Selecting previously unselected package apt-file.
Unpacking apt-file (from .../apt-file_2.5.0ubuntu1_all.deb) ...
Selecting previously unselected package libstdc++6-4.6-dev.
Unpacking libstdc++6-4.6-dev (from .../libstdc++6-4.6-dev_4.6.3-1ubuntu5_amd64.deb) ...
Selecting previously unselected package g++-4.6.
Unpacking g++-4.6 (from .../g++-4.6_4.6.3-1ubuntu5_amd64.deb) ...
Selecting previously unselected package g++.
Unpacking g++ (from .../g++_4%3a4.6.3-1ubuntu5_amd64.deb) ...
Selecting previously unselected package libdpkg-perl.
Unpacking libdpkg-perl (from .../libdpkg-perl_1.16.1.2ubuntu7_all.deb) ...
Selecting previously unselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.16.1.2ubuntu7_all.deb) ...
Selecting previously unselected package build-essential.
Unpacking build-essential (from .../build-essential_11.5ubuntu2.1_amd64.deb) ...
Selecting previously unselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.18.2-1_amd64.deb) ...
Selecting previously unselected package libalgorithm-diff-perl.
Unpacking libalgorithm-diff-perl (from .../libalgorithm-diff-perl_1.19.02-2_all.deb) ...
Selecting previously unselected package libalgorithm-diff-xs-perl.
Unpacking libalgorithm-diff-xs-perl (from .../libalgorithm-diff-xs-perl_0.04-2build2_amd64.deb) ...
Selecting previously unselected package libalgorithm-merge-perl.
Unpacking libalgorithm-merge-perl (from .../libalgorithm-merge-perl_0.08-2_all.deb) ...
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
dpkg: dependency problems prevent configuration of texlive-base:
 texlive-base depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
dpkg: error processing texlive-base (--configure):
 dependency problems - leaving unconfigured
Setting up curl (7.22.0-3ubuntu4) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          Setting up libconfig-file-perl (1.50-2) ...
Setting up libapt-pkg-perl (0.1.25build2) ...
Setting up liblist-moreutils-perl (0.33-1build1) ...
Setting up libregexp-assemble-perl (0.35-2) ...
Setting up apt-file (2.5.0ubuntu1) ...
The system-wide cache is empty. You may want to run 'apt-file update'
as root to update the cache. You can also run 'apt-file update' as
normal user to use a cache in the user's home directory.
Setting up libdpkg-perl (1.16.1.2ubuntu7) ...
Setting up dpkg-dev (1.16.1.2ubuntu7) ...
Setting up fakeroot (1.18.2-1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode.
Setting up libalgorithm-diff-perl (1.19.02-2) ...
Setting up libalgorithm-diff-xs-perl (0.04-2build2) ...
Setting up libalgorithm-merge-perl (0.08-2) ...
Setting up libstdc++6-4.6-dev (4.6.3-1ubuntu5) ...
Setting up g++-4.6 (4.6.3-1ubuntu5) ...
Setting up g++ (4:4.6.3-1ubuntu5) ...
update-alternatives: using /usr/bin/g++ to provide /usr/bin/c++ (c++) in auto mode.
Setting up build-essential (11.5ubuntu2.1) ...
Errors were encountered while processing:
 tex-common
 texlive-base
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

```
sudo apt-file update
Downloading complete file http://de.archive.ubuntu.com/ubuntu/dists/precise/Contents-amd64.gz
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
 10 21.2M   10 2206k    0     0  23696      0  0:15:38  0:01:35  0:14:03 68316
curl: (18) transfer closed with 19972859 bytes remaining to read
Download of http://de.archive.ubuntu.com/ubuntu/dists/precise/Contents-amd64.gz failed
Command exited with code 18
Downloading complete file http://de.archive.ubuntu.com/ubuntu/dists/precise-updates/Contents-amd64.gz
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 3990k  100 3990k    0     0  84943      0  0:00:48  0:00:48 --:--:--  246k
Downloading complete file http://de.archive.ubuntu.com/ubuntu/dists/precise/Contents-amd64.gz
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
 39 21.2M   39 8533k    0     0  42834      0  0:08:39  0:03:23  0:05:16 45097
curl: (18) transfer closed with 13493833 bytes remaining to read
Download of http://de.archive.ubuntu.com/ubuntu/dists/precise/Contents-amd64.gz failed
Command exited with code 18
Downloading Index http://de.archive.ubuntu.com/ubuntu/dists/precise-updates/Contents-amd64.diff/Index:
No Index available.
Downloading complete file http://de.archive.ubuntu.com/ubuntu/dists/precise-updates/Contents-amd64.gz
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:--  0:00:05 --:--:--     0
File is up-to-date.
Downloading complete file http://de.archive.ubuntu.com/ubuntu/dists/precise/Contents-amd64.gz
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  1 21.2M    1  219k    0     0   3177      0  1:56:37  0:01:10  1:55:27 28271
curl: (18) transfer closed with 22006830 bytes remaining to read
Download of http://de.archive.ubuntu.com/ubuntu/dists/precise/Contents-amd64.gz failed
Command exited with code 18
Downloading Index http://de.archive.ubuntu.com/ubuntu/dists/precise-updates/Contents-amd64.diff/Index:
No Index available.
Downloading complete file http://de.archive.ubuntu.com/ubuntu/dists/precise-updates/Contents-amd64.gz
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:--  0:00:01 --:--:--     0
File is up-to-date.
Downloading complete file http://security.ubuntu.com/ubuntu/dists/precise-security/Contents-amd64.gz
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 2667k  100 2667k    0     0  24976      0  0:01:49  0:01:49 --:--:--  143k
Downloading Index http://security.ubuntu.com/ubuntu/dists/precise-security/Contents-amd64.diff/Index:
No Index available.
Downloading complete file http://security.ubuntu.com/ubuntu/dists/precise-security/Contents-amd64.gz
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:--  0:00:08 --:--:--     0
File is up-to-date.
Downloading Index http://security.ubuntu.com/ubuntu/dists/precise-security/Contents-amd64.diff/Index:
No Index available.
Downloading complete file http://security.ubuntu.com/ubuntu/dists/precise-security/Contents-amd64.gz
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0
File is up-to-date.
Ignoring source without Contents File:
  http://archive.canonical.com/ubuntu/dists/precise/Contents-amd64.gz
Ignoring source without Contents File:
  http://extras.ubuntu.com/ubuntu/dists/precise/Contents-amd64.gz
Downloading complete file http://de.archive.ubuntu.com/ubuntu/dists/precise-proposed/Contents-amd64.gz
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  317k  100  317k    0     0  69635      0  0:00:04  0:00:04 --:--:-- 81726
Ignoring source without Contents File:
  http://dl.google.com/linux/chrome/deb/dists/stable/Contents-amd64.gz
bekirsalgin@bekirsalgin:~$ apt-file search /etc/texmf/texmf.d/05TeXMF.cnf

```

---

### Post by Bashing-om on 2012-11-18
and apt-file search gives no result ?

If so, I am really at a loss presently.

[INDENT]try'n to keep afloat ==> BDQ

[/INDENT]

---

### Post by bekirs on 2012-11-18
Could it be helpful to install TeXLive from [http://www.tug.org]("http://www.tug.org")?

---

### Post by Bashing-om on 2012-11-18
I may be in error, But I do not think you can install another version of texworks without removing the current one...

we still go round and round trying to remove and or (re)install that sucker, over a config file ?
[INDENT]awaiting more knowledgeable input ==> BDQ

[/INDENT]

---

### Post by bekirs on 2012-11-18
I suggest to install TeXLive (the binaries?), not the TeXWorks. What do you think?

---

### Post by Bashing-om on 2012-11-18
well... might be a possibility, if what you have in mind is to extract that missing config file, in theory, should work. (best if the versions are the same) I am interested in participating in the process.
Just be aware we have no confirmation that the 05TeXMF.cnf config file does belong in the /etc/ directory...but one error definitely points that way.

[INDENT]swim 'till we make butter ! ==> BDQ

[/INDENT]

---

### Post by bekirs on 2012-11-19
Hi,

the problem seems to be solved but I don't know how. Before I started this thread, the installation of TeXworks from the repository was reporting some errors but it was anyhow possible to reach TeXworks under "Applications Menu" and also to open it. However, when I was attempting to compile a ".tex" file, some missing configuration packages were reported.
 
Today I tried to compile the same file and noticed that the error message is different, i.e. it said to properly install TeXLive files or to point the folder (from the "Preferences") where the files exist. 
Therefore, I've downloaded and installed TeXLive as explained in [http://www.tug.org/texlive/quickinstall.html]("http://www.tug.org/texlive/quickinstall.html") . The output of the compilation was the same. 

At the end, I changed the folder information from the "Preferences", and it started to work properly.

I don't know whether you recommend any other command for checking the proper installation of the software, but I'm already satisfied with the output.

Thanks a lot for your help!

---

### Post by Bashing-om on 2012-11-19
That is great that the application now works (that is the important thing) !

Linux is smart, the longer I am associated with this operating system the more impressed I become.
Perhaps (hindsight) the issue was but a pointer to the required file ? <file in brain for future reference>.

In any event I am glad for you. 

Please mark this thread as "solved" from the thread tools option at top of post.
[INDENT][INDENT]high regards <== BDQ

[/INDENT][/INDENT]

---

