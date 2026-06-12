---
title: "Check if all data it was well copy"
date: 2021-06-28
forum: New to Ubuntu
---

### Post by sed_faster on 2021-06-28
Hi guys,

Exist another secure way to copy data between discs on server ubuntu beyond the command "cp -arvp /home/user/disk1/ /home/user/disk2/"?

Because after copy all data I checked if all data it was copy through command "du -sh folder/" and button right and properties (see report on the file manager, in this case the nautilus) and sometimes the result don't match between source and destiny (both the number of files and the disk space).

Thanks

---

### Post by TheFu on 2021-06-28
rsync is one.  In the list of great human inventions, rsync is up there with "Unix", ssh, vaccines, and the printing press. It is THAT good.

but most file systems don't actually validate that the data sent to be written actually got onto the disk correctly.  I know only 1 file system which does verify - ZFS. It wants ECC RAM to do this validation.

---

### Post by sed_faster on 2021-06-28
> **TheFu said:**
> rsync is one.  In the list of great human inventions, rsync is up there with "Unix", ssh, vaccines, and the printing press. It is THAT good.

but most file systems don't actually validate that the data sent to be written actually got onto the disk correctly.  I know only 1 file system which does verify - ZFS. It wants ECC RAM to do this validation.

But with rsync occur the same scenario. There is always a difference between file number.

---

### Post by sudodus on 2021-06-28
I would run the copy command with **elevated permissions** in order to copy also from and to files/directories where the current user may not have permissions and to preserve the permissions. And I prefer rsync, but cp should work too, when copying locally.

For example, you can try

```

sudo rsync -Havn source/ target

```

which is a 'dry run' and when things look OK remove the [FONT=Courier New]**n**[/FONT] and do the real work.

You will find a lot of options in [FONT=Courier New]**man rsync**[/FONT]

If necessary you can make sure that the source and target are identical with the rsync option [FONT=Courier New]**-c**[/FONT], but it will make things much slower.

```

        -c, --checksum
              This changes the way rsync checks if the files have been changed
              and  are in need of a transfer.  Without this option, rsync uses
              a "quick check" that (by default) checks if each file’s size and
              time of last modification match between the sender and receiver.
              This option changes this to compare a 128-bit checksum for  each
              file  that  has a matching size.  Generating the checksums means
              that both sides will expend a lot of disk I/O  reading  all  the
              data  in  the  files  in  the transfer (and this is prior to any
              reading that will be done to transfer changed  files),  so  this
              can slow things down significantly.

              The  sending  side generates its checksums while it is doing the
              file-system scan that builds the list of  the  available  files.
              The  receiver  generates  its  checksums when it is scanning for
              changed files, and will checksum any file that has the same size
              as the corresponding sender’s file:  files with either a changed
              size or a changed checksum are selected for transfer.

              Note that rsync always verifies that each transferred  file  was
              correctly  reconstructed  on  the  receiving  side by checking a
              whole-file checksum that is generated  as  the  file  is  trans&#8208;
              ferred,  but  that automatic after-the-transfer verification has
              nothing to do with this option’s before-the-transfer "Does  this
              file need to be updated?" check.

              For  protocol  30  and  beyond  (first  supported in 3.0.0), the
              checksum used is MD5.  For older protocols, the checksum used is
              MD4.

       -a, --archive
              This  is equivalent to -rlptgoD. It is a quick way of saying you
              want recursion and want to preserve almost everything  (with  -H
              being  a  notable  omission).   The  only exception to the above
              equivalence is when --files-from is specified, in which case  -r
              is not implied.

              Note that -a does not preserve hardlinks, because finding multi&#8208;
              ply-linked files is expensive.  You must separately specify -H.

```

---

### Post by TheFu on 2021-06-28
> **sed_faster said:**
> But with rsync occur the same scenario. There is always a difference between file number.

4 possible things.
* different block sizes on the disks
* permissions don't allow the userid running the command to copy all the data
* symbolic links
* using sparse files

If one disk has 512b blocks and the other has 4Kb blocks, then the sizes will be different between the source and target.  The smallest file will use 4Kb, not 512b - that's 3x larger.

Permissions issues - too large a topic to cover, but if there is any confusion about permissions, that could be the problem.

Sparse files can be used by some programs to create relatively small files on disk, that can grow to huge sizes.  Many commands have a sparse file option to ensure proper handling during copies.  
The **cp** manpage:
```
       By  default, sparse SOURCE files are detected by a crude heuristic and the corresponding DEST
       file is made sparse as well.  That  is  the  behavior  selected  by  --sparse=auto.   Specify
       --sparse=always  to create a sparse DEST file whenever the SOURCE file contains a long enough
       sequence of zero bytes.  Use --sparse=never to inhibit creation of sparse files.
```

