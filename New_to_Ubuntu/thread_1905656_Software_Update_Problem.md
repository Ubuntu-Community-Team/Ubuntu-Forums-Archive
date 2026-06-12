---
title: "Software Update Problem"
date: 2012-01-07
forum: New to Ubuntu
---

### Post by krishkochi on 2012-01-07
Hello,

I am quite new to Ubuntu and I am just learning things. 

A couple of days ago there was an error in the automatic update process run by the Ubuntu Software Center.
Now a red circle icon appears on the Taskbar and Software Center is not opening. 
The error that I got when I ran the "apt-get update" command is "E: Malformed line 61 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read."

I am running Ubuntu 11.10.

Please help.

---

### Post by 2F4U on 2012-01-07
The error message says it, there is something wrong in your /etc/apt/source.list file at line 61. Open the file and correct the problem or post the file here.

---

### Post by Old_Grey_Wolf on 2012-01-07
Post the output of this command ```
cat /etc/apt/sources.list
```

---

### Post by androssofer on 2012-01-07
> **krishkochi said:**
> Hello,

I am quite new to Ubuntu and I am just learning things. 

A couple of days ago there was an error in the automatic update process run by the Ubuntu Software Center.
Now a red circle icon appears on the Taskbar and Software Center is not opening. 
The error that I got when I ran the "apt-get update" command is "E: Malformed line 61 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read."

I am running Ubuntu 11.10.

Please help.

seems like an error in your sources list....

do 

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
```

this makes a backup of the list. then do

 ```
sudo gedit /etc/apt/sources.list
```

and it will open a text editor, with you sources list in it. go to line 61, delete it, hit save. and try updating... 

```
apt-get update
```

thats what i would do.. cant guarantee it will work. and someone else might have a better suggestion.. but is worth a try ;-)

---

### Post by Paqman on 2012-01-07
Can you post the contents of your /etc/apt/sources.list inside some [noparse]```

```[/noparse] tags?

---

