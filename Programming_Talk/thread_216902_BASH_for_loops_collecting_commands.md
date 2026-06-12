---
title: "BASH for loops collecting commands"
date: 2006-07-16
forum: Programming Talk
---

### Post by mikeym on 2006-07-16
Hi,

Sorry this is my second thread on this toppic but I posted the last one in the General thread and realised that it was in the wrong place, but I don't know how to move it.

I'm trying to write my first propper BASH script at the moment and I am stuck with a few things. 

**Firstly [COLOR="Red"](covered)[/COLOR]** 

I am trying to use a for loop to call a script once for each file in a directory, but when I run it it is calling the script once for all 3 files.

I want to run it like a script like this:

```

#!/bin/sh

nzbperl.pl "/mp3/dvd/nzb/TestR.nzb" 2>> /dev/null
echo "$?"
nzbperl.pl "/mp3/dvd/nzb/TestF.nzb" 2>> /dev/null
echo "$?"
nzbperl.pl "/mp3/dvd/nzb/TestO.nzb" 2>> /dev/null
echo "$?"
```

This results in the nzbperl.pl script being run 3 times.

But my code results in it being run once and passed a parameter for all 3 files.

```
for NZBFILE in "$(find /mp3/dvd/nzb -iname *.nzb -maxdepth 1 2> /dev/null)"; do
        echo "$NZBFILE"
        date +"%F %T Running 'nzbperl.pl'." >> /var/log/getnzbfiles.log
        nzbperl.pl "$NZBFILE" 2>> /dev/null
        echo "$?"
done
```

How can I force it to run nzbperl.pl 3 separate times?

[B]
Secondaly [COLOR="Red"](covered)[/COLOR][/B]

I am trying to ouput a command usage list but when I try to format it with tabs it ignores them or doesn't do the substitutions.

```
function PrintUseage {
        echo "Useage: \t $0 [options]"
        echo "Options:"
        echo "-cron \t Restrict graphical output for cron."
        echo "-shutdown \t Shutdown the computer on completion."
}
```

Creates the output;

```
Useage: \t /home/mikey/bin/getnzbfiles.sh [options]
Options:
-cron \t Restrict graphical output for cron.
-shutdown \t Shutdown the computer on completion.
```


**Thirdly [COLOR="Red"](Not possible)[/COLOR]**

I want to interperate the nzbperl.pl script's ouput to understand how it has exited. The a call to "echo $?" to get an error afer the script has exited abnormally still returns 0, so I think it doesn't use error return codes. The nzbperl.pl script uses a graphical interface so I don't think I can direct it to file without it getting too big, and the error output gives many readings in the same way.

Is there a way to capture the begning of the output just so I can get that before it starts trying to do graphics?

Here is an ouput where it encounters an error:

```
 Sorry, but nzb file is broken!  The xml could not be parsed:

 Couldn't open /mp3/dvd/nzb/TestR.nzb
/mp3/dvd/nzb/TestF.nzb
/mp3/dvd/nzb/TestO.nzb:
No such file or directory at /usr/local/bin/nzbperl.pl line 2126

 *** nzbperl requires valid, well-formed XML documents.

```

---

### Post by bscbrit on 2006-07-16
I think the following should do what you want, assuming all the files that you wish to process are in the current directory.  If they are not, it is fairly trivial to change.

for FILE in $(ls *.nzb) ; do
    nzbperl.pl $FILE &2>>/dev/nul
done

I'm just going to find my bash manual to check....

---

### Post by bscbrit on 2006-07-16
Sorry, I missed the 'echo' command out of the loop - but I'm sure that you get the general idea.

---

### Post by mikeym on 2006-07-16
Ohh Dear!

I had put quotes round the for statement it would have worked without them!

So first point covered - thanks.

---

### Post by kabus on 2006-07-17
Regarding your second problem: Try 'echo -e' instead of just 'echo'.

---

### Post by mikeym on 2006-07-17
Thank you that is exactly what was needed for my second question.

I have decided that the 3 part of my question is not possible the way I was thinking. There is an option to read the logs created by 'nzbperl' the problem however is that if there is a problem reading one of the 'nzb' files then the log is not touched, so I would have to test for this.

---

