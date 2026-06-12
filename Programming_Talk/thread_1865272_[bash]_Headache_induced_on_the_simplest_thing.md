---
title: "[bash] Headache induced on the simplest thing"
date: 2011-10-19
forum: Programming Talk
---

### Post by cryptotheslow on 2011-10-19
Hi,

I hope someone with even a little bash scripting experience can help a scripting newb out here.

Summary:
Eventual goal of this exercise is to have a script called every system shutdown to set an RTC wake event for 21:00 UTC. If it is invoked >21hrs and before end of day UTC then set it for 21:00 UTC the following day. Seemed simple.

I have worked out how to write the wake event and tested just fine from the command line. And I know how to have it invoked at shutdown. Only problem I have is that I have been tripping myself up for hours now trying to get the script correct to calculate the value for "21:00 UTC Tomorrow" - and my now head hurts!

Let me post the script and output (excuse the excessive commenting and echoing in it - just me trying to keep my thoughts straight and debugging :) )

Script:
```
crypto@ubuserver:~$ cat ./test.sh
#!/bin/bash
# Script to set RTC wakeup time to make sure ubuserver is awake when MHShost WHM backsup.
# MHS host starts back up at 17:11 EDT/EST, with files being FTP'd before 20 minutes past the hour.
# FTP destination is ubuserver. ubuserver userland is set to GMT/BST.
# EDT/EST change dates do not align with GMT/BST.
# ubuserver rtc is set to UTC.
# ubuserver userland is set to GMT/BST.
# So file arrival time could be 22:xx or 21:xx in ubuserver userland
# File rotation on ubuserver takes place at 23:46 GMT/BST
# Aaaargh... timezones hurting my head now. Let's just do this script in UTC.
# Let's make sure ubuserver is up between 21:00 and 23:59 UTC.
# So we set RTC wakeup to 21:00 UTC for today if time now is <21:00 and for 21:00 tomorrow if later on.
# This script will be called at ubuserver shutdown and set the next wakeup time.

# Let's find what the UTC hour is
hournow=`date -u +%H`
echo UTC Hour now is: $hournow

# Is it before 21:00?
if [ ! $hournow -ge 21 ]; then
    before21=1
    echo before21: $before21
else
    before21=0
    echo before21: $before21
fi

## !!NOTE: I know the qualification should be =0 on this if but for debugging have set it to =1 as it is now
# Later than 21:00 let's work out UTC 21:00 for tomorrow and put it in a var
if [ $before21 -eq 1 ]; then
    # Get tomorrow's date in dd/mm/yy form
    tomorrowdate=`date -d tomorrow -u +%x`
    echo tomorrowdate is: $tomorrowdate
    # Convert dd/mm/yy to UTC seconds since epoch
    tomorrowdateepoch=`date --date $tomorrowdate +%s`
    echo tomorrowdateepoch is: $tomorrowdateepoch
    # Add 21 hours to tomorrowdateepoch and put it into waketime var
    waketime=$tomorrowdateepoch + 75600
    echo waketime is: $waketime
fi
crypto@ubuserver:~$

```
Output:
```
crypto@ubuserver:~$ ./test.sh
UTC Hour now is: 02
before21: 1
tomorrowdate is: 21/10/11
date: invalid date `21/10/11'
tomorrowdateepoch is:
./test.sh: line 38: +: command not found
waketime is:
crypto@ubuserver:~$

```
What I can't grasp is why $tomorrowdate echos just fine but then when used in the date command in line 38 appears to get wrapped in mismatched ` and ' breaking the command.

I know this is going to be such a simple answer that I will kick myself, but I have been looking at quoting and escaping examples and tutorials for hours now and hit a dead-end trying to get this to work.

Some help getting over this little hurdle and I'm sure I can get the rest of the thing working :D Can't believe I've spent this long trying to get this to work only to save me having to remember just to walk upstairs and push the power button :lolflag:

TIA
crypto

---

### Post by papibe on 2011-10-19
Hi cryptotheslow.

