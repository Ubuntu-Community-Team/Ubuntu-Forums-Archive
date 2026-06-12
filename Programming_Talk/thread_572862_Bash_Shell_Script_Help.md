---
title: "Bash Shell Script Help"
date: 2007-10-10
forum: Programming Talk
---

### Post by exhume on 2007-10-10
hey everyone so I am currently trying to write a shell script to organize my rather large music collection so that inside my music folder are folders with artist names. Inside those should be album titles with the tracks for that album inside all of which should be named in the format Band_Name-Track-Song_Title.mp3. I am very close but am having a problem with the mv command. The code for my script as it is now is:

```
#!/bin/bash
i=1
if [ "$1" == "" ]
then
wd=`pwd`
else
wd="$1"
fi

cd $wd
`ls | grep .mp3 >> tmp`
count=`ls | grep .mp3 | wc -l`
while [ "$i" -le "$count" ]
do
`sed -n "$i"p tmp>> tmp2`
i=`expr $i + 1`
done
sed -e s/" "/"\\ "/g tmp2>> tmp3
i=1
while [ "$i" -le "$count" ]
do
file=`sed -n "$i"p tmp3`
`mp3info "$file">> tmp4`
i=`expr $i + 1`
done
i=1
count=`expr $count + $count + $count + $count + $count + $count`
k=1
`sed -e s/" "/"\\\ "/g tmp3 >> tmp5`
while [ "$i" -le "$count" ]
do
file=`sed -n "$k"p tmp3`
j=`expr $i + 1`
title=`sed -n "$j"p tmp4 | awk -F : '{print $2}' | sed -e s/" Track"/""/`
track=`sed -n "$j"p tmp4 | awk -F : '{print $3}'`
j=`expr $i + 2`
artist=`sed -n "$j"p tmp4 | awk -F : '{print $2}'`
j=`expr $i + 3`
album=`sed -n "$j"p tmp4 | awk -F : '{print $2}' | sed -e s/" Year"/""/`
artist=`echo $artist | sed -e s/" "/"_"/g`
mkdir ../$artist
album=`echo $album | sed -e s/" "/"_"/g`
mkdir ../$artist/$album
title=`echo $title | sed -e s/" "/"_"/g`
newfile=`echo $artist-$track-$title.mp3`
file=`ls | grep .mp3 | sed -e s/" "/"\\\ "/g | sed -n "$k"p`
echo $file ../$artist/$album/$newfile
mv $file ~/Desktop/$artist/$album/$newfile
i=`expr $i + 6`
k=`expr $k + 1`
done
rm -f tmp
rm -f tmp2
rm -f tmp3
rm -f tmp4
rm -f tmp5
```

my problem is that I cant get sed to escape spaces in the original file name with this line:
```
file=`ls | grep .mp3 | sed -e s/" "/"\\\ "/g | sed -n "$k"p`
```

The output of that line is always the same as the original ls | grep would have been. Anyone see my mistake?

---

### Post by dwhitney67 on 2007-10-11
Can you please provide a sample of the name format of your music files *prior* to being changed.  The code your wrote seems very lengthy for what might be something simple to do.

---

### Post by exhume on 2007-10-11
The length is because the script uses ID3 tags to rename and sort everything. the program i found that would input that information into the shell unfortunately does so with several things on a line which is a majority of the code. The original file names often contain spaces, which is why there is a lot of seds as well.

---

### Post by bashologist on 2007-10-11
Did you remove the indentation just for us, or did you actually write like this?
> cd $wd
USE MORE QUOTES! [http://bash-hackers.org/wiki/doku.php?id=syntax:words](http://bash-hackers.org/wiki/doku.php?id=syntax:words), [http://www.grymoire.com/Unix/Quote.html](http://www.grymoire.com/Unix/Quote.html)
> `ls | grep .mp3 >> tmp`
There's no need for backticks here.
> i=`expr $i + 1`
Alternatively you could do "((i++))".
> sed -e s/" "/"\\ "/g tmp2>> tmp3
I don't know what you're trying to do here, but you really should fix it, with some single quotes I'm guessing.
> `mp3info "$file">> tmp4`
Again, you don't need backquotes here either.
> count=`expr $count + $count + $count + $count + $count + $count`
Alternatively you could do "((count*6))".
> `sed -e s/" "/"\\\ "/g tmp3 >> tmp5`
Again, you don't need backquotes here either.
> mkdir ../$artist
USE MORE QUOTES! [http://bash-hackers.org/wiki/doku.php?id=syntax:words](http://bash-hackers.org/wiki/doku.php?id=syntax:words), [http://www.grymoire.com/Unix/Quote.html](http://www.grymoire.com/Unix/Quote.html)

---

### Post by Ramses de Norre on 2007-10-11
People are not going to spend fifteen minutes figuring out what that code does... Adopt some proper coding style (indentation, significant whitespace, ...) if you want people to read your code.

---

### Post by Jacks0n on 2007-10-12
try something like this. I haven't tried it though

```

#!/bin/bash

IFS="
"

# First argument is folder where files are
FOLDER="$1"
cd "$FOLDER"

for FILE in $(ls) ; do
     BAND="$(echo $FILE | cut -d'-' -f1)

     # If folder doesn't exist, make it.
     if [[ ! -d "${FOLDER}/${BAND}" ]]; then
          mkdir "${FOLDER}/${BAND}"
     fi

     NEW_FILENAME=$(echo $FILE | sed "s/${BAND}-/g")
     mv "$FILE" "${FOLDER}/${BAND}/${NEW_FILENAME}"
done

```

---

