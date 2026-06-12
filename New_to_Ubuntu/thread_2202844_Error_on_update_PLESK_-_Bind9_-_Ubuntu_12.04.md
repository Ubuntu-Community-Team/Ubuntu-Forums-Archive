---
title: "Error on update PLESK - Bind9 - Ubuntu 12.04"
date: 2014-01-31
forum: New to Ubuntu
---

### Post by enio-san on 2014-01-31
Hi,
Hope anyone can help me.
I have a Cloud Server set with Ubuntu 12.04, and Plesk 11.5. Regular updates come up every once in a while. But this morning, it reported an issue related to BIND9 not starting or something. I clicked on REPAIR on Plesk control panel (I guess I shouldnt have done that) and another error came up.

Here is the first LOG:

>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
Execution failed.
Command: autoinstaller
Arguments: Array
(
    [0] => --select-product-id
    [1] => plesk
    [2] => --select-release-current
    [3] => --upgrade-installed-components
    [4] => --include-components-from-class
    [5] => vendor=parallels
    [6] => --include-components-from-class
    [7] => patched
)

Details: File downloading products.inf3: 100% was finished.
File downloading plesk.inf3: 12%..26%..34%..41%..51%..63%..70%..84%..92%..100% was finished.
File downloading ppsmbe.inf3: 100% was finished.
File downloading sitebuilder.inf3: 100% was finished.
File downloading sso.inf3: 100% was finished.
File downloading setemplates.inf3: 100% was finished.
File downloading pp-sitebuilder.inf3: 25%..37%..66%..71%..99%..100% was finished.
File downloading billing.inf3: 14%..22%..38%..41%..58%..74%..91%..100% was finished.
File downloading mysql.inf3: 100% was finished.
File downloading apache.inf3: 100% was finished.
File downloading nginx.inf3: 100% was finished.
Checking for installed packages... 
File downloading PSA_11.5.30/plesk-11.5.30-ubt12.04-x86_64.inf3: 12%..24%..53%..70%..100% was finished.
File downloading PSA_11.5.30/plesk-patches-11.5.30-ubt12.04-x86_64.inf3: 24%..53%..70%..99%..100% was finished.
File downloading SITEBUILDER_11.5.10/sitebuilder-11.5.10-deball-all.inf3: 100% was finished.
File downloading BILLING_11.5.30/billing-11.5.30-deball-all.inf3: 100% was finished.
File downloading NGINX_1.5.0/nginx-1.5.0-ubt12.04-x86_64.inf3: 100% was finished.
Synchronizing the Debian APT package index files...
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise Release.gpg
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]
Get:2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates Release.gpg [198 B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports Release.gpg
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise Release
Get:3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates Release [49.6 kB]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe TranslationIndex
Get:5 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main Sources [451 kB]
Get:6 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted Sources [7642 B]
Get:7 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe Sources [102 kB]
Get:8 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse Sources [8486 B]
Get:9 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main amd64 Packages [745 kB]
Get:10 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted amd64 Packages [12.5 kB]
Get:11 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe amd64 Packages [231 kB]
Get:12 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse amd64 Packages [14.2 kB]
Get:13 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main i386 Packages [769 kB]
Get:14 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted i386 Packages [12.5 kB]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [96.8 kB]
Get:16 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe i386 Packages [236 kB]
Get:17 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse i386 Packages [14.4 kB]
Get:18 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main TranslationIndex [3564 B]
Get:19 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse TranslationIndex [2605 B]
Get:20 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted TranslationIndex [2461 B]
Get:21 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe TranslationIndex [2850 B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe Translation-en
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [2494 B]
Get:23 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [30.9 kB]
Get:24 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [1797 B]
Get:25 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages [357 kB]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe Translation-en
Get:26 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages [4627 B]
Get:27 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages [90.5 kB]
Get:28 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages [2454 B]
Get:29 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [377 kB]
Get:30 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [4620 B]
Get:31 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [94.7 kB]
Get:32 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [2650 B]
Get:33 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex [74 B]
Get:34 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex [72 B]
Get:35 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex [72 B]
Get:36 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex [73 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en
Ign [http://autoinstall.plesk.com](http://autoinstall.plesk.com) precise Release.gpg
Ign [http://autoinstall.plesk.com](http://autoinstall.plesk.com) all Release.gpg
Ign [http://autoinstall.plesk.com](http://autoinstall.plesk.com) all Release.gpg
Ign [http://autoinstall.plesk.com](http://autoinstall.plesk.com) precise Release
Ign [http://autoinstall.plesk.com](http://autoinstall.plesk.com) all Release
Ign [http://autoinstall.plesk.com](http://autoinstall.plesk.com) all Release
Get:37 [http://autoinstall.plesk.com](http://autoinstall.plesk.com) precise/all amd64 Packages [31.8 kB]
Get:38 [http://autoinstall.plesk.com](http://autoinstall.plesk.com) precise/all i386 Packages [31.7 kB]
Ign [http://autoinstall.plesk.com](http://autoinstall.plesk.com) precise/all TranslationIndex
Ign [http://autoinstall.plesk.com](http://autoinstall.plesk.com) all/all TranslationIndex
Ign [http://autoinstall.plesk.com](http://autoinstall.plesk.com) all/all TranslationIndex
Get:39 [http://autoinstall.plesk.com](http://autoinstall.plesk.com) all/all amd64 Packages [913 B]
Get:40 [http://autoinstall.plesk.com](http://autoinstall.plesk.com) all/all i386 Packages [913 B]
Get:41 [http://autoinstall.plesk.com](http://autoinstall.plesk.com) all/all amd64 Packages [770 B]
Get:42 [http://autoinstall.plesk.com](http://autoinstall.plesk.com) all/all i386 Packages [770 B]
Ign [http://autoinstall.plesk.com](http://autoinstall.plesk.com) precise/all Translation-en
Ign [http://autoinstall.plesk.com](http://autoinstall.plesk.com) all/all Translation-en
Ign [http://autoinstall.plesk.com](http://autoinstall.plesk.com) all/all Translation-en
Fetched 3847 kB in 3min 33s (18.0 kB/s)
Reading package lists...
Warning: not connected 'universe' repository section
Warning: not connected 'multiverse' repository section
Detecting installed product components.
Gathering information about installed license key...
Checking whether the package dependencies are resolved.
Following amount of diskpace required in directories:
/opt: 1200.00 Mb.
Total required: 1200.00 Mb, available 32728.00 Mb.

Installing packages
Reading package lists...
Building dependency tree...
Reading state information...
bind9 is already the newest version.
The following packages will be upgraded:
  libapache2-mod-fcgid-psa
1 upgraded, 0 newly installed, 0 to remove and 24 not upgraded.
1 not fully installed or removed.
Need to get 61.5 kB of archives.
After this operation, 0 B of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  libapache2-mod-fcgid-psa
Authentication warning overridden.
Get:1 [http://autoinstall.plesk.com/ubuntu/PSA_11.5.30/](http://autoinstall.plesk.com/ubuntu/PSA_11.5.30/) precise/all libapache2-mod-fcgid-psa amd64 2.3.9-14012812 [61.5 kB]
Fetched 61.5 kB in 0s (180 kB/s)
(Reading database ... 179473 files and directories currently installed.)
Preparing to replace libapache2-mod-fcgid-psa 2.3.7-13012809 (using .../libapache2-mod-fcgid-psa_2.3.9-14012812_amd64.deb) ...
Unpacking replacement libapache2-mod-fcgid-psa ...
Setting up bind9 (1:9.8.1.dfsg.P1-4ubuntu0.8) ...
 * Starting domain name service... bind9
   ...fail!
invoke-rc.d: initscript bind9, action "start" failed.
Setting up libapache2-mod-fcgid-psa (2.3.9-14012812) ...
dpkg: error processing bind9 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 bind9
E: Sub-process /usr/bin/dpkg returned an error code (1)
Synchronizing the Debian APT package index files...

ERROR: An error occurred on attempt to install packages.
Attention! Your software might be inoperable.
Please, contact product technical support.
<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<

Then, after hitting 'repair' on plesk, it returned the following, which looks pretty much the same, but a different version on libapache2-mod-fcgid-psa_xxx

>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
Execution failed.
Command: autoinstaller
Arguments: Array
(
    [0] => --select-product-id
    [1] => plesk
    [2] => --select-release-current
    [3] => --upgrade-installed-components
    [4] => --include-components-from-class
    [5] => vendor=parallels
    [6] => --include-components-from-class
    [7] => patched
)

Details: File downloading products.inf3: 100% was finished.
File downloading plesk.inf3: 12%..26%..34%..41%..51%..63%..70%..84%..92%..100% was finished.
File downloading ppsmbe.inf3: 100% was finished.
File downloading sitebuilder.inf3: 100% was finished.
File downloading sso.inf3: 100% was finished.
File downloading setemplates.inf3: 100% was finished.
File downloading pp-sitebuilder.inf3: 25%..37%..66%..71%..99%..100% was finished.
File downloading billing.inf3: 14%..22%..38%..41%..58%..74%..91%..100% was finished.
File downloading mysql.inf3: 100% was finished.
File downloading apache.inf3: 100% was finished.
File downloading nginx.inf3: 100% was finished.
Checking for installed packages... 
File downloading PSA_11.5.30/plesk-11.5.30-ubt12.04-x86_64.inf3: 12%..24%..53%..70%..100% was finished.
File downloading PSA_11.5.30/plesk-patches-11.5.30-ubt12.04-x86_64.inf3: 24%..53%..70%..99%..100% was finished.
File downloading SITEBUILDER_11.5.10/sitebuilder-11.5.10-deball-all.inf3: 100% was finished.
File downloading BILLING_11.5.30/billing-11.5.30-deball-all.inf3: 100% was finished.
File downloading NGINX_1.5.0/nginx-1.5.0-ubt12.04-x86_64.inf3: 100% was finished.
Synchronizing the Debian APT package index files...
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise Release.gpg
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]
Get:2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates Release.gpg [198 B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports Release.gpg
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise Release
Get:3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates Release [49.6 kB]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe TranslationIndex
Get:5 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main Sources [451 kB]
Get:6 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted Sources [7642 B]
Get:7 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe Sources [102 kB]
Get:8 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse Sources [8486 B]
Get:9 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main amd64 Packages [745 kB]
Get:10 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted amd64 Packages [12.5 kB]
Get:11 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe amd64 Packages [231 kB]
Get:12 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse amd64 Packages [14.2 kB]
Get:13 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main i386 Packages [769 kB]
Get:14 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted i386 Packages [12.5 kB]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [96.8 kB]
Get:16 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe i386 Packages [236 kB]
Get:17 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse i386 Packages [14.4 kB]
Get:18 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main TranslationIndex [3564 B]
Get:19 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse TranslationIndex [2605 B]
Get:20 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted TranslationIndex [2461 B]
Get:21 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe TranslationIndex [2850 B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe Translation-en
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [2494 B]
Get:23 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [30.9 kB]
Get:24 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [1797 B]
Get:25 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages [357 kB]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe Translation-en
Get:26 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages [4627 B]
Get:27 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages [90.5 kB]
Get:28 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages [2454 B]
Get:29 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [377 kB]
Get:30 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [4620 B]
Get:31 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [94.7 kB]
Get:32 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [2650 B]
Get:33 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex [74 B]
Get:34 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex [72 B]
Get:35 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex [72 B]
Get:36 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex [73 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en
Ign [http://autoinstall.plesk.com](http://autoinstall.plesk.com) precise Release.gpg
Ign [http://autoinstall.plesk.com](http://autoinstall.plesk.com) all Release.gpg
Ign [http://autoinstall.plesk.com](http://autoinstall.plesk.com) all Release.gpg
Ign [http://autoinstall.plesk.com](http://autoinstall.plesk.com) precise Release
Ign [http://autoinstall.plesk.com](http://autoinstall.plesk.com) all Release
Ign [http://autoinstall.plesk.com](http://autoinstall.plesk.com) all Release
Get:37 [http://autoinstall.plesk.com](http://autoinstall.plesk.com) precise/all amd64 Packages [31.8 kB]
Get:38 [http://autoinstall.plesk.com](http://autoinstall.plesk.com) precise/all i386 Packages [31.7 kB]
Ign [http://autoinstall.plesk.com](http://autoinstall.plesk.com) precise/all TranslationIndex
Ign [http://autoinstall.plesk.com](http://autoinstall.plesk.com) all/all TranslationIndex
Ign [http://autoinstall.plesk.com](http://autoinstall.plesk.com) all/all TranslationIndex
Get:39 [http://autoinstall.plesk.com](http://autoinstall.plesk.com) all/all amd64 Packages [913 B]
Get:40 [http://autoinstall.plesk.com](http://autoinstall.plesk.com) all/all i386 Packages [913 B]
Get:41 [http://autoinstall.plesk.com](http://autoinstall.plesk.com) all/all amd64 Packages [770 B]
Get:42 [http://autoinstall.plesk.com](http://autoinstall.plesk.com) all/all i386 Packages [770 B]
Ign [http://autoinstall.plesk.com](http://autoinstall.plesk.com) precise/all Translation-en
Ign [http://autoinstall.plesk.com](http://autoinstall.plesk.com) all/all Translation-en
Ign [http://autoinstall.plesk.com](http://autoinstall.plesk.com) all/all Translation-en
Fetched 3847 kB in 3min 33s (18.0 kB/s)
Reading package lists...
Warning: not connected 'universe' repository section
Warning: not connected 'multiverse' repository section
Detecting installed product components.
Gathering information about installed license key...
Checking whether the package dependencies are resolved.
Following amount of diskpace required in directories:
/opt: 1200.00 Mb.
Total required: 1200.00 Mb, available 32728.00 Mb.

Installing packages
Reading package lists...
Building dependency tree...
Reading state information...
bind9 is already the newest version.
The following packages will be upgraded:
  libapache2-mod-fcgid-psa
1 upgraded, 0 newly installed, 0 to remove and 24 not upgraded.
1 not fully installed or removed.
Need to get 61.5 kB of archives.
After this operation, 0 B of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  libapache2-mod-fcgid-psa
Authentication warning overridden.
Get:1 [http://autoinstall.plesk.com/ubuntu/PSA_11.5.30/](http://autoinstall.plesk.com/ubuntu/PSA_11.5.30/) precise/all libapache2-mod-fcgid-psa amd64 2.3.9-14012812 [61.5 kB]
Fetched 61.5 kB in 0s (180 kB/s)
(Reading database ... 179473 files and directories currently installed.)
Preparing to replace libapache2-mod-fcgid-psa 2.3.7-13012809 (using .../libapache2-mod-fcgid-psa_2.3.9-14012812_amd64.deb) ...
Unpacking replacement libapache2-mod-fcgid-psa ...
Setting up bind9 (1:9.8.1.dfsg.P1-4ubuntu0.8) ...
 * Starting domain name service... bind9
   ...fail!
invoke-rc.d: initscript bind9, action "start" failed.
Setting up libapache2-mod-fcgid-psa (2.3.9-14012812) ...
dpkg: error processing bind9 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 bind9
E: Sub-process /usr/bin/dpkg returned an error code (1)
Synchronizing the Debian APT package index files...

ERROR: An error occurred on attempt to install packages.
Attention! Your software might be inoperable.
Please, contact product technical support.
<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<

---

