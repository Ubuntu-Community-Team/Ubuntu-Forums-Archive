---
title: "rsync not logging/rsync advice"
date: 2012-09-27
forum: Programming Talk
---

### Post by Xplorer4x4 on 2012-09-27
I need rsync to sync my local svn folder, based on my dev site, to my debian dev server from my local kubuntu machine. I need it to do 3 things. 
1. Log the transferred files to a local log file.
2. Exclude the. svn folder for security reasons.
3. Transfer new and changed files.
Here is what I have and I believe it accomplishes 2 and 3 fine, but not #1. The log file is where it should be and named what it should be but for some reason I get a log file on the server in the "local" folder in the example below, and the local log just turns up empty but so does the one on the sever. Any tips to improve this and fix the log problem?

```
rsync -i /path/to/autosync.log -hvrx --no-owner --exclude .svn/ /path/to/local/svn/folder user@remote-server.com:/path/to/www
```

---

### Post by papibe on 2012-09-27
Hi Xplorer4x4.

The option for itemize the changes (-i) does not take arguments. You would have to redirect the rsync's output to a file in order to catch its results.

I would use the option --log-file instead:
```
rsync **--log-file=/path/to/autosync.log** -hvrx --no-owner --exclude .svn/ /path/to/local/svn/folder user@remote-server.com:/path/to/www
```
Hope it helps, and let us know how it goes.
Regards.

---

### Post by Xplorer4x4 on 2012-09-27
Awesome thanks, but does this truly sync only changed or new files? From the out put it looks like rsync is syncing all the files every time.

---

### Post by drdos2006 on 2012-09-27
It depends how to tell rsync what you want to do.
Here is an extract from "man rsync".
```

 -W, --whole-file            copy files whole (w/o delta-xfer algorithm)
        -x, --one-file-system       don't cross filesystem boundaries
        -B, --block-size=SIZE       force a fixed checksum block-size
        -e, --rsh=COMMAND           specify the remote shell to use
            --rsync-path=PROGRAM    specify the rsync to run on remote machine
            --existing              skip creating new files on receiver
            --ignore-existing       skip updating files that exist on receiver
            --remove-source-files   sender removes synchronized files (non-dir)
            --del                   an alias for --delete-during
            --delete                delete extraneous files from dest dirs
            --delete-before         receiver deletes before transfer (default)
            --delete-during         receiver deletes during xfer, not before
            --delete-delay          find deletions during, delete after
            --delete-after          receiver deletes after transfer, not before
            --delete-excluded       also delete excluded files from dest dirs
            --ignore-errors         delete even if there are I/O errors
            --force                 force deletion of dirs even if not empty
            --max-delete=NUM        don't delete more than NUM files
            --max-size=SIZE         don't transfer any file larger than SIZE
            --min-size=SIZE         don't transfer any file smaller than SIZE
            --partial               keep partially transferred files
            --partial-dir=DIR       put a partially transferred file into DIR
            --delay-updates         put all updated files into place at end
        -m, --prune-empty-dirs      prune empty directory chains from file-list
            --numeric-ids           don't map uid/gid values by user/group name
            --timeout=SECONDS       set I/O timeout in seconds
            --contimeout=SECONDS    set daemon connection timeout in seconds
        -I, --ignore-times          don't skip files that match size and time
            --size-only             skip files that match in size
            --modify-window=NUM     compare mod-times with reduced accuracy
        -T, --temp-dir=DIR          create temporary files in directory DIR
        -y, --fuzzy                 find similar file for basis if no dest file
            --compare-dest=DIR      also compare received files relative to DIR
            --copy-dest=DIR         ... and include copies of unchanged files
            --link-dest=DIR         hardlink to files in DIR when unchanged
        -z, --compress              compress file data during the transfer
            --compress-level=NUM    explicitly set compression level
            --skip-compress=LIST    skip compressing files with suffix in LIST

```
The log file tells me a file has been added.
>f+++++++++  new-file-name.txt
The log file tells me that the file has been synchronised.
>f.st          existing-file-altered.txt

regards
[edit]
> 
       --out-format=FORMAT
              This allows you to specify exactly what the rsync client outputs to the user on a per-update basis.  The format is
              a  text  string  containing  embedded single-character escape sequences prefixed with a percent (%) character.   A
              default format of "%n%L" is assumed if -v is specified (which reports the name of the file and, if the item  is  a
              link,  where  it  points).  For a full list of the possible escape characters, see the "log format" setting in the
              rsyncd.conf manpage.

              Specifying the --out-format option will mention each file, dir, etc. that gets updated in  a  significant  way  (a
              transferred file, a recreated symlink/device, or a touched directory).  In addition, if the itemize-changes escape
              (%i) is included in the string (e.g. if the --itemize-changes option was used), the logging of names increases  to
              mention  any  item  that is changed in any way (as long as the receiving side is at least 2.6.4).  See the --item&#8208;
              ize-changes option for a description of the output of "%i".

              Rsync will output the out-format string prior to a file&#8217;s transfer unless one of the transfer-statistic escapes is
              requested,  in  which  case  the  logging is done at the end of the file&#8217;s transfer.  When this late logging is in
              effect and --progress is also specified, rsync will also output the name of the file being  transferred  prior  to
              its progress information (followed, of course, by the out-format output).

       --log-file=FILE
              This  option  causes  rsync to log what it is doing to a file.  This is similar to the logging that a daemon does,
              but can be requested for the client side and/or the server side of a  non-daemon  transfer.   If  specified  as  a
              client  option,  transfer  logging  will be enabled with a default format of "%i %n%L".  See the --log-file-format
              option if you wish to override this.

              Here&#8217;s a example command that requests the remote side to log what is happening:

                rsync -av --rsync-path="rsync --log-file=/tmp/rlog" src/ dest/

              This is very useful if you need to debug why a connection is closing unexpectedly.

       --log-file-format=FORMAT
              This allows you to specify exactly what per-update logging is put into the file specified by the --log-file option
              (which  must also be specified for this option to have any effect).  If you specify an empty string, updated files
              will not be mentioned in the log file.  For a list of the possible escape characters, see the "log format" setting
              in the rsyncd.conf manpage.

              The default FORMAT used if --log-file is specified and this option is not is &#8217;%i %n%L&#8217;.

[/edit]

---

### Post by Xplorer4x4 on 2012-09-27
> **drdos2006 said:**
> It depends how to tell rsync what you want to do.
Here is an extract from "man rsync".

Thanks drdos2006, but thats the problem with man pages. People like to say to rtm(not saying you did, just stating), but what good does it do if we don't understand any or some of the options? If it is one or two, sure I dont mind trying to google but if there are 5 or more, it can get overly time consuming. 

> The log file tells me a file has been added.
>f+++++++++  new-file-name.txt
The log file tells me that the file has been synchronised.
f.st          existing-file-altered.txt

regards
Everytime I sync all files show thisj:
<f..T......
> So acording to the man page:
T means  that  the  modification  time will  be  set  to the transfer time, which happens when a ile/symlink/device is updated without --times and when a symlink  is  changed and the receiver can't set its time.
From the sound of it this means that the server modified time would be updated to the time the sync happened. If the sync happens at 5PM then the server should show the modified time as 5PM, but it doesn't so I think I misunderstood. this is an example of where man pages really fail (sometimes)imo. 

Then we have 
> -i, --itemize-changes       output a change-summary for all updates
I dont see the difference between using -i and not using -i. Is it possible to log ONLY when a new file is synced because it is new or because it was changed?

---

