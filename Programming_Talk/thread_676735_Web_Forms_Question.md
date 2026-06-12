---
title: "Web Forms Question"
date: 2008-01-24
forum: Programming Talk
---

### Post by Saxenm on 2008-01-24
Hey guys,  I'm trying to build a form for the web in which there are two fields: name, and desired time for a work shift. Upon clicking the submit button, I would like for this information to be added to a text file on my web server serving as a large list of names and desired work shifts, or something to that effect so that there's a constantly updating list. I have the form done with. Willing to accept the fact I'm not advanced enough to do such a thing but I'd like to find out about how to go about doing so just in case it's not too advanced of a task. Thanks!

---

### Post by scizzo on 2008-01-24
Hello,

You can always do this task with a little help of PHP.

There are various other languages that can handle this however I suggest you to look at php.

[http://www.php.net/]("http://www.php.net/")

It shouldn't be to hard to make in PHP and no matter what...someone that is really good with PHP on the forums might help you.

---

### Post by peabody on 2008-01-24
I'm not good with php, but even I can code up a simple solution to this in a matter of minutes.

```

<?php

$file = fopen("filename", 'a');
if ($file) {
  flock($file, LOCK_EX); // lock file
  fwrite($file, $_GET['name'] . '|' . $_GET['time'] . "\n");
  flock($file, LOCK_UN); // unlock file
  fclose($file);
}
?>
<html>
<body>
Thank you, data submitted.
</body>
</html>

```

code assumes your form elements were named name and time and that you want each piece of data separated by a pipe character.  flock prevents more than one than one person writing to the file at once.  "filename" should be changed to a file that the apache process can write to.  This file shouldn't be accessible via the document root.

---

### Post by pmasiar on 2008-01-24
PHP is easy to get into but hard to make clean code (and easy to make messy code). You may want to take look at Python. Simple way to create simple app: 

[http://learnpython.pbwiki.com/WebApplication](http://learnpython.pbwiki.com/WebApplication)

---

### Post by LaRoza on 2008-01-24
> **pmasiar said:**
> PHP is easy to get into but hard to make clean code (and easy to make messy code). You may want to take look at Python. Simple way to create simple app: 

[http://learnpython.pbwiki.com/WebApplication](http://learnpython.pbwiki.com/WebApplication)

... 

@OP It sounds like you would benifit from a database, in your case, SQLite or MySQL would be good solutions and they work with PHP and Python.

For the language to use, "hard to make clean code" is a bad argument. I find it very easy to make clean code, and to keep the logic separate from the content. Nevertheless. Python and PHP are both easy to learn, free to use, and have widespread support.

That PHP snippet shouldn't be used verbatim, you have to also check for the existant of null responses, injection attempts, and other realities. (Meaning, you can use the code, just add this functionality). I recommend the POST method, instead of the GET method.

---

### Post by pmasiar on 2008-01-24
> **LaRoza said:**
> For the language to use, "hard to make clean code" is a bad argument. I find it very easy to make clean code

Well, then you should create easy-to-find page on your wiki with "best practices" in clean PHP coding, so there would be less of the messy code around. I did not found any obvious one on your wiki.

But you have nice forum for learners, I'll look around. :-)

---

### Post by LaRoza on 2008-01-24
> **pmasiar said:**
> Well, then you should create easy-to-find page on your wiki with "best practices" in clean PHP coding, so there would be less of the messy code around. I did not found any obvious one on your wiki.

But you have nice forum for learners, I'll look around. :-)

Yes, I should. I do not really have a good web development section on my wiki, and give very few references for it.

Consider it on my to do list.

A nice forum? It is just a free service, with ads, and the default theme, that I made for the sites so feedback and quick questions are easier. I rarely get any questions.

---

