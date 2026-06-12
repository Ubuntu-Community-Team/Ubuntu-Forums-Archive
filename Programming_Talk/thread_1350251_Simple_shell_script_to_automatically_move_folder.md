---
title: "Simple shell script to automatically move folder"
date: 2009-12-09
forum: Programming Talk
---

### Post by knutz on 2009-12-09
Hey everybody!

I'm in desperate (not really) need of a simple shell script that move folders, to a specific location, according to the name of the folder.

For example I want the folder "SeriesName - 3x11 - Name of episode" to be moved to "/SeriesName/Season 3/" automatically.

Does anyone know a script that can do this?


Thanks.

/knutz

---

### Post by dwhitney67 on 2009-12-09
Here's a simple script:
```

#!/bin/bash

series_name=`echo $1 | awk -F" " '{ print $1 }'`
season_num=`echo $1 | awk -F" " '{ print $3 }' | awk -F"x" '{ print $1 }'`

mkdir -p /$series_name/Season\ $season_num
mv "$1" /$series_name/Season\ $season_num

```
It takes as an command-line argument the name of the directory that you want to move.

P.S.  Per your request, the new directory is created under the '/' directory.  To do this, one requires root (sudo) privileges.  Is this really where you want to place these new directories??

P.S #2 I also assumed that the season number is yielded from the first number of "3x11".  If I am wrong, then where is the season number coming from?

---

### Post by knutz on 2009-12-09
> **dwhitney67 said:**
> Here's a simple script:
```

#!/bin/bash

series_name=`echo $1 | awk -F" " '{ print $1 }'`
season_num=`echo $1 | awk -F" " '{ print $3 }' | awk -F"x" '{ print $1 }'`

mkdir -p /$series_name/Season\ $season_num
mv "$1" /$series_name/Season\ $season_num

```
It takes as an command-line argument the name of the directory that you want to move.

P.S.  Per your request, the new directory is created under the '/' directory.  To do this, one requires root (sudo) privileges.  Is this really where you want to place these new directories??

P.S #2 I also assumed that the season number is yielded from the first number of "3x11".  If I am wrong, then where is the season number coming from?


**_Thank you very much for this._**
P.S. #1 > That was a mistake. I have a folder for it. :D 
P.S #2 > Yes you are correct.

