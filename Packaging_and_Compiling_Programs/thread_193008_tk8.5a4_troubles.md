---
title: "tk8.5a4 troubles"
date: 2006-06-09
forum: Packaging and Compiling Programs
---

### Post by OrganicPanda on 2006-06-09
hey all i am having trouble getting tk8.5a4 to 'make': i get a nice output like:

```

SNIP
/home/panda/Desktop/tk/unix/../generic/tk3d.c:1253: error: syntax error before ‘)’ token
/home/panda/Desktop/tk/unix/../generic/tk3d.c:1256: error: syntax error before ‘)’ token
/home/panda/Desktop/tk/unix/../generic/tk3d.c:1256: error: syntax error before ‘)’ token
/home/panda/Desktop/tk/unix/../generic/tk3d.c:1257: error: syntax error before ‘)’ token
/home/panda/Desktop/tk/unix/../generic/tk3d.c:1277: error: request for member ‘borderTable’ in something not a structure or union
/home/panda/Desktop/tk/unix/../generic/tk3d.c:1277: error: request for member ‘borderTable’ in something not a structure or union
/home/panda/Desktop/tk/unix/../generic/tk3d.c:1281: error: syntax error before ‘)’ token
/home/panda/Desktop/tk/unix/../generic/tk3d.c:1283: error: syntax error before ‘)’ token
/home/panda/Desktop/tk/unix/../generic/tk3d.c:1283: error: syntax error before ‘)’ token
/home/panda/Desktop/tk/unix/../generic/tk3d.c:1284: error: syntax error before ‘)’ token
/home/panda/Desktop/tk/unix/../generic/tk3d.c: In function ‘TkDebugBorder’:
/home/panda/Desktop/tk/unix/../generic/tk3d.c:1364: error: ‘borderPtr’ undeclared (first use in this function)
/home/panda/Desktop/tk/unix/../generic/tk3d.c:1367: error: invalid operands to binary *
/home/panda/Desktop/tk/unix/../generic/tk3d.c:1367: error: syntax error before ‘)’ token
/home/panda/Desktop/tk/unix/../generic/tk3d.c:1370: error: request for member ‘borderTable’ in something not a structure or union
/home/panda/Desktop/tk/unix/../generic/tk3d.c:1370: error: request for member ‘borderTable’ in something not a structure or union
/home/panda/Desktop/tk/unix/../generic/tk3d.c:1372: error: syntax error before ‘)’ token
make: *** [tk3d.o] Error 1


```

this is most annoying as installing endless amounts of programes from source i have fallen at the last hurdle. 8.4 stable wont do because its missing features i need and 8.5a1, 8.5a2 and 8.5a3 all fail before that stage, can anybody suggest what could be causing all those errors?
cheers,
steve

---

### Post by WishMaster on 2006-06-09
I installed it succesfully on Dapper (using it for aMSN)

> cd .../tcl8.5a4/unix
./configure --prefix=/usr
make
sudo make install 

---

### Post by OrganicPanda on 2006-06-09
that was quick lol, yeah i got tcl8.5a4 installed fine but its tk that is givinf me the error,

thanks for the reply anyway

---

### Post by OrganicPanda on 2006-06-10
so no ideas then, damn it all lol i need amsn

---

### Post by panurge77 on 2006-06-13
You're probably missing some deps, so try this:
sudo apt-get build-dep tcl8.4 tk8.4

(they should be the same deps from the older version)

---

