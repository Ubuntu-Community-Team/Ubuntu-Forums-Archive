---
title: "Root partition issues"
date: 2012-05-05
forum: New to Ubuntu
---

### Post by Hiuhu on 2012-05-05
My root partition is full but my hard disk is not yet full wat could be the problem ?
Here is the screen shot :

---

### Post by grahammechanical on 2012-05-05
The screen shot did not make it into your post but I will have two guesses.

1) You have a Wubi install and you need to increase the size that you set Uubuntu to use inside Windows.

2) Your root or / partition is full because it does not take up the full size of the hard disk.

If I create a 7GB partition and install Ubuntu into it then the OS will give me disk full messages as I fill up the partition with applications and data. I have had this happen.

Partitions are fixed in size. We can re-size them.

Regards.

---

### Post by Hiuhu on 2012-05-05
Ok. Sorry here is the scrren shot :

---

### Post by Hiuhu on 2012-05-05
Here is the partition statistic :
root@Hiuhu:~# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              21G   20G     0 100% /
none                  967M  272K  967M   1% /dev
none                  973M   36K  973M   1% /dev/shm
none                  973M  252K  973M   1% /var/run
none                  973M     0  973M   0% /var/lock
/dev/sda7              37G  4.1G   31G  12% /home
/dev/sda8              13G  4.7G  7.1G  40% /usr
/dev/sda9              41G   30G   12G  73% /media/L
/dev/sda5              74G   67G  7.8G  90% /media/Local Disk
/dev/sda11             21G  5.5G   16G  27% /media/<>
/dev/sda13             20G  9.7G  9.5G  51% /media/<-->

---

### Post by oldfred on 2012-05-05
With a separate /home ( and /usr) your / of 20GB should be plenty. What are you installing or running to consume all that space. Did you run a backup that defaulted back into / ( I have done that when I forgot to mount my /backup partition). I typically only use 7GB out of my 25GB / partitions with 1GB for /home included but all data in other parittions.

HouseKeeping:
sudo apt-get update #resync package index
sudo apt-get upgrade #newest versions of all packages, update must be run first
sudo apt-get autoremove  #removes depenancies no longer needed
# removes .deb
sudo apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
Sometimes this does more?
sudo apt-get dist-upgrade  #updates dependancies

HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
HOWTO: Cleaning up all those unnecessary junk files...
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)
    Caution deborphan will delete anything you manually installed. See comment:
Better to use Synaptic to select the ones you no longer want. Also you get notified about dependencies to be removed and can reconsider, if need be.
[http://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc](http://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc)

# remove log files if no issues
cd /var/log
sudo rm -f messages.*
sudo rm -v /var/log/*.gz

Check current kernel I also keep one older just in case:
lsb_release -a
Go to Synaptic Package Manager and search for linux-image.
More info in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

#check for large files:
sudo du -h --max-depth=1 / | grep '[0-9]G\>'   # folders larger than 1GB
sudo find / -name '*' -size +1G    # files larger than 1GB
find . -maxdepth 1 -type d ! -name . -exec du -sh '{}' \; | sort -h
dpkg-query -Wf '${Installed-Size}\t${Package}\n' | sort -n
gksudo nautilus /root/.local/share/Trash/files  # Be sure to enable viewing of hidden files.

---

