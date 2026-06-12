---
title: "LiveCDCustomization"
date: 2011-10-22
forum: New to Ubuntu
---

### Post by DaimyoKirby on 2011-10-22
Ok, so I've very quickly run into some problems, sadly enough.

Following [these instructions]("https://help.ubuntu.com/community/LiveCDCustomization"), I entered:
```
alden@LinuxZombie:~/livecdtmp$ rsync --exlcude=/casper/filesystem.squashfs -a mnt/ extract-cd

```

And terminal returned this error:
```
rsync: --exlcude=/casper/filesystem.squashfs: unknown option
rsync error: syntax or usage error (code 1) at main.c(1453) [client=3.0.8]

```

Can anyone tell me what's going wrong?

---

### Post by haqking on 2011-10-22
> **DaimyoKirby said:**
> Ok, so I've very quickly run into some problems, sadly enough.

Following [these instructions]("https://help.ubuntu.com/community/LiveCDCustomization"), I entered:
```
alden@LinuxZombie:~/livecdtmp$ rsync --exlcude=/casper/filesystem.squashfs -a mnt/ extract-cd

```

And terminal returned this error:
```
rsync: --ex**lc**ude=/casper/filesystem.squashfs: unknown option
rsync error: syntax or usage error (code 1) at main.c(1453) [client=3.0.8]

```

Can anyone tell me what's going wrong?

you have a spelling mistake, exclude is cl not lc

---

### Post by DaimyoKirby on 2011-10-22
Thanks, I often fail to see these things.

I'm going to keep this thread open so I can post any other questions I have about these same instructions.

P.S. Long time no see;)

---

### Post by DaimyoKirby on 2011-10-22
Ok, question #2.

I reached these instructions:
>  Generally background files are located in **/usr/share/backgrounds**. Copy your png file there, adjust owner and file access,  and edit the files: 

[LIST=1]
[*]**/usr/share/gnome-background-properties/ubuntu-wallpapers.xml** and 
[*]**/usr/share/gconf/defaults/16_ubuntu-wallpapers** or other files in the same directory.  by changing the string **/usr/share/backgrounds/warty-final-ubuntu.png** to point to your file 
[/LIST]
Eventually change or add attributes to  other configuration files such as: **/var/lib/gconf/debian.defaults/%gconf-tree.xml** or **/etc/gconf/gconf.xml.defaults/%gconf-tree.xml**). 
Historical: [More for Dapper...]("http://ubuntuforums.org/showthread.php?t=462810&highlight=warty-final-ubuntu.png") 
 
**Change gconf values (fonts, panels etc.)**

 To make any change on the gconf attributes you must add the value that you want in the file **/etc/gconf/gconf.xml.defaults/%gconf-tree.xml**.  Adding a value in that file will change the default values of Gnome or  other applications, so you can change fonts, backgrounds, themes,  cursors etc. 
Instead of editing the file with **gedit** or another text editor, you can use the **gconftool-2**, under the chroot environment, running the following line: 
gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.defaults --type string --set yourkey "yourvalue"where *string*, *yourkey* and *yourvalue* must be the type, key and value that you want to change... 
 


What does it mean? I'm running xubuntu, so I think my backgrounds are in a different place. Also, what does the gconf value thing mean?

---

