---
title: "help need to rename files in order via bash"
date: 2009-04-05
forum: Programming Talk
---

### Post by shane2peru on 2009-04-05
Ok, I'm working on a large project and want to automate it via a bash script to simplify this.  I have a bunch of directories full of tif files that were scanned out of old books.  I want to convert them to pdf files, so I have scripted out all of that.  However I ran into a bump because some of the files have been named in this as an example:
```

hif_033.tif
hif_034.tif
hif_035.tif
hif_035[COLOR="Red"]a[/COLOR].tif
hif_036.tif

```
It is that a, and b and c that are giving me problems.  So when I run ```

convert -monitor -density 480 *_03*.tif +adjoin 03%01d.pdf
``` in my bash script, it puts the hif_035a(or b or c).tif into a different order than it should be.  So I need to rename only those files to something that imagemagick will keep them in order.  I have tried a few different names like```
hif_035.1.tif
``` and imagemagick still grossly puts this in a different order.  Here is the script I'm working with: 
([COLOR="Red"]Warning view at your own risk, the bad coding may hurt your eyes.[/COLOR]) :D
```

#!/bin/bash
rm -fv *.pdf
read -p "What is the name of the book?  :" NAME
# Here we are going to rename all the tif files with letters in them to put them in the proper order, this is done in three stages
#first replace
illegal=a
replace=.1

for i in $( ls *$illegal* );
do
src=$i
tgt=$(echo $i | sed -e "s/$illegal/$replace/")
mv $src $tgt
done
#second replace
illegal=b
replace=.2

for i in $( ls *$illegal* );
do
src=$i
tgt=$(echo $i | sed -e "s/$illegal/$replace/")
mv $src $tgt
done
#Third replace
illegal=c
replace=.3

for i in $( ls *$illegal* );
do
src=$i
tgt=$(echo $i | sed -e "s/$illegal/$replace/")
mv $src $tgt
done
#now
convert -monitor -density 480 *_00*.tif +adjoin 00%01d.pdf
convert -monitor -density 480 *_01*.tif +adjoin 01%01d.pdf
convert -monitor -density 480 *_02*.tif +adjoin 02%01d.pdf
convert -monitor -density 480 *_03*.tif +adjoin 03%01d.pdf
convert -monitor -density 480 *_04*.tif +adjoin 04%01d.pdf
convert -monitor -density 480 *_05*.tif +adjoin 05%01d.pdf
convert -monitor -density 480 *_06*.tif +adjoin 06%01d.pdf
convert -monitor -density 480 *_07*.tif +adjoin 07%01d.pdf
convert -monitor -density 480 *_08*.tif +adjoin 08%01d.pdf
convert -monitor -density 480 *_09*.tif +adjoin 09%01d.pdf
convert -monitor -density 480 *_10*.tif +adjoin 10%01d.pdf
convert -monitor -density 480 *_11*.tif +adjoin 11%01d.pdf
convert -monitor -density 480 *_12*.tif +adjoin 12%01d.pdf
convert -monitor -density 480 *_13*.tif +adjoin 13%01d.pdf
convert -monitor -density 480 *_14*.tif +adjoin 14%01d.pdf
convert -monitor -density 480 *_15*.tif +adjoin 15%01d.pdf
convert -monitor -density 480 *_16*.tif +adjoin 16%01d.pdf
convert -monitor -density 480 *_17*.tif +adjoin 17%01d.pdf
convert -monitor -density 480 *_18*.tif +adjoin 18%01d.pdf
convert -monitor -density 480 *_19*.tif +adjoin 19%01d.pdf
convert -monitor -density 480 *_20*.tif +adjoin 20%01d.pdf
convert -monitor -density 480 *_21*.tif +adjoin 21%01d.pdf
convert -monitor -density 480 *_22*.tif +adjoin 22%01d.pdf
convert -monitor -density 480 *_23*.tif +adjoin 23%01d.pdf
convert -monitor -density 480 *_24*.tif +adjoin 24%01d.pdf
convert -monitor -density 480 *_25*.tif +adjoin 25%01d.pdf
convert -monitor -density 480 *_26*.tif +adjoin 26%01d.pdf
convert -monitor -density 480 *_27*.tif +adjoin 27%01d.pdf
convert -monitor -density 480 *_28*.tif +adjoin 28%01d.pdf
convert -monitor -density 480 *_29*.tif +adjoin 29%01d.pdf
convert -monitor -density 480 *_30*.tif +adjoin 30%01d.pdf
convert -monitor -density 480 *_31*.tif +adjoin 31%01d.pdf
convert -monitor -density 480 *_32*.tif +adjoin 32%01d.pdf
convert -monitor -density 480 *_33*.tif +adjoin 33%01d.pdf
convert -monitor -density 480 *_34*.tif +adjoin 34%01d.pdf
convert -monitor -density 480 *_35*.tif +adjoin 35%01d.pdf
convert -monitor -density 480 *_36*.tif +adjoin 36%01d.pdf
convert -monitor -density 480 *_37*.tif +adjoin 37%01d.pdf
convert -monitor -density 480 *_38*.tif +adjoin 38%01d.pdf
convert -monitor -density 480 *_39*.tif +adjoin 39%01d.pdf
convert -monitor -density 480 *_40*.tif +adjoin 40%01d.pdf
convert -monitor -density 480 *_41*.tif +adjoin 41%01d.pdf
convert -monitor -density 480 *_42*.tif +adjoin 42%01d.pdf
convert -monitor -density 480 *_43*.tif +adjoin 43%01d.pdf
convert -monitor -density 480 *_44*.tif +adjoin 44%01d.pdf
convert -monitor -density 480 *_45*.tif +adjoin 45%01d.pdf
convert -monitor -density 480 *_46*.tif +adjoin 46%01d.pdf
convert -monitor -density 480 *_47*.tif +adjoin 47%01d.pdf
convert -monitor -density 480 *_48*.tif +adjoin 48%01d.pdf
convert -monitor -density 480 *_49*.tif +adjoin 49%01d.pdf
pdftk *.pdf cat output $NAME.pdf
cp $NAME.pdf ../
rm -frv *.pdf
exit

```
ps. I set this up to only do 10 at a time because imagemagick will load all of them into memory before converting them, which brings my system to it's knees.  Any help would greatly be appreciated!

