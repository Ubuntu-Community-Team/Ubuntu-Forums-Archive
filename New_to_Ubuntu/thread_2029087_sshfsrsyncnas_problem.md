---
title: "sshfs/rsync/nas problem"
date: 2012-07-19
forum: New to Ubuntu
---

### Post by il pepe on 2012-07-19
Hi,
I'm trying to move files from my desktop to a NAS (Lacie's network space 2).

So if I figured i sshfs the network drive to a mount point on the desktop and perform a rsync to move all of the files (>500 gigs).

Everything was going (not fast at all, but still going, which at this moment is the most important).
But after a while the mount point is just gone, at least the sshfs connection seems to get lost, while rsync was still going strong... this happened already twice, so i figured there is a structural problem here, not a coincidence...

The second problem (and probably related) is the fact that nautilus seems to hang, especially after a sshfs drop-out....

More info?
I using ubuntu 12.04, wired connection.
Because of some problems with unity (tends to hang on this back-ups) I'm trying to do this from pure command line (like ctrl alt F1 kind of thing).

any help? 
IS sshfs the preferred way?
I tried FTP but that is slower, as is samba (did the fstab with cifs...)

best regards,
Pieter

---

### Post by richpri on 2012-07-19
I would use the scp command.

```
NAME
     scp — secure copy (remote file copy program)

SYNOPSIS
     scp [-12346BCpqrv] [-c cipher] [-F ssh_config] [-i identity_file]
         [-l limit] [-o ssh_option] [-P port] [-S program]
         [[user@]host1:]file1 ... [[user@]host2:]file2

DESCRIPTION
     scp copies files between hosts on a network.  It uses ssh(1) for data
     transfer, and uses the same authentication and provides the same security
     as ssh(1).  Unlike rcp(1), scp will ask for passwords or passphrases if
     they are needed for authentication.

     File names may contain a user and host specification to indicate that the
     file is to be copied to/from that host.  Local file names can be made
     explicit using absolute or relative pathnames to avoid scp treating file
     names containing ‘:’ as host specifiers.  Copies between two remote hosts
     are also permitted.

```

---

### Post by papibe on 2012-07-19
Hi il pepe.

Although scp would work just fine, I would recommend using rsync because if anything happens during the transfer, you just running again and rsync would take care of any inconsistency.

The option --partial will be specially useful when transferring large amount of data.

Regards.

---

