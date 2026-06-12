---
title: "Too many files in folder"
date: 2012-09-01
forum: New to Ubuntu
---

### Post by ricardisimo on 2012-09-01
Hey there all. I have a folder with about 165,000 largish images, and sadly nautilus and any other app that I try to use gets so hung up trying to catalog all of the contents that I can't select one or several for editing or batch editing. They are all named sequentially, 000001.jpg, 000002.jpg, etc.

So my question is, how do I cut and paste into a separate folder manageable numbers of them from the command line? Let's suppose they are in /home/ricardisimo/Pictures/JPEG right now. Thanks in advance.

---

### Post by squenson on 2012-09-01
I am sure that it is possible to automate my solution but it should not take too long anyway.

Open a terminal session: Ctrl-Alt-T
Go to the folder where all the images are: cd /home/ricardisimo/Pictures/JPEG
Create a subfolder 00: mkdir 00
Repeat the command 16 times with 01, 02, ..., 16
Move the files to the first folder: mv 00*.jpg 00/
Repeat 16 times: mv 01*.jpg 01/    ...    mv 16*.jpg 16/

Now, you have 17 folders with maximum 10,000 files in each.

---

### Post by Lyfang on 2012-10-15
You could file a bug report, open up a terminal and run the following command (Launchpad account needed):
```
ubuntu-bug nautilus
```

---

### Post by Pletched on 2012-10-15
I'm curious, 165,000 files you say. How did you get that many in one folder in the first place?

---

### Post by jerrrys on 2012-10-15
Untried by me, but you may find it interesting.

