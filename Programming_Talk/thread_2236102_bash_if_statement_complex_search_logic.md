---
title: "bash if statement complex search logic"
date: 2014-07-24
forum: Programming Talk
---

### Post by getut2 on 2014-07-24
I have bitten off more than I can chew with some bash scripting involving a very poorly laid out log file that I have no option to change. I have 2 different scenarios that have me stumped.

The log file is in the format of Time/Date related lines with other junk mixed in, followed by other lines detailing information about the processes run state that does NOT have date/time stamps.

Pseudo code for the self descriptive 1st scenario, this one is easier but still has me stumped at my padawan bash scripting level:

if logfile.log contains any line with the string 07/24/14 followed on the very next line by the text "Parsing Complete"
 then
    echo "parse complete"
else
  echo "parse failed or did not run"

The second scenario is similar but harder. It has the date/time stamp line followed by task states on lines following, but POTENTIAL fixes to problems after a search. I am completely lost on how to even start with this. 

Here is a sample log section:

Process run started on 7/24/14 9:23AM
status t8 succeed
status t9 succeed
status t10 succeed
status t11 failure
status t12 succeed

Pseudo code:

if logfile.log contains any line with the string 07/24/14 followed by a GROUP of lines all containing the text "status t" and the text "failure"
   then
     set a variable to the 1 or 2 digit number of the failure lines

My problem is I just don't know how to chop the data up into pieces I can deal with. 2 lines as a group in the first scenario and a grouped chunk of lines in the 2nd scenario.

---

### Post by steeldriver on 2014-07-24
Often with pattern matching problems, it's as important to consider what you **don't** want to match - remember you are trying to find the *minimal* set of attributes that *uniquely* defines the thing you want to extract. And what's the overall structure of the log? Are blocks separated by blank lines?

Since you have two quite distinct things, you might want to consider separating them into their own files for further processing. For example, you could do a multiline match like

```

pcregrep -nM '^.*\d{1,2}/\d{1,2}/\d{1,2}.*(\nstatus.*)+' *yourlog*

```

(I've used pcregrep - available from the repository; you *may* be able to use grep in PCRE mode with the -z option, but I couldn't make the -n switch work in that case) which will give you an output like

```

17:Process run started on 7/24/14 9:23AM
status t8 succeed
status t9 succeed
status t10 succeed
status t11 failure
status t12 succeed
32:Process run started on 7/24/14 9:23AM
status t8 succeed
status t9 succeed
status t10 succeed
status t11 failure
status t12 succeed

```

i.e. extracts each of the "type II" blocks, prepended with their starting line numbers in the original file - you could then further process these to find the 'failure' lines 

```

pcregrep -nM '^.*\d{1,2}/\d{1,2}/\d{1,2}.*(\nstatus.*)+' mylog | sed -r 's/(^[0-9]+):.*/\n\1/' > mylogII

awk -vRS= -F\n '{n=$1; for(i=2;i<=NF;i++) {if ($i ~ /failure/) print n+i-1;} }' mylogII

```

Just some ideas to get you started

---

### Post by ofnuts on 2014-07-24
You can transform your input with sed or awk. 

For the first case just remove the linefeed characted at the end of any line containing '7/24/14' to make it one single line with the next one. Then keep the lines with '7/24/14' and see those that contain "parsing complete"

For the second drop the linefeed just before "status" to splice into one line the data and the varoius status reports, then keep the line with '7/24/14' and may be split them again.

Or you can just read your file and implement the logic with a bit of Perl or Python. That could be more maintainable in the end, and not necessarily much slower. Bash one-liners are fun, but one should be pragmatic at times.

---

### Post by getut2 on 2014-08-26
Ok... I have still been mulling this one over and I think I have thought of an easier way to crack this nut but it is still beyond my skill level and I need help pulling it off. I can do everything I need to do with this file if I do the following FIRST.

Scan the file line by line for date and time stamps embedded in the line. Set a variable with the date and time stamp that is found, put the date and time stamp at the beginning of each line including and after that line until the next line with a date and time stamp is found.

---

### Post by steeldriver on 2014-08-26
You would probably get better answers if you explained your end goal and and gave a minimal representative sample of the actual log file and what you want to extract from it - otherwise it's easy to fall into the [X-Y problem]("http://www.perlmonks.org/index.pl?node_id=542341") trap

