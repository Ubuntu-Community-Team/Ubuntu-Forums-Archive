---
title: "Shell/bash"
date: 2014-08-08
forum: Programming Talk
---

### Post by rhss6-2011 on 2014-08-08
Hello there,
**I stopped making shell/bash scripts about two years ago** due to having more responsibilities in my life. A couple years before that, I made a wonderful script that I wrote on commission for someone who uses torrents - the main purpose of this script was to **FIND certain file-types and then do various things with them** depending on what the user selected** from a menu IN the terminal.**
Problem is that** I wrote that script in Ubuntu/Xubuntu 10.04**... And for some reason** with ABSOLUTELY NO CHANGES it magically stopped working after I upgraded my system**, so I'm wondering if anyone can help me make the script work again.

Keep in mind, it has been multiple YEARS since I used shell/bash which means I'm pretty much a NOOB right now since I forgot most of what I learned thanks to being preoccupied with the military. **After you take a look at the script it'll become very obvious what I'm trying to do here - and the part that I'm currently working on** **is in bold**. **Everything else is built off of that one part**, so it practically makes the entire script worthless.
**Let me know if you have any ideas, as long as you can EXPLAIN how it works to me** - if you post an answer and I don't understand what you're trying to tell me, I might send a message asking you about it but I probably won't implement your idea until someone can explain it to me (_**yes, feel free to treat me like an idiot - just be respectful**_).

Again, it's been years since I did anything with code - I still understand some of the basics, but don't throw any advanced or intermediate level coding on me and expect me to understand anything at this time...

**Here's a copy of my NOT-WORKING code**:

```

#!/bin/bash
# Command to execute is as follows
#Enter directory with this script, then
#sh extract.sh /DIRECTORY/WITH/ALL/FOLDERS/CONTAINING/RAR/FILES/
#DO NOT FORGET THE LAST SLASH
#For numbers 4-6 you need to edit the path to your own preferred directory...
echo ""
echo "Do NOT use numbers 08-10 unless you have modified the script for your"
echo "personal use!!!"
echo ""
echo "to run this script you need to add a directory in which to execute"
echo "example - sh MYNAME.sh /directory/in/which/I/may/help"
echo ""
if [ $# -ne 1 ]
then
  echo "You forgot to enter directory where I should work!"
  echo ""
  exit
fi


while 
mesg="\n==============================================\n
  01.. Check .sfv files.\n
  02.. Unrar all rar files.\n
  03.. Delete rar and sfv files.\n
  04.. Extract TAR files.\n
  05.. Extract TAR.GZ files.\n
  06.. Extract TAR.BZ2 files.\n
  07.. Gunzip ZIP files.\n
  08.. Move AVI files to your location.\n
  09.. Move MP4 files to your location.\n
  10.. Move MKV files to your location.\n
  X.. Exit
  \n==============================================\n
Select: \c"
do
  echo -e $mesg
  read selection
  case $selection in
  01)
    cd $1
    cfv -r ;;
**  02)**
**    for r in `find $1 -wholename *.rar`**
**    do**
**      echo "Unpacking in directory: "`dirname $r`**
**      unrar e -v $r `dirname $r`**
**    done ;;**
  03)
    for g in `find $1 -wholename *.r*`
    do 
      cd `dirname $g`
      echo "Deleting in directory: "`dirname $g`
      rm *.r?? *.url *.sfv imdb.nfo
      rm -r Sample/
    done ;;
  04)
  # we will need this soon:
    prevdir=`pwd`
    for f in `find $1 -wholename *.tar`
    do
      echo "Unpacking in directory: "`dirname $f`
      # you were using the wrong arguments for tar; any 
      # arguments after the tar file name in your command
      # tar -xvf $f `dirname $f`
      # are treated as files to extract from within the tar.
      # Instead, cd to the directory first, then extract:
      cd `dirname $f`
      tar -zxvf `basename $f`
      # then go back to the dir we were in to start with.
      cd $prevdir
    done ;;
  05)
    # we will need this soon:
    prevdir=`pwd`
    for f in `find $1 -wholename *.tar.gz`
    do
      echo "Unpacking in directory: "`dirname $f`
      # you were using the wrong arguments for tar; any 
      # arguments after the tar file name in your command
      # tar -xvf $f `dirname $f`
      # are treated as files to extract from within the tar.
      # Instead, cd to the directory first, then extract:
      cd `dirname $f`
      tar -zxvf `basename $f`
      # then go back to the dir we were in to start with.
      cd $prevdir
    done ;;
  06)
    # we will need this soon:
    prevdir=`pwd`
    for f in `find $1 -wholename *.tar.bz2`
    do
      echo "Unpacking in directory: "`dirname $f`
      # you were using the wrong arguments for tar; any 
      # arguments after the tar file name in your command
      # tar -xvf $f `dirname $f`
      # are treated as files to extract from within the tar.
      # Instead, cd to the directory first, then extract:
      cd `dirname $f`
      tar -jxvf `basename $f`
      # then go back to the dir we were in to start with.
      cd $prevdir
    done ;;
  07)
    for z in `find $1 -wholename *.zip`
    do
      echo "Unpacking in directory: "`dirname $z`
      gunzip -d -v -r $z `basename $z`
    done ;;
  08)
      for f in `find $1 -wholename *.avi`
    do
      echo "Moving AVI files from: `dirname $f` to /mnt/DATA/Downloads/01-TORRENTS/01-Downloaded/Walker.Texas.Ranger.S08E01-25.DVDRip.XviD-OSiTV"
      find $1/ -name "*.avi"
      mv $f /mnt/DATA/Downloads/01-TORRENTS/01-Downloaded/Walker.Texas.Ranger.S08E01-25.DVDRip.XviD-OSiTV
    done ;;
  09)
      for f in `find $1 -wholename *.mp4`
    do
      echo "Moving MP4 files from: `dirname $f` to /home/masterchief/MOVETESTING"
      find $1/ -name "*.mp4"
      mv $f /home/masterchief/MOVETESTING
    done ;;
  10)
      for f in `find $1 -wholename *.mkv`
    do
      echo "Moving MKV files from: `dirname $f` to /home/masterchief/MOVETESTING"
      find $1/ -name "*.mkv"
      mv $f /home/masterchief/MOVETESTING
    done ;;
  X) 
    exit;;
  esac
done

```



