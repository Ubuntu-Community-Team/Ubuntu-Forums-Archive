---
title: "wget downloading with a python dictionary??"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by pluckypigeon on 2008-06-13
is their a way that I could create a dictionary of links and get wget to download each simultaneously without re typing?

could python be useful?

Eg 

wget http://mysite.com/{dictionary}


dictionary = "apple.html", "pear.html", "banana.html"

Any ideas?

---

### Post by aktiwers on 2008-06-13
I am not completely sure what you mean. Check wgets man page:
[http://linuxreviews.org/man/wget/](http://linuxreviews.org/man/wget/)

or type :
```
man wget
```
in terminal.

Do you just want to download all the stuff in [http://mysite.com/folder/](http://mysite.com/folder/) ?
Then I believe:
```
wget -r http://mysite.com/folder/
```

Would do the trick..  or if you only want .html files:
```
wget -r -np -A html -l 2 http://mysite.com/folder/
```

---

