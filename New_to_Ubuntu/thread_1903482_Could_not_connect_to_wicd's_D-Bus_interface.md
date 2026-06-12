---
title: "Could not connect to wicd's D-Bus interface"
date: 2012-01-02
forum: New to Ubuntu
---

### Post by TyeS on 2012-01-02
I am very new to Ubuntu and I haven't had problems with my internet connection via wireless until I plugged my friend's wired internet into the computer. I was connected for a while and then when I rebooted the computer I was asked to type in a password which has never been needed to start the computer. When I went to open the wicd network it asked for a password also/ sometimes now it will just show the icon in the dock as if it's opening then disappear.


the message I get is: [COLOR="Red"]Could not connect to wicd's D-Bus interface. Check the wicd log for error messages.[/COLOR]

I looked up how to check the wicd log but when I got to the [COLOR="red"]var/log/wicd[/COLOR] the folder icon had an "x" on it and the folder is empty.

I also read a forum where they said to check the [COLOR="red"]etc/init.d/wicd[/COLOR]

and the forum had the proper scripts to replace it with. However when I tried to put the correct scripts in I got this message:

[COLOR="red"]Could not save the file /etc/init.d/wicd. You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.[/COLOR]

I also tried going to the [COLOR="red"]"/etc/wicd/wired-settings.conf"[/COLOR] but when I do the [COLOR="red"]manager-settings.conf[/COLOR] has an "x", [COLOR="red"]wired-settings.conf [/COLOR]has an "x" and the [COLOR="red"]wireless-settings.conf[/COLOR] has an "x" on them and cannot be opened. 

Does anyone know how to fix this problem? I am extremely new to Ubuntu and very confused.

---

### Post by cortman on 2012-01-02
I think the solution should be pretty simple- you need to be root user to edit those system files. To edit etc/init.d/wicd open a terminal and type

```
gksu gedit etc/init.d/wicd
```

It'll ask you for your password.
The "gksu" or "sudo" prefix logs you in as root or administrator user. All user profiles in Ubuntu are not administrators for security.
Try editing your file now, and that might do the trick.

---

### Post by cortman on 2012-01-02
...And to browse around in the system files as root (which should enable you to open and/or edit the contents of the folders) use

```
gksu nautilus
```

Nautilus is the name of the file browser used by Ubuntu.

WARNING: Be VERY, VERY careful what you do as root! Linux systems are all open and completely editable, unlike most of Windows, so you have the power to seriously mess up or destroy your system when using root privileges. Don't do anything in root unless you are following good advice or know what you're doing.

---

### Post by chipbuster on 2012-01-02
> **TyeS said:**
> [COLOR=red]You do not have the permissions necessary to save the file.[/COLOR]

Did the command that you used have "sudo" at the beginning? If not, enter the command with "sudo" at the beginning. Not sure if that'll help your issue, but that might be what's stopping the command from going through.

EDIT: Or use gksu like everyone above me recommends. Totally forgot about that :<

---

### Post by gandaran on 2012-01-02
I have answered your post on the other thread with the fix, check post #20 
[http://ubuntuforums.org/showthread.php?t=1903410&page=2](http://ubuntuforums.org/showthread.php?t=1903410&page=2)

---

### Post by TyeS on 2012-01-02
While trying to go in as the root I came across another problem. When I go to system/ users and groups I cannot access the root at all to select it. Any suggestions on that.

---

### Post by TyeS on 2012-01-02
Should I be typing these codes in the startup root?

---

