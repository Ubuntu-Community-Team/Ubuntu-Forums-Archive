---
title: "batch photo management script /2"
date: 2014-07-28
forum: Programming Talk
---

### Post by mcapri76 on 2014-07-28
[http://ubuntuforums.org/showthread.php?t=2081272&p=12640154#post12640154](http://ubuntuforums.org/showthread.php?t=2081272&p=12640154#post12640154)

Vaphell et all were very helpful in creating the script above to automatically resize and rename my photo archive.

The script worked a treat for years but now everytime I run it I get this error message:

**sudo ./resize_pics.sh**
[I]stat: cannot stat `pics_2014-07-13.log': No such file or directory
latest log file: pics_2014-07-13.log ()
current log file: /media/data1tb/BACKUP/Photos_resized/logs/pics_2014-07-27.log

-----------------------------------
find: ‘pics_2014-07-13.log’: No such file or directory

[/I]I know what you are thinking, have you checked the log path? Well, I did over and over again and the .log file is in the location specified, I tried to run as admin to see if it was something to do with access rights. I tried to debug it myself but to no avail. The only thing I've noticed is that if I remove all .log files and start afresh the script works. But after the first run it will return the error message above.

I am running 12.04 (Mythbuntu).

Thanks

---

### Post by Vaphell on 2014-07-28
:/

is there a reason why you are running sudo with the script? It's all userspace stuff, in principle there is no need to invoke superpowers for that.

---

### Post by mcapri76 on 2014-07-28
Either with our without sudo the result is exactly the same. I tried to sudo it in the hope that it was something to do with folder permission/file creation - I was clearly wrong!

Thanks for the support Vaphell

---

### Post by Vaphell on 2014-07-28
what's your current config?
I see you have some mounted partition there, so the first question would be is it actually mounted when running the script?

---

### Post by tgalati4 on 2014-07-28
Have you run out of disk space on that drive?  I would move all of the log files out of the log directory.  Start with a clean directory and then start the script.  A new log file should be created to get you going again.  I think if the script gets interrupted (for any reason) then you have a newer log file created than the last log file--and that trips up the script logic.  There should be logic to include a log file that is newer than the last log file found and ask what to do with it.  Perhaps delete it and start again, or rename it to orphanXX.log.

---

### Post by mcapri76 on 2014-07-28
[Vaphell] the mount is a second HDD (ext4) that mounts automatically at boot. The script is manually launched from the mount (so it is mounted) and when I look for the file that the system cannot find: *pics_2014-07-13.log *I find it where in the correct folder[I]/media/data1tb/BACKUP/Photos_resized/logs/

[/I][tgalati4] In an attempt to fix the problem on 2014-07-13 I tried what you suggested. It worked and the script resized/renamed all the pictures. The error message in my first post is what I am getting since running the script the second time. Space is not a problem I've got hudreds of GBs available.

---

### Post by Vaphell on 2014-07-28
what do you get if you add these lines under the* read _ lastlog < <( ... )* line?
```
find "$log_dir" -iname '*.log' -printf "%T@\t%f\n" | sort -nr
[ -f "$lastlog" ] && echo "== $lastlog"
stat -c %y "$lastlog"
```

btw you can create a debug script with only the first part that ends with ---------------------
less noise to deal with.

---

### Post by tgalati4 on 2014-07-28
It sounds like the logic for detecting the latest log file is messed up.  What changes did you make to your system before and after this behavior?  Any updates?  After running the script, run *env* and look at the variables defined.  Make a list of each variable (from your script) and it's value before and after running the script.  I think there is an initialization problem.

```
env
```

You should not run your script with *sudo* because that will create a log directory with root permissions and then if you run it without *sudo*, you won't be able to write to it.
What are the permissions of the log directory?

```
ls -la /media/data1tb/BACKUP/Photos_resized/
```  Don't post the directory contents, just examine the permissions--the first, third and fourth column of the directory listing.

Also, the way the script is written, it must be run in the directory with the photos, not above or below, otherwise you will get multiple log directories or errors.

---

### Post by Vaphell on 2014-07-28
i think there is a confusion with directories, when i wrote the script i set log_dir to . so things might have been working by accident even if i didn't invoke that dir by mistake.

find $log_dir -print %f returns only filename, no path
that means stat $lastlog runs in the context of the current dir (./script) not the log dir

OP, try changing %f to %p and see if stat doesn't complain and returns something sane with full path and the timestamp in ()

---

### Post by mcapri76 on 2014-07-29
[tgalati4] in your second paragraph you hit the nail on the head! When I removed the logs and resized pictures I re-run the script using sudo. This is causing problem now that I'm trying to run the script using my user.

[Vaphell] I changed the %f to %p as suggested and following up on what above if I run the script using sudo it works:

mcapri@ubuntu:/media/data1tb/BACKUP/Photos_resized$ sudo ./resize_pics.sh
latest log file: /media/data1tb/BACKUP/Photos_resized/logs/pics_2014-07-13.log (2014-07-13 12:26:58.258049995 +0100)
current log file: /media/data1tb/BACKUP/Photos_resized/logs/pics_2014-07-29.log
-----------------------------------
9 new files found in '/media/data1tb/BACKUP/Photos/My_Baby_Girl_2012/2yr_3yr'!
*** file: /media/data1tb/BACKUP/Photos/My_Baby_Girl_2012/2yr_3yr/2yr_3yr_0000000001.jpg
resized: /media/data1tb/BACKUP/Photos_resized/2014/My_Baby_Girl_2012/2yr_3yr/2yr_3yr_0000000001.jpg

 This small change is causing an issue with the renaming part of the script. The format used to be <folder name>_<ascending three digits>.jpg (eg: holidays_001.jpg) for some reason now the newly created files are renamed with a 10 digits suffix: holidays_0000000001.jpg

---

### Post by Vaphell on 2014-07-29
I am unable to reproduce that. What is the value of w?
for w=4 i get this:
```

1 new file found in './src/Photos/My_Baby_Girl_2012/2yr_3yr'!
*** file: ./src/Photos/My_Baby_Girl_2012/2yr_3yr/2yr_3yr_0000000001.jpg
`./src/Photos/My_Baby_Girl_2012/2yr_3yr/2yr_3yr_0000000001.jpg' -> `./src/Photos/My_Baby_Girl_2012/2yr_3yr/2yr_3yr_0001.jpg'
resized: ./dest/2014/Photos/My_Baby_Girl_2012/2yr_3yr/2yr_3yr_0001.jpg
```



btw change the *fnew=...* line to this:
```
fnew="$fdir/${album}_$( printf [COLOR="#0000FF"]'%0*d' $w[/COLOR] $i ).jpg"
```
since writing the original script i learned about %*****d

---

### Post by ofnuts on 2014-07-30
It is still not normal to have to use sudo to run these scripts. You need to figure out what you haven't got the rights to do it as a regular user. What is worse is that all this means you are running scripts that are barely working with root privileges. A small typo and your system can be wiped out. You have been warned. And no, don't think you will fix that "later".

---

### Post by mcapri76 on 2014-07-30
I spotted the problem, in my attempt to troubleshoot I changed the value of w. Without realising what it was used for :( Now I know ;)

[ofnuts] It was the plan to find the fix (with the help of the forum) and re-run the script from scratch without root privileges.

The script is running flawlessly right now. Thanks for the support guys.

---

