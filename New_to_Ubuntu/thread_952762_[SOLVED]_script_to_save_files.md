---
title: "[SOLVED] script to save files"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by DoubleMcLovin on 2008-10-19
I wanted to make a script that when run would copy the contents of the folder "Master" into another folder with the date of the day the script was run, and copy that folder to several locations.

The idea is that I have some sensitive files that I edit frequently, I take great care to make sure that I have about 6 copies (on different media) at all times incase one of the files should be corrupted. I have been doing this process by hand for some time, but just recently switched to linux under the impressions that anything is possible and surely such a simple task can be done =D

---

### Post by snova on 2008-10-19
So basically you want a backup of these files? That should be easy enough. Just use the cp (copy) command.

```

#!/bin/bash
LOCATION="/place/to/put/copy/`date`"
mkdir "$LOCATION"
cp /location/of/Master "$LOCATION"
cp "$LOCATION" /second/copy
cp "$LOCATION" /third/copy

```

External media will have to be mounted before this will work, but that's easy enough.

(Yay! My 200th post!)

---

### Post by The Cog on 2008-10-19
You may want to look at subversion. It is a version control system, and you can have it keep copies and record all previous versions of files. It is used for tracking changes in software, where being able to recall all previous versions is kind of handy.

---

### Post by DoubleMcLovin on 2008-10-19
Thank you both, I will try both methods as I would like to get some experience with scripts. 1 more noob question, how do I make a script?? :confused:

---

### Post by BDNiner on 2008-10-19
Copy the contents of Snova's script into a blank text document and name it whatever you want just make sure that the extension is '.sh' eg "copyscript.sh". Then make the file executable
```

chmod a+x copyscript.sh

```

and then you can type ./copyscript.sh to run it.

---

### Post by DoubleMcLovin on 2008-10-19
Ok, I made the script file, and I made it executable. I managed to get it to copy within my home folder just fine, but over a removable media and a network it doesn't create the directory I think.
```
#!/bin/bash
LOCATION="/home/andy/Documents/work/`date`"
LOCATION2="/media/disk/Work/2008/`date`"
LOCATION3="smb://wndws-lptp/wndws-lptp/system/backup/`date`"
mkdir "$LOCATION"
mkdir "$LOCATION2"
mkdir "$LOCATION3"
cp /home/andy/Documents/work/master/*.* "$LOCATION"
cp /home/andy/Documents/work/master/*.* "$LOCATION2"
cp /home/andy/Documents/work/master/*.* "$LOCATION3"
```

Thats my code right now, and like I said "$LOCATION" works fine, but $LOCATION2 and $LOCATION3 both fail.

Here is my error in the terminal 

```
andy@andy-desktop:~/Documents/work$ ./backup.sh
mkdir: cannot create directory `/media/disk/Work/2008/Sun Oct 19 17:14:35 MST 2008': Invalid argument
mkdir: cannot create directory `smb://wndws-lptp/wndws-lptp/system/backup/Sun Oct 19 17:14:35 MST 2008': No such file or directory
cp: target `/media/disk/Work/2008/Sun Oct 19 17:14:35 MST 2008' is not a directory
cp: target `smb://wndws-lptp/wndws-lptp/system/backup/Sun Oct 19 17:14:35 MST 2008' is not a directory

```

I went to those paths and was able to create folders and files, so its not a permission thing. Something wrong with code?

---

### Post by unutbu on 2008-10-19
Try changing date to date +%F. This will create a date like "2008-10-19".

Also change mkdir to mkdir -p. This will create parent directories as needed.

```
#!/bin/bash
LOCATION="/home/andy/Documents/work/`date +%F`"
LOCATION2="/media/disk/Work/2008/`date +%F`"
LOCATION3="smb://wndws-lptp/wndws-lptp/system/backup/`date +%F`"
mkdir -p "$LOCATION"
mkdir -p "$LOCATION2"
mkdir -p "$LOCATION3"
cp /home/andy/Documents/work/master/*.* "$LOCATION"
cp /home/andy/Documents/work/master/*.* "$LOCATION2"
cp /home/andy/Documents/work/master/*.* "$LOCATION3"
```

---

### Post by DoubleMcLovin on 2008-10-19
ok, that fixed $LOCATION2 however each time I execute the script instead of copying over the network to the smb: location, it simply creates a folder smb: and the subdirs in the directory im in when executing the script. I have 2 more computers I wanted to add to this over a network like that, any way we can get this to have network functionality?

---

### Post by unutbu on 2008-10-19
Sorry, I don't know much about samba.

Perhaps try this:
Use this guide, [https://wiki.ubuntu.com/ComprehensiveSambaGuide](https://wiki.ubuntu.com/ComprehensiveSambaGuide),
to mount the samba share at /media/winshares.

Then edit the backup script 
```

LOCATION3="/media/winshares/`date +%F`"
```

---

### Post by snova on 2008-10-20
I don't know much about Samba either, but it's not working because the cp command doesn't handle URLs.

If Samba shares can be mounted as normal filesystems (it looks like it), then add a command to perform that mount prior to the command that copies the file to that point. (Then add an unmount command afterwards.)

Otherwise, use whatever commands you would normally use to copy files over Samba.

As to version control systems, that might be a better solution. Rather than having many subdirectories with dated names, a VCS would store history automatically. All of them that I know of can work over a network, but I don't know if they work over Samba...

I like Bazaar personally. It has a command to keep branches in sync ("push -- update a mirror of this branch") which is probably about what you need. Bazaar works over FTP and HTTP, and it also has a built in "smart server" with a custom protocol.

In theory you can just run the server on each network share and then use "bzr push bzr://location" (or something similar) several times. It would take a bit of work to set things up, but no more than Samba. You'd also have to find out the specifics of how it's done, as I'm not sure.

---