**THE PROBLEM** is mainly that** it STARTS doing what it's supposed to do**. Then** after it gets done extracting one set of ("r00", "r01", "r02") files** and gives me the finished file - such as an ISO or movie file, **the script thinks it's done and stops**, bringing the menu back up. I don't really understand what the problem is since I haven't changed ANYTHING in the script since I originally created it.

---

### Post by The Cog on 2014-08-08
Moved to programming forum, where it won't get buried so quickly and should find more appropriate readers.
Sorry I don't think I can help myself.

---

### Post by papibe on 2014-08-08
Hi rhss6-2011.

I believe this would be the code you want to fix?
```
    for r in `find $1 -wholename *.rar`
    do
      echo "Unpacking in directory: "`dirname $r`
      unrar e -v $r `dirname $r`
    done
```
In general, that would work OK, but only if there's no spaces and special characters on the file names. To avoid those rare cases, I would use this structure:
```
while IFS= read -d $'\0' -r rarfile
do
    echo "Unpacking in directory: "`dirname $r`
    unrar e -v $r `dirname $r`
done< <(find "$1" -type f -iname '*.rar' -print0)

```
You could gain some speed and readability, if you only call 'dirname' only once:
```
while IFS= read -d $'\0' -r rarfile
do
    unpack_dir="$(dirname "$rarfile")"

    echo "Unpacking in directory: $unpack_dir"
    unrar e -v "$rarfile" "$unpack_dir"

done< <(find "$1" -type f -iname '*.rar' -print0)

```
Note too that all variables are quoted to avoid problems with spaces and special characters.

