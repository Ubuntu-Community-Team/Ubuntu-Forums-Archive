---
title: "Touch Script:Multiple Files in Multiple Folders"
date: 2012-08-03
forum: New to Ubuntu
---

### Post by smackheid on 2012-08-03
Hi all,

Here's a challenge...

I need to update the modified date/time for different logfiles with the same name, with different dates/times.

The logfile is dumped into a FTP box every 30 mins and has the same name (BlockedNode.csv), so overwrites the previous one. Said files have been collected and put in a directory of it's own(File1, File2 etc), to preserve the filename for the past 2 weeks (672 files in total).

Each file in it's folder has then placed into a folder for the day (day1, day2 etc). So, each Day folder (eg Day1) has 48 subfolders, each containing the single logfile of the same name.

The files have been manipulated and it's last modified date lost. I want to read the contents of the file read into a database, where the last modified date will serve as a reference point for the log entry and I need the last modified date to reflect the actual date/time of when the even was captured.

Can anyone think of a way of writing a script that will go into the folder (logfile) then into the subfolder (DayX) then into individual folder (File1) and update the modified timestamp of file BlockedNode.csv with say 25072012 0000 then move to folder (File2) and update the file BlockedNodes.csv with 25072012 0030, for all 48 files that day (0000-2330) and then move to the next day folder and repeat, only with the next day's date?

Thanks in advance
SmackHeid

---

### Post by idoitprone on 2012-08-03
this sounds too intelligent for me and very confusing read

why dont you make name of the folder the date it was created and symlink the folder name to day1, day2, or whatever?

---

### Post by cortman on 2012-08-03
Ouch. Too complicated.

Sounds to me like a simple renaming script would be a better idea than trying to separate them into folder after folder. Something that would grab the timestamp info and append it to the backup file's name. Run it with cron every ten minutes or so.

---

### Post by smackheid on 2012-08-03
Good shout, but I should mention that the directory structure and their contents have already been created and cannot be changed without excessive manual intervention. 

Any other thoughtss?

---

### Post by cortman on 2012-08-03
> **smackheid said:**
> Good shout, but I should mention that the directory structure and their contents have already been created and cannot be changed without excessive manual intervention. 

Any other thoughtss?

You could still run a script to rename each file with the timestamp- just be sure that script gets it before it gets sorted.

---

### Post by steeldriver on 2012-08-03
These things are easier if you specify them EXACTLY - for example are the directories really called Day1, Day2 etc. or are they actual date strings e.g. 2012-07-27 and so on? Can you provide a (truncated) output from ls -R at the top level of the log directory tree?

---

### Post by smackheid on 2012-08-03
Absolutely, but I can't figure out the logic, being a noob and all. 

How would I give a script the ability to change a file, knowing to update the time by a factor of 30 mins and add 1 to the date for each day's files?

---

### Post by smackheid on 2012-08-03
steeldriver: the folders really are called day and file. Not at terminal just now, but here's an example...

Logfiles/Day1/File1/BlockedNode.csv. 

Day1..14
File1..48

---

### Post by steeldriver on 2012-08-03
OK so I had a quick play,

```
for i in {1..2}; do for j in {1..2}; do echo $(date --date="2012-07-25 + $j days") File$i/Day$j/BlockedNodes.csv; done; done
Thu Jul 26 00:00:00 EDT 2012 File1/Day1/BlockedNodes.csv
Fri Jul 27 00:00:00 EDT 2012 File1/Day2/BlockedNodes.csv
Thu Jul 26 00:00:00 EDT 2012 File2/Day1/BlockedNodes.csv
Fri Jul 27 00:00:00 EDT 2012 File2/Day2/BlockedNodes.csv


```echos the correct dates + filenames, so I would think that

```
for i in {1..48}; do for j in {1..14}; do touch -d "$(date --date="2012-07-25 + $((j-1)) days")" File$i/Day$j/BlockedNodes.csv; done; done

```*ought* to work 

see if you can figure it out :)

---

### Post by smackheid on 2012-08-05
Hi Steeldriver,

Thank you very much for your help. I appreciate it to no end.

Unfortunately though, I can't seem to figure out how to change the time by 30 minute increments. 

Here is what I've come up with so far:

$ for i in {1..14}; do for j in {1..48}; do $((h=(j-1)/2,m=(j-1)%2*30)); date +%Y%m%d%H%M -d "2012-07-24 + $i day $h:$m"; Day$i/File$j/BlockedNodes.csv; done; done

