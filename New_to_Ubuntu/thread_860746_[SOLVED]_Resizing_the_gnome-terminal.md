---
title: "[SOLVED] Resizing the gnome-terminal"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by Kolmogorov on 2008-07-15
Hi, 

I want to know how to resize the window from the gnome-terminal application to a user-given default size...

Is this possible ?

Thanks in advance !

---

### Post by drs305 on 2008-07-15
> **Kolmogorov said:**
> Hi, 

I want to know how to resize the window from the gnome-terminal application to a user-given default size...

Is this possible ?

Thanks in advance !

You can open a terminal window of a specific size with the following command. Just change the values to those you wish.
```
gnome-terminal --geometry 146x5+30+42

```

Width, Line Height, Offset from Left, Offset from Top

You can make a launcher with the above command, with the Custom Application Launcher and "Run in terminal"

---

### Post by webofunni on 2008-07-15
Hello drs305,

  Thanks for that ;-)

---

