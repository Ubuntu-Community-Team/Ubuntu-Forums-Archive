---
title: "Kill the beep."
date: 2008-07-26
forum: New to Ubuntu
---

### Post by RobbyemCee on 2008-07-26
When I boot up my machine gives a system beep right when gdm comes up asking me for my username and pass.

Does anyone know how to disable this?

-RobbyemCee

---

### Post by SuperSonic4 on 2008-07-26
It could be in system -> Preferences -> sounds

but failing that you could always physically remove the speaker

---

### Post by AndyCooll on 2008-07-26
If you go to System > Preferences > Sound and choose the "System Beep" tab you can disable it there.

:cool:

---

### Post by RuleMaker on 2008-07-26
System->Preferences->Sound->System Beep and disable the system beep.

---

### Post by OutOfReach on 2008-07-26
And if the system still beeps even after you disabled it,
type this into the terminal:
```
sudo gedit /etc/modprobe.d/blacklist
```

It'll bring up the text editor, now at the bottom of the list add the following:

```
blacklist pcspkr
```

That will blacklist the system beep, but you need to restart (or log out, im not sure) for it to take effect.

---

