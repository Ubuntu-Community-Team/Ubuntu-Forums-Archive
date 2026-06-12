---
title: "SCRIPT: Add local folder to apt sources list"
date: 2005-07-02
forum: Outdated Tutorials &amp; Tips
---

### Post by arnix on 2005-07-02
This script will let you automatically install (key -i) the **/var/cache/apt-add/dists/hoary/main/binary-i386/** folder as one of your apt sources.
Later, every time you add some new ".deb" files in that folder, you must update the Packages file by -u key.
You can also delete all added things by -d key.

Example of usage:

```

$ cd ~/
$ wget http://freenet.am/~arnix/scripts/apt-add.sh.gz
$ gzip -d apt-add.sh.gz
$ su
# mkdir -p /var/cache/apt-add/dists/hoary/main/binary-i386/
# cp ~/media/usbdisk/*.deb /var/cache/apt-add/dists/hoary/main/binary-i386/
# ./apt-add.sh -i

```

The script:
[http://freenet.am/~arnix/scripts/apt-add.sh.gz](http://freenet.am/~arnix/scripts/apt-add.sh.gz)

Though it's my first script, i think it's working heh, anyway, use at your own risk, if you find any bugs please inform me.

---

