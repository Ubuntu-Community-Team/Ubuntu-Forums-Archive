---
title: "replace a text in a text"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by just_linux on 2008-08-07
hi, :(
I have a file called "address.txt" :popcorn:
which has:( including the spaces !!!!!)
[HTML]				<a href="http://Sajhgaminic/Yahoo/128KB/Mehrshhmak/sdfg.mp3">

				<a href="http:///Sajhgaminic/Yahoo/128KB/Mehrsh0Cheshmak/0sdfg.mp3">[/HTML]

Now I want to clean it up and make a a clean list like here:
[HTML]
http://Sajhgaminic/Yahoo/128KB/Mehrshhmak/sdfg.mp3
http:///Sajhgaminic/Yahoo/128KB/Mehrshshmak/0sdfg.mp3
http:///Sajhgaminic/Yahoo/128KB/Me0Cheshmak/0sdfg.mp3
[/HTML]:lolflag:

I know I need to use SED but I could not find the correct way of doing this
Please explain clearly 
Thanks :guitar:

---

### Post by Niedra on 2008-08-07
Doesn't Replace function work for this. Replace is found in almost any text editor. Just replace the spaces and html tags with blank space.

---

### Post by ibuclaw on 2008-08-07
sed is a brilliant app for this sort of text editing. :)

[EDIT]
It appears that the whitespace was tabs. Sorry. fixed!
```
sed 's/\t//g;s/^<a href="//g;s/">$//g;/^$/d' **filename**
```

Regards
Iain

---

### Post by just_linux on 2008-08-07
NO NO !!
I want to do it without opening the file and do it only on the terminator, 
There are too many files that this needs to run through and Also, it is part of a bigger shell program !!!
Any other why ( ONLY IN TERMINATOR PLEASE !!)

---

### Post by LowSky on 2008-08-07
Do you mean Terminal? A Terminator is a Robot Cyborg designed to destroy human kind and was played by the current California Governor in three movies. As far as I know you need a text editor to edit a text file. No way around that. If you want to do it in a terminal use the command ```
sudo nano */location/file name* 
```

---

### Post by ibuclaw on 2008-08-07
You can have the -i function, so sed saves the edit back to the file.

Although, I never personally use this in the event that things go wrong...

```
sed -i 's/\t//g;s/^<a href="//g;s/">$//g;/^$/d' **filename**
```

Regards
Iain

---

### Post by just_linux on 2008-08-07
Thank you so much for your solution worked nicely 
Would you plz expline it so I could do that myslef too. and also how should I deal with the the end of it? " "> "
Please walk throught the coe you wrote !
Thanks a lot

---

### Post by ibuclaw on 2008-08-07
Sed, as well as Awk and Grep are one of those wonderful languages that make text processing so much simpler.

Here is a general walkthrough of what happens in the line.

start sed and tell it to write back to the file, instead of stdout.
```
sed -i
```
the **s** function searches and replaces all matches.
ie:
**s/match/replace/**

the **g** option at the end means to repeat the action throughout the file, and not just for the first match.

Here we replace all "**\t**" tabs for nothing "**//**" (essentially removing them).
```
's/\t//g;
```
Here we replace all "**<a href="**" that occur at the beginning of the line with nothing.
```
s/^<a href="//g;
```
The **^** and **$** symbols represent the start and end of a line.
^ = start
$ = end.

Here we just replace/remove all occurences of "**">**" at the end of the line (notice the "$").
```
s/">$//g;
```
And lastly, we use the **d** option to delete lines.
Here we delete all empty lines, hence the match "^$"
```
/^$/d'
```

You can learn more about the complex uses of sed here:
[http://sed.sourceforge.net/sed1line.txt](http://sed.sourceforge.net/sed1line.txt)

Regards
Iain

---

### Post by ghostdog74 on 2008-08-10
if your file really has such a format, this will do
```

# awk -F'"' '!/^$/{print $2}' file
http://Sajhgaminic/Yahoo/128KB/Mehrshhmak/sdfg.mp3
http:///Sajhgaminic/Yahoo/128KB/Mehrsh0Cheshmak/0sdfg.mp3


```

---

