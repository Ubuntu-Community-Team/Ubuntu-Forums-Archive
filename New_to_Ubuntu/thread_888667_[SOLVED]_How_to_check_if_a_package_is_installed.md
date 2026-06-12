---
title: "[SOLVED] How to check if a package is installed?"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by appi2012 on 2008-08-13
I'm trying to create a bash script that needs to check if certain packages are installed, and if not, then install them. How can I do this?

---

### Post by Nepherte on 2008-08-13
You can see if it's installed with this command:
```
dpkg -s <packagename>
```

---

### Post by theyranos on 2008-08-13
[PHP]
if dpkg -s "$PACKAGE_NAME" 2>/dev/null 1>/dev/null; then
  echo "Package $PACKAGE_NAME is installed."
else
  echo "Package $PACKAGE_NAME isn't installed."
fi
[/PHP]

---

### Post by meindian523 on 2008-08-13
```
sudo apt-get remove <package name>
```
If it asks you whether you want to remove,it's installed.If it says,package not installed,so not removed,it's not installed.
In a GUI,open Synaptic,search for the package name,if the box corresponding to the package is green,it's installed,if blank,not.

---

### Post by ilrudie on 2008-08-13
dpkg-query -l 'evolution*'

replace evolution* with whatever package name you want.

---

### Post by hillbilly1980 on 2010-03-14
dpkg-query -s 'package name' 
if [ "$?" == "1" ]; then
 echo "package installed"
else
 echo "package not installed
fi

---

### Post by surfer on 2010-08-18
none of these work... [FONT="Courier New"]dpkg -l[/FONT] and [FONT="Courier New"]dpkg -s[/FONT] both return 0 whether the pakage is installed or not. any other ideas?

---

### Post by kristopolous on 2011-09-20
Because I don't see an answer here and I got here through google I'll provide an answer.  

The basic problem is that if you install then uninstall a package, dpkg -l <package> still return 0.

However, dpkg -L (list files) does not.

```
$ sudo apt-get remove curl
$ dpkg -L curl 
$ echo $?
```will show you the magic you want.

---

### Post by oldos2er on 2011-09-20
Closed for necromancy.

---

