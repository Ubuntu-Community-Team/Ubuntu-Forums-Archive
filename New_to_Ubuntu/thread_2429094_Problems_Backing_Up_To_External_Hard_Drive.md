---
title: "Problems Backing Up To External Hard Drive"
date: 2019-10-13
forum: New to Ubuntu
---

### Post by wpwend42 on 2019-10-13
Running Ubuntu 18.04 on a new laptop...been having problems backing up to an external hard drive...have a Seagate 4TB and backup is extremely slow. I've never had a problem backing up with previous EHDs. What could be wrong? Searching online unfortunately gets little about backup and primarily information about putting Ubuntu on an external drive :(

---

### Post by Bashing-om on 2019-10-13
wpwend42; Hey hey

How about some info to work with ?

What are the source and destination file systems ?
```

sudo fdisk -lu

```

what means are you using to do that backup ?
GUI, terminal cp or rsync ?

[INDENT]garbage in == garbage out
[/INDENT]

---

### Post by wpwend42 on 2019-10-13
I'm using the GUI doing it manually dragging folders so they copy to the external drive.

---

### Post by SeijiSensei on 2019-10-13
Is the external drive formatted as ext4?  Using USB 3.0?

---

### Post by TheFu on 2019-10-13
Backups on Unix systems need to be more than just the files/data. The permissions, ACLs, owner, group are critical for a successful restore.  

The file system used matters.  Backing up Linux files to NTFS or exFAT or FAT-whatever will lose all that other metadata too.

Also, if you backup files that are owned by other userids using a GUI, it is highly likely that the permissions, ACLs, owner and group will be totally lost.  For files in a single user's HOME, it isn't a big deal. For files anywhere else, good luck. Best to use a real backup tool and run it using sudo with specific options that maintain not just the data, but also the other things.

If you'd consider using a real backup tool, we'd like to help.

---

### Post by oldrocker99 on 2019-10-13
Grsync is easy to use, and is in the repos.

---

### Post by Tadaen_Sylvermane on 2019-10-14
I'd suggest command line duplicity run as root so that it globally backs up all users. This is the script I've been using. Hasn't caused me issue yet.

```
if [[ "$USER" == root ]] ; then           
  for user in /home/* ; do
    BACKUPUSER=$(basename "$user")
    TARGETDIR="$POOLLOC"/backups/.googledrive/homebackups/"$BACKUPUSER"
    if ssh "$TARGETUSER"@"$SERVERFQDN" "[[ ! -d ${TARGETDIR} ]]" ; then
      ssh "$TARGETUSER"@"$SERVERFQDN" "mkdir -p ${TARGETDIR}"
    fi
    duplicity \
    --exclude-if-present .nobackup \
    --no-encryption \
    --full-if-older-than 1M \
    /data/"$BACKUPUSER" scp://"$TARGETUSER"@"$SERVERFQDN"/"$TARGETDIR"
    duplicity remove-all-but-n-full 4 --force \
    scp://"$TARGETUSER"@"$SERVERFQDN"/"$TARGETDIR"
  done
fi
```

I need to mod this to work with my ltsp setup to keep backing up to google drive.

---

### Post by TheFu on 2019-10-14
Duplicity has the bonus of storing the data and metadata as part of the backups. The target file system isn't too important, provided the chunked backup files aren't larger than it can support.  Duplicity, when working as designed, checks all the boxes for an excellent backup tool.

There are downsides for duplicity, however.  

Some others to consider:
* borg backup
* rsnapshot
* rdiff-backup  <---- I use this.
* restic
there must be 50 others.  Each as limitations and caveats, so don't just assume they will work for your needs, on your system, on your storage, blindly.

OTOH, having solid, working, automatic, versioned backups, that can be restored is a great thing. Let's me sleep very well at night.

---

### Post by wpwend42 on 2019-11-04
> **SeijiSensei said:**
> Is the external drive formatted as ext4?  Using USB 3.0?

The external HD is formatted as NTFS.

---

### Post by TheFu on 2019-11-04
> **wpwend42 said:**
> The external HD is formatted as NTFS.

That probably reduces the throughput about 20-30% and means that rsync isn't a suitable backup since owner, group, permissions and ACLs will be lost.  Manually copying files has this same issue.

If you can't or are unwilling to change to a native Linux file system, duplicity is really the only backup tool option, unless you go with file system images, like fsarchiver or ddrescue can make. Also, enabling big_writes on the mount options should help with performance. The ntfs mount manpage explains more.

IMHO.

---

### Post by wpwend42 on 2019-11-04
Also can someone explain why this doesn't work anymore? I have backed up files to external hard drives for years without problem. Only been an issue in the last few years on and off. Really frustrating and makes me nervous.

---

### Post by wpwend42 on 2019-11-04
What do you mean by "native Linux file system"?

---

### Post by TheFu on 2019-11-04
> **wpwend42 said:**
> What do you mean by "native Linux file system"?

How about any file system that supports **chown**, **chmod**, and **setfacl** --- as a starting place.  That excludes the Windows file systems, at least when accessed by Linux.

If you don't have a specific reason to use something else, on SSDs and HDDs, use ext4.
On thumb drives and other highly limited flash media, the choice is harder.

---

