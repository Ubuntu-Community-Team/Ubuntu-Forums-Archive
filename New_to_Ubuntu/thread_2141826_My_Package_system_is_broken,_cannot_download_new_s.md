---
title: "My Package system is broken, cannot download new software"
date: 2013-05-03
forum: New to Ubuntu
---

### Post by cymbri on 2013-05-03
I think I tried to root download the worng version of open office or libre office. The errors I'm getting are related to libre office
I've tried sudo apt-get install -f
[FONT=arial]and the [/FONT][COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get autoremove gives me a similar error... I am a new linux/terminal user and I am completely stumped. Please help![/FONT][/COLOR]

---

### Post by ibjsb4 on 2013-05-03
Try
```

sudo apt-get clean && sudo apt-get update
```

---

### Post by cymbri on 2013-05-03
.I tried that code, but I am still getting the same errors regarding my package system being broken

---

### Post by QIII on 2013-05-03
Hello!

Do you get similar errors if you try to uninstall libreoffice and openoffice?

For example:
```
sudo apt-get purge libreoffice
```

What do you mean by "root download"?

---

### Post by cymbri on 2013-05-03
So it appears that I can neither install nor delete it... I tried to use the graphic interface to delete all files pertaining to libreoffice, I didn't think to actually uninstall it, and as far as I can tell I didn't actually get rid of all of the files pertaining to libreoffice


[IMG]http://imageshack.us/a/img42/568/uninstalllibreoffice.png[/IMG]

---

### Post by QIII on 2013-05-03
OK.

Again, what do you mean by "root download"?

How did you initially install LibreOffice and OpenOffice?

---

### Post by cymbri on 2013-05-03
i mean i tried to use the terminal to download open office because that's the only way you can as far as I know...
I down loaded libre office first with the download manager, and then i downloaded it online and tried to use the terminal to install it.

At this point I don't even care if I have to strip the computer and install xubuntu all over again, except that i can't find my usb storage device

---

### Post by ibjsb4 on 2013-05-03
I think I would manually remove libreoffice.

```
gksudo nautilus
```

Go to File System and search/remove libreoffice.

And since openoffice is a possibility, do the same for it.

---

