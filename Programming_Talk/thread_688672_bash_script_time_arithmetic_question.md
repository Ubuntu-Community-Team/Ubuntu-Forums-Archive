---
title: "bash script time arithmetic question"
date: 2008-02-05
forum: Programming Talk
---

### Post by v4169sgr on 2008-02-05
My shell scripting isn't very good, so I'd really appreciate a pointer. Save me time in the office! ;)

```

date | awk '{ print $4 }'
```

on the Solaris system at work will return me the time in HH:MM:SS format. Fro various reasons that I will not go into here :) I need to find the time 10 seconds ago and hold that in a local variable.

I know I can find the answer, but not without a LOT of digging. OTOH any passing guru will be able to save time for me and others in a few seconds!

Thanks for any help! :guitar:

---

### Post by v4169sgr on 2008-02-05
Just verified the code is the same on my Ubuntu Dapper system. Also, I need the output in the SAME FORMAT so unfortunately a Julian Date thing, while very nice, will not do unless there is a reverse conversion the other way.

---

### Post by stroyan on 2008-02-05
The date command takes an optional format string.
```
date +%H:%M:%S
```
That makes it easy to get a HH:MM:SS format.
The part about subtracting ten seconds is complicated by all of the wraparound effects at the start of a minute, hour, and day.
```

D=$(date +%H:%M:%S)
IFS=: read H M S <<< "$D"
((H=10#$H))
((M=10#$M))
((S=10#$S))
if [[ $S -gt 9 ]]
then
  (( S=$S-10 ))
else
  (( S=$S+50 ))
  if [[ $M -gt 0 ]]
  then
    (( M=$M-1 ))
  else
    M=59
    if [[ $H -gt 0 ]]
    then
      (( H=$H-1 ))
    else
      H=23
    fi
  fi
fi
D=$(printf "%02d:%02d:%02d" $H $M $S)
echo $D
```

---

### Post by Ramses de Norre on 2008-02-05
Something like this maybe:
```

_DATE=$(date +%h:%M:%S)
_HOUR=$(date +%H)
_MIN=$(date +%M)
_SEC=$(date +%S)

if [ ${_SEC} -ge 10 ]; then
    _SEC=$((_SEC-10))
else
    if [ ${_MIN} -ne 0 ]; then
        _MIN=$((_MIN-1))
        _SEC=$((60+(_SEC-10)))
    else
        if [ ${_HOUR} -ne 0 ]; then
            _HOUR=$((_HOUR-1))
        else
            _HOUR=23
        fi
        _MIN=59
        _SEC=$((60+(_SEC-10)))
    fi
fi

echo ${_DATE}" gives "${_HOUR}":"${_MIN}":"${_SEC}
```

I wrote it in five minutes so make sure for yourself that it is correct. But it should give you the basic idea and syntax to do so.

Edit: it seems to work:
```
$ bash dateminusten.sh 
23:55:03 gives 23:54:53
$ bash dateminusten.sh 
23:57:31 gives 23:57:21
```

---

### Post by geirha on 2008-02-05
Is the [companion CD](http://www.sun.com/software/solaris/freeware/) installed? If so you can use gdate, which is GNU's date. If it's installed, you'll most likely find it at /opt/sfw/bin/gdate or possibly /usr/sfw/bin/gdate.

Then all you need to do to get the current time minus 10 seconds, is: ```
gdate -d "-10 seconds" "+%H:%M:%S"
```

---

### Post by tukuyomi on 2008-02-05
Another way to give the same result :)```
#!/bin/bash

# Thanks to stroyan for this function :D
D=$(date +%H:%M:%S)
IFS=: read H M S <<< "$D"
# Edit according to Post #10
((H=10#$H))
((M=10#$M))
((S=10#$S))

SEC=$(($S+$M*60+$H*3600-10))

H=$(($SEC/3600))
M=$(((($SEC-$H*3600))/60))
S=$(($SEC-$H*3600-$M*60))
 
echo $(printf "%02d:%02d:%02d" $H $M $S)

```

---

### Post by tukuyomi on 2008-02-05
geirha is right! even date has this feature!
```
date -d "-10 seconds" "+%H:%M:%S"
```