If you are unpacking LOTS of file, it may be also good to use Bash internal parameter substitution instead of a call to 'dirname'":
```
while IFS= read -d $'\0' -r rarfile
do
    unpack_dir=""${rarfile%/*}""

    echo "Unpacking in directory: $unpack_dir"
    unrar e -v "$rarfile" "$unpack_dir"

done< <(find "$1" -type f -iname '*.rar' -print0)

```
Hope it helps. Let us know if that fix the problem or not.
Regards.

P.S.1.: I've learned most of these tricks from [sisco311]("http://ubuntuforums.org/member.php?u=244665") (thanks!)
P.S.2.: There are other observations I can make, but I imagine your main concern is to get the script working again.

---

### Post by rhss6-2011 on 2014-08-08
That wasn't actually my problem - this was (as an example)

I have a folder called "Torrent Downloads"
In that folder let's say there are TEN sub-folders.

In those ten sub-folders are the files I want to extract.


The script goes into the first sub-folder, extracts the files and then stops because it thinks that the job is done. I currently have no idea how to fix this issue.

The files are getting extracted properly just the way it should, but for some reason after the first sub-folder is done getting extracted then it stops.

Any ideas?

---

### Post by papibe on 2014-08-08
Did you try the new code?

Quick fix: try replacing the find statement in your code
From:
```
find $1 -wholename *.rar
```
to
```
find "$1" -type f -iname '*.rar'
```
Let us know if that helps.
Regards.

---

### Post by rhss6-2011 on 2014-08-11
I tried that, and I still have the exact same problem; After it extracts the first set of files in the first sub-folder, it stops... This is getting weird - I've never seen this type of problem before...

**Edited to add this:**

I'm not sure if it's a bug in the Shell/Bash coding with Xubuntu/Ubuntu, or if it could possible be a cause from upgrading my system; maybe some of the internal coding changed and my terminal no longer reads the script the way it has for the past year???

The only changes (aside from your suggestions which I tried implementing) that I've made to this script, are quotation marks. Other than that, literally nothing changed and it stopped working properly, as if by magic after upgrading my system. I'm really confused, to be honest...

---

### Post by Vaphell on 2014-08-11
maybe give examples of paths that find is supposed to return. Crapshoot is not a valid way of debugging.

---

### Post by papibe on 2014-08-11
Time to debug.

Run this:
```
#!/bin/bash

if [ "$#" -ne 1 ]; then
    echo "Usage ./script.sh path_to_downloads"
    exit 1
fi

DIR="$1"

echo "----------------------------------------------"
echo "find $DIR -wholename *.rar"
echo "Files found: $(find $DIR -wholename *.rar | wc -l)"
echo

echo "----------------------------------------------"
echo "find $DIR -iname *.rar"
echo "Files found: $(find $DIR -iname *.rar | wc -l)"
echo

echo "----------------------------------------------"
echo "find "$1" -type f -iname '*.rar'"
echo "Files found: $(find "$1" -type f -iname '*.rar' | wc -l)"
echo

echo "----------------------------------------------"
echo "while IFS..."

rar_count=0
while IFS= read -d $'\0' -r rarfile
do
    rar_count=$((rar_count+1))

done< <(find "$DIR" -type f -iname '*.rar' -print0)

echo "Files found: $rar_count"
echo

```
Copy this script on the same directory where your current script is.

I believe something like this is happening: if there's a rar file on the root directory where the script is executed, Bash would expand the expression '*.rar', and then you won't find all the files (see results marked in red).
```

$ l -R
.:
LAS/  Linux Unplugged/  SciByte/  script.sh*  TechSNAP/

./LAS:
LAS.rar

./Linux Unplugged:
Linux Unplugged.rar

./SciByte:
SciByte.rar

./TechSNAP:
TechSNAP.rar
$ ./script.sh .
----------------------------------------------
find . -wholename *.rar
Files found: 4

----------------------------------------------
find . -iname *.rar
Files found: 4

----------------------------------------------
find . -type f -iname '*.rar'
Files found: 4

----------------------------------------------
while IFS...
Files found: 4

$ touch dummy.rar
$ ./script.sh .
----------------------------------------------
find . -wholename *.rar
Files found: [COLOR="#FF0000"]**0**[/COLOR]

----------------------------------------------
find . -iname *.rar
Files found: [COLOR="#FF0000"]**1**[/COLOR]

----------------------------------------------
find . -type f -iname '*.rar'
Files found: 5

----------------------------------------------
while IFS...
Files found: 5

$ mv dummy.rar LAS.rar
$ ./script.sh .
----------------------------------------------
find . -wholename *.rar
Files found: [COLOR="#FF0000"]**0**[/COLOR]

----------------------------------------------
find . -iname *.rar
Files found: [COLOR="#FF0000"]**2**[/COLOR]

----------------------------------------------
find . -type f -iname '*.rar'
Files found: 5

----------------------------------------------
while IFS...
Files found: 5
```
Let us know if that helps.
Regards.

