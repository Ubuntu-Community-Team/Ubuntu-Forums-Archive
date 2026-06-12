---
title: "Understanding a sed line in a bash script."
date: 2013-08-18
forum: Programming Talk
---

### Post by Erik1984 on 2013-08-18
I found a script to generate moodbars for Amarok [http://wiki.ubuntuusers.de/Moodbar#Unter-Amarok](http://wiki.ubuntuusers.de/Moodbar#Unter-Amarok). 

The complete script:
```

#!/bin/bash
control_c()        # Den Vorgang abbrechen, wenn der Nutzer Strg+c drückt
{
 echo $1 > lastreadsong
 echo "Exiting..."
 exit
}
if [ -e lastreadsong ]; then
  read filetodelete < lastreadsong
  rm "$filetodelete" lastreadsong
fi
find . -type f -regextype posix-awk -iregex '.*\.(mp3|ogg|flac|wma)' | while read i
do
  trap 'control_c "$OUTF"' SIGINT
  TEMP="${i%.*}.mood"
  OUTF=`echo "$TEMP" | sed 's#\(.*\)/\([^,]*\)#\1/.\2#'`
  if [ ! -e "$OUTF" ]; then
    moodbar -o "$OUTF" "$i"
  fi
done
```

I understand what the script does but I don't see what the sed line does exactly. This is the part I'm interested in:
```
  TEMP="${i%.*}.mood"
  OUTF=`echo "$TEMP" | sed 's#\(.*\)/\([^,]*\)#\1/.\2#'`
```

How does it work? All that seems necessary is to add a "." before the filename, other than that TEMP seems to contain the right value.

---

### Post by Vaphell on 2013-08-18
TEMP line strips shortest possible rightside (%) '.'+anything (.*) - read: extension - and adds .mood
OUTF line pipes $TEMP value to sed which splits the whole path in 2 parts with the last /, effectively cutting it to path (\1) and filename (\2) parts. Then it glues them back with /. which effectively means the filename got prefixed with .
with -r parameter the picture is clearer
sed -r 's#[COLOR="#0000FF"](.*)[/COLOR]/[COLOR="#008000"]([^,]*)[/COLOR]#[COLOR="#0000FF"]\1[/COLOR]/.[COLOR="#008000"]\2[/COLOR]#'

Why the filename part is matched by [COLOR="#0000FF"]not-[/COLOR][COLOR="#008000"]colon[/COLOR] [COLOR="#EE82EE"]any number of times[/COLOR] [[COLOR="#0000FF"]^[/COLOR][COLOR="#008000"],[/COLOR]][COLOR="#EE82EE"]*[/COLOR] - no idea.

```
$ i=/some/path/file.mp3
$ TEMP="[COLOR="#0000FF"]${i%.*}[/COLOR].mood"
$ echo "$TEMP"
[COLOR="#0000FF"]/some/path/file[/COLOR].mood
$ OUTF=$( echo "$TEMP" | sed -r 's#[COLOR="#0000FF"](.*)[/COLOR]/[COLOR="#008000"]([^,]*)[/COLOR]#[COLOR="#0000FF"]\1[/COLOR]/.[COLOR="#008000"]\2[/COLOR]#' )
$ echo "$OUTF"
[COLOR="#0000FF"]/some/path[/COLOR]/.[COLOR="#008000"]file.mood[/COLOR]
```
the same behavior in pure bash using trimming shortest rightside (%) /* pattern and longest leftside (##) */ pattern. More efficient than creating separate sed process for each file
```
$ OUTF=[COLOR="#0000FF"]${TEMP%/*}[/COLOR]/.[COLOR="#008000"]${TEMP##*/}[/COLOR]
$ echo "$OUTF"
[COLOR="#0000FF"]/some/path[/COLOR]/.[COLOR="#008000"]file.mood[/COLOR]
```

---

### Post by ofnuts on 2013-08-18
Would not that be simpler (or at least more readable)?
```

OUTF=$(dirname $i)/.$(basename $i .mp3).mood

```

---

### Post by Erik1984 on 2013-08-18
Thanks Vaphell and ofnuts! Well especially Vaphell here for the extensive explanation :)

Your solutions are a lot friendlier on the eyes ;) let's say regular expressions are not my strongest point.

@ofnuts
Your solution looks elegant but the problem is that my collection contains music with different extensions. it could be .mp3 but also .ogg .wma (one pesky folder) or .flac

---

### Post by Crusty Old Fart on 2013-08-18
> **Vaphell said:**
> ...Why the filename part is matched by [COLOR=#0000FF]not-[/COLOR][COLOR=#008000]colon[/COLOR] [COLOR=#EE82EE]any number of times[/COLOR] [[COLOR=#0000FF]^[/COLOR][COLOR=#008000],[/COLOR]][COLOR=#EE82EE]*[/COLOR] - no idea...
Well, not to be a nitpicker, but to correctly name the character for what it is, because I'll be referring to it later: it's a comma, not a colon.
The negated character class: [^,]* matches any non-comma character zero or more times. The author may know that none of his filename parts contain commas. So this allows him to match the entire filename part.
It might be argued that he could accomplish the same match by using: .* 
However, the dot metacharacter does not actually match any single character. It matches any single character EXCEPT for newline characters. In essence, the dot metacharacter in Unix regex is short for: [^\n]
So, assuming the author knows that none of his filename parts contain commas, and he wants his match to include newline characters, then the negated character class: [^,]* works for him whereas: .* does not.
(Ref.: [http://www.regular-expressions.info/dot.html](http://www.regular-expressions.info/dot.html))

Now everybody can sleep tonight :cool:

---

### Post by Vaphell on 2013-08-19
my bad, i always have trouble recalling english names of ,:; :)

---

### Post by Erik1984 on 2013-08-19
Thanks again :) I'll mark this as solved as I have successfully executed the script with Vaphells code instead of the sed line.

```

musicdir="$HOME/Music/"
find $musicdir -type f -regextype posix-awk -iregex '.*\.(mp3|ogg|flac|wma|m4a)' | while read i
do
    TEMP="${i%.*}.mood"
    OUTF=${TEMP%/*}/.${TEMP##*/}    
    if [ ! -e "$OUTF" ];
    then
        moodbar -o "$OUTF" "$i"
    fi    
done

```

---

### Post by Vaphell on 2013-08-19
home/$USER is less rocksolid than simple $HOME (you don't have to have your homedir in /home, root cerainly doesn't) but $HOME will always point to the right place)

---

### Post by Erik1984 on 2013-08-19
Thanks, changed it. :) I put $USER there to 'censor' my username which is in the script on my machine. $HOME seems a better choice to distribute the script for common use.

---

### Post by ofnuts on 2013-08-19
> **Euroman said:**
> Thanks Vaphell and ofnuts! Well especially Vaphell here for the extensive explanation :)

Your solutions are a lot friendlier on the eyes ;) let's say regular expressions are not my strongest point.

@ofnuts
Your solution looks elegant but the problem is that my collection contains music with different extensions. it could be .mp3 but also .ogg .wma (one pesky folder) or .flac

Hmmm Then technically nothing says you won't get "foo.mp3" and "foo.ogg" in the same folder, so the extension shouldn't be removed (.foo.mp3.mood).

---

### Post by Erik1984 on 2013-08-20
I am not sure that if you name the file like that, Amarok is still able to find the .mood file. Should test your suggestion on a small directory.  Technically you are right songname.mp3 and songname.ogg could exist in one directory so they would share a .mood file in the original script. So it would make sense to put .mood after the 'extension' which means nothing in Linux.

---