Any clues?

Thanks again
Smackheid

---

### Post by steeldriver on 2012-08-05
why not just convert the whole thing into minutes?

```
#!/bin/bash

for i in {1..14}; do 
  for j in {1..48}; do 
    mins=$((60*24*(i-1) + 30*(j-1)))
    touch -d "$(date -d "2012-07-25 + $mins minutes")" ./Day$i/File$j/BlockedNodes.csv"
  done
done
```

---

### Post by steeldriver on 2012-08-05
well it's a wet afternoon and the dog's asleep so here's another (possibly more elegant) way you might do it, which doesn't rely on iterating over a fixed number of files / dirs

```
#!/bin/bash

while read -r -d $'\0' file; do
  
  # extract the day index and 30-min time interval from the filename
  daynum=$(echo "$file" | sed -rn 's/(^.*Day)([0-9]+)(.*$)/\2/p')
  filenum=$(echo "$file" | sed -rn 's/(^.*File)([0-9]+)(.*$)/\2/p')
  
  # check we have valid day and time digits
  if [[ "$daynum" =~ [0-9]+ && "$filenum" =~ [0-9]+ ]]; then
    # calculate the total time offset in minutes
    mins=$((60*24*(daynum-1) + 30*(filenum-1)))
    # perform the touch
    echo "touching $file => $(date --date="2012-07-25 + $mins minutes")"
    touch -d "$(date --date="2012-07-25 + $mins minutes")" $file
  else
    # report any undateable matching files
    echo "ERROR : $file : file undateable" 1>&2
  fi

done < <(find . -name 'BlockedNodes.csv' -print0)
```

---

### Post by smackheid on 2012-08-07
> **steeldriver said:**
> well it's a wet afternoon and the dog's asleep so here's another (possibly more elegant) way you might do it, which doesn't rely on iterating over a fixed number of files / dirs

```
#!/bin/bash

while read -r -d $'\0' file; do
  
  # extract the day index and 30-min time interval from the filename
  daynum=$(echo "$file" | sed -rn 's/(^.*Day)([0-9]+)(.*$)/\2/p')
  filenum=$(echo "$file" | sed -rn 's/(^.*File)([0-9]+)(.*$)/\2/p')
  
  # check we have valid day and time digits
  if [[ "$daynum" =~ [0-9]+ && "$filenum" =~ [0-9]+ ]]; then
    # calculate the total time offset in minutes
    mins=$((60*24*(daynum-1) + 30*(filenum-1)))
    # perform the touch
    echo "touching $file => $(date --date="2012-07-25 + $mins minutes")"
    touch -d "$(date --date="2012-07-25 + $mins minutes")" $file
  else
    # report any undateable matching files
    echo "ERROR : $file : file undateable" 1>&2
  fi

done < <(find . -name 'BlockedNodes.csv' -print0)
```

Steeldriver, you are a god amongst men. Thank you very much for your help with this. Words fail me. I wish I had your abilities.

Thanks to everyone else who contributed, I love how the Linux community are so willing and ready to help out.

Thanks and regards
Smackheid

---

### Post by steeldriver on 2012-08-07
Happy to help - I try to give back what I've learned on here plus bits + bobs of programming I've picked up over the years. TBH I don't really understand all the stuff with 'find' and 'read' so I hope I've done it right - the idea was to make it safe for situations like filenames with spaces and so on (overkill for your application - but a good habit to get into).

The clever part imo is how (at least the GNU version of) 'date' seems to be able to handle almost any human readable time string you throw at it and somehow figure out what you mean... I was surprised about that :)

Regards

EDIT: in hindsight  don't know why I suggested the ugly sed expressions to extract the day and file numbers - you might want to do something like this instead:

```
  # extract the day index and 30-min time interval from the filename
  tmp=$(echo "$file" | grep -Eo 'Day[0-9]+'); daynum=${tmp##Day}
  tmp=$(echo "$file" | grep -Eo 'File[0-9]+'); filenum=${tmp##File} 
```or even (if you are sure about the order of the Day and File directory in the path)

```
  # extract the day index and 30-min time interval from the filename
  read -d'\n' daynum filenum < <(echo "$file" | grep -Eo '(Day|File)[0-9]+' | grep -Eo '[0-9]+') 
```

---

