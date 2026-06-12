---
title: "sed help"
date: 2013-03-19
forum: Programming Talk
---

### Post by tobiasgardner on 2013-03-19
Hi, I am stuck on this, have spent hours trying to find an answer :/

I am trying to use sed to strip away content in .html files. Sometimes the html files have the html tags on own rows and sometimes not, as in the examples below:

Example a.html:
```

<html>
<head>
<title>Example A</title>
</head>
<body style="styleA">
<p>Some text
</body>
</html>

```

Example b.html:
```

<html><head><title>Example B</title></head><body style="styleB"><p>Some text</body></html>

```

With the following sed command I can add text after a tag independent of if it has a newline or not...

```

tobbe@virtualbox:~/$ sed 's/<[\/]*body[^>]*>/&\
/g' a.html
<html>
<head>
<title>Example A</title>
</head>
<body style="styleA">


<p>Some text
</body>


</html>
tobbe@virtualbox:~/$ 
tobbe@virtualbox:~/$ 
tobbe@virtualbox:~/$ sed 's/<[\/]*body[^>]*>/&\
/g' b.html
<html><head><title>Example B</title></head><body style="styleB">
<p>Some text</body>
</html>

```

BUT I only want to add the newline when the tag is NOT followed by a newline... So I am trying to do the same as above but use the searchcritera as above + NOT a newline which I thought was '^$', i.e.

```

tobbe@virtualbox:~/$ sed 's/<[\/]*body[^>]*>[COLOR=#ff0000]^$[/COLOR]/&\
/g' b.html
<html><head><title>Example B</title></head><body style="styleB"><p>Some text</body></html>

```

---

### Post by varunendra on 2013-03-19
*Thread moved to **Programming Talk**.*
------------------------------------

A nice reference link for sed usage : [http://www.grymoire.com/Unix/Sed.html](http://www.grymoire.com/Unix/Sed.html)
I'm no expert, but I managed to do everything I wanted with a very complex mix up of html files with the help of that guide and some bash references.

Perhaps someone here can give you a better link or maybe even an elegant solution to what you want.

---

### Post by Vaphell on 2013-03-19
. is not-a-newline ;-)

try this:
```
sed -r 's/(<[\/]*body[^>]*>)(.)/\1\n\2/g'
```

---

