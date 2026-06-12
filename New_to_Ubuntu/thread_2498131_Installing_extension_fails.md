---
title: "Installing extension fails"
date: 2024-05-31
forum: New to Ubuntu
---

### Post by zoe33 on 2024-05-31
hi im new to linux, so i wanted to look more like windows11. I tried to follow the video How to make ubuntu look like windows 11 | 22.04 Gnome 43/42 [https://www.youtube.com/watch?v=x7LEHV4LRpU](https://www.youtube.com/watch?v=x7LEHV4LRpU). But at Installing required Packages it tells me: Prompt:  sudo apt install gnome-shell-extensions gnome-shell-extension-prefs gnome tweaks
Paketlisten werden gelesen… Fertig (read package list - Done)
Abhängigkeitsbaum wird aufgebaut… Fertig (Building dependentcy tree - Done)
Statusinformationen werden eingelesen… Fertig (Reading state information - Done)
E: Paket tweaks kann nicht gefunden werden. (package cannot be found)

what to do now, what can I learn from that?

---

### Post by currentshaft on 2024-05-31
Terminals (or more accutely, UNIX shells) use something called [IFS]("https://en.wikipedia.org/wiki/Internal_field_separator") to interpret commands, you can check what it's set to:

$ echo $IFS | hexdump -C
00000000  20 09 0a 00 0a                                    | ....|
00000005

Which is a space (20), a tab (09) and a newline (0a).

Anyway, as a result, you're telling apt to install two applications "gnome" and "tweaks" while it's one application: "gnome-tweaks".

Hope this helps.

---

### Post by grahammechanical on 2024-05-31
We do not know what version of Ubuntu you are using. Do you have the universe repository enabled? Open Software & Updates>Ubuntu Software and tick the box "Community maintained free and open source software (universe)" if it is not already ticked.

You can also try running that command as three commands to install each package separately.

```
sudo apt install gnome-shell-extensions
```

```
sudo apt install gnome-shell-extension-prefs
```

```
 sudo apt gnome-tweaks
```

That way you identify which one of three packages is throwing out that "package not found" message.

Regards

---

### Post by zoe33 on 2024-06-01
Hi, thank you for your fast reply. 

my current version is 24.04 LTS

Summery:
 Unfortunately I dont know how to follow currentshafts advice.
But I could achive a result from grahammechanicals 

Results:

@ currentshaft unfortunately I dont know how to use the commands so I typed them in:

julian-z-ller@Legion49:~$ IFS
IFS: Befehl nicht gefunden.
julian-z-ller@Legion49:~$ $ echo $IFS | hexdump -C
$: Befehl nicht gefunden.
julian-z-ller@Legion49:~$ 

Im pretty shure I didnt understand quite right.

anyways follwing the advise @grahammechanical I could identifie the unknown command:
"The box Community maintained free and open source software" was ticked  already so I tried the commands one by one at the given order.
sudo apt gnome-tweaks
E: Ungültige Operation gnome-tweaks (unvalid operation gnome-tweaks)

The last one is the one 

What is that telling me? How can I find a work arround If possible

kind regards

---

### Post by tea for one on 2024-06-01
sudo apt gnome-tweaks - missing command here 
```
sudo apt install gnome-tweaks
```

---

### Post by QIII on 2024-06-01
Support, not chat.

Moved to **New to Ubuntu**

---

