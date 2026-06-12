---
title: "How to erase Gutsy by installing Hardy on same partition?"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by psychedelix on 2008-06-02
Hi everyone.  I hear of upgrade.  But I want to clean-install the new version of of Ubuntu, Hardy Heron on same partition as the Gutsy one, and thus erase the latter.  But I am not being able to do it.  Can someone help me?
Thanks.

---

### Post by neurostu on 2008-06-02
What do you mean you're unable to do it?

run the liveCd and install Hardy, when it asks you the partitioning question, tell it you want to configure manually. Then select the partition on which Gutsy is installed and Hardy will be installed over it.  Remember to reformat the partition and set its mount point as /

---

### Post by sayakb on 2008-06-02
Try to reformat as neurostu said, or delete the gutsy's / partition and create it again. Please note that in the Hardy LiveCD partitioner, you will not see the Gutsy's / as a / mountpoint, but something like /media/sda*
You should know which partition you are deleting/reformatting.

---

### Post by durand on 2008-06-02
Uh, just install ubuntu over your current installation. I haven't used the installer recently but when it asks you to choose your partitions, format them first.

EDIT: Oops. left it on this page for way too long.

---

