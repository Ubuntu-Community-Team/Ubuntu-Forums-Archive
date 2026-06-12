---
title: "Renaming a batch of files"
date: 2013-09-18
forum: Programming Talk
---

### Post by alfirdaous on 2013-09-18
Good day to you,

I would like to rename a batch of files using command line:

```

00001-fqAQHelS.mp4
00002-cKIaSnn1.mp4
00003-d6lha9ys.mp4
00004-eUyAzS7x.mp4
00005-nVFSjsiW.mp4
..
00010-ffdsfselS.mp4
00011-fqAQHelS.mp4
00012-cKIaSnn1.mp4
00013-d6lha9ys.mp4
00014-eUyAzS7x.mp4
00015-nVFSjsiW.mp4

```

Some files have 4 zeros at the begining (0001) and some 3 (00010), then 2 (00100),.. my command line is:

```

N=1; for i in *.mp4; do echo $i title_$[N+1].mp4; N=$[N+1]; done

```

The output is something like:

```

title_2.mp4
title_3.mp4
..
title_10.mp4
title_11.mp4
title_12.mp4

```

How can I keep the same number of zeros as the first ones:

```

title_00002.mp4
title_00003.mp4
..
title_00010.mp4
title_00011.mp4
title_00012.mp4

```
 so number of digits (5) will remain the same??

Thanks in advance

---

### Post by steeldriver on 2013-09-18
If you are set on using your current loop solution, you could use printf to create the new name with a zero-padded number i.e. (simple illustration)

```
$ n=1; for i in {1..10}; do printf -v newname "title_%05d" $((i++)); echo "$newname"; done
title_00001
title_00002
title_00003
title_00004
title_00005
title_00006
title_00007
title_00008
title_00009
title_00010

```

However you could just use the perl-based 'rename' command to substitute the original numbering e.g.

```
$ rename -vn 's/(\d+)-[^.]*/title_$1/' *.mp4
00010-ffdsfselS.mp4 renamed as title_00010.mp4
00011-fqAQHelS.mp4 renamed as title_00011.mp4
00012-cKIaSnn1.mp4 renamed as title_00012.mp4
00013-d6lha9ys.mp4 renamed as title_00013.mp4
00014-eUyAzS7x.mp4 renamed as title_00014.mp4
00015-nVFSjsiW.mp4 renamed as title_00015.mp4

```

---

### Post by TheFu on 2013-09-18
There is a regex rename tool already ... called **rename**.
**rename 's/[-].*$/.mp4/g' *mp4**
will remove the - to the end.

Then **rename 's/^/title_/g' *mp4**
will insert the beginning.

Clear as mud?  BTW, I didn't test this, but I use rename ALL_THE_TIME.

Now, if you WANT to retain your method, we need to know which scripting language are you using.

I like steeldrivers answer better. I didn't remember the use of substitutions off the top of my head. Pretty slick, huh?

---

### Post by papibe on 2013-09-18
**EDIT: this solves your sequence output, but not your renaming problem.**

Hi alfirdaous.

You can use 'seq' to generate your number's sequence. For instance:
```
$ for n in $(seq 10); do echo $n; done
1
2
3
4
5
6
7
8
9
10

```
If you set a format you can keep all number with the same amount of digits and proper padding zeros:
```
$ for n in $(seq -f "%02.0f" 10); do echo $n; done
01
02
03
04
05
06
07
08
09
10
```
In your case you'd need something like "%05.0f"

Hope it helps. Let us know how it goes.
Regards.

---

### Post by steeldriver on 2013-09-18
Just for completeness, the built-in bash sequence generator will pad field widths as well i.e.

```

$ for i in {0006..0012}; do echo $i; done
0006
0007
0008
0009
0010
0011
0012

```

---

### Post by alfirdaous on 2013-09-18
> **steeldriver said:**
> If you are set on using your current loop solution, you could use printf to create the new name with a zero-padded number i.e. (simple illustration)


Thanks in advance, I did not get the printf way

> **TheFu said:**
> There is a regex rename tool already ... called **rename**.


In this case I need to use 2 commands line

> **papibe said:**
> [B]
EDIT: this solves your sequence output, but not your renaming problem.[/B]


I liked the code, quite simple, but still don't understand the printf

Another thing, If I would like to increment the names, for exemple:

0001 ==> 0005
0002 ==> 0006
0003 ==> 0007

and so on

---

### Post by steeldriver on 2013-09-18
Well you basically have 3 approaches available to you

[LIST=1]
[*](as per your original post) loop over the *.mp4 files using a shell glob, and separately increment a counter that will form the basis of the new file name. In that case, if you want the number to have a particular format, you can do that using 'printf'. The bash printf builtin is usually used to write formatted output to the terminal, but the optional form 'printf -v *var* ... ' allows you to write it to shell variable *var*, which you can use in your script. Type 'help printf' at the bash prompt for more info. 
[*]you can create a suitable numeric sequence in the desired (zero padded) format using either 'seq -f' or like 'for n in {00000...00199}', and then look for a file with that number in its name, and rename it 
[*]you can use rename (or sed) to create the new name from the old name by *substitution* 
[/LIST]

---

### Post by Vaphell on 2013-09-19
printf is a classic command/function used in many languages. Format string has % placeholders in which values of provided parameters are put. %05d is a placeholder that means 0-padded 5 digits wide decimal number, so eg
```
i=5; printf "filename-[COLOR="#0000CD"]%05d[/COLOR]" [COLOR="#0000CD"]$i[/COLOR]
```
will produce "filename-00005" string. optionally *-v variable* stores the result in *variable*