---

### Post by Vaphell on 2014-08-26
```
$ awk '/Process.*:[0-9][0-9][AP]M/{ d=$(NF-1)" "$NF; next; } { print d": " $0; }' <<< '17:Process run started on 7/24/14 9:23AM
status t8 succeed
status t9 succeed
32:Process run started on 7/26/14 2:55PM
status t11 failure
status t12 succeed'

7/24/14 9:23AM: status t8 succeed
7/24/14 9:23AM: status t9 succeed
7/26/14 2:55PM: status t11 failure
7/26/14 2:55PM: status t12 succeed
```

---

### Post by getut2 on 2014-08-26
I have the examples in the first post of the log file. I can't really give examples of the end goal because even I don't know what those are. Over the next few weeks I'm going to need to do a ton of work from this file and I just haven't been able to parse it in any useful way so far.

This particular log file is VERY poorly laid out as I state in the first email. It is generated from some very old windows software that is no longer supported. But basically it is in the format of:

Something started on date time
info about the task with no date or time
info about the task with no date or time
""

The number of information lines varies per task and can be any mix of successes or failures.

I see vaphell's response and I had not thought of doing it that way... I was in the process of testing with a while read line loop. Could someone break down what is going on it vaphell's one liner? I really am in this for the learning.. not just getting the task done although I am killing 2 birds with one stone.

---

### Post by Vaphell on 2014-08-26
in that awk code there are 2 blocks
the 1st one tests for the 'Process ... <date>', sets the variable assuming that the timestamp is stored in the last 2 fields: $(NF-1) and $NF (NF obviously being the internal variable storing the number of fields in the current line), gets next line right off the bat ignoring block #2
the 2nd block is reached for every other type of line and prints *date: original content*

---

### Post by getut2 on 2014-08-26
OMG.. I have spent all day beating on this trying to figure out what  witchcraft you were using that made this work on my test file but not on  my live file if I changed ANYTHING about the regex portion or what  portion of the file was doing something different than what I thought it  was that I was breaking if I altered it.

It wasn't witchcraft. If is a difference in a file created on windows versus my test file created on my linux box.  :<

I  finally copied the ENTIRE contents of my test file into the shell of  the live file AND IT STILL DIDN'T WORK. This one, I'll have to figure  out tomorrow. My head hurts. One single line has kicked my butt today.

---

### Post by Vaphell on 2014-08-27
care to post a snippet from original file, carriage returns and whatnot included?

---

### Post by getut2 on 2014-08-27
Here is one section of content from one of my live files. Wording changes, date and time formats change slightly from one file to the next (24 hour time vs AM/PM), but I have 3 different output files that are basically in the same format of:
1 line  of "Something started or ended on a date/time"
Multiple lines of specific details and steps and their status without a date or time

My ultimate goal is to process these files in multiple different ways, but this thread specifically is about how I can modify the original file so that the lines without date and time can have that added. This will make later processing much easier.

Here is real output from one of the files. This is the one I was fighting with yesterday that I finally figured out works if it is in the log file I created on linux, but fails if this same text is pasted into the log file generated by the windows software.

