---
title: "please help"
date: 2015-12-05
forum: New to Ubuntu
---

### Post by chase13 on 2015-12-05
system error

E:Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list, E:The list of sources could not be read., E:The package lists or status file could not be parsed or opened.


what should i do ?

---

### Post by Geoffrey_Arndt on 2015-12-05
What version of Ubuntu?   I don't think the medibuntu repository is supported anymore.    Best to edit your sources list and remove that source.

---

### Post by matt_symes on 2015-12-05
Hi

Open a terminal and type or copy and paste this into it. It will delete your invalid source file.

```
sudo rm /etc/apt/sources.list.d/medibuntu.list
```

Enter your password when prompted. It will not be echoed to the screen. This is normal.

Then type

```
sudo apt-get update
```

In future you may want to add a more descriptive title than 'please help'.

Kind regards

---

### Post by chase13 on 2015-12-05
thank you very much

---