---

### Post by rhss6-2011 on 2014-08-11
Ok, I'm not entirely sure what the heck that did, but... the image should give you an idea of my Downloads folder, as well as whatever the script just figured out, because I sure don't know what it's talking about...

Something about an unexpected redirect???


**Edited to add this:**
By the way, all the sub-folders have a series of rar files that "need" to be extracted (which is what I'm testing this all on). To give you a visual idea - the image (not thumbnail)...

(Basically since it's a friend I'm trying to help, I have his folders actually copied on to my hard-drive...)

[IMG]https://fbcdn-sphotos-g-a.akamaihd.net/hphotos-ak-xpa1/t1.0-9/10599473_721810514553963_8900543494481479596_n.jpg[/IMG]

---

### Post by Vaphell on 2014-08-11
L2copypaste ;-)
you can highlight-select/middle-click paste
or if you prefer ctrl+shift+c/v in terminal, ctrl+c/v everywhere else.

Either way i see in the screenshot that you are running sh explicitly, despite the fact the script is for bash as indicated by the hashbang. sh =/= bash

---

### Post by rhss6-2011 on 2014-08-11
Ok, so Shell or Bash? All the scripts I've been using (based on what I was taught through a couple of books) told me to "ALWAYS" use that beginning. What's the difference?

And aside from that, I'm still not exactly wrong with the script. It worked just fine about two or three years ago... I install updates and it's not working? I'm not sure what exactly the problem is to begin with; I don't know what the right question is for that matter!

**Edited to add this:**

And even using "bash extract.sh" in my terminal the end result is still the same, regardless...

---

### Post by Vaphell on 2014-08-12
#!/bin/bash literally says "please use /bin/bash program to interpret this file".
If you have executable bit set, *./script* to run is enough because system figures things out from #!. If you call shell explicitly, you override the header of the file.
There are different kinds of shells with common basics but with different feature sets.
*That debug.sh: redirection unexpected* in the screenshot is barebone sh/dash failing at bash only feature.


so what happens when you replace 02 block with papibe's suggestion #2, #3 or #4 ( *while read ... done < <( find ... )* )
btw, add something like *echo "'$r'"* inside the loop to print out values of r to confirm that proper paths are passed.

---

### Post by papibe on 2014-08-12
We are getting close.

I believe there are a rar file in the folder you are executing the script, as only **[COLOR="#FF0000"]one[/COLOR]** file is found.

Please run again the debug script, but now in only one of these two ways:
```
bash ./debug.sh /path/to/downloads
```
or
```
chmod a+x ./debug.sh
./debug.sh /path/to/downloads
```
(replace /path/to/downloads with the actual path to the download directory).

BTW you can copy/paste the text from the terminal to post the results. 
Regards.

---

### Post by rhss6-2011 on 2014-08-12
**Same output as before...**

