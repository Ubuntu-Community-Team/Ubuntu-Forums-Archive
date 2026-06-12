---
title: "How to check if a txt file uploaded to my web site with some script?"
date: 2020-06-05
forum: New to Ubuntu
---

### Post by chrisnk on 2020-06-05
Hi!
I wish to write a script which could check if a predefined txt file is uploaded to my web site in some directory.

Is that possible with some script?
Something like .cmd or .bat in win?

Thank you.

---

### Post by SeijiSensei on 2020-06-05
Is it possible to open this file via a URL, or is it in some directory not accessible via the web server?

If the first, you can write a simple script based on the command described here: 
[https://superuser.com/questions/619592/get-modification-time-of-remote-file-over-http-in-bash-script](https://superuser.com/questions/619592/get-modification-time-of-remote-file-over-http-in-bash-script)

This version returns the "Unix" date of the file, measured as the number of consecutive seconds since midnight on 1/1/1970.

```

$ date +%s --date="$(curl -s -v -X HEAD https://www.takinganimeseriously.com/images/1920-model-t.jpg 2>&1 | grep 'Last-Modified' | sed 's/^.*Last-Modified: //g')"
1587242851

```
This uses curl to get the file's Last-Modified date and expresses it in Unix time via the formatting code "+%s".  Here that date is 1587242851.

If you were to store this value each time the script is run, then compare the value returned here to the stored value, you'll know if the file has changed.

---

### Post by chrisnk on 2020-06-05
Thanks for the quick replay.
Yes, the file is possible to open via URL.

I would like to know does my file is present on the desired URL or not.

Lets say if the desired file is not present on the URL than a msgbox should pop-up and tell the user does the file is not present temporarily.. 

Or maybe is it possible to access to a mysql database and check if a data is present via script?

Sorry I'm new to Linux but I'm a power user and programmer in win...

---

### Post by ActionParsnip on 2020-06-06
You can use wget to download the one from the website and use diff or even md5sum to compare the two. If they are identical then you win

Something like:

```

#!/bin/bash
wget -O /tmp/webver.txt https://www.foo.com/file.txt
md5sum /tmp/webver.txt
md5sum $HOME/Documents/masterver.txt

``` 

If they are the same then you win. You could even awk the output of the md5sum commands and compare the 2 sums in the script to output a nice humanly readable line like "it's a match" etc or cron the script and send an email if it doesn't match.

---

### Post by TheFu on 2020-06-06
> **chrisnk said:**
>  
Sorry I'm new to Linux but I'm a power user and programmer in win...

How would you do it in Windows?  The same method would apply except if you have file system access to the server or ssh access, then it is pretty easy.  Bash scripting is very common, but you can use one of the 100+ other scripting languages, C, C++, Java or one of the 300 compiled languages.

In bash, 
```
if [ -f /some/path/to/file.txt ] ; then
   echo "File exists!"
fi
```

Of course, there are 500+ other ways. The basics come down to 
[LIST=1]
[*]Try to get a copy of the txt file, if that fails, most tools like **scp**, **wget**, **curl** will provide a non-zero return value.
[*]Check if the local copy of the file time stamp is new enough. Date/second math is easy in bash.  This will calculate a time difference in seconds between now and the time on a file :
```
DUR=$(($(date +%s) - $(date +%s -r "$filename" )))
```
[/LIST]

If you have ssh, you could setup an **sshfs** connection and have file system access to the file on the remote system.

Did I mention there are 500+ different ways?
Beginning bash scripting guide: [https://www.tldp.org/LDP/Bash-Beginners-Guide/html/Bash-Beginners-Guide.html](https://www.tldp.org/LDP/Bash-Beginners-Guide/html/Bash-Beginners-Guide.html)

There are intermediate and advanced guides.  Your system probably has 1,000 bash scripts on it already. Plenty of examples there.  Don't worry too much about the age for any bash scripting help/how-tos. Bash has been pretty much the same for 15 yrs.  Any 20+ yr old Unix Scripting or "Power Tools" book for $1 at a used bookstore is still valid.  It is only when you delve into the fuller languages like python, ruby, perl, where watching the specific version used matters.  sh, ksh, bash scripting really has been very well handled for a very long time.  

In the early 1990s, Bourne Shell (sh) is what we scripted using. Back then, all the Windows options were toys in comparison.  I remember talking with MSFT about a job in 2000 to join their PowerShell team to bring Unix scripting to Windows. PowerShell is the closest analogy to bash, ksh scripting, but it is much more verbose and uses keywords that nobody would want to type into a terminal.  Bash, OTOH, is terse, but clear. Commands that you'd type in a terminal/shell - you can put into a script and that will be 80% of what a script needs. The other 20% is error handling and making the script bulletproof using "best practices".  For a personal script, we can get away without that, but for a work in production, those extra validations and techniques are necessary.

Rather than having your workstation poll for the file existing, why not just have the server send it after it arrives? There's a tool - inotify - which can watch a directory for a file, then take any scripted action.  It is a little more to setup than having a polling script run every day or every 6 hrs or at 8am, noon, 4pm. That could easily be possible.

Having something graphical pop-up is a problem. Sending an email would be easier or having an RSS feed updated would be easier.  You already have things that let you know stuff, right?  Why not feed into those existing methods?  You could have the script post a tweet if that's how you roll ... or post on IRC or discord or ... 50 other services that you already have notifications about.

A bash script to send a tweet: [https://github.com/agubelu/bash-send-tweet](https://github.com/agubelu/bash-send-tweet)  There are some others if you need more.

---

