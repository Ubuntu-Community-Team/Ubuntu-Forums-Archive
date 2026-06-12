---
title: "Adding to variable pulled from awk command"
date: 2013-10-16
forum: Programming Talk
---

### Post by The_Dawg on 2013-10-16
Newbie to programming...

I having a problem getting this to work, can you see my error?

[IMG]http://www.peoplesboard.com/news/shellscript.jpg[/IMG]

Back story:

Bash script.
This portion of the script goes through a text file, strips away blank  lines, lines that begin with #, sorts by the 4th column, grabs only the  last column, pulls the last value.  I assigned it to "$lastID".

The last value in this case is 711

I want to add 1 (one) to this number for the nextID when I write back to the file.

It will not add no matter what I've tried.  I echo'ed out the filename (check), the value 711 (check), but I cant get it to add.

*** I added the let statement just to see if it worked... no dice.

Thanks.

---

### Post by Lars Noodén on 2013-10-16
Can you show a sample line or two from the file referenced by $*filename*?  And, based on that input, what specifically do you want the line to produce?

A bitmapped image is hard to work from.  You can use [****code] and [****/code] to wrap your script excerpt and it will display better.

Also, cat is unnessary.  You can use grep directly on a file.  

```

grep -v '^\s*$' "$filename" |  ...

```

Arithmetic is done in bash like this:

[http://www.tldp.org/LDP/abs/html/arithexp.html](http://www.tldp.org/LDP/abs/html/arithexp.html)

---

### Post by The_Dawg on 2013-10-16
Thanks, I'll remove the cat portion.

Here is the text file:

```
# name major school id
# names beginning with # left

Raina Mcconnel,Philosophy,Oregon University,117
Sal Machnik,Psychology,Penn State University,112
India Fonville,Engineering,Indiana University,611
Neville Yeadon,Literature,Notre Dame University,119
Daysi Berndt,Engineering,Ohio State University,121
#Shakita Shutter,Elementary Ed.,Wisconsin University,211
Domitila Meller,Psychology,Wisconsin University,311
Lindy Williams,Engineering,Notre Dame University,113
#Kandice Tran,Neuroscience,Northwestern University,131
Jeanie Zeiler,Elementary Ed.,Notre Dame University,411
Isaura Clawson,Psychology,Stanford University,141
#Lesa Burlew,Secondary Ed.,Indiana University,511
Letitia Mcubin,Neuroscience,Indiana University,151

Jasmin Chairez,Elementary Ed.,Oregon University,118
#Keli Goodin,Psychology,Northwestern University,114
Caren Vasko,Neuroscience,Stanford University,111
Isaura Clawson,Psychology,Stanford University,141

Percy Dorfinkle,Neuroscience,Dartmouth University,107
Jenae Devine,Secondary Ed.,Penn State University,115
#Alana Mattos,Psychology,Notre Dame University,116
India Fonville,Engineering,Indiana University,611
Pok Crail,Literature,Stanford University,161
Laila Shuler,Philosophy,Oregon University,711
#Kandice Tran,Neuroscience,Northwestern University,131

```

I used the grep etc. to sort the column by the last (4th) column, then took the value of the highest number (which was on the last line).  I assigned it to lastID ( 711 ).  That part works.

What I want to do is assign $lastID + 1 to the variable nextID.

---

### Post by steeldriver on 2013-10-16
Are you sure your file doesn't have trailing non-printing characters (most likely - Windows line endings)? For example

```

$ lastId=$(echo -e "Laila Shuler,Philosophy,Oregon University,711" | awk -F',' '{print$4}')
$ echo $lastId
711
$ nextId=$(expr $lastId + 1); echo $nextId
712

```

works but

```

$ lastId=$(echo -e "Laila Shuler,Philosophy,Oregon University,711[COLOR=#ff0000]**\r**[/COLOR]" | awk -F',' '{print$4}')
$ echo $lastId
711
$ nextId=$(expr $lastId + 1); echo $nextId
expr: non-integer argument

```

looks like the awk returns integer '711' but actually has a trailing CR that breaks the math - you can check your file with

```
cat -e *yourfile*
```

FWIW I would suggest using the bash (( ... ))) math instead of expr

```
nextId=$((lastId+1))
```

---

### Post by The_Dawg on 2013-10-16
When I cat -e the file all lines end with ^M$

Is that how it should be?

I added a test variable to see if I could combine the 2 to see if there was a space:

```

echo $filename
echo $lastID
tester="world"
test=$lastID$tester
echo $test

```

Result:
members.dat
711
world

---

### Post by steeldriver on 2013-10-16
The ^M indicates the CR as guessed (^M$ means \r\n which is the standard Windows line termination)

If you know your files will *always* have that termination, you could account for it by setting the awk record separator accordingly

```
awk -F',' '**BEGIN{RS="\r\n"}** {print $4}')
```

In fact I *think* that GNU awk allows a regex for the RS so you could try

```
awk -F',' '**BEGIN{RS="\r?\n"}** {print $4}')
```

which should cover both cases (optional CR, mandatory LF)

---

### Post by The_Dawg on 2013-10-16
Thanks Steeldriver - That fixed it!

You are the man!


Also thanks for Lars for the initial advice. :)

---

### Post by Vaphell on 2013-10-16
If you drop to awk to do something, you can as well use it to perform the required math too :-) You could get new id straight from awk, because it is able to +1 just fine
```
$ test="Raina Mcconnel,Philosophy,Oregon University,117
Sal Machnik,Psychology,Penn State University,112
India Fonville,Engineering,Indiana University,611
Neville Yeadon,Literature,Notre Dame University,119"
$ awk -F, '{ id=$4>id?$4:id; } END { print id+1; }' <( echo "$test" )
612
```

---

### Post by The_Dawg on 2013-10-17
^^^
Nice I will use that in the future.

---

