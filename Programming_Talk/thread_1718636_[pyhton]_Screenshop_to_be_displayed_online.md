---
title: "[pyhton] Screenshop to be displayed online"
date: 2011-03-31
forum: Programming Talk
---

### Post by Pyro.699 on 2011-03-31
Hey,

Im trying to create a web-app that will allow me to view snapshots of my desktop from a remote location. For example i could go to [http://MyComp/screen.php](http://MyComp/screen.php) and it would display the site. Id like to use the tag **<img src="./screen.py" />**. I do have python enabled on the web server. I just need a way for me to access the current x screen and get an image from it.

[edit]
After a bit of playing around i have this all setup...
[php]
def run(*args):
        import os
        os.system("import -window root -display :0.0 screen.png")
        return file("screen.png")
[/php]

Running that i get this in my /var/log/apache2/error.log
**import: unable to open X server `:0.0' @ error/import.c/ImportImageCommand/362.**

However, if i run that line in my ssh connection window. It runs fine...
[/edit]

Thanks
~Cody

---

### Post by Pyro.699 on 2011-04-01
I have also tried adding in localhost:0, localhost:0.0 and just :0 all  return errors. Could it be that user www-data does not have access to  the x display?

Thanks
~Cody

---

### Post by deadtom on 2011-11-01
Having this same problem. Did you ever get it figured out?

---

### Post by deadtom on 2011-11-01
Never mind. Figured out that I have to export HOME to make it work. :)

```
HOME=/home/blah export HOME
```

---

