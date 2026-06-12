---
title: "Help with &quot;CMS&quot; in bash"
date: 2008-04-22
forum: Programming Talk
---

### Post by DrNed on 2008-04-22
I've run into a little trouble with the script below, what I was planning on doing is pipping it to netcat so someone could use a telnet client and add text to an html file. (Silly I know)

```
echo "#CMS.sh"
echo -n "Title of post: "
read title
echo -n "Text: "
read text
echo "<i>" >>date
date >>date
echo "</i>" >>date
echo "<p>" >>new.html
cat date >>new.html
echo "</p>" >>new.html
echo "...................." >>new.html
echo "<h1>"$title"</h1>" >>new.html
echo $text >>new.html
cat index.html >>old.html
cat old.html >>index.html
cat new.html >>index.html
rm -f new.html old.html date 
```

This is what the index.html looks like when I run it.

```
    Tue Apr 15 22:34:48 CDT 2008
    ....................
    old title
    old text

    Tue Apr 15 22:34:53 CDT 2008
    ....................
    new title
    new text

    Tue Apr 15 22:34:48 CDT 2008
    ....................
    old title
    old text


```

I'm trying to make it place the newest text at the top of the page. 

Any help is appreciated. 

Thank You!

-drned

---

### Post by ghostdog74 on 2008-04-22
```

awk 'NR==1{print "New text";next}1' htmlfile  > newfile
mv newfile htmlfile

```

---

### Post by stroyan on 2008-04-22
You are using ">>" in a few places that you want ">".
And you are putting old.html, then new.html into index.html instead of starting with the new.
You can use "read -p" instead of echo to emit a prompt before a read.
You can use quotes across multiple lines instead of separate echoes.
You can expand variables inside double quotes, changing
 echo "<h1>"$title"</h1>"
to
 echo "<h1>$title</h1>"

Here is a much compressed CMS.sh.
```

$ cat CMS.sh 
echo "#CMS.sh"
read -p "Title of post: " title
read -p "Text: " text
echo "<p>
<i>
$(date)
</i>
</p>
....................
<h1>$title</h1>
$text">new.html # put newer stuff at front of new.html
cat index.html >>new.html # add older stuff to end of new.html
mv new.html index.html # replace contents of index.html

$ touch index.html 
$ sh CMS.sh 
#CMS.sh
Title of post: first
Text: First Post!
$ cat index.html 
<p>
<i>
Tue Apr 22 14:40:34 MDT 2008
</i>
</p>
....................
<h1>first</h1>
First Post!
$ sh CMS.sh 
#CMS.sh
Title of post: second
Text: Me Too!
$ cat index.html 
<p>
<i>
Tue Apr 22 14:40:55 MDT 2008
</i>
</p>
....................
<h1>second</h1>
Me Too!
<p>
<i>
Tue Apr 22 14:40:34 MDT 2008
</i>
</p>
....................
<h1>first</h1>
First Post!
$
```

---

