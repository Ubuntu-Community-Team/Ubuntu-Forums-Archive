---
title: "apt-get update broken after backup/restore"
date: 2014-01-09
forum: New to Ubuntu
---

### Post by petrux3 on 2014-01-09
Following this example I've been playing a bit doing backup with the following script:

```
#!/bin/bash
DEF_DEST_DIR=/tmp
DEST_DIR=$1
if [ -z $1 ]; then
DEST_DIR=$DEF_DEST_DIR
fi

DEST_DIR=$DEST_DIR/`whoami`-`hostname`-backup-`date +%Y-%m-%d_%H-%M-%S`
mkdir $DEST_DIR
sudo apt-key exportall > $DEST_DIR/Repo.keys
sudo cp /etc/apt/sources.list $DEST_DIR/sources.list
dpkg --get-selections > $DEST_DIR/Package.list
pip freeze > $DEST_DIR/requirements.txt
rsync -r --progress --exclude=Downloads --exclude=Dropbox /home/`whoami` $DEST_DIR
rsync -r --progress /opt $DEST_DIR
cp restore.sh $DEST_DIR
chmod 775 $DEST_DIR/restore.sh
```

and restoring my system with the:

```
sudo rsync -r --progress `whoami` /home/
sudo rsync -r --progress ./opt /
sudo apt-key add Repo.keys
sudo cp sources.list /etc/apt/sources.list 
sudo apt-get update
sudo apt-get install dselect
sudo dpkg --set-selections < Package.list
sudo apt-get dselect-upgrade -y
sudo pip install -r requirements.txt
```

After that I performed a sudo apt-get update and got this error:

```
W: Failed to fetch bzip2:/var/lib/apt/lists/partial/it.archive.ubuntu.com_ubuntu_dists_saucy-updates_main_binary-amd64_Packages Hash Sum mismatch
W: Failed to fetch bzip2:/var/lib/apt/lists/partial/it.archive.ubuntu.com_ubuntu_dists_saucy-updates_universe_binary-amd64_Packages Hash Sum mismatch
W: Failed to fetch bzip2:/var/lib/apt/lists/partial/it.archive.ubuntu.com_ubuntu_dists_saucy-updates_main_binary-i386_Packages Hash Sum mismatch
W: Failed to fetch bzip2:/var/lib/apt/lists/partial/it.archive.ubuntu.com_ubuntu_dists_saucy-updates_universe_binary-i386_Packages Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

How can I fix this whole stuff? Is my backup/restore process buggy per se?

---

### Post by ptn107 on 2014-01-09
Clear out the lists folder with the below command and try *'apt-get update; apt-get upgrade'* again.
```
rm -rf /var/lib/apt/lists/*
```

---

