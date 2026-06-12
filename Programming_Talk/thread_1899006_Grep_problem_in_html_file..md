---
title: "Grep problem in html file."
date: 2011-12-22
forum: Programming Talk
---

### Post by Trapper on 2011-12-22
I have a grep routine for inserting some text into a large quantity of htm files. I am doing okay, with one exception. I don't seem to be able to grep and find the following string to insert some text just prior to it:

<div class='header'>

Here's a function that works to insert the contents of a text file just before the </head> in a group of htm files:

```
for file in *.htm ; do
while read line
do
  grep -q "</head>" <<<$line && cat jsinsert.txt >> "$file".tmp
  echo $line >> "$file".tmp
done < "$file"
done
```However if I try to insert the contents of a file just before the <div class='header'> in a file (there's only one instance of this in each file) I cannot do it. I am wondering if it has something to do with the single quotes in the string.

Here's the target line I am searching for and my code that fails to find <div class='header'> in that line.```
<div class="recipe"><img src="pics/13.jpg"><div class='header'><p class='Title'><span class='label'>Title:</span> Almond Puff Coffeecake</p>

This is my routine that fails:

for file in *.htm ; do
while read line
do
  grep -q "<div class='header'>" <<<$line && cat divname.txt >> "$file".tmp
  echo $line >> "$file".tmp
done < "$file"
done

```The contents of divname.txt is simply a line containing <div id="print_div1">
I get the temp file but it's an exact duplicate of the original file. No info is inserted just prior to <div class='header'>

?????

---

### Post by r-senior on 2011-12-23
I didn't really dig into your script but wouldn't it be easier to use sed?

```
sed -e "s/[COLOR="Blue"]<div class='header'>[/COLOR]/[COLOR="Red"]<div id=\"print_div1\"><div class='header'>[/COLOR]/g"
```

The blue is the matched string, the red is the replacement. The 'g' means all occurrences.

Lots of good examples of sed here ...

[http://www.grymoire.com/Unix/Sed.html#uh-0](http://www.grymoire.com/Unix/Sed.html#uh-0)

---

### Post by dargaud on 2011-12-23
Or an in-place replacement with perl (dangerous, test it on a spare file before):
```
perl -pi -w -e "s/<div class='header'>/<div id=\"print_div1\"><div class='header'>/;" FileName
```

More generally you want to [read this]("https://mytechrants.wordpress.com/2009/11/25/you-cant-parse-html-with-regex/").

---

