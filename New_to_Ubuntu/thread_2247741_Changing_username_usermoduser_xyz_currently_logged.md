---
title: "Changing username usermod:user xyz currently logged in"
date: 2014-10-10
forum: New to Ubuntu
---

### Post by govinda3 on 2014-10-10
[COLOR=#333333][FONT=UbuntuRegular]I am trying to change username of my Ubuntu account by using this command[/FONT][/COLOR]
xyz@piechucker:~/abc/in$ usermod -l myname xyz
[COLOR=#333333][FONT=UbuntuRegular]and it is saying[/FONT][/COLOR]
usermod: user xyz is currently logged in
[COLOR=#333333][FONT=UbuntuRegular]I know I have to rename it using recovery mode ,I am new to Ubuntu ,please help me .[/FONT][/COLOR]

---

### Post by ajgreeny on 2014-10-10
> **govinda3 said:**
> [COLOR=#333333][FONT=UbuntuRegular]I am trying to change username of my Ubuntu account by using this command[/FONT][/COLOR]
[COLOR=#ff0000]xyz@piechucker:~/abc/in$ usermod -l myname xyz[/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]and it is saying[/FONT][/COLOR]
usermod: user xyz is currently logged in
[COLOR=#333333][FONT=UbuntuRegular]I know I have to rename it using recovery mode ,I am new to Ubuntu ,please help me .[/FONT][/COLOR]
If the line in red is exactly what you saw then you are still logged in as xyz, so you can not be in recovery mode.

What exactly did you do to get to recovery mode; did you use the grub menu?  I am baffled, or confused, or both.

---

### Post by oldos2er on 2014-10-10
Moved to New to Ubuntu.

---

