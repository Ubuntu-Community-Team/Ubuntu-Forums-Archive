---
title: "Unable to see files created by script"
date: 2014-06-17
forum: New to Ubuntu
---

### Post by Michelle_Lister on 2014-06-17
Hi,

Firstly I would just like to say I am an absolute beginner and I am currently working through a "Linux for Dummies" type book.  

One of the tasks I am supposed to perform is creating a new folder using a specified script.  I used "mkdir /home/user/PDF" which didn't work so I tried "sudo mkdir /home/user/PDF".  This created the folder but when I looked in the "Home directory" in the user folder I could not see it even when showing hidden folders.  If I run "cd /home/user/PDF" the folder exists.  I assume this has something to do with permissions but I was under the impression I could create folders in my user directory without having to use sudo.  

Could someone please give me some advise on this.  I have since deleted the foler using "sudo rmdir /home/user/PDF" and just created one by adding a new folder in a widows fashion but this dosen't really help me learn anything.

Thanks

---

### Post by cariboo on 2014-06-17
you may have to restart the file manager, or press F5 to refresh the folder list.

---

### Post by buzzingrobot on 2014-06-17
Yep, you're right, they should work as you expect in your /home directory.  When you used "sudo", it created a directory owned by root.  That might account for what you saw, or didn't see.

Use 'ls' in a terminal to list files and you won't need to wonder about a file manager needing to be refreshed ot not.

By the way, hidden files are just ordinary files with a '.' (a period) prefixed to the name.

---

### Post by Michelle_Lister on 2014-06-17
Thanks for the reply...unfortunately this does not work.

---

### Post by Michelle_Lister on 2014-06-17
Thanks buzzinrobot.  Using ls showed that the folder was not there :(

I'm just not sure why I can't create the folder using "mkdir /home/user/PDF"

---

### Post by lisati on 2014-06-17
> **Michelle_Lister said:**
> Thanks buzzinrobot.  Using ls showed that the folder was not there :(

I'm just not sure why I can't create the folder using "mkdir /home/user/PDF"

Does the folder /home/user exist?

---

### Post by buzzingrobot on 2014-06-17
I'm going to guess the book has you writing a script that looks something like this, assuming "michelle" is your username:

```

#!/bin/bash

mkdir /home/michelle/PDF


```

If that's saved as "test.sh" and executed, the directory called 'PDF' will be created in /home/michelle.

---

### Post by ajgreeny on 2014-06-17
I presume you used your actual username in the commands and not just the word "user"?

---

### Post by Michelle_Lister on 2014-06-17
Yes the book gave the following script:

**mkdir /home/Michelle/test**

This is the responce I got;

[PHP]mkdir: cannot create directory ‘/home/Michelle/test’: Permission denied

cat help

cat: help: No such file or directory

mkdir /Home/Michelle/test

mkdir: cannot create directory ‘/Home/Michelle/test’: No such file or directory[/PHP]

Sorry Buzzingrobot, as I said I am very new to this so I am not sure what "test.sh" means

---

### Post by texpat on 2014-06-17
Don't capitalize.

[FONT=Courier New]/Home/Michelle/[/FONT] should probably be [FONT=Courier New]/home/michelle/[/FONT]

If you type 
```
whoami
```
in a terminal, it will return your user name. Make sure you use that exact name.

You can also substitute the [FONT=Courier New]/home/YOURUSERNAME/[/FONT] with [FONT=Courier New]~/[/FONT] and the OS will automatically insert the correct value there. Saves making mistakes.

---

### Post by steeldriver on 2014-06-17
Is your actual username Michelle - or is it michelle? Unlike Windows, Linux/Unix is case-sensitive. You can find out by typing

```

id -nu

```
or 
```

whoami

```

Similarly for '/Home' versus '/home'  - the standard is for Linux/Unix to use all lower-case /home and trying to create a new file or directory in /Home will result in an error

---

### Post by Michelle_Lister on 2014-06-17
Brilliant, thank you everyone. 

Looks like it should be michelle not Michelle.  I'm pleased it was something as simple as case-sensitivity.  I now have my folder.

:P

---

