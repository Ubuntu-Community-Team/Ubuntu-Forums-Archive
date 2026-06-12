---
title: "File watcher to create symlinks to files"
date: 2009-11-28
forum: Programming Talk
---

### Post by talz13 on 2009-11-28
I have a whole lot of things that get downloaded, and need to keep track of what I have viewed and what I have not.  Currently, I use vuze's statusmailer plugin to send a completion notification to my gmail account which gets starred and labeled 'torrents'.  After watching the show, I un-star and mark as read in gmail.

I was thinking that it would be nice to have an "unwatched" folder that would simply contain symlinks to the files so that, after finishing, I could just delete the symlink through windows media center.  I have tested this already by making a copy of a video, and a symlink to that copy.  When I told media center to delete the file that I labeled as a symlink, it removed the symlink and left the original file untouched.

I believe that I would need some kind of file watcher to run and create the symlinks that I want.  It could run on a schedule (like every 15 minutes or something), recursively scan my videos folder, and create symlinks to any new files created since the last scan.

How can I do this?

---

### Post by stylishpants on 2009-11-28
Something like this:

```
inotifywait -qme CREATE --format '%w%f' /tmp/watch | while read f; do ln -s "$f" /tmp/other/; done
```

This watches the directory /tmp/watch, and copies all newly created files into /tmp/other.

Using quotes around the filename means it should handle filenames with spaces properly.

Note that if you don't use an absolute path for the watched directory, you'll have to do some additional fiddling in the while loop to specify the proper file targets to "ln -s".

If the link to be created already exists, you should get a warning on STDERR but the command won't terminate.

This uses inotify instead of polling.  "inotify" is a linux kernel subsystem that provides notification of filesystem events.

---

### Post by slavik on 2009-11-29
you can also scan for files that have old access times (provided you did not turn off atime).
```

find /some/dir -atime +7

```
the above will tell you what files haven't been accessed in the past 7 days.

---

### Post by talz13 on 2009-12-01
> **stylishpants said:**
> Something like this:

```
inotifywait -qme CREATE --format '%w%f' /tmp/watch | while read f; do ln -s "$f" /tmp/other/; done
```

This watches the directory /tmp/watch, and copies all newly created files into /tmp/other.

Using quotes around the filename means it should handle filenames with spaces properly.

Note that if you don't use an absolute path for the watched directory, you'll have to do some additional fiddling in the while loop to specify the proper file targets to "ln -s".

If the link to be created already exists, you should get a warning on STDERR but the command won't terminate.

This uses inotify instead of polling.  "inotify" is a linux kernel subsystem that provides notification of filesystem events.

I went with this path, and it seems like it will work very well.  I ran into a little problem, however...  I put this in to run at boot time (S99fileWatcher on runlevels 2,3 and 5), but it looks like it's running... and not letting go!  My VM and webmin do not start when I reboot now, and I have traced it down to running this as a startup script before them.  I just have it start backgrounded by putting the & afterwards so that the system can move on with the rest of the startup scripts:

Courtesy of webmin:```
#!/bin/sh
# Watch for created files in /home/shares/video and link them to /home/shares/video/unwatched

case "$1" in
'start')
	inotifywait -qmre CREATE --format '%w%f' /home/shares/video | while read f; do ln -s "$f" /home/shares/video/unwatched; done &
	;;
'stop')
	;;
*)
	echo "Usage: $0 { start | stop }"
	;;
esac
exit 0
```Now my VM and webmin appear to be starting up correctly, and my file watcher is listening in the background as it should be.

Also, my fear of it fork bombing or something on trying to create the link underneath the folder that it is watching (creating link inside /home/shares/video/unwatched from files created under /home/shares/video/) was unfounded.  Sure, it throws the warning that it can't create the link the second time because it already exists, but then it stops trying to link that file a second time, moves on, and everything is right with the world.

---

### Post by talz13 on 2009-12-28
Ok, I have an update to this request.  I have a habit of using my 'video' share as a convenient dumping ground for little files (.reg files, .txt files, etc.) and would like to be able to ignore these without making links in my 'unwatched' folder.

The two options that I have come up with so far are:
1. Ignore everything that's not in a list of approved filetypes (i.e. .mkv, .mp4, .avi, etc.)
2. Ignore files that are below a certain size (not ideal, as I COULD have a large non-video file)

But I'm not sure how to implement either function.  My startup script is the same as what is in my last post above.


edit: I forgot I made a minor change to the command, it makes hard links instead of symlinks, since my wdtv live couldn't read the symlinks:

inotifywait -qmre CREATE --format '%w%f' /home/shares/video | while read f; do ln "$f" /home/shares/video/unwatched; done &

---

### Post by talz13 on 2010-01-08
Another small problem... I started doing some downloads with sabnzbd, downloading to a temporary folder in my home directory before having the files moved (or extracted) to my video share folder upon completion.  It appears that inotifywait is missing these files.  I have updated my inotifywait command as follows:

```
inotifywait -qmre CREATE,MOVED_TO --format '%w%f' /home/shares/video | while read f; do ln "$f" /home/shares/video/unwatched; done &
```

It appears to mainly be working only on files that are created under the folder /home/shares/video/ and is having trouble with anything that is created outside of this folder and then automatically moved or extracted there.

---

### Post by talz13 on 2010-01-14
Ok, another update.  I decided that I would try to move all the linking logic to a python script.  This is presenting some issues... Here are my inotifywait command and python script:

```
inotifywait -qmre CREATE,MOVED_TO --format '%w%f' /home/jeff/test | while read f; do python /home/jeff/scripts/filelink.py "$f" /home/jeff/testlinked; done &
```

```
import sys
import os
import subprocess
print sys.argv

file = sys.argv[1]
dir = sys.argv[2]

extensions = ['.3g2','.3gp','.asf','.avi','.divx','.evo','.f4v','.flv','.ifo','.iso','.m2ts','.mcf','.mka','.mkv','.mov','.mp4','.mpeg','.mpg','.nut','.ogg','.ps','.qt','.rmvb','.ts','.vob','.wma','.wmv']

fileExtension = os.path.splitext(file)[1]

print fileExtension

if fileExtension.lower() in extensions:
    print 'COMMAND TO RUN: ln "' + file + '" ' + dir
    subprocess.call('ln "' + file + '" ' + dir)


```

I ran the inotify command as my logged in user, and then copied a file into the watched directory (~/test), with the directory (~/testlinked) given as the folder to perform the link on.

I'm getting the following output:```
jeff@server:~$ cp /home/shares/video/anime/bleach/\[DB\]_Bleach_250_\[B568DD26\].avi test/
['/home/jeff/scripts/filelink.py', '/home/jeff/test/[DB]_Bleach_250_[B568DD26].avi', '/home/jeff/testlinked']
.avi
COMMAND TO RUN: ln "/home/jeff/test/[DB]_Bleach_250_[B568DD26].avi" /home/jeff/testlinked
Traceback (most recent call last):
  File "/home/jeff/scripts/filelink.py", line 17, in <module>
    subprocess.call('ln "' + file + '" ' + dir)
  File "/usr/lib/python2.6/subprocess.py", line 444, in call
    return Popen(*popenargs, **kwargs).wait()
  File "/usr/lib/python2.6/subprocess.py", line 595, in __init__
    errread, errwrite)
  File "/usr/lib/python2.6/subprocess.py", line 1092, in _execute_child
    raise child_exception
OSError: [Errno 2] No such file or directory
jeff@server:~$
```

Could it be trying to link the file before completing the copy?  Does that even matter if it's only creating a pointer to the file node?

---

