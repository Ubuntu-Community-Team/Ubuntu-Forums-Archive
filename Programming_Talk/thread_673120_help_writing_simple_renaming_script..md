---
title: "help writing simple renaming script."
date: 2008-01-20
forum: Programming Talk
---

### Post by syxbit on 2008-01-20
I've spent a while searching, reading man pages, etc.. but none of the sites seem to show how to do a rename in the way i would like.

i have files (usually .jpg) given to me with horrible naming schemes.
such as

holiday01vegas.jpg
holiday02vegas.jpg
holiday03vegas.jpg

I want to rename them all

"Trip to Vegas - 01.jpg"
"Trip to Vegas - 02.jpg"
etc..

So, I basically want to just keep the numbers, and choose what text to put at the beginning.

I've looked at the rename command, but the man page is really brief.
Also, shouldn't there be a way to even pick the numbers?
Because if i don't specify, lets say they were named

holiday-A-vegas.jpg
holiday-B-vegas.jpg
holiday-C-vegas.jpg

you should still be able to do it, as if you traverse across 'holiday*' it will go in order alphanumerically, so it would correctly rename A first, then B

I've been doing the renaming by hand right now.
I'd rather not use a gui based program, as i would like to automate it in scripts later.

could anyone help me out?

the best site i found is [this]("http://www.kangry.com/topics/viewcomment.php?index=538")

which explains using
rename holiday xmas_photos holiday
but i don't know how to put spaces in, and, it only targets the part of the name that's before the numbers

---

### Post by geirha on 2008-01-20
To do this kind of thing I usually use sed to change the name using regular expressions. You should read up on regular expressions and sed. Here's an example with the filenames you listed above:
```
for file in holiday*.jpg; do 
  newname=`echo "$file" | sed -r 's/holiday([0-9]+)vegas(\..*)/Trip to Vegas - \1\2/'`; 
  mv -iv "$file" "$newname"; 
done

```

Executed as a "one-liner":
```
$ for file in holiday*.jpg; do newname=`echo "$file" | sed -r 's/holiday([0-9]+)vegas(\..*)/Trip to Vegas - \1\2/'`; mv -iv "$file" "$newname"; done
«holiday01vegas.jpg» -> «Trip to Vegas - 01.jpg»
«holiday02vegas.jpg» -> «Trip to Vegas - 02.jpg»
«holiday03vegas.jpg» -> «Trip to Vegas - 03.jpg»

```

---

### Post by pmasiar on 2008-01-20
IMHO your needs are custom, and you need custom script. 

Python lets you to get list of filenames in a directory, parse them, generate new names, and rename those files. 

...and I am not sure why you want spaces in file names. ;-) Space is filename delimiter, having spaces in names is no-ending pain.

---

### Post by syxbit on 2008-01-20
wow
genius.
I've tried reading the perl regex man pages. I'll try again.
so, would this script be significantly easier and shorter if i didn't require the spaces?

---

### Post by geirha on 2008-01-20
I've never actually used rename before, but after reading the man-page I realised that I should have :)

You can do something like this: (used a simpler regex this time)

```
rename 's/holiday([0-9]+)vegas.jpg/Trip to Vegas $1.jpg/' *.jpg
```

