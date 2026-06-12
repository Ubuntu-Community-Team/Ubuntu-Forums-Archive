---
title: "fdupes question"
date: 2014-05-26
forum: New to Ubuntu
---

### Post by Herbon on 2014-05-26
I was looking for a way to manage my MP3 collection. Itunes for whatever reason created a bunch of duplicate.
Now im using Rhythmbox on Linux. 

I found this site 

```

http://dosnlinux.wordpress.com/2007/02/18/fdupes-tutorial/

```

Which highlight this.....

```


b=""
fdupes tmp/ --recurse | \
while read f
do
if [ "$f" = "" ]
then
b=&#8221;"
else
if [ "$b" = "" ]
then
b=&#8221;$f&#8221;
else
rm &#8220;$f&#8221; && echo &#8220;Removed \&#8221;$f\&#8221;"
fi
fi
done

```

My question is, what does this do??  The OP failed to include comments :-k

Thanks in advance

---

### Post by papibe on 2014-05-26
Hi Herbon.

That script is removing the duplicates. I would not use it as it is.

If I were you, I studied the output of fdupes, and evaluate how much duplicates you have. If indeed you have so many that it would be better to make script to delete them, I would also test the code first, by printing the rm command so you can have a sense of what is going to be delete it:
```
echo "rm $f” && echo “Removed \”$f\”"
```
Also notice that since you copied the script from a web page, there are several characters that were not pasted correctly.

Hope it helps. Let us know how it goes.
Regards.

P.S.: what I understand from the logic of the script: fdupes prints duplicates separated by an empty line, the variable 'b' represents the line before, and f the current line. When the both b and f are not empty, it means that f holds a file that is duplicated and may be removed.

---

### Post by Herbon on 2014-05-26
Ok so how do I go about deleted them :-k

I tried another less fancy command:

```

yes 1 | fdupes --rdN /media/Herbon/Music

# yes 1 | leaves 1 file
# -r --recurse
# -d --delete
# -N --noprompt

```

Which removed a lot of the "duplicates" files, but I still some remain. Yet don&#8217;t show up during the process, but I can see them in the folders.

---

### Post by papibe on 2014-05-27
If you are not concern with which copy to keep, i.e., just keep one copy, this should do the trick:
```
fdupes -rdN /media/Herbon/Music
```
(note that there's just one dash for the options).

Hope it helps. Let us know if that worked for you.
Regards.

---

### Post by Herbon on 2014-05-27
> **papibe said:**
> If you are not concern with which copy to keep, i.e., just keep one copy, this should do the trick:
```
fdupes -rdN /media/Herbon/Music
```
(note that there's just one dash for the options).

Hope it helps. Let us know if that worked for you.
Regards.

It removed most, but left some.  :confused:

---

