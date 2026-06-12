---
title: "Backuppc dreaded Last error is &quot;Unable to read 4 bytes&quot;.  failure"
date: 2008-10-02
forum: New to Ubuntu
---

### Post by noahclark on 2008-10-02
Good day!

I have the ssh keys working for rsync and so I know that is working correctly, however, I get the "Last error is "Unable to read 4 bytes"." error whenever I try to run the backup from the web interface in backuppc.  See Below for my config files.

here is my 192.168.0.4.pl file
```
$Conf{XferMethod} = 'rsync';
$Conf{CompressLevel} = 9;
$Conf{RysncClientPath} = '/usr/bin/rsync';
$Conf{RsyncShareName} = '/';
$Conf{RsyncClientRestoreCmd} = '$sshPath -q -x -l backuppc $hostIP $rsyncPath $argList+';
$Conf{RsyncClientCmd} = '$sshPath -q -x -l backuppc $rsyncPath $argList+';

```

and here is my hosts file 
```
#============================================================= -*-perl-*-
#
# Host file list for BackupPC.
#
# DESCRIPTION
#
#   This file lists all the hosts that should be backed up by
#   BackupPC.
#
#   Each line in the hosts file contains three fields, separated
#   by white space:
#
#     - The host name.  If this host is a static IP address this
#       must the machine's IP host name (ie: something that can
#       be looked up using nslookup or DNS).  If this is a DHCP
#       host then the host name must be the netbios name of the
#       machine.  It is possible to have a host name that contains
#       spaces, but that is discouraged.  Escape a space with "\", eg:
#
#                craigs\ pc
#
#     - DHCP flag.  Set to 0 if this is a static IP address host
#       or if the machine can be found using nmblookup.  Otherwise,
#       if the client can only be found by looking through the DHCP
#       pool then set this to 1.
#
#     - User name (unix login/email name) of the user who "owns"
#       or uses this machine.  This is the user who will be sent
#       email about this machine, and this user will have permission
#       to stop/start/browse/restore backups for this host.  This
#       user name must match the name the user authenticates with
#       via apache.
#
#     - Optional additional user names (comma separated, no white space) of
#       users who are also allowed to stop/start/browse/restore backups
#       for this client via the CGI interface.  These users are not sent
#       email.  These do not need to be valid email names; they simply
#       need to match the name the user authenticates with via apache.
#
# AUTHOR
#   Craig Barratt  <craig@arraycomm.com>
#
# COPYRIGHT
#   Copyright (C) 2001  Craig Barratt
#
#   See http://backuppc.sourceforge.net.
#
#========================================================================

#
# The first non-comment non-empty line gives the field names and should
# not be edited!!
#
host        dhcp    user    moreUsers     # <--- do not edit this line
#farside    0       craig   jill,jeff     # <--- example static IP host entry
#larson     1       bill                  # <--- example DHCP host entry
server	0	backuppc	
PEACHTREE 0 backuppc
192.168.0.4 0 backuppc
Dj95plf1 0 backuppc


```

Thanks in advance!

---

### Post by noahclark on 2008-10-02
Do I need to have an rsync server of sorts up and running on the backup machine or can I just have rsync installed?

EDIT:

I ran the command: 

```
sudo rsync --delete -azvv -e ssh /home/backuppc backuppc@192.168.0.4:./home/backuppc
```

and then did a >>log.txt and even though it complains about bad keys not working, the log.txt file looks like it worked just fine.  I think I need to set backuppc user to have access to all of the file system.  How would I go about doing that?

Thanks!

---

