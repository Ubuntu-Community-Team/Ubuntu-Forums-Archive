---
title: "How do I transfer my files to google drive mount via terminal, Ubuntu 19.04"
date: 2019-09-17
forum: New to Ubuntu
---

### Post by tianbuntu on 2019-09-17
[COLOR=#242729][FONT=Arial]Under *Settings* &#8594; *Online Accounts* I am able to connect my gmail account, which allows me to mount my google drive as a network drive. The path of the mount was found by opening a terminal within the mount window. It is given by:[/FONT][/COLOR]
[COLOR=#303336][FONT=inherit]/[/FONT][/COLOR][COLOR=#303336][FONT=inherit]run[/FONT][/COLOR][COLOR=#303336][FONT=inherit]/[/FONT][/COLOR][COLOR=#303336][FONT=inherit]user[/FONT][/COLOR][COLOR=#303336][FONT=inherit]/[/FONT][/COLOR][COLOR=#7D2727][FONT=inherit]1000[/FONT][/COLOR][COLOR=#303336][FONT=inherit]/[/FONT][/COLOR][COLOR=#303336][FONT=inherit]gvfs[/FONT][/COLOR][COLOR=#303336][FONT=inherit]/[/FONT][/COLOR][COLOR=#303336][FONT=inherit]google[/FONT][/COLOR][COLOR=#303336][FONT=inherit]-[/FONT][/COLOR][COLOR=#303336][FONT=inherit]drive[/FONT][/COLOR][COLOR=#303336][FONT=inherit]:[/FONT][/COLOR][COLOR=#303336][FONT=inherit]host[/FONT][/COLOR][COLOR=#303336][FONT=inherit]=[/FONT][/COLOR][COLOR=#303336][FONT=inherit]gmail[/FONT][/COLOR][COLOR=#303336][FONT=inherit].[/FONT][/COLOR][COLOR=#303336][FONT=inherit]com[/FONT][/COLOR][COLOR=#303336][FONT=inherit],[/FONT][/COLOR][COLOR=#303336][FONT=inherit]user[/FONT][/COLOR][COLOR=#303336][FONT=inherit]=[/FONT][/COLOR][COLOR=#303336][FONT=inherit]gmail_user_name[/FONT][/COLOR][COLOR=#303336][FONT=inherit]
[/FONT][/COLOR]

[COLOR=#242729][FONT=Arial]I am trying to write a crontab background process which syncs specified folders from my home directory every so often. I do so by using the following bash script to transfer specified directories into the mounted network drive.
[/FONT][/COLOR]
```
[COLOR=#858C93][FONT=inherit]#!/bin/bash[/FONT][/COLOR][COLOR=#303336][FONT=inherit]
googledrive_dir[/FONT][/COLOR][COLOR=#303336][FONT=inherit]=/[/FONT][/COLOR][COLOR=#303336][FONT=inherit]run[/FONT][/COLOR][COLOR=#303336][FONT=inherit]/[/FONT][/COLOR][COLOR=#303336][FONT=inherit]user[/FONT][/COLOR][COLOR=#303336][FONT=inherit]/[/FONT][/COLOR][COLOR=#7D2727][FONT=inherit]1000[/FONT][/COLOR][COLOR=#303336][FONT=inherit]/[/FONT][/COLOR][COLOR=#303336][FONT=inherit]gvfs[/FONT][/COLOR][COLOR=#303336][FONT=inherit]/[/FONT][/COLOR][COLOR=#303336][FONT=inherit]google[/FONT][/COLOR][COLOR=#303336][FONT=inherit]-[/FONT][/COLOR][COLOR=#303336][FONT=inherit]drive[/FONT][/COLOR][COLOR=#303336][FONT=inherit]:[/FONT][/COLOR][COLOR=#303336][FONT=inherit]host[/FONT][/COLOR][COLOR=#303336][FONT=inherit]=[/FONT][/COLOR][COLOR=#303336][FONT=inherit]gmail[/FONT][/COLOR][COLOR=#303336][FONT=inherit].[/FONT][/COLOR][COLOR=#303336][FONT=inherit]com[/FONT][/COLOR][COLOR=#303336][FONT=inherit],[/FONT][/COLOR][COLOR=#303336][FONT=inherit]user[/FONT][/COLOR][COLOR=#303336][FONT=inherit]=[/FONT][/COLOR][COLOR=#303336][FONT=inherit]gmail_user_name
dir_cat[/FONT][/COLOR][COLOR=#303336][FONT=inherit]=[/FONT][/COLOR][COLOR=#7D2727][FONT=inherit]'Admin'[/FONT][/COLOR][COLOR=#303336][FONT=inherit]

[/FONT][/COLOR][COLOR=#101094][FONT=inherit]for[/FONT][/COLOR][COLOR=#303336][FONT=inherit] name [/FONT][/COLOR][COLOR=#101094][FONT=inherit]in[/FONT][/COLOR][COLOR=#303336][FONT=inherit] $dir_cat
[/FONT][/COLOR][COLOR=#101094][FONT=inherit]do[/FONT][/COLOR][COLOR=#303336][FONT=inherit]
    rsync [/FONT][/COLOR][COLOR=#303336][FONT=inherit]-[/FONT][/COLOR][COLOR=#303336][FONT=inherit]avhz [/FONT][/COLOR][COLOR=#303336][FONT=inherit]~/[/FONT][/COLOR][COLOR=#303336][FONT=inherit]$name $googledrive_dir[/FONT][/COLOR][COLOR=#303336][FONT=inherit]/[/FONT][/COLOR][COLOR=#303336][FONT=inherit]--[/FONT][/COLOR][COLOR=#303336][FONT=inherit]delete
[/FONT][/COLOR][COLOR=#101094][FONT=inherit]done

[/FONT][/COLOR]
```[COLOR=#242729][FONT=Arial]Upon running the bash script, the files inside the directories within each specified folder in dir_cat are deleted. And I get an output error, shown below:

[/FONT][/COLOR]
```
[COLOR=#303336][FONT=inherit]sending incremental file list
rsync[/FONT][/COLOR][COLOR=#303336][FONT=inherit]:[/FONT][/COLOR][COLOR=#303336][FONT=inherit] failed to [/FONT][/COLOR][COLOR=#101094][FONT=inherit]set[/FONT][/COLOR][COLOR=#303336][FONT=inherit] times on [/FONT][/COLOR][COLOR=#7D2727][FONT=inherit]"/run/user/1000/gvfs/google-drive:host=gmail.com,user=google_user_name/Admin"[/FONT][/COLOR][COLOR=#303336][FONT=inherit]:[/FONT][/COLOR][COLOR=#2B91AF][FONT=inherit]Operation[/FONT][/COLOR][COLOR=#303336][FONT=inherit] not supported [/FONT][/COLOR][COLOR=#303336][FONT=inherit]([/FONT][/COLOR][COLOR=#7D2727][FONT=inherit]95[/FONT][/COLOR][COLOR=#303336][FONT=inherit])[/FONT][/COLOR][COLOR=#303336][FONT=inherit]
deleting [/FONT][/COLOR][COLOR=#2B91AF][FONT=inherit]Admin[/FONT][/COLOR][COLOR=#303336][FONT=inherit]/[/FONT][/COLOR][COLOR=#7D2727][FONT=inherit]19sZNc[/FONT][/COLOR][COLOR=#303336][FONT=inherit]-[/FONT][/COLOR][COLOR=#303336][FONT=inherit]h9o1u65ZT5ANXyKXgQVEzU92Th
[/FONT][/COLOR][COLOR=#2B91AF][FONT=inherit]Admin[/FONT][/COLOR][COLOR=#303336][FONT=inherit]/[/FONT][/COLOR][COLOR=#303336][FONT=inherit]
[/FONT][/COLOR][COLOR=#2B91AF][FONT=inherit]Admin[/FONT][/COLOR][COLOR=#303336][FONT=inherit]/[/FONT][/COLOR][COLOR=#303336][FONT=inherit]cubicle_name_tag[/FONT][/COLOR][COLOR=#303336][FONT=inherit].[/FONT][/COLOR][COLOR=#303336][FONT=inherit]odt
rsync[/FONT][/COLOR][COLOR=#303336][FONT=inherit]:[/FONT][/COLOR][COLOR=#303336][FONT=inherit] mkstemp [/FONT][/COLOR][COLOR=#7D2727][FONT=inherit]"/run/user/1000/gvfs/google-drive:host=gmail.com,user=google_user_name/Admin/.cubicle_name_tag.odt.Que9bQ"[/FONT][/COLOR][COLOR=#303336][FONT=inherit] failed[/FONT][/COLOR][COLOR=#303336][FONT=inherit]:[/FONT][/COLOR][COLOR=#2B91AF][FONT=inherit]Operation[/FONT][/COLOR][COLOR=#303336][FONT=inherit] not supported [/FONT][/COLOR][COLOR=#303336][FONT=inherit]([/FONT][/COLOR][COLOR=#7D2727][FONT=inherit]95[/FONT][/COLOR][COLOR=#303336][FONT=inherit])[/FONT][/COLOR][COLOR=#303336][FONT=inherit]

sent [/FONT][/COLOR][COLOR=#7D2727][FONT=inherit]11.68K[/FONT][/COLOR][COLOR=#303336][FONT=inherit] bytes  received [/FONT][/COLOR][COLOR=#7D2727][FONT=inherit]377[/FONT][/COLOR][COLOR=#303336][FONT=inherit] bytes  [/FONT][/COLOR][COLOR=#7D2727][FONT=inherit]3.44K[/FONT][/COLOR][COLOR=#303336][FONT=inherit] bytes[/FONT][/COLOR][COLOR=#303336][FONT=inherit]/[/FONT][/COLOR][COLOR=#303336][FONT=inherit]sec
total size is [/FONT][/COLOR][COLOR=#7D2727][FONT=inherit]13.12K[/FONT][/COLOR][COLOR=#303336][FONT=inherit]  speedup is [/FONT][/COLOR][COLOR=#7D2727][FONT=inherit]1.09[/FONT][/COLOR][COLOR=#303336][FONT=inherit]
rsync error[/FONT][/COLOR][COLOR=#303336][FONT=inherit]:[/FONT][/COLOR][COLOR=#303336][FONT=inherit] some files[/FONT][/COLOR][COLOR=#303336][FONT=inherit]/[/FONT][/COLOR][COLOR=#303336][FONT=inherit]attrs were not transferred [/FONT][/COLOR][COLOR=#303336][FONT=inherit]([/FONT][/COLOR][COLOR=#303336][FONT=inherit]see previous errors[/FONT][/COLOR][COLOR=#303336][FONT=inherit])[/FONT][/COLOR][COLOR=#303336][FONT=inherit]([/FONT][/COLOR][COLOR=#303336][FONT=inherit]code [/FONT][/COLOR][COLOR=#7D2727][FONT=inherit]23[/FONT][/COLOR][COLOR=#303336][FONT=inherit])[/FONT][/COLOR][COLOR=#303336][FONT=inherit] at main[/FONT][/COLOR][COLOR=#303336][FONT=inherit].[/FONT][/COLOR][COLOR=#303336][FONT=inherit]c[/FONT][/COLOR][COLOR=#303336][FONT=inherit]([/FONT][/COLOR][COLOR=#7D2727][FONT=inherit]1207[/FONT][/COLOR][COLOR=#303336][FONT=inherit])[/FONT][/COLOR][COLOR=#303336][FONT=inherit][[/FONT][/COLOR][COLOR=#303336][FONT=inherit]sender[/FONT][/COLOR][COLOR=#303336][FONT=inherit]=[/FONT][/COLOR][COLOR=#7D2727][FONT=inherit]3.1[/FONT][/COLOR][COLOR=#303336][FONT=inherit].[/FONT][/COLOR][COLOR=#7D2727][FONT=inherit]3[/FONT][/COLOR][COLOR=#303336][FONT=inherit]]


[/FONT][/COLOR]
```[FONT=Arial][COLOR=#242729]I found that by replacing the '[/COLOR][COLOR=#101094]-a'[/COLOR][COLOR=#242729] with '[/COLOR][COLOR=#101094]-r',[/COLOR][COLOR=#242729] rsync first deletes all the contents in the specified folders before copying over the files. This process is time consuming and computationally wasteful.

How should I go about this?

[/COLOR][/FONT]

---

### Post by TheFu on 2019-09-17
I don't use cloudy storage, except my own storage 100% owned by me. Don't know a thing about box, google, msft, amazon or any other cloudy storage, but .... 

rsync -avz [source] [target]
is the normal command I use for this.  However, if both the source and target appear to be local, then rsync assumes that just doing the copy is faster than performing the block-by-block comparison.  You can tell rsync to use timestamps and file sizes over just copying everything for local-to-local copies.  The rsync manpage has those options.

There are rsync options to delete-before and delete-after and files that have been removed from the source that are still in the target too.

GVFS is just about the slowest remote storage protocol out there, except, perhaps sshfs.  
[https://ubuntuforums.org/showthread.php?t=2337462](https://ubuntuforums.org/showthread.php?t=2337462) is where people complain about poor performance too. Looks like they use the web interface to get the best performance.  [https://www.omgubuntu.co.uk/2017/04/mount-google-drive-ocamlfuse-linux](https://www.omgubuntu.co.uk/2017/04/mount-google-drive-ocamlfuse-linux) is a different FUSE option which might be faster?  IDK.

---

### Post by SeijiSensei on 2019-09-17
> rsync: failed to set times on "/run/user/1000/gvfs/google-drive:host=gmail.com,user=google_user_name/Admin":Operation not supported (95)
deleting Admin/19sZNc-h9o1u65ZT5ANXyKXgQVEzU92Th

This happens when the remote device doesn't support standard *nix protocols.  It's possible the Google drive is formatted with NTFS or some other filesystem.

Using the -a switch will overwrite any files that have changed and leave untouched those which have not been changed. Unfortunately for you, since the modification times on the remote drive are not available to rsync, it has to transfer all the files again.

One kludgy solution to this problem is to use tar to create a compressed archive of the files you want to back up and transfer the tar archive.

```

cd /
tar czpf Admin.tgz Admin
rsync -avz Admin.tgz /run/user/1000/gvfs/google-drive:host=gmail.com,user=gmail_user_name

```

Maybe some version of that will work for you.  

You might want to create versioned archives with filenames that include dates like
```

tar czpf Admin-$(date +%Y%m%d).tgz Admin

```

I keep five backups and delete the oldest one every day.
```

rm -f /path/to/archive/dir/Admin-$(date +%y%m%d --date='5 days ago').tgz

```

---

### Post by GrouchyGaijin on 2019-09-17
I may have misunderstood something, but if you want to move files to Google Drive couldn't you connect to Google as an online account and move files locally?
I am running Ubuntu 18.04 with Gnome shell. I connected to Google as an offline account. When I look in:

```
/run/user/1000/gvfs
```

I see both my Google Drive and my NAS which I mount as a Samba share. I can move files to and from the gvfs folders via the terminal.

OOPS I guess I did not read the first post carefully enough.

---

### Post by TheFu on 2019-09-17
As soon as there is a "gvfs" in the path, it will be slow.  That applies to local storage or remote storage.  

Almost always, the performance solution to this is to do anything you can to avoid GVFS in the access for any storage.  That usually means simply avoid making the initial access using a GUI.  I like to say "use real mounts" for storage.  That usually means there are 3 viable options.
[LIST=1]
[*]/etc/fstab
[*]sudo mount .....  on a command line or in a script
[*]autofs - which effectively uses the same mount as the fstab method
[/LIST]
None of those have GUI equivalents. Each has pros/cons.  All also require the correct disk/access driver be loaded. For google-drive, it appears the ocamlfuse driver is needed?  IDK.  I found some articles saying there is a PPA for this driver, but none of the links are to sites I know as reputable. YMMV.

The Gnome project was trying to fix the gvfs performance issues the last year, but I've not seen anything other than vague announcements they were going to do something.  No results announced that I've seen. [https://www.phoronix.com/scan.php?page=news_item&px=GNOME-3.33.1-Released](https://www.phoronix.com/scan.php?page=news_item&px=GNOME-3.33.1-Released) was the last I found.

---

### Post by tianbuntu on 2019-09-18
Awesome, thanks for the advice. Will check ocamlfuse out, thanks for the recommendation!

---

### Post by tianbuntu on 2019-09-19
UPDATE: google-drive-ocamlfuse works brilliantly with rsync -azv --delete source destination.
Thanks for the reccomendations!!

---

