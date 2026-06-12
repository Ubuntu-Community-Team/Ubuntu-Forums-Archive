---
title: "Screen resolution"
date: 2012-03-14
forum: New to Ubuntu
---

### Post by bouldie on 2012-03-14
I have somehow managed to delete the icon in the system preferences menu that allowed me to change the screen resolution (monitors?). Can someone tell me how to restore it please.

---

### Post by MG&amp;TL on 2012-03-14
I'm sure there is a user-friendly way to do this, but this should cover all ubuntu releases and desktops:

1. Open a terminal (Press Ctrl-Alt-T, or find it in your menus/dash.

2. Type the following command:
```
sudo apt-get install --reinstall gnome-control-center
```

3. Type your password (you can't see it).

4. Wait for the terminal to return to normal. It should now have a monitor entry. Post back if it doesn't.

---

