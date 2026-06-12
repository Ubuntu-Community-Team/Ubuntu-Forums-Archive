---
title: "Power interrupted during upgrade, now root files won't mount."
date: 2014-07-17
forum: New to Ubuntu
---

### Post by trooperchix on 2014-07-17
I have an old Dell Inspiron 1420 laptop that was running a 13.xx version of ubuntu.  I cannot recall which version, and I was in the midst of upgrading to 14.04 LTS when my cord was pulled from the side of the laptop and the power was interrupted.  I have a bad batttery.  When I turn the laptop on in the attempt to continue/finish the upgrade, the system is unable to mount several root files to even complete the boot.  I am online now using the cd.  I will go through boot again and write down what it says and post it up here.  I had tried to access the files to simply back them up using my 14.04 LTS live disc, and the problem I am having with that is permissions.  It won't let me open or move the files because of the above issue.  Any help would be much appreciated.  Thanks.

---

### Post by Bashing-om on 2014-07-17
trooperchix; "Were not for bad luck --"

We can try and salvage the install. Let's try the easier approach 1st and see if we can access/fix the file system.
From liveDVD of 14.04 so everything is unmounted,swap off if necessary ( may be checked from GParted), change example shown with partition sda1 to your partition(s) as shown by the output of 'fdisk'.
```

sudo fdisk -lu
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required#
sudo e2fsck -C0 -p -f -v /dev/sda1
#if errors: -y auto answers yes for fixes needing response see:
man e2fsck
sudo e2fsck -f -y -v /dev/sda1

```
If the file system check is positive, try and access your install from the liveDVD, just as a check/verification for the next step(s):
assuming here that your root is installed to the 1st hard disk and on the 1st partition, if not adjust your syntax.
```

sudo mkdir /mnt/work
sudo mount /dev/sda1 /mnt/work
ls -la /mnt/work
##Any output here is a good thing. Do the files look good to you ? ##
ls -la /mnt/work/home/trooperchix ##substitute your -username- on the system if different than trooperchix ##
##Do you see your personal Files ?

```
At this point we are just look'n, We may be back. For now lets back out and reboot and see if you can boot into the install.
```

sudo umount /mnt/work

```

Reboot into the install and advise of status. We then consider what it is going to take to complete the upgrade to 14.04.

[INDENT][INDENT][INDENT]hey, it could happen
[/INDENT][/INDENT][/INDENT]

---

### Post by trooperchix on 2014-07-17
Ok, here goes..

---

