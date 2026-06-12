---
title: "help needed with sed or another replacement tool"
date: 2011-11-18
forum: Programming Talk
---

### Post by ryanrio95 on 2011-11-18
hi there.

i need help with something

for example i have an file named example.txt that contains

Name=Ryan
Loves=Riome
Hates=Xbox360

and i want to change all the lines that are containing Loves=[wildcard] to change to Loves=PS3

I know that i can change Loves=Riome with the sed command like this

sed -i 's/Loves=Riome/Loves=PS3/g' example.txt

but can't it be done like this? or with another command

sed -i 's/Loves=[wildcard]\n/Loves=PS3\n/g' example.txt

so that it changes the lines that are containing Loves=[wildcard]
And not only change the line when Loves=Riome.

Greets. Ryan.

---

### Post by Vaphell on 2011-11-18
google regular expressions and read about them, they make life so much easier
.* = any sequence of characters (. = any char, * = 0-or-more)

```
echo 'Loves=whatever' | sed -r 's/(Loves=).*/\1PS3/' 
Loves=PS3
```
i could write loves=.*/loves=ps3 but i used selection group which you can reuse in replacement

---

### Post by Bachstelze on 2011-11-18
This looks like the kind of stuff Perl is good for.

---

### Post by ryanrio95 on 2011-11-19
> **Vaphell said:**
> google regular expressions and read about them, they make life so much easier
.* = any sequence of characters (. = any char, * = 0-or-more)

```
echo 'Loves=whatever' | sed -r 's/(Loves=).*/\1PS3/' 
Loves=PS3
```i could write loves=.*/loves=ps3 but i used selection group which you can reuse in replacement

Really thanks, i will use it this way now:
sed -i 's/Loves=.*/Loves=PS3/g' example.txt

**Another Question: how to use**
sed -i 's/Loves=.*/Loves=/usr/share/background/PS3.jpg/g' example.txt

This gives an expression because of the slashes after Loves=
How could i use the slashes?

Greets, Ryan.

---

### Post by Vaphell on 2011-11-19
you can either escape them with \ -> \/ (this tells sed 'these are not the /'s you are looking for)

```
$ echo Loves=crap | sed 's/Loves=.*/Loves=\/usr\/share\/background\/PS3.jpg/'
Loves=/usr/share/background/PS3.jpg
```
or pick another separator for readability (symbol you type after s is used to cut the expression to pieces)
```
$ echo Loves=crap | sed 's[COLOR="Blue"]:[/COLOR]Loves=.*:Loves=/usr/share/background/PS3.jpg:'
Loves=/usr/share/background/PS3.jpg
```

---

### Post by SeijiSensei on 2011-11-19
If you really have square brackets in the file ("[]") you'll need to escape those as well ("\[" and "\]") if you're matching with regular expressions.

---

### Post by Vaphell on 2011-11-19
i personally don't like escaping in sed regexes so i use enumeration to avoid escaping in case of [].^$ etc. (ok ] is tricky :-))
[abc123] = one of the following: abc123, so
[[] = literal [
[.] = literal dot
and **-r** to make (){} have their regex function in unescaped form
i am surprised that people don't use -r more often, it allows for much greater readability of the regexp.

---