```

stephen@UNSC:/mnt/DATA/Downloads/01-TORRENTS/01-Downloaded$ bash ./debug.sh /mnt/DATA/Downloads/01-TORRENTS/01-Downloaded/
----------------------------------------------
find /mnt/DATA/Downloads/01-TORRENTS/01-Downloaded/ -wholename *.rar
Files found: 1


----------------------------------------------
find /mnt/DATA/Downloads/01-TORRENTS/01-Downloaded/ -iname *.rar
Files found: 1


----------------------------------------------
find /mnt/DATA/Downloads/01-TORRENTS/01-Downloaded/ -type f -iname '*.rar'
Files found: 1


----------------------------------------------
while IFS...
Files found: 1


stephen@UNSC:/mnt/DATA/Downloads/01-TORRENTS/01-Downloaded$

```


The main issue here, is that it's only recognizing "ONE" rar file (or set of files) to extract when **it should be recognizing one in EVERY sub-folder as shown in the screenshot**. The folder in which I have the two scripts DOESN'T have any files to extract - just the sub-folders...

---

### Post by Vaphell on 2014-08-12
to be honest i don't see any *.rar file in the screenshot, it's all numbers and sfv

---

### Post by rhss6-2011 on 2014-08-12
That's just because it doesn't show.

Here's a breakdown - r.00, r.01, r.02 etc. belong together. They're all rar files. My script (in the past) recursively looked for those files in the subfolder and extracted them either for a video, or ISO image. If one of the rars are missing I can't get the file completely extracted. That was the whole point of the script. It'd go into the subfolder and extract the files until EVERY folder was completely finished.

Now it finds the first set, and then after extraction it stops.

---

### Post by spjackson on 2014-08-12
Please post the output of:
```

find /mnt/DATA/Downloads/01-TORRENTS/01-Downloaded
ls -laR /mnt/DATA/Downloads/01-TORRENTS/01-Downloaded

```

---

### Post by Vaphell on 2014-08-12
> That's just because it doesn't show.

why would that be the case? It's not a hidden filetype. Occam bets 20 bucks and his razor that there is no rar file as in characters 'r' 'a' 'r'.

---

### Post by rhss6-2011 on 2014-08-12
It's been that way for years. EVERY torrent download I've seen from my friends, and my father included use rar files in that manner - why, I don't know nor do I really care and the point of this thread isn't really to discuss the validity of how people create/download torrents.

I'm trying to get help on fixing my (now outdated, apparently...) script.

---

### Post by rhss6-2011 on 2014-08-12
And as far as your "bet" is concerned... Here's a thumbnail.

---

### Post by papibe on 2014-08-12
You need to change the coding strategy.

Both your current script, and my debug script look for files **only named** 'something.rar'.

My guess is that the torrents now come in a different packaging, split, and naming convention. For what you have been saying, that was not the case before. Also, if the script worked before and not now, it also confirms that the naming convention has changed.

A thought:
What happen if you manually unrar, say the 'something.001' file? If it unrars the whole content successfully, then a possible approach would be to find '*.001' files instead of looking for rars.

Let us know what you think, and if you need help with that.
Regards.

---

### Post by Vaphell on 2014-08-12
> **rhss6-2011 said:**
> And as far as your "bet" is concerned... Here's a thumbnail.

that's not a .rar file in a literal sense of having .rar as filename extension.
Globs don't care about what virtual type saved in some pseudo registry the file supposedly belongs to. This is command line we are talking about. CLI tools only care about characters in the filename itself. *.rar will never ever match any .r01 or .001 file, period.


i suggest trying something like *find -regextype posix-extended -iregex '.*(rar|r01|001)'*

---

### Post by varunendra on 2014-08-12
> **rhss6-2011 said:**
> It's been that way for years. EVERY torrent download I've seen from my friends, and my father included use rar files in that manner - why, I don't know nor do I really care and the point of this thread....
Nope, it never used to be that way, at least not until a couple of years ago when I used to be a hardcore Windows user. And you must care now since the naming convention seems to have changed as papibe pointed out -

> **papibe said:**
> My guess is that the torrents now come in a different packaging, split, and naming convention. For what you have been saying, that was not the case before. Also, if the script worked before and not now, it also confirms that the naming convention has changed.

