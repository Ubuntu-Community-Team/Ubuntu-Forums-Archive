---
title: "How do I remove these folders?"
date: 2008-05-29
forum: Philippine Team
---

### Post by killer_d76 on 2008-05-29
i have installed some windows programs on wine to test what best suits for  my need, now that i have chosen which program to use and succesfully uninstalled all the unnescessary programs, but it left all the folders behind (see attached pic).. so how do i remove these folders? :confused:

thanks po! ;)

[ [IMG]http://www.imagehosting.com/out.php/i1767213_Screenshot.png[/IMG]](http://www.imagehosting.com)

---

### Post by renzokuken on 2008-05-29
those folders are located at

```
/home/*username*/.wine/drive_C/Program\ Files/
```

you can either browse to them with nautilus (use Ctrl+H to view hidden folders i.e. .wine) and delete them that way or use the terminal to cd to the parent directory and remove them recursively

---

### Post by killer_d76 on 2008-05-29
> **renzokuken said:**
> those folders are located at

```
/home/*username*/.wine/drive_C/Program\ Files/
```

you can either browse to them with nautilus (use Ctrl+H to view hidden folders i.e. .wine) and delete them that way or use the terminal to cd to the parent directory and remove them recursively


thanks renzokuken for quick reply.. i have tried that first option already and those folders are still there.. here's what on my Program Files and these folders left are folders used on my remaining program..

[ [IMG]http://www.imagehosting.com/out.php/i1767334_Screenshot.png[/IMG]](http://www.imagehosting.com)




could you guide me on how to do the second option, i mean using the terminal, am not really good at this.. thanks

---

### Post by renzokuken on 2008-05-29
ok, did a bit googling and found this

[http://techxplorer.com/2008/04/21/removing-wine-application-entries-on-ubuntu/](http://techxplorer.com/2008/04/21/removing-wine-application-entries-on-ubuntu/)

see if that helps

---

### Post by killer_d76 on 2008-05-29
thanks renzokuken!.. this procedure removed the folders!..

 "Alternatively you can use the File Browser if you prefer. The .local directory is in your home directory. If you can’t see it use the <ctrl>+h keyboard shortcut to show hidden files."
 

...using this procedure i was able to see those two folders, then i tried deleting those two and voila!.. :guitar:

[ [IMG]http://www.imagehosting.com/out.php/i1767434_Screenshot.png[/IMG]](http://www.imagehosting.com)

---

### Post by renzokuken on 2008-05-29
awesome, congrats........

---

