---
title: "Intrepid, Automount and FSTAB"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by BGFG on 2008-11-17
Hi all,

In HARDY I had figured out how to automount drives by editing /etc/fstab and etc/mtab. Since my upgrade to intrepid, i have since forgotten.

So for all noobs, 

Go: Applications>>Add Remove>>System Tools

then install: Storage Device Manager. (there are actually several such tools to choose from, just scroll through and read the info)

Using this tool via System>>Administration>>Storage Device Manager, I was able to set my extra ext3 and ntfs drives to be mounted at boot :) Yay. I restarted (long time since i did that) to test and works great. I checked my fstab and the relevant entries had been made.

Using the terminal to configure your system and edit files is a great way to learn linux and empower yourself, but there are talented programmers out there who insist on making life easy for us and providing GUI's. All we have to do is be willing to search for a little.

Also feel free to check out some of the other such tools and report back.

---

### Post by BGFG on 2008-11-18
Bump, i posted this pretty late :) apologies.

---

### Post by granny4linux on 2008-12-12
Thanks, this was a big help.

---

### Post by Eric Qel-Droma on 2008-12-13
What options do I need to check in Storage Device Manager to make it so that I can open the files in these drives as read-write and NOT read-only, which is what I'm stuck with now?

I can run gksudo nautilus, but that's not something I really want to do all the time, is it?

Thanks,

Eric

---

### Post by merwizard on 2008-12-13
To enable read/write support for fat and ntfs partitions, the parameter umask=000 must be specified. In addition, ntfs partitions should be mounted as ntfs-3g type. This has to be manually written in fstab, and then the storage device manager has to be opened again, and the new configuration applied.

I really am puzzled about not being able to modify /etc/fstab by hand, since it is overwritten at boot. Took me hours to find this post and get things right. I wonder why the storage device  manager was not included **by default**, since there seems to be no other way to add new partitions to be mounted at boot?

---

### Post by Eric Qel-Droma on 2008-12-13
Questions:

1) What is the benefit of mounting ntfs as ntfs-3g?  Using umask=000, I can read/write documents (apparently) and delete them.  What else is there?

2) Why is that now my documents "cannot be moved to the trash"?  Any ideas?

3) I'm also a little curious why  storage device manager isn't default, but I don't think I used it in 8.04, I know I didn't manually edit fstab by hand, and yet I still had these drives mounting automatically.  I wish I could remember how I did it.

Anyway, thanks for the umask=000 tip.  Incidentally, what does "umask" mean, and why must it be set to "000"?

Thanks again.

---

### Post by drs305 on 2008-12-13
ntfs and ntfs-3g are now interchangeable in fstab, at least in intrepid and later.

You can check in gconf-editor, /apps/nautilus/preferences and select the media_automount option. Start gconf-editor with the terminal command "gconf-editor" or you can run the following to enable automounting:
```

gconftool-2 --type bool --set /apps/nautilus/preferences/media_automount 'true'

```

Storage Device Manager is simply an app that someone wrote. It is actually a bit old and although it still can do the job it probably could use an update. Here is a tutorial on how to use it. For those that aren't familiar with it, Storage Device Manager is a gui-based app that will create fstab entries for mounting devices.
[GUI Fstab Editing with PySDM]("http://ubuntuforums.org/showthread.php?t=872197")

---

### Post by BGFG on 2008-12-16
Sorry I'm back so late. My monitor power chord gave out and i had exams. Anyone tried other utilities in add remove ?

---

### Post by BGFG on 2008-12-23
Bump :)

---

### Post by John Wiersba on 2009-01-30
Maybe you're looking for the Configuration Editor for the GConf configuration system?
Try gconf-editor from the command line or use applications -> system tools -> configuration editor.  Then go to apps -> nautilus -> preferences -> media_automount.  You may need to Add/Remove the Configuration Editor application first and/or use the Main Menu appliction (system -> preferences -> main menu) to enable it.

---

### Post by koala15 on 2011-02-13
Worked - Thank you for your efforts, appreciated. :D

---

