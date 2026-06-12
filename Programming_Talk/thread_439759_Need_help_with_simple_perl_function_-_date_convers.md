---
title: "Need help with simple perl function - date conversion"
date: 2007-05-11
forum: Programming Talk
---

### Post by SNYP40A1 on 2007-05-11
I have a file with many dates in it and I want to convert from this:

05/08/0714:02:46

to this:

20070508140246
(year, month, day, hour (military time), minute, second.

Anyone know an easy way to do this?  I figured that the easiest way would be to use some sort of character mask like this:

mm/dd/yyhh:mm:ss and then see if Perl could do the matching, but I have not found such a function.  Currently, I am using substrings, but it is tedious and ugly.  Any suggestions?

---

### Post by hyperair on 2007-05-11
Learn up your regexp well. It's dead useful. But here's the code anyway:
```

$date = "05/08/0714:02:46";
$newdate = $date;
$newdate =~ s/^(\d\d)\/(\d\d)\/(\d\d)(\d\d)\:(\d\d)\:(\d\d)$/sprintf("%4d%02d%02d%02d%02d%02d",$3+2000,$1,$2,$4,$5,$6)/e;

```

A bit long, I know, but once you understand regular expressions you'll understand this.

---

### Post by xadder on 2007-05-11
Or, here's another way:

```

$_ = "05/08/07 14:02:46";

 ( $date, $time ) = split;  # Splits on white space
 ( $mm, $dd, $yy ) = split('/',$date);
  $time =~ s/://g;

 $newdate = sprintf("%4d%02d%02d%06d",2000+$yy, $mm,$dd,$time);
 print $newdate, "\n";

```

I find this style easier to keep track of

---

### Post by SNYP40A1 on 2007-05-12
thanks for the help.  I tried hyperair's script and it worked perfectly (although I don't understand what it does).  Xadder, I understand your script and it is better than what I was doing.  Thanks.  If anyone knows a good guide for this stuff, please let me know.

---

### Post by hyperair on 2007-05-13
Referring to Xadder's script, don't forget to put the "my" keyword, or you end up having those temporary variables ( $date, $time, $mm, $dd, $yy ) becoming global variables.

Another thing, Xadder's script is more readable, but uses a slightly different approach to mine, in that he uses string functions instead of regular expressions. Regular expressions are slow, and hence I recommend that you use Xadder's script instead of mine. I've benchmarked it (using a rather crude, self-written benchmark) and the results are always the same-Xadder's script runs faster than mine. ^^ The time difference is not a lot, but hey it's there-about 3 microseconds (I'm very fussy about efficiency)

---

### Post by xadder on 2007-05-13
Yep, I agree about adding "my". In real code, I always use "use strict" and add "my", "our", etc. to everything. Catches a lot of errors that way.

As to a good guide, then after the classic  "Learning Perl" and "Programming Perl" books,  my favourite is the Perl Cookbook. Very well written, and loads of examples of perl in action.

---

### Post by ghostdog74 on 2007-05-13
there are also modules like Date::Format , Date::Manip you can use for such task.
if you are open for alternative, here's an awk one
```

  awk '{ split($1,date,"/");
          gsub(":","",$2) 
	  print "20"date[3]date[2]date[1]$2 }' "file"

```
assuming "file" contains "05/08/07 14:02:46"

---

### Post by hyperair on 2007-05-13
Awk? Isn't awk another language? In that case we would never end with the solutions :p I could post a few Ruby codes as well as C and C++ codes, and maybe a few Javascript ones as well

O Reilly's Advanced Perl Programming's good too-I learnt a lot of stuff from there: [http://www.unix.org.ua/orelly/perl/advprog/index.htm](http://www.unix.org.ua/orelly/perl/advprog/index.htm)

At the bottom of that page there are links to other book titles as well.

---

### Post by ghostdog74 on 2007-05-13
> **hyperair said:**
> Awk? Isn't awk another language? 

yes, awk is a small utility most suitable for doing quick scripts like scanning patterns and processing them. every person playing with the shell should learn how to use it. It has been around for ages in the unix world, way before Perl
> 
In that case we would never end with the solutions :p I could post a few Ruby codes as well as C and C++ codes, and maybe a few Javascript ones as well

Ruby doesn't exists in all unix systems,  you got to install it if want to use it. C/C++ and Javascript for OP's purpose is overkill.

---

### Post by hyperair on 2007-05-13
You have a point, but the thing is you don't know what context this belongs to. he could be converting dates for storage in some web processed thing, CGI/Perl maybe. On the other hand, he could be asking for this for personal use. 

What about sed, though? I've seen sed being used with regular expressions akin to those of Perl before, but I've never really known how to use it. Could you recommend me to some tutorials on awk and sed?

---

### Post by ghostdog74 on 2007-05-13
> **hyperair said:**
> You have a point, but the thing is you don't know what context this belongs to. he could be converting dates for storage in some web processed thing, CGI/Perl maybe. On the other hand, he could be asking for this for personal use. 

yes, i understand that's why i have said if he is "open to alternatives". 
> 
What about sed, though? I've seen sed being used with regular expressions akin to those of Perl before, but I've never really known how to use it. Could you recommend me to some tutorials on awk and sed?
sed is also a good and simple pattern matching tool, however AFAIK it lacks features such as non greediness, etc..(so does awk).  that's where Perl/(or other PCRE regexp tools) comes in the picture. 
you can have a look at [this sticky]("http://ubuntuforums.org/showthread.php?t=333867"), under my nick there's a unix ebook you can read. also check [this website]("http://www.unix.org.ua/orelly/unix/sedawk/") Its about sed and awk. have fun

---

### Post by hyperair on 2007-05-14
Ah, thanks for the links. What did you mean by non greediness anyway?

---

### Post by ghostdog74 on 2007-05-14
> **hyperair said:**
> What did you mean by non greediness anyway?
just a very simple example. you have this string:
```
This is a <H1>greedy</H1> test.
```. And say if you want to match the words inside <>, ie H1, and /H1.
if you do /<.*>/, the regexp engine will search the string and match for you the first '<' of H1 and the last '>' of /H1...this is called greediness...the ways to overcome this is to put '?' question mark, as in <.*?>
for more information, you can see [here]("http://www.regular-expressions.info/repeat.html"). have fun

---

