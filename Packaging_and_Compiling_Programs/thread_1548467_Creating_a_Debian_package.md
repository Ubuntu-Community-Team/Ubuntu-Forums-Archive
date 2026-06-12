---
title: "Creating a Debian package"
date: 2010-08-08
forum: Packaging and Compiling Programs
---

### Post by GameFrame on 2010-08-08
Hi. I am Debian user but never used Ubuntu. However I know it uses exactly the same package management as Debian does.

I have recently released a Linux Proxy Checker named NiX (Freeware). At the moment I am working on .deb package for it.  It´s first time I try to create such a package. Debian package (.deb) should work also in Ubuntu what I am aware of.

Here´s what I have got done so far:

> 
Package: nix-proxychecker
Version: 1.3.0
Section: web 
Priority: optional
Architecture: all
Essential: no
Depends: php5-cli,geoip-bin
Pre-Depends: coreutils,gawk,grep,sed
Installed-Size: 404
Maintainer: Tapio Niemela [nix@myproxylists.com]
Provides: nix-proxychecker
Description: NiX - Proxy Checker - Supported proxies: HTTP(S) CONNECT, Socks 4, Socks 4a, Socks 5 - Fully multi-threaded and more.
Homepage: [http://myproxylists.com/](http://myproxylists.com/)
How do I implement "debian preinst script" in to my .deb package? It requires one PHP extension which I would like to get copied in to PHP´s "extension_dir" automatically via script but just need a small guidance how to make my package execute that script, let´s say "nixinstall.sh" upon installation?

Thanks

---

### Post by Iowan on 2010-08-08
Moved to Packaging and Compiling Programs

---

### Post by SevenMachines on 2010-08-09
If you're using debhelper to package then you can just put maintainer scripts in the debian directory and they'll be automatically installed. For instance
debian/nix-proxychecker.preinst
will be installed to
/var/lib/dpkg/info
and run during installation

---

### Post by GameFrame on 2010-08-10
> **SevenMachines said:**
> If you're using debhelper to package then you can just put maintainer scripts in the debian directory and they'll be automatically installed. For instance
debian/nix-proxychecker.preinst
will be installed to
/var/lib/dpkg/info
and run during installation

I think I have got it now. The place is is the same where I already have put the above "control" file.

When I have got my .deb package done and verified, does anyone know how to supply that package so that checker would be possibly available in official distribution.

The tool itself really is that good.

---

### Post by SevenMachines on 2010-08-10
* See the [REVU process for Ubuntu,]("https://wiki.edubuntu.org/MOTU/Packages/REVU") you might want to check the [REVU Checklist]("https://wiki.ubuntu.com/MOTU/Packages/REVU/CheckList") too. 

* If you have a launchpad page you might want to [upload it to a ppa first]("https://help.launchpad.net/Packaging/PPA/Uploading"), this has the benefit of people being able to use it easily before its reached the main repositories. 

* Try irc #ubuntu-motu and see if theres anyone free to look over your packaging and offer advice, the process is quicker if you can make any needed changes to the packaging early. 

* Also remember, if you can get it uploaded to debian then ubuntu will get it when it syncs, and so will all of debian and its downstreams

---

### Post by GameFrame on 2010-08-10
> **SevenMachines said:**
> * See the [REVU process for Ubuntu,]("https://wiki.edubuntu.org/MOTU/Packages/REVU") you might want to check the [REVU Checklist]("https://wiki.ubuntu.com/MOTU/Packages/REVU/CheckList") too. 

* If you have a launchpad page you might want to [upload it to a ppa first]("https://help.launchpad.net/Packaging/PPA/Uploading"), this has the benefit of people being able to use it easily before its reached the main repositories. 

* Try irc #ubuntu-motu and see if theres anyone free to look over your packaging and offer advice, the process is quicker if you can make any needed changes to the packaging early. 

* Also remember, if you can get it uploaded to debian then ubuntu will get it when it syncs, and so will all of debian and its downstreams

Thanks for all help. As usually, I want to try these things myself out and if I will end up with no solution, then I will ask help. The best way to learn new things.

---

### Post by KdotJ on 2010-08-10
This is exactly the thread I was looking for :D
I too wanted to have a small bash script that was executed during the installation of the .deb file

---

### Post by GameFrame on 2010-08-10
> **KdotJ said:**
> This is exactly the thread I was looking for :D
I too wanted to have a small bash script that was executed during the installation of the .deb file

Cheers. My preinst etc. are working. Expect a Debian/Ubuntu package of NiX soon. I am finally happy that I can share some of my knowledge to other Linux users. So many nice tools included in Linux distributions already.

---

