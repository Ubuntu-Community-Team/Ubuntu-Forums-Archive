---
title: "Gambas script help PLEASE!!"
date: 2005-09-20
forum: Programming Talk
---

### Post by mhancoc7 on 2005-09-20
I am working on a little program with Gambas. I am a novice programmer.

I am using a script to open some of the common Linux configuration files such as menu.lst. I can successfully open the files with gedit, but they are Read/Only. I can't figure out how to run the script with sudo and have the password entered automatically either from a testbox in my app or just prompted for. 

Can someone please help me with this. I would really appreciate it.

Here is my script so far.```
' Gambas class file
PUBLIC FUNCTION Call(cmd AS String) AS String
DIM result AS String
DIM s AS String
result = ""
s = Temp()
SHELL cmd WAIT 
TRY result = file.Load(s)
TRY KILL s
RETURN result
END

PUBLIC SUB GrubEdit_Click()
PRINT Call("gedit /boot/grub/menu.lst")
END

PUBLIC SUB FstabEdit_Click()
PRINT Call("gedit /etc/fstab")
END

PUBLIC SUB ModulesEdit_Click()
PRINT Call("gedit /etc/modules")
END
```

God Bless and Thank you in advance, Jereme

---

### Post by damvcoool on 2006-12-04
why dont you just compile the app, and run it with sudo after you have compiled it.

like 
```

$sudo app.gambas
password:*******

```

or you could make an entry on the menu pointing to gksudo and the that to execute your app. in that way is wide usable and distributable.

---

### Post by !nkubus on 2006-12-04
try 

PRINT Call("gksu gedit /boot/grub/menu.lst")

---

