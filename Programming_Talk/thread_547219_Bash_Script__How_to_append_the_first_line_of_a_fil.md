---
title: "Bash Script:  How to append the first line of a file."
date: 2007-09-09
forum: Programming Talk
---

### Post by KrazyPenguin on 2007-09-09
How do I append the first line of a file.

Say i have a text file named fruit.txt and it looks like this:

apples 
oranges
grapes
cherries

and I want to change apples to bananas, but leave the rest of the file intact, what is the best command to do this with??

I've tried sed but couldn't get it to work.

Thanks.
:confused:

---

### Post by CptPicard on 2007-09-09
Well, this is a bit ugly but my first idea.. ;)

```

echo bananas > newfile.txt
numlines=$(wc -l oldfile.txt)
newnumlines=$(dc -e "$numlines 1 - n")
tail -n $newnumlines >> newfile.txt

```

Note that I'm not a such a bash guru to get this neccessarily syntactically correct first time around and I'm not testing, but you'll catch my drift :)

---

### Post by AlexThomson_NZ on 2007-09-09
sed -r 's/apples/bananas/g' fruit.txt

---

### Post by KrazyPenguin on 2007-09-09
> **AlexThomson_NZ said:**
> sed -r 's/apples/bananas/g' fruit.txt


I tried this but some reason it won't work, no errors either.

---

### Post by KrazyPenguin on 2007-09-09
OK this does work if I add in a redirect

sed -r 's/apples/bananas/g' fruit.txt > apples.text

but i wanted to change the original file.

Thanks 

;-)

---

### Post by aJayRoo on 2007-09-09
Use this:
```
sed -i 's/apples/bananas/g' fruit.txt
```
the '-i' option performs in place operations (ie. makes changes to the original file.)

---

### Post by CptPicard on 2007-09-09
Umm, that sed code replaces everywhere, right?

---

### Post by AlexThomson_NZ on 2007-09-09
Yep, so be careful with the pineapples ;)

---

### Post by aJayRoo on 2007-09-09
Oh yeah! I wasn't thinking about that really, I was more concerned with the 'i' option. If the file contains one word per line then it is pretty simple to fix:
```
sed -i 's/^apples$/bananas/' fruit.txt
```
That assumes the line begins with the word and ends immediately after it. I'm sure there are other ways of doing this too.

EDIT: OK here is another (better) way of implementing this:
```
sed -i 's/\bapples\b/bananas/' fruit.txt
```
This will only match apples as a whole word (making it safe for use on pineapples ;)) and also works if you have more than one word per line. If you have more than one instance of 'apples' on a line the g option can also be safely added to the end of the regular expression to make this work too.

---

### Post by CptPicard on 2007-09-09
Hmm, you still need to do the ^ as the OP specifically wanted to replace the first line of the file. Perhaps a better regex that does exactly what is wanted would just match  ^.*\n and replace that.

I'm glad there will be no freaky pinebananas though. :)

---

### Post by aJayRoo on 2007-09-09
Ah OK, I interpreted the question differently. I thought OP said the first line as it was the line of interest in the particular example, and was looking for general case solution.

---

### Post by KrazyPenguin on 2007-09-10
Yes, I was looking for the first line only, but all those examples really helped.

Thanks again

:guitar:

;-)

---

### Post by stylishpants on 2007-09-10
For completeness, here's the answer to the original question.

This is how to replace the first line of a file with sed.

```
sed -i -e '1c \banana' file
```

---

### Post by KrazyPenguin on 2007-09-10
Thanks for the completeness, that works great!!!

;-)

---

### Post by moodsey211 on 2009-06-11
Hi guys,

What if, instead of replacing the apples with bananas, I would like to append the bananas in the very first line. Making it like this:

Old List:

apples 
oranges
grapes
cherries

After inserting banana on top of the list:

banana
apples 
oranges
grapes
cherries

Sorry for the naive question but I'm new to ubuntu and I'm just trying out it's functionalities.

Best Regards,
moodsey

---

### Post by ad_267 on 2009-06-11
This isn't very efficient as you have to create a new file, then overwrite the old one. Someone else can probably come up with something better:

```
echo "banana" | cat - fruits.txt > fruits_temp.txt
mv fruits_temp.txt fruits.txt
```

The "-" in cat means to read from standard input. So this concatenates the banana with the rest of the fruits file.

---

### Post by ghostdog74 on 2009-06-11
cat, other than concatenating files, are pretty much useless. most tools, like grep, sed and awk will read files as stdin.

```

# awk '/apples/{print "banana";print;next}1' file
banana
apples
oranges
grapes
cherries


```

---

### Post by stylishpants on 2009-06-11
Sed can be used to insert a new first line in a file.

```
bob@cob:~$ cat /tmp/file
apples
oranges
grapes
cherries

bob@cob:~$ sed -i '1i bananas' /tmp/file

bob@cob:~$ cat /tmp/file
bananas
apples
oranges
grapes
cherries

```

---

### Post by ghostdog74 on 2009-06-11
for big files , use awk or cat method
```

echo "bananas" > temp;cat file >>temp;mv temp file

```

---

### Post by syadnom on 2010-04-13
> **KrazyPenguin said:**
> How do I append the first line of a file.

Say i have a text file named fruit.txt and it looks like this:

apples 
oranges
grapes
cherries

and I want to change apples to bananas, but leave the rest of the file intact, what is the best command to do this with??

I've tried sed but couldn't get it to work.

Thanks.
:confused:

#
sed -i 's/^apples$/bananas/g' fruit.txt

---

