---
title: "Packaging git-core problem"
date: 2010-08-17
forum: Packaging and Compiling Programs
---

### Post by skkeeper on 2010-08-17
Hi everyone,
Since I always enjoy using the bleeding edge of my favorite software I've been compiling quite a few in my laptop, but today I found out how I can package my compilations very easily using checkinstall.

So I went ahead and compiled git, here is exactly what I did:

git clone [http://github.com/git/git.git](http://github.com/git/git.git)

Next I removed my pre-installed git from the ubuntu repos
sudo apt-get remove git-core

make configure
./configure
make prefix=/usr/ all
sudo checkinstall -D --install=no --maintainer=skkeeper@gmail.com --pkgname=git-core --pkgversion=1.7.2.1.97.g3235b --provides=git --requires=libc6,libcurl3-gnutls,libdigest-sha1-perl,liberror-perl,libexpat1,perl-modules,zlib1g make prefix=/usr/ install all

No problem, the package was sucessfully created and then I installed it:
sudo dpkg -i git-core_1.7.2.1.97.g3235b-1_amd64.deb

Sucess. Git is installed in /usr/bin.

My problem is that when I install a package from the ubuntu repositories, it tries to upgrade the git-core back to the repo version.

Example:
sudo apt-get install git-cola

The following extra packages will be installed:
  git-core gitk
Suggested packages:
  git-arch git-cvs git-svn git-email git-daemon-run git-gui gitweb
The following NEW packages will be installed:
  git-cola gitk
[COLOR="Red"][B]The following packages will be upgraded:
  git-core[/B][/COLOR]

Did I do something wrong during the packaging? Keep in mind that this is really simple and I dont want to package to PPA or official repos. This is just a way for me to send bleeding edge software to my friends when they need it.

Thanks for your time, Namaste

---

### Post by SevenMachines on 2010-08-17
The repository version uses the epoch number in the version number (the 1: bit), so you need to too. so version is 1:1.7.2.1.97.g3235b and not 1.7.2.1.97.g3235b

try,
> $ sudo checkinstall -D --install=no --maintainer=skkeeper@gmail.com --pkgname=git-core --pkgversion=1:1.7.2.1.97.g3235b --provides=git --requires=libc6,libcurl3-gnutls,libdigest-sha1-perl,liberror-perl,libexpat1,perl-modules,zlib1g make prefix=/usr/ install all

---

### Post by skkeeper on 2010-08-17
That worked like a charm, can you explain me what does this epoch number mean? Just for future reference ;)

---

### Post by SevenMachines on 2010-08-17
see epoch section in [_Ubuntu Policy on Versioning_]("http://people.canonical.com/%7Ecjwatson/ubuntu-policy/policy.html/ch-controlfields.html#s-f-Version")

---

