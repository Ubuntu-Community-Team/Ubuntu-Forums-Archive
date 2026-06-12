---
title: "ubuntu 12.04 is not properly connecting to wired network"
date: 2013-06-04
forum: New to Ubuntu
---

### Post by choklo on 2013-06-04
i have installed ubuntu 12.04 at a pc that was going to be thrown away. It is pluged to an institutional wired network (at work). Now it runs very good and even firefox connects to the internet nicely. But somethings went wrong during install, the installer was not able to connect to the internet so it went further in offline modus. The result is an imperfect language setting (german was set, but the desktop communicates with me in english while the terminal in german). Most important, the software repository is empty. "sudo apt-get update" gave the following:

Ign cdrom://Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release i386 (20130213) precise InRelease
Ign cdrom://Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release i386 (20130213) precise/main TranslationIndex
Ign cdrom://Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release i386 (20130213) precise/restricted TranslationIndex
Ign cdrom://Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release i386 (20130213) precise/main Translation-de_DE
Ign cdrom://Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release i386 (20130213) precise/main Translation-de
Ign cdrom://Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release i386 (20130213) precise/main Translation-en
Ign cdrom://Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release i386 (20130213) precise/restricted Translation-de_DE
Ign cdrom://Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release i386 (20130213) precise/restricted Translation-de
Ign cdrom://Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release i386 (20130213) precise/restricted Translation-en
Hole:1 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease
Hole:2 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease
Hole:3 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg
Hole:4 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg
Hole:5 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release
E: GPG-Fehler: [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release: Die folgenden Signaturen waren ungültig: NODATA 1 NODATA 2

Translating part of the last line: "the following signatures were not valid". Downloading software and installing it via software center, does not work either. Please advice me (a total beginner on linux/networking) how to solve this.

liebe grüße!
choklo

---