```
POLLING MODULE started 08/16/14 01:30:00 
UPL_PRE_DATE - SUCCESS 
UPL_RPT_Z1_REG - SUCCESS 
UPL_RPT_Z1_TIM - SUCCESS 
UPL_TIM_CLK - SUCCESS 
UPL_TIM_Z1_EMP - SUCCESS 
UPL_TIM_Z2_EMP - SUCCESS 
UPL_RPT_Z1_DEPST - SUCCESS 
UPL_RPT_Z1_DCR - SUCCESS 
POLLING MODULE ended 08/15/14 16:35:15: SUCCESS 
POLLING MODULE started 08/15/14 17:00:00 
UPL_PRE_DATE - SUCCESS 
UPL_RPT_Z1_REG - SUCCESS 
UPL_RPT_Z1_ALL_PLU - SUCCESS 
POLLING MODULE ended 08/15/14 17:00:59: SUCCESS 
POLLING MODULE started 08/15/14 17:05:00 
UPL_PRE_DATE - SUCCESS 
UPL_RPT_Z1_REG - SUCCESS 
UPL_RPT_Z1_TIM - SUCCESS 
UPL_TIM_CLK - SUCCESS 
UPL_TIM_Z1_EMP - SUCCESS 
UPL_TIM_Z2_EMP - SUCCESS 
UPL_RPT_Z1_DEPST - SUCCESS 
UPL_RPT_Z1_DCR - SUCCESS 
POLLING MODULE ended 08/15/14 17:05:15: SUCCESS 
POLLING MODULE started 08/15/14 17:30:00 
UPL_PRE_DATE - SUCCESS 
UPL_RPT_Z1_REG - SUCCESS 
UPL_RPT_Z1_ALL_PLU - SUCCESS 
POLLING MODULE ended 08/15/14 17:31:07: SUCCESS 
POLLING MODULE started 08/15/14 17:35:00 
UPL_PRE_DATE - SUCCESS 
UPL_RPT_Z1_REG - SUCCESS 
UPL_RPT_Z1_TIM - SUCCESS 
UPL_TIM_CLK - SUCCESS 
UPL_TIM_Z1_EMP - SUCCESS 
UPL_TIM_Z2_EMP - SUCCESS 
UPL_RPT_Z1_DEPST - SUCCESS 
UPL_RPT_Z1_DCR - SUCCESS 
POLLING MODULE ended 08/15/14 17:35:15: SUCCESS 
POLLING MODULE started 08/15/14 18:00:00 
UPL_PRE_DATE - SUCCESS 
UPL_RPT_Z1_REG - SUCCESS 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T2 comm busy 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T5 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T6 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T7 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T8 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T9 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T10 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T11 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T12 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T13 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T14 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T15 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T16 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T17 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T18 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T19 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T20 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T2 comm busy 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T5 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T6 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T7 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T8 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T9 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T10 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T11 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T12 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T13 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T14 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T15 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T16 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T17 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T18 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T19 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T20 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T2 comm busy 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T5 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T6 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T7 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T8 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T9 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T10 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T11 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T12 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T13 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T14 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T15 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T16 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T17 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T18 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T19 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T20 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T2 comm busy 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T5 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T6 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T7 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T8 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T9 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T10 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T11 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T12 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T13 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T14 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T15 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T16 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T17 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T18 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T19 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T20 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T2 comm busy 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T5 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T6 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T7 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T8 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T9 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T10 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T11 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T12 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T13 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T14 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T15 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T16 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T17 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T18 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T19 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Status: T20 no check 
ERROR:[UPL_RPT_Z1_ALL_PLU] Communication Failed 
POLLING MODULE ended 08/15/14 18:01:26: FAILED 
POLLING MODULE started 08/15/14 18:05:00 
UPL_PRE_DATE - SUCCESS 
ERROR:[UPL_RPT_Z1_REG] Status: T2 comm busy 
ERROR:[UPL_RPT_Z1_REG] Status: T5 no check 
ERROR:[UPL_RPT_Z1_REG] Status: T6 no check 
ERROR:[UPL_RPT_Z1_REG] Status: T7 no check 
ERROR:[UPL_RPT_Z1_REG] Status: T8 no check 
ERROR:[UPL_RPT_Z1_REG] Status: T9 no check 
ERROR:[UPL_RPT_Z1_REG] Status: T10 no check 
ERROR:[UPL_RPT_Z1_REG] Status: T11 no check 
ERROR:[UPL_RPT_Z1_REG] Status: T12 no check 
ERROR:[UPL_RPT_Z1_REG] Status: T13 no check 
ERROR:[UPL_RPT_Z1_REG] Status: T14 no check 
ERROR:[UPL_RPT_Z1_REG] Status: T15 no check 
ERROR:[UPL_RPT_Z1_REG] Status: T16 no check 
ERROR:[UPL_RPT_Z1_REG] Status: T17 no check 
ERROR:[UPL_RPT_Z1_REG] Status: T18 no check 
ERROR:[UPL_RPT_Z1_REG] Status: T19 no check 
ERROR:[UPL_RPT_Z1_REG] Status: T20 no check 
UPL_RPT_Z1_REG - SUCCESS 
UPL_RPT_Z1_TIM - SUCCESS 
UPL_TIM_CLK - SUCCESS 
UPL_TIM_Z1_EMP - SUCCESS 
UPL_TIM_Z2_EMP - SUCCESS 
UPL_RPT_Z1_DEPST - SUCCESS 
UPL_RPT_Z1_DCR - SUCCESS 
POLLING MODULE ended 08/15/14 18:05:28: SUCCESS 
POLLING MODULE started 08/15/14 18:30:00 
UPL_PRE_DATE - SUCCESS 
UPL_RPT_Z1_REG - SUCCESS 
UPL_RPT_Z1_ALL_PLU - SUCCESS 
POLLING MODULE ended 08/15/14 18:30:57: SUCCESS
```

