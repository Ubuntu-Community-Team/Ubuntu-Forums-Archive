---
title: "batch photo management script"
date: 2012-11-06
forum: Programming Talk
---

### Post by mcapri76 on 2012-11-06
I recently bought a nice homeserver that I am trying to customise to my needs. The problem I've got has to do with photos management.

What I am trying to do is creating a script that daily checks for changes in the /mount/photos folder and subfolders for newly added pics and resize and move the resized copy into /mount/photos/resized.

Useless to say that I am not 'big' in programming ;) . I guess I am stuck because
I cannot tackle the first item on the list. I checked FAQs and searched for similar queries in this forum but to no avail.

*Automatic Daily running script that does the following:*


[LIST]
[*]SCAN - /mount/photos sub-directories for photos (jpg) more recent than this script log file
[*]RENAME - <folder_name>+<date>+<sequential>.jpg sequential=picking up from the last one
[*]RESIZE - selected files [convert example.jpg -resize 1920 example.jpg]
[*]MOVE - resized pictures into /mount/images/resized/2012
[*]CREATE - log file with outcome of the script
[/LIST]

Any help is appreciated.

Cheers
mcapri

---

### Post by Vaphell on 2012-11-06
```
#!/bin/bash

src_dir=.                    # main dir (SCAN)
dest_dir=../new_pics         # dir for resized stuff (RESIZE+MOVE)
log_dir=.                    # 
log=pics_$( date +%F ).log   # log name, not used yet
year=$( date +%Y )           # not used yet (MOVE)

# find latest log file
read _ lastlog < <( find "$log_dir" -iname '*.log' -printf "%T@\t%f\n" | sort -nr )
if [ "$lastlog" ]
then
  log_ts=$( stat -c %y "$lastlog" )   # log timestamp for debugging
  echo "latest log file: $lastlog ($log_ts)"
  # prepare parameter list
  scan_options=( "-newer" "$lastlog" "-iname" "*.jpg" )
else
  scan_options+=( "-iname" "*.jpg" )
fi

# print find options
# for s in "${scan_options[@]}"; do echo "'$s'"; done

# find files newer than the log file (all files if there is no .log file)
files=() 
while read -r -d $'\0' f
do
  files+=( "$f" )
done < <( find "$src_dir" "${scan_options[@]}" -print0 )

# print files etc
for f in "${files[@]}"
do
  echo "file: $f   ($( stat -c %y "$f" )) > ($log_ts)"
# test if in proper format
#  [[ $f =~ .+-.+-[0-9]+.jpg ]] && echo proper format || echo rename
done  #> "$log_dir/$log"

```

that should find the files newer than the newest existing log file. Obviously variables at the top should be filled with proper values to point where they should.
It doesn't produce log by itself, i skipped that part as it would make debugging annoying (every run would create newer log and i'd have to roll its timestamp back or touch all dummy files - pain in the back when you have to do this every 10 seconds)
Create whatever .log file in proper location, use touch command to set it to some time, eg.
```
touch -d 'now -2 days' test.log
```
and see if the list is ok.

Could you elaborate more on the renaming part? What would the date format be exactly? And is the sequence global in the directory or maybe it is only related to subsets based on days?

```

global:                     day based:
abc-(yesterday)-001.jpg     abc-(yesterday)-001.jpg
abc-(yesterday)-002.jpg     abc-(yesterday)-002.jpg
abc-(today)-003.jpg         abc-(today)-001.jpg
abc-(today)-004.jpg         abc-(today)-002.jpg

```

---

### Post by mcapri76 on 2012-11-07
Thanks you for your help.

Sorry not to have been more specific about the rename part. Looking back I should have removed the <date> bit. I normally include the year in the folder name to make it unique. So the script should just rename to <foldername>+<sequential>.jpg

mcapri

---

### Post by Vaphell on 2012-11-07
so you throw some files in and expect them to be renamed to fit the rest of files in that dir?
abc/abc-0001.jpg
abc/abc-0002.jpg
abc/some-junk.jpg -> abc-0003.jpg

