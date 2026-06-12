---
title: "Regular Expressions"
date: 2011-05-20
forum: Programming Talk
---

### Post by nair on 2011-05-20
I have no experience with regular expressions.  I am trying to find a good application out there which can implement regular expressions for the purposes of searching and replacing pieces of text in a text file.

So far I have attempted to use Notepad++ and Visual Studio 2010.  I haven't found any good documentation for Notepad++ regarding regular expressions, and VS2010 has examples which I either have not been able to follow/replicate...or do not address the actual problem I am trying to solve.

A few things that I want to be able to do with regular expressions are:

[LIST=1]
[*] Search multiple lines at the same time, (ex. line 1 has "Joe", line 2 has "Blow"...be able to search and return one result for "Joe Blow").
[*]Handle spaces and tabs that are in variable amounts, (ex. "_____Joe", and "Joe" can all be found in the same search for "Joe"; whether spaces/tabs are present or not should not prevent the result from being returned; NOTE that underline is intended to be several spaces, but this forum's formatting will not allow me to post it like that).
[*]Be able to do a find on one line (ex. line 5) and perform the replace on a different line (ex. line 4 or line 6) located relative to the found line.
[/LIST]
 
I've performed several search on Google, and found marginally useful information on StackOverflow pertaining to my exact problem.  Can anyone point me in the right direction? I am open to using the previously mentioned applications for this task, or using entirely different ones. I am a huge regular expressions noob.

---

### Post by StrayEddy on 2011-05-20
You can do regex (regular expressions) in notepad++:

[http://astuces.jeanviet.info/bureautique/rechercher-et-remplacer-du-texte-avec-notepad-et-quelques-regex.htm](http://astuces.jeanviet.info/bureautique/rechercher-et-remplacer-du-texte-avec-notepad-et-quelques-regex.htm)

And to test your regex beforehand, use:

[http://rubular.com/](http://rubular.com/)
(this site is sooo awesome and usefull)

Good luck

---

### Post by simeon87 on 2011-05-20
Have a look at grep, it's installed in Ubuntu and you can search through files using regular expressions. With some knowledge of regular expressions, you can find what you want with grep.

---

### Post by bashologist on 2011-05-23
Perl is great the the kind of examples you've given. Read a good book on perl. 

Books that I've read and found useful:
Learning Perl
Mastering Regular Expressions

---

### Post by nair on 2011-05-25
Is it true that regular expressions are based on some sort of global standard?  It seems like, just from comparing Notepad++ and VS, that regular expressions work differently or have a different type of formatting depending upon the environment/IDE in which they are implemented.

---

### Post by Barrucadu on 2011-05-25
There is a POSIX standard, PCRE (Perl's regular expressions - POSIX but with extensions) is very widespread, and mathematical conventions (regular expressions are, after all, merely a syntax for denoting a (regular) formal grammar), but no "enforced" standards.

---

