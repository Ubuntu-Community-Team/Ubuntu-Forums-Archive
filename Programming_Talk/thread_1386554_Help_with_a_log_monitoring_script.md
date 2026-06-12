---
title: "Help with a log monitoring script"
date: 2010-01-20
forum: Programming Talk
---

### Post by tworkemon on 2010-01-20
Hello. I am in need of some help with a script I am trying to write. The goal is to monitor/watch/tail a log file and when it finds a specific regex/match look for another regex/match then execute a command.

Log file example:
```
2010-01-20 22:54:51 [7164][User1][1.2.3.4]Start download file '/test.log'
2010-01-20 22:54:51 [5482][User2][2.3.4.5]Start download file '/test1.log'
2010-01-20 22:54:51 [7164][User1][1.2.3.4]End download file '/test.log' : 100%
```

So basically it will monitor that log file and wait until "Start" and somehow recognize that it is from User1 then when "End" from user1 occurs it will move the file from /test.log to another directory.

I know how to parse out the Start part but not sure how to continue after that. How to check for the user and then continue to monitor it until End is reached for that user. Ideally should be running all the time and work for multiple users at once.

Any help would be appreciated !!

---

### Post by Axos on 2010-01-20
Would it suffice to just look for the end and then move the file? Is there some other reason why you need to know when the download starts?

---

### Post by d3v1150m471c on 2010-01-20
```
[COLOR=#808080]*#!/bin/bash*[/COLOR]
# name this file dsnatch and save it in your home folder
# in the terminal type "chmod +x dsnatch"
# you can then run this script by typing "./dsnatch" in your terminal
# before you do alter the pathnames on this script
[COLOR=#007800]test.log=[/COLOR]$[COLOR=#000000]1
[/COLOR] 
[COLOR=#000000]**if**[/COLOR] [COLOR=#7a0874]**[**[/COLOR] -e [COLOR=#007800]$test.log[/COLOR] [COLOR=#7a0874]**]**[/COLOR];
[COLOR=#000000]**then**[/COLOR]
   mv /path/to/test.log /new/path/to/test.log
[COLOR=#000000]**else**[/COLOR]
   [COLOR=#7a0874]**echo**[/COLOR] [COLOR=#ff0000]"File $test.log does not exist"[/COLOR]
[COLOR=#000000]**fi**[/COLOR]
 
```

Copy and paste this and follow the above directions instructed adjacent to the # characters. Hope that helps

---

### Post by tworkemon on 2010-01-20
> **Axos said:**
> Would it suffice to just look for the end and then move the file? Is there some other reason why you need to know when the download starts?
Ideally it would then send an email with the start/end lines and saying that the file was moved. But I guess you are right for now I could just look at the end lines and do it that way. The start/email part would be a bonus.

---

### Post by d3v1150m471c on 2010-01-20
there's probably a command for that but i don't know it. you'd also have to factor in your mail client, firewalls, yada yada

---

### Post by falconindy on 2010-01-20
Might want to consider a different approach. Piping the output of inotifywait into a 'while read' loop and using lsof to determine when the file is "free" might be a better way to accomplish this. Something like...

```
#!/bin/bash

WATCHDIR=/dir/to/watch
inotifywait -qm -e CREATE --format %f "$WATCHDIR" | while read file; do
  while [[ $(lsof "$WATCHDIR/$file" ]]; do sleep 5; done
  mv "$WATCHDIR/$file" "/new/location/for/file"
  # echo some output here or send a mail, etc
done
```
The above is untested, but I've written things like this before -- it's what inotify was meant for.

---

### Post by tworkemon on 2010-01-21
> **falconindy said:**
> Might want to consider a different approach. Piping the output of inotifywait into a 'while read' loop and using lsof to determine when the file is "free" might be a better way to accomplish this. Something like...

```
#!/bin/bash

WATCHDIR=/dir/to/watch
inotifywait -qm -e CREATE --format %f "$WATCHDIR" | while read file; do
  while [[ $(lsof "$WATCHDIR/$file" ]]; do sleep 5; done
  mv "$WATCHDIR/$file" "/new/location/for/file"
  # echo some output here or send a mail, etc
done
```
The above is untested, but I've written things like this before -- it's what inotify was meant for.

Completely different approach and a pretty good one. I will have to read up a bit on inotifywait. Thanks for this suggestion.

---

### Post by tworkemon on 2010-01-21
> **tworkemon said:**
> Completely different approach and a pretty good one. I will have to read up a bit on inotifywait. Thanks for this suggestion.

The issue with this is when someone uses "ls" within sftp it will catch that event. Is there a way to ignore the ISDIR event ?

WATCHDIR=/test
inotifywait -qm -e MODIFY -e CLOSE_NOWRITE -e CLOSE "$WATCHDIR"


"LS is done in directory"
/test OPEN,ISDIR 
/test CLOSE_NOWRITE,CLOSE,ISDIR 

"GET is done in directory"
/test OPEN test.txt
/test ACCESS test.txt
/test ACCESS test.txt
/test ACCESS test.txt
/test ACCESS test.txt
/test CLOSE_NOWRITE,CLOSE test.txt

---

### Post by tworkemon on 2010-01-21
Getting really close now.

```

WATCHDIR=/test
inotifywait -qm -e CLOSE_NOWRITE "$WATCHDIR" --format %f |while read file; do
#inotifywait -qm -e CLOSE_NOWRITE "$WATCHDIR"
if [ -n "$file" ]; then
#  while [[ $(lsof "$WATCHDIR$file") ]]; do sleep 5; done
#	mv $WATCHDIR$file /tmp/
        echo $file
fi
done

```
The problem I am having now if when I enable the mv line I get the following error
```
mv: cannot stat `/test/test.txt': No such file or directory
```
It does move the file but inotifywait is picking up the move command as well I am assuming. So how do I get inotifywait to ignore the move within the script yet still monitor the directory?

To add a bit more complexity is it possible to monitor multiple directories at once?

---