---

### Post by geirha on 2008-02-05
> **tukuyomi said:**
> geirha is right! even date has this feature!
```
date -d "-10 seconds" "+%H:%M:%S"
```

Not the date-command that ships with solaris though, but the GNU version has that feature.

---

### Post by tukuyomi on 2008-02-05
> **geirha said:**
> Not the date-command that ships with solaris though, but the GNU version has that feature.
Oups, my bad... :oops:

---

### Post by stroyan on 2008-02-05
I should comment on these lines from my previous post.
Other replies dropped them.  But they are important.
```
((H=10#$H))
((M=10#$M))
((S=10#$S))
```
With the hours, minutes, and seconds formatted as two digit numbers there is trouble waiting.
Using a value of 08 or 09 as a number will produce an error of 'value too great for base'.
The leading zero causes the number to be treated as an octal base 8 encoding.
The extra step of assigning ((H=10#$H)) forces bash to consider a value such as 10#08 as base 10.

---

### Post by v4169sgr on 2008-02-06
> **tukuyomi said:**
> Another way to give the same result :)```
#!/bin/bash

# Thanks to stroyan for this function :D
D=$(date +%H:%M:%S)
IFS=: read H M S <<< "$D"
# Edit according to Post #10
((H=10#$H))
((M=10#$M))
((S=10#$S))

SEC=$(($S+$M*60+$H*3600-10))

H=$(($SEC/3600))
M=$(((($SEC-$H*3600))/60))
S=$(($SEC-$H*3600-$M*60))
 
echo $(printf "%02d:%02d:%02d" $H $M $S)

```

Thank you **ALL** for your replies, and thank you especially to stroyan and tukuyomi - I took up your solution - it worked straight away without adaption. Saved me quite a bit of time and enabled me to arrive at an overall solution much more quickly than would have been the case.

Just to give a flavour for what was involved, I was developing a simple sh / bash script for periodically tailing a large log file and printing out lines containing certain protocol statements, in a way that would give the illusion of a real time display i.e. no dupes or missing messages. I'm most of the way there, but not convinced yet; hopefully once the code is working it willbe returned to the community as I see people asking about this stuff but no working examples :)

Couple of quick points:

* date +%T delivers the same format as above i.e. HH:MM:SS;

* The solaris environment in question did not have the extra freebies installed. I'm sure the admins have more on their hands than a few more apps to assist with QA!

Thank you again :guitar:

---

### Post by v4169sgr on 2008-02-07
Here is the script in question. It is not the finest or most elegant of scripts, but it does the job, and used 'in anger' yesterday it did not slip up once. It is a little buggy still and can almost certainly be written better and tidied up.

The main purpose of this script is to print, in as near real time as possible, only messages written in the FIX Protocol [[www.fixprotocol.org](www.fixprotocol.org)] from a large and rapidly growing log containing a lot of other information.

I hope that it can be of some use to other people.


```
#!/bin/bash
#
session=$1

if [ -n "$session" ]
then
        break;
else
        echo "Usage: 'fixlog.sh <SESSIONID>'"
        exit 1;
fi

echo
echo "Tailing FIXServer.log for FIX messages on session $session"
echo

#linecount=0

while [ 1 ]
do

        datestring=$(date +%H:%M:%S)

#       Subtract 9 seconds from current time as computed by 'date', taking account of minutes and hours
#       Attributed to tukuyomi and stroyan on ubuntu forums

        IFS=: read H M S <<< "$datestring"
        ((H=10#$H))
        ((M=10#$M))
        ((S=10#$S))

        SEC=$(($S+$M*60+$H*3600-9))
        H=$(($SEC/3600))
        M=$(((($SEC-$H*3600))/60))
        S=$(($SEC-$H*3600-$M*60))

        timeminus=$(printf "%02d:%02d:%02d" $H $M $S)

        # Extracts only those FIX messages in the time space in consideration. v4169sgr.

        sleep 10

        cat -v /home/ffprd/log/fusion/FIXServer.log | tail -1000 | awk '$3>=from&&$3<=to' from=$timeminus to=$datestring | grep "$session" | grep "8=FIX" | sed -e "s/\^A/\|/g" | sed -e "s/FFS\: Comm\: Sending data\:/\>\>\>\>\>\>/" | sed -e "s/FFS\: Comm\: Received data\:/\<\<\<\<\<\</"

done 
```

---

### Post by ghostdog74 on 2008-02-07
> **v4169sgr said:**
> ...
        cat -v /home/ffprd/log/fusion/FIXServer.log | tail -1000 | awk '$3>=from&&$3<=to' from=$timeminus to=$datestring | grep "$session" | grep "8=FIX" | sed -e "s/\^A/\|/g" | sed -e "s/FFS\: Comm\: Sending data\:/\>\>\>\>\>\>/" | sed -e "s/FFS\: Comm\: Received data\:/\<\<\<\<\<\</"

done [/CODE]


too much chaining sometimes make your code slow and ugly. you can combine those sed and grep statements, using awk. also you can do away with the cat. just an example ....
```

tail -1000 /home/ffprd/log/fusion/FIXServer.log | awk from=$timeminus to=$datestring sess="$session" '
    $3>=from&&$3<=to {
       if ( $0 ~ sess && $0 ~ "8=FIX") {
         gsub( /\^A/ , "|")
         gsub( ... )
         gsub( ... )
       }
    }'

```

---

### Post by tukuyomi on 2008-02-08
the timeminus will be wrong every day at 12:00:00am until12:00:10am
You have to take in consideration the day, the month and the year... if it's written in the log or hack the code somehow...
Say it's 12:00:06am
```
H=0; M=0; S=6
SEC=$(($S+$M*60+$H*3600-9))
H=$(($SEC/3600))
M=$(((($SEC-$H*3600))/60))
S=$(($SEC-$H*3600-$M*60))
echo $(printf "%02d:%02d:%02d" $H $M $S)
```
doesn't returns 23:59:57 but 00:00:-03 ... odd
By the way, does anyone knows of a function/command that returns unix time?

---

### Post by Ramses de Norre on 2008-02-08
A more efficient version of that last line: > **v4169sgr said:**
> 
```
cat -v /home/ffprd/log/fusion/FIXServer.log |\
tail -1000 |\
awk '$3>=from&&$3<=to' from=$timeminus to=$datestring |\
grep "$session&8=FIX" |\
sed -e "s/\^A/\|/g" \
-e "s/FFS\: Comm\: Sending data\:/\>\>\>\>\>\>/" \
-e "s/FFS\: Comm\: Received data\:/\<\<\<\<\<\</"
 
```

This uses single sed and grep calls.

---

### Post by ghostdog74 on 2008-02-08
> **Ramses de Norre said:**
> A more efficient version of that last line: 

This uses single sed and grep calls.
there's still room for more efficiency.

---

### Post by v4169sgr on 2008-02-08
> **tukuyomi said:**
> the timeminus will be wrong every day at 12:00:00am until12:00:10am
You have to take in consideration the day, the month and the year... if it's written in the log or hack the code somehow...
Say it's 12:00:06am
```
H=0; M=0; S=6
SEC=$(($S+$M*60+$H*3600-9))
H=$(($SEC/3600))
M=$(((($SEC-$H*3600))/60))
S=$(($SEC-$H*3600-$M*60))
echo $(printf "%02d:%02d:%02d" $H $M $S)
```
doesn't returns 23:59:57 but 00:00:-03 ... odd
By the way, does anyone knows of a function/command that returns unix time?

Thanks, but this is not required for use in the script, unless you are burning midnight oil or something, in which case you can always re-start the script.

Unix time is returned by date +%s - hope that helps :)