---

### Post by steeldriver on 2014-08-27
The issue with Windows files is almost certainly the different convention for line terminations (CR-LF instead of plain LF) - you can either preprocess the files with a tool like sed, tr, or dos2unix or (depending on the text processing tools you choose) handle the alternative delimiters explicitly within your script.

FYI since your logs appear to have clear *record separators* of the form 

```

POLLING MODULE ended MM/DD/YY hh:mm:ss

```

you could also consider doing stuff like

```

awk -F'\n' -vRS="POLLING MODULE ended[^\n]*\n" -vseldate='08/15/14' '$1 ~ seldate' file

```

which will extract all the records for selection date '08/15/14', and is IMHO 'cleaner' than prepending each line of every record with the datestamp.

---

### Post by getut2 on 2014-08-27
I think its awesome that it is possible to do that and I'll definitely file it, but unless I am missing something it seems like it doesn't gain me much. In an effort to find certain specific errors that are typically buried in between the separators I'd to launch into another search to find the exact date and time of the error to report on it and take action based on the error found. A big problem that I'm going to have to script around is errors that show up but have been fixed later on, so I think I am going to have to a lot of bottom up parsing. Looking for successes first then specific failures that are actionable without human intervention, then finally the failures that have to have the human touch.

So with all that said and all the work that I have to do with these files in multiple passes, its seems easiest to me to just make one pass and put the time date on each line, because in the end in every scenario that I am currently aware of, all the errors that the script will be able to deal with have relevant data all on a single line.

Once I figure out the file difference problem, how do I make the awk line actually modify the original file?

---

### Post by Vaphell on 2014-08-28
i agree that depending on the use case you don't buy much with the elegant approach, while sprinkling dates all over the place makes the data trivially greppable which is convenient.

> Once I figure out the file difference problem, how do I make the awk line actually modify the original file? 

I'd say you should leave the source as is. Failed transformation may irreversibly destroy data and you certainly don't want that. Also leaving the source as is makes it possible to come up with a different, better solution in the future. You should rather use a pipeline with a middleman like
untouched original -> convenient format -> operations.

i'd probably go with something like quick-n-dirty this
```
#!/bin/bash

awk '      /started/ { print $0; from=$(NF-1)" "$(NF); }
    !/started|ended/ { print "["from"]\t"$0; }
             /ended/ { print $0; }' < <( sed 's/\r//' "$1" )
```

```
$ ./log_plower.bash log.txt | grep 'UPL_RPT_Z1_REG'
[08/16/14 01:30:00]	UPL_RPT_Z1_REG - SUCCESS 
[08/15/14 17:00:00]	UPL_RPT_Z1_REG - SUCCESS 
[08/15/14 17:05:00]	UPL_RPT_Z1_REG - SUCCESS 
[08/15/14 17:30:00]	UPL_RPT_Z1_REG - SUCCESS 
[08/15/14 17:35:00]	UPL_RPT_Z1_REG - SUCCESS 
[08/15/14 18:00:00]	UPL_RPT_Z1_REG - SUCCESS 
[08/15/14 18:05:00]	ERROR:[UPL_RPT_Z1_REG] Status: T2 comm busy 
[08/15/14 18:05:00]	ERROR:[UPL_RPT_Z1_REG] Status: T5 no check 
```

---

