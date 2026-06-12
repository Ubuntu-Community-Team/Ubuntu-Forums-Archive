---
title: "Acestream causing dependancy errors"
date: 2013-10-17
forum: New to Ubuntu
---

### Post by dvjunk on 2013-10-17
I tried installing Acestream on my Mythbuntu 12.04.3 LTS system and got some dependency errors. Now update manager gets stalled and I'm not sure how to fix this.
Can I run Acestream on this system, or is it not recommended?? I would like to be able to stream HD video.

Here are my notes... any help is greatly appreciated:

Install acestream for high def streaming
[http://forum.wiziwig.eu/threads/82806-Install-AceStream-on-Ubuntu](http://forum.wiziwig.eu/threads/82806-Install-AceStream-on-Ubuntu)
wget [http://torrentstream.org/downloads/linux/test/acestream-local_2.0.0_i386.deb](http://torrentstream.org/downloads/linux/test/acestream-local_2.0.0_i386.deb)
sudo apt-get install python2.7-apsw python2.7-m2crypto libqt4-webkit
sudo dpkg -i acestream-local_2.0.0_i386.deb
got dependancy errors
ran Software Center and it says it needs to be repaired - repair doesn't work
update manager says it needs a partial upgrade - OK - stalled??
Ran software center while update manager was running - not smart!!! now I think I'm stalled.
Update Manager stalls when I try to do a partial install
Web site says to use
[http://packages.ubuntu.com/quantal/i...udev0/download](http://packages.ubuntu.com/quantal/i...udev0/download)
if you have dependancy issues, but this site says I should use a package manager under Ubuntu... not sure what to do
This site
[http://steamcommunity.com/app/221410/discussions/0/846940248038094571/](http://steamcommunity.com/app/221410/discussions/0/846940248038094571/)
says:
sudo apt-get update
sudo apt-get install libudev0 
This command says
You might want to run 'apt-get -f install' to correct these:
sudo apt-get -f install
gave a bunch of
 message, and at the end said:
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  python-minimal python2.7-minimal (due to python-minimal)
0 upgraded, 142 newly installed, 144 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 56.0 MB of archives.
After this operation, 73.8 MB disk space will be freed.
You are about to do something potentially harmful.
To continue type in the phrase 'Yes, do as I say!'
 ?]
Sounds too dangerous
Tried Update manager again... stalled

---

### Post by dvjunk on 2013-10-31
I went into Ubnuntu Software Center, searched for Acestream and found that "ACE Stream engine and multimedia player based on VLC" shows up as installed there.
I tried to remove it but I get a message that the package system is broken with the following details:
The following packages have unmet dependencies:

acestream:i386: Depends: python2.7 (>= 2.7.2) but 2.7.3-0ubuntu3.2 is installed
                Depends: python2.7-apsw but it is a virtual package
                Depends: python2.7-m2crypto but it is a virtual package
                Depends: python-appindicator (>= 0.4.1) but it is not installed
                Depends: libavcodec-extra-53 (>= 4:0.7-1) but 4:0.8.6ubuntu0.12.04.1 is installed
                Depends: libavformat-extra-53 (>= 4:0.7-1) but it is not installed
                Depends: libavutil-extra-51 (>= 4:0.7-1) but 4:0.8.6ubuntu0.12.04.1 is installed
                Depends: libc6 (>= 2.13) but 2.15-0ubuntu10.4 is installed
                Depends: libfontconfig1 (>= 2.8.0) but 2.8.0-3ubuntu9.1 is installed
                Depends: libfreetype6 (>= 2.2.1) but 2.4.8-1ubuntu2.1 is installed
                Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.3-1ubuntu5 is installed
                Depends: libgnutls26 (>= 2.9.11-0) but 2.12.14-5ubuntu3.4 is installed
                Depends: libqtcore4 (>= 4:4.7.0~beta1) but 4:4.8.1-0ubuntu4.4 is installed
                Depends: libqtgui4 (>= 4:4.5.3) but 4:4.8.1-0ubuntu4.4 is installed
                Depends: libqt4-network (>= 4:4.5.3) but 4:4.8.1-0ubuntu4.4 is installed
                Depends: libqt4-declarative (>= 4:4.7.4) but 4:4.8.1-0ubuntu4.4 is installed
                Depends: libmpcdec6 (>= 1:0.1~r435) but 2:0.1~r459-1ubuntu1 is installed
                Depends: libncursesw5 (>= 5.6+20070908) but 5.9-4 is installed
                Depends: libpostproc-extra-52 (>= 4:0.7-1) but it is not installed
                Depends: libsmbclient (>= 3.0.24) but 2:3.6.3-2ubuntu2.6 is installed
                Depends: libstdc++6 (>= 4.6) but 4.6.3-1ubuntu5 is installed
                Depends: libswscale-extra-2 (>= 4:0.7-1) but it is not installed
                Depends: libtinfo5 (>= 5.6+20070908) but 5.9-4 is installed
                Depends: libudev0 (>= 147) but 175-0ubuntu9.4 is installed
                Depends: libxml2 (>= 2.7.4) but 2.7.8.dfsg-5.1ubuntu4.6 is installed
                Depends: zlib1g (>= 1:1.2.0.2) but 1:1.2.3.4.dfsg-3ubuntu4 is installed


After trying a bunch of things I decided to try:
sudo apt-get remove acestream:i386
which seems to have cleared things up.
Next time I'll install it from software center.

---

