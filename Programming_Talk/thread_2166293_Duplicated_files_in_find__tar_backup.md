---
title: "Duplicated files in find | tar backup"
date: 2013-08-08
forum: Programming Talk
---

### Post by kevin1 on 2013-08-08
I wish to back up a file structure which has spaces in paths and filenames, retaining the structure.

I am testing with this structure:

[INDENT]home/kevin/Test/Source Directory/
home/kevin/Test/Source Directory/Directory One/
home/kevin/Test/Source Directory/Directory One/Document Two.odt
home/kevin/Test/Source Directory/Directory One/Document One.odt[/INDENT]

This is my script, which resulted from much googling:

```
#!/bin/bash
find '/home/kevin/Test/Source Directory' -print0 | xargs -0 tar -czpf /home/kevin/Test/Backups.tgz --null
read -p "Press ENTER to quit"
```

Tar outputs these messages:

[INDENT]tar: Removing leading `/' from member names
tar: Removing leading `/' from hard link targets[/INDENT]

When I explore Backups.tgz using Archive Manager the directory structure is correct, but with each file there are a further two copies with the same name, but size zero bytes.

When I run my restore script:

```
#!/bin/bash/
tar zxvf /home/kevin/Test/Backups.tgz -C /home/kevin/Test/Restored
```

Tar displays:

[INDENT]home/kevin/Test/Source Directory/
home/kevin/Test/Source Directory/Directory One/
home/kevin/Test/Source Directory/Directory One/Document Two.odt
home/kevin/Test/Source Directory/Directory One/Document One.odt
home/kevin/Test/Source Directory/Directory One/
home/kevin/Test/Source Directory/Directory One/Document Two.odt
home/kevin/Test/Source Directory/Directory One/Document One.odt
home/kevin/Test/Source Directory/Directory One/Document Two.odt
home/kevin/Test/Source Directory/Directory One/Document One.odt[/INDENT]

... which shows the repeated files, but the restored directory structure is correct, having only one of each file.

Although the end result is as it should be I would rather the internal structure of the backup file was correct.

I am sure there must be an error in my backup script.

Thanks for any advice.

Kevin

---

### Post by r-senior on 2013-08-08
What happens if you use "-type f" as an option to find?

---

### Post by TheFu on 2013-08-08
There are lots of ways to backup. Tar is old-school ... which is fine, if it meets your needs.

Doesn't this work?```
$ tar cvzf  /home/kevin/Test/Backups.tgz  "/home/kevin/Test/Source Directory"
```

Tar removes the leading / - it is a safety thing.  If you run this from your ~/Test/ directory, then using 
```
$ tar cvzf  Backups.tgz  "Source Directory"
```
should work with relative paths.

Is there a reason you don't want to use DejaDup or Back-In-Time or rdiff-backup or rsnapshot or rbackup instead?  These all will create more efficient backups for storage thanks to librsync and hardlinks. Further, running daily will create daily snapshots with just the changed data, while letting you restore from a backup from today, yesterday, last week or last month ... whatever your retention needs might be.  Just offering alternatives - tar is fine.

---

### Post by kevin1 on 2013-08-09
**r-senior:**

'-type f' fixed the problem - I'm curious as to why it is necessary. My script is now:
```
find '/home/kevin/Test/Source Directory' -type f -print0 | xargs -0 tar -czpf /home/kevin/Test/Backups.tgz --null
```

The only message from tar is now 
[INDENT]tar: Removing leading `/' from member names.[/INDENT]

Backups.tgz now appears as it should in Archive Manager and the paths displayed by tar when restoring are as expected.

**TheFu:**
```
tar cvzf  /home/kevin/Test/Backups.tgz  "/home/kevin/Test/Source Directory"
```

also works perfectly! Everything I have read says that tar cannot cope with spaces in paths, so I am thoroughly confused.

I may investigate some of the more sophisticated backup alternatives, but just wanted to get a basic backup system set up.


Many thanks to both of you for your help.

Kevin

---

### Post by TheFu on 2013-08-09
> **kevin1 said:**
> I may investigate some of the more sophisticated backup alternatives, but just wanted to get a basic backup system set up.