should the index width be fixed? 4digits or something?

---

### Post by mcapri76 on 2012-11-07
exactly! 

It makes sense to me to have all files in a photo directory (e.g: Lanzarote2011) having the name of the folder plus the sequential. Three digits are more than enough.

Just out of curiosity, do you have any photo files naming standard that you use?

Cheers

---

### Post by Vaphell on 2012-11-07
i don't collect photos, so no ;-)

---

### Post by Vaphell on 2012-11-07
```
#!/bin/bash

src_dir=.                    # main dir (SCAN)
resized=../resized          # RESIZE+MOVE
log_dir=.                    # 
log=pics_$( date +%F ).log   # log name, not used yet
year=$( date +%Y )           # not used yet (MOVE)
w=3                          # index width

# exit if any of dirs is missing
[ -d "$src_dir" ] || exit 1
[ -d "$log_dir" ] || exit 1
[ -d "$resized" ] && mkdir -p "$resized/$year" || exit 1

# find latest log file
read _ lastlog < <( find "$log_dir" -iname '*.log' -printf "%T@\t%f\n" | sort -nr )

if [ "$lastlog" ]
then
  log_ts=$( stat -c %y "$lastlog" )   # log timestamp for debugging
  echo "latest log file: $lastlog ($log_ts)"
  echo "new log file: $log_dir/$log"
  # prepare parameter list
  scan_options=( "-newer" "$lastlog" "-iname" "*.jpg" )
else
  scan_options+=( "-iname" "*.jpg" )
fi
echo "-----------------------------------"
# find files newer than the log file (all files if there is no .log file)
files=() 
while read -r -d $'\0' f
do
  files+=( "$f" )
done < <( find "$src_dir" "${scan_options[@]}" -print0 ) 

echo "${#files[@]} new file(s) found!"

# print files etc
for f in "${files[@]}"
do
#  echo "*** file: $f ($( stat -c %y "$f" )) newer than $log_dir/$lastlog ($log_ts)"
  echo "*** file: $f"
  pdirpath="${f%/*}";
  pdir="${pdirpath##*/}";

  # find first unused fileXXX.jpg
  i=0
  while (( ++i ))
  do
    newfpath="$pdirpath/$pdir $( printf "%0${w}d" $i ).jpg"
    [ "$newfpath" = "$f" ] && break
    [ -f "$newfpath" ] || break
  done

  # rename if 
  [ "$newfpath" != "$f" ] && mv -v -- "$f" "$newfpath"
  # resize if the resized version doesn't exist
  resfpath=$resized/$year/${newfpath##*/}
  [ ! -f "$resfpath" ] && echo "resized: $resfpath" && convert "$newfpath" -resize 1920 "$resfpath"
  echo
done >> "$log_dir/$log"


```


i haven't used real jpg files so i simply echoed that convert line. Either way, test it hard on some dummy set of files and locations. I wouldn't want to be responsible for a heavy mess caused by improper **mv** calls or something.

