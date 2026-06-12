---
title: "Viewing &quot;Windows Hidden Files&quot; on a cd"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by sebba on 2008-05-13
Hi All,

Not sure if it is just a little glitch or whether I am doing something wrong.

I have a cd containing a mixture of normal files and files which have been set to 'hidden' on the windows machine that burnt the cd. These files can be seen fine in windows if the 'show hidden files' option is checked.

In ubuntu (hardy) the cd mounts fine, and I can see the normal files, but all the files which are "windows" hidden cannot be seen. Ctrl H to show/unshow hidden files has no effect. Obviously I can work around this by copying the files to another partition/reburning without hidden options, but is there anyway of displaying these hidden files in ubuntu.

Note that it is not just nautilus that cannot see them, no program can! (Sudo nautilus also does not see them).

Any ideas?

Many thanks.

---

### Post by mapes12 on 2008-05-13
What is the reason why you are looking to hide the files you are referring to?

---

### Post by sebba on 2008-05-13
It is more the fact that they are already hidden and I wish to know how I can view them, so that I know there is a way I can do it without booting into windows.

---

### Post by SunnyRabbiera on 2008-05-13
are these folders encrypted by any chance?
or have permissions attached to them in windows?

---

### Post by sebba on 2008-05-13
Thank you for your replies.

Definately not encrypted. Not aware of any permissions. The common feature of the files that aren't viewable is that they are 'hidden' by windows whereas the ones that can be seen are not hidden.

---

### Post by Endolith on 2008-08-31
This is the way it SHOULD work, but not the way it does work.  Hidden Windows files are always visible in Nautilus.

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/130997](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/130997)

I don't think your problem is related to the fact that they are hidden?

---

### Post by glacialfury on 2008-09-22
No, I don't think that's the problem.  I've seen it too.

I have a CD with cadaver images that, for privacy reasons, are tagged as "Hidden" files.  Normally, it only shows the user an .htm file that starts it all up.  If, in Windows, you change the option to see hidden files, they show up normally in Explorer.

When I mount that same CD in Ubuntu, I only see the .htm file.  Using ctrl+H doesn't change whether or not I see the other files.  If I load that .htm file in a browser, it reads the page, but the browser ALSO cannot access the files, because it doesn't see them either.

In my case, I loaded the CD in WindowsXP in VirtualBox and copied all the hidden files to a directory that is shared with the external Ubuntu host.  All this so I can run a simple CD.

---

### Post by AStroP on 2008-11-14
I had the same problem. [Ubuntu 8.04]
Even Firefox was unable to access the hidden files on a CD.
I found the solution here:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount.2Funmount_CD.2FDVD-ROM_manually.2C_and_show_all_hidden_and_associated_files.2Ffolders](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount.2Funmount_CD.2FDVD-ROM_manually.2C_and_show_all_hidden_and_associated_files.2Ffolders)

> [...snip...]

How to mount/unmount CD/DVD-ROM manually, and show all hidden and associated files/folders:
e.g. Assumed that /media/cdrom0/ is the location of CD/DVD-ROM 

* To mount CD/DVD-ROM 

sudo mount /media/cdrom0/ -o unhide

* To unmount CD/DVD-ROM 

sudo umount /media/cdrom0/

[...snip...]

---

