---
title: "rsync copies all files, every time"
date: 2011-10-14
forum: New to Ubuntu
---

### Post by chris282 on 2011-10-14
Hi,

When I backup my home directory to an external hard drive using the following command I find that all my files are copied every time. 

```
rsync -rqa --delete /home/chris/* /media/250GB\ EXT/
```

I would expect only new and amended files to be copied.  Could anyone suggest why this might be?

I am using Ubuntu 10.04 Lucid.
The external hard drive is a Sumvision 3.5" e-sata II Apex Plus.

---

### Post by aeiah on 2011-10-14
well, your q flag is probably suppressing any messages that might tell you what's going on. also, r is redundant, because a implies r (and a bunch of others). also, you dont need the asterisk. try this command, and then take out the P (show progress) if you don't want it. you could also add a q after you know it works:

```

rsync -aP --delete /home/chris /media/250GB\ EXT/

```

leaving the slash off your 'chris' directory means it'll create the directory on your target rather than put everything directly in the root.

bear in mind that your home dir will have stuff like web browser caches etc that you might want to exclude. also, you may find that your command was working fine, and you only thought it was copying everything each time because it was copying a lot of temp files that change each time.

---

### Post by whitethorn on 2011-10-14
Have a look at the man pages. There's an option --update or -u.

```

man rsync

```

> 
 -u, --update                skip files that are newer on the receiver
            --inplace               update destination files in-place
            --append                append data onto shorter files
            --append-verify         --append w/old data in file checksum



---

### Post by aeiah on 2011-10-14
> **whitethorn said:**
> Have a look at the man pages. There's an option --update or -u.

```

man rsync

```

but OP is just doing a backup. there shouldnt be any files that are newer on the receiver :???: also, rsync by default doesn't copy stuff that's already there.

---

### Post by whitethorn on 2011-10-14
> **aeiah said:**
> but OP is just doing a backup. there shouldnt be any files that are newer on the receiver :???: also, rsync by default doesn't copy stuff that's already there.

> 
 -u, --update
              This forces rsync to skip any files which exist on the  destina&#8208;
              tion  and  have  a  modified  time that is newer than the source
              file.  (If an existing destination file has a modification  time
              equal  to the source file’s, it will be updated if the sizes are
              different.)

              Note that this does not affect the copying of symlinks or  other
              special  files.   Also,  a difference of file format between the
              sender and receiver is always considered to be important  enough
              for  an update, no matter what date is on the objects.  In other
              words, if the source has a directory where the destination has a
              file, the transfer would occur regardless of the timestamps.

              This  option  is  a transfer rule, not an exclude, so it doesn’t
              affect the data that goes  into  the  file-lists,  and  thus  it
              doesn’t  affect  deletions.   It  just limits the files that the
              receiver requests to be transferred.



It could be that it's not needed, I've always used it. Seems odd to have a specific option when it does it by default (maybe just for the update options). I'll have to test it out.

---

### Post by aeiah on 2011-10-14
i guess -u is useful if there's a chance that the target is being modified. in a backup this shouldn't be the case though. i havent ever used the update flag myself.

a normal rsync -a will overwrite files on the target if they're different (older or newer) from files on the source, whereas rsync -au will leave files on the target alone if they're newer. i suppose its a good option to use for copies that aren't strictly read-only backups.

---

### Post by collisionystm on 2011-10-14
> **aeiah said:**
> well, your q flag is probably suppressing any messages that might tell you what's going on. also, r is redundant, because a implies r (and a bunch of others). also, you dont need the asterisk. try this command, and then take out the P (show progress) if you don't want it. you could also add a q after you know it works:

```

rsync -aP --delete /home/chris /media/250GB\ EXT/

```

leaving the slash off your 'chris' directory means it'll create the directory on your target rather than put everything directly in the root.

bear in mind that your home dir will have stuff like web browser caches etc that you might want to exclude. also, you may find that your command was working fine, and you only thought it was copying everything each time because it was copying a lot of temp files that change each time.


-r, --recursive             recurse into directories

---

### Post by collisionystm on 2011-10-14
Here...