---

### Post by v4169sgr on 2008-02-08
> **ghostdog74 said:**
> too much chaining sometimes make your code slow and ugly. you can combine those sed and grep statements, using awk. also you can do away with the cat. just an example ....
```

tail -1000 /home/ffprd/log/fusion/FIXServer.log | awk from=$timeminus to=$datestring sess="$session" '
    $3>=from&&$3<=to {
       if ( $0 ~ sess && $0 ~ "8=FIX") {
         gsub( /\^A/ , "|")
         gsub( ... )
         gsub( ... )
       }
    }'

```

Thanks for these suggestions.

The cat is needed because there are non-printing character delimiters in the protocol statements, and there does not appear any way to get them printed with tail, so I use 'cat -v'.

The awk statements do look interesting, and could provide an excuse to get more into control structures in awk [and axctually start learning some of this stuff! :)]. In particular I've been looking for ways in which to act on messages conditional on their message types.

---

### Post by ghostdog74 on 2008-02-08
> **v4169sgr said:**
> The cat is needed because there are non-printing character delimiters in the protocol statements, and there does not appear any way to get them printed with tail, so I use 'cat -v'.

sure, not a problem using cat.
In awk(sed), you can print non printing characters too, but then its left to you to explore if you are interested.
> 
The awk statements do look interesting, and could provide an excuse to get more into control structures in awk [and axctually start learning some of this stuff! :)]. In particular I've been looking for ways in which to act on messages conditional on their message types.
good.

