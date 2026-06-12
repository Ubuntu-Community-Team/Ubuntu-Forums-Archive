---
title: "Loads of apt-get errors ... :("
date: 2006-02-22
forum: Repositories &amp; Backports
---

### Post by Watcher on 2006-02-22
Right, I've tried a lot of different sources.list (even tried the sources.list-generator) files but I always seem to get loads of errors which is not fun :(

> # Automatically generated sources.list
# [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse

# Ubuntu backports project (packages, GPG key: 437D05B5)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

# Ubuntu backports project (sources, GPG key: 437D05B5)
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

# kubuntu.org packages for the latest KDE version (packages, GPG key: DD4D5088)
deb [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest) breezy main

# kubuntu.org packages for the latest KDE version (sources, GPG key: DD4D5088)
deb-src [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest) breezy main

# kubuntu.org packages for the latest Koffice version (packages, GPG key: DD4D5088)
deb [http://kubuntu.org/packages/koffice-latest](http://kubuntu.org/packages/koffice-latest) breezy main

# kubuntu.org packages for the latest Koffice version (sources, GPG key: DD4D5088)
deb-src [http://kubuntu.org/packages/koffice-latest](http://kubuntu.org/packages/koffice-latest) breezy main

# kubuntu.org packages for the latest amaroK version (packages, GPG key: DD4D5088)
deb [http://kubuntu.org/packages/amarok-latest](http://kubuntu.org/packages/amarok-latest) breezy main

# kubuntu.org packages for the latest amaroK version (sources, GPG key: DD4D5088)
deb-src [http://kubuntu.org/packages/amarok-latest](http://kubuntu.org/packages/amarok-latest) breezy main


And this is the output I get when doing "sudo apt-get update":
> bernard@Hyphomicrobium:/etc/apt$ sudo apt-get update
Ophalen:1 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Ophalen:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Ophalen:3 [http://kubuntu.org](http://kubuntu.org) breezy Release.gpg [189B]
Genegeerd [http://kubuntu.org](http://kubuntu.org) breezy Release.gpg
Ophalen:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release.gpg [189B]
Ophalen:5 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release [27,0kB]
Ophalen:6 [http://kubuntu.org](http://kubuntu.org) breezy Release.gpg [189B]
Ophalen:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release.gpg [189B]
Ophalen:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release [30,9kB]
Ophalen:9 [http://kubuntu.org](http://kubuntu.org) breezy Release [2327B]
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Genegeerd [http://kubuntu.org](http://kubuntu.org) breezy Release
Genegeerd [http://kubuntu.org](http://kubuntu.org) breezy Release
Ophalen:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release [30,9kB]
Ophalen:11 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages [4458B]
Genegeerd [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Ophalen:12 [http://kubuntu.org](http://kubuntu.org) breezy Release [2330B]
Genegeerd [http://kubuntu.org](http://kubuntu.org) breezy Release
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Ophalen:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release [19,6kB]
Genegeerd [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release
Ophalen:14 [http://kubuntu.org](http://kubuntu.org) breezy/main Packages [88,2kB]
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Ophalen:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages [585kB]
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages
Ophalen:16 [http://kubuntu.org](http://kubuntu.org) breezy/main Sources [13,2kB]
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Sources
Ophalen:17 [http://kubuntu.org](http://kubuntu.org) breezy/main Packages [7779B]
Ophalen:18 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages [4055B]
58% [18 Packages gzip 0] [15 Packages 269916/585kB 46%] [Wachtend op de kopteksten]
gzip: stdin: not in gzip format
Fout [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
  Subproces gzip gaf de foutcode 1 terug
Ophalen:19 [http://kubuntu.org](http://kubuntu.org) breezy/main Sources [1001B]
Ophalen:20 [http://kubuntu.org](http://kubuntu.org) breezy/main Packages [3032B]
Ophalen:21 [http://kubuntu.org](http://kubuntu.org) breezy/main Sources [725B]
Genegeerd [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
Ophalen:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages [5061B]
Genegeerd [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
Ophalen:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources [232kB]
Genegeerd [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources
Ophalen:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Sources [1454B]
Ophalen:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages [2304kB]
Genegeerd [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Ophalen:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages [91,6kB]
Genegeerd [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
Ophalen:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources [915kB]
Genegeerd [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
Ophalen:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Sources [46,9kB]
Genegeerd [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Sources
Ophalen:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages [31,3kB]
Genegeerd [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages
Ophalen:30 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages [14B]
4% [30 Packages bzip2 0] [Er wordt verbinding gemaakt met archive.ubuntu.com (82.211.81.182)]               325kB/s 49710d 6h28m3s
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Fout [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages
  Subproces bzip2 gaf de foutcode 2 terug
Ophalen:31 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources [15,8kB]
Genegeerd [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources
Ophalen:32 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources [14B]
Ophalen:33 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/universe Packages [8929B]
Genegeerd [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/universe Packages
Ophalen:34 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/multiverse Packages [708B]
Genegeerd [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/multiverse Packages
Ophalen:35 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/universe Sources [1019B]
Ophalen:36 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/multiverse Sources [365B]
Genegeerd [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/multiverse Sources
Ophalen:37 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages [14,0kB]
Ophalen:38 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages [14B]
Ophalen:39 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages [26,1kB]
Ophalen:40 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages [1353B]
Genegeerd [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages
Ophalen:41 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Sources [5185B]
Genegeerd [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Sources
Ophalen:42 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Sources [14B]
5% [42 Sources bzip2 0] [Er wordt verbinding gemaakt met archive.ubuntu.com (82.211.81.182)]                325kB/s 49710d 6h28m3s
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Fout [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Sources
  Subproces bzip2 gaf de foutcode 2 terug
Ophalen:43 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Sources [10,2kB]
Ophalen:44 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Sources [701B]
Ophalen:45 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages [767kB]
19% [45 Packages gzip 0] [Er wordt verbinding gemaakt met archive.ubuntu.com (82.211.81.182)]               325kB/s 49710d 6h28m3s
gzip: stdin: not in gzip format
Fout [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
  Subproces gzip gaf de foutcode 1 terug
Ophalen:46 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages [4735B]
19% [Er wordt verbinding gemaakt met archive.ubuntu.com (82.211.81.182)]                                    325kB/s 49710d 6h28m3s
gzip: stdin: not in gzip format
Fout [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
  Subproces gzip gaf de foutcode 1 terug
Ophalen:47 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources [305kB]
23% [Er wordt verbinding gemaakt met archive.ubuntu.com (82.211.81.182)]                                    325kB/s 49710d 6h28m3s
gzip: stdin: not in gzip format
Fout [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources
  Subproces gzip gaf de foutcode 1 terug
Ophalen:48 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages [3028kB]
Fout [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
  Fout bij het lezen van de server - read (104 Verbinding door partner opnieuw ingesteld)
Ophalen:49 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages [116kB]
16% [49 Packages gzip 0] [Er wordt verbinding gemaakt met archive.ubuntu.com (82.211.81.182)]                          292kB/s 24s
gzip: stdin: not in gzip format
Fout [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
  Subproces gzip gaf de foutcode 1 terug
Ophalen:50 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources [1223kB]
Fout [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
  Fout bij het lezen van de server - read (104 Verbinding door partner opnieuw ingesteld)
Ophalen:51 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Sources [58,0kB]
15% [51 Sources gzip 0] [Wachtend op de kopteksten]                                                                    292kB/s 29s
gzip: stdin: not in gzip format
Fout [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Sources
  Subproces gzip gaf de foutcode 1 terug
Ophalen:52 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages [38,1kB]
Fout [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages
  Fout bij het lezen van de server - read (104 Verbinding door partner opnieuw ingesteld)
Ophalen:53 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources [19,0kB]
Fout [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources
  Fout bij het lezen van de server - read (104 Verbinding door partner opnieuw ingesteld)
Ophalen:54 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/universe Packages [9214B]
15% [Er wordt verbinding gemaakt met archive.ubuntu.com (82.211.81.182)]                                               292kB/s 29s
gzip: stdin: not in gzip format
Fout [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/universe Packages
  Subproces gzip gaf de foutcode 1 terug
Ophalen:55 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/multiverse Packages [610B]
Ophalen:56 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/multiverse Sources [319B]
Ophalen:57 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages [1241B]
15% [Er wordt verbinding gemaakt met archive.ubuntu.com (82.211.81.182)]                                               292kB/s 29s
gzip: stdin: not in gzip format
Fout [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages
  Subproces gzip gaf de foutcode 1 terug
Ophalen:58 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Sources [5219B]
15% [Bezig]                                                                                                            292kB/s 29s
gzip: stdin: not in gzip format
Fout [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Sources
  Subproces gzip gaf de foutcode 1 terug
665kB opgehaald in 28s (23,2kB/s)
Ophalen van [http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz) Subproces gzip gaf de foutcode 1 terug is mislukt
Ophalen van [http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz) Subproces bzip2 gaf de foutcode 2 terug is mislukt
Ophalen van [http://archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/source/Sources.gz) Subproces bzip2 gaf de foutcode 2 terug is mislukt
Ophalen van [http://archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz) Subproces gzip gaf de foutcode 1 terug is mislukt
Ophalen van [http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz) Subproces gzip gaf de foutcode 1 terug is mislukt
Ophalen van [http://archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz) Subproces gzip gaf de foutcode 1 terug is mislukt
Ophalen van [http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz) Fout bij het lezen van de server - read (104 Verbinding door partner opnieuw ingesteld) is mislukt
Ophalen van [http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz) Subproces gzip gaf de foutcode 1 terug is mislukt
Ophalen van [http://archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz) Fout bij het lezen van de server - read (104 Verbinding door partner opnieuw ingesteld) is mislukt
Ophalen van [http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/source/Sources.gz) Subproces gzip gaf de foutcode 1 terug is mislukt
Ophalen van [http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz) Fout bij het lezen van de server - read (104 Verbinding door partner opnieuw ingesteld) is mislukt
Ophalen van [http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz) Fout bij het lezen van de server - read (104 Verbinding door partner opnieuw ingesteld) is mislukt
Ophalen van [http://archive.ubuntu.com/ubuntu/dists/breezy-updates/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/universe/binary-i386/Packages.gz) Subproces gzip gaf de foutcode 1 terug is mislukt
Ophalen van [http://archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz) Subproces gzip gaf de foutcode 1 terug is mislukt
Ophalen van [http://archive.ubuntu.com/ubuntu/dists/breezy-backports/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/main/source/Sources.gz) Subproces gzip gaf de foutcode 1 terug is mislukt
Pakketlijsten worden ingelezen... Klaar
W: GPG error: [http://kubuntu.org](http://kubuntu.org) breezy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A506E6D4DD4D5088
W: GPG error: [http://kubuntu.org](http://kubuntu.org) breezy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A506E6D4DD4D5088
W: Kon de status van de bronpakketlijst [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) niet opvragen - stat (2 Onbekend bestand of map)
W: Kon de status van de bronpakketlijst [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) niet opvragen - stat (2 Onbekend bestand of map)
W: Kon de status van de bronpakketlijst [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) niet opvragen - stat (2 Onbekend bestand of map)
W: Kon de status van de bronpakketlijst [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) niet opvragen - stat (2 Onbekend bestand of map)
W: Kon de status van de bronpakketlijst [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) niet opvragen - stat (2 Onbekend bestand of map)
W: Kon de status van de bronpakketlijst [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) niet opvragen - stat (2 Onbekend bestand of map)
W: Kon de status van de bronpakketlijst [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_universe_binary-i386_Packages) niet opvragen - stat (2 Onbekend bestand of map)
W: Kon de status van de bronpakketlijst [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) niet opvragen - stat (2 Onbekend bestand of map)
W: Kon de status van de bronpakketlijst [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) niet opvragen - stat (2 Onbekend bestand of map)
W: Kon de status van de bronpakketlijst [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) niet opvragen - stat (2 Onbekend bestand of map)
W: Kon de status van de bronpakketlijst [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) niet opvragen - stat (2 Onbekend bestand of map)
W: Kon de status van de bronpakketlijst [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) niet opvragen - stat (2 Onbekend bestand of map)
W: Kon de status van de bronpakketlijst [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) niet opvragen - stat (2 Onbekend bestand of map)
W: Kon de status van de bronpakketlijst [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_universe_binary-i386_Packages) niet opvragen - stat (2 Onbekend bestand of map)
W: U kunt misschien 'apt-get update' uitvoeren om deze problemen te verhelpen
E: Ophalen van sommige indexbestanden is mislukt, deze zijn of genegeerd, of er zijn oudere versies van gebruikt.

(sorry it's in dutch :s). As you can see a lot of errors and I would really like to get an error-free sources.list, but as I'm new to Linux I don't really know what to do :s. Any help would be greatly appreciated.

---

### Post by XDevHald on 2006-02-22
Here's my sources.list, just replace **dapper **with **breezy **and you'll be good to go. just apt-get update when you save the sources.list.

Let us know how it goes :)

> ## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

---

### Post by Watcher on 2006-02-23
Still causes some errors (mostly the same as above)

> bernard@Hyphomicrobium:/etc/apt$ sudo apt-get update
Ophalen:1 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Ophalen:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Ophalen:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release.gpg [189B]
Ophalen:4 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release [27,0kB]
Ophalen:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release.gpg [189B]
Geraakt [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Ophalen:6 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages [37,5kB]
Ophalen:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release [30,9kB]
Genegeerd [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release
Ophalen:8 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages [4458B]
Ophalen:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release [19,6kB]
Genegeerd [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release
Ophalen:10 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources [11,8kB]
Genegeerd [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
Ophalen:11 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources [960B]
Ophalen:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages [5061B]
Genegeerd [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
Genegeerd [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources
Geraakt [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Sources
Genegeerd [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Genegeerd [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
Ophalen:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages [31,3kB]
Genegeerd [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages
Ophalen:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages [14B]
Ophalen:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources [15,8kB]
Genegeerd [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources
Ophalen:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources [14B]
Ophalen:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages [14,0kB]
Ophalen:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages [14B]
Genegeerd [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages
Ophalen:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages [26,1kB]
Genegeerd [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages
Ophalen:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages [1353B]
Genegeerd [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages
Ophalen:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Sources [5185B]
Genegeerd [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Sources
Ophalen:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Sources [14B]
Genegeerd [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Sources
Ophalen:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Sources [10,2kB]
Ophalen:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Sources [701B]
Genegeerd [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Sources
Ophalen:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages [767kB]
91% [25 Packages gzip 0] [Wachtend op de kopteksten]
gzip: stdin: not in gzip format
Fout [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
  Subproces gzip gaf de foutcode 1 terug
Ophalen:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages [4735B]
91% [Er wordt verbinding gemaakt met archive.ubuntu.com (82.211.81.182)]
gzip: stdin: not in gzip format
Fout [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
  Subproces gzip gaf de foutcode 1 terug
Ophalen:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources [305kB]
Fout [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources
  Fout bij het lezen van de server - read (104 Verbinding door partner opnieuw ingesteld)Ophalen:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages [3028kB]
91% [Bezig]
gzip: stdin: not in gzip format
Fout [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
  Subproces gzip gaf de foutcode 1 terug
Ophalen:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources [1223kB]
93% [Er wordt verbinding gemaakt met archive.ubuntu.com (82.211.81.182)]
gzip: stdin: not in gzip format
Fout [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
  Subproces gzip gaf de foutcode 1 terug
Ophalen:30 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages [38,1kB]
93% [30 Packages gzip 0] [Er wordt verbinding gemaakt met archive.ubuntu.com (82.211.81.
gzip: stdin: not in gzip format
Fout [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages
  Subproces gzip gaf de foutcode 1 terug
Ophalen:31 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources [19,0kB]
93% [Er wordt verbinding gemaakt met archive.ubuntu.com (82.211.81.182)]
gzip: stdin: not in gzip format
Fout [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources
  Subproces gzip gaf de foutcode 1 terug
Ophalen:32 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages [20B]
Ophalen:33 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages [29,3kB]
93% [Er wordt verbinding gemaakt met archive.ubuntu.com (82.211.81.182)]
gzip: stdin: not in gzip format
Fout [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages
  Subproces gzip gaf de foutcode 1 terug
Ophalen:34 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages [1241B]
Ophalen:35 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Sources [5219B]
93% [Er wordt verbinding gemaakt met archive.ubuntu.com (82.211.81.182)]
gzip: stdin: not in gzip format
Fout [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Sources
  Subproces gzip gaf de foutcode 1 terug
Ophalen:36 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Sources [20B]
Ophalen:37 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Sources [593B]
129kB opgehaald in 5s (25,3kB/s)
Ophalen van [http://archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz) Subproces gzip gaf de foutcode 1 terug is mislukt
Ophalen van [http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz) Subproces gzip gaf de foutcode 1 terug is mislukt
Ophalen van [http://archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz) Fout bij het lezen van de server - read (104 Verbinding door partner opnieuw ingesteld) is mislukt
Ophalen van [http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz) Subproces gzip gaf de foutcode 1 terug is mislukt
Ophalen van [http://archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz) Subproces gzip gaf de foutcode 1 terug is mislukt
Ophalen van [http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz) Subproces gzip gaf de foutcode 1 terug is mislukt
Ophalen van [http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz) Subproces gzip gaf de foutcode 1 terug is mislukt
Ophalen van [http://archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz) Subproces gzip gaf de foutcode 1 terug is mislukt
Ophalen van [http://archive.ubuntu.com/ubuntu/dists/breezy-backports/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/main/source/Sources.gz) Subproces gzip gaf de foutcode 1 terug is mislukt
Pakketlijsten worden ingelezen... Klaar
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Kon de status van de bronpakketlijst [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) niet opvragen - stat (2 Onbekend bestand of map)
W: Kon de status van de bronpakketlijst [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) niet opvragen - stat (2 Onbekend bestand of map)
W: Kon de status van de bronpakketlijst [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) niet opvragen - stat (2 Onbekend bestand of map)
W: Kon de status van de bronpakketlijst [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) niet opvragen - stat (2 Onbekend bestand of map)
W: Kon de status van de bronpakketlijst [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) niet opvragen - stat (2 Onbekend bestand of map)
W: Kon de status van de bronpakketlijst [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) niet opvragen - stat (2 Onbekend bestand of map)
W: U kunt misschien 'apt-get update' uitvoeren om deze problemen te verhelpen
E: Ophalen van sommige indexbestanden is mislukt, deze zijn of genegeerd, of er zijn oudere versies van gebruikt.


As you can see most errors are about gzip returning errorcode 1 or stuff not being in gzip format, also some errors about stat (2 unknown file or directory) which I think is about not being able to find servers ...
So unfortunatly the problem is still not solved :(

---

### Post by Watcher on 2006-03-05
Right, tried changing to the archive servers to [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) and also tried se and fr. But still no go :mad: 

Maybe it comes from being inside my  university LAN (although they say that they don't block that traffic :-k ) (KULeuven, Belgium to be precise) .. ??

If anybody has some more ideas please let me know!

---

### Post by wanger123 on 2006-03-11
Hi there Watcher, try what I said here: [http://www.ubuntuforums.org/showthread.php?p=652997#post652997](http://www.ubuntuforums.org/showthread.php?p=652997#post652997)

change username and password with your **actual **username and password

cheers
wanger

---

