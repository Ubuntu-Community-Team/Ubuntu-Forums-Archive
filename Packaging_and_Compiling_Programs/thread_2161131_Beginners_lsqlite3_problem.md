---
title: "Beginners lsqlite3 problem"
date: 2013-07-09
forum: Packaging and Compiling Programs
---

### Post by toshe5kov on 2013-07-09
Known story: I am a web developer and I wanted to try using QT Creator Ubuntu SDK after tryed to build simple c++ html5 app i got an error msg saying "cannot find -lsqlite3" and off course "collect2: id retirned 1 exit status". I guess there is some dev package i need but still is there need to configure QT...? Here I attached a image, hope can help you help me. Thanx in advance...  :confused:
 

[ATTACH=CONFIG]244553[/ATTACH]

---

### Post by Kujua on 2013-07-09
This should fix your sqlite3 linking error:
```
sudo apt-get install libsqlite3-dev
```

---

### Post by toshe5kov on 2013-07-10
#-o problem solved **thnx Kujua** qt platform is a worthy peace of technology :P

---

