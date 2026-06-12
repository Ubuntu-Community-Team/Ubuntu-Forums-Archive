---
title: "Time parameters with find command"
date: 2011-11-03
forum: New to Ubuntu
---

### Post by casteurr on 2011-11-03
Hello, guys. So, I need to find a set of files that were modified between certain dates ( let's say 21.08.2011 and 14.09.2011 ) using the find command in the terminal. The problem is, I can not figure out how to do this and I would very much appreciate your help with this issue. Thank you! :)

---

### Post by Vaphell on 2011-11-03
```
find . -newer[COLOR="Blue"]m[/COLOR]t '20110821 0000' ! -newer[COLOR="Blue"]m[/COLOR]t '20110914 2359'
```

newer than D1, not (!) newer than D2 (=older than D2)

you need to test the date format to suit your needs, it is somewhat flexible (it can do '21 August 2011 12:00' but will crap out on '21/10/2011' because in this case it expects USian format of month/day/year)

m in blue indicates 'modify time', you can pick from [COLOR="Blue"]a[/COLOR]ccess/[COLOR="Blue"]m[/COLOR]odify/[COLOR="Blue"]c[/COLOR]hange

---

### Post by wolfen69 on 2011-11-03
I can help this much: say you want to find which have been modified in the last 15 days, you would do
```
find . -mtime -15
```
but I don't know how to modify it to specific times.

---

### Post by casteurr on 2011-11-12
So, I am still having a little bit of trouble using the find command. I need to find some files in a folder that end either in .jpg or .bmp, that are between 6k and 48k and that were modified between 11.06.2011 and 19.06.2011 or 24.07.2011 and 02.08.2011. 

I tried this:

find . \( -name '*.jpg' -o -name '*.bmp' \) \( -size +6k  ! -size +48k \) \(\( -newermt '20110611 0000' ! -newermt '20110619 2359' \) -o \( -newermt '20110724 0000' ! -newermt '20110802 2359' \)\)

but it doesn't work. Please help me. Thank you! :)

---

### Post by casteurr on 2011-11-13
:confused:

---

### Post by Vaphell on 2011-11-13
```
find . '(' -iname '*.txt' -o -iname '*.sh' ')' '(' -size +1k -size -40k ')' '(' '(' -newermt '20110724 0000' ! -newermt '20111111 2359' ')' -o '(' -newermt '20110101 0000' ! -newermt '20110422 0000' ')' ')'
```

granted, values of parameters are changed for my testing purposes but i get some results when i run find in this format in my junk folder. I think your version may fail because of (( and )) glued together.

---

### Post by Cyclane on 2011-11-13
never mind, see post above.

---

