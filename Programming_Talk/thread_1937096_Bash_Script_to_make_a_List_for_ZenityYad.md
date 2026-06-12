---
title: "Bash Script to make a List for Zenity/Yad"
date: 2012-03-07
forum: Programming Talk
---

### Post by Jose Catre-Vandis on 2012-03-07
Need to create a list for yad (zenity) from directory listings:

dir-a contains files 1,2,3,4,5,6

dir-b contains files a,b,c,d,e,f

Final list (in a variable) needs to read:

"1" "a" "2" "b" "3" "c" "4" "d" "5" "e" "6" "f"

( For simplicity I will always ensure that "1" goes with "a", etc.)

The list can be any length. The directories may be in different place on the drive and may contain different file types. And how could this be expanded should I want a third or fourth item in the list:

"1" "a" "@" "2" "b" "#" "3" "c" "%" - for example.

I can see a way to use "ls" to get dir contents, to export the output to a file and then do some "sorting", this is a bit slow for big lists, but can it all be done with bash ?

Thanks

---

### Post by Habitual on 2012-03-07
Sorting with bash can be done, but it is not the optimal way AFAIK.
perl is so much better for sorting lists. 

```
ls -1 A B | grep -v "A|B"
1
2
3
4
5
6

a
b
c
d
e
f

```
The unsorted list command (which you may already have)
```
yad --list --column "Files.."  --search-column 1 $(ls -1 A B | \grep -v ":")
```

I had a dialog box that sorted and listed, but I have since lost it,

I wish I had more, I used to be addicted to yad/zenity

HTH somewhat?

---

### Post by Jose Catre-Vandis on 2012-03-07
Hi Habitual, thanks for your help, but ....

The variable to be fed into the columns needs to be:

"1" "a" "2" "b" "3" "c" "4" "d" "5" "e" "6" "f"

and not

"1" "2" "3" "4" "5"  "6" "a" "b" "c" "d" "e" "f"

so

```
listing=$(function to alternate numbers and letters in dirs A & B)
echo $listing
"1" "a" "2" "b" "3" "c" "4" "d" "5" "e" "6" "f"
```

My "yad" would be something like

```
yad --list --column "Numbers" --column "Letters" $listing
```

and the dialog would look something like:

> 
Numbers__|__Letters
1________|__a______
2________|__b______
3________|__c______
4________|__d______
5________|__e______
6________|__f______

---

### Post by Habitual on 2012-03-07
OK Jose...

You're making me bust out my yad kung-fu!   :razz:

subscribed with interest...

---

### Post by Habitual on 2012-03-07
```

var1=`ls -1 ~/A`
var2=`ls -1 ~/B`

yad --list --column="Letters":TEXT "$var2" --column="Numbers":TEXT "$var1"
```I'll leave the sorting to *you*!

Reference: [http://groups.google.com/group/yad-common/browse_thread/thread/58eb6e61c357df09/53efb7a7c474f4b1?lnk=gst&q=columns#53efb7a7c474f4b1](http://groups.google.com/group/yad-common/browse_thread/thread/58eb6e61c357df09/53efb7a7c474f4b1?lnk=gst&q=columns#53efb7a7c474f4b1)

So, using your method...
listing=$(function to alternate numbers and letters in dirs A & B)
```
yad --list --column="title":TEXT $listing
```HTH!

---

### Post by Jose Catre-Vandis on 2012-03-07
For me, that just creates one big entry in the list (your thumbnail seems to indicate the same), yes it all lines up, but unable to select an individual line. I also tried the example on the yad discussion group you pointed to, and that did the same thing. :( This is a bash thing, not a yad thing ;)

Found this though:
```
var1="1.txt 2.txt 3.txt 4.txt 5.txt 6.txt"
var2="1.jpg 2.jpg 3.jpg 4.jpg 5.jpg 6.jpg"
var1="$var1 $var2"
var3=$($var1|tr " " "\n"|sort|tr "\n" " ")

```
which will properly sort two directories if the file names were the same but extensions were different. Ah, found a better one for this but may need a few entries cleaning out:```
ls -R | sort
```

Also found this, but only seems to work on files and not variables:
```
awk '{print;getline < "file1";print $0 "\n----"}' file2
```

---

