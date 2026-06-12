---
title: "Ubuntu 12.10. What is taking up so much space on the disk?"
date: 2013-11-05
forum: New to Ubuntu
---

### Post by mmcc1178 on 2013-11-05
I am trying to free up some disk space.


I entered:

sudo find / -name '*' -size +500M

Results:

/home/.ecryptfs/comp/.Private/ECRYPTFS_FNEK_ENCRYPTED.FWZIKBtcaNt.i-S.vEXzPtz0B9t-ObfCo9YbBFzDMrese72xqNlbBAbXuE--/ECRYPTFS_FNEK_ENCRYPTED.FWZIKBtcaNt.i-S.vEXzPtz0B9t-ObfCo9Ybn4DXCHYsk-pO3SjHSfQ4g---
/home/.ecryptfs/comp/.Private/ECRYPTFS_FNEK_ENCRYPTED.FWZIKBtcaNt.i-S.vEXzPtz0B9t-ObfCo9YbBFzDMrese72xqNlbBAbXuE--/ECRYPTFS_FNEK_ENCRYPTED.FWZIKBtcaNt.i-S.vEXzPtz0B9t-ObfCo9YbHZ6xKS7OQAcjnzG2WOjeYU--/ECRYPTFS_FNEK_ENCRYPTED.FYZIKBtcaNt.i-S.vEXzPtz0B9t-ObfCo9YbANUe0jPzl0tbzediGB36yUzFH7SwUQEuKN4eiFsX4CH94SoR-dYM7DX.hIqhmFLx
/home/.ecryptfs/comp/.Private/ECRYPTFS_FNEK_ENCRYPTED.FWZIKBtcaNt.i-S.vEXzPtz0B9t-ObfCo9YbBFzDMrese72xqNlbBAbXuE--/ECRYPTFS_FNEK_ENCRYPTED.FWZIKBtcaNt.i-S.vEXzPtz0B9t-ObfCo9Yb3bPikVGDgxU4ZQm-NXG25---
/home/.ecryptfs/comp/.Private/ECRYPTFS_FNEK_ENCRYPTED.FWZIKBtcaNt.i-S.vEXzPtz0B9t-ObfCo9YbBFzDMrese72xqNlbBAbXuE--/ECRYPTFS_FNEK_ENCRYPTED.FWZIKBtcaNt.i-S.vEXzPtz0B9t-ObfCo9YbOnHi-UnUqdZu8R91GLn5h---/ECRYPTFS_FNEK_ENCRYPTED.FZZIKBtcaNt.i-S.vEXzPtz0B9t-ObfCo9YbcVe.gh.HpfhTpYXgBOQxLFt99zPQJRNB623R3uAc3ak7wzmchdczekvZuw828jsksgdxuU6CtVI3Z7rL2cx.2U--
/home/comp/Video/Amélie [2001]
/home/comp/Video/Barry Lyndon
/home/comp/Video/Persona 1966
find: `/run/user/comp/gvfs': Permission denied
/proc/kcore
find: `/proc/13714/task/13714/fd/5': No such file or directory
find: `/proc/13714/task/13714/fdinfo/5': No such file or directory
find: `/proc/13714/fd/5': No such file or directory
find: `/proc/13714/fdinfo/5': No such file or directory



& also
After entering:

df -h

Results:

comp@comp-ThinkPad-T43:~$ df -h
Filesystem              Size  Used Avail Use% Mounted on
/dev/sda1                36G   29G  5.7G  84% /
udev                    487M  4.0K  487M   1% /dev
tmpfs                   498M   28K  497M   1% /tmp
tmpfs                   199M  848K  198M   1% /run
none                    5.0M     0  5.0M   0% /run/lock
none                    498M  600K  497M   1% /run/shm
none                    100M   16K  100M   1% /run/user
/home/comp/.Private   36G   29G  5.7G  84% /home/comp


This is the second computer I've ran Ubuntu on, the first one I never encountered any encrypted files when searching for large files or a "private" "duplicate"[?] of dev/sd** (/home/comp/.Private   36G   29G  5.7G  84% /home/comp)

Is this normal for the system files to take up so much space when I only have a few large video, etc. files? I may have a lot of packages but I suspect there may be some hidden and unnecessary files taking up space.

---

### Post by TheFu on 2013-11-06
Videos can be 30G in size. It all comes down to the resolution and length. Those can be 200MB too - no way to tell.
It is possible for a mount point to hide files ... anything underneath the directory where the other filesystem is mounted, for example.

Notice that /home/comp/.Private is really part of sda1 and there is 500MB (half a Gig) in /tmp/.  A reboot will clean that up probably.  The .private "hits" are the same as the videos in your HOME.

The way I look for big files is by starting in / - run **sudo du -sh**.  Then work down the largest directories and find what is eating all the space.  /var/lib and /var/mail might be it depending on stuff you've loaded.  OTOH, it is almost always /home sucking all the storage.

---

### Post by crazymonkey05 on 2013-11-06
if you want a simple GUI to do it for you then use ubuntu tweak and run the janitor

---

