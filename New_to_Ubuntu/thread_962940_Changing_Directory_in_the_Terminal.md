---
title: "Changing Directory in the Terminal"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by bakentake on 2008-10-29
In the windows viewer the place I need to get to is:

/home/zach/.wine/drive_c/Program Files/Funcom/Anarchy Online

so I open terminal and type:

cd /home/zach/.wine/drive_c/Program Files/Funcom/Anarchy Online



but it wont switch to the directory.

---

### Post by Zzl1xndd on 2008-10-29
You may need quotes as in 

cd "/home/zach/.wine/drive_c/Program Files/Funcom/Anarchy Online"

because of the space in Anarchy Online

---

### Post by OutOfReach on 2008-10-29
Try this:
```

cd /home/zach/.wine/drive_c/Program\ Files/Funcom/Anarchy\ Online

```

---

### Post by Rocket2DMn on 2008-10-29
You can't have space in the name for anything in terminal.  To get around this you either use quotes or the escape character.  The quote example is above, here is with the \ escape character:
```
cd /home/zach/.wine/drive_c/Program\ Files/Funcom/Anarchy\ Online
```
Tab complete is also amazingly useful, just type a few letters and hit TAB - it will autocomplete the name.  If it doesn't fully autocomplete then you have not provided a unique enough set of letters, so just hit tab twice to see your remaining options and keep typing.

---

### Post by Teabicky on 2008-10-29
Just been having this problem myself, I found that quotation marks around directories and files with spaces in helped e.g.

cd /home/zach/.wine/drive_c/"Program Files"/Funcom/"Anarchy Online"

Hope this works....

---

### Post by nhasian on 2008-10-29
[TAB] is your friend.  it autocompletes filenames/directories in terminal.  Even ones with spaces in it :)

---

### Post by porteclefs on 2008-10-29
It should work fine to just put " " around Anarchy Online... it's the space that's messing up your syntax

---

### Post by Miguellint on 2008-10-29
You can also drag a folder onto the terminal and it will do the quotation marks thing automatically. Just make sure you type cd and then hit the spacebar before you drag the folder

Regards

---

### Post by bakentake on 2008-10-30
Wow I didn't expect so many replies, thanks to everyone who took the time I just learned three new ways to do what I wanted. :)

---

### Post by MasterNetra on 2008-10-30
Here is another. use the wild card * for spaces.

---