The **rsync** manpage:
```
       -S, --sparse
              Try  to handle sparse files efficiently so they take up less space on the destination.
              If combined with --inplace the file created might not end up with sparse  blocks  with
              some combinations of kernel version and/or filesystem type.  If --whole-file is in ef&#8208;
              fect (e.g. for a local copy) then it will always work because rsync truncates the file
              prior to writing out the updated version.

              Note  that  versions of rsync older than 3.1.3 will reject the combination of --sparse
              and --inplace.
```
There are other references to sparse file handling in both manpages.

The way that symbolic links are handled will matter too.  They can be retained as links or they can be "followed", which could pull much more data into the backup - possibly creating a circular link.

---

### Post by sed_faster on 2021-06-28
**UPDATE:**
I will try this command "sudo rsync -HaS --progress source target". Which command I can try to check the difference between folders? So I test the veracity of the two commands.

Maybe the problems be on the different block sizes between on the disks

---

### Post by sudodus on 2021-06-28
You can check with

```

sudo -Havcn source/ target

```

c forces checksum test of each file, n dry run (that is only check, no copying). The list of files will show which files are not matching (and should be copied).

But it does not show files on the target side, which are not matched on the source side. You can check that with a second test,

```

sudo -Havcn target/ source

```

but if synchronizing is what you want, there are better tools, for example [FONT=Courier New]**unison**[/FONT] (and [FONT=Courier New]**unison-gtk**[/FONT]).

---

### Post by TheFu on 2021-06-28
-H follows symlinks.  That might not be desirable.
Be 100% certain you understand every option.

To see what got out of data, I'd re-run the rsync over, just with --dry-run. That will show what it thinks is out of date. Be 100% certain the systems have the correct date/time. That's important to rsync and for security in general.  Also, if the target keeps growing in size, understand that rsync doesn't delete any files not in the source, but still in the target directories.  There are multiple delete option, if the goal is to have a data mirror.

Without a delete option, new files will be added, but files not in the source, will never be deleted in the target.  cp has the same consideration.

---

### Post by sudodus on 2021-06-28
I thought -H [in rsync] is only checking for hard-links (not symbolic links).

```

       -H, --hard-links
              This  tells rsync to look for hard-linked files in the source and link together
              the corresponding files on the destination.  Without this option, hard-linked
              files in the source are treated  as  though  they were separate files.

              ...

```

---

### Post by TheFu on 2021-06-28
-H ... my mistake.  -H (or is that -h) in cp means follow symlinks. From the cp manpage:
```
       -H     follow command-line symbolic links in SOURCE
```

I'm so confused!  I need to fully understand all the options for the command, right? ;)

---

### Post by sed_faster on 2021-06-28
I only need check if all content was copied correctly. I have two disks on a Ubuntu server and I want copy all data from disk 1 to disk 2. I am trying this command:

```

sudo rsync -Havcn /home/user/disk1/folder/* /home/user/disk2/folder_backup/ >> log.txt

```

**UPDATE1:**
What output can I expect if there are files that have not been copied between source and destination? Should I run this command (inverse)?:
```

sudo rsync -Havcn /home/user/disk2/folder_backup/ /home/user/disk1/folder/* >> log.txt

```

Thanks

---

### Post by sudodus on 2021-06-28
```

sudo rsync -Havcn /home/user/disk1/folder/ /home/user/disk2/folder_backup/ >> log.txt

```

**The files listed in [FONT=Courier New][SIZE=3]log.txt[/SIZE][/FONT] do not match (either are not copied or are different).**

Please notice the special meaning of a trailing slash in the specification of the source in rsync

```

[B]              rsync -avz foo:src/bar/ /data/tmp

       A  trailing slash on the source changes this behavior to avoid creating
       an additional directory level at the destination.[/B]  You can think  of  a
       trailing / on a source as meaning "copy the contents of this directory"
       as opposed to "copy the directory by  name",  but  in  both  cases  the
       attributes  of the containing directory are transferred to the contain&#8208;
       ing directory on the destination.  In other words, each of the  follow&#8208;
       ing  commands copies the files in the same way, including their setting
       of the attributes of /dest/foo:

              rsync -av /src/foo /dest
              rsync -av /src/foo/ /dest/foo

```

Edit: If you are not synchronizing, only copying, you need *[COLOR="#0000CD"]not[/COLOR]* worry about extra files in the target (files not matching corresponding files in the source).

---

### Post by scorp123 on 2021-06-28
Oops. Don't mind me. I am not here.

---