> charles@MAWS5240:~$ rsync --help
rsync  version 3.0.8  protocol version 30
Copyright (C) 1996-2011 by Andrew Tridgell, Wayne Davison, and others.
Web site: [http://rsync.samba.org/](http://rsync.samba.org/)
Capabilities:
    64-bit files, 64-bit inums, 64-bit timestamps, 64-bit long ints,
    socketpairs, hardlinks, symlinks, IPv6, batchfiles, inplace,
    append, ACLs, xattrs, iconv, symtimes

rsync comes with ABSOLUTELY NO WARRANTY.  This is free software, and you
are welcome to redistribute it under certain conditions.  See the GNU
General Public Licence for details.

rsync is a file transfer program capable of efficient remote update
via a fast differencing algorithm.

Usage: rsync [OPTION]... SRC [SRC]... DEST
  or   rsync [OPTION]... SRC [SRC]... [USER@]HOST:DEST
  or   rsync [OPTION]... SRC [SRC]... [USER@]HOST::DEST
  or   rsync [OPTION]... SRC [SRC]... rsync://[USER@]HOST[:PORT]/DEST
  or   rsync [OPTION]... [USER@]HOST:SRC [DEST]
  or   rsync [OPTION]... [USER@]HOST::SRC [DEST]
  or   rsync [OPTION]... rsync://[USER@]HOST[:PORT]/SRC [DEST]
The ':' usages connect via remote shell, while '::' & 'rsync://' usages connect
to an rsync daemon, and require SRC or DEST to start with a module name.

Options
 -v, --verbose               increase verbosity
 -q, --quiet                 suppress non-error messages
     --no-motd               suppress daemon-mode MOTD (see manpage caveat)
 -c, --checksum              skip based on checksum, not mod-time & size
 -a, --archive               archive mode; equals -rlptgoD (no -H,-A,-X)
     --no-OPTION             turn off an implied OPTION (e.g. --no-D)
 -r, --recursive             recurse into directories
 -R, --relative              use relative path names
     --no-implied-dirs       don't send implied dirs with --relative
 -b, --backup                make backups (see --suffix & --backup-dir)
     --backup-dir=DIR        make backups into hierarchy based in DIR
     --suffix=SUFFIX         set backup suffix (default ~ w/o --backup-dir)
 -u, --update                skip files that are newer on the receiver
     --inplace               update destination files in-place (SEE MAN PAGE)
     --append                append data onto shorter files
     --append-verify         like --append, but with old data in file checksum
 -d, --dirs                  transfer directories without recursing
 -l, --links                 copy symlinks as symlinks
 -L, --copy-links            transform symlink into referent file/dir
     --copy-unsafe-links     only "unsafe" symlinks are transformed
     --safe-links            ignore symlinks that point outside the source tree
 -k, --copy-dirlinks         transform symlink to a dir into referent dir
 -K, --keep-dirlinks         treat symlinked dir on receiver as dir
 -H, --hard-links            preserve hard links
 -p, --perms                 preserve permissions
 -E, --executability         preserve the file's executability
     --chmod=CHMOD           affect file and/or directory permissions
 -A, --acls                  preserve ACLs (implies --perms)
 -X, --xattrs                preserve extended attributes
 -o, --owner                 preserve owner (super-user only)
 -g, --group                 preserve group
     --devices               preserve device files (super-user only)
     --specials              preserve special files
 -D                          same as --devices --specials
 -t, --times                 preserve modification times
 -O, --omit-dir-times        omit directories from --times
     --super                 receiver attempts super-user activities
     --fake-super            store/recover privileged attrs using xattrs
 -S, --sparse                handle sparse files efficiently
 -n, --dry-run               perform a trial run with no changes made
 -W, --whole-file            copy files whole (without delta-xfer algorithm)
 -x, --one-file-system       don't cross filesystem boundaries
 -B, --block-size=SIZE       force a fixed checksum block-size
 -e, --rsh=COMMAND           specify the remote shell to use
     --rsync-path=PROGRAM    specify the rsync to run on the remote machine
     --existing              skip creating new files on receiver
     --ignore-existing       skip updating files that already exist on receiver
     --remove-source-files   sender removes synchronized files (non-dirs)
     --del                   an alias for --delete-during
     --delete                delete extraneous files from destination dirs
     --delete-before         receiver deletes before transfer, not during
     --delete-during         receiver deletes during transfer (default)
     --delete-delay          find deletions during, delete after
     --delete-after          receiver deletes after transfer, not during
     --delete-excluded       also delete excluded files from destination dirs
     --ignore-errors         delete even if there are I/O errors
     --force                 force deletion of directories even if not empty
     --max-delete=NUM        don't delete more than NUM files
     --max-size=SIZE         don't transfer any file larger than SIZE
     --min-size=SIZE         don't transfer any file smaller than SIZE
     --partial               keep partially transferred files
     --partial-dir=DIR       put a partially transferred file into DIR
     --delay-updates         put all updated files into place at transfer's end
 -m, --prune-empty-dirs      prune empty directory chains from the file-list
     --numeric-ids           don't map uid/gid values by user/group name
     --timeout=SECONDS       set I/O timeout in seconds
     --contimeout=SECONDS    set daemon connection timeout in seconds
 -I, --ignore-times          don't skip files that match in size and mod-time
     --size-only             skip files that match in size
     --modify-window=NUM     compare mod-times with reduced accuracy
 -T, --temp-dir=DIR          create temporary files in directory DIR
 -y, --fuzzy                 find similar file for basis if no dest file
     --compare-dest=DIR      also compare destination files relative to DIR
     --copy-dest=DIR         ... and include copies of unchanged files
     --link-dest=DIR         hardlink to files in DIR when unchanged
 -z, --compress              compress file data during the transfer
     --compress-level=NUM    explicitly set compression level
     --skip-compress=LIST    skip compressing files with a suffix in LIST
 -C, --cvs-exclude           auto-ignore files the same way CVS does
 -f, --filter=RULE           add a file-filtering RULE
 -F                          same as --filter='dir-merge /.rsync-filter'
                             repeated: --filter='- .rsync-filter'
     --exclude=PATTERN       exclude files matching PATTERN
     --exclude-from=FILE     read exclude patterns from FILE
     --include=PATTERN       don't exclude files matching PATTERN
     --include-from=FILE     read include patterns from FILE
     --files-from=FILE       read list of source-file names from FILE
 -0, --from0                 all *-from/filter files are delimited by 0s
 -s, --protect-args          no space-splitting; only wildcard special-chars
     --address=ADDRESS       bind address for outgoing socket to daemon
     --port=PORT             specify double-colon alternate port number
     --sockopts=OPTIONS      specify custom TCP options
     --blocking-io           use blocking I/O for the remote shell
     --stats                 give some file-transfer stats
 -8, --8-bit-output          leave high-bit chars unescaped in output
 -h, --human-readable        output numbers in a human-readable format
     --progress              show progress during transfer
 -P                          same as --partial --progress
 -i, --itemize-changes       output a change-summary for all updates
     --out-format=FORMAT     output updates using the specified FORMAT
     --log-file=FILE         log what we're doing to the specified FILE
     --log-file-format=FMT   log updates using the specified FMT
     --password-file=FILE    read daemon-access password from FILE
     --list-only             list the files instead of copying them
     --bwlimit=KBPS          limit I/O bandwidth; KBytes per second
     --write-batch=FILE      write a batched update to FILE
     --only-write-batch=FILE like --write-batch but w/o updating destination
     --read-batch=FILE       read a batched update from FILE
     --protocol=NUM          force an older protocol version to be used
     --iconv=CONVERT_SPEC    request charset conversion of filenames
 -4, --ipv4                  prefer IPv4
 -6, --ipv6                  prefer IPv6
     --version               print version number
(-h) --help                  show this help (-h works with no other options)

Use "rsync --daemon --help" to see the daemon-mode command-line options.
Please see the rsync(1) and rsyncd.conf(5) man pages for full documentation.
See [http://rsync.samba.org/](http://rsync.samba.org/) for updates, bug reports, and answers
charles@MAWS5240:~$ rsync --help | grep -r
Usage: grep [OPTION]... PATTERN [FILE]...
Try `grep --help' for more information.

---

### Post by aeiah on 2011-10-14
> **collisionystm said:**
> -r, --recursive             recurse into directories

-a implies -r

---

### Post by collisionystm on 2011-10-14
> **aeiah said:**
> -a implies -r

-a, --archive archive mode; equals -rlptgoD (no -H,-A,-X)

Yup I see an "r" in there.

---

### Post by chris282 on 2011-10-14
> **aeiah said:**
> well, your q flag is probably suppressing any messages that might tell you what's going on. also, r is redundant, because a implies r (and a bunch of others). also, you dont need the asterisk. try this command, and then take out the P (show progress) if you don't want it. you could also add a q after you know it works:

```

rsync -aP --delete /home/chris /media/250GB\ EXT/

```leaving the slash off your 'chris' directory means it'll create the directory on your target rather than put everything directly in the root.

bear in mind that your home dir will have stuff like web browser caches etc that you might want to exclude. also, you may find that your command was working fine, and you only thought it was copying everything each time because it was copying a lot of temp files that change each time.

aeiah, I have run the suggested command twice, back to back.  The first time, as expected, the 'chris' directory was created and all files were saved to this.  The second time, as previously, all files were saved again.  This was particularly noticeable with larger files such as music and videos, so it doesn't appear to be just a lot of temp files being copied.

---

### Post by chris282 on 2011-10-14
Any ideas on this, anyone?

---

### Post by papibe on 2011-10-14
Is "/media/250GB\ EXT/" an NTFS external drive?

If so, I think may be experiencing the [known problem]("ftp://ppp.samba.org/pub/unpacked/rsyncweb/daylight-savings.html") of DST and UTC time conversion of NTFS and FAT file systems.

rsync has an option to deal with that problem:
```
--modify-window=1
```
Start as the example (value 1) and check if that solve the problem. If not maybe a value of 2 may work better.

Hope it helps,
Regards.

---

### Post by vajorie on 2011-10-15
> **papibe said:**
> Is "/media/250GB\ EXT/" an NTFS external drive?


or a fat32 filesystem...

---

### Post by chris282 on 2011-10-15
Many thanks papibe.  This does seem to be the problem, and using the command

```
rsync -aP --delete --modify-window=3601 /home/chris /media/250GB\ EXT/
```to ignore time differences of up to an hour appears to work for my purposes.

To clarify, the external hard drive I'm using is a [Seagate Barracuda 7200.10]("http://www.seagate.com/ww/v/index.jsp?vgnextoid=a62099f4fa74c010VgnVCM100000dd04090aRCRD&locale=en-US") (*not* as previously stated, a Sumvision Apex Plus, which I have embarrassingly discovered to be the casing #-o).  How would I find out whether this uses FAT32, NTFS (or whatever)?  Is this something I can change?

---

### Post by vajorie on 2011-10-15
You can find it in the "Disk Utility" app (click on the drive, the filesystem is listed under Volumes > Types once you click on the relevant drive). 

You can also check using

```
sudo fdisk -l
```

which gives you the partition type. The external drive will probably be listed as /dev/sdbX (where X is a number).

You can change it using the Disk Utility or by installing (via apt-get) and using gparted to an ext3 filesystem (which is what I use for my backups), but keep in mind that Windows and Mac computers will then be *unable to read* the disk.

---

### Post by chris282 on 2011-10-16
That's fantastic, many thanks Vajorie.  For the record, the drive was type FAT32.

---

### Post by The Cog on 2011-10-16
Good to see that's all sorted then. I wonder if the hour's difference is something to do with daylight savings? I haven't heard of that being a problem before.

A note on whether you need -update: I could be wrong, but I suspect that the normal behaviour is to rewrite the file if the target differs from the source in either timestamp or in size. --update changes this so that the file will not be re-written if the source file is older than the target file. For backups, this might not be what you want - it means that if you restore an older copy from somewhere else for some reason, the backup won't be updated to reflect that.

-update is useful if you're doing a 2-way sync though. For instance, I maintain a folder on a server that I periodically sync with all my other PCs. When I edit a file on one PC, the next sync updates from that PC to the server, and then later other PCs update from the server to themselves. In this case, I explicitly don't want the older file to overwrite the newer one - I do an rsync from PC to server, then from server to PC, both with the -update flag.

---

