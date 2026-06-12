---
title: "Problem with dpkg-scanpackages (making custom repo)"
date: 2006-05-27
forum: Repositories &amp; Backports
---

### Post by spottraining on 2006-05-27
Hi

I am trying to make my own small repo to my web server, so that I have possible to install different software easy with apt-get. It is about ten different deb files, but what all working fine with Ubuntu. My idea - make all necessary files in my computer and then upload they to web server.

I have found this Howto: [http://www.ubuntuforums.org/showthread.php?t=42862](http://www.ubuntuforums.org/showthread.php?t=42862)

Problem is - that this not working. Main problem right now is, that when I run in this folder, where are my deb files fallowing command, to make Packages.gz file:
```
sudo dpkg-scanpackages . /dev/null | gzip -9c > Packages.gz
```
Then its shows me information from one file:
```
suvi@lapakas:~/ubunturepo$ sudo dpkg-scanpackages . /dev/null | gzip -9c > Packages.gz
Unprocessed text from ./FrostWire-4.10.9-2.i586.deb control file; info:
Package: frostwire
Version: 4.9.11
Section: Networking
Priority: optional
Architecture: all
Essential: no
Depends:
Pre-Depends:
Recommends:
Suggests:
Installed-Size: 16386
Maintainer: Gubatron [gubatron@gmail.com]
Conflicts:
Replaces:
Provides: frostwire
Description: A Truly Free and Open Source Peer to Peer client
             for the Gnutella Network. It's core is based on
             LimeWire. Which needs the Sun Java Runtime Environment
             (minimum version tested is JRE 1.4+)
. / .
suvi@lapakas:~/ubunturepo$

```
and that all. When I then look to Packages.gz file, extract that - this is empty.

Also with apt-get update I see for my server this information:
```
Ign http://myserver.org ubuntu/ Release.gpg
Ign http://myserver.org ubuntu/ Release
Ign http://myserver.org ubuntu/ Packages

```
So this server is ignored.

I have check also Ubuntu Wiki and guide about how to make repo CD, also this:
[http://www.debian.org/doc/manuals/repository-howto/repository-howto](http://www.debian.org/doc/manuals/repository-howto/repository-howto)
But these explain all about big repository, with different arch and versions. I need only my small repo for my personal needs.

Maybe someone can help

---

### Post by ketsugi on 2006-05-27
I would like to second the request for a howto on how to set up and maintain a small repository for Ubuntu Dapper. I'm especially interested in learning how to sign packages with gpg so I can avoid the "Not authenticated" warning.

---

### Post by az on 2006-05-27
[QUOTE=ketsugi]I would like to second the request for a howto on how to set up and maintain a small repository for Ubuntu Dapper. I'm especially interested in learning how to sign packages with gpg so I can avoid the "Not authenticated" warning.[/QUOTE]
wiki.ubuntu.com/AptMoveHowto

---

### Post by spottraining on 2006-05-28
OK

I get dpkg-scanpackages work. I have now problems with my repo and Release file I think.
Previous problem whas with one deb package. I remove this and now its works. What I have make then:

 First I make one folder - ubunturepo, there I but all my deb files. I dont use source files - so all are in one folder.
Then 
```

cd /bin
sudo nano autorepo

```
I enter the following lines into autorepo
```

#!/bin/bash sudo dpkg-scanpackages . /dev/null | gzip -9c > Packages.gz
```
I save the file and make it executable
```

sudo chmod +x autorepo

```
Now - when I have in my ubunturepo folder, then I need only run the command:
```
autorepo
```

Now I need to make Release file. I make this very simple like this:
```
nano Release
```
```

Archive: unstable
Origin: myserver.org
Label: My Ubuntu
Architecture: all

```
So now I have in my folder my deb files, Packages.gz file and Release file. Now I make also GPG
I need to first make my GPG Key, this is simple (guide is there [Ubuntu Wiki](https://wiki.ubuntu.com/GnuPrivacyGuardHowto?action=show&redirect=GPGKey#head-29ca86ddfcea8dd78b5c5fa9144f9f695035bb24))
with fallowing command:
```
gpg --gen-key
```
Then I make my Release.gpg key
```
gpg -bao Release.gpg Release
```
and now I make public.key file:
```
gpg --export -a "MyGPGName" > public.key
```
This name I give, when I generate my GPG Key.

Now I updated all my files, what is in folder ubunturepo to my server. There is in http server, folder ubuntu. I add to the sources list lines:
```

#My Ubuntu repo
deb http://myserver.org/ubuntu /

```

Now - when I need to sign my server, then I need to download public.key file.
```
wget http://myserver.org/ubuntu/public.key
```
and I can then this key simply add in Synaptic
Settings> Repositories> Authentication> Add> Selected the download key public.key

and now I can simply apt-get programs, what I have but to my server.

Maybe somebody, who better knows about repositorys - looks my steps and says is everything OK?

EDIT: one problem I have with Release file. I get now errors: No MD5Sum entry in Release file
How to fix this?

---

