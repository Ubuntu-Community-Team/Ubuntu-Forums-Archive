---
title: "replace character in a string"
date: 2007-11-28
forum: Programming Talk
---

### Post by dunryc on 2007-11-28
Hi all hope some one can help me ive writng a bash script scrape data from web site (from the html source) ive got most of the sript running fine but have a small prob one of the sites i need to seach replaces space dharacters  in the seach string with "%20" not including the quotation marks the string is stored in a variable search wich ive got from the user using the read command , hope some one can help or at least understand what im not very elequently tring to say !! 

regards dunryc

---

### Post by volanin on 2007-11-28
> hope some one can help or at least understand what im not very elequently tring to say !!

Your english is very good.
It seems that you are just lazy to type correctly.
It would be much easier to get your point across with correct punctuation, believe me!
:)

Try this:
```
echo $VARIABLE | sed 's/%20/ /g'
```

Or this to modify the file directly:
```
sed -i 's/%20/ /g' index.html
```

---

### Post by Wybiral on 2007-11-28
I can't help you with BASH, but if you could afford to do it in Python it's pretty simple:

```

print "Hello%20World!".replace("%20", " ")

```

---

### Post by geirha on 2007-11-28
If you want a really, really dirty way of doing it, you can try
```
line="Hello%20%3A%29"
eval `echo echo -e $line | sed 's/%\([A-F0-9]\{2\}\)/"\\\0"\`echo "ibase=16;obase=8;\1"|bc\`/g'`
```
which will replace any %## with its respective ascii symbol.

Beautiful isn't it?

---

### Post by dunryc on 2007-11-28
wow thanks for the quick responces, I tried all of the above , but settled with the following. :-

>  VARIABLE1=$(echo $$VARIABLE2 | sed 's/ /30%/g')_

Which seems to work perfectly (until i break it) leaving the output of the sed command in $VARIABLE1.

Once again thanks for the heads up guys :)

---

### Post by Keith Hedger on 2007-11-28
Easier:
var1="AAA%20BBB%20CCC"
var1=${var1//'%20'/" "}
echo $var1
=
AAA BBB CCC

---

### Post by dunryc on 2007-11-28
thanks keith that works great and makes it asy for me and others to understand

---

### Post by easoukenka on 2008-08-25
Thanks Keith you really helped me with this one believe it or not I was googling forever for this for some reason no export trick ever worked for me your solution was the simplest and only one that worked for me!

---