---

### Post by tukuyomi on 2008-02-09
> **v4169sgr said:**
> Unix time is returned by date +%s - hope that helps :)
It was written in the date --help... *going to buy some eyes*
Thank you :)

---

### Post by v4169sgr on 2008-02-12
I've been busy attempting to put some of these suggestions into practice, and along the way learn a little awk; however I've come to a bit of an impasse and will appreciate your collective wisdom in seeing me past.

There's nothing here that is remotely original; all I am doing is trying to understand.

Here is the code:

      ```
 cat -v /home/ffprd/log/fusion/FIXServer.log | tail -1000 | awk '\
                if ($3 >= from && $3 <= to) {\
                        if ($0 ~ sess && $0 ~ "8=FIX") {\
                                gsub(/\^A/,"|")\
                                gsub(/FFS\: Comm\: Sending data\:/, ">>>>>>")\
                                gsub(/FFS\: Comm\: Received data\:/, "<<<<<<")\
                        }\
                }' from=$timeminus to=$datestring sess="$session"

```

and here is the error I get on execution [from within a bash scrpt]:

```
awk: syntax error near line 2
awk: bailing out near line 2

```

I don't know much, and I am sure I am missing something obvious, but do not seem to be able to see what.

Thanks for any help!!:)

---

### Post by stroyan on 2008-02-12
You need a set of  braces around the awk script.
Awk needs 'if' lines to be inside an action denoted by '{ }'.
You don't need the backslashes at the end of lines.
The single quotes handle sending the multiple lines to awk.
You do need an explicit print after the gsub action.
Your earlier use of awk was based on an implicit print from the 'if' test.
```

 cat -v /home/ffprd/log/fusion/FIXServer.log | tail -1000 | awk '{
                if ($3 >= from && $3 <= to) {
                        if ($0 ~ sess && $0 ~ "8=FIX") {
                                gsub(/\^A/,"|")
                                gsub(/FFS\: Comm\: Sending data\:/, ">>>>>>")
                                gsub(/FFS\: Comm\: Received data\:/, "<<<<<<")
                        }
                        print
                }
                }' from=$timeminus to=$datestring sess="$session"
```

---

### Post by v4169sgr on 2008-02-13
Thanks for your help! Here is my script:

```
        cat -v /home/ffprd/log/fusion/FIXServer.log | tail -1000 | awk '{
                if ($3 >= from && $3 <= to) {
                        if ($0 ~ sess && $0 ~ "8=FIX") {
                                gsub(/\^A/,"|")
                                gsub(/FFS\: Comm\: Sending data\:/, ">>>>>>")
                                gsub(/FFS\: Comm\: Received data\:/, "<<<<<<")
                        }
                        print
                }
        }' from=$timeminus to=$datestring sess="$session"
```

and here are the compilation errors:

```
awk: syntax error near line 3
awk: illegal statement near line 3
awk: syntax error near line 4
awk: illegal statement near line 4
awk: syntax error near line 5
awk: illegal statement near line 5
awk: syntax error near line 6
awk: illegal statement near line 6
awk: syntax error near line 10
awk: bailing out near line 10 
```