If there is no log file in provided location, all files are caught. If the log files (name based on date) exist, newest one is picked for comparison.
Files that match the name pattern (in case it's possible to have good name on a file newer than the latest log file) are skipped.
script is not smart in case there are gaps. If the name is in proper format but the first empty slot is before that index, file will be renamed.
proper format 001.jpg
proper format 002.jpg
proper format 004.jpg -> proper format 003.jpg

resized/**$year** currently is automatically calculated (YEAR of date='now'), but do you need that? i think it's nice but what should happen when you drop something into the 'NewYearsEve 2012' photo album in 2013?

the naming convention - after some thinking i'd say that 'year(+month?)+name' format of directory names would be best to preserve chronology. Of course it all depends on what logic the format is supposed to represent.

---

### Post by mcapri76 on 2013-04-10
After many hiccups I was able to test the script above and it works a treat! 

Thank you.

The test highlighted one thing I did not think about; is it possible to modify the script so it replicates the original photo folder structure into the /resized/$year folder.

Photos > Folder1 > Photo1 > Photo2 > Photo3
          > Folder2 > PhotoA > PhotoB > PhotoC
          > Folder3

Resized/2013/Folder1 > Photoresized1 > Photoresized2 > Photoresized3
                   /Folder2 > PhotoresizedA > PhotoresizedB > PhotoresizedC
                   /Folder3

I honestly tried to work it out myself but I am New to this whole thing (with the capital 'N').

Cheers

---

### Post by Vaphell on 2013-04-10
```
#!/bin/bash

src_dir=.                    # main dir (SCAN)
resized=../resized           # RESIZE+MOVE
log_dir=.                    # log dir
log=pics_$( date +%F ).log   # log name
w=3                          # index width
year=$( date +%Y )

# exit if any of dirs is not available
[ -d "$src_dir" ] || exit 1
[ -d "$log_dir" ] || exit 1
[ -d "$resized" ] && mkdir -p "$resized/$year" || exit 1

# find latest log file
read _ lastlog < <( find "$log_dir" -iname '*.log' -printf "%T@\t%f\n" | sort -nr )

if [ "$lastlog" ]
then
  log_ts=$( stat -c %y "$lastlog" )   # log timestamp for debugging
  echo "latest log file: $lastlog ($log_ts)"
  echo "current log file: $log_dir/$log"
  # prepare parameter list
  scan_options=( "-cnewer" "$lastlog" "-iname" "*.jpg" )
else
  scan_options=( "-iname" "*.jpg" )
fi
echo "-----------------------------------"
# find files newer than the log file (all files if there is no .log file)
files=() 
while read -r -d $'\0' f
do
  files+=( "$f" )
done < <( find "$src_dir" "${scan_options[@]}" -print0 ) 

echo "${#files[@]} new file(s) found!"

# print files etc
for f in "${files[@]}"
do
#  echo "*** file: $f ($( stat -c %y "$f" )) newer than $log_dir/$lastlog ($log_ts)"
  echo "*** file: $f"
  fdir="${f%/*}";
  album="${fdir##*/}";

  # find first unused fileXXX.jpg
  i=0
  while (( ++i ))
  do
    fnew="$fdir/$album $( printf "%0${w}d" $i ).jpg"
    [ "$fnew" = "$f" ] && break
    [ -f "$fnew" ] || break
  done

  # rename if 
  [ "$fnew" != "$f" ] && mv -vi -- "$f" "$fnew"
  # resize if the resized version doesn't exist
  res_fnew="$resized/$year/${fnew##$src_dir/}"
  if [ ! -f "$res_fnew" ]
  then
    mkdir -p "${res_fnew%/*}"
    echo "resized: $res_fnew"
    convert "$fnew" -resize '1920x1920>' "$res_fnew"
  fi
  echo
done | tee -a "$log_dir/$log"

