---
title: "DBDesigner Error while executing Query:...... ERROR Message: libmidas.so.1:cannot op"
date: 2006-11-13
forum: Programming Talk
---

### Post by Marco Modesto on 2006-11-13
Using DBDesigner 4.0.5.4 in Ubuntu 6.06 Dapper Drake, I got this error when I was trying to make a SQL query in DBDesign:

"Error while executing Query:...... ERROR Message: libmidas.so.1:cannot open shared object file"

Solution:

Create a simbolic link to /path/to/DBDesigner4/Linuxlib/libmidas.so.1.0 in /usr/lib


Command: 
sudo ln -sf /usr/local/DBDesigner4/Linuxlib/libmidas.so.1.0 /usr/lib/libmidas.so.1

Restart DBDesign!


Others related problems (in spanish):
[http://www.unixmexico.org/modules.php?name=News&file=article&sid=1645](http://www.unixmexico.org/modules.php?name=News&file=article&sid=1645)

---

