---
title: "Mount iso without burning them"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by yamawho on 2008-05-23
Burning the iso's just to retrieve a file or just read it is becoming a real drag.

So far I found these links ...

[http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html](http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html)

and this on iso master which I found in synaptic ...

[http://ubuntufriends.wordpress.com/2007/03/31/edit-and-create-your-bootable-iso-image-the-easy-way/](http://ubuntufriends.wordpress.com/2007/03/31/edit-and-create-your-bootable-iso-image-the-easy-way/)

Which is the way to go ?

---

### Post by dnns123 on 2008-05-23
try gmount-iso

---

### Post by logos34 on 2008-05-23
> **yamawho said:**
> Burning the iso's just to retrieve a file or just read it is becoming a real drag.

all you have to do is right-click on .iso>open with archive manager>right-click file inside>extract

---

### Post by dnns123 on 2008-05-23
> **logos34 said:**
> all you have to do is right-click on .iso>open with archive manager>right-click file inside>extract

Thats also a perfect method. If your not stingy about disk space, you can do that. My method just opens the file and allows you to read and copy it. It's faster.

---

### Post by yamawho on 2008-05-23
> **dnns123 said:**
> try gmount-iso

gmountiso seems to be what I'm looking for.

Thanks for the replies guys.

---

### Post by txcrackers on 2008-05-24
Old school (in a terminal window)
```

mkdir $HOME/temp
sudo mount /path/to/iso -o loop $HOME/temp
# copy stuff
sudo umount $HOME/temp

```

---

