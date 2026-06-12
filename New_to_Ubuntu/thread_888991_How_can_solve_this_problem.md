---
title: "How can solve this problem"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by hocine20 on 2008-08-13
Big problem not find a solution
some pro crashed in ubunu 	
Especially firefox
	
I learned that the problem is **[COLOR="Red"]Segmentation fault[/COLOR]**
How can solve this problem
	
This already precarious 
	
I welcome suggestions
[IMG]http://ibncheikh.googlepages.com/Screenshot-3.png[/IMG]

---

### Post by Crafty Kisses on 2008-08-13
Have you tried reinstalling Firefox?

---

### Post by hocine20 on 2008-08-13
yes

---

### Post by wirelessmonkey on 2008-08-13
Remove and reinstall firefox.
sudo apt-get remove firefox
sudo apt-get install firefox

---

### Post by OffAxis on 2008-08-13
which version?

```
sudo aptitude install firefox-2
```

or 
```

sudo aptitude install firefox-3.0
```

?

you could try the other one and see if it works.

---

### Post by wirelessmonkey on 2008-08-13
If these aren't working, try sudo dpkg-reconfigure -a

---

