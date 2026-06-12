---
title: "help sending form vars with php"
date: 2006-06-13
forum: Programming Talk
---

### Post by oldmanstan on 2006-06-13
ok, i am writing a wordpress plugin and it is in two files. apparently the second file can't access wordpress functions, only the main one (which I thought was kinda weird but i'll deal with it later)

anyway, the second file just returns an image so i need it to know the path i want it to look in but when i put something with slashes as a "get" variable it doesn't like it

for instance   [www.something.com/index.php?dir=/home/bob/](www.something.com/index.php?dir=/home/bob/)

doesn't work

is there a php function to clean up the forward slashes?

---

### Post by johnnymac on 2006-06-13
I believe if you set it up as a POST you'd probably get past the issue of having to clean anything up.  Or, you can have it go to a dummy page that just relocates the browser to the directory you want it to go into.

---

### Post by oldmanstan on 2006-06-13
yeah, see the problem is that i'm not actually sending the info with a form, otherwise i would use the post method, but i'm directly calling the script from an <img> tag, i.e. <img src='somesuch.php?file=hello.jpg'/>

thanks for the help though, anyone else have any ideas?

---

### Post by oldmanstan on 2006-06-13
EDIT: i'm an idiot, apparently i had a different bug in the script that was causing the problem and it only seemed to trace back to the GET string, problem solved

---

### Post by blm126 on 2006-06-13
Have you looked at the [urlencode]("http://us3.php.net/manual/en/function.urlencode.php") function. It should get rid of the slashes for you.

---

