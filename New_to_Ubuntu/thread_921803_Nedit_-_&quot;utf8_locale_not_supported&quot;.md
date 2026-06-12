---
title: "Nedit - &quot;utf8 locale not supported&quot;"
date: 2008-09-16
forum: New to Ubuntu
---

### Post by age99 on 2008-09-16
Hi, I'm using nedit, and each time I execute it from the terminal, it gives me the annoying message of "utf8 locale not supported".  I know it doesn't actually affect me using the program, but I would like to get rid of it. 

Thanks

---

### Post by Pro-reason on 2008-09-16
A program that can't even deal with UTF-8 is a bad program.  Use gedit or vim as your editor instead.

---

### Post by fbrauer on 2008-11-20
Nedit is a great program as it supports rectangular selections (unlike gedit),great syntax highlighting, etc. 
I got rid of the UTF-8 problems by adding the line
en_CA ISO-8859-1
to /var/lib/locales/supported.d/local, 
then 
$ sudo dpkg-reconfigure locales

Then run nedit with (note extra dot):
$ LANG=en_CA.ISO-8859-1 nedit

and create a convenient alias in .bash_aliases

---

