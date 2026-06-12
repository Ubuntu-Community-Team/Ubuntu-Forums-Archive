---
title: "bash noob needs help"
date: 2011-03-24
forum: Programming Talk
---

### Post by Drenriza on 2011-03-24
Hi All:KS

I have a question to some code. I have a server, where i driffent folders in a path example /video1/name1/

In this /video1/name1/ i have a file 1.mpeg
their also exist
/video1/name2/
/video1/name3/
/video1/name4/
and so on, all containing a x.mpeg file.

My question is. How can i make a script that
#1 check ALL the driffent folders in the path /video1/ to see their are any x.mpeg files over 960MB
#2 IF their are any x.mpeg files over 960MB i want to execute the command ```
split -b 960m 1.mpeg
```

Hope it makes sense. 
Kind regards.

---

### Post by hakermania on 2011-03-24
```

for $i in $(ls /video1/name*/); do

if [ $(echo "scale=3; $(stat -c %s "$i")/1048576" | bc) -gt 960 ]; then #stat will give us the size and the division with 104mplampla will give it to us in MB
#your command here
split -b 960m "$i"
fi
done
```not tested but it should work

---

### Post by DaithiF on 2011-03-24
```
find video1/ -size +960M | while read file
do
   echo $file
   # whatever other commands you want here, e.g.
   # split -b 960M "$file"
done
```

---

### Post by sisco311 on 2011-03-24
Please check out: 
[http://mywiki.wooledge.org/BashPitfalls#for_i_in_.24.28ls_.2A.mp3.29](http://mywiki.wooledge.org/BashPitfalls#for_i_in_.24.28ls_.2A.mp3.29)
[http://mywiki.wooledge.org/BashFAQ/020](http://mywiki.wooledge.org/BashFAQ/020)

In this case the find command will do the trick;
```
find /path/to/dir -iname '*.mpeg' -size 960+ -execdir split -b 960M '{}' \;
```

---

### Post by Drenriza on 2011-03-25
Hi all.

Thanks for the quick answers. I will be looking into them today.
I think its great how the Ubuntu forums work. I can ask almost anything and get good and usefull answers. I have not experienced this on other forums. Mac / Windows.

So thanks again.
:KS

---

### Post by Drenriza on 2011-03-25
> **hakermania said:**
> ```

for $i in $(ls /video1/name*/); do

if [ $(echo "scale=3; $(stat -c %s "$i")/1048576" | bc) -gt 960 ]; then #stat will give us the size and the division with 104mplampla will give it to us in MB
#your command here
split -b 960m "$i"
fi
done
```not tested but it should work

Hi. I tried this code, but it says.
 
./split-movies.sh: line 10: syntax error: unexpected end of file  << this was when i changed done to exit 0
 
comp:/video1# ./split-movies.sh 
./split-movies.sh: line 9: `$i': not a valid identifier  << this was when their stood done in the end of the file

---

### Post by Drenriza on 2011-03-25
Hi guys.

It seems that 
```
find video1/ -size +960M | while read file
do
   echo $file
   # whatever other commands you want here, e.g.
   # split -b 960M "$file"
done
```
Works without a hitch. A question i have now (that i forgot to ask in post #1) is. When the split command runs. It create files called xxa.mpeg xxb.mpeg and so on, until their are no more files created and named.

How can you get the script to find and name these xxa.mpeg to 1.mpeg and xxb.mpeg to 2.mpeg and so on

xxc.mpeg to 3.mpeg
xxd.mpeg to 4.mpeg

Hope it makes sense. And thanks all.

EDIT.

Hi guys, so far you have been very helpful. And i have thought of a new question to the two i already have.

in the /video1/something/ folder their is several sub-directoryes and files.
in a file something.vod (text file) their is a line i want to delete. This line exists in the same file in every folder in /video1/something.

Can anyone tell me how a script can edit this text file, delete the line and save the file again?
I know what commands i can use to delete the correct line and save the file. The problem is, i dont know how to get a script to do it automatic for each directory in /video1/*. I only know how to manuel select each directory.

Hope it makes sense.

---

### Post by DaithiF on 2011-03-25
a couple of comments:
1. before running split you would need to cd into the same directory as the file you are splitting, otherwise the split files will get saved to the current directory, and you would end up with a mess of files from different files

2. if I'm not mistaken the output of split will be xaa, xab, xac, etc... not xxa.mpeg, xxb.mpeg, etc.
you can ask for numeric rather than alpha names with the -d parameter.  and you can change the prefix if required.  i don't think you can specify a suffix though, so you'll probably need to run a rename command after split.

so all in all, something like this:
```
find video1/ -size +960M | while read file
do
    echo "Processing $file"

    dir=${file%/*}
    filename=${file##*/}

    cd "$dir" || { echo "Could not cd to $dir, exiting"; exit 1; }

    split -b 960M -d "$filename"

    rename 's/^x(.*)/$1.mpeg/' x[0-9]*

    cd -
