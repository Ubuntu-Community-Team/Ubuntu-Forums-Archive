---
title: "External HDD folders locked under Ubuntu Oneric"
date: 2012-01-17
forum: New to Ubuntu
---

### Post by paulsails01 on 2012-01-17
I am hoping that somebody may be able to assist me.

I use an external Hardrive to store and work from all of my documents and picture libraries, but after installing the latest Ubuntu OS (Oneric Ocelot) my folders in the external HDD are all "locked" and do not allow me to cut, paste, copy or edit. This situation appears to be of a permanent nature.

This is very frustrating as I do not know what is the cause, I really need to have full access to this HDD as I have very important legal template type documents that I need to work on.

I originally chose Ubuntu some years ago as of the virus free environment was appealing, I also have grown to like the simplicity of the Linux OS systems, I dabble but rarley venture into the CL, although not afraid, just never really had the need until now.

So if somebody can provide guidance to methodically identify the problem and then suggest remedial action I would be appreciative.

regards,   Paul.

---

### Post by Gone fishing on 2012-01-18
If you open the files as a superuser are they still locked?

sudo nautilus

---

### Post by lechien73 on 2012-01-18
It looks like the drive is being mounted as read-only. You could try:

1. Unmount the drive, and unplug the USB connection.

2. Open a terminal window, plug the hard drive back in and type:

```
dmesg
```

You may see errors there that indicate why the drive is being mounted as read-only.

It could be something as simple as a dirty file system, in which case run the **Disk Utility** from the dash (click on the Ubuntu icon in the sidebar, type *disk utility* into the search box), unmount the device & check the file system from there.

NB - if you want to run Nautilus as the superuser, then I'd suggest:

```
gksu nautilus
```

instead of sudo :)

---

### Post by Double.J on 2012-01-18
> **lechien73 said:**
> 
```
gksu[COLOR="Green"]do[/COLOR] nautilus
```


;)

---

### Post by Grenage on 2012-01-18
> **gnu/mirow said:**
> ;)

gksu works, it's a symlink to the same program; I think gksu might even be the original name!

---

### Post by lechien73 on 2012-01-18
@gnu/mirow - true...good catch :D

---

### Post by Gone fishing on 2012-01-18
Fair enough gksu nautilus would be better.

However, what we need to know is is the drive being mounted read only or is it a permissions problem.

If it isn't locked with nautilus as a superuser then it's a permissions problem - I wasn't suggesting running nautilus as a superuser as the solution to the problem.

---

### Post by paulsails01 on 2012-01-18
The  following message was displayed after I typed the command "gksu nautilus". I am unsure what it means, however I suspect that there is nothing wrong?
I also performed the "system check" with the "disk utility" and final message was everything is OK.
I suspect that this may be a permissions issue, but am unsure what is required to take the "locks" of my folders and files.  
Paul

paul@Desktop-black:~$ gksu nautilus

(gksu:2820): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksu:2820): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksu:2820): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksu:2820): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
** (nautilus:2822): DEBUG: Syncdaemon not running, waiting for it to start in NameOwnerChanged
Initializing nautilus-gdu extension

--- Hash table keys for warning below:
--> l2049
--> root
--> inode/directory

--- Hash table keys for warning below:
--> file:///
Shutting down nautilus-gdu extension

(nautilus:2822): Eel-WARNING **: "unique eel_ref_str" hash table still has 3 elements at quit time (keys above)

(nautilus:2822): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time (keys above)
paul@Desktop-black:~$

---

### Post by Gone fishing on 2012-01-18
gksu opens nautilus (the file manager) as superuser (root). Once nautilus is open can you go to the external drive (using nautilus as superuser) and open, change and save files?

---

### Post by syerges on 2012-01-18
use gparted to see if it is mounted as read only or read/write access

if not you have to edit your fstab so it does

---

### Post by paulsails01 on 2012-01-18
When I CL "gksu nautilus" I am taken to the GUI of my external HDD. I can open up to the files but the files have the "lock" image in lower left hand corner which will not allow me to "cut, rename, move to, move to the rubbish bin"
I am not familiar with Gparted, could someone walk me through this operation?

---

### Post by Gone fishing on 2012-01-19
I think you drive is being mounted read only can you just check that you have ntfs-3g installed.

sudo apt-get install ntfs-3g

---