Bash math expression are handled with double parenthesis. Try this:
```
...
waketime=$(($tomorrowdateepoch + 75600))
...
```
Hope it helps,
Regards.

---

### Post by cryptotheslow on 2011-10-20
Thank you Papibe - that will surely help and I have updated the script as below.

But it's still tripping up before it gets to that point on the error in line 38 - although the output is now no longer stating line 38 :confused:

So now I'm just assuming it is something to do with how I am including $tomorrowdate in this line:

```
tomorrowdateepoch=`date --date $tomorrowdate +%s`
```
Revised complete script:

```
crypto@ubuserver:~$ cat test.sh
#!/bin/bash
# Script to set RTC wakeup time to make sure ubuserver is awake when MHShost WHM backsup.
# MHS host starts back up at 17:11 EDT/EST, with files being FTP'd before 20 minutes past the hour.
# FTP destination is  ubuserver. ubuserver userland is set to GMT/BST.
# EDT/EST change dates do not align with GMT/BST.
# ubuserver rtc is set to UTC.
# ubuserver userland is set to GMT/BST.
# So file arrival time could be 22:xx or 21:xx in ubuserver userland
# File rotation on ubuserver takes place at 23:46 GMT/BST
# Aaaargh... timezones hurting my head now. Let's just do this script in UTC.
# Let's make sure ubuserver is up between 21:00 and 23:59 UTC.
# So we set RTC wakeup to 21:00 UTC for today if time now is <21:00 and for 21:00 tomorrow if later on.
# This script will be called at ubuserver shutdown and set the next wakeup time.

# Let's find what the UTC hour is
hournow=`date -u +%H`
echo UTC Hour now is: $hournow

# Is it before 21:00?
if [ ! $hournow -ge 21 ]; then
    before21=1
    echo before21: $before21
else
    before21=0
    echo before21: $before21
fi

## !!NOTE: I know the qualification should be =0 on this if but for debugging have set it to =1 as it is now
# Later than 21:00 let's work out UTC 21:00 for tomorrow and put it in a var
if [ $before21 -eq 1 ]; then
    # Get tomorrow's date in dd/mm/yy form
    tomorrowdate=`date -d tomorrow -u +%x`
    echo tomorrowdate is: $tomorrowdate
    # Convert dd/mm/yy to UTC seconds since epoch
    tomorrowdateepoch=`date --date $tomorrowdate +%s`
    echo tomorrowdateepoch is: $tomorrowdateepoch
    # Add 21 hours to tomorrowdateepoch and put it into waketime var
    waketime=$(($tomorrowdateepoch + 75600))
    echo waketime is: $waketime
fi
crypto@ubuserver:~$

```Revised script output:

```
crypto@ubuserver:~$ ./test.sh
UTC Hour now is: 03
before21: 1
tomorrowdate is: 21/10/11
date: invalid date `21/10/11'
tomorrowdateepoch is:
waketime is: 75600
crypto@ubuserver:~$

```I think I'm still bedevilled by that `' around the var content being fed into the date command in line 38 - at least that is the best I can make of it as the output is no longer referencing line 38 and not complaining about the + in it being a separate command. WTH? All I changed was the line that sets waketime which is after line 38.

I'm lost now. How can the output of an earlier line in a script change if one changes a later line? Either the change has inadvertently closed an unclosed expression higher up or I fundamentally do not understand how bash scripts are parsed :(

I'll continue battling on this myself as it puzzles me, but any help gratefully received.

---

### Post by Vaphell on 2011-10-20
no, your problem is all about date not recognizing the input format
```
$ LANG=C date -d 21/10/11
date: invalid date `21/10/11'
$ LANG=C date -d 21.10.2011
date: invalid date `21.10.2011'

```
simple as that

date appears to be US-centric and will crap out more often than not when given different format (my locale spits out 21.10.2011 from %x and i get the same deal - standard date format for my locale, produced by date is not later accepted by the same date command, wtf)