done

```

---

### Post by DaithiF on 2011-03-25
> **Drenriza said:**
> 
in the /video1/something/ folder their is several sub-directoryes and files.
in a file something.vod (text file) their is a line i want to delete. This line exists in the same file in every folder in /video1/something.

Can anyone tell me how a script can edit this text file, delete the line and save the file again?


```
find /video1 -type f -iname '*.vod' -exec sed -i.bak '/pattern matching line to delete/d' "{}" \;
```

should do it ... will create backup copy of files before updating ... drop the .bak if you don't want this.  try it on one file to make sure its ok before unleashing on the full population.

---

### Post by Drenriza on 2011-03-25
So this means.
If i execute
```
find video1/ -size +960M | while read file
do
    echo "Processing $file"

    dir=${file%/*}
    filename=${file##*/}

    cd "$dir" || { echo "Could not cd to $dir, exiting"; exit 1; }

    split -b 960M -d "$filename"

    rename 's/^x(.*)/$1.mpeg/' x[0-9]*

    cd -
done
``` from the /video1/ directory. Than i will end up with alot of driffent spitted files in the /video1/ directory, instead off in their respective subdirectories of /video1/?

Isint it possible to do.
#1 execute the script from /video1/
#2 the script takes the first directory in any order, contained in /video1/
#3 execute the split command
#4 rename the files
#5 cd back to /video1/ and start from 1-5 on the next directory in the order?

Im not a bash expert, so i cannot actually see if the above code does what i just suggested.

---

### Post by DaithiF on 2011-03-25
yes the code aims to do what you suggested.
e..g
before:
video1/movie1/bigfile1.mpg
video1/movie2/anotherbigfile.mpg
after:
video1/movie1/00.mpeg
video1/movie1/01.mpeg
video1/movie2/00.mpeg
video1/movie2/01.mpeg
 video1/movie2/02.mpeg

---

### Post by sisco311 on 2011-03-25
I know that backslashes and newlines aren't so common in filenames, but still the preferred method for doing this would be something like:
```
while **IFS=** read **-r -d ''** file
do
    echo "Processing $file"
    ...
done < <(find video1/ -size +960M **-print0**)
```
or
```
shopt -s globstar nullglob
for file in video/**/*.mpeg
do
    echo "$file"
done
```

---

### Post by Drenriza on 2011-03-29
Hi DaithiF.
Thanks for your script it works as intended.

I have a question / request tho :p since im totally bash noob myself.

When the script runs the line
```
rename 's/^x(.*)/$1.mpeg/' x[0-9]*
```

Is it possible to get the script to 
#1 rename the files video_1.mpeg - video_9.mpeg (instead of x00 - x09)
#2 their is an existing video_1.mpeg file (this is the one that gets splitted) so the renamed video_1.mpeg needs to overwrite the existing one. Is this possible?

Once more i thank you, for your work. And hopefully i can one day be somewhat at your level.
If you have any points tips i'm all ears.

This is something i found out, once i runned the script and saw how it worked.

Kind regards.

---

### Post by DaithiF on 2011-03-30
> **Drenriza said:**
> 
When the script runs the line
```
rename 's/^x(.*)/$1.mpeg/' x[0-9]*
```Is it possible to get the script to 
#1 rename the files video_1.mpeg - video_9.mpeg (instead of x00 - x09)
#2 their is an existing video_1.mpeg file (this is the one that gets splitted) so the renamed video_1.mpeg needs to overwrite the existing one. Is this possible?

```
rename -f 's/^x(.*)/video_$1.mpeg' x[0-9]*
```
-f will cause rename to overwrite any existing file with the destination name.

the resulting files will be video_0.mpeg, video_1.mpeg, etc, rather than starting at 1 as you wish.  To have them start at 1 would require writing your own custom renaming logic rather than relying on rename.  I don't think it would be worth the effort.

---

