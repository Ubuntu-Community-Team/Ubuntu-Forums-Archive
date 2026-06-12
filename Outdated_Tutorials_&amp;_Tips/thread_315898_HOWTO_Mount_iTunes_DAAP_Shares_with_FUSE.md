---
title: "HOWTO: Mount iTunes DAAP Shares with FUSE"
date: 2006-12-09
forum: Outdated Tutorials &amp; Tips
---

### Post by sciurus on 2006-12-09
Apple combines DAAP and Zeroconf in iTunes to automatically share music on a local network. It is possible to configure Avahi and Amarok or Rhythmbox in (K)Ubuntu to access these shares, but wouldn't it be nice if you were able to access them from any program and actually transfer them to your computer? Enter fusedaap.

[PHP]sudo aptitude install build-essential subversion fuse-utils libfuse2 libfuse-dev python-dev[/PHP]

Make sure that you are in the fuse group, then logout and log back in.

Make sure that fuse is listed in /etc/modules, then

[PHP]sudo modprobe fuse[/PHP]

fusedaap requires one piece of software not in the ubuntu repositories, and one that is but it outdated. We'll download and install them from source now.

[PHP]wget "http://mercurial.creo.hu/repos/fuse-python-hg/?ca=tip;type=gz"  --output-document=fuse-py-snapshot.tar

tar -xf fuse-py-snapshot.tar

cd fuse-py-*

python setup.py build

sudo python setup.py install

cd ..

svn co http://jerakeen.org/svn/tomi/Projects/PythonDaap/ PythonDaap

cd PythonDaap

python setup.py build

sudo python setup.py install

cd ..[/PHP]

Now let's install fusedaap. I'll put it in /opt.

[PHP]
svn co https://svn.sourceforge.net/svnroot/fusedaap/trunk fusedaap

sudo mv fusedaap /opt
[/PHP]

Let's mount the DAAP shares. We need somewhere to mount do this; I'll use /media/daap.

[PHP]
sudo mkdir /media/opt

python /opt/fusedaap/fusedaap.py /media/opt
[/PHP]

After a few seconds look in /media/daap and you should see folders for shares and artists. When you're finished using fusedaap, disconnect with

[PHP]
fusermount -u /media/daap
[/PHP]

To make connecting and disconnecting easier you could put this script in /usr/local/bin/mountdaap and use it.

[PHP]
#!/bin/bash
if (pgrep -f -c fusedaap)
then
        Xdialog --wrap --title "iTunes Share Control"\
                --help "This script unmounts fusedaap from /media/daap "\
                --yesno "iTunes shares are connected to /media/daap. \
                Would you like to disconnect?" 0 0

        case $? in
        0)
                fusermount -u /media/daap &> /dev/null;;
        esac
else
        Xdialog --wrap --title "iTunes Share Control"\
                --help "This script mounts fusedaap from /media/daap "\
                --yesno "iTunes shares are not connected. \
                Would you like to mount them on /media/daap?" 0 0

        case $? in
        0)
                python /opt/fusedaap/fusedaap.py /media/daap &> /dev/null;;
        esac
fi
[/PHP]

---