And here I thought I was on to a good thing:lolflag:

Any help much appreciated.

---

### Post by stroyan on 2008-02-13
That is very strange.  I can cut and paste that script into a shell here and awk runs without complaint.

---

### Post by ghostdog74 on 2008-02-13
you should show the whole script you have. also, whats your awk version? do a awk --version and find out.

---

### Post by v4169sgr on 2008-02-14
Thanks for the continued interest. Here is the script in question; it's been a busy day in work today, so awk version will folllow tomorrow.

```
#!/bin/bash
#
session=$1

if [ -n "$session" ]
then
        break;
else
        echo "Usage: 'fixlog.sh <SESSIONID>'"
        exit 1;
fi

echo
echo "Tailing FIXServer.log for FIX messages on session $session"
echo

#linecount=0

while [ 1 ]
do

        datestring=$(date +%H:%M:%S)

#       Subtract 9 seconds from current time as computed by 'date', taking account of minutes and hours
#       Attributed to tukuyomi and stroyan on ubuntu forums

        IFS=: read H M S <<< "$datestring"
        ((H=10#$H))
        ((M=10#$M))
        ((S=10#$S))

        SEC=$(($S+$M*60+$H*3600-9))
        H=$(($SEC/3600))
        M=$(((($SEC-$H*3600))/60))
        S=$(($SEC-$H*3600-$M*60))

        timeminus=$(printf "%02d:%02d:%02d" $H $M $S)

        # Extracts only those FIX messages in the time space in consideration. v4169sgr.

        sleep 10

        cat -v /home/ffprd/log/fusion/FIXServer.log | tail -1000 | awk '{
                if ($3 >= from && $3 <= to) {
                        if ($0 ~ sess && $0 ~ "8=FIX") {
                                gsub(/\^A/,"|")
                                gsub(/FFS\: Comm\: Sending data\:/, ">>>>>>")
                                gsub(/FFS\: Comm\: Received data\:/, "<<<<<<")
                        }
                        print
                }
        }' from=$timeminus to=$datestring sess="$session"

done
```

---

### Post by ghostdog74 on 2008-02-14
i looked back some of the post, and realized you are using Solaris. On Solaris, use nawk, instead of awk. try that first .

---

### Post by v4169sgr on 2008-02-15
> **ghostdog74 said:**
> i looked back some of the post, and realized you are using Solaris. On Solaris, use nawk, instead of awk. try that first .

Thanks very much for that tip! Replacing 'awk' with 'nawk' solved everything and allowed me to make rapid progress. Well, who'd a thought a?:popcorn:

Don't know which version of awk that was btw but must have been truly ancient as this is apparently SunOS 5.10. Good job it had nawk. Ubuntu, on the other hand, is right up there, with the times, even on Dapper:)

One more question, if you wouldn't mind:

How could I use a character like '|' in an awk 'if' statement? For example

```
if ($0 ~ "|35=0|") { ....

```

Escaping the pipe character with '\' doesn't work either.

Cheers!

---

### Post by tukuyomi on 2008-02-15
Maybe using single quotes? (I didn't try... sorry)
```
if ($0 ~ '|35=0|') { ....
```

---

### Post by ghostdog74 on 2008-02-15
> **v4169sgr said:**
> 

How could I use a character like '|' in an awk 'if' statement? For example

```
if ($0 ~ "|35=0|") { ....

```

Escaping the pipe character with '\' doesn't work either.

Cheers!
use // for regular expression, not double quotes.
eg
```

if ( $0 ~ /\|35=0\|/) {
  print "make sure you escape the pipe character with backslash"
}

```
however, if you have specified your field separator as pipes, you  might not need to check for pipes. In that case if your "35=0" is in the 3rd field for example , then your awk statement looks like
```

awk 'BEGIN{FS="|"} $3 ~ /35=0/ ' file

```

---

### Post by v4169sgr on 2008-02-18
> **ghostdog74 said:**
> use // for regular expression, not double quotes.
eg
```

if ( $0 ~ /\|35=0\|/) {
  print "make sure you escape the pipe character with backslash"
}

```


Many thanks again for your help - this has saved me a lot of time and is being suitably credited :guitar:

One more thing: :)