Shane

---

### Post by ghostdog74 on 2009-04-05
check if convert has options for "appending" or adding files. then use a loop to go through each file, appending each one as the loop goes.

---

### Post by kaibob on 2009-04-05
Deleted by Kaibob. My proposed solution would overwrite existing files.

---

### Post by shane2peru on 2009-04-05
> **ghostdog74 said:**
> check if convert has options for "appending" or adding files. then use a loop to go through each file, appending each one as the loop goes.

hmm, I'm not 100% sure I understand.  But I think I need to change these names before convert gets a hold of them so they will be in the right order before being converted.  If you leave an example I'm pretty good at deciphering examples.

Shane

---

### Post by shane2peru on 2009-04-06
Ok, the real problem is that the 0030.tif file should come after the 0030a.tif file and it will not render them in that order because there is extra stuff after the number, so I have tried with numerous renaming bash things to no avail.  The name must be changed so that the a is removed from the one name and put on the other name, or something of that nature.  Course it could be an a, or b or c is what I have seen so far that would all need to be manipulated.  Any help would be appreciated.  Thanks!

Shane

---

### Post by kaibob on 2009-04-06
> **shane2peru said:**
> Ok, the real problem is that the 0030.tif file should come after the 0030a.tif file and it will not render them in that order because there is extra stuff after the number, so I have tried with numerous renaming bash things to no avail....

Isn't that the default sort order? For example:

