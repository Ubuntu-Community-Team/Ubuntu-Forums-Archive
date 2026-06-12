---
title: "Pictures"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by tilley661 on 2008-10-13
OK i know there i probably no way, but when i installed Ubuntu i had backed up everything, but i lost my pictures in the process. when i installed Ubuntu i wiped windows off the system and started a fresh (windows was a nightmare). i don't suppose there is any possible way of searching deep into the hard drive and getting them pictures back ?

thanks, 
dan

---

### Post by Nxion on 2008-10-13
To be honest there is no EASY way to recover them. It has been my experience that you would have to use some 3rd party forensics software to recover the data. Since you say you reloaded over the top of windows, I would say the data if pretty fragmented now. The only other possible solution is to take the hard drive to a place that does data recovery, but they can be time consuming and very pricey.

---

### Post by spiderbatdad on 2008-10-13
maybe photorec. It can potentially put 1000's of images into your home folder, but with root ownwership and limited permissions...you will need to learn how to re-assign ownership in bulk, if you are successful...The command involves sudo chown & sudo chmod...it is not too difficult. First see if you can get the files.
The program photorec may have been absorbed by testdisk...not sure. Check synaptic package manager or ```
sudo apt-get install testdisk
man testdisk
```

---

### Post by spiderbatdad on 2008-10-13
ok looks easy enough install testdisk then run```
sudo photorec
```

---

### Post by tilley661 on 2008-10-19
this seems to something, but the directories i get come as:
 
  d empty
1 * linux
3 E extended
5 L linux swap

and i have no idea which one to pick :(

---

