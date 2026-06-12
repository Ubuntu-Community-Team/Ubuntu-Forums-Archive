---
title: "Can't use startx on another tty"
date: 2016-07-28
forum: New to Ubuntu
---

### Post by mohammadbagheri2010 on 2016-07-28
Hi.
I want to have another screen same as the default one that appears on boot after login.
All I did was this :
```
Ctrl + Alt + F1
Logining in 
# Here I expect  "startx" not to run and saying that it's already running but it does not.anyway I used this instead -> 
startx -- :1 

```
now i can only see my background and nothing on it and a cross instead of my mouse pointer.
how i can have another normal screen like default one?

---

### Post by Bashing-om on 2016-07-28
mohammadbagheri2010; Hello;

The command to start the GUI depends on the Desktop Environment .
Is your system the default ubuntu that uses unity as the DE ?
I Have not done this, but I can accept that we will have to also declare a dbus instance for the added GUI to run in.

[INDENT][INDENT]that process of learning
[/INDENT][/INDENT]

---

### Post by mohammadbagheri2010 on 2016-07-28
> **Bashing-om said:**
> mohammadbagheri2010; Hello;

The command to start the GUI depends on the Desktop Environment .
Is your system the default ubuntu that uses unity as the DE ?
I Have not done this, but I can accept that we will have to also declare a dbus instance for the added GUI to run in.
[INDENT][INDENT]that process of learning
[/INDENT]
[/INDENT]

I use lighdm(?!).
Actually how to know which Desktop Environment am i using?

---

### Post by deadflowr on 2016-07-28
> **mohammadbagheri2010 said:**
> I use lighdm(?!).
Actually how to know which Desktop Environment am i using?

```
printenv | grep XDG_CURRENT_DESKTOP
```
should show you which DE is in use.

If using Ubuntu's default desktop, unity, then startx does not work with it, properly; as far as I remember, because unity requires to start with the display manager, lightdm.
(though I have had it start with gdm, once upon a time; unless that was an illusion)

---

### Post by Bashing-om on 2016-07-28
mohammadbagheri2010; Hey ..

Be aware, we may be in for a long hard tough fight now-a-days to make this happen.
See: [https://ubuntuforums.org/showthread.php?t=2330506](https://ubuntuforums.org/showthread.php?t=2330506)

Which indicates that in 16.04 (systemd) will be a real challenge.
Which raises the question of which release we are working with ,, will make a big big difference.
To know what you have for the DE and the Display manager:
```

echo $DESKTOP_SESSION " " $XDG_CURRENT_DESKTOP
cat  /etc/X11/default-display-manager

```

I can do this on my system .. BUT .. I run release 14.04 and my GUI is " xfce4-session 4.10.1 (Xfce 4.10) " .
I do this on a rare occasions .. If in 16.04 (systemd) this can no longer be done, I will miss this "feature"  .

[INDENT][INDENT]Nothing like trying
[INDENT][INDENT][INDENT]see what works[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

