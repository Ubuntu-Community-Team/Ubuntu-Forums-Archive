---
title: "Ubuntu Server &amp; iMac: need to share files"
date: 2014-06-02
forum: New to Ubuntu
---

### Post by netrix-g on 2014-06-02
Good morning all !
I've fairly new to Ubuntu and to OS X for that matter. I have successfully installed Ubuntu 14.04 on an HP N54L micro server, I have installed and configured 3 WD Red drives as a Raid 5 array.

I have also installed a couple of apps that worked for a while, but as I try and understand Ubuntu and get things "tweaked" they have stopped working, but they are secondary to my main problem, which is:


I can see the Ubuntu server in Finder on the iMac, and I can successfully connect to it [username and password etc] - but I do not see any folders/shares so cannot share files between the two machines.
I followed a guide to use Netatalk to enable the Ubuntu server to act as a Time Machine Backup and, thankfully, that still works.

My username for both machines is the same (and password for that matter) - not sure if the username would be a problem, thought I'd mention it.
I have been doing a fair bit of Googling trying to find help from other posts etc but need to start a thread specific to my problem.

My raid array is mounted at /mnt/nas and I want to share that with the network (eventually an iMac. a macbook air and a couple of iPads - and possibly to the Internet eventually)

In OSX Finder I see the HP server, and when connected I see a folder named netrix - but cannot see anything else.

I'm assuming I have messed up the permissions but during my very steep learning curve for Ubuntu I don't think I'ver ever seen the Raid share in Finder :(

Thanks in advance for all/any help !

Regards

Netrix

---

### Post by netrix-g on 2014-06-02
… adding some outputs that may be relevant:

> netrix@HPServer:~$ sudo smbtree
Enter root's password:
HOME
    \\IMAC-NETRIX            Netrix
    \\HPSERVER               HPServer server (Samba, Ubuntu)
        \\HPSERVER\nas                
        \\HPSERVER\print$             Printer Drivers
        \\HPSERVER\IPC$               IPC Service (HPServer server (Samba, Ubuntu))
    \\BTHUB5                 BT Home Hub 5.0A File Server[INDENT]netrix@HPServer:~$[/INDENT]
[INDENT]
[/INDENT]
[INDENT]


[/INDENT]
> netrix@HPServer:~$ ls -al /home/netrix
total 68368
drwx--x--x 21 netrix netrix     4096 May 24 16:30 .
drwxr-xr-x 10 root   root       4096 May 19 12:28 ..
drwx------  3 netrix netrix     4096 May 13 12:14 .adobe
-rw-------  1 netrix netrix    25930 May 26 18:06 .bash_history
-rw-r--r--  1 netrix netrix      220 May  8 09:41 .bash_logout
-rw-r--r--  1 netrix netrix     3637 May  8 09:41 .bashrc
drwx------ 18 netrix netrix     4096 May 31 14:26 .cache
drwx------  3 netrix netrix     4096 May 15 22:32 .compiz
drwx------ 17 netrix netrix     4096 May 19 11:14 .config
-rw-------  1 netrix netrix      158 May  9 13:44 dead.letter
drwxr-xr-x  3 netrix netrix     4096 May 31 15:03 Desktop
-rw-r--r--  1 netrix netrix       25 May 13 12:06 .dmrc
drwxr-xr-x  2 netrix netrix     4096 May 13 12:06 Documents
-rw-rw-r--  1 netrix netrix 36418794 Jan 23 22:01 download
-rw-rw-r--  1 netrix netrix 33412740 Dec  6  2011 download.1
drwxr-xr-x  2 netrix netrix     4096 May 13 12:06 Downloads
drwxrwxrwx  2 root   root       4096 May  9 08:19 GBBACKUP
drwx------  3 netrix netrix     4096 May 24 16:30 .gconf
-rw-r-----  1 netrix netrix        0 May 13 15:40 .gksu.lock
drwxrwxr-x  2 netrix netrix     4096 May 13 12:14 .gstreamer-0.10
-rw-------  1 netrix netrix     3260 May 24 16:30 .ICEauthority
drwxr-xr-x  3 netrix netrix     4096 May 13 12:06 .local
drwx------  3 netrix netrix     4096 May 13 12:15 .macromedia
drwx------  4 netrix netrix     4096 May 13 12:14 .mozilla
drwxr-xr-x  2 netrix netrix     4096 May 13 12:06 Music
-rw-------  1 root   root        118 May 26 18:05 .nano_history
drwxr-xr-x  2 netrix netrix     4096 May 31 15:03 Pictures
-rw-r--r--  1 netrix netrix      675 May  8 09:41 .profile
drwxr-xr-x  2 netrix netrix     4096 May 13 12:06 Public
-rw-r--r--  1 root   root         66 May  9 12:21 .selected_editor
drwx------  2 netrix netrix     4096 May  9 08:24 .ssh
drwxr-xr-x  2 netrix netrix     4096 May 13 12:06 Templates
-rwxr--r--  1 root   root        114 May  9 13:30 testContinuous.sh
drwxr-xr-x  2 netrix netrix     4096 May 13 12:06 Videos
-rw-------  1 netrix netrix      636 May 19 12:24 .viminfo
-rw-------  1 netrix netrix       53 May 24 16:30 .Xauthority
-rw-------  1 netrix netrix      221 Jun  2 08:15 .xsession-errors
-rw-------  1 netrix netrix      942 May 23 22:34 .xsession-errors.old
netrix@HPServer:~$

and


> netrix@HPServer:~$ ls -al /mnt/nas
total 52
drwxrwxrwx 10 netrix      nogroup              4096 May 23 07:46 .
drwxr-xr-x  3 root        root                 4096 May  9 07:25 ..
drwxr-xrwx  2 root        root                 4096 May  9 15:06 data
drwxr-xrwx  2 root        root                16384 May  9 07:35 lost+found
drwxr-xrwx  7 root        root                 4096 May 13 18:42 media
drwxrwxr-x 21 netrix      netrix               4096 May 23 19:25 Seagate 1 terabyte [this is a dump of a hard drive temporarily stored here]
drwxr-xrwx  8 timemachine timemachine          4096 Jun  2 08:51 TIMEMACHINE
drwxr-xrwx  5 root        debian-transmission  4096 May 12 17:28 Transmission
drwx------  5 netrix      netrix               4096 May 23 19:29 .Trash-1000
drwxr-xrwx  6 root        root                 4096 May  9 15:06 Users
netrix@HPServer:~$ 

---

### Post by netrix-g on 2014-06-03
150 views and no help yet - probably 150 other poor souls in need of help :(

Since posting I have found out that from the iMac I have the option to log on to the Ubuntu server as a guest. If I do this I can see the raid array mounted at /mnt/nas. And I can copy and paste between the two etc. 
I cannot, however access/copy a bunch of movies that I recently copied to the server via a USB stick

if someone could point me in the right direction for things to check - I have a grasp of file/folder permissions now but still cannot fathom out where I went wrong. 

Regards

Netrix

---

### Post by netrix-g on 2014-06-06
Sorted it myself in the end

---

### Post by bapoumba on 2014-06-06
That would be good to others if you posted how you got it solved. Maybe noone knew how to help you, or the ones knowing did not stumble upon your thread (we are international forums, people live in all timezones and the forums are busy). In any case, we are a community resource, thanks :)

---