I can confirm that the multi-part rar files used to be **ONE .rar file, then .r01, .r02,.... etc**. And even windows used (I believe it still does) to only recognize upto the .r05 or probably a few more files (would open them with winrar on double-clicking), not .r06 onwards (won't know what to do with them on double-click). Linux always decides a file-type by looking at its headers, so recognizing them wasn't a problem then nor is now. But that is not the point here.

To extract them, one had to right-click the first file (.rar), which would then extract all the other files automatically. If I remember correctly, one could also open/extract them via those other files (.r01, .r02.... upto .r05 or .r06) that were associated in registry as rar files, thus being recognized as rar archives. But that also is not the point here - the unrar program will probably still do its job as it should. The point is - There _USED TO BE a rar file_ in each set.

You want your script to go in each directory where there are files to extract. To identify and list these directories, you are using 'find' command. Now the find command, in its current form in your script, will -

1) ONLY find and list those directories which have a .rar file in them.
2) If there is no .rar file in a directory, **find** simply won't list it, period.

If this same script used to work like you want, and if you still have any of those source directories/packages stored anywhere, go look into them - you'll find .rar files in each of them.

If it could help, I could attach multiple screenshots displaying that older naming convention (still can, since I have an XP installation in a VM, and old versions of winrar), but it won't. What can help is understanding the fundamentals of bash or any shell interpreter.

---

### Post by rhss6-2011 on 2014-08-13
We're all kinda right - **I just found what the real issue is**... Interesting enough...

Ok, so after everyone mentioned how the torrents used to be split up and how that changed I took a MUCH closer look at EACH folder and the files within. I came to the conclusion that the one **folder where it works properly HAS a .rar file**. **When I move all 46 r.0* files** into a different folder I of course **can't extract the contents** of the rar. Likewise, **when I move the rar file I can't extract it either**.
HOWEVER,** when I have BOTH **the rar AND r.0* files in the folder together** it will extract the files**.

So, I guess I've been asking the wrong question; **the REAL question is, is there a workaround** for the torrent downloads that only use the r.0* files? If I randomly click on any of them and extract manually I still get the file. That's what the script is supposed to do...


If I'm not giving a good enough explanation, see the **two thumbnails** I posted. **One shows the files** in the folder I need to extract (and the extracted ISO in this case since It's a game of some sort) and **the other** thumbnail [B]shows my terminal, having gone through all the individual r.0* files to actually extract the iso.


[/B]So my script WAS working... just not exactly how I expected it to since this issue never came up in the past.

[I]Any ideas?



[/I][B]
EDITED TO ADD THIS:[/B]
Is there maybe some way to force my script to recognize the other files as a collective rar like the actual archivemanager program does? In my thumbnail earlier it showed that "filearchiver" or whatever it's called recognizes it for what it is, which enables me to extract the file I want... Any idea on how to implement that into the script, or do I have a few more years to go before I learn enough scripting to figure that one out?

---

### Post by varunendra on 2014-08-13
> **rhss6-2011 said:**
> I came to the conclusion that the one **folder where it works properly HAS a .rar file**. **When I move all 46 r.0* files** into a different folder I of course **can't extract the contents** of the rar. Likewise, **when I move the rar file I can't extract it either**.
HOWEVER,** when I have BOTH **the rar AND r.0* files in the folder together** it will extract the files**.
Exactly what I described already -
> **varunendra said:**
> ..the multi-part rar files used to be **ONE .rar file, then .r01, .r02,.... etc**....
....
To extract them, one had to right-click the first file (.rar), which would then extract all the other files automatically. If I remember correctly, one could also open/extract them via those other files (.r01, .r02.... upto .r05 or .r06) that were associated in registry as rar files, thus being recognized as rar archives.
Of course all the parts need to be in the same directory. Extraction will be failed/aborted prematurely if even one of those parts (anyone) is missing.

> **rhss6-2011 said:**
> So, I guess I've been asking the wrong question; **the REAL question is, is there a workaround** for the torrent downloads that only use the r.0* files?
The problem was already understood and possible solutions (easy and simple ones) have already been suggested by our experts -
> **papibe said:**
> You need to change the coding strategy.
....
....a possible approach would be to find '*.001' files instead of looking for rars.