What if the SeriesName contains a " " (space). Would this script work then? (Don't know if I am understanding it correctly)
And what if the SeriesName contains the letter x?

---

### Post by dwhitney67 on 2009-12-09
> **knutz said:**
> 
What if the SeriesName contains a " " (space). Would this script work then? (Don't know if I am understanding it correctly)

No; someone else with better bash scripting experience would have to help you with this issue.

> 
And what if the SeriesName contains the letter x?
Yes, as long as the Series Name does not contain a space.  For example, "x-files - 3x11" would work; but directories with names like "x files - 3x11" or "fu manchu - 2x5", which contain a space in the series name, would not work.

---

### Post by Rany Albeg on 2009-12-09
Just enclose arguments with double quotes.

---

### Post by dwhitney67 on 2009-12-09
> **Rany Albeg said:**
> Just enclose arguments with double quotes.

It's not that simple.

Below is a hokey solution that probably could stand to be refined:
```

#!/bin/bash

series_name=""

tmp=$1
while [ true ]
do
        tmp2=`echo $tmp | awk -F" " '{ print $1 }'`

        if [ "$tmp2" == "-" ]
        then
                break
        fi

        tmp=`echo $tmp | cut -d" " -f2-`

        if [ "$series_name" == "" ]
        then
                series_name="$tmp2"
        else
                series_name="$series_name $tmp2"
        fi
done

season_num=`echo $1 | awk -F"-" '{ print $2 }' | awk -F"x" '{ print $1 }' | awk -F" " '{ print $1 }'`

#echo "$series_name"
#echo "$season_num"

mkdir -p "$series_name"/Season\ $season_num
mv "$1" "$series_name"/Season\ $season_num

```

---

### Post by knutz on 2009-12-09
> **dwhitney67 said:**
> It's not that simple.

Below is a hokey solution that probably could stand to be refined:
```

#!/bin/bash

series_name=""

tmp=$1
while [ true ]
do
        tmp2=`echo $tmp | awk -F" " '{ print $1 }'`

        if [ "$tmp2" == "-" ]
        then
                break
        fi

        tmp=`echo $tmp | cut -d" " -f2-`

        if [ "$series_name" == "" ]
        then
                series_name="$tmp2"
        else
                series_name="$series_name $tmp2"
        fi
done

season_num=`echo $1 | awk -F"-" '{ print $2 }' | awk -F"x" '{ print $1 }' | awk -F" " '{ print $1 }'`

#echo "$series_name"
#echo "$season_num"

mkdir -p "$series_name"/Season\ $season_num
mv "$1" "$series_name"/Season\ $season_num

```

This works! 

Thank you very much!!
I sure hope this can be helpful to others as well.


THANKS!

/knutz

---

### Post by knutz on 2009-12-09
How do i run the script as root?
When i try to run it, it goes bananas..

---

### Post by mo.reina on 2009-12-09
> **dwhitney67 said:**
> Here's a simple script:
```

#!/bin/bash

series_name=`echo $1 | awk -F" " '{ print $1 }'`
season_num=`echo $1 | awk -F" " '{ print $3 }' | awk -F"x" '{ print $1 }'`

mkdir -p /$series_name/Season\ $season_num
mv "$1" /$series_name/Season\ $season_num

```
It takes as an command-line argument the name of the directory that you want to move.

P.S.  Per your request, the new directory is created under the '/' directory.  To do this, one requires root (sudo) privileges.  Is this really where you want to place these new directories??

P.S #2 I also assumed that the season number is yielded from the first number of "3x11".  If I am wrong, then where is the season number coming from?

if the filename has a space, just use "-" as the delimiter

```
series_name=`echo $1 | awk -F"-" '{ print $1 }'`
```

---

### Post by dwhitney67 on 2009-12-09
> **mo.reina said:**
> if the filename has a space, just use "-" as the delimiter

```
series_name=`echo $1 | awk -F"-" '{ print $1 }'`
```

How does one then remove the space at the end of the resulting 'series_name'?

If the file has the format of "foo foo - 3x11", and I use the statement you have shown above, the resulting 'series_name' is "foo foo " (note the trailing white-space).

P.S.  I ask the simple question above because, believe it or not, earlier today I thought of the suggestion you offered, and naturally I encountered a problem with it.

---

### Post by mo.reina on 2009-12-09
> **dwhitney67 said:**
> How does one then remove the space at the end of the resulting 'series_name'?

If the file has the format of "foo foo - 3x11", and I use the statement you have shown above, the resulting 'series_name' is "foo foo " (note the trailing white-space).

P.S.  I ask the simple question above because, believe it or not, earlier today I thought of the suggestion you offered, and naturally I encountered a problem with it.

have you tried sed?

```
series_name=`echo $1 | awk -F"-" '{ print $1 }' | sed 's/ $//'`
```

or awk

```
series_name=`echo $1 | awk -F"-" '{ print $1 }' | awk '{ sub(/ $/, ""); print }'
```

i'm sure this can be done with only one pipe, but i'm not quite sure how....

---

### Post by dwhitney67 on 2009-12-09
Ok, that works!  I learn something new everyday.  :-)

---

### Post by knutz on 2009-12-09
So how is that implemented into the script? :)
And can i run that as root?

Thanks.

/knutz

---

### Post by dwhitney67 on 2009-12-09
> **knutz said:**
> So how is that implemented into the script? :)
And can i run that as root?

Thanks.

/knutz

```

#!/bin/bash

# change DEST to be the root-directory
# where you want your new folders created.
DEST="/"

series_name=`echo $1 | awk -F"-" '{ print $1 }' | sed 's/ $//'`
season_num=`echo $1 | awk -F"-" '{ print $2 }' | awk -F"x" '{ print $1 }' | awk -F" " '{ print $1 }'`

mkdir -p "$DEST/$series_name/Season $season_num"
mv "$1" "$DEST/$series_name/Season $season_num"

```
To run the script as root, use sudo.  For example:
```

sudo scriptName <folder>

```

---

### Post by knutz on 2009-12-09
> **dwhitney67 said:**
> ```

#!/bin/bash

# change DEST to be the root-directory
# where you want your new folders created.
DEST="/"

series_name=`echo $1 | awk -F"-" '{ print $1 }' | sed 's/ $//'`
season_num=`echo $1 | awk -F"-" '{ print $2 }' | awk -F"x" '{ print $1 }' | awk -F" " '{ print $1 }'`

mkdir -p "$DEST/$series_name/Season $season_num"
mv "$1" "$DEST/$series_name/Season $season_num"

```
To run the script as root, use sudo.  For example:
```

sudo scriptName

```

Now this works!

Thank you VERY much!!

/knutz

---