### Post by getut2 on 2014-08-28
ugh... See these already are copies of the real logs SFTP'd in from over 70 different locations leaving unaltered logs on the devices. Like I said I have a couple different log formats that I'm bringing together and pre-processing for other processes that will come behind it. In one of my scripts I'm already truncating the particular log file, the communications log, I have been using for most examples here. 

find . -name "*commd.log" -print | xargs sed -i "1,/$(date +'%m\/%d\/%y') 04/d"

In your example code, I can't figure out how to get an in place update for the date time similar to what the above line is doing. I need to do it to ALL of the logs, 70+ multiple times per day.

Using -i for the sed portion of your example doesn't give me what I need because it only works for the sed portion of the line and awk's in place doesn't work either. I can't figure out how to pass your code as an xarg because it is file specific and I need it to work as a wildcard. The following code doesn't work but it will give you an example of what I need to do. Consider it pseudo code... Basically I need to apply "in place" the date time modification of type X to all log files of type X. Then I have other batches of log files that use AM/PM for example (different log name) that need modification type Y to all files type Y.    After all the modifications, alerting and alarms, it all gets archived as a bundle relevant to a specific time period that equates to a specific task that is performed at the end user level that is being evaluated centrally.

```
find . -name "*commd.log" -print | xargs sed -i "1,/$(date --date="1 hour ago" +'%m\/%d\/%y %l') /d"
find . -name "*sysd.log" -print | xargs sed -i "1,/$(date --date="1 hour ago" +'%m\/%d\/%y %l') /d"
find . -name "*commd.log" -print | xargs `awk '      /started/ { print $0; from=$(NF-1)" "$(NF); }
    !/started|ended/ { print "["from"]\t"$0; }
             /ended/ { print $0; }' < <( sed 's/\r//' "$All Files Found by FIND portion of the command" )`
find . -name "*sysd.log" -print | xargs `awk '      /started/ { print $0; from=$(NF-1)" "$(NF); }
    !/begin|end/ { print "["from"]\t"$0; }
             /end/ { print $0; }' < <( sed 's/\r//' "$All Files Found by FIND portion of the command" )`
```

Steeldriver... you mentioned the X-Y problem. This is really a case of me trying to spare you guys from having to explain everything. I'm doing something big. Its alot of stuff. I've bitten off alot and am trying to learn alot of things along the way. So far it is going well thanks to help and teaching you guys have done. Some of it I'm understanding at a deeper level but some of it not quite. This particular awk sed combination is one that falls into the "not quite understanding it all" category. I've already automated tasks that were taking a human an hour and half each day down to about a 45 second script run. To tell you guys the end picture is just too much to do. I realize there are things that I'm doing in 2 lines or 4 that could be done in 1 liners and I'll learn those as I get better and understand more, but I'm already excited that I have written my first massive script in linux bash that parses 20 MB of log files on an hourly basis, finds errors, sends email alerts, corrects issues, reboots remote devices if needed etc... but I do have other chunks of code and other programs involved that are putting some limitations on me. Some I will be able to clean up with time and do what you consider the right way and other I won't because I don't have source code and the software is dead.

---

### Post by Vaphell on 2014-08-28
i pretty much never use xargs because that command promotes overloaded, borderline unreadable oneliners that suck when it comes to readability and maintainability. I prefer using full blown loop to iterate over sets of files one file at a time, that makes the individual steps obvious.
How many files are we talking about? I wonder if it's worth the hassle running xargs based oneliners for performance reasons or maybe it's worth it to take a small hit and break things down to level of individual files.


Awk doesn't have an in-place mode, you have to use temp file, roughly like this
```
awk < in.data > tmp.out
mv tmp.out in.data
```



these 2 lines seem to perform exact same operation so the obvious optimization would be to merge them into one to avoid find thrashing hard disks twice
```
find . -name "*commd.log" -print | xargs sed -i "1,/$(date --date="1 hour ago" +'%m\/%d\/%y %l') /d"
find . -name "*sysd.log" -print | xargs sed -i "1,/$(date --date="1 hour ago" +'%m\/%d\/%y %l') /d"
```
eg
```
find . -name '*commd.log' -o -name '*sysd.log'
```



this thing looks kinda messy. 
```
find . -name "*sysd.log" -print | xargs `awk '      /started/ { print $0; from=$(NF-1)" "$(NF); }
    !/begin|end/ { print "["from"]\t"$0; }
             /end/ { print $0; }' < <( sed 's/\r//' "$All Files Found by FIND portion of the command" )`