If you want bone-head simple, end-user backups, use **Back-in-Time** [http://backintime.le-web.org/](http://backintime.le-web.org/) .  It is in the repos, has a GUI (both Gnome and KDE) and it works.  The target HDD will need to be Linux formatted, since hardlinks are used.  Most importantly, it is 100% automatic and keeps more backup sets closer to "now". Over time, fewer and fewer backups are retained - 1 per prior years, 1 per month in the current year, ... you get the idea.

[http://blog.jdpfu.com/2011/11/12/best-practices-for-home-desktop-computer-backups](http://blog.jdpfu.com/2011/11/12/best-practices-for-home-desktop-computer-backups) lists the attributes for backup best practices:

[LIST=1]
[*]    Stable / Works Every Time
[*]    Automatic
[*]    Different Storage Media
[*]    Fast
[*]    Efficient
[*]    Secure
[*]    Versioned
[*]    Offsite / Remote
[*]    Restore Tested
[/LIST]
Getting all of those usually removes some usability traits.  I give up encrypted remote storage for usability, but besides that, **rdiff-backup** handles everything else nicely for system-level backups and is more efficient than other methods I've tried.  10-20% more storage than a mirror needs for 30-60 days of backups. THAT is impressive.

---

### Post by kevin1 on 2013-08-10
Thanks for the advice TheFu.

---

### Post by r-senior on 2013-08-11
> **kevin1 said:**
> '-type f' fixed the problem - I'm curious as to why it is necessary.
I'm not totally clear on this but I think it is because find is picking up hard links, presumably from '.' and '..', as you traverse the directory structure. That theory is consistent with the messages you were getting. Restricting the find to regular files fixes the issue.

> Everything I have read says that tar cannot cope with spaces in paths, so I am thoroughly confused.
The GNU utilities often have improvements and additional options over their traditional Unix counterparts. Although they aim to implement existing standards, e.g. POSIX, they are rewrites inspired by, rather than derivatives of. There is no definitive *tar* program, just different implementations of a tape archiver called *tar*.

---

### Post by steeldriver on 2013-08-11
Isn't it just because tar is the original serial (tape) archiver - it never 'winds the tape back' to see if a file is already in the archive

```

$ tar cvf tests.tar tests/one tests/one tests/one
tests/one
tests/one
tests/one
$ 
$ tar tf tests.tar 
tests/one
tests/one
tests/one

```

so if you tell it to archive a directory (implicitly including its contents) and then explicitly tell it to archive each of the files in the directory it does exactly that

```

$ tar cvf tests.tar tests tests/one tests/two tests/three
tests/
tests/two
tests/three
tests/one
tests/one
tests/two
tests/three
$ 
$ tar tf tests.tar
tests/
tests/two
tests/three
tests/one
tests/one
tests/two
tests/three

```

By adding the -type f to find, you are no longer passing + implicitly descending the parent directories as well as the individual files

Or am I missing something?

---

### Post by r-senior on 2013-08-11
I like the theory but how would it explain that the "copies" were zero size?

---

### Post by steeldriver on 2013-08-11
Sorry, you're right - I totally missed that part of the discussion in fact in my simple test above, tar t**v**f indicates the duplicates are added as hardlinks

```

$ tar tvf tests.tar
drwxr-xr-x steeldriver/steeldriver   0 2013-08-11 17:27 tests/
-rw-rw-r-- steeldriver/steeldriver 245 2013-08-11 17:27 tests/two
-rw-rw-r-- steeldriver/steeldriver  26 2013-08-11 17:27 tests/three
-rw-rw-r-- steeldriver/steeldriver 256 2013-08-11 17:27 tests/one
hrw-rw-r-- steeldriver/steeldriver   0 2013-08-11 17:27 tests/one link to tests/one
hrw-rw-r-- steeldriver/steeldriver   0 2013-08-11 17:27 tests/two link to tests/two
hrw-rw-r-- steeldriver/steeldriver   0 2013-08-11 17:27 tests/three link to tests/three

```

---