```

again, try on a set of dummy images first. I made some minor changes, i didn't like old variable names ;-)
also, out of curiosity: what should happen when you put some image that scales to let's say 1920x1440? Do you consider it a valid output format?

---

### Post by ofnuts on 2013-04-11
In the "find" option, you should really use -cnewer instead of "-newer". With -newer, if you import old photos (with modification date older than last run), they won't be taken in account. But their inode change date should still tell when they were imported.

---

### Post by Vaphell on 2013-04-11
good point, modified the script

---

### Post by mcapri76 on 2013-04-11
Vaphell, I am saying 1920 because I was looking for a smaller format that will suit my mobile/tablet and Plasma screen alike. Thinking about it, if there is a way to resize to 1920 the longest side it would be even better. Another thing, is the script retaining the original metadata; data taken, exif .... ?

The more I think about this the more complex it becomes! 

One final thing, how would you suggest a new user (me) to learn about bash scripts?

---

### Post by Vaphell on 2013-04-11
> Vaphell, I am saying 1920 because I was looking for a smaller format that will suit my mobile/tablet and Plasma screen alike. Thinking about it, if there is a way to resize to 1920 the longest side it would be even better. Another thing, is the script retaining the original metadata; data taken, exif .... ?

resize '1920x1920^' means pretty much scale down to fit in 1920x1920 box. 
i asked just in case you wanted to fit images in full-hd format (1920x1440 is too big for 1920x1080) - proper scaling down would require a bit of rather trivial math

> The more I think about this the more complex it becomes! 

that's everyday life of your average programmer, most seemingly simple things are not simple when it comes to finer details :)

> One final thing, how would you suggest a new user (me) to learn about bash scripts? 

Somewhere in the stickies in beginner forum there should be a thread about command line resources but i learned simply by reading bash related threads in these forums and by writing scripts with the help of google.  I have a directory for scripting tests and have dozens of bash scripts exploring different concepts and problems.
You just need to learn to identify building blocks of your whole solution and formulate right questions: 'bash split string', 'bash replace string', 'bash read file'. Don't stop reading when you see the first working solution, read why it works and when it can fail. Once you got an idea how to solve the problem, ask if there is some hole in your train of thought or obvious flaw. Pointed out mistakes and different angles of approaching the task at hand are invaluable in learning.

I think that once you learn about globs (patterns matching files/dirs), parameter expansion, if, while- and for-loops and about 10 basic commands like grep, sed, find, sort you are golden. Minute details will come with time and experience.

---

### Post by mcapri76 on 2013-04-21
Thanks for the helpful tips, during testing I tried to make more sense of your script. The comments really helped. I still have a couple of outstanding issues: resized file naming standard - removal of the space between the filename and number. This will help file handling using the command line, by looking into the script code I was unable to identify where this is inserted. Another issue is the file size, 4MB pics once resized are still 1.8MB. This is more than expected, so I tried the resized command with the -quality option. Tweaking it to 90 already makes a big difference (600KB).

---

### Post by schragge on 2013-04-21
> **mcapri76 said:**
> removal of the space between the filename and number. This will help file handling using the command line, by looking into the script code I was unable to identify where this is inserted. Here:
```
fnew="$fdir/$album[highlight][COLOR=#ffd700]_[/COLOR][/highlight]$( printf "%0${w}d" $i ).jpg"
```

---

### Post by Vaphell on 2013-04-21
while not using spaces is somewhat beneficial because it simplifies things a bit, learning to tame them is more. If you plan to use your new skills only with conveniently named files, you are into a lot of disappointment. Luckily you have various options that make spaces a non-issue:
- autocompletion with tab (it escapes all the nasty characters on top of doing 90% of the typing work)
- \[space] -space in the open becomes harmless when treated with \
- "string[space]string" - quotes define single entity, overriding 'break to separate words on whitespace' rule. You can quote parts of/whole paths no problem
- "$variable_storing_value_with_whitespace" - as a rule of thumb always double-quote your variables
- file-matching patterns (globs) don't care about spaces much (just make sure glob is treated as a single entity), eg *" "* works plenty fine, just leave wildcard chars outside quotes
- avoiding for-loops with anything other than globs

---

### Post by mcapri76 on 2013-05-08
Thanks guys, I am getting there - slowly but I am moving forward about this.
Today I had some time to carry out some testing and there is a new issue with the script. The renaming part does not take into consideration the order of the pictures. Normally photos are ordered by when they were taken, with older photos having lower numbers that newer photos. This applies in my photo collection, but when the script renames the photos it also changes the order without following the creation data order.

example below:
-rwxrw-rw- 1 mcapri mcapri 2737801 2007-04-30 22:45:16.000000000 +0100 Bfest_Apr07023.jpg
-rwxrw-rw- 1 mcapri mcapri 2803667 2007-04-30 22:29:30.000000000 +0100 Bfest_Apr07024.jpg
-rwxrw-rw- 1 mcapri mcapri 2902748 2007-04-30 22:41:56.000000000 +0100 Bfest_Apr07025.jpg
-rwxrw-rw- 1 mcapri mcapri 3038780 2007-04-30 22:25:38.000000000 +0100 Bfest_Apr07026.jpg
-rwxrw-rw- 1 mcapri mcapri 2797056 2007-04-30 22:32:36.000000000 +0100 Bfest_Apr07027.jpg

---

### Post by Vaphell on 2013-05-08
try changing this fragment
```
files=() 
while read -r -d $'\0' [COLOR="#0000FF"]ts[/COLOR] f
do
  files+=( "$f" )
