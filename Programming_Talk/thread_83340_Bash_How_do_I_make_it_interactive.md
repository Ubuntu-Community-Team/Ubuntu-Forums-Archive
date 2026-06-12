---
title: "Bash: How do I make it interactive?"
date: 2005-10-28
forum: Programming Talk
---

### Post by ramdisc on 2005-10-28
Hello,

Can someone please help me write an interactive bash script if it's not too much trouble?

Okay, please bear with me, I am going to speak in plain English.

This is what I got as a base:

for I in `seq 1 20`; do wget websitegoeshere$I.rar; done

Here's an imaginary interaction bash script in Konsole:

ramdisc@linux:~>./getit.sh
Please insert URL
ramdisc@linux:~>http://website.com/dir/foo

I run the script. The scrip then asks me for the URL. I enter the URL and hit enter.  Then the script starts doing its job of downloading all 20 files (from foo1.rar to foo20.rar).

Not sure if anyone can understand me.  :/

---

### Post by LorenzoD on 2005-10-28
I think you may want to 'man read'

---

### Post by ramdisc on 2005-10-29
That's not exactly help.

The manual has over 35 pages, and those are the numericals.  There is an addition of like 20 more pages from the alphabetic listing.

At least give me the chapter and subchapter that might help me.  I wouldn't know where to look since I am not familiar with these programming terms.

---

### Post by toojays on 2005-10-29
What you want is section 4.2 of the manual, "Bash Builtin Commands". I'm looking at the info page (from the bash-doc package) rather than the man page.

Here's a small example which converts the entered string to uppercase:```
read -p "Enter a string to be uppercased: " foo
upper_foo=$(echo ${foo} | tr "[a-z]" "[A-Z]")
echo ${upper_foo}
```

---