```


```
while read f
do
    # remove date-1hr stuff, carriage returns, do awk, replace contents of individual files via tmp file
    sed -i "1,/$(date --date="1 hour ago" +'%m\/%d\/%y %l') /d; s/\r//" "$f"
    awk '    /started/ { print $0; from=$(NF-1)" "$(NF); }
          !/begin|end/ { print "["from"]\t"$0; }
                 /end/ { print $0; }' < "$f" > file.tmp
    mv file.tmp "$f"
done < <( find -name '*sysd.log' -o -name '*commd.log' )
```

do you want to merge the files into one or keep them separated?

---

### Post by getut2 on 2014-08-29
> **Vaphell said:**
> How many files are we talking about? I wonder if it's worth the hassle running xargs based oneliners for performance reasons or maybe it's worth it to take a small hit and break things down to level of individual files.

In total I'm dealing with about 350 files that my script is gathering (SFTP) from about 70 remote sites. About 20MB worth of data each iteration of the script that gets pared down to about 2MB of relevant data before the real processing begins. This script does warnings, notifications and emailing about problems that show up in the logs and then automatically RE-gets sites that have issues in later runs until the problems are resolved. Once all issues for each iteration are resolved and verified by the script it is pre-processed and formatted and ultimately sent to a Business intelligence system running on MS-SQL Server.


these 2 lines seem to perform exact same operation so the obvious optimization would be to merge them into one to avoid find thrashing hard disks twice
```
find . -name "*commd.log" -print | xargs sed -i "1,/$(date --date="1 hour ago" +'%m\/%d\/%y %l') /d"
find . -name "*sysd.log" -print | xargs sed -i "1,/$(date --date="1 hour ago" +'%m\/%d\/%y %l') /d"
```
eg
```
find . -name '*commd.log' -o -name '*sysd.log'
```

> **Vaphell said:**
> 
```
while read f
do
    # remove date-1hr stuff, carriage returns, do awk, replace contents of individual files via tmp file
    sed -i "1,/$(date --date="1 hour ago" +'%m\/%d\/%y %l') /d; s/\r//" "$f"
    awk '    /started/ { print $0; from=$(NF-1)" "$(NF); }
          !/begin|end/ { print "["from"]\t"$0; }
                 /end/ { print $0; }' < "$f" > file.tmp
    mv file.tmp "$f"
done < <( find -name '*sysd.log' -o -name '*commd.log' )
```

do you want to merge the files into one or keep them separated?

I actually started this particular part of the search with a loop and wound back up at a loop so I guess that was the best way to do it after all! Although yours is much more elegant than mine was. You are doing all 3 of this questions in a single loop. Mine at best would have been 3 different loops.

I'm still trying to figure out all the awk stuff. Until this thread I was 100% awk free in anything I had ever done. It seems powerful but I have a lot to learn just for that command alone. I guess that is why the wiki page for awk says its a language, not a command. I guess in a way vi and regexes are too so maybe I shouldn't be so intimidated, I picked those up to a ** WORKING ** proficiency level pretty quickly. I can get stuff done, but I'm no where near efficiency and code beauty stages yet.

---

### Post by Vaphell on 2014-08-29
yep, awk is a full blown scripting language that most often is used by people passing miniscripts to execute.
You can write a file with #!/usr/bin/awk, make it executable and put all that code in quotes inside and it will run beautifully.
Oh, btw sed is the same - you can write sed scripts.

Imo awk is well worth it and it offers excellent return on time investment. It's a poor man's perl that can be used every time you need to pass info about state between records. It can easily solve 95% of common problems. Doing the same stuff in sed is usually possible but infinitely more tricky and i never bothered learning advanced sed tricks, given awk being there. For the really fancy stuff i just use python (i consider perl too arcane to bother - i like readability - and on its way out) but really it's only when i need multilayered data structures to do the job. That happens maybe in one case out of 20.

Once you figure out how to think in awk's way of series of *<condition> { code block to run }* and how to play with its variables to redefine what a record or a field is you are golden.

---

