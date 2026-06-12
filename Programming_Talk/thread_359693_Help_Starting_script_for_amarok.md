---
title: "Help: Starting script for amarok"
date: 2007-02-12
forum: Programming Talk
---

### Post by hanexar on 2007-02-12
Hi, 

I'm looking for help to write a simple script for amarok. 

Here's my problems: all my music files are on an external hard drive and if I start amarok without starting the external drive first, it lost the collection and have to rebuild it all... and it's quite long ! So I'm looking for a script that prevent amarok opening if the external drive is not mounted. Something simple like
```

if usbdisk = unmounted then error message: "please mount usbdisk"
else
amarok
fi
```
As you see, I have (almost) no knowledge in any kind of programming, that's why I'm asking for a hand ;) If anyone know any easy resources I could use in the future, I would also be appreciate ;)

thanx

---

### Post by kebes on 2007-02-12
Just off the top of my head, I think a script like this would work.

```

#!/usr/bin/python
import os

if os.path.exists("/media/usbdrive/file.txt"):
  os.system('amarok &')
else:
  print "USB drive seems not to be mounted..."

```


Remember that you have to set the file as executable. Let's say you saved the above in a file "start_amarok", you would go:
sudo chmod +x start_amarok


Then execute with:
./start_amarok

(or click on its icon...)



Hope that helps.

---

### Post by hanexar on 2007-02-12
Thanx a lot! You rocks ;)

Is there a way to make the print appear in a pop-up box in case I'm trying to start the script with the icon?

Thanx again!

---

### Post by kebes on 2007-02-12
Oops, in my above instructions I said to do "sudo chmod ..." but you don't need the "sudo" part, just:
chmod +x start_amarok


As for creating a popup, there are many ways... one of the easiest is to use "zenity". So in python you would issue a command like:

```

#!/usr/bin/python
import os

if os.path.exists("/media/usbdrive/file.txt"):
  os.system('amarok &')
else:
[COLOR="Red"]  os.system('zenity --text "USB drive seems not to be mounted." --info')[/COLOR]

```


Make sure you change the ".path.exists" to look for a file/directory that will only be present once the drive is mounted! Hope it works.

---

### Post by hanexar on 2007-02-12
Exactly what I was looking for!

Thanx again, it's working great!

---