### Post by trooperchix on 2014-07-17
So I followed your instructions as closely as I could understand them (copy and paste save for the username update).  I'm getting the impression it may be easier to somehow change the permissions on the home folder on those locked files in the home file so I can just back those up through the live dvd do a clean install.  Here's a printout off terminal of what I get when I run your commands from the first box:

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00004cd2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   308406271   154202112   83  Linux
/dev/sda2       308408318   312580095     2085889    5  Extended
/dev/sda5       308408320   312580095     2085888   82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda1
                                                                               
      136465 inodes used (1.42%, out of 9641984)
        1764 non-contiguous files (1.3%)
          75 non-contiguous directories (0.1%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 132987/2141/8
    32852532 blocks used (85.22%, out of 38550528)
           0 bad blocks
           9 large files

      116500 regular files
       17291 directories
           0 character device files
           0 block device files
           0 fifos
           0 links
        2663 symbolic links (1317 fast symbolic links)
           2 sockets
------------
      136456 files
ubuntu@ubuntu:~$ sudo e2fsck -f -y -v /dev/sda1
e2fsck 1.42.9 (4-Feb-2014)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

      136465 inodes used (1.42%, out of 9641984)
        1764 non-contiguous files (1.3%)
          75 non-contiguous directories (0.1%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 132987/2141/8
    32852532 blocks used (85.22%, out of 38550528)
           0 bad blocks
           9 large files

      116500 regular files
       17291 directories
           0 character device files
           0 block device files
           0 fifos
           0 links
        2663 symbolic links (1317 fast symbolic links)
           2 sockets
------------
      136456 files
ubuntu@ubuntu:~$ 
```

I don't know what a positive result should be on these tests.  If you mean go back into the partition and try and view one of the locked files, I'm still locked out.  Onward to your second box of commands:

```
ubuntu@ubuntu:~$ sudo mkdir /mnt/work
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt/work
ubuntu@ubuntu:~$ ls -la /mnt/work
total 84
drwxr-xr-x 17 root root  4096 Jan 21 21:58 .
drwxr-xr-x  1 root root    60 Jul 18 00:24 ..
drwxr-xr-x  3 root root 12288 Jan 17 07:57 boot
drwxr-xr-x  2 root root  4096 May 20  2011 cdrom
drwxr-xr-x  2 root root  4096 Jan 21 21:58 etc
drwxr-xr-x  3 root root  4096 May 20  2011 home
lrwxrwxrwx  1 root root    33 Jan 16  2014 initrd.img.old -> /boot/initrd.img-3.8.0-35-generic
lrwxrwxrwx  1 root root    34 Jan 15  2014 libnss3.so -> /usr/lib/i386-linux-gnu/libnss3.so
drwx------  2 root root 16384 May 20  2011 lost+found
drwxr-xr-x  4 root root  4096 Jan 16 21:25 media
drwxr-xr-x  2 root root  4096 Apr 21  2011 mnt
drwxr-xr-x  5 root root  4096 Jan 16 21:04 opt
drwx------ 23 root root  4096 Dec 31  2013 root
drwxr-xr-x  2 root root  4096 Jul 14  2011 run
drwxr-xr-x  2 root root  4096 Apr 25  2011 srv
drwxrwxrwt  7 root root  4096 Jan 17 08:20 tmp
drwxr-xr-x  2 root root  4096 Jan 21 21:53 ubiquity-apt-clone
drwxr-xr-x  4 root root  4096 Jan 21 21:57 usr
drwxr-xr-x  4 root root  4096 Jan 21 21:57 var
ubuntu@ubuntu:~$ 
```

You ask me if everything looks ok.  To me, it looks ok, but then again I'm sadly not an ubuntu ninja.  More like a tyke.  And onward:

```
ubuntu@ubuntu:~$ ls -la /mnt/work/home/eddie
total 52516
drwxr-xr-x  62 1000 1000     12288 Jan 17 05:57 .
drwxr-xr-x   3 root root      4096 May 20  2011 ..
drwxr-xr-x   2 1000 1000      4096 Oct 25  2011 acetonefolder
drwxr-xr-x   2 1000 1000      4096 Oct 27  2011 .acetoneiso
drwx------   5 1000 1000      4096 Dec 14  2011 .adobe
-rw-------   1 1000 1000      4733 Dec 31  2013 .bash_history
-rw-r--r--   1 1000 1000       220 May 20  2011 .bash_logout
-rw-r--r--   1 1000 1000      3353 May 20  2011 .bashrc
drwx------   2 1000 1000      4096 May 21  2011 .bogofilter
drwx------  37 1000 1000      4096 Jan 16 21:45 .cache
drwxr-xr-x 294 1000 1000     12288 Oct  5  2013 Calibre Library
drwx------   2 1000 1000      4096 Sep 15  2010 .camel_certs
-rw-rw-r--   1 1000 1000       576 Jan 16 21:00 C:\nppdf32Log\debuglog.txt
drwx------   3 1000 1000      4096 Jan 15  2014 .compiz
drwxrwxr-x   3 1000 1000      4096 Nov  5  2011 .compiz-1
drwxr-xr-x  41 1000 1000      4096 Jan 16 22:25 .config
drwxr-xr-x   2 1000 1000      4096 Sep 24  2011 converter
-rw-------   1 1000 1000 134000640 Sep 21  2012 core
drwx------   3 1000 1000      4096 May 21  2011 .dbus
drwxr-xr-x  32 1000 1000      4096 Dec 31  2013 Desktop
-rw-r--r--   1 1000 1000       145 Oct 27  2011 .devede
-rw-r--r--   1 1000 1000        93 Jan 17 05:57 .dmrc
-rw-rw-r--   1 1000 1000        63 Apr 24  2013 doc_data.txt
drwxr-xr-x  40 1000 1000      4096 Jun 27  2013 Documents
drwxr-xr-x  16 1000 1000      4096 Jan 16 22:43 Downloads
drwxr-xr-x   2 1000 1000      4096 Jan 27  2013 dwhelper
drwxr-x---   2 1000 1000      4096 Sep 24  2011 .easytag
drwx------   2 1000 1000      4096 Jun 15  2011 Ebooks
-rw-------   1 1000 1000        16 May 21  2011 .esd_auth
drwx------   3 1000 1000      4096 May 21  2011 .evolution
-rw-r--r--   1 1000 1000       179 May 20  2011 examples.desktop
-rw-rw-r--   1 1000 1000   8720946 Aug 28  2012 Firefox_wallpaper.png
-rw-r--r--   1 1000 1000    609557 Jul 16  2011 fm4jessicaluniewski
-rw-r--r--   1 1000 1000    427483 Jul 16  2011 fm4thomasluniewski
drwxr-xr-x   2 1000 1000      4096 Jan 15  2014 fontconfig
drwxr-xr-x   2 1000 1000      4096 Jan 15  2014 .fontconfig
drwxr-xr-x   2 1000 1000      4096 Oct 25  2011 .furiusisomount
drwx------   5 1000 1000      4096 Jan 17 07:57 .gconf
drwx------   2 1000 1000      4096 Nov  5  2011 .gconfd
drwx------   4 1000 1000      4096 May 21  2011 .gegl-0.0
drwxr-xr-x  22 1000 1000      4096 May  6  2013 .gimp-2.6
-rw-r-----   1 1000 1000         0 Jan 14  2014 .gksu.lock
drwx------   7 1000 1000      4096 Jan 16  2014 .gnome2
drwx------   2 1000 1000      4096 May 21  2011 .gnome2_private
-rw-------   1 1000 1000         0 Apr 16  2013 .goutputstream-06SJVW
-rw-------   1 1000 1000         0 Sep  4  2012 .goutputstream-0QZFKW
-rw-------   1 1000 1000         0 Aug 20  2012 .goutputstream-0VFVJW
-rw-------   1 1000 1000         0 Jul 25  2012 .goutputstream-0ZI5HW
-rw-------   1 1000 1000         0 Dec  7  2012 .goutputstream-0ZV8OW
-rw-------   1 1000 1000         0 May 26  2013 .goutputstream-1EQYXW
-rw-------   1 1000 1000         0 Feb 18  2013 .goutputstream-1IT2SW
-rw-------   1 1000 1000         0 Jun 14  2012 .goutputstream-1KATFW
-rw-------   1 1000 1000         0 Jul 24  2012 .goutputstream-22UWHW
-rw-------   1 1000 1000         0 Mar  4  2013 .goutputstream-28OQTW
-rw-------   1 1000 1000         0 May  5  2013 .goutputstream-2ANKWW
-rw-------   1 1000 1000         0 Jun  2  2013 .goutputstream-2IZOXW
-rw-------   1 1000 1000         0 Jul 13  2013 .goutputstream-2XKK0W
-rw-------   1 1000 1000         0 Jul  4  2012 .goutputstream-2ZHVGW
-rw-------   1 1000 1000         0 Feb  7  2013 .goutputstream-3JWFSW
-rw-------   1 1000 1000         0 Aug  5  2012 .goutputstream-3PTGIW
-rw-------   1 1000 1000         0 Jan 16  2014 .goutputstream-3UBH9W
-rw-------   1 1000 1000         0 Dec 24  2012 .goutputstream-41VNPW
-rw-------   1 1000 1000         0 Jan  4  2013 .goutputstream-447PQW
-rw-------   1 1000 1000         0 Jul 12  2012 .goutputstream-4UU4GW
-rw-------   1 1000 1000         0 Mar  3  2013 .goutputstream-4UZQTW
-rw-------   1 1000 1000         0 May  2  2013 .goutputstream-4V7XWW
-rw-------   1 1000 1000         0 Aug 11  2012 .goutputstream-51FNIW
-rw-------   1 1000 1000         0 Nov 24  2013 .goutputstream-7SK96W
-rw-------   1 1000 1000         0 Sep 27  2012 .goutputstream-8NVDLW
-rw-------   1 1000 1000         0 Jul 17  2013 .goutputstream-95I8ZW
-rw-------   1 1000 1000         0 Aug 18  2012 .goutputstream-9ZFXIW
-rw-------   1 1000 1000         0 Jun 26  2012 .goutputstream-A5YOGW
-rw-------   1 1000 1000         0 Jul  9  2013 .goutputstream-AIYMZW
-rw-------   1 1000 1000         0 Aug 22  2012 .goutputstream-ALWQJW
-rw-------   1 1000 1000         0 Apr  5  2013 .goutputstream-B15IUW
-rw-------   1 1000 1000         0 Jun 22  2013 .goutputstream-BAP0YW
-rw-------   1 1000 1000         0 Jul 25  2012 .goutputstream-BJIYHW
-rw-------   1 1000 1000         0 Aug  9  2013 .goutputstream-CDAP1W
-rw-------   1 1000 1000         0 Jul 12  2012 .goutputstream-CU9UGW
-rw-------   1 1000 1000         0 Oct  4  2012 .goutputstream-D2S8KW
-rw-------   1 1000 1000         0 Jan  4  2013 .goutputstream-D90PQW
-rw-------   1 1000 1000         0 Jun 16  2012 .goutputstream-DD3JFW
-rw-------   1 1000 1000         0 Jan 23  2013 .goutputstream-F2WXQW
-rw-------   1 1000 1000         0 Oct 18  2012 .goutputstream-F56LMW
-rw-------   1 1000 1000         0 Sep  1  2012 .goutputstream-FG66JW
-rw-------   1 1000 1000         0 Jul  1  2013 .goutputstream-FJCPZW
-rw-------   1 1000 1000         0 May 18  2013 .goutputstream-FQ7HXW
-rw-------   1 1000 1000         0 Jun 20  2013 .goutputstream-G1DHZW
-rw-------   1 1000 1000         0 Jul 11  2012 .goutputstream-G2W5GW
-rw-------   1 1000 1000         0 Sep  7  2012 .goutputstream-G936JW
-rw-------   1 1000 1000         0 Apr  5  2013 .goutputstream-GAEPUW
-rw-------   1 1000 1000         0 Jan 15  2014 .goutputstream-GIAL9W
-rw-------   1 1000 1000         0 Feb 18  2013 .goutputstream-GN7RSW
-rw-------   1 1000 1000         0 Jul 18  2013 .goutputstream-HOOP0W
-rw-------   1 1000 1000         0 May  7  2013 .goutputstream-IHMMWW
-rw-------   1 1000 1000         0 Nov  8  2012 .goutputstream-IJ7ANW
-rw-------   1 1000 1000         0 Jan 16  2013 .goutputstream-IVY1QW
-rw-------   1 1000 1000         0 Mar 28  2013 .goutputstream-J18JUW
-rw-------   1 1000 1000         0 Jun 27  2013 .goutputstream-JWK6YW
-rw-------   1 1000 1000         0 Jul  3  2012 .goutputstream-JXT5GW
-rw-------   1 1000 1000         0 May 14  2013 .goutputstream-K4IFXW
-rw-------   1 1000 1000         0 Jan 15  2014 .goutputstream-K8P19W
-rw-------   1 1000 1000         0 Oct  6  2013 .goutputstream-KA9S4W
-rw-------   1 1000 1000         0 Oct  8  2013 .goutputstream-KV7I4W
-rw-------   1 1000 1000         0 Nov 28  2012 .goutputstream-L1KKOW
-rw-------   1 1000 1000         0 Nov  7  2012 .goutputstream-L3YDNW
-rw-------   1 1000 1000         0 Apr 23  2013 .goutputstream-LG07VW
-rw-------   1 1000 1000         0 Apr 10  2013 .goutputstream-LL27UW
-rw-------   1 1000 1000         0 Aug 14  2013 .goutputstream-LLAT1W
-rw-------   1 1000 1000         0 Mar 12  2013 .goutputstream-LT8RTW
-rw-------   1 1000 1000         0 Jul 30  2012 .goutputstream-MJ19HW
-rw-------   1 1000 1000         0 Sep  8  2012 .goutputstream-MTY0JW
-rw-------   1 1000 1000         0 Jun 30  2012 .goutputstream-N3CHGW
-rw-------   1 1000 1000         0 Oct 11  2013 .goutputstream-NT524W
-rw-------   1 1000 1000         0 Jun 20  2013 .goutputstream-O7R8YW
-rw-------   1 1000 1000         0 Apr 18  2013 .goutputstream-OAG7UW
-rw-------   1 1000 1000         0 Jun 28  2012 .goutputstream-OBOLGW
-rw-------   1 1000 1000         0 Feb 21  2013 .goutputstream-OY71SW
-rw-------   1 1000 1000         0 Sep 15  2013 .goutputstream-OYVP3W
-rw-------   1 1000 1000         0 May 14  2013 .goutputstream-PTGFXW
-rw-------   1 1000 1000         0 May 30  2012 .goutputstream-PYNXEW
-rw-------   1 1000 1000         0 Sep 13  2012 .goutputstream-QM1OKW
-rw-------   1 1000 1000         0 Jun 30  2013 .goutputstream-QWVNZW
-rw-------   1 1000 1000         0 Oct 20  2012 .goutputstream-S54GMW
-rw-------   1 1000 1000         0 May  9  2013 .goutputstream-SOADWW
-rw-------   1 1000 1000         0 May 28  2013 .goutputstream-SYS6XW
-rw-------   1 1000 1000         0 Jan 25  2013 .goutputstream-T55XRW
-rw-------   1 1000 1000         0 Oct  5  2012 .goutputstream-T9KQLW
-rw-------   1 1000 1000         0 Jul  9  2013 .goutputstream-UB4RZW
-rw-------   1 1000 1000         0 Jun 29  2012 .goutputstream-V00DGW
-rw-------   1 1000 1000         0 Jun 24  2013 .goutputstream-V7XZYW
-rw-------   1 1000 1000         0 Sep 12  2012 .goutputstream-WG4KKW
-rw-------   1 1000 1000         0 Jul  8  2012 .goutputstream-WQ4CHW
-rw-------   1 1000 1000         0 Jun 21  2013 .goutputstream-YB2VYW
-rw-------   1 1000 1000         0 Jul 29  2013 .goutputstream-YEUU0W
-rw-------   1 1000 1000         0 Jul  4  2012 .goutputstream-Z3EAHW
-rw-------   1 1000 1000         0 Sep 21  2012 .goutputstream-Z3VKKW
-rw-------   1 1000 1000         0 Nov  6  2012 .goutputstream-Z416MW
-rw-------   1 1000 1000         0 Jan 14  2014 .goutputstream-ZGTW9W
-rw-------   1 1000 1000         0 Oct 30  2012 .goutputstream-ZISJMW
-rw-------   1 1000 1000         0 Aug 17  2012 .goutputstream-ZX91IW
drwxr-xr-x   2 1000 1000      4096 Jan 16 21:15 .gstreamer-0.10
-rw-rw-r--   1 1000 1000       137 Jan 16 22:06 .gtk-bookmarks
-rw-rw-r--   1 1000 1000       137 Jun 27  2013 .gtk-bookmarks.P1C2YW
drwx------   2 1000 1000      4096 May 21  2011 .gvfs
-rw-rw-r--   1 1000 1000     90181 Apr 15  2012 hd_service.pdf
drwxr-----   2 1000 1000      4096 Jan 17 08:13 .hplip
-rw-------   1 1000 1000    205520 Jan 17 05:57 .ICEauthority
drwxr-xr-x   5 1000 1000      4096 May 25  2011 .icedtea
drwxr-xr-x   2 1000 1000      4096 Jan 16 22:57 .icons
drwx------   3 1000 1000      4096 Oct 26  2011 .kde
-rw-rw-r--   1 1000 1000         0 Jun 19  2013 libpeerconnection.log
drwxr-xr-x   3 1000 1000      4096 May 23  2011 .libreoffice
drwxr-xr-x   3 1000 1000      4096 May 21  2011 .local
drwx------   3 1000 1000      4096 May 21  2011 .macromedia
drwx------   3 1000 1000      4096 May 27  2011 .mission-control
drwx------   5 1000 1000      4096 Sep  2  2011 .mozilla
drwxr-xr-x   2 1000 1000      4096 Oct 13  2011 .mplayer
-rw-r--r--   1 1000 1000         0 Oct 27  2011 .mtab.fuseiso
drwxr-xr-x 245 1000 1000     12288 Feb 14  2012 Music
drwxr-xr-x   2 1000 1000      4096 Aug 17  2011 My Kindle Content
-rw-r--r--   1 1000 1000    378707 Aug 15  2011 newthreat
drwxrwxr-x  23 1000 1000      4096 Sep 10  2012 Nonnaubusiness
drwxr-x---   6 1000 1000      4096 Nov 24  2011 .openshot
-rw-r--r--   1 1000 1000        35 Jul 24  2012 .pam_environment
drwxr-xr-x   4 1000 1000      4096 Sep 17  2012 Pictures
drwx------   3 1000 1000      4096 May 21  2011 .pki
-rw-r--r--   1 1000 1000       675 Jul 24  2012 .profile
drwxr-xr-x   2 1000 1000      4096 May 21  2011 Public
drwx------   2 1000 1000      4096 Jan 16  2014 .pulse
-rw-------   1 1000 1000       256 May 21  2011 .pulse-cookie
drwx------   5 1000 1000      4096 May  6  2013 .purple
drwx------   3 1000 1000      4096 Dec 31  2013 .sane
drwxr-xr-x   4 1000 1000      4096 Apr 13  2012 .shotwell
drwx------   6 1000 1000      4096 Nov 24  2013 .Skype
drwxr-xr-x   2 1000 1000      4096 Oct 13  2011 .spumux
-rw-r--r--   1 1000 1000         0 May 23  2011 .sudo_as_admin_successful
drwxr-xr-x   2 1000 1000      4096 May 21  2011 Templates
drwxr-xr-x   2 1000 1000      4096 May 21  2011 .themes
drwx------   5 1000 1000      4096 Feb  6  2013 .thumbnails
drwxrwxr-x   2 1000 1000      4096 May 21  2011 Ubuntu One
drwxr-xr-x   2 1000 1000      4096 Oct 27  2011 Videos
drwxr-xr-x   4 1000 1000      4096 Jul  9  2013 .wine
-rw-------   1 1000 1000        56 Jan 17 05:57 .Xauthority
drwxr-xr-x   8 1000 1000      4096 Sep 21  2012 .xbmc
-rw-rw-r--   1 1000 1000       655 Sep 21  2012 xbmc_crashlog-20120921_034617.log
-rw-r--r--   1 1000 1000       834 Jun 26  2011 .xscreensaver-getimage.cache
-rw-------   1 1000 1000    707810 Jan 17 08:13 .xsession-errors
-rw-------   1 1000 1000      4876 Jan 17 05:45 .xsession-errors.old
ubuntu@ubuntu:~$ 
```

Yes, I see my personal files.  At least I see mention of my desktop and document files that have much of what I need saved.  I ran that last little bit:

```
ubuntu@ubuntu:~$ sudo umount /mnt/work
ubuntu@ubuntu:~$ 
```

I do not understand what you mean by reboot into my install.  Disk out?  It goes back to not mounting the root files of my original ubuntu partition.  With the disk it looks like it wants to do a fresh install, and I am a bit terrified to let it go because I have files I have to back up.  

Thanks again ahead of time.

---

### Post by steeldriver on 2014-07-17
What is the exact error message when you try to boot without the live disk? "unable to mount several root files" is a bit difficult to decipher

---

### Post by trooperchix on 2014-07-17
mount: mounting on /dev on /root/dev failed: no such file or directory
mount: mounting on /sys on /root/sys failed: no such file or directory
mount: mounting on /proc on /root/proc failed: no such file or directory

Target file system doesn't have requested /sbin/init.  No init found.
Try passing init=bootarg.

That is what I get upon boot.  Thanks again.

---

### Post by trooperchix on 2014-07-17
Ran Boot Repair.  Not so repaired.  In fact, it's worse.  My system is reacting as if the hard drive isn't even installed, though it is recognized when I use the live cd.  Odd.  Anyway, here's the Boot Repair results [http://paste.ubuntu.com/7812166](http://paste.ubuntu.com/7812166)  Thanks again.

---

### Post by Bashing-om on 2014-07-17
trooperchix; Hey;
Guardian Angel, steeldriver. looking over our shoulder.

From all indications, I do not think the install is a lost cause at all.

File system check is good, files are in place and the errors on booting the install are grub (booting) related, We will have to at some point change the files in your home directory back to you and complete the upgrade. All perhaps no big deal.

Iffen ya game for it, we can start again and try and (RE-)install grub and see what then results ( now that we are certain what/where we are working with/from).

Here goes:
Boot up the liveDVD , and even though the versions are different I think there is a good chance will work well enough for us to at least be able to boot from the install grub prompt . - when we get at least a grub > prompt, we can make the boot -
```

sudo mount /dev/sda1 /mnt
sudo grub-install --boot-directory=/mnt /dev/sda
Code:sudo umount /mnt

```

And hey .. this is also an institution of teaching, if ya do not understand, or want to know .. pause me and ask ! .. Someone will respond and answer - more thoughtful questions get more thoughtful answers -

Now, let's see what is -> reboot into the real install and advise the exact results.

Depending on what results here is what actions we will then take.

[INDENT][INDENT]where are those deep salvage license [/INDENT][/INDENT]

---

### Post by trooperchix on 2014-07-18
Rock on, I'm game.  Ok, I followed what you posted and did a reboot into the real install.  It booted this time, before it was just saying missing operating system.  Now it goes into GRUB (I think):

[INDENT]GNU GRUB version 2.02~beta2-9[/INDENT]

Minimal BASH-like line editing is supported.  For the first word, TAB lists
possible command completions.  Anywhere else TAB lists possible device
or file completions.

grub>

---

### Post by Bashing-om on 2014-07-18
trooperchix; Hey !

We are making progress .

OK, I am done for this session, but I will leave at this 1st stab at booting up from the grub prompt - just a stab more or less to see what results, BUT, might boot !
From the grub > prompt:
```

linux (hd0,msdos1)/vmlinuz root=/dev/sda1 ro
initrd (hd0,msdos1)/initrd.img
boot

```
What results, exactly - in the event it does not boot - so we get a idea of what grub is hunting for and not finding.

[INDENT][INDENT]the game is on
[/INDENT][/INDENT]

---

### Post by trooperchix on 2014-07-18
I run the following line of command:

grub> linux (hd0,msdos1)/vmlinuz root=/dev/sda1 ro

error: file '/vmlinuz' not found.

Am I missing a file?  I'm in way over my head, I don't know what to ask to resolve this.  Thanks.  :)

---

### Post by Bashing-om on 2014-07-18
trooperchix; Morning;

No great big thing (yet):
> 
Am I missing a file? I'm in way over my head, I

I expect the file is there, just that grub does not know where it is .. we need to tell grub ( a couple of ways to do so ).

I am disappointed though that grub can not find it's files. Means we have to work harder, longer !

Let's do some poking about and see what grub is aware of, and then try and inform grub about it's files.

Now, my thinking is literal and in sequence, not sorry about the way I think -- hey, I feel good I can think at all .. but the cost is slow in my processes.
Now we are at the step to see what grub knows, and I want to know this before a next step in the process.
So, what returns from the grub command:
```

set

``` yeah just that little word .. to see what parameters, paths and locales grub knows about.

Will be a bit of effort to get the info back to the forum: - no copy/paste capability at the grub > prompt - 
a) take a photograph and paste it
b) hand copy the result and (maybe) a  LOT of typing to transcribe back to the thread.

Well, just a bit of parallel thinking: Also what returns from grub commands:
```

search -f /vmlinuz
search -f /sbin/init
ls -la /initrd.img
ls -la (hd0,msdos1)/boot/grub/grub.cfg

```
We get booted into the operating system then we have:
1) reset /home permissions
2) Finish the upgrade ( a process in and of it's self )
3) then fix grub to boot properly .


[INDENT][INDENT][INDENT]what is your thought ? Any errors in my think'n you can see ?

[INDENT][INDENT][INDENT]we are on our mark
[INDENT][INDENT][INDENT]getting set , to go
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by trooperchix on 2014-07-18
Ok, here goes:

grub> set
cmdpath=(hd0)
color_highlight=black/light-gray
color_normal=light-gray/black
feature_200_final=y
feature_all_video_module=y
feature_chainloader_bpb=y
feature_defaul_font_path=y
feature_menuentry_id=y
feature_menuentry_options=y
feature_nativedisk_cmd=y
feature_ntldr=y
feature_platform_search_hint=y
feature_timeout_style=y
grup_cpu=i386
grub_platform=pc
lang=
locale_dir=
pager=
prefix=(hd0,msdos1)/grub
root=hd0,msdos1
socondary_locale_dir=
grub>

---

### Post by trooperchix on 2014-07-18
grub> search -f /vmlinuz
error: no such device /vmlinuz.

grub> search -f /sbin/init
error: no such device /sbin/init.

grub> ls -la /initrd.img
error: file 'initrd.img' not found.

grub> ls -la (hd0,msdos1)/boot/grub/grub.cfg
grub.cfg
grub>

---

### Post by Bashing-om on 2014-07-18
trooperchix; Hummm,,

Strange as "root' is set:
> 
root=hd0,msdos1
 as we know to be correct from the livedvd 'fdisk' that '/' is indeed sda1 ( hd0=1st Hard disk -sda- , msdos1 = 1st partition -sda1-)
And grub can not find it's files when the path is set ???
OK, let's look
grub command:
```

ls -lh (hd0,msdos1)
ls -lh (hd0,msdos1)/boot
Language and locale not set is not as important presently as the locating the kernel (vmlinuz) and the INITialRamdDevideIMGage ( initrd.img) files.

```

Maybe the symbolic links to the actual files have been dropped ?? 
Don't know, but I am going to reboot at this time to grub on my system and verify 14.04 still works the way I expect it to ( from former release experience).

Won't take me long.

[INDENT][INDENT]safety is no accident
[/INDENT][/INDENT]

---

### Post by trooperchix on 2014-07-18
This is what I got.  It appears the files are there.  Could the issue with root being set as root=hd0,msdos1 because I ran that boot repair program I mentioned earlier?  It's a thought.

[[IMG]http://i46.photobucket.com/albums/f115/Trooperchix/IMAG0192_zps94907f0f.jpg[/IMG]](http://s46.photobucket.com/user/Trooperchix/media/IMAG0192_zps94907f0f.jpg.html)

P.S. thanks for the idea on using a picture, I'd been typing for awhile...

---

### Post by steeldriver on 2014-07-18
I'm wondering if it would be a good idea to chroot into the system from a live disk/USB and make sure that any pending kernel updates got finished e.g.

```

apt-get update

apt-get -f install

```

I'd also perhaps suggest a manual

```

update-initramfs -u

```

at the end of all that (although likely any kernel upgrades will do that anyway as a post-install step) since the original error message makes me suspect the original issue might have been related to the initial ram image somehow - an extra one shouldn't hurt any

---

### Post by trooperchix on 2014-07-18
what does it mean to chroot into the system, and does that involve any extra coding than what you posted?

---

### Post by Bashing-om on 2014-07-18
@steeldriver; Yeah, that thought is in my mind also. Can do wonderful things in that Full CHange Root environment.
However, I would like to explore further if the image and initrd.img files do exist and if we can boot, if we give grub the explicit path and files.

@trooperchix IRT boot-repair. A wonderful tool .. and has worked wonders for many, and should have worked on your single drive/ operating system .. But to be real honest using it on my system is a big part of my gaining the knowledge I have of grub in that in using it, it did not effect a repair of my booting situation and I did spend the time and effort to learn grub to a great degree. Be advised though that I multi-boot on multi hard drives.

To the issue at hand. 
The upgrade could not have progressed far as the installed kernels are still at 12.04 versions with hardware stack enablement.
Now in this situation here is what gets me, IF root, prefix, linux, and initrd are correct then the operating system should boot with:
the code we have tried:
```

linux (hd0,msdos1)/vmlinuz root=/dev/sda1 ro
initrd (hd0.msdos1)/initrd.img
boot

```
Huh ? It don't !
Also from my experience the file "/boot/grub/grub.cfg" must be correct , here, grub has found it. This file is a part of that stage 2 booting process ( parsed by normal.mod ??).

With the above in mind, before we dig in deeper, let's "try" this method:
```

linux (hd0,msdos1)/boot/vmlinuz-3.8.0-35-generic root=/dev/sda1 ro
initrd (hd0,msdos1)/boot/initrd.img-3.8.0-35-generic
boot

```
Now, what we do not know is the UUID that is sda1 that has to match what is in grub.cfg
and remains to be determined -> WHY is '/sbin/init/' not found ... and that may be a great big biggy.
And in addition we do not know what is taking place in the kernel space during the boot ( that is where rebuilding initramfs from the CH Root environment may come in !).

If it fails to boot I will not be too discouraged .

It is a process
[INDENT][INDENT][INDENT]let's make it work
[/INDENT][/INDENT][/INDENT]

---

### Post by trooperchix on 2014-07-18
Ok, I think we are getting close.  I ran that second box of code, everything went beautifully but the boot pooped out on me part way through.  Things scrolled by so fast I don't know how to get all that info down.  Below is the last screen's full of info viewable. 

[[IMG]http://i46.photobucket.com/albums/f115/Trooperchix/IMAG0207_zps9bb279a3.jpg[/IMG]](http://s46.photobucket.com/user/Trooperchix/media/IMAG0207_zps9bb279a3.jpg.html)

Then after I type boot:

[[IMG]http://i46.photobucket.com/albums/f115/Trooperchix/IMAG0208_zpscdefb8eb.jpg[/IMG]](http://s46.photobucket.com/user/Trooperchix/media/IMAG0208_zpscdefb8eb.jpg.html)

Like I said, it poops out.  It's trying though.  :)

---

### Post by Bashing-om on 2014-07-18
trooperchix; Weeeelll,

1st appears to be a typo on your part in that the ending ')' on "(hd0,msdos1)" looks to be a '0' .. Not our biggest problem .. 
Still with not finding "/sbin/init" .... Let's see if it exist .. 
from the grub prompt, grub command:
```

ls -lh (hd0,msdos1)/sbin/init

```
I will compare the file size to mine ( I also have 12.04 installed on this box), very real possibility that the file has become corrupted in the upgrade to 14.04 process. 
As noted above the status of the 'init' file concerns me greatly.

It is a step we have to have.

[INDENT][INDENT][INDENT]work'n on that process of booting
[/INDENT][/INDENT][/INDENT]

---

