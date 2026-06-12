---
title: "Python + MySQL... anyone?"
date: 2006-07-05
forum: Programming Talk
---

### Post by noob_Lance on 2006-07-05
Hey,

Im looking to develop a small application for some home purposes. And i was hoping i could use Python and use it to interact with MySQL. Does anyone know how this can be done? 

Thanks
~Lance

---

### Post by Daverz on 2006-07-05
I think you want the python-mysqldb package.  However, for a small app, I highly recommend using sqlite + pysqlite instead.  sqlite gives you most SQL92 features, and it's just a small dll that you can include with your app.

[http://initd.org/tracker/pysqlite](http://initd.org/tracker/pysqlite)

---

### Post by scxtt on 2006-07-05
what about PHP?

---

### Post by noob_Lance on 2006-07-05
php i could.. because its easy as hell after making a shopping cart (damn worst 4 months ever) but i prefer to install as little as possible to get it done. its nothing big.. so python will suit it just fine ^_^

---

### Post by Daverz on 2006-07-05
Another thing I should mention is dabodev:

[http://dabodev.com/](http://dabodev.com/)

---

### Post by scxtt on 2006-07-05
what other downloads besides php5 + apache2 would you need?

---

### Post by noob_Lance on 2006-07-05
dave... what is dabodev? the website isnt loading for me :(

~Lance

---

### Post by Daverz on 2006-07-05
[QUOTE=noob_Lance]dave... what is dabodev? the website isnt loading for me :(

~Lance[/QUOTE]

Yeah, they seem to be having problems right now.  It's a database application framework on top of wxpython.  Check out this screencast:

[http://leafe.com/screencasts/populategrid.html](http://leafe.com/screencasts/populategrid.html)

---

### Post by kripkenstein on 2006-07-06
I use Python+MySQL. As Daverz said, for tiny applications other solutions might be simpler/faster... but, I think it's useful to learn MySQL, seeing as it's so popular. You might find out later on in your life (or the project's life) that you need it, so any learning curve now will eventually pay off.

I learned how to interact Python with MySQL using this [very basic tutorial ]("http://www.kitebird.com/articles/pydbapi.html"). It's a good start. If you have any questions feel free to ask.

---

