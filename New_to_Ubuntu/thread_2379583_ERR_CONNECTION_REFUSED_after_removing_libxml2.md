---
title: "ERR_CONNECTION_REFUSED after removing libxml2"
date: 2017-12-07
forum: New to Ubuntu
---

### Post by dhouha2 on 2017-12-07
[COLOR=#111111][FONT=Ubuntu]I have been using ubuntu 15.04 and i like to uninstall libxml2.9 and install libxml2.6 now and I have been having all problems ERR_CONNECTION_REFUSED.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I've tried doing these commands:
[/FONT][/COLOR]
> sudo apt-get remove --auto-remove libxml2
sudo apt-get purge --auto-remove libxml2
sudo apt-get install libxml2

sudo cp /etc/apt/sources.list ~/ 
sudo wget "http://pastebin.com/raw.php?i=uzhrtg5M" -O /etc/apt/sources.list 
sudo apt-get update

[COLOR=#111111][FONT=Ubuntu]I've getting this error:
[/FONT][/COLOR]> 
Fetched 5.530 kB in 53s (104 kB/s)
W: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192
W: Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/Release](http://dl.google.com/linux/chrome/deb/dists/stable/Release) Unable to find expected entry 'main/binary-i386/Packages' in Release file (Wrong sources.list entry or malformed file)
E: Some index files failed to download. They have been ignored, or old ones used instead.

[COLOR=#111111][FONT=Ubuntu]This error was solved when i've been entering this command:
[/FONT][/COLOR]
> sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 16126D3A3E5C1192

[COLOR=#111111][FONT=Ubuntu]I've changing /etc/apt/sources.list like this:
[/FONT][/COLOR]
> deb [http://us-central1.gce.archive.ubuntu.com/ubuntu/](http://us-central1.gce.archive.ubuntu.com/ubuntu/) vivid main
deb-src [http://us-central1.gce.archive.ubuntu.com/ubuntu/](http://us-central1.gce.archive.ubuntu.com/ubuntu/) vivid main

deb [http://us-central1.gce.archive.ubuntu.com/ubuntu/](http://us-central1.gce.archive.ubuntu.com/ubuntu/) vivid-updates main
deb-src [http://us-central1.gce.archive.ubuntu.com/ubuntu/](http://us-central1.gce.archive.ubuntu.com/ubuntu/) vivid-updates main

deb [http://us-central1.gce.archive.ubuntu.com/ubuntu/](http://us-central1.gce.archive.ubuntu.com/ubuntu/) vivid universe
deb-src [http://us-central1.gce.archive.ubuntu.com/ubuntu/](http://us-central1.gce.archive.ubuntu.com/ubuntu/) vivid universe
deb [http://us-central1.gce.archive.ubuntu.com/ubuntu/](http://us-central1.gce.archive.ubuntu.com/ubuntu/) vivid-updates universe
deb-src [http://us-central1.gce.archive.ubuntu.com/ubuntu/](http://us-central1.gce.archive.ubuntu.com/ubuntu/) vivid-updates universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) vivid-security main
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) vivid-security main
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) vivid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) vivid-security universe

[COLOR=#111111][FONT=Ubuntu]With this configuartion i can update and install libxml2 but i always get ERR_CONNECTION_REFUSED.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I've tring this solution [https://ubuntuforums.org/archive/index.php/t-1846203.html](https://ubuntuforums.org/archive/index.php/t-1846203.html) but i get always ERR_CONNECTION_REFUSED.[/FONT][/COLOR]
> ifconfig eth0 up

dhclient eth0

ping -c 4 google.com

apt-get update
apt-get install ubuntu-desktop libxml2
    apt-get install ubuntu-desktop libxml2
    Reading package lists... Done
    Building dependency tree
    Reading state information... Done
    E: Unable to locate package ubuntu-desktop
reboot


[COLOR=#111111][FONT=Ubuntu]In error.log, i found:
[/FONT][/COLOR]
> [Wed Dec 06 15:10:30.816274 2017] [mpm_prefork:notice] [pid 19962] AH00163: Apache/2.4.10 (Ubuntu) OpenSSL/1.0.1f mod_perl/2.0.9dev Perl/v5.20.2 configured -- resuming normal operations
[Wed Dec 06 15:10:30.816295 2017] [core:notice] [pid 19962] AH00094: Command line: '/usr/sbin/apache2'
[Wed Dec 06 15:10:31.698384 2017] [mpm_prefork:notice] [pid 19962] AH00169: caught SIGTERM, shutting down
[Wed Dec 06 15:10:32.760398 2017] [mpm_prefork:notice] [pid 29008] AH00163: Apache/2.4.10 (Ubuntu) OpenSSL/1.0.1f mod_perl/2.0.9dev Perl/v5.20.2 configured -- resuming normal operations
[Wed Dec 06 15:10:32.760577 2017] [core:notice] [pid 29008] AH00094: Command line: '/usr/sbin/apache2'
[Wed Dec 06 15:10:34.236447 2017] [mpm_prefork:notice] [pid 29008] AH00169: caught SIGTERM, shutting down

[COLOR=#111111][FONT=Ubuntu]Any help please!
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Thanks in advance.[/FONT][/COLOR]

---

### Post by Holger_Gehrke on 2017-12-07
Hello and welcome to the forum!

First: as you were already told on [askubuntu]("https://askubuntu.com/questions/983815/err-connection-refused-after-removing-libxml2"), you're running an out of support version of Ubuntu. Support for 15.04 ended 9 month after it's release in early 2016. It's generally a bad idea to run a system that doesn't get security updates and bugfixes, but as long as the system isn't connected to the internet, you can stay out of trouble, mostly. More important: the repositories for that version simply aren't there anymore, so the message 'E: Unable to locate package ubuntu-desktop' does not surprise me at all ...

Second: downgrading a library is usually not an end in itself. Doing it will break stuff that depends on the newer version. You're probably trying to get some (old, binary only ?) program that refuses to run with the newer library to work. Telling us what your real goal is might allow us to point you in a better direction. If you can get the source code of that program, compiling it yourself might work. If you can't, then you might try to put the needed older libraries in a directory outside the normal library search path and direct the library loader to them by prefixing the call to your program with 'LD_LIBRARY_PATH=<directory>' (where <directory> is the place where you put the old libs).

Holger

---

### Post by dhouha2 on 2017-12-08
I have 3 sites web live and http, https and DNS no longer working.

I tried to downgrade libxml because i have a problem with symfony translation theme in Prestashop and in github they suggested to downgrade this library.

I couldn't install apache2 also.

How can i do to resolve all these problems ?

---

