---
title: "[bash] Popup/alert window?"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by linkmaster03 on 2008-07-31
How can I spawn a popup/alert window from a terminal? I am on GNOME.

---

### Post by ConMan318 on 2008-07-31
Read up on 'xmessage'.

```

man xmessage

```

---

### Post by unutbu on 2008-07-31
```
zenity --error --text 'Hi linkmaster03!'
``` or
```
zenity --info --text 'Hi linkmaster03!'
``` or
```
zenity --warning --text 'Hi linkmaster03!'
```
For more options, type

```

man zenity
```

---

### Post by linkmaster03 on 2008-07-31
Thanks unutbu, that's exactly what I was looking for! :D :D

---

### Post by ferarg on 2009-08-19
Great Info, I didn't know that this soft, zenity, exist!

Thanks a lot



-= FErArg =-

[www.FErArg.com](www.FErArg.com)
[www.SerInformaticos.es](www.SerInformaticos.es)

---

### Post by Tibuda on 2009-08-19
If you want to popup a notification, you can install [libnotify-bin]("apt:libnotify-bin") and use notify-send.

---

### Post by r.lopez.negrete on 2010-03-18
Hi all,

Is there any way I can have this popup appear at login?

thanks,
 Rodrigo

---

### Post by pareshverma91 on 2010-08-04
hi @^,
You could do this by modifying the startup processes.
You could first make a bash script of it
```
#! /bin/bash 
{then your code as mentioned above}
```make it executable using```
chmod 777 filename
```Now, go to System > Preferences > Startup Applications
Click on the Add button.
Fill in the any desired name and browse in the file location in the command tab (basically you would end up with a command sth  as /<somepath>/filename).
And you are done with it.

(You could also make it a command by moving the file to /usr/bin folder)

---

