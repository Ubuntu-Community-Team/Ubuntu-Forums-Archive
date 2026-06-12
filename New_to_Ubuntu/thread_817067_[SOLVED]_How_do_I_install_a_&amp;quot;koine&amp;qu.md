---
title: "[SOLVED] How do I install a &amp;quot;koine&amp;quot; Greek font"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by Berean on 2008-06-03
Hi,

I've been using Ubuntu for a little while, but have used XP for some things.  Now wanting to switch completely to Linux, can anyone recommend a Greek (koine) font that will work in Ubunut/Open Office 2.4, and tell me how to install it, please?  Thanks in advance.  Regards,

---

### Post by Stefanie on 2008-06-03
do you need every possible diacritic (spiritus lenis and asper, the three accents, coronis, special symbols and all combinations) ?

---

### Post by Stefanie on 2008-06-03
this site [http://www.translatum.gr/fonts/](http://www.translatum.gr/fonts/) contains a link with greek fonts for linux. 
i always use latex with the teubner package, but if you want to use openoffice that won't help you i'm afraid.

---

### Post by Berean on 2008-06-03
> **Stefanie said:**
> do you need every possible diacritic (spiritus lenis and asper, the three accents, coronis, special symbols and all combinations) ?

It's not absolutely necessary for all those you mention, but accents would be nice.  I'm no expert, but in the middle of writing an intermediate essay so have some experience of koine Greek (ie New Testament).  From this, you may deduce that I do/n't need what you've mentioned.  Thank you for your advice.

---

### Post by Stefanie on 2008-06-03
for texts from the new testament, i'd recommend using accents and spiritus's. which fonts do you use in windows, spionic, sgreek, wingreek,...? 
on this page you can find an overview of greek fonts : [http://perswww.kuleuven.be/~u0013314/greekg/fonts.htm](http://perswww.kuleuven.be/~u0013314/greekg/fonts.htm) . you can use the first one, sgreek, with openoffice. i tried it (in hardy) and it works perfectly. to do this you first need to install the msttcorefonts:
```

sudo apt-get install msttcorefonts
```
then you can download sgreekfixed.ttf : [http://www.clas.ufl.edu/users/pcraddoc/dfgib/SGFIXED.TTF](http://www.clas.ufl.edu/users/pcraddoc/dfgib/SGFIXED.TTF) 
put this .TTF file in the hidden folder .fonts (in your home folder, in nautilus it will become visible after clicking view -> show hidden files).  
when you do this the font will immediately be available in openoffice. 

if you want a keyboard map, you can find it here: [http://www.sbh-gent.be/Grieks/toetsenbordSgreekFixed.doc](http://www.sbh-gent.be/Grieks/toetsenbordSgreekFixed.doc)  you have to use the sgreekfixed font on the first column in order to see the greek letters.

---