done < <( find "$src_dir" "${scan_options[@]}"[COLOR="#0000FF"] -printf '%T@\t%p\0' | sort -zn[/COLOR] ) 
```

find is nicely asked to print matches in the *timestamp[tab]path\0* format, output is sorted numerically which should put files in chronological order.
While read intercepts ts (not needed anymore) and path, the rest stays the same.

---

### Post by Vaphell on 2013-05-09
after some thinking it occured to me that the way the script worked is wasteful when looking for the first free index. Every single file made it look from 0 all the way up, eg 0->995, then 0->996, then 0->997.
I split the process to 2 stages
1. look for directories that have new files (find files, but only get dir part with* -printf %h*).
2. for each directory search for new files (this is sadly redundant, we find the same files 2nd time), but only limited to that dir (so it should be plenty fast). The advantage is that it allows to skip the wasteful index discovery - once you are at number 844 you dont have to test from 0, just check availability of 845, right? As a bonus you get more detailed info (X new files found **in dir Y**)

```
#!/bin/bash

src_dir=.                    # main dir (SCAN)
resized=../resized           # RESIZE+MOVE
log_dir=.                    # log dir
log=pics_$( date +%F ).log   # log name
w=3                          # index width
year=$( date +%Y )

# exit if src is not available, create logdir and resized if missing
[ -d "$src_dir" ] || exit 1
mkdir -p "$log_dir"
mkdir -p "$resized/$year"

# find latest log file
read _ lastlog < <( find "$log_dir" -iname '*.log' -printf "%T@\t%f\n" | sort -nr )

if [ "$lastlog" ]
then
  log_ts=$( stat -c %y "$lastlog" )   # log timestamp for debugging
  echo "latest log file: $lastlog ($log_ts)"
  echo "current log file: $log_dir/$log"
  # prepare parameter list
  scan_options=( "-cnewer" "$lastlog" "-iname" "*.jpg" )
else
  scan_options=( "-iname" "*.jpg" )
fi
echo "-----------------------------------"

# find dirs with files newer than the log file (all files if there is no .log file)
dirs=()
while read -r -d $'\0' d
do
  dirs+=( "$d" )
done < <( find "$src_dir" "${scan_options[@]}" -printf '%h\0' | sort -zu ) 

# do the procedure 1 dir at a time
for d in "${dirs[@]}"
do
  # find files for processing
  files=() 
  while read -r -d $'\0' ts f
  do
    files+=( "$f" )
  done < <( find "$d" -maxdepth 1 "${scan_options[@]}" -printf '%T@\t%p\0' | sort -zn ) 
  (( ${#files[@]}==1 )) && s='' || s='s'    # singular/plural
  echo "${#files[@]} new file${s} found in '$d'!"

  i=0
  # print files etc
  for f in "${files[@]}"
  do
  #  echo "*** file: $f ($( stat -c %y "$f" )) newer than $log_dir/$lastlog ($log_ts)"
    echo "*** file: $f"
    fdir="${f%/*}";
    album="${fdir##*/}";

    # find first unused fileXXX.jpg
    while (( ++i ))
    do
      fnew="$fdir/${album}_$( printf "%0${w}d" $i ).jpg"
      [ "$fnew" = "$f" ] && break
      [ -f "$fnew" ] || break
    done

    # rename if 
    [ "$fnew" != "$f" ] && mv -v -- "$f" "$fnew"
    # resize if the resized version doesn't exist
    res_fnew="$resized/$year/${fnew##$src_dir/}"
    if [ ! -f "$res_fnew" ]
    then
      mkdir -p "${res_fnew%/*}"
      echo "resized: $res_fnew"
      convert "$fnew" -resize '1920x1920>' "$res_fnew"
    fi
    echo
  done
done | tee -a "$log_dir/$log"
```

---