> kaibob@dell:~/temp$ ls -l
-rw-r--r-- 1 bob bob 0 2009-04-05 21:59 hif_029.tif
-rw-r--r-- 1 bob bob 0 2009-04-05 21:59 hif_030a.tif
-rw-r--r-- 1 bob bob 0 2009-04-05 21:59 hif_030.tif
-rw-r--r-- 1 bob bob 0 2009-04-05 21:59 hif_031.tif

---

### Post by Arndt on 2009-04-06
> **kaibob said:**
> Isn't that the default sort order? For example:

(To kaibob: if you include your block text in 'quote' tags, they will not show up when somebody quotes your message, it seems, like now. With 'code' tags, I think they would.)

The environment variable LC_COLLATE affects matters:

```
$ LC_COLLATE=C ls
f029.tif  f030.tif  f030a.tif  f031.tif
```

```
$ LC_COLLATE= ls
f029.tif  f030a.tif  f030.tif  f031.tif
```

---

### Post by shane2peru on 2009-04-06
> **Arndt said:**
> (To kaibob: if you include your block text in 'quote' tags, they will not show up when somebody quotes your message, it seems, like now. With 'code' tags, I think they would.)

The environment variable LC_COLLATE affects matters:

```
$ LC_COLLATE=C ls
f029.tif  f030.tif  f030a.tif  f031.tif
```

```
$ LC_COLLATE= ls
f029.tif  f030a.tif  f030.tif  f031.tif
```

Ok, that seems to work, except I'm not 100% sure how to incorporate that into my script.  Here is the best renaming script I came up with after scouring the web:

```

#!/bin/bash
x=1
for fname in *.tif
do
mv $fname `printf "%04d.tif" $x`
x=$(($x+1))
done

```
Is there a way to incorporate the LC_COLLATE=   into this part of the script?  Thanks for the input!  It is greatly appreciated.

Shane

PS course after that I will have to change my convert line to read it by 10's but that isn't a big deal.

---

### Post by Arndt on 2009-04-06
> **shane2peru said:**
> Ok, that seems to work, except I'm not 100% sure how to incorporate that into my script.  Here is the best renaming script I came up with after scouring the web:

```

#!/bin/bash
x=1
for fname in *.tif
do
mv $fname `printf "%04d.tif" $x`
x=$(($x+1))
done

```
Is there a way to incorporate the LC_COLLATE=   into this part of the script?  Thanks for the input!  It is greatly appreciated.

Shane

PS course after that I will have to change my convert line to read it by 10's but that isn't a big deal.

Just export it first thing in the script (it won't affect other than the script itself, since scripts are run in a shell process of their own):

```

#!/bin/bash
export LC_COLLATE=C
x=1
...

```

I thought it was the LC_COLLATE=C effect you wanted, but no doubt you know best. Is LC_COLLATE defined already in your shell?

I think what the other (default) sort order does is this: it sorts according to letters and digits first, and then, if two strings are deemed equal, it looks at separators, like periods and underscore. (If the locale is for example French, it does even more complex things with letters with accents.)

Another way to change the order according to this analysis (which may be faulty - I tried to look it up, but find it strangely difficult to find) is to change the placement of the 'a' compared to the 't' of "tif", so to speak. If I rename hif_035a.tif to hif_035za.tif, it will be sorted after hif_035.tif, regardless of LC_COLLATE.

---

### Post by shane2peru on 2009-04-06
> **Arndt said:**
> 
Another way to change the order according to this analysis (which may be faulty - I tried to look it up, but find it strangely difficult to find) is to change the placement of the 'a' compared to the 't' of "tif", so to speak. If I rename hif_035a.tif to hif_035za.tif, it will be sorted after hif_035.tif, regardless of LC_COLLATE.

This was the key!!!  renaming the file to hif_035az.tif worked!!!  :popcorn:   Thank you a bunch, that is super easy to incorporate into my script and everything will come out great!  Thanks a bundle!!

Shane

---

