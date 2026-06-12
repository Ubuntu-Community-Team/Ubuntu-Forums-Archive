---
title: "deleting fonts"
date: 2012-06-14
forum: New to Ubuntu
---

### Post by tojonukokhadush on 2012-06-14
how can i delete unused fonts or fonts i do not like to use in open office in ubuntu 10.04?

---

### Post by cortman on 2012-06-14
Any number of [these links]("http://www.google.com/search?sugexp=chrome,mod=13&sourceid=chrome&ie=UTF-8&q=how+to+delete+fonts+in+ubuntu") would help you. The first one seems to address it specifically.

---

### Post by Cheesemill on 2012-06-14
Open a file browser with root access by typing:
```
gksudo nautilus
```
Navigate to /usr/share/fonts and delete any unwanted fonts.
Then rebuild the font cache by doing:
```
sudo fc-cache -f
```

---