### Post by sed_faster on 2021-06-28
Exist difference between folders. I guess the difference it is caused by the different users and groups I have created. Because the data (that I'm copying) came from an external NAS.
But right now I have two disks on my server and I want copy all data from disk2 to disk1. Which best program and method I should use?

Maybe If I change all users and groups relating to my files, standardizing everything, I will copy all data without problems. What do you think?

Thanks

---

### Post by sudodus on 2021-06-28
I think [FONT=Courier New]**rsync**[/FONT] is the best program. If you run it with elevated permissions (with [FONT=Courier New]**sudo**[/FONT]), it should work without modifying the permissions. I think it is risky to start modifying the users and groups, not so much for plain data files (pictures, documents etc), but definitely for configuration files.

So you should be able to run it according to my earlier tips, only remember to remove the option [FONT=Courier New]**n**[/FONT] ('dry run').

---

### Post by TheFu on 2021-06-28
> **sed_faster said:**
> Exist difference between folders. I guess the difference it is caused by the different users and groups I have created. Because the data (that I'm copying) came from an external NAS.
But right now I have two disks on my server and I want copy all data from disk2 to disk1. Which best program and method I should use?

Maybe If I change all users and groups relating to my files, standardizing everything, I will copy all data without problems. What do you think?

Thanks

It depends.  Do you need those users and groups or not?  If you do not, then change all the file and directories on the source to be owned by your normal userid. This assumes they are just data, not OS files or data or configs.

OTOH, if the users and groups are still necessary, then the solution, as stated by sudodus a few times, is to elevate the permissions using sudo for the rsync command.  That will retain the existing owner and groups based on the values in the source.

---

### Post by sed_faster on 2021-06-28
I will try this command "sudo rsync -HSav --progress f1/ f2/" without parameter -n because I want copy all data, this is firstly synchronize.

---

### Post by sed_faster on 2021-06-28
> **TheFu said:**
> It depends.  Do you need those users and groups or not?  If you do not, then change all the file and directories on the source to be owned by your normal userid. This assumes they are just data, not OS files or data or configs.

OTOH, if the users and groups are still necessary, then the solution, as stated by sudodus a few times, is to elevate the permissions using sudo for the rsync command.  That will retain the existing owner and groups based on the values in the source.

Yes, it is only data, not OS files. I don't need all this users or groups. The system its is the same (I need study more about the Linux because I need learn how management data on this environment.

Do you suggest change first users/groups and only after run rsync?

---

### Post by TheFu on 2021-06-28
If only 1 userid is needed, then do this first:
```
sudo chown -R $USER:$USER /home/user/disk1/folder
```

Then you won't need sudo for the rsync, since that command above will change the owner to the current userid first.

If you are serious about learning Linux, then work through this book, [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) 1 chapter a week. Do all the exercises - even the "optional" ones.

If you want to kick-start, there's a free training website: [https://linuxjourney.com/](https://linuxjourney.com/)  Then go to that book and do the first 25-ish pages.  And if you want to keep going, [https://gitlab.com/sofreeus/Linux-Camp](https://gitlab.com/sofreeus/Linux-Camp) is beginning admin resource.

---

### Post by ActionParsnip on 2021-06-28
Could use a bash loop to shasum each file from source and destination to verify

---

### Post by TheFu on 2021-06-28
> **ActionParsnip said:**
> Could use a bash loop to shasum each file from source and destination to verify

Or use 1% par2 parity files.  Then xfer over the *par2 files and run a verify task.
$ more ~/bin/par2-create
```
#!/bin/sh

for filename in "$@"; do

   # Create a 10% recovery data with blocksize of 300KB
   nice par2 create -s307200 -r10 "$filename"

done
```
This script is dependent on filenames NOT having any spaces.  The space is a natural delimiter, so running the command as **par2-create *** will create a set of par2 parity files for every file in the CWD.

---

### Post by sed_faster on 2021-09-20
Hello, I am back,
I am so sorry for my absence but I only got it now it is possible appear here (In the last few months I couldn't even read the linux book or anything :/ ).

At the moment I have three hard drives from different computers on the same computer (ubuntu server). Which result in different users and permissions (which result a complication to copy and organize all data). What is the best strategy to put all files under the same user?

I have the root user (normal) plus the system user plus and an user in samba. When a folder is created/changed under/through the windows computer, that files remains with the samba user. Is this good practice?

My goal it is organize all data and after that following a tutorial to learn and create a ubuntu server with option samba (because on my network I have a computer windows)

Thanks

---

### Post by ActionParsnip on 2021-09-21
Could use md5sum on the files as a quick and dirty way to check the files have copied OK

---

