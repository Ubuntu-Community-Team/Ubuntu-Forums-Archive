---
title: "[SOLVED] Who wants to fork gedit to fix 2 yr network share saving bug?"
date: 2008-03-28
forum: Programming Talk
---

### Post by MountainX on 2008-03-28
The following bug has been much discussed for at least two years [https://bugs.launchpad.net/gedit/+bug/34813](https://bugs.launchpad.net/gedit/+bug/34813)

Gedit fails when editing files over a cifs/sshfs (and now smbfs in Hardy) share. This applies to gedit and any other editor that relies on moving the file that is being edited while the filehandle is kept open. 

Here is a good diagnosis of the issue:
[https://bugs.launchpad.net/gedit/+bug/34813/comments/20](https://bugs.launchpad.net/gedit/+bug/34813/comments/20)
[https://bugs.launchpad.net/gedit/+bug/34813/comments/40](https://bugs.launchpad.net/gedit/+bug/34813/comments/40)
Here is the relevant part copied from comment 20:
The problem with gedit is the "save" routine. It relies on moving the file that is being edited while the filehandle is kept open. This works for most filesystems, but it fails on cifs and sshfs. 

The easiest way to fix this in gedit is to stop trying to move open files. Simply copy the file to create the backup.

The current gedit devs don't like the idea of changing their way of saving files because this other solution would require a full copy of the text file (for backup).

Doesn't this sound like the developers are too caught up in the idea of machine efficiency? Yes, it takes more time to copy the file for backup. But many editors already do this and the amount of time it takes is so small most users will never notice it. (And for very old slow machines or very large files, we have several easy solutions that are compatible with this fix.)

Do you agree that this misguided desire to be "efficient" means that gedit fails to satisfy a real need for a lot of users -- the ability to work with files over common network shares.

I copied Peter Wuertz's proposed solution here:
[https://bugs.launchpad.net/gedit/+bug/34813/comments/61](https://bugs.launchpad.net/gedit/+bug/34813/comments/61)

Since the gedit devs haven't been willing to put the needs of real users ahead of their seemingly misguided idea about the need to avoid copying a backup file for "efficiency" reasons, why don't we fork gedit?

The other option is to take an existing editor (such as SciTE maybe) and tweak it a bit to blend in to Ubuntu better.

Since I think gedit is a nice editor, I am proposing that we fix this important bug.

---

### Post by lilian on 2008-03-28
I agree that this problem is very annoying and it is a big problem for me because I am trying to use Ubuntu at work and need to deal with network shares...

But I think the problem is not only regarding gedit. I don't know what is the root cause, but it affects at least gedit and eclipse.

For example, if I create an Eclipse workspace on a samba share over cifs, it is quite impossible to work, eclipse is always saying "the file was modified outside..." or "out of sync" etc.

I cannot be sure, but I think the problem is the same and comes from samba.

A better idea than forking gedit may be identifying the root cause and solve it :cool:

Best regards
Lilian

---

### Post by frego on 2008-03-28
Your proposal is interesting.  But how do you handle a race condition?  What if two people are editing the same file at roughly the same time?  Who gets the lock if you are copying to a temp file?

---

### Post by mssever on 2008-03-28
Anytime you fork a project, you pay a very large penalty. Is it really worth it just to fix one bug?

---

### Post by MountainX on 2008-03-28
> **lilian said:**
> 
A better idea than forking gedit may be identifying the root cause and solve it :cool:

Peter did a good job of identifying the root cause. See his posts in the comments at the original bug.

The solution he proposed (copy the file to create a backup) does solve the root cause in a good way while avoiding the need to mess with cifs, smbfs, etc. As Peter points out, it is not desirable to move (rename) an open file. Just copy it.

---

### Post by MountainX on 2008-03-28
> **frego said:**
> Your proposal is interesting.  But how do you handle a race condition?  What if two people are editing the same file at roughly the same time?  Who gets the lock if you are copying to a temp file?

The modern method used in disconnected database updates should be fine I would think. 

I don't think there is really a race condition if a backup copy is made. Consider this scenario:
User 1 opens file for editing. A backup copy is made while original file is locked for editing. User 2 (or user N) cannot edit the original file until user 1 closes it. If we wanted to be careful, maybe we could either hold a lock on the backup file too or, maybe, just make the backup file hidden.

Am I over looking something?

---

### Post by MountainX on 2008-03-28
> **mssever said:**
> Anytime you fork a project, you pay a very large penalty. Is it really worth it just to fix one bug?

How else can we fix this bug? I'm open to any ideas.

If we fork gedit, maybe we could call it fedit. F is the next progression in the alphabet and it could stand for "fixed/forked gedit"

---

### Post by asmoore82 on 2008-03-28
I justed tested this with Gedit over sshfs on 7.10 Gutsy.

on a Graphically "mounted" sshfs via Nautilus "Places -> Connect to Server,"
I encountered no problems whatsoever.

on a terminal mounted sshfs via the `sshfs` command,
I saw the issue and resolved it by simply telling Gedit not to create backup files:
In Gedit, open "Edit -> Preferences,"
click the "Editor" tab and uncheck "Create a backup copy of files before saving"

I am pleased that I saw this thread today, because I *really don't* want "*~" files all over the place!
So, where's the Fire?

---

### Post by MountainX on 2008-03-28
So maybe there is a simple solution...

I just tested this with Hardy on a share mounted with cifs.

Open Nautilus to the network share and from the Nautilus file menu select "create document" > empty.

Open the new document in gedit. (Make sure backup files is disabled.)
Type some text and try to save the document.

I get the error "Could not save the file /media/sharename/deleteme1.txt"

I cannot find a way to resolve it. I do not get the error with other editors I have tried.

---

### Post by asmoore82 on 2008-03-28
*Update*

**_EVEN_** with Gedit's default backup file behavior enabled,
I encounter no problems whatsoever when using sshfs like this:
```
 sshfs **-o uid=$UID** *username*@*hostname*:*directory* *mountpoint*
```

---

### Post by mssever on 2008-03-28
> **MountainX said:**
> Here is the relevant part copied from comment 20:
The problem with gedit is the "save" routine. It relies on moving the file that is being edited while the filehandle is kept open. This works for most filesystems, but it fails on cifs and sshfs.
It seems to me that the proper solution is to fix the filesystem. Having special case behavior for different filesystems, or reducing the program to use the lowest common denominator, is only a band-aid that doesn't solve the problem (and can easily make matters worse in the long run). Filesystems should present a common interface. If what you quoted is correct, that's the real problem. (I haven't read the links you gave.)

The problem with forks boils down to this: you either split developer mindshare (which hurts everybody); or your fork suffers from a lack of mindshare. If you don't have adequate mindshare, you fall behind.

What about the following compromise: Make your own custom deb with a patch for the bug (as is common in debs). Every time a new release of Gedit comes down the pike, evaluate it and update your deb accordingly. Of course, you should send your patch upstream, but if it's the wrong solution (as it appears), don't expect it to be accepted.

---

### Post by MountainX on 2008-03-28
> **asmoore82 said:**
> *Update*

**_EVEN_** with Gedit's default backup file behavior enabled,
I encounter no problems whatsoever when using sshfs like this:
```
 sshfs **-o uid=$UID** *username*@*hostname*:*directory* *mountpoint*
```

I have never tested it with sshfs because I've been told that sshfs isn't suitable for large files (videos, backups, virtual machine images, etc.). 

I

---

### Post by MountainX on 2008-03-28
> **mssever said:**
> It seems to me that the proper solution is to fix the filesystem. Having special case behavior for different filesystems, or reducing the program to use the lowest common denominator, is only a band-aid that doesn't solve the problem (and can easily make matters worse in the long run). Filesystems should present a common interface. If what you quoted is correct, that's the real problem. (I haven't read the links you gave.)

The problem with forks boils down to this: you either split developer mindshare (which hurts everybody); or your fork suffers from a lack of mindshare. If you don't have adequate mindshare, you fall behind.

What about the following compromise: Make your own custom deb with a patch for the bug (as is common in debs). Every time a new release of Gedit comes down the pike, evaluate it and update your deb accordingly. Of course, you should send your patch upstream, but if it's the wrong solution (as it appears), don't expect it to be accepted.

Good suggestions. My opinion is the same as Peter's: renaming or moving an open file is a bad solution. Therefore, I do not agree that the focus should  be placed on changing the filesystems (cifs, smbfs, etc.). 

The whole reason gedit has been stuck with this bug for over two years is that each side points the finger at the other side. As long as that is going on nothing will get done. The file system people are not going to do any work to support a behavior they feel is incorrect (and that makes perfect sense to me). 

The only way to move forward to is deal with this on the editor side.

---

### Post by MountainX on 2008-03-28
I'm going to copy from Peter's original comment here:
[https://bugs.launchpad.net/gedit/+bug/34813/comments/20](https://bugs.launchpad.net/gedit/+bug/34813/comments/20)

He says:

[I]Ok, this is the problem:

Gedit opens a file, moves the original file to a backup file while keeping the file open, and finally deletes the backup file if you choose not to keep backups.
The rename method sets errno = ETXTBSY, so moving the original file fails.

I don't think moving/deleting open files on purpose is a good idea, although it works for most linux file systems. But its definitely a bad idea for network file systems like sshfs and cifs, which of course fails.[/I]

This explains why disabling the backup preference in gedit doesn't solve the issue under cifs shares to Windows computers. If I understand Peter correctly, when the backup option is disabled, the attempt to move/rename the file is still made.

---

### Post by MountainX on 2008-03-28
> **asmoore82 said:**
> I justed tested this with Gedit over sshfs on 7.10 Gutsy.

on a Graphically "mounted" sshfs via Nautilus "Places -> Connect to Server,"
I encountered no problems whatsoever.

I think the most of the people seeing the problem are using shares residing on Windows machines.

> **asmoore82 said:**
> 
I saw the issue and resolved it by simply telling Gedit not to create backup files:
As your later post indicates, this seems to have nothing to do with the "backup" preference in gedit. I understand gedit still attempts to move the original file no matter how this option is set.

---

### Post by frego on 2008-03-28
I just did some testing myself.  I'm mounting a cifs share from Gutsy on an XP box using fstab of:

//winbox/share /mnt/winbox cifs credentials=/home/myusername/.smbpasswd,noperm,nocase,file_mode=0777,dir_mode=0777 0 0

and gedit will open and save to a file on that share, although periodically, it does give me a weird message:

"The file /mnt/winbox/test.txt has been modified since reading it.
If you save it, all the external changes could be lost. Save it anyway?"

I'm allowed to choose "save anyways" or "don't save".  If I choose "Save anyways", it saves it.  So the message is annoying but hardly anything worthy of forking.  I also notice my ~ file is created ok too.  Maybe your experience differs from mine because you aren't mounting the same way, or perhaps its a difference between an actual windows box and a samba share.  Either way, I don't see it being a gedit issue.  Or am I missing something?

---

### Post by MountainX on 2008-03-28
> **frego said:**
>  Or am I missing something?

Just wait 'til you upgrade to Hardy. Then it will be completely broken.

---

### Post by frego on 2008-03-28
I just did my above testing on a Hardy machine and gedit still works!  I do still get the nag message though.

I did have some trouble getting my cifs share to mount.  For anyone else, I had to install smbfs to be able to mount as shown in my previous thread.  Can you replicate this problem on a windows share or are your files you are trying to edit on a samba share?

---

### Post by MountainX on 2008-03-28
> **frego said:**
> I just did my above testing on a Hardy machine and gedit still works!  I do still get the nag message though.

Wow. I will have to keep trying. I could get it to work under Gutsy but not under Hardy now. I understand that in Hardy smbfs is just a wrapper for cifs. Maybe you installed something that is in addition to the Hardy packages?

> **frego said:**
> 
I did have some trouble getting my cifs share to mount.  For anyone else, I had to install smbfs to be able to mount as shown in my previous thread.  Can you replicate this problem on a windows share or are your files you are trying to edit on a samba share?

By "samba share" do you mean smbfs on Linux servers? And by "windows share" do you mean samba client connected to Windows machines? I'm still trying to get all the terminology straight.

---

### Post by frego on 2008-03-28
> By "samba share" do you mean smbfs on Linux servers?
YES

> And by "windows share" do you mean samba client connected to Windows machines?
YES, I meant my ubuntu machine mounting a native (true) windows share, XP SP2 through mount -t cifs (see my fstab from prior post for exact syntax.  NOTE:  specific permission for files and directories that was needed.)

> Maybe you installed something that is in addition to the Hardy packages?
YES
What I installed on my Hardy machine that finally allowed me to mount was to go into Synaptic and add the program whose name is:
smbfs

It wasn't installed by default even though samba client is.:grin:

---

### Post by slavik on 2008-03-29
do you have to fork gedit to fix it? can't you just submit a patch?

---

### Post by MountainX on 2008-03-29
> **slavik said:**
> do you have to fork gedit to fix it? can't you just submit a patch?

My understanding, based on reading the bug report comments, is that the gedit devs know how to fix it. (I believe patches have been submitted in the past.) I am told that the gedit devs don't want to copy the backup file because (I assume) it is inefficient. But wouldn't it be better to have code that is more robust even if slightly less efficient?

There is all this discussion about the fact that renaming/moving an open file works on Linux file systems, so the problem isn't really a gedit problem. But Windows won't let you do that, so if gedit is going to function in a mixed environment, it can't attempt to do something that won't work on Windows shares. I do not see that this can be addressed at the file system level. Apparently it could easily be fixed in gedit if the devs weren't so against copying the file instead of moving it.

Keep in mind all my comments are simply based on reading the bug reports. If someone knows better than I do, feel free to correct me.

---

### Post by AnRa on 2008-03-29
Did you try using the **native** support of gedit to open the file via SSH or SAMBA instead of mounting the filesystem?

---

### Post by MountainX on 2008-03-30
RESOLUTOIN:
I installed  Windows Services for Unix (SFU 3.5) and the accompanying NFS server on my file server (which runs Windows Server 2003 SP1). 

It took me all weekend to work out the issues, but now I'm using the NFS protocol instead of samba or cifs. That solved the gedit/cifs issue for me and believe I'll have better file sharing speed over the network (although I haven't found the definitive benchmark yet).

I have also come to like SciTE quite a bit. I used it while I couldn't work with gedit. It has some great handling of line end characters for people who use both Windows and Linux.

While this does nothing for the bigger picture, others might like knowing that there are ways to resolve this without patching or modifying gedit or cifs -- basically, just side step the issue ;)

---

### Post by slavik on 2008-03-30
> **MountainX said:**
> My understanding, based on reading the bug report comments, is that the gedit devs know how to fix it. (I believe patches have been submitted in the past.) I am told that the gedit devs don't want to copy the backup file because (I assume) it is inefficient. But wouldn't it be better to have code that is more robust even if slightly less efficient?

There is all this discussion about the fact that renaming/moving an open file works on Linux file systems, so the problem isn't really a gedit problem. But Windows won't let you do that, so if gedit is going to function in a mixed environment, it can't attempt to do something that won't work on Windows shares. I do not see that this can be addressed at the file system level. Apparently it could easily be fixed in gedit if the devs weren't so against copying the file instead of moving it.

Keep in mind all my comments are simply based on reading the bug reports. If someone knows better than I do, feel free to correct me.
but do you have to fork gedit?

---

### Post by AceGopher on 2008-08-21
Looks like Red Hat has taken the matter into their own hands and fixed gedit in their upstream:

link: [URL="http://rhn.redhat.com/errata/RHBA-2008-0019.html"]
gedit bug fix update[/URL] (rhn.redhat.com)

"* gedit was not able to save changes to a file on a Windows share mounted
using the Common Internet File System (CIFS)."

Perhaps the Ubuntu packagers need to take a cue from Red Hat on this one.

BTW, I'm seeing the issue too (in Hardy)...

-Ace

---

### Post by Aikon- on 2009-01-30
> **AceGopher said:**
> Looks like Red Hat has taken the matter into their own hands and fixed gedit in their upstream:

link: [URL="http://rhn.redhat.com/errata/RHBA-2008-0019.html"]
gedit bug fix update[/URL] (rhn.redhat.com)

"* gedit was not able to save changes to a file on a Windows share mounted
using the Common Internet File System (CIFS)."

Perhaps the Ubuntu packagers need to take a cue from Red Hat on this one.

BTW, I'm seeing the issue too (in Hardy)...

-Ace

This would indeed be nice... or at least the *option*! I understand how the devs want to keep option bloat down, but I have seen so many bug reports and forum posts about this, and I am affected by it myself, it seems to be a big enough issue to warrant one!

-Aikon

---

### Post by michaelzap on 2009-03-19
> **Aikon- said:**
> This would indeed be nice... or at least the *option*! I understand how the devs want to keep option bloat down, but I have seen so many bug reports and forum posts about this, and I am affected by it myself, it seems to be a big enough issue to warrant one!
Agreed. This option would definitely not be bloat. If I can't resolve this issue I'm going to have to stop using Gedit, and I'd really rather not do that.

Why is this issue marked as solved? The only resolution that I see listed here is to use NFS or some other protocol to mount the remote file system. That's not a viable option for me (my files are on a Buffalo Linkstation that only speaks SMB/CIFS), and it's not really a fix but just an avoidance of the problem.

Is there another resolution that I missed somewhere?

---

### Post by sarang on 2009-03-19
> **MountainX said:**
> RESOLUTOIN:
I installed  Windows Services for Unix (SFU 3.5) and the accompanying NFS server on my file server (which runs Windows Server 2003 SP1). 

It took me all weekend to work out the issues, but now I'm using the NFS protocol instead of samba or cifs. That solved the gedit/cifs issue for me and believe I'll have better file sharing speed over the network (although I haven't found the definitive benchmark yet).


FYI: NFS is a whole new can of worms. Very little security, if at all. AFAIK, anyone can change anyone else's files with very little effort.

---

### Post by vaibhav8275 on 2012-12-29
> **lilian said:**
> I agree that this problem is very annoying and it is a big problem for me because I am trying to use Ubuntu at work and need to deal with network shares...

But I think the problem is not only regarding gedit. I don't know what is the root cause, but it affects at least gedit and eclipse.

For example, if I create an Eclipse workspace on a samba share over cifs, it is quite impossible to work, eclipse is always saying "the file was modified outside..." or "out of sync" etc.

I cannot be sure, but I think the problem is the same and comes from samba.

A better idea than forking gedit may be identifying the root cause and solve it :cool:

Best regards
Lilian

Hi Lilian
I am new to linux platform can you help me how to fork gedit and what do you mean by forking?

---

### Post by howefield on 2012-12-29
Old thread closed.

---