Looking at the script has a whole, I've seen this error message ever snce I switched the script to Solaris' /bin/sh to /bin/bash:

```
./fixlog_dev.sh: line 9: break: only meaningful in a `for', `while', or `until' loop

```

Almost strangely, that part of the script works as intended, but the error message is unsightly. What to do about it?

Your continued assistance is very valuable!

---

### Post by stroyan on 2008-02-18
You have
```

if [ -n "$session" ]
then
        break;
else
        echo "Usage: 'fixlog.sh <SESSIONID>'"
        exit 1;
fi
```
But the break builtin doesn't do anything but cause a warning.
You actually mean for it to do nothing at all, continuing on after the if/then/else statement.
You could use
```

if [ -n "$session" ]
then
        : ;
else
        echo "Usage: 'fixlog.sh <SESSIONID>'"
        exit 1;
fi
```
or
```
if [ -z "$session" ]
then
        echo "Usage: 'fixlog.sh <SESSIONID>'"
        exit 1;
fi
```

---

### Post by v4169sgr on 2008-02-19
> **stroyan said:**
> 
```
if [ -z "$session" ]
then
        echo "Usage: 'fixlog.sh <SESSIONID>'"
        exit 1;
fi
```

That did it! Many thanks again :guitar:

---

### Post by boxholder on 2010-08-31
I know this is an old thread, but it got me pretty close to what I need.  That is, to 
subtract  tenths of a second from hh:mm:ss.ss .

I've been stringing small avi files together. Problem, each file has a short audiable click
created when the video camera is turned off.  ffmpeg will report the duration of a
video file in the hh:mm:ss.ss  format. I wanted to loop through the files and subtract 
.30 seconds from the duration of each video. 

Here is a snipet of the modified bash code showing how to subtract tenths of a second
from the given duration. Hope this helps someone :D

```
 
  # use ffmpeg to get info about avi file ie. Duration hh:mm:ss.ss

  duration_orig=$(ffmpeg -i $AVI_file_name 2>&1 | grep "Duration:" \
          | tr -s " " | cut -d " " -f3 | tr -d ",")

  oldIFS=$IFS # save orig field seperator
 
 IFS=: read H M S <<< "$duration_orig"

  # remove decimal point ".", effectively multiplying by 100
  # so that we're working with an integer instead of a decimal number

  S=$( echo $S | tr -d "." )

  # the format x=10#$var forces base 10 numbers
  ((H=10#$H))
  ((M=10#$M))
  ((S=10#$S))

  ###############################
  # clipping value

  clip=30  # trim off .30 seconds
  ###############################

  SEC=$(($S+$M*6000+$H*360000))

  SEC=$(($S+$M*6000+$H*360000-$clip))  # subtraction happens here

  H=$(($SEC/360000))                 # start converting back to hh:mm:ss.ss
  M=$(((($SEC-$H*360000))/6000))
  S=$(($SEC-$H*360000-$M*6000))
  IFS="$oldIFS"

  sec_int=$((S/100))
  sec_dec=$((S-(sec_int*100)))

  # force H (hours) to two places
  if [ ${#H} -eq 0 ];then
     H="00"
   else
     if [ ${#H} -eq 1 ];then H="0$H";fi
  fi

  # force M (minutes) to two places
  if [ ${#M} -eq 0 ];then
     M="00"
   else
     if [ ${#M} -eq 1 ];then M="0$M";fi
  fi

  # force sec_int to two places
  if [ ${#sec_int} -eq 0 ];then
     sec_int="00"
   else
     if [ ${#sec_int} -eq 1 ];then sec_int="0$sec_int";fi
  fi

  # force sec_dec to two places
  if [ ${#sec_dec} -eq 0 ];then
     sec_dec="00"
   else
     if [ ${#sec_dec} -eq 1 ];then sec_dec="$sec_dec0";fi
  fi

  endpos="$H:$M:$sec_int.$sec_dec"   # here it's all strung back together

  echo "$duration_orig - .$clip = $endpos"
#-----------------------------------------------------------

```

---

