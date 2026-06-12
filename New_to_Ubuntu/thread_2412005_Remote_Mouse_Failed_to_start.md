---
title: "Remote Mouse Failed to start"
date: 2019-02-07
forum: New to Ubuntu
---

### Post by jamesjiby on 2019-02-07
After successful installation, when try to run 

sudo mono ./RemoteMouse/RemoteMouse.exe

it returns the error as:

Unhandled Exception:
System.IO.FileNotFoundException: Could not load file or assembly or one of its dependencies.
File name: 'gtk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f'

My OS: Ubuntu 18.04 LTS

---

### Post by 0N3 on 2019-02-10
```
sudo apt install libappindicator0.1-cil libappindicator3-0.1-cil-dev
```

Should solve your problem.

---

### Post by 0N3 on 2019-02-10
Shouldn't need sudo to run it. I've downloaded the program and moved it ti /opt/ and start the application on login to my desktop. Edit startup applications and in command I use:

```
/opt/RemoteMouse/RemoteMouse.exe
```

---

