---
title: "Bash special characters"
date: 2010-06-11
forum: Programming Talk
---

### Post by j_arquimbau on 2010-06-11
I'm getting a spanish random words generator and I'm having trouble with special characters: I get 

[LIST]
[*]kilocalor&#65533;a
[*]concejal&#65533;a
[/LIST]

instead of 
[LIST]
[*]kilocaloría
[*]concejalía
[/LIST]

which is weird, as I can, for instance, acces to the image folders typing
```
:~$ cd Imágenes 
```

Can anybody help me with this?

Thank you!

PS: I'm also having trouble with the been program as nothing sounds when I type 
```
beep
``` (speakers are on ;))

---

### Post by geirha on 2010-06-11
Sounds like that word generator outputs words in a specific character encoding, ignoring your current one. Is that a program you got from the ubuntu repositories?

---

### Post by j_arquimbau on 2010-06-11
Hello geirha and thank you for answering. The program is, in fact, a bash script which uses for the output head and tail:

```
l=$(cat diccionario);n=$(( 100+(`od -An -N2 -i /dev/urandom` )%(49308-0+1) ));cat diccionario |  head -n$n | tail -n1
```

The words are in a clear text file (diccionario).

It might be important to know that I've tried the bash script in the mobile terminal of the iphone and there is no problem with the special characters of the words listed (there are problems whith the characters when using the echo command for other outputs, though).

Thank you again!

---

### Post by j_arquimbau on 2010-06-11
OK, it was simple... Sorry for any inconvenience... I had to add another encodig (ISO...)
[IMG]http://img819.imageshack.us/img819/9051/pantallazoo.png[/IMG]

---

### Post by geirha on 2010-06-11
Better to just convert it to your current locale. Try
```
#!/bin/bash
dict=diccionario
n=$(wc -l < "$dict")
r=$(( $(od -An -N3 -i /dev/urandom) % n + 1 )
sed -n "$r{p;q;}" "$dict" | iconv -f iso-8859-15

```

---

### Post by j_arquimbau on 2010-06-12
Thank you! I'm going to try.

---

### Post by j_arquimbau on 2010-06-12
I've realized that the problem was on editting the dictionary file: I took that one from /usr/share/myspell and edited it. If I copy the words and paste them in a new document, there is no problem any more.

---

