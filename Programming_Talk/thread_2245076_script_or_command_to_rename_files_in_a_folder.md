---
title: "script or command to rename files in a folder"
date: 2014-09-21
forum: Programming Talk
---

### Post by dave131 on 2014-09-21
In converting part of my family history from Windows over to where it is usable in Ubuntu, I've come up against something I hope there is a faster way to do.  I have several files that start with a capital "I", followed by 5 numbers, followed by 3 capital letters (either ALB, GRV or LIC) and then followed by an extension of (capitalized) .HTML.  I need to leave the capital "I" at the front, but for all characters after that I need to change the capital letters to lower case letters.  So far I'm having trouble figuring out pattern matching and substitution in the shell.  I was used to, years ago in another OS, using an editor and doing  S/ALB.HTML/alb.html/ (as an example) - I usually had an editor "program" in that I scripted all the statements I wanted done.  I've tried looking at sed, but this pattern matching and substitution is strange to me.

Can someone point me to beginners explanation and samples of pattern matching and substitution in the shell?

Thanks.

EDIT:  What I was thinking:

feed output of ls I*.HTML to a script with these substitutes, with "var" somehow containing the filename from the ls output one by one:

${var/ALB.HTML/alb.html/}
${var/GRV.HTML/grv.html/}
${var/LIC.HTML/lic.html/}
and then build a mv command for each filename of mv <path & filename> <path & lowercase converted name>

*IF* a mv to the same folder will essentially create the new file and delete the old file.

Then end result is to have only lower case filenames after the "I".

EDIT-EDIT:  I should mention that I've tried the following from a terminal:  mv I*ALB.HTML I*alb.html  but it gives me an error.  Doing the same thing but explicitly specifying the fully qualified file names does work.  If there is a way to just make this work I won't need to worry about the substitution things I was showing above.

---

### Post by Lars Noodén on 2014-09-21
The program you are looking for is 'rename'.  It uses [Perl regular expressions](http://manpages.ubuntu.com/manpages/trusty/en/man1/perlre.1.html) which are more powerful, you may have run across them before as PCRE.  Use 'rename' with the -n option first to show the input and output without making any changes.  Then when the patterns are right, run it without the -n and it will rename the files.  

Do you have some examples of the real filenames that you could share?  It would be easier to visualize the pattern needed then.

---

### Post by dave131 on 2014-09-21
Sure!   

I00010ALB.HTML
I00010GRV.HTML
I00010LIC.HTML
I00010WED.HTML

These are the actual html file names for 1 individual in the history, containing picture ALBum (hummm...;) ), picture and info on GRaVe, wedding LICense application and WEDding license.  I did all the work initially in Windows over a decade ago now, and now needed to make changes/additions and currently only run Ubuntu - and Ubuntu is case sensitive whereas Windows wasn't.  So, in a main html file for individual I00010 there is a link (text "See xxxxxxxx") for each but they are specified in lower case - so no match.  It would be easier to rename the files than to edit each of the individuals (22,000+ !!) html files.

So, I've tried rename and get an error: ```
me@me1735:~/.wine/drive_c/ftwtest/cdimage/myhtml$ ls *ALB*
I00011ALB.HTML  I00052ALB.HTML  I00142ALB.HTML  I00502ALB.HTML  I00564ALB.HTML  I01378ALB.HTML  I03392ALB.HTML  I21693ALB.HTML
I00012ALB.HTML  I00065ALB.HTML  I00493ALB.HTML  I00515ALB.HTML  I00585ALB.HTML  I01380ALB.HTML  I03445ALB.HTML  I21694ALB.HTML
I00044ALB.HTML  I00066ALB.HTML  I00495ALB.HTML  I00516ALB.HTML  I00587ALB.HTML  I01397ALB.HTML  I12239ALB.HTML  SKELETONALB.HTML
I00047ALB.HTML  I00069ALB.HTML  I00501ALB.HTML  I00522ALB.HTML  I00589ALB.HTML  I01399ALB.HTML  I12240ALB.HTML
me@me1735:~/.wine/drive_c/ftwtest/cdimage/myhtml$ 
me@me1735:~/.wine/drive_c/ftwtest/cdimage/myhtml$ 
me@me1735:~/.wine/drive_c/ftwtest/cdimage/myhtml$ rename *ALB* *alb*
Bareword "I00011ALB" not allowed while "strict subs" in use at (eval 1) line 1.
Bareword "HTML" not allowed while "strict subs" in use at (eval 1) line 1.
me@me1735:~/.wine/drive_c/ftwtest/cdimage/myhtml$ 
me@me1735:~/.wine/drive_c/ftwtest/cdimage/myhtml$ 
me@me1735:~/.wine/drive_c/ftwtest/cdimage/myhtml$ rename I*ALB.HTML I*alb.html
Bareword "I00011ALB" not allowed while "strict subs" in use at (eval 1) line 1.
Bareword "HTML" not allowed while "strict subs" in use at (eval 1) line 1.
me@me1735:~/.wine/drive_c/ftwtest/cdimage/myhtml$ 
```

Thanks, Lars!

---

### Post by Lars Noodén on 2014-09-21
The program [rename](http://linux.die.net/man/1/rename) takes the pattern as an argument, so it needs to be passed in quotes so that the program receives it intact.  (Otherwise, the shell will process it as [globbing](http://manpages.ubuntu.com/manpages/trusty/en/man7/glob.7.html).)

Try something like this:

```

rename -n 's/(ALB|GRV|LIC|WED)\.HTML$/\L$1.html/' *.HTML

```

The basic pattern rule is **s///** with the pattern to be sought in the first part and the desired replacement in the second part.  The parenthesis are for matching a group, in the first part.  In the replacement, the result of that first match is **$1** in the second part.  The \L is a modifier to set anything following as lowercase.  The dollar sign signifies the end of the string, which means that the pattern will be looked for only at the end of the file name.  

You could also do it with literals, with perl there is always another way to do it.

---

### Post by dave131 on 2014-09-21
Wow!  I never would have figured that out!  Thank you so much for explaining what it is doing - that helps very much!

Thanks!

---

### Post by Lars Noodén on 2014-09-21
No  worries.  Like I mentioned, it could probably also be done with literals (and thus four sets of s/// in the script) if that is easier to read.

```

rename -n 's/ALB\.HTML$/alb.html/; s/GRV\.HTML$/grv.html/; s/LIC\.HTML$/lic.html/; s/WED\.HTML$/wed.html/;' *.HTML

```

There's more than one way to do it. ;)

---

### Post by dave131 on 2014-09-21
Another WOW!  I downloaded a beginners book for the shell but what you have put here is so far beyond what I even think I can learn from that!  Thanks very much - you've solved my quandry excellently!

---