store the date in a locale-free format (USian that is: month/day/year)
```
$ day=$( LANG=C date -d tomorrow +%x )
$ date -d $day
pi&#261;, 21 Pa&#378; 2011, 00:00:00 CEST

```
and it will work. LANG=C sets the locale to 'none'

btw, drop backticks `` and replace them with $( ... )

---

### Post by papibe on 2011-10-20
**EDIT: Oops: too slow to answer..**

It appears to be a locale's date representation. See my results:
```
$ date +%x
10/20/2011

```
Also, your script runs fine here:
```
$ ./time.sh 
UTC Hour now is: 05
before21: 1
tomorrowdate is: 10/21/2011
tomorrowdateepoch is: 1319173200
waketime is: 1319248800
waketime is: 1319248800

```
I would try to use another date format. I would start with the self explanatory default:
```
tomorrowdateepoch=$(date --date $tomorrowdate)
```
If that doesn't work, may something like US style maybe (+%D)?

Hope that helps.
Regards.

---

### Post by Vaphell on 2011-10-20
Why on earth do the USian formats have precedence over the locale ones in the first place. That is seriously messed up. Why should one know or care about the specifics of the US format when one spends whole life dealing with y[/.-]m[/.-]d or d[/.-]m[/.-]y formats?

---

### Post by cryptotheslow on 2011-10-20
Thank you both for taking the time to look at this. I've not had time to fully digest your replies yet - however I was trying to avoid complication in the script by using UTC, but it seems localisation is still defeating me along the way. Logically to me UTC > all when it comes to timezone rationality.

I expect the problem is my syntax or logic rather than a flaw in "date".  Maybe I should just export the timezone within the script as UTC and have it run in a UTC context rather than bother with the grief in the script. That sounds feasible right now but hell, everything seems feasible right now lol

I will come back to this when I've slept some. I really do appreciate you putting eyes and thought on this - I was stuck there, now I have new avenues open to explore again :D

---

### Post by Vaphell on 2011-10-20
the script did say what the problem is, (invalid date `$date') didn't it? :)

utc shifts time according to your timezone, but it says nothing about the format. These are 2 separate things.
You need to store the date in a format that is 100% sure to work and for presentation/calculation puproses pass it through date command with the formatting of choice to get the derived form.

---

### Post by papibe on 2011-10-20
> **Vaphell said:**
> Why on earth do the USian formats have precedence over the locale ones in the first place. That is seriously messed up. Why should one know or care about the specifics of the US format when one spends whole life dealing with y[/.-]m[/.-]d or d[/.-]m[/.-]y formats
+1

I completely agree.

I dug a little but, and it seems that the only way to do 'serious' dates scripting and manipulation is to use "timestamps" (a.k.a Unix timestamps, epoch timestamps, or just plain "seconds since 1970-01-01 00:00:00 UTC"). This is my [reference]("http://mywiki.wooledge.org/BashFAQ/070?highlight=%28date%29").

Example applied to cryptotheslow's:
```
    # Convert dd/mm/yy to UTC seconds since epoch
    tomorrowdateepoch=$(date -d tomorrow +%s)
    echo "tomorrowdateepoch is: $tomorrowdateepoch"

    # Get tomorrow's date in local form
    human_tomorrowdate=$(date -d @"$tomorrowdateepoch")
    echo "tomorrowdate is: $human_tomorrowdate"

    # Add 21 hours to tomorrowdateepoch and put it into waketime var
    waketime=$(($tomorrowdateepoch + 75600))
    echo "waketime is (epoch): $waketime"

    #Get the printable human local form of waketime
    human_waketime=$(date -d @"$waketime")
    echo "waketime is (human): $human_waketime"

```
Since we all have different locales, it would be a great test if we all test that code. This is mine:
```
tomorrowdateepoch is: 1319180506
tomorrowdate is: Fri Oct 21 02:01:46 CDT 2011
waketime is (epoch): 1319256106
waketime is (human): Fri Oct 21 23:01:46 CDT 2011

```
Which seems to be working here.

Kind regards.

---

### Post by Vaphell on 2011-10-20
```
tomorrowdateepoch is: 1319183583
tomorrowdate is: pi&#261;, 21 pa&#378; 2011, 09:53:03 CEST
waketime is (epoch): 1319259183
waketime is (human): sob, 22 pa&#378; 2011, 06:53:03 CEST
```

---

### Post by cryptotheslow on 2011-10-20
> **Vaphell said:**
> the script did say what the problem is, (invalid date `$date') didn't it? :) 

