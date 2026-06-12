---
title: "Network manager - how to apply patch for known bug"
date: 2016-06-06
forum: New to Ubuntu
---

### Post by bchun on 2016-06-06
I'm currently trying to configure access to my university's network. I'm using TLS authentication with a .cer and .p12 file that I get from my university.

There are two issues I had with Ubuntu 16.04, both of which are apparently known:
1) I cannot load the .p12 file and instead must drag and drop the file into the box next to "private-key"
2) I get the error: "Unencrypted private keys are insecure The selected private key does not appear to be protected by a password. This could allow your security credentials to be compromised. Please select a password-protected private key. (You can password-protect your private key with openssl)"

I'm okay with my workaround for #1, but #2 appears to be an a known issue: [https://bugs.launchpad.net/network-manager/+bug/1573720](https://bugs.launchpad.net/network-manager/+bug/1573720).

Furthermore, it seems like there's a fix: [https://bugs.launchpad.net/network-manager/+bug/1573720/comments/6](https://bugs.launchpad.net/network-manager/+bug/1573720/comments/6)

However, I don't know how to apply the fix, which seems to consist of editing [libnm-core/nm-utils.c]("https://cgit.freedesktop.org/NetworkManager/NetworkManager/tree/libnm-core/nm-utils.c?id=5660bbfacc2d1c96a8cf9dc542312a1468646543"). I cannot seem to be able to find/access that directory or file. What steps must I follow in order to apply the known fix?

Thanks,

---

### Post by bchun on 2016-06-06
So it also seems from my reading of [https://bugzilla.gnome.org/show_bug.cgi?id=766684](https://bugzilla.gnome.org/show_bug.cgi?id=766684) (which was linked to as an "upstream bug" in the first link in my first point) that I would need to rebuild the nm-applet package and use my own version of that package. Is that correct?

---

### Post by jeremy31 on 2016-06-07
You would need to download the source code for the package, apply the patch and then compile.  I have only patched kernel modules, so I am unsure of the exact method

---

### Post by bchun on 2016-06-07
Thanks,

I managed to figure out how to do that and compile the package based off the commit in one of the links, but when I installed my compiled package (a nightmare sudo apt-get'ing all the required dependencies) it managed to break my network manager to the point that installing network manager and network manager applet based off .deb files I found online didn't fix it... so I've given up on this issue for now.

---

### Post by Geoffrey_Arndt on 2016-06-08
Might try another network manager  . . . perhaps Wicd (pronounced "Wicked" network manager).   It's in the repos.

---

### Post by bchun on 2016-06-15
Thanks,

I ended up being able to successfully use the VPN using the protocol followed in [http://tomtomtom.org/networkmanager-openconnect/](http://tomtomtom.org/networkmanager-openconnect/), which I've quoted below (for my own personal reference in the future)


> On Ubuntu 16.04 the network-manager-openconnect and network-manager-openconnect-gnome plugins are not usable because they are to old to use with the current version of network-manager.

This is the english version of [this guide]("https://forum.ubuntuusers.de/post/8198598/") from a german ubuntu support forum.

Unofficial built packages are available here:

[http://tomtomtom.org/networkmanager-openconnect_1.1.93-1_i386.deb](http://tomtomtom.org/networkmanager-openconnect_1.1.93-1_i386.deb)

[http://tomtomtom.org/networkmanager-openconnect_1.1.93-1_amd64.deb](http://tomtomtom.org/networkmanager-openconnect_1.1.93-1_amd64.deb)


NOTE: You won´t get any security updates for this! It is just a workaround until the packages will have been fixed in the official repository!

Using VPN is a security feature - so it is better to build the package manually from source because you don´t know what I put into the packages. :-P


At first remove the unusable packages

sudo apt-get purge network-manager-openconnect network-manager-openconnect-gnome

You will need the build-dependencies.

sudo apt-get build-dep network-manager-openconnect
(NOTE: For this the 'deb-src'-Sources in /etc/apt/sources.list must be active.)

You can do this with sed e.g.

sudo sed -i s/#deb-src/deb-src/g /etc/apt/sources.list

the new dependency for the new version.


sudo apt-get install libnm-dev
and the sourcecode from GNOME project.


wget [http://ftp.gnome.org/pub/GNOME/sources/NetworkManager-openconnect/1.1/NetworkManager-openconnect-1.1.93.tar.xz](http://ftp.gnome.org/pub/GNOME/sources/NetworkManager-openconnect/1.1/NetworkManager-openconnect-1.1.93.tar.xz)

Unpack the tarball

tar -xf NetworkManager-openconnect-1.1.93.tar.xz
change to the unpacked directory

cd NetworkManager-openconnect-1.1.93
and run the configure script.

./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var --libexecdir=/usr/lib/NetworkManager/ --enable-more-warnings=yes --disable-static

start compiling
.
make

and install manually 

sudo make install

install the dependency for use the software

sudo apt-get install openconnect

or build a package with checkinstall

sudo checkinstall

If you do so enter this:

networkmanager-openconnect as package name

adduser, libc6, libdbus-glib-1-2, libglib2.0-0, libnm-glib-vpn1, libnm-util2, network-manager, openconnect as requirements

and

network-manager-openconnect, network-manager-openconnect-gnome

as conflicts.

If you get errormessages by installing the package try

sudo apt-get -f install

to resolve unmet dependencies.

To use the software it is necessary to add a systemuser for this

sudo adduser --system --quiet --home /var/lib/NetworkManager --no-create-home --gecos "NetworkManager OpenConnect plugin" --group nm-openconnect}

At last restart the system.

---

