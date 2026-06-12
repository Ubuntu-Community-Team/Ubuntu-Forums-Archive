---
title: "Bash script - photo re-sizer"
date: 2008-12-29
forum: Programming Talk
---

### Post by jonathanku on 2008-12-29
Hi folks, I'm struggling to get this script to work. It all works I think, except the line that tries to determine if a file begins with a certain string (i.e. "web-" without the quotes):
```

echo Photo re-size script \(800px max\)
echo $PWD

for img in *.JPG		# for every JPG in the directory
do
 echo
 echo \$img: $img		# output file name
 if [ -f web-$img ]		# check if a "web-" version of this file already exists
 then
  echo web-$img already exists
 elif [[ $img == "web-.*" ]]	# check if this file begins with "web-" so that we don't convert a converted file
 then
  echo File $img has already been converted
 else					# otherwise convert the file and prefix with "web-"
  convert -resize 800x800 $img web-$img
  echo $img resized
 fi
done

```

This line is the problem: **elif [[ $img == "web-.*" ]]**

Any thoughts? I'm thinking that regular expression might be required.
JK

---

### Post by Cracauer on 2008-12-29
elif [[ $img == "web-.*" ]]

==>

```

case "$img"
in
    web-*) doonething;;
    *) dosometrhingelse;;
esac

```

I also think you misplaced the dot and the star

---

### Post by jonathanku on 2008-12-29
OK - thanks. The dot and the star was an attempt at regex <any character><zero or more times>.

Not used case before ...funny syntax with the two semi-colons.

I'll try this when I'm next at the PC. Cheers.

---

### Post by ghostdog74 on 2008-12-29
what wrong with specifying "web-" in your for loop?
```

for img in web-*.JPG
do
 ...
done

```

---

### Post by Cracauer on 2008-12-29
> **jonathanku said:**
> 
I'll try this when I'm next at the PC. Cheers.

That's a pretty funny statement :)

BTW, there are no regular expressions anywhere in bourne shell syntax.

---

### Post by jonathanku on 2008-12-30
> **ghostdog74 said:**
> what wrong with specifying "web-" in your for loop?I'm not trying to operate on files with "web-" - I'm trying to ignore them.
> **Cracauer said:**
> BTW, there are no regular expressions anywhere in bourne shell syntax.Is bourne shell what I'm using.?!  :?

---

### Post by jonathanku on 2008-12-30
> **Cracauer said:**
> elif [[ $img == "web-.*" ]]

==>

```

case "$img"
in
    web-*) doonething;;
    *) dosometrhingelse;;
esac

```

I also think you misplaced the dot and the star
So now I'm struggling to get this case statement to meld with my other requirements. 

With the if-loop, I was also checking whether there was a web- version of the file in question.... and I don't know if that can be done with a case statement.
i.e. three checks in total :
[LIST=1][*]For this file, e.g. file1.jpg, does web-file1.jpg exist[*]For this file, does its name begin with "web-"[*]If neither of the above, convert this jpg and prefix it with "web-"
[/LIST]

I'm thinking there must be a simple way to determine if the first four characters in a variable are "web-".... no?


**Ha---- hang on...** I think I've got it... if statement first to check point 1, then case statement to deal with 2 and 3. I'll be back.

---

### Post by jonathanku on 2008-12-30
Works! Thanks.```
clear
echo Photo re-size script \(800px max\)
echo $PWD

for img in *.JPG
do
	echo \$img: $img
	if [ -f web-$img ]
	then 
		echo web-$img already exists
	else
		case "$img"
		in
			web-*) echo this file is already converted;;
			*) convert -resize 800x800 $img web-$img;;
		esac
	fi
done

echo 
```
One last question, any ideas how to say
**for img in *.jpg _or_ *.JPG**  ?

---

### Post by ghostdog74 on 2008-12-30
> **jonathanku said:**
> I'm not trying to operate on files with "web-" - I'm trying to ignore them.
then try the find command
```

find . \( ! -name "web*.jpg" -a -name "*.jpg" \)  | while read FILE
do
  # do something with $FILE
done

```

---

### Post by Cracauer on 2008-12-30
> **jonathanku said:**
> 
One last question, any ideas how to say
**for img in *.jpg _or_ *.JPG**  ?

This is a problem in sh, actually.

If you say
for file in *.jpg *.JPG ; do ...

then you'll get *.JPG inserted as a token for no file that exists. Stupid. And you still miss *.JpG files.

Either use find as indicated in the last post or like this
for file in `find . -iname \*.jpg \! -name web-\*` ; do ...

Or you do it like this:
for file in *.jpg *.JPG ; do ...
   test -f "$file" || continue # skip junk inserted

When we did so far isn't safe when you have space in filenames, BTW.

---

### Post by jonathanku on 2009-02-08
My Unix friend at work helped with this.... all I needed was

**for img in *.[jJ][pP][gG]**

So anything within the square brackets is OR-ed.

---