Yes I suppose it did, but not in a way I could understand. I'm still confused about the ` and ' :confused:

> **Vaphell said:**
> utc shifts time according to your timezone, but it says nothing about the format. These are 2 separate things.
You need to store the date in a format that is 100% sure to work and for presentation/calculation puproses pass it through date command with the formatting of choice to get the derived form.

As I understand it UTC doesn't shift time at all, more that the timezone shifts local time relative to UTC. i.e. UTC is the same in all places on Earth at any given moment in time. (I'm sure we used to call it GMT lol)

And yes - I am sure you are right about the formatting being the root of the evil here. Other scripting stuff I've done (mostly php/mysql/tcl), I always put time into seconds since epoch utc before doing anything with it. Which is what I was trying to do here but failing dismally thanks to my terribly poor grasp of the language.

---

### Post by cryptotheslow on 2011-10-20
> **papibe said:**
> +1

I completely agree.

I dug a little but, and it seems that the only way to do 'serious' dates scripting and manipulation is to use "timestamps" (a.k.a Unix timestamps, epoch timestamps, or just plain "seconds since 1970-01-01 00:00:00 UTC"). This is my [reference]("http://mywiki.wooledge.org/BashFAQ/070?highlight=%28date%29").

Example applied to cryptotheslow's:
```
    # Convert dd/mm/yy to UTC seconds since epoch
    tomorrowdateepoch=$(date -d tomorrow +%s)
    echo "tomorrowdateepoch is: $tomorrowdateepoch"

    # Get tomorrow's date in local form
    human_tomorrowdate=$(date -d @"$tomorrowdateepoch")
    echo "tomorrowdate is: $human_tomorrowdate"

    # Add 21 hours to tomorrowdateepoch and put it into waketime var
    waketime=$(($tomorrowdateepoch + 75600))
    echo "waketime is (epoch): $waketime"

    #Get the printable human local form of waketime
    human_waketime=$(date -d @"$waketime")
    echo "waketime is (human): $human_waketime"

```Since we all have different locales, it would be a great test if we all test that code. This is mine:
```
tomorrowdateepoch is: 1319180506
tomorrowdate is: Fri Oct 21 02:01:46 CDT 2011
waketime is (epoch): 1319256106
waketime is (human): Fri Oct 21 23:01:46 CDT 2011

```Which seems to be working here.

Kind regards.


Thanks papibe. Will try this shortly and report back.

---

### Post by Vaphell on 2011-10-20
> **cryptotheslow said:**
> Yes I suppose it did, but not in a way I could understand. I'm still confused about the ` and ' :confused:

`'? they are used in error messages quite often to indicate failing parameter (but don't ask me why backtick + single_quote) eg.
```
$ rm there_is_no_such_thing
rm: cannot remove `there_is_no_such_thing': No such file or directory
```

> As I understand it UTC doesn't shift time at all, more that the timezone shifts local time relative to UTC. i.e. UTC is the same in all places on Earth at any given moment in time. (I'm sure we used to call it GMT lol)

that's what i meant but expressed it poorly :)

---

### Post by cryptotheslow on 2011-10-20
Thanks papibe.

 example:

```
crypto@ubuserver:~$ ./test.sh
UTC Hour now is: 09
before21: 1
tomorrowdateepoch is: 1319188809
tomorrowdate is: Fri Oct 21 10:20:09 BST 2011
waketime is (epoch): 1319264409
waketime is (human): Sat Oct 22 07:20:09 BST 2011
crypto@ubuserver:~$

```

