---
title: "error message installing Google Earth in terminal"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by Peterfc on 2008-09-19
Hi All

I need to install Google Earth so i searched for install Google Earth an answer from "drs305" seemed the answer i followed the first part in a terminal then the second part, but at the bottom of the second part No2 after it ran at the bottom was an error  I need to manually run 'dpkg and configure a. Sorry but what does this all mean. Thanks for reading

No1
 sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

No2 
sudo apt-get update && sudo apt-get install googleearth


No3 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
peter@peter-desktop:~$

---

### Post by acidsolution on 2008-09-19
You must have interupted apt-get any time before 
```

sudo dpkg --configure -a

```
will solve the problem 
and than try to install google earth

---

### Post by acidsolution on 2008-09-19
mark the thread solved if this help you :)

---

### Post by gjoellee on 2008-09-19
you should use Ultamatix and install software from that program. It is graphical and really easy! Download the .deb here [http://linux.softpedia.com/progDownload/Ultamatix-Download-24551.html](http://linux.softpedia.com/progDownload/Ultamatix-Download-24551.html)

---

