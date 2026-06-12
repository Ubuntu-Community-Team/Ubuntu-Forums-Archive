---
title: "Sofware sources downlaod server issue"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by idodos on 2008-08-07
First of all I am using 8.04.
I accidentally changed the download server for israel.
which is where i am from.. and now I can't find the the israeli server to add it back...
it doesn't seem to exist there, is there any way to change back to it?

---

### Post by idodos on 2008-08-07
Bump.

---

### Post by sharks on 2008-08-07
go to software sources(system---adminstration) , choose a server and reload it and see whether u find israel server . if u dont find it, choose best server.

---

### Post by idodos on 2008-08-07
the israeli server is not there... and the best server is not so good for me...

---

### Post by oliviacond on 2008-08-07
change the server to official/US
then,
open Terminal
```
sudo gedit /etc/apt/sources.list
```

find all the links, for example
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted

add il. to the link, for example
deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) hardy main restricted

then at the terminal,
```
sudo apt-get update
```

---

### Post by sharks on 2008-08-07
i think the main server is good.

---

### Post by armageddon08 on 2008-08-07
> **sharks said:**
> i think the main server is good.

yup....the main server works really well for me too....much better than most of the regional ones.

---

### Post by idodos on 2008-08-07
> **oliviacond said:**
> change the server to official/US
then,
open Terminal
```
sudo gedit /etc/apt/sources.list
```

find all the links, for example
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted

add il. to the link, for example
deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) hardy main restricted

then at the terminal,
```
sudo apt-get update
```

i don't really understand what i must do.. could you explain it differently?

---

### Post by tamoneya on 2008-08-07
> **idodos said:**
> i don't really understand what i must do.. could you explain it differently?

when you run the first command in the box it will open up a text file.  There will be a bunch of links.  You need to modify them to work with the Israeli server by putting "il." at the beginning.  Then you save the file and run the second command in order to get your computer in sync with the israeli servers.

---