[http://ubuntuforums.org/showthread.php?t=976447](http://ubuntuforums.org/showthread.php?t=976447)

---

### Post by papibe on 2012-10-15
Hi ricardisimo.

I've faced a similar situation and both squenson's, and jerrrys' link will work somehow.

I initially started as squenson's (manually), and then I used something like jerrrys' (guessing a directory size).

My problem was that the responsiveness of nautilus is not dependant of the number of files exclusively, but also how fast/powerful your machine is.

Finally, I took another approach. Divide by 2 the number of directories each time, until nautilus works acceptable.

Here's how it works:
```
$ l -R
.:
001-100/  divider.sh*  recreate.sh*

./001-100:
001.jpeg  014.jpeg  027.jpeg  040.jpeg  053.jpeg  066.jpeg  079.jpeg  092.jpeg
002.jpeg  015.jpeg  028.jpeg  041.jpeg  054.jpeg  067.jpeg  080.jpeg  093.jpeg
003.jpeg  016.jpeg  029.jpeg  042.jpeg  055.jpeg  068.jpeg  081.jpeg  094.jpeg
004.jpeg  017.jpeg  030.jpeg  043.jpeg  056.jpeg  069.jpeg  082.jpeg  095.jpeg
005.jpeg  018.jpeg  031.jpeg  044.jpeg  057.jpeg  070.jpeg  083.jpeg  096.jpeg
006.jpeg  019.jpeg  032.jpeg  045.jpeg  058.jpeg  071.jpeg  084.jpeg  097.jpeg
007.jpeg  020.jpeg  033.jpeg  046.jpeg  059.jpeg  072.jpeg  085.jpeg  098.jpeg
008.jpeg  021.jpeg  034.jpeg  047.jpeg  060.jpeg  073.jpeg  086.jpeg  099.jpeg
009.jpeg  022.jpeg  035.jpeg  048.jpeg  061.jpeg  074.jpeg  087.jpeg  100.jpeg
010.jpeg  023.jpeg  036.jpeg  049.jpeg  062.jpeg  075.jpeg  088.jpeg
011.jpeg  024.jpeg  037.jpeg  050.jpeg  063.jpeg  076.jpeg  089.jpeg
012.jpeg  025.jpeg  038.jpeg  051.jpeg  064.jpeg  077.jpeg  090.jpeg
013.jpeg  026.jpeg  039.jpeg  052.jpeg  065.jpeg  078.jpeg  091.jpeg
[COLOR="Red"]**$ ./divider.sh **[/COLOR]
$ l -R
.:
001-50/  51-100/  divider.sh*  recreate.sh*

./001-50:
001.jpeg  008.jpeg  015.jpeg  022.jpeg  029.jpeg  036.jpeg  043.jpeg  050.jpeg
002.jpeg  009.jpeg  016.jpeg  023.jpeg  030.jpeg  037.jpeg  044.jpeg
003.jpeg  010.jpeg  017.jpeg  024.jpeg  031.jpeg  038.jpeg  045.jpeg
004.jpeg  011.jpeg  018.jpeg  025.jpeg  032.jpeg  039.jpeg  046.jpeg
005.jpeg  012.jpeg  019.jpeg  026.jpeg  033.jpeg  040.jpeg  047.jpeg
006.jpeg  013.jpeg  020.jpeg  027.jpeg  034.jpeg  041.jpeg  048.jpeg
007.jpeg  014.jpeg  021.jpeg  028.jpeg  035.jpeg  042.jpeg  049.jpeg

./51-100:
051.jpeg  058.jpeg  065.jpeg  072.jpeg  079.jpeg  086.jpeg  093.jpeg  100.jpeg
052.jpeg  059.jpeg  066.jpeg  073.jpeg  080.jpeg  087.jpeg  094.jpeg
053.jpeg  060.jpeg  067.jpeg  074.jpeg  081.jpeg  088.jpeg  095.jpeg
054.jpeg  061.jpeg  068.jpeg  075.jpeg  082.jpeg  089.jpeg  096.jpeg
055.jpeg  062.jpeg  069.jpeg  076.jpeg  083.jpeg  090.jpeg  097.jpeg
056.jpeg  063.jpeg  070.jpeg  077.jpeg  084.jpeg  091.jpeg  098.jpeg
057.jpeg  064.jpeg  071.jpeg  078.jpeg  085.jpeg  092.jpeg  099.jpeg
[COLOR="Red"]**$ ./divider.sh **[/COLOR]
$ l -R
.:
001-25/  26-50/  51-75/  76-100/  divider.sh*  recreate.sh*

./001-25:
001.jpeg  005.jpeg  009.jpeg  013.jpeg  017.jpeg  021.jpeg  025.jpeg
002.jpeg  006.jpeg  010.jpeg  014.jpeg  018.jpeg  022.jpeg
003.jpeg  007.jpeg  011.jpeg  015.jpeg  019.jpeg  023.jpeg
004.jpeg  008.jpeg  012.jpeg  016.jpeg  020.jpeg  024.jpeg

./26-50:
026.jpeg  030.jpeg  034.jpeg  038.jpeg  042.jpeg  046.jpeg  050.jpeg
027.jpeg  031.jpeg  035.jpeg  039.jpeg  043.jpeg  047.jpeg
028.jpeg  032.jpeg  036.jpeg  040.jpeg  044.jpeg  048.jpeg
029.jpeg  033.jpeg  037.jpeg  041.jpeg  045.jpeg  049.jpeg

./51-75:
051.jpeg  055.jpeg  059.jpeg  063.jpeg  067.jpeg  071.jpeg  075.jpeg
052.jpeg  056.jpeg  060.jpeg  064.jpeg  068.jpeg  072.jpeg
053.jpeg  057.jpeg  061.jpeg  065.jpeg  069.jpeg  073.jpeg
054.jpeg  058.jpeg  062.jpeg  066.jpeg  070.jpeg  074.jpeg

./76-100:
076.jpeg  080.jpeg  084.jpeg  088.jpeg  092.jpeg  096.jpeg  100.jpeg
077.jpeg  081.jpeg  085.jpeg  089.jpeg  093.jpeg  097.jpeg
078.jpeg  082.jpeg  086.jpeg  090.jpeg  094.jpeg  098.jpeg
079.jpeg  083.jpeg  087.jpeg  091.jpeg  095.jpeg  099.jpeg

```
etc.

Here's the code:
```
#!/bin/bash

# Globals
# digits necesary to represent sequence
DIGITS="03"         # e.g., 001 - 100 needs 3 digits.

# files extention
EXTENSION=".jpeg"

# for each directory
while IFS= read -d '' dir; do

    # equivalent of basename
    clean_name=${dir##*/}

    # get first and last name from dirname
    first=${clean_name%-*}
    last=${clean_name#*-}

    # calculate half of the range
    half=$((($first+$last)/2))

    # create 2 new ranges

    # lower range
    lower_first="$first"
    lower_last="$half"

    # upper range
    upper_first=$(($half+1))
    upper_last="$last"

    # new directory names
    lower_dir="$lower_first-$lower_last"
    upper_dir="$upper_first-$upper_last"

    # renaming old directory to lower_dir
    mv -i "$dir" "$lower_dir"

    # creating upper_dir
    mkdir "$upper_dir"

    for count in $(seq -f "%""$DIGITS"".f" "$upper_first" "$upper_last"); do
        mv -i "$lower_dir"/"$count""$EXTENSION"  "$upper_dir"
    done

done< <(find -mindepth 1 -maxdepth 1 -type d -print0)
```
Hope it helps. Let us know how it goes.
Regards.

---

