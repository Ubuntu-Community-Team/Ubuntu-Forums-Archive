---
title: "assigning a variable an integer value from a string"
date: 2013-03-05
forum: Programming Talk
---

### Post by toad3000 on 2013-03-05
Hello I have some confusion. 

```
wc -l ${list[$y]} | a= cut -d ' ' -f1a=$a+0
echo "$a --test a"
```

when I do this I am suppose to get a value for the variable a. And before this code I wrote typeset -i a=0 

yet when I'm suppose to get a certain value I;'m always getting 0. Does anyone know why? 
Thanks

edit* list array contains files. the wc command works because it lists the number of lines plus the file name but when I use cut and get the first number and assign it to a i'm still getting 0.

---

### Post by papibe on 2013-03-05
Hi

I'm not entirely sure if this is you want to do, but if you want to set 'a' with how many lines has a file, you can do this:
```
a=$(wc -l file.txt | cut -c1)
``` 
Let us know how it goes.
Regards.

---

### Post by toad3000 on 2013-03-05
My gosh! Thank you so much! This is exactly what I wanted! Thank you!!
if you could could you tell me whats wrong this the coded I wrote before 

wc -l file | a= cut -d ' ' -f1

---

### Post by papibe on 2013-03-05
Sure.

This:
```
a= cut -d ' ' -f1 
```
Assign blank (null string) to 'a', and then execute the command:
```
cut -d ' ' -f1
```
Thus the result of your previous line:
```
wc -l file | a= cut -d ' ' -f1 
```
actually returns what you want, but it print it on the standard input instead of saving it on a variable.

The second part of your line is very similar to this construction:
```
DISPLAY=:0.1  vlc movie.mkv
```
which is used to run the media player vlc on a second display, identify by ":0.1"

Does that help?
Regards.

---

### Post by toad3000 on 2013-03-06
Oh I think i get it now. 
So I guess in the future If I want to assign a value something I should not do it in a pipe stream I Guess? Like in the code I wrote before I was assigning 'a' a value through a command that is piped. But your command assigned a after everything was piped and the final result is obtained?

---

### Post by toad3000 on 2013-03-06
ahhh i created another post by mistake and don't know how to delete it.....

---

### Post by papibe on 2013-03-06
I think you got it.

It is always helps to play with some code examples:
```
$ unset var
$ echo $var

$ echo "Hello, World."
Hello, World.
$ echo "Hello, World." | sed 's/Hello/Bye/'
Bye, World.
$ echo "Hello, World." | var= sed 's/Hello/Bye/'
Bye, World.
$ echo $var

$ var= echo "Hello, World." | sed 's/Hello/Bye/'
Bye, World.
$ echo $var

$ var=$(echo "Hello, World." | sed 's/Hello/Bye/')
$ echo $var
Bye, World.
$ 

```
Does that help?
Regards.

---

### Post by toad3000 on 2013-03-06
wow thanks for those examples. I tried them and played with them a bit and I think i got the hang of it!

---

### Post by apmcd47 on 2013-03-07
Can I make just one comment about the original problem, viz:```
a=$(wc -l file.txt | cut -c1)
```
When using wc with a filename is lists the filename, e.g:```
$ wc -l myfile
45 myfile
$
```
But when it is used on the standard input, no filenames are listed:```
$ wc -l < myfile
45 
$
```
thus simplifying any code that has to count lines from:
```
a=$(wc -l file.txt | awk 'print $1')
``` to:
```
a=$(wc -l < file.txt)
```

Just my tuppence worth.

Andrew

---

### Post by toad3000 on 2013-03-10
cool thanks! I didn't know that. you made the code a lot simpler to read.

---

