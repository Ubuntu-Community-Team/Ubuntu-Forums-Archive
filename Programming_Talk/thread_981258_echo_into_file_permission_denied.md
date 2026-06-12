---
title: "echo into file permission denied"
date: 2008-11-13
forum: Programming Talk
---

### Post by craigp on 2008-11-13
from the user www-data i am trying to run this:

sudo echo -e "something" > /etc/apache2/sites-available/example.com.conf


now the reply i get when i run as su www-data i get:

"sh: /etc/apache2/sites-available/example.com.conf: permission denied"

Any help?
Cheers

---

### Post by taurus on 2008-11-13
```

sudo echo -e "something" > **sudo** /etc/apache2/sites-available/example.com.conf

```

---

### Post by rjack on 2008-11-13
Using tee```
echo "ciao" | sudo tee /path/to/file
```has one advantage: the program that outputs data is run as normal user, so it's safer in the general case where the program is not a simple "echo".

More on this topic in the [RootSudo]("https://help.ubuntu.com/community/RootSudo#Downsides of using sudo") wiki page.

---

### Post by sisco311 on 2008-11-13
```
echo -e "something" | sudo tee /etc/apache2/sites-available/example.com.conf
```

to append the file:
```
echo -e "something" | sudo tee **-a** /etc/apache2/sites-available/example.com.conf
```

---

### Post by craigp on 2008-11-13
thanks guys that worked perfectly

---

### Post by sisco311 on 2008-11-13
Cool!

Please mark the thread solved by selecting 
**Mark this thread as solved** from the [COLOR="Red"]**Thread Tools**[/COLOR].

---

### Post by Cracauer on 2008-11-13
Or 

sudo sh -c "echo foo > /blah"

---