> **Vaphell said:**
> i suggest trying something like *find -regextype posix-extended -iregex '.*(rar|r01|001)'*

> **rhss6-2011 said:**
> Is there maybe some way to force my script to recognize the other files as a collective rar like the actual archivemanager program does?.... Any idea on how to implement that into the script, or do I have a few more years to go before I learn enough scripting to figure that one out?
You don't need to recognize all the files as a collective .rar archive. It only needs to identify only one (any one) of them. It is then the job of the 'unrar' program to automatically detect the other parts (if they are present) and extract them to one complete file (or directory/collection of files).

As such the strategy (suggested by both experts) to look for either .rar, or .r01, or .001 and then execute the unrar command on it should work as good as right-click > extract does.

If you want the script to verify before extracting that the file it found is indeed a rar archive, you can make use of "file" command. For example -
```
if [ "$(file "$r" | grep "RAR archive")" ]; then
	unrar e -v "$r" $(dirname "$r")
fi
```

---

### Post by rhss6-2011 on 2014-08-13
Alright, well I tried a few different things, and** I found the solution** *(thanks to Vaphell for posting it)*.

All I had to use was:

```

  for r in `find -regextype posix-extended -iregex '.*(rar|r01|001|01)'`
    do
      echo "Unpacking in directory: "`dirname $r`
      unrar e -v $r `dirname $r`
    done ;;

```

and it worked just fine from there...

---

### Post by papibe on 2014-08-15
Hi again.

I believe you are having issues with spaces in both paths and filenames.

In post#3 there's a explanation on how to avoid any problem with spaces, and other special characters. This is important in the long run because you have to consider that some torrents are not originated in English speaking languages, so may even contain non ASCII characters. 

The safest approach is to use a while<<find structure like this:
```
while IFS= read -d $'\0' -r rarfile
do
    echo "Unpacking in directory: "`dirname $rarfile`
    unrar e -v "$rarfile" `dirname "$rarfile"`

done< <(find "$1" -type f -regextype posix-extended -iregex '.*\.(rar|r01|001|01)' -print0)
```
Although, I recommend taking it a little but further and use:
```
while IFS= read -d $'\0' -r rarfile
do
    unpack_dir=""${rarfile%/*}""

    echo "Unpacking in directory: $unpack_dir"
    unrar e -v "$rarfile" "$unpack_dir"

done< <(find "$1" -type f -regextype posix-extended -iregex '.*\.(rar|r01|001|01)' -print0)
```
I hope that helps. Let us know how it goes.
Regards.

P.S.: there could be a minor issue when in a single directory there's a both a 'something.rar' file, and another file called 'something.r01'. The current code would extract the content twice. I don't know how frequent that would be, but let us know if you want to tackle those cases.

---

### Post by varunendra on 2014-08-15
> **papibe said:**
> P.S.: there could be a minor issue when in a single directory there's a both a 'something.rar' file, and another file called 'something.r01'. The current code would extract the content twice. I don't know how frequent that would be, but let us know if you want to tackle those cases.

Good point, certainly going to happen with all such archives that have been compressed with older versions of WinRar.

---

### Post by rhss6-2011 on 2014-08-16
Hello there,
I haven't been able to implement the tip you gave me for my script to resolve issues with spaces since I'm always... busy... weekends doing whatever with my friends. Anyways, you mentioned how I can run into an issue with "something.rar" and "something.r01"...

Well, I actually noticed that after trying out the updatedT script to find any possible form of "rar" files to extract. Two of my folders had the file.rar within the folder - this meant that the terminal paused and gave me a menu to overwrite, skip, rename, or do something else with the files and wouldn't proceed until I addressed the situation.