Seems to be localising fine now. I just need to hack it a little so waketime ends up being 21:00 tomorrow (utc) rather than this time tomorrow + 21 hours. All good... I have a way forward rather than a dead-end I went to bed on lol

Damn - using brackets rather than back ticks makes it so much more readable. Someone must have been having a laugh when they put both back ticks and single quotes in this language as meaningful things! :D


Thanks Vaphell for the clarification on the `' wrap on failed parameters. I must have "seen" it a gazillion times but never seen it!

```
crypto@ubuserver:~$ rm random_wut_why_would_anyone_do_that
rm: cannot remove `random_wut_why_would_anyone_do_that': No such file or directory

```

lol...  I wasn't in a dead-end at all... I had gone off down a rabbit-hole trying to work out the `' for hours. Comical! :D

Thanks both again - hopefully the next time I post back it will be with this thing working and just to dump my poorly mashed together script on the world lol

---

### Post by cryptotheslow on 2011-10-20
OK - got back to this after being obliged to do some real work and then a little snooze.

Fresh eyes and another scour of the date man page - and the solution is remarkably simple.

For the world's consumption here it is, all you need to know is the UTC hour you wish the machine to wakeup (just change all references of 21 to your chosen hour).

Oh - and all echos except the last 2 lines can be taken out.

The script:
```
#!/bin/bash
# Script to set RTC wakeup time to make sure ubuserver is awake when remote backup arrives.
# Need to make sure ubuserver is up at 21:00 UTC every day.
# So we set RTC wakeup to 21:00 UTC for today if time now is <21:00 and for 21:00 tomorrow if later on.
# This script will be called at ubuserver shutdown and set the next wakeup time.

# Let's find what the UTC hour is now
utchournow=$(date -u +%H)
echo UTC Hour now is: $utchournow

# Is it before 21:00?
if [ ! $utchournow -ge 21 ]; then
    before21=1
    echo before21: $before21
else
    before21=0
    echo before21: $before21
fi

if [ $before21 -eq 1 ]; then
    # Earlier than 21:00 let's get UTC 21:00 for today and put it in a var
    waketime=$(date -u --date="today 21:00:00" +%s)
    echo waketime - secs since epoch utc: $waketime
else
    # Later than 21:00 let's get UTC 21:00 for tomorrow and put it in a var
    waketime=$(date -u --date="tomorrow 21:00:00" +%s)
    echo waketime - secs since epoch utc: $waketime
fi

# Let's clear and then write the RTC wake event
echo 0 > /sys/class/rtc/rtc0/wakealarm
echo $waketime > /sys/class/rtc/rtc0/wakealarm

```And the output:
```
crypto@ubuserver:~$ cat /proc/driver/rtc
rtc_time        : 17:44:19
rtc_date        : 2011-10-20
alrm_time       : 17:49:10
alrm_date       : ****-**-20
alarm_IRQ       : no
alrm_pending    : no
24hr            : yes
periodic_IRQ    : no
update_IRQ      : no
HPET_emulated   : yes
DST_enable      : no
periodic_freq   : 1024
batt_status     : okay
crypto@ubuserver:~$ sudo ./test.sh
UTC Hour now is: 17
before21: 1
waketime - secs since epoch utc: 1319144400
crypto@ubuserver:~$ cat /proc/driver/rtc
rtc_time        : 17:44:31
rtc_date        : 2011-10-20
alrm_time       : 21:00:00
alrm_date       : 2011-10-20
alarm_IRQ       : yes
alrm_pending    : no
24hr            : yes
periodic_IRQ    : no
update_IRQ      : no
HPET_emulated   : yes
DST_enable      : no
periodic_freq   : 1024
batt_status     : okay
crypto@ubuserver:~$
```The joy :D

Feel free to suggest improvements or poke fun at it :popcorn:


Thanks papibe and Vaphell for your help, wouldn't have got this done without you guys :)



Add Google friendly terms: bash script RTC wake wakeup alarm event BIOS

---

