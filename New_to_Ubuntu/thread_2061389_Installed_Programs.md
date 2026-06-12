---
title: "Installed Programs"
date: 2012-09-22
forum: New to Ubuntu
---

### Post by Oldpeter on 2012-09-22
Is it possible to print (under the sub sections) of all the information output when you ask the Software Centre to show you all installed programs  i.e. The programs named and a short description of what it does.

Don't seem to be able to pick the information up with a Copy command and thus paste into a document for printing.

As an  alternative (or as well) would like the facility under dash of asking for the  same information by just searching on  the sub section i.e Audio    Thanks

---

### Post by Frogs Hair on 2012-09-22
You can copy and paste a description of each package from the synaptic package manager but you will need to install it. 

Open the application and search for the application, select the line where it appears and description will be displayed.

---

### Post by Cheesemill on 2012-09-22
Is this any good?
```
aptitude search '~i!~M'
```

You may need to install aptitude first by doing:
```
sudo apt-get install aptitude
```

---

