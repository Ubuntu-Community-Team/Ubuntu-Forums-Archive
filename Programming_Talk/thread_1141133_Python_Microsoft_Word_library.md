---
title: "Python Microsoft Word library"
date: 2009-04-28
forum: Programming Talk
---

### Post by Kilon on 2009-04-28
Which one is the best ? I want to able to access the files and modify them with python .

---

### Post by Kilon on 2009-04-28
forgot to add that the library should be at least for ubuntu , windows and macos. 

I am opening to any suggestion . I will accept any kind of library even one that offers only limited amount of WORD functionality.

---

### Post by myrtle1908 on 2009-04-30
I'm not sure that there are libraries for this in Python (however I'm guessing).

If you can go with Java there is an excellent offering from a company named Aspose which offers non-COM interfaces to most of the Microsoft range of Office products.  Its is expensive but very powerful.  It is best used when multi-user/server-side MS document manipulation/generation is required.

The poor mans option would be to use COM automation but obviously this is windows only and blows for any hardcore multi-user processing.

---

### Post by Kilon on 2009-05-01
> **myrtle1908 said:**
> I'm not sure that there are libraries for this in Python (however I'm guessing).

If you can go with Java there is an excellent offering from a company named Aspose which offers non-COM interfaces to most of the Microsoft range of Office products.  Its is expensive but very powerful.  It is best used when multi-user/server-side MS document manipulation/generation is required.

The poor mans option would be to use COM automation but obviously this is windows only and blows for any hardcore multi-user processing.

Yes I asked around and seems there is not any. 

Well I only want basic DOC functionality so I probably hack a basic library myself. It should not be too hard.

---

### Post by myrtle1908 on 2009-05-01
In that case this will probably help you ...  [http://download.microsoft.com/download/0/B/E/0BE8BDD7-E5E8-422A-ABFD-4342ED7AD886/Word97-2007BinaryFileFormat(doc)Specification.pdf](http://download.microsoft.com/download/0/B/E/0BE8BDD7-E5E8-422A-ABFD-4342ED7AD886/Word97-2007BinaryFileFormat(doc)Specification.pdf)

---

### Post by Kilon on 2009-05-01
> **myrtle1908 said:**
> In that case this will probably help you ...  [http://download.microsoft.com/download/0/B/E/0BE8BDD7-E5E8-422A-ABFD-4342ED7AD886/Word97-2007BinaryFileFormat(doc)Specification.pdf](http://download.microsoft.com/download/0/B/E/0BE8BDD7-E5E8-422A-ABFD-4342ED7AD886/Word97-2007BinaryFileFormat(doc)Specification.pdf)

thanks i have already downloaded it as someone suggest it in the python irc channel. 

Too much info for my brain but it is good to have a detailed idea about the format.

---

### Post by loell on 2009-05-01
your best bet would be to manipulate the file via Python UNO for openoffice, even then, there's no assurance that the formated file won't break down if opened in Microsoft word.

---

### Post by Kilon on 2009-05-01
> **loell said:**
> your best bet would be to manipulate the file via Python UNO for openoffice, even then, there's no assurance that the formated file won't break down if opened in Microsoft word.


Thanks thousand times!!! 

Will I need to run it from inside open office or can it work independently ?

---

### Post by loell on 2009-05-01
it is run alongside openoffice, so you need to run OO writer with a parameter to accept socket connection.

then in separate python script
you just.

```
import uno
```

---

### Post by Kilon on 2009-05-01
> **loell said:**
> it is run alongside openoffice, so you need to run OO writer with a parameter to accept socket connection.

then in separate python script
you just.

```
import uno
```

oh I see, well it is better than nothing at all. Thanks. I will give it a try.

---

