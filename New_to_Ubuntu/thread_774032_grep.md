---
title: "grep"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by hungryOrb on 2008-04-29
Can I use grep to search for a string in the contents of files? Can't find any good examples :|

---

### Post by Monicker on 2008-04-29
Yes, of course.  That is pretty much the purpose of grep.

```
grep dog example.txt
```


That would search the file example.txt for all lines where "dog" appears.  By default grep is case sensitive.

If you want to search for "dog" but don't care about the case of the letters:

```
grep -i dog example.txt
```


That would find "Dog", "DOG", "dog", etc.


You can get more details here:

[http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_04_02.html]("http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_04_02.html")

---

### Post by Wim Sturkenboom on 2008-04-29
And for a complete string, place the string between double quotes
```

grep "my dog is called Ubuntu" example.txt

```
Which is true, by the way.

---

### Post by tacutu on 2008-04-29
grep can do a lot of nifty searches. Just google for "grep tutorials" or "grep examples" and you'll find plenty of info.

---

### Post by hungryOrb on 2008-04-29
> **Wim Sturkenboom said:**
> And for a complete string, place the string between double quotes
```

grep "my dog is called Ubuntu" example.txt

```
Which is true, by the way.

ROFL ;D So cool!

---

### Post by hungryOrb on 2008-04-29
Thanks guys, I did find some examples, just not ones that I could use, I'd like to be able to define exactly where it searches. For example, search all files within one directory '/etc/apache2'

---

### Post by tacutu on 2008-04-29
this should do the trick:
grep "my dog is called" /etc/apache2/*

or, if you want to search recursively in embedded folders, do:

grep -R "my dog is called" /etc/apache2/*

this will search (i) all the files immediately contained in /etc/apache2 but also (ii) all the files in any folders within /etc/apache2 (e.g. /etc/apache2/my-backup/)

---

### Post by hungryOrb on 2008-04-29
Thankyou! :] That was it

---

