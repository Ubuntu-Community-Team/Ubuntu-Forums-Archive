---
title: "Ubuntu running in low graphics mode by setting var/lib as root permission"
date: 2020-03-03
forum: New to Ubuntu
---

### Post by weirdygeekpsych on 2020-03-03
So Here is the mistake I made, 

1) installed an app from snap store, tried to run it, i got an error saying error: /var/lib/snapd/seccomp not root owned 1000:1000
2) change the permission to root and worked, and came to know its danger to put it with root permission and changed to primary user
3) Now lightdm also changed to primary user as I used this command sudo chown -R username:username /var/lib

can anyone help me to reset the /var/lib folder to default settings?

---

### Post by Impavidus on 2020-03-03
Most files and directories in /var/lib should be owned by root:root. The exceptions on my system are:```

drwxr-xr-x   2 geoclue  geoclue      4096 jul 20  2017 ./geoclue
drwxr-xr-x   4 colord   colord       4096 mei  7  2017 ./colord
(and all subdirectories)
drwxr-xr-x   2 systemd-timesync systemd-timesync     4096 mei 30  2019 ./systemd/timesync
-rw-r--r--   1 systemd-timesync systemd-timesync        0 mrt  3 11:56 ./systemd/timesync/clock
drwxr-x---   6 lightdm          lightdm              4096 jun 21  2018 ./lightdm
(and all subdirectories)
-rw-r-----   1 root             mlocate          14783215 mrt  3 09:10 ./mlocate/mlocate.db
drwxr-xr-x   2 avahi-autoipd    avahi-autoipd        4096 okt 12  2016 ./avahi-autoipd
drwxrwx---   2 username         lightdm              4096 okt 14  2016 ./lightdm-data/username
drwxrwx---   2 lightdm          lightdm              4096 mrt  3 09:05 ./lightdm-data/lightdm
drwx------   2 _apt             root                 4096 feb 14  2019 ./update-notifier/package-data-downloads/partial
drwxr-xr-x   2 _apt             root                 4096 jun 22  2018 ./apt/lists/auxfiles
drwx------   2 _apt             root                20480 mrt  3 11:45 ./apt/lists/partial
```On your system, the list could be different.

It's a fairly short list, so you may be able to fix this. Another option you can try in such a case is reinstalling every package that has files in /var/lib. When you make this error in a directory with more files, the best fix is to reinstall. Recursive chowns and chmods destroy entropy, so they're very hard to undo.

---

### Post by SeijiSensei on 2020-03-03
Here's my list of directories in /var/lib with non-root owners from Kubuntu 20.04:

```

drwxr-xr-x  2 avahi-autoipd avahi-autoipd 4096 Jan  6 00:19 avahi-autoipd
drwxr-xr-x  3 colord        colord        4096 Jan  7 14:11 colord
drwxr-xr-x  2 geoclue       geoclue       4096 Aug 13  2019 geoclue
drwxr-xr-x  4 statd         nogroup       4096 Feb 19 11:33 nfs
drwxr-x---  6 sddm          sddm          4096 Jan  7 13:48 sddm
drwxr-xr-x  2 tss           tss           4096 Dec  3 16:50 tpm

```
Of those, only colord, nfs, and sddm have any files (which are owned by the directory owner). The other directories are empty.

However if you have things like mysql installed, they also occupy /var/lib and have non-root owners and groups, e.g., mysql:mysql.

---

### Post by weirdygeekpsych on 2020-03-04
@impavidus "can you tell me what you mean by recursvie chowns and chmods destroy entropy, so they're very hard to undo?" 
because what I am thinking is to change the ownership of files as it seems to be the easiest way for resetting. reinstall everything inside var folder is plenty of work for me

Also can you tell me the permission for var folder also?

---

### Post by Impavidus on 2020-03-04
Normally, many different files and directories have different owners. After a recursive chown, they all have the same owner. In terms of mathematics, the new situation has less entropy. It's really easy to go automatically from a situation where everything is different to a situation where everything is the same, but very hard to go from a situation where everything is the same to one where everything is different, but not random. The same for permissions. Did I confuse you with the term "entropy"? It doesn't really matter.

Your best chance of fixing this without a reinstall is by going over the files and directories in /var/lib and fixing them one by one. All should have owner root and group root (in short: root:root) except the ones I listed in my previous post and maybe some that don't exist on my system. To fix it, try this:```
sudo chown -R root:root /var/lib
sudo chown -R colord:colord /var/lib/colord
sudo chown -R lightdm:lightdm /var/lib/lightdm
sudo chown geoclue:geoclue /var/lib/geoclue
sudo chown systemd-timesync:systemd-timesync /var/lib/systemd/timesync
...
```I hope you can make up the other commands yourself. As SeijiSensei showed, the exact list of files and directories not owned by root depends on the packages you have installed. There's no nfs, sddm or tpm on my system.

If there are files or directories in /var/lib that you have doubts about, find the package where the file/directory belongs to and reinstall that package. To find the name of the package, use```
dpkg --search /path/to/file
```To reinstall the package, use```
sudo apt install --reinstall package-name
```

---