EDIT: and [this](http://perldoc.perl.org/perlrequick.html) seems to explain the regexes fairly well. In this case the search and replace (near the bottom of that page) syntax is used

---

### Post by rosegarden78 on 2008-01-20
FFMPEG supports numbering like that and converts all video types.

---

### Post by syxbit on 2008-01-20
> **geirha said:**
> I've never actually used rename before, but after reading the man-page I realised that I should have :)

You can do something like this: (used a simpler regex this time)

```
rename 's/holiday([0-9]+)vegas.jpg/Trip to Vegas $1.jpg/' *.jpg
```

EDIT: and [this](http://perldoc.perl.org/perlrequick.html) seems to explain the regexes fairly well. In this case the search and replace (near the bottom of that page) syntax is used

much better!
thanks.
so, this says
match 'holiday' followed by any numbers (not sure what the '+' is for), followed by 'vegas.jpg' and replace with 'Trip to Vegas' and then $1, which i assume is a variable.

i'll do some more regex reading.
thanks. very nice solution

---

### Post by sas on 2008-01-20
> **syxbit said:**
> much better!
thanks.
so, this says
match 'holiday' followed by any numbers (not sure what the '+' is for), followed by 'vegas.jpg' and replace with 'Trip to Vegas' and then $1, which i assume is a variable.


The '+' means repeat the previous thing 
$1 is a backreference which matches the first matched expression (i.e. the bit in brackets)

---

### Post by geirha on 2008-01-20
```

[0-9]      matches one digit.
[0-9]+     mathces one or more digits
[0-9]?     matches zero or one digit
[0-9]*     matches zero or many digits
[0-9]{2}   matches exactly two digits
[0-9]{2,4} mathces two, three or four digits.

```
the parenthesis around ([0-9]+) says that we want to store those one or more digits. In the replacement string $1 then becomes that number. If you add more parenthesises, they become $2, $3 and so forth, counting from left to right.
If you want to match a literal ( or + or . or any other of the special regex characters, you need to escape them by putting a \ in front of them. It's all explained on that perlrequick page ...

---

### Post by rosegarden78 on 2008-01-26
Might need to use regular expressions.  A regular expression editor exists in the repos.

---

### Post by maurolust on 2011-12-22
I'm using rename with regexes, following every tip I see, however the dollar (as in $1$2) is not responding as expected when used as backreference (not as an anchor).

Using 'Backlash'('\')  instead of 'dollar' does the job, but causes annoying warnings. Why is that?
```

rename -v -n "s/([1-6])([01][0-9])/M$1D$2/g" *.jpg
401-Memoirs.jpg renamed as MD-Memoirs.jpg
402-ElectricBike.jpg renamed as MD-ElectricBike.jpg
403-BroadcastBen.jpg renamed as MD-BroadcastBen.jpg

```

```

rename -v -n "s/([1-6])([01][0-9])/M\1D\2/g" *.jpg
\1 better written as $1 at (eval 1) line 1.
\2 better written as $2 at (eval 1) line 1.
401-Memoirs.jpg renamed as M4D01-Memoirs.jpg

```

Thanks everyone (Im spelling 'dollar' extensively instead of '$' to make this topic more googlable)

---

### Post by geirha on 2011-12-22
> **maurolust said:**
> I'm using rename with regexes, following every tip I see, however the dollar (as in $1$2) is not responding as expected when used as backreference (not as an anchor).

Using 'Backlash'('\')  instead of 'dollar' does the job, but causes annoying warnings. Why is that?
```

rename -v -n "s/([1-6])([01][0-9])/M$1D$2/g" *.jpg
401-Memoirs.jpg renamed as MD-Memoirs.jpg
402-ElectricBike.jpg renamed as MD-ElectricBike.jpg
403-BroadcastBen.jpg renamed as MD-BroadcastBen.jpg

```

Bash will expand parameter expansions inside double quotes, so it replaces $1 and $2 with the first two arguments of your shell (which are typically empty in an interactive shell). With single quotes (also known as hard quotes), bash does no expansions whatsoever; everything is treated literally, so just use single quotes. 

```
rename -v -n 's/([1-6])([01][0-9])/M$1D$2/g' *.jpg
```

[http://mywiki.wooledge.org/Quotes](http://mywiki.wooledge.org/Quotes)

---

### Post by maurolust on 2011-12-22
> **geirha said:**
> Bash will expand parameter expansions inside double quotes, so it replaces $1 and $2 with the first two arguments of your shell (which are typically empty in an interactive shell). With single quotes (also known as hard quotes), bash does no expansions whatsoever; everything is treated literally, so just use single quotes. 

```
rename -v -n 's/([1-6])([01][0-9])/M$1D$2/g' *.jpg
```

[http://mywiki.wooledge.org/Quotes](http://mywiki.wooledge.org/Quotes)

The devil is in the details, but angels hang out at ubuntu forums, thanks.

---

