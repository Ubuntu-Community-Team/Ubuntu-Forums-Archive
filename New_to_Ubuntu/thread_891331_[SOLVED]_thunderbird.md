---
title: "[SOLVED] thunderbird??"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by rixtr66 on 2008-08-15
i downloaded thunderbird and it gave me some kind of file i dont know what to do with.its not a source file,im not sure what it is .how do i make it work?
it was the standard thunderbird linux download.
rick

---

### Post by OutOfReach on 2008-08-15
Well I think an easier way to install Thunderbird is to goto Applications>Accessories>Terminal and type in:

```
sudo apt-get install thunderbird
```

;)

---

### Post by Victormd on 2008-08-15
search for it in synaptic or
```
sudo apt-get install thunderbird
```

---

### Post by Dougie187 on 2008-08-15
My bet is it's an executable.
Probably open a terminal and move to that folder they type
```
chmod 755 *filename*
```
then type
```
./*filename*
```

Or...
you can type
```
sudo apt-get install thunderbird
```

This will install the package using apt-get for you so you won't have to worry about it, then you can just run it by typing thunderbird.

---

### Post by rixtr66 on 2008-08-15
yeah im kicking myself,right after i wrote this post i tried apt-get,and gotit. thanks for the help though.
rick

---

