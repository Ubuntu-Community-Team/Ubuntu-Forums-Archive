---
title: "Shell script...hope this is the right place...."
date: 2006-02-04
forum: Programming Talk
---

### Post by robfindlay on 2006-02-04
I need help creating either a perl or a bash script that will do the following.

When invoked scan the contents of a directory and put certain file names into a  file.  Sort of like what this would do: 

ls -al *par2 > pars

then read that "pars" file one line at a time sort of like this: 

sed -n '1p' pars, 2p, 3p, etc etc. 

then once that file name is read it would need to evoke a command like 

par2repair filename_read_from_pars_file. 

you can see what I'm trying to get at.  

I wrote a half assed bash script that basically excuted those commands the only problem is when i get to this part:     

sed -n '1p' pars | par2repair 

par2repair acts like it hasn't been given a par2 file to look at and issues an error, as if the sed command was inserting a carriage return somplace and causing par2repair to miss it.  

btw cat pars | par2repair does the same thing. 


Hope someone with some scripting skills can help me out i'm still pretty noobish. 

TIA.

Rob

---

### Post by kabus on 2006-02-04
Can't you just do 

```
for i in *{par2,PAR2}; do par2 r "$i"; done
```

?

---

### Post by joft on 2006-02-04
> par2repair filename_read_from_pars_file.

you can see what I'm trying to get at.

I wrote a half assed bash script that basically excuted those commands the only problem is when i get to this part:

sed -n '1p' pars | par2repair

Are you sure that par2repair (whatever that is) is able to read filenames from stdin (standard input)? In the first line quoted above, you give the filename as the first argument to par2repair. But in the last line quoted above, you assume that par2repair is reading filenames from stdin.

Assuming par2repair is reading a filename from the first argument, I would do:

```
par2repair `sed -n '1p' pars`
```

Which will execute par2repair with the first filename in your file "pars".

Or am I getting you wrong?

---

### Post by toojays on 2006-02-04
How about "find . -name '*.par2' -exec par2repair '{}' ';'"?

---

### Post by robfindlay on 2006-02-04
[QUOTE=kabus]Can't you just do 

```
for i in *{par2,PAR2}; do par2 r "$i"; done
```

?[/QUOTE]

Oh holy crap that did it!  Can you break your code down for this newb so i can understand whats up?  

Its obvious your reading directly from the directory but beyond that i'm lost....i've barely just started trying to learn perl and so bash scripting is a mystry to me altogehter.



Okay, one other thing, what if I wanted this to run continuously in a loop?  Maybe pausing for an hour at the end and then restarting at the top ?

What'd i'd really love is an automation script that checks an entire RAR set with par2's and then when its complete excutes unrar to extract the files. ;-) 

Rob

---

### Post by robfindlay on 2006-02-04
Can someone give me the basics on how to loop such a script ?

Meaning execute, wait like an hour and then start over.


Rob

---

### Post by kabus on 2006-02-04
> Oh holy crap that did it! Can you break your code down for this newb so i can understand whats up?

It's just a simple for loop. Take a look here for a better explanation than I could come up with :) :

[http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_09_01.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_09_01.html)

> Okay, one other thing, what if I wanted this to run continuously in a loop? Maybe pausing for an hour at the end and then restarting at the top ?

I guess you could use a while loop (while true; do ...;done) or run a cron job once an hour :

[https://wiki.ubuntu.com/CronHowto](https://wiki.ubuntu.com/CronHowto)

BTW, I guess you want to process usenet downloads. Check out hellanzb, it does all the par/rar stuff automatically : 

[http://www.hellanzb.com/trac/](http://www.hellanzb.com/trac/)

---

### Post by robfindlay on 2006-02-04
> **kabus]It's just a simple for loop. Take a look here for a better explanation than I could come up with :) :

[http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_09_01.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_09_01.html)



I guess you could use a while loop (while true said:**
> https://wiki.ubuntu.com/CronHowto[/url]

BTW, I guess you want to process usenet downloads. Check out hellanzb, it does all the par/rar stuff automatically : 

[http://www.hellanzb.com/trac/](http://www.hellanzb.com/trac/)

Oh great now you tell me....lol :-) 

What i think i'll use is "watch" to execute the script in a screen session.


Now if  I can just get somthing more stable then PAN i can kiss windows goodbye.

---

### Post by robfindlay on 2006-02-04
> **kabus]It's just a simple for loop. Take a look here for a better explanation than I could come up with :) :

[http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_09_01.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_09_01.html)



I guess you could use a while loop (while true said:**
> https://wiki.ubuntu.com/CronHowto[/url]

BTW, I guess you want to process usenet downloads. Check out hellanzb, it does all the par/rar stuff automatically : 

[http://www.hellanzb.com/trac/](http://www.hellanzb.com/trac/)


Have you been able to get hellanzb to work under breezy?  I downloaded the tarball but when I run the setup.pl i get an error about a missing MakeFile. 

If you've gotten it running could you be so kind as to post up a how-to or perhaps msg me with it offline?


Rob

---

### Post by kabus on 2006-02-04
As far as I remember you'll have to install the python-dev and python-twisted packages to make it work.

---

### Post by GrinRoth on 2006-04-14
[QUOTE=kabus]As far as I remember you'll have to install the python-dev and python-twisted packages to make it work.[/QUOTE]

Thanks m8!
I was trying to get this very handy program to work on Dapper and it didn't work.
But with those 2 packages installed, everything going fine! :-D

---

