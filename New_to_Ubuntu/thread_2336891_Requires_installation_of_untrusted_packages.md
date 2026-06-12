---
title: "Requires installation of untrusted packages"
date: 2016-09-12
forum: New to Ubuntu
---

### Post by chris-burmajster on 2016-09-12
Hello,

I have received the following message from my package manager: "requires installation of untrusted packages". What do I do? Package is Ubuntu 16.04. Result of sudo apt-get is:

```
Hit:1 [http://mirror.vorboss.net/ubuntu-archive](http://mirror.vorboss.net/ubuntu-archive) xenial InRelease
Get:2 [http://mirror.vorboss.net/ubuntu-archive](http://mirror.vorboss.net/ubuntu-archive) xenial-updates InRelease [95.7 kB]
Hit:3 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease                     
Hit:4 [http://mirror.vorboss.net/ubuntu-archive](http://mirror.vorboss.net/ubuntu-archive) xenial-backports InRelease      
Hit:5 [http://mirror.vorboss.net/ubuntu-archive](http://mirror.vorboss.net/ubuntu-archive) xenial-security InRelease       
Get:6 [http://mirror.vorboss.net/ubuntu-archive](http://mirror.vorboss.net/ubuntu-archive) xenial/main Translation-en_GB [426 kB]
Get:7 [http://mirror.vorboss.net/ubuntu-archive](http://mirror.vorboss.net/ubuntu-archive) xenial/restricted Translation-en_GB [2,556 B]
Get:8 [http://mirror.vorboss.net/ubuntu-archive](http://mirror.vorboss.net/ubuntu-archive) xenial/universe Translation-en_GB [3,040 kB]
Hit:9 [https://repo.skype.com/deb](https://repo.skype.com/deb) stable InRelease                              
Get:10 [https://download.01.org/gfx/ubuntu/16.04/main](https://download.01.org/gfx/ubuntu/16.04/main) xenial InRelease [3,651 B]
Ign:10 [https://download.01.org/gfx/ubuntu/16.04/main](https://download.01.org/gfx/ubuntu/16.04/main) xenial InRelease          
Get:11 [http://mirror.vorboss.net/ubuntu-archive](http://mirror.vorboss.net/ubuntu-archive) xenial/multiverse Translation-en_GB [88.1 kB]
Get:12 [http://mirror.vorboss.net/ubuntu-archive](http://mirror.vorboss.net/ubuntu-archive) xenial-updates/universe amd64 Packages [324 kB]
Get:13 [http://mirror.vorboss.net/ubuntu-archive](http://mirror.vorboss.net/ubuntu-archive) xenial-updates/universe i386 Packages [321 kB]
Ign:14 [http://download.ebz.epson.net/dsc/op/stable/debian](http://download.ebz.epson.net/dsc/op/stable/debian) lsb3.2 InRelease     
Hit:15 [http://download.ebz.epson.net/dsc/op/stable/debian](http://download.ebz.epson.net/dsc/op/stable/debian) lsb3.2 Release
Fetched 4,300 kB in 1s (4,166 kB/s)
Reading package lists... Done
W: GPG error: [https://download.01.org/gfx/ubuntu/16.04/main](https://download.01.org/gfx/ubuntu/16.04/main) xenial InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 56A3DEF863961D39
W: The repository 'https://download.01.org/gfx/ubuntu/16.04/main xenial InRelease' is not signed.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: [http://download.ebz.epson.net/dsc/op/stable/debian/dists/lsb3.2/Release.gpg:](http://download.ebz.epson.net/dsc/op/stable/debian/dists/lsb3.2/Release.gpg:) Signature by key E5220FB7014D0FBDA50DFC2BE5E86C008AA65D56 uses weak digest algorithm (SHA1)
```

Chris Burmajster

---

### Post by howefield on 2016-09-12
You could use..

```
wget --no-check-certificate https://download.01.org/gfx/RPM-GPG-KEY-ilg-4 -O - | sudo apt-key add -
```

You'll likely get a weak digest warning like you are already getting for the epson repository but should fix the untrusted error. That isn't so much of a worry for now.

What is it that you use that repository for, I'd suggest re-evaluating if you need it ?

---

### Post by mastablasta on 2016-09-13
looks like that repo is for intel drivers. this shouldn't be necessary to have. in linux new kernel=new drivers (excluded are those closed soruce ones that patch kernel - e.g. nvidia, old AMD driver called fglrx...). if you need newer driver then by default in 16.04 you can enable hardware enablement stack. read more about that here: [URL="https://wiki.ubuntu.com/Kernel/LTSEnablementStack"]https://wiki.ubuntu.com/Kernel/LTSEnablementStack
[/URL]
another option is to upgrade the whole OS (e.g. to 16.10 when it gets out)

if you must have the latest version pathched to current kernel, then there are a couple good PPA's (signed and trusted) that will provide the very latest version of the driver (look into xorg edgers, oibaf...).

final option is you choose to trust the site. but no siganture means anyone could have added the files to the site (e.g. "hack" the webstie and add the malicious software under the driver). in short you would be doing drivers windows style.

---

