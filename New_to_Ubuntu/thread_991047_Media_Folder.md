---
title: "Media Folder"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by byrong on 2008-11-23
I keep running out of diskspace on my old 40 GB hard drive.  I think I've moved everything off but linux and it shows 2.9 GB free after doing all the purges shown on this forum that I could find.  I did a list of subdirectories and size and I get this:

	Size MB	Size GB
bin	4.9	0.0048
boot	52.9	0.0517
cdrom	0	0.0000
dev	2	0.0020
etc	8	0.0078
home	2355.2	2.3000
initrd	2764.8	2.7000
lib	382.1	0.3821
lost+found	unreadable	unreadable
media	25395.2	24.8000
mnt	0	0.0000
opt	0	0.0000
proc	512.1	0.5121
root	0	0.0000
sbin	6.4	0.0064
srv	0	0.0000
sys	295.3	0.2953
tmp	0.1	0.0001
usr	2355.2	2.3000
var	344.9	0.3449
		
	34479.1	33.7071

I have since deleted the lost+found directory but there wasn't anything in there.  

I look in Media folder and it shows my CDROM, Other hard drive, and a backup file.  It looks like as the drives are mounted it puts them in here but that doesn't make sense to me.  I have some experience with Novell but don't remember it doing that.  What's up?

Thank you.

---

### Post by Paqman on 2008-11-23
Removable media like CDs and external hard drives definitely do go in /media. The backup file sounds wrong though. Was it supposed to get written to the other hard drive? If the drive wasn't connected to the machine when the backup ran, it may have written the backup to /media/somefolder locally instead of writing it to the device that would have been mounted there. I just got caught out by a backup doing that to me a couple of days ago.

---

### Post by byrong on 2008-11-23
OK - I deleted that weird backup file and that helps a lot.

Why doesn't mounted media take up space on the primary hard drive?

Why do I have two other hard drives showing and two floppy drives showing when I only have one of each?

Thank you.

---

### Post by byrong on 2008-11-23
And, if I delete stuff out of the media subdirectory does it delete it off the other hard drive?

---

### Post by Paqman on 2008-11-23
> **byrong said:**
> OK - I deleted that weird backup file and that helps a lot.

Why doesn't mounted media take up space on the primary hard drive?


Because it would be a pain if it did. Example: my root partition is something like 19GB. When I mount my 160GB's of data in my NAS to /media I obviously don't want it think i've put 160GB into a 19GB system!

> 
Why do I have two other hard drives showing and two floppy drives showing when I only have one of each?

Thank you.

Are you looking in /media or /dev? /dev has all sorts of weird stuff.

> **byrong said:**
> And, if I delete stuff out of the media subdirectory does it delete it off the other hard drive?

If you mount your hard drive to /media/harddrive then if that drive is mounted, it will be treated as if all it's contents were on the local machine. So if you delete /media/hardrive/folder then yes, /folder will be deleted on that drive. You can have some control over how much damage you can do by setting some permissions in the line in /etc/fstab which mounts the drive.

---

### Post by byrong on 2008-11-23
Yes.  This is what my media folder looks like.  

<a href="http://s437.photobucket.com/albums/qq94/byron_allis/?action=view&current=Screenshot-media-FileBrowser.png" target="_blank"><img src="http://i437.photobucket.com/albums/qq94/byron_allis/Screenshot-media-FileBrowser.png" border="0" alt="screenshot"></a>

External backup is the name of my other hard drive in my PC.  I had it in a USB external hard drive box but couldn't get it to work so put it in my PC.  The External Backup without the _ at the end looks like it has backup files in it too.  I use Simple Backup.

Thank you for your help.

---

### Post by byrong on 2008-11-23
Try this pic maybe.

[IMG]http://i437.photobucket.com/albums/qq94/byron_allis/Screenshot-media-FileBrowser.png[/IMG]

---

### Post by byrong on 2008-11-23
It seems everything was caused by the simple backup program.  It made the separate volumes and put copies of the backups in there.  Maybe it's how I set it up.  Anyway.  Makes sense now.  Thank you for the help.  I learned a lot today.

---

