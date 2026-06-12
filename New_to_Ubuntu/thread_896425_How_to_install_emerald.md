---
title: "How to install emerald"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by lynx_hanan on 2008-08-21
Can anyone tell me how can i install emerald under compiz fusion. i have the fusion icon installed. And whats Beryl???

---

### Post by tarps87 on 2008-08-21
Try
```

sudo apt-get install emerald

```
I believe beryl has been replaced by emerald but I may be wrong

---

### Post by Troll_the_Great on 2008-08-21
You can install Emerald from Synaptic.Go to System-Administration-Synaptic Package Manager and in the "Search" bar type "Emerald".
Beryl is compiz in a way.Look at this link, it will explain better.
[http://www.beryl-project.org/](http://www.beryl-project.org/)
Cheers!

---

### Post by kpkeerthi on 2008-08-21
To have emerald decorate your window borders, see [http://wiki.compiz-fusion.org/Plugins/Decoration](http://wiki.compiz-fusion.org/Plugins/Decoration)

Beryl was a fork from compiz and was later merged back to compiz. There is no Beryl now.

---

### Post by lynx_hanan on 2008-08-21
Thanks a lot fellows

---

### Post by lynx_hanan on 2008-08-21
Dnt i have to add a repository for emerald
????

and i cant find on synaptics, i searced it didnt return any results.

---

### Post by kpkeerthi on 2008-08-21
[http://packages.ubuntu.com/hardy/emerald](http://packages.ubuntu.com/hardy/emerald)

Do you have 'Universe' repository enabled under System -> Admin -> Software Sources ?

---

### Post by tuxxy on 2008-08-21
Compiz replaced Beryl, 

```
sudo apt-get install emerald
```

To run emerald type

```
emerald --replace
```

---

### Post by lynx_hanan on 2008-08-21
Its working. i installed it.Ive also heard that we can get new themes by searching in Emerald Theme Managers Window. Can preview themes and install them from here ??? if so how. some Key needs to be added. plz guide me

---

### Post by tuxxy on 2008-08-21
To install new emerald themes download them [from here]("http://www.gnome-look.org/index.php?xsortmode=down&page=0&xcontentmode=102")

Once they are downloaded to your Desktop, make sure emerald is open and just drag and drop the tar.gz file into emerald :)

---

### Post by lynx_hanan on 2008-08-21
yes i know that. but there is a way in which it does it self. fetches the themes sort of. something abt a GPG key or something

---

### Post by tuxxy on 2008-08-21
I always did it this way, theres also a large emerald theme package in the repos, lots of themese there too.

---

