---
title: "Using fileschanged - Executes too early"
date: 2008-06-26
forum: Programming Talk
---

### Post by editorreilly on 2008-06-26
I'm running multi platforms in a LAN where I want to drop a LARGE file from machine-A(MACOSX) onto machine-B (UBUNTU 7.10) via samba.  I'm using fileschanged:

```
fileschanged --exec=*myshellscript* ~/Desktop/mydirectory/
```

to monitor a change in *mydirectory* to execute a shell script I wrote to automate a video conversion of a LARGE file via mencoder.  
```
#!/bin/bash
encode="/usr/bin/mencoder -of lavf -oac mp3lame -lameopts abr:br=56 -ovc lavc -lavcopts vcodec=flv:vbitrate=800000:mbd=2:mv0:trell:v4mv:cbp:last_pred=3 -srate 22050 -lavfopts i_certify_that_my_video_stream_does_not_use_b_frames -sub /home/cm01/Desktop/scripts/subtitles.srt"
find ~/Desktop/mydirectory/ -name '*.mov' | while read file; do
  dest="$(basename "$file" .mov).flv"
  $encode -o ~/Desktop/anotherdirectory/"$dest" "$file"
done
wait
bash ftper
exit 0
```
Which in turn executes ftper:

```
#!/bin/sh
HOST='*ftpserver*'
USER='*myusername*'
PASSWD='*mypassword*'
ftp -n $HOST <<END_SCRIPT
quote USER $USER
quote PASS $PASSWD
cd /somedirectory/
lcd ~/Desktop/anotherdirectory/
put *.flv
quit
END_SCRIPT
exit 0
```
Which in turn uploads the file to a remote server.  

The problem I'm having is that fileschanged executes *myshellscript* on the LARGE file before it can finish copying from machine-A to machine-B.  Sometimes there is no problem, but other times it wreaks havoc on the whole process.  

What I want to know is how to stop the process from starting until the entire file has finished copying to machine-B. Any ideas?

---

### Post by geirha on 2008-06-26
First thing that comes to mind is to copy the file to a neighboring folder, and when it's successfully copied, move it to the folder you're watching for changes. If the two folders are on the same filesystem, the move operation should be instant.

---

### Post by editorreilly on 2008-06-26
I'm trying to automate the process from machine-A, because I've got "creative" type people doing these drops. 

I've created a shortcut for the drop, and I want them to just be able to drop the LARGE file onto it.  

The less they have to do, the better.  If there is a way to screw it up, the users will find a way.

---

### Post by geirha on 2008-06-26
I see. You might try lsof. It will return true if some process has the file open, and return false if no processes currently has the file open

```

count=0
while lsof "$file"; do 
  sleep 10; 
  [ $((count++)) -gt 60 ] && break 
done
# assume $file is finished copying
```

Another way might be to use stat to check the modification date. If it hasn't been modified for a minute for example, assume it is finished.

---

### Post by editorreilly on 2008-07-01
It works perfectly when a app. like mplayer has it open, but it only loops once when its copying, so it still catches it in the middle of a copy.

---

