---
title: "[SOLVED] How to install a downloaded program?"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by Anathallo on 2008-08-27
I downloaded songbird and it is on my desktop as a .tar.gz but I don't know how to install it from there. I looked at the stickied pages but I don't really understand what to do.

---

### Post by jonabyte on 2008-08-27
If you want to install from source here are the steps (from terminal--use sudo in front of the commands):

```

gunzip file.tar.gz
tar xf file.tar
./configure
make
make install

```

but it might be in the repositories and you can try this (again with a terminal):

```
sudo apt-get install program.ver.number.etc
```

---

### Post by david sousa on 2008-08-27
When you download a program like that the folder which you take out from the compressed file has an installation guide in a document that says "INSTALL". 

I usually put that folder at /opt as it is empty.

then type at terminal " cd /opt"

now just follow the instructions...

Now if you want something much simpler go here: [http://www.getdeb.net/download/3116/0](http://www.getdeb.net/download/3116/0) (direct download to songbird in .deb format, so the installation is automatic)
 ;)

---

### Post by wolfen69 on 2008-08-27
[Here]("http://www.getdeb.net/search.php?keywords=songbird") is a link to the .deb file of songbird. just click to install.

---

### Post by Anathallo on 2008-08-27
Ah thank you all for the replys. The .deb file was alot easier to install :) 
But how did you get it as a .deb?

---

### Post by wolfen69 on 2008-08-27
> **Anathallo said:**
> Ah thank you all for the replys. The .deb file was alot easier to install :) 
But how did you get it as a .deb?

not sure i understand your question. it has to be made into a .deb file. getdeb.net is a great place to find 1 click apps.

---

### Post by dmsymr on 2008-08-27
I had the same issue, so Ill tell you how I worked around it, although Im sure the great people on here in the know will explain the correct way to deal with it!
Ok, I downloaded the file to my desktop, then i double clicked it and requested that it 'extracted' to a location, usually its my desktop but I wanted the files to go into my home folder. after it extracted, I went into the file and found the executable file (the file that just says 'songbird.exe')and while pressing the left mouse button,dragged it to my top panel. I closed everything else down, and I now click the button on my top panel and it opens songbird up automatically!
I downloaded a .png image for songbird and dragged and dropped it onto the springy picture in the properties menu!

Like I said, this worked for me, and Im stumbling around in the dark with Ubuntu! ( until I found this forum!)

---