Shouldn't I be able to fix that with
"**unrar e -v -o*+/-* $r `dirname $r**" - If I use the **dash** it would tell the terminal **NOT to overwrite** (but I'm not entirely sure what would happen after that) or if I use the **plus sign** it'd tell the terminal to just go ahead and **overwrite**, which I think might not be such a bad idea ultimately...

Any thoughts?

Edited to add this:

Ok, so I tried the code you gave me... and received an error...

```

     while IFS= read -d $'\0' -r rarfile
	do
    echo "Unpacking in directory: "`dirname $rarfile`
    unrar e -v "$rarfile" `dirname "$rarfile"`
    done <<(find "$1" -type f -regextype posix-extended -iregex '.*\.(rar|r01|001|01)' -print0) ;;

```

**extract.sh: 48: extract.sh: Syntax error: "(" unexpected**

What happened? All the brackets are where they belong, and have a closing bracket as well - Not sure how to deal with this one.

---

### Post by Vaphell on 2014-08-16
spaces are important here, it's not
```
<<(...)
```
it's
```
<[COLOR="#0000FF"]_[/COLOR]<(...)
```

< (redirection) + <(...) (process substitution)

---

### Post by rhss6-2011 on 2014-08-17
The problem is, when I did that I had a different error:

**extract.sh: 48: extract.sh: Syntax error: redirection unexpected**

```

     while IFS= read -d $'\0' -r rarfile
    do
    echo "Unpacking in directory: "`dirname $rarfile`
    unrar e -v "$rarfile" `dirname "$rarfile"`
    done < <(find "$1" -type f -regextype posix-extended -iregex '.*\.(rar|r01|001|01)' -print0) ;;

```

---

### Post by Vaphell on 2014-08-17
20 bucks says it's (da)sh instead of bash.

---

### Post by rhss6-2011 on 2014-08-19
Err...

What's the difference between DASH, BASH, and SH???

**Edited to add this:**

Used bash extract.sh...

and received....

**Extracting from /mnt/DATA/Downloads/01-TORRENTS/01-Downloaded/Dark Souls Prepare To Die Edition-FLT/flt-dspd.081**

**No files to extract**

So... It now RECOGNIZES the files, but won't extract them with spaces... Any ideas?

---

### Post by Vaphell on 2014-08-19
sh is barebone, bash has additional features which are convenient to use and fix many shortcomings of sh.

Why don't you echo some variables so you get to track the progress of the script and to see if the values are what you think they are. You didn't check what unrar gets exactly as the last param (quotes around embedded commands do matter).  L2debug.

Also stop using deprecated backticks ``, use $() instead.
stripping the* /filename.ext* part can be done with %/* in bash

```
echo "Unpacking in directory: '${rarfile%/*}'"
unrar e -v "$rarfile" "${rarfile%/*}"
```
or if you really have to use dirname
```

echo "Unpacking in directory: '$(dirname $rarfile )'"
unrar e -v "$rarfile" "$( dirname "$rarfile" )"
```

---

### Post by rhss6-2011 on 2014-08-22
Alright, I actually fixed it using the slightly different version that Pabibe wrote down:

```

	while IFS= read -d $'\0' -r rarfile
	do
	unpack_dir=""${rarfile%/*}""
	echo "Unpacking in directory: $unpack_dir"
    	unrar e -v "$rarfile" "$unpack_dir"
	done < <(find "$1" -type f -regextype posix-extended -iregex '.*\.(rar|r01|001|01)' -print0) ;;

```

I don't really understand what the difference is though...

---

### Post by Vaphell on 2014-08-22
the difference is there is a temporary variable that is used correctly with "" when called. Your embedded cmd was not shielded properly from breaking down to space separated pieces (i don't see the quotes around ``). The first part of my #34 post is equivalent to the solution, it just lacks that temporary var and there is a variant with embedded command in the second part, using quoted $().
What the expression does is stripping shortest rightmost '/'+anything which in case of paths would be the */<filename>*



also double double quotes do nothing. ""${}"" = open quoted string, close string, ${...}, open quoted string, close quoted string. You attach 2 empty strings to both sides which does nothing.
Either way you don't need quotes with assignment x=... if the ... part is in a single chunk.
*unpack_dir=${rarfile%/*}*
will do just fine

---

### Post by rhss6-2011 on 2014-08-22
Ok, thank you.

I appreciate the help (and lessons) you (and Pabibe) have given me - much appreciated.

---