and if you want to shift numbers, rename is out of question - regular expressions rock but they don't know concept of math (it's all characters)
Assuming transition from 99999-garbage.mp4 to title_99999.mp4, you'd need something like 
```
for f in *.mp4; do n=${f%%-*}; n=$(( 10#$n+4 )); mv "$f" "$( printf "title_%05d.mp4" "$n" )"; done
```
n=${f%%-*} = strip rightside '-'+anything from filename, leaving the digits
n=$(( 10#$n+4 ))   =  by default leading 0s suggest octal number, so 10# makes sure it is considered decimal, add 4.

but be warned - if you want to change numbers by adding N but preserve the filename format you need to be careful. Going in ascending order means overwriting files with higher indices ( file-0001 becomes file-0005 overwriting old file-0005 before it gets processed), you need to go in descending order or use temporary format to avoid naming collisions

---

### Post by GrouchyGaijin on 2013-09-19
This is pretty cool, although I don't understand how it works.
For a long time I've been wanting to be able to batch rename photos from the command line.

If I have a bunch of photos with names of various lengths and ending in .jpg or .JPG,
how could I rename the entire batch to something like September-19-2013-1.jpg September-19-2013-2.jpg etc?

---

### Post by Vaphell on 2013-09-19
does order or any part of original filenames matter?
if not you simply do something like

```
i=1; for f in *.[jJ][pP][gG]; do mv -- "$f" "$( printf "September-19-2013-%04d.jpg" $i )"; ((i++)); done
```
printf is only for 0-padding so if you dont need it you can simply use plain "September-19-2013-**$i**.jpg" instead
how it works: take all files matching given glob and rename them in loop to format with $counter plugged in, increment $counter after each file

```
$ ls
garbage.jpg  something.JPG  trolololo.JPG
$ i=1; for f in *.[jJ][pP][gG]; do mv -- "$f" "$( printf "September-19-2013-%04d.jpg" $i )"; ((i++)); done
$ ls
September-19-2013-0001.jpg  September-19-2013-0002.jpg  September-19-2013-0003.jpg
```

---

### Post by GrouchyGaijin on 2013-09-19
SWEET - I've been wondering how to do this for a long time!

---

### Post by CaptainMark on 2013-09-19
And the search continues for a bash question that Vaphell can't answer, can it be done? Probably not.....

---

### Post by GrouchyGaijin on 2013-09-19
One more question (I feel like Colombo, if you remember that old show), how could I have the file renamed automatically to today's date?
I tried inserting $date and that caused an error.

---

### Post by Vaphell on 2013-09-19
> And the search continues for a bash question that Vaphell can't answer, can it be done? Probably not..... 

of course it can, eg hacks dependent on switching stdin, stdout, stderr around :)

---

### Post by GrouchyGaijin on 2013-09-19
No Mark I don't think it can.  He IS a wizard and we all benefit!

---

### Post by Vaphell on 2013-09-19
> One more question (I feel like Colombo, if you remember that old show), how could I have the file renamed automatically to today's date?
I tried inserting $date and that caused an error. 

"**$( date +%B-%d-%Y )**-%04d.jpg"

---

### Post by GrouchyGaijin on 2013-09-19
Thank you.  Once again you have made my life a bit easier.

---

### Post by alfirdaous on 2013-09-19
In my case, I think something like the below one will do the job:

```

N=1; for i in {00001..00012}; do echo title_$i.mp4; N=$[N+1]; done

```

but to make it increment by 5 does NOT work, did not get it yet

---

### Post by Vaphell on 2013-09-19
```
format="title_%05d.mp4"; for i in {12..1}; do [COLOR="#808080"]echo[/COLOR] mv "$( printf "$format" "$i" )" "$( printf "$format" "$((i+5))" )"; done
mv title_00012.mp4 title_00017.mp4
mv title_00011.mp4 title_00016.mp4
mv title_00010.mp4 title_00015.mp4
mv title_00009.mp4 title_00014.mp4
mv title_00008.mp4 title_00013.mp4
mv title_00007.mp4 title_00012.mp4
mv title_00006.mp4 title_00011.mp4
mv title_00005.mp4 title_00010.mp4
mv title_00004.mp4 title_00009.mp4
mv title_00003.mp4 title_00008.mp4
mv title_00002.mp4 title_00007.mp4
mv title_00001.mp4 title_00006.mp4
```

---

### Post by alfirdaous on 2013-09-19
Oh thanks for everybody, I think we cannot do it at one command line

---

### Post by GrouchyGaijin on 2013-10-05
For what it is worth, here is a little script to make it [COLOR=#0000ff]*slightly*[/COLOR] easier:


```


#!/bin/bash 
#By GrouchyGaijin
# Hard part (lines 15 and 21) by Vaphell
#Last Updated: 04-Oct-2013 (Friday - yes see what I do on Firday nights) @ 23:37
#Put this in path and call it by typing batchrename in the terminal
#Version 0.3
echo "This script is for batch renaming files."
read -p "Enter the path to the folder containing the files. " path
cd $path
read -p "Enter the file extension. " extension
echo "Press N if you want to use a new name or D if you want to use the date"
read x 
if [ "$x" = "D" ]
then
i=1; for f in *; do mv -- "$f" "$( printf "$( date +%d-%b-%Y )-%04d.$extension" $i )"; ((i++)); done
fi


if [ "$x" = "N" ] 
    then
read -p "Enter the new base name: " new_name
i=1; for f in *; do mv -- "$f" "$( printf "$new_name-%04d.$extension" $i )"; ((i++)); done 
 fi  




#OK S11 - change this to Thunar 
nautilus $path


```

---

### Post by Vaphell on 2013-10-05
cd $path, nautilus $path - fail in case of whitespace. "" are your friends.

cleaned up 'meat' of the script
```
if   [ "$x" = "D" ]; then
  new_name=$( date +%d-%b-%Y )
elif [ "$x" = "N" ]; then
  read -p "Enter the new base name: " new_name
else
  echo "Unknown option: '$x'"
  exit 1
fi

i=1
for f in *; do
  mv -- "$f" "$( printf "$new_name-%04d.$extension" $i )"
  ((i++))
done
```

and just for kicks a bit fancier d/n choice that doesn't require enter and doesn't care about upper/lowercase
```
read -p "[D]ate, [N]ew name... " -n1 x
x=${x^^}
printf "\b[$x]\n"
```

---

### Post by GrouchyGaijin on 2013-10-05
> **Vaphell said:**
> cd $path, nautilus $path - fail in case of whitespace. "" are your friends.

cleaned up 'meat' of the script
```
if   [ "$x" = "D" ]; then
  new_name=$( date +%d-%b-%Y )
elif [ "$x" = "N" ]; then
  read -p "Enter the new base name: " new_name
else
  echo "Unknown option: '$x'"
  exit 1
fi

i=1
for f in *; do
  mv -- "$f" "$( printf "$new_name-%04d.$extension" $i )"
  ((i++))
done
```

and just for kicks a bit fancier d/n choice that doesn't require enter and doesn't care about upper/lowercase
```
read -p "[D]ate, [N]ew name... " -n1 x
x=${x^^}
printf "\b[$x]\n"
```

You the man!!

---

