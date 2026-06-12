---
title: "File downloading and XML parsing"
date: 2011-10-23
forum: Programming Talk
---

### Post by xtjacob on 2011-10-23
Hello, I'm trying to write a program in C the requires me to download a XML file, parse it for data, and display parsed text from the file. What is the best way to do this? I cannot seem to find a way that makes sense. Thanks!

---

### Post by gsmanners on 2011-10-23
I don't know what you would do (or why) but if I wanted to parse XML, I'd probably start with this:

```
sudo apt-get libxml2-dev libxml2-doc
```

Then just look up the references in devhelp.

---

### Post by xtjacob on 2011-10-23
Well I'm trying to write a weather program, and the api for the website I'm using uses XML files, so I assumed I needed to parse them to get the information out of them. Unless there's a better way that I don't know about...

---

### Post by gsmanners on 2011-10-23
It's probably easier to parse than to download. See this if you need an example, I guess. [http://xmlsoft.org/examples/parse1.c](http://xmlsoft.org/examples/parse1.c)

---

### Post by Fallen_Demon on 2011-10-24
gsmanners is right on the XML part, libxml is your friend here. To grab the data from the site, you can use libcurl
```

sudo apt-get install libcurl-dev

```
From what I remember when I was playing with it, libxml takes in a file pointer. Not sure if it's possible to give it an URL

---

