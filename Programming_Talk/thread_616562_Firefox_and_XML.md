---
title: "Firefox and XML"
date: 2007-11-18
forum: Programming Talk
---

### Post by Dannik on 2007-11-18
My firefox cannot resolve external entities in xml file.
file.xml
```

<?xml version="1.0"?>
<!DOCTYPE ROOT [
<!ENTITY ent1 SYSTEM "ent1.xml">
]>
<ROOT>
&ent1;
</ROOT>

```
ent1.xml
```

<FOO>bar</FOO>

```

Firefox shows empty ROOT "<ROOT></ROOT>". What's the deal?

---

### Post by Kadrus on 2007-11-18
mmm..try using Epiphany web browser...
If you want to install it type 
```
sudo apt-get install epiphany-browser

```

It's pretty good..

---

### Post by Dannik on 2007-11-18
It shows the same thing. I am so lost. Internet Explorer on my windows PC has no problem displaying the file :(

---

### Post by Kadrus on 2007-11-18
mmm..weird...you might not want to try this but you can install opera
Download it from here:[http://www.opera.com/download/index.dml?platform=linux](http://www.opera.com/download/index.dml?platform=linux)

Open terminal and type this:
```
sudo dpkg -i opera_9.10-20061214.6-shared-qt_en_i386.deb
```
Open Applications--->Internet--->and Opera
Hope it will work :)

And if it doesn't  work you can always try installing Internet Explorer under wine...

---

### Post by Dannik on 2007-11-18
Ok, so I found out that Mozilla does not support external parsed entities. The only thing that is left for me to try is wine IE. But there must be some other way for me to test xml files on Linux, right?

---

### Post by Kadrus on 2007-11-18
mm..don't think so..at least not as far as I am concerned...did u try Opera?I think it works on it..

---

### Post by Vadi on 2007-11-18
XML Copy editor ([click]("http://www.getdeb.net/search.php?release=Dapper&keywords=xml+copy+editor"))

---

### Post by Kadrus on 2007-11-18
> **Vadi said:**
> XML Copy editor ([click]("http://www.getdeb.net/search.php?release=Dapper&keywords=xml+copy+editor"))
I found that pretty neat indeed...

---

### Post by Dannik on 2007-11-18
Ah! Opera worked thank you for your advice!  Couldn't try XML Copy Editor as I have Debian installed :)

---

### Post by Kadrus on 2007-11-18
> **Dannik said:**
> Ah! Opera worked thank you for your advice!  Couldn't try XML Copy Editor as I have Debian installed :)
Glad to help:)

---

### Post by Vadi on 2007-11-18
> **Dannik said:**
> Ah! Opera worked thank you for your advice!  Couldn't try XML Copy Editor as I have Debian installed :)

Ah, sorry. There's their homepage ([click]("http://xml-copy-editor.sourceforge.net/")), you can build it from source.

---

### Post by LaRoza on 2007-11-18
> **Dannik said:**
> Ah! Opera worked thank you for your advice!  Couldn't try XML Copy Editor as I have Debian installed :)

Here's a deb: [XML Copy Editor -- .deb]("http://www.getdeb.net/search.php?keywords=xml+copy+editor")

---

