---
title: "How Do I How Do I Stop &quot;X&quot;"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by mengd2002 on 2008-06-28
How do I go about stopping "X" completely?  And then how do I start it again?  I want to install driver for my nvidia graphics card and I have to do it from the command prompt.  Thanks.

---

### Post by hotstovejer on 2008-06-28
From a command line

```
sudo /etc/init.d/gdm stop
```

to stop it.

To start it,

```
sudo /etc/init.d/gdm start
```

This would be if you are using Gnome. If you are using KDE, please swap out gdm with kdm

Let us know if you need anything else!

Thanks!

Jeremy

---

### Post by nick_h on 2008-06-28
Go to a virtual terminal with Ctrl-Alt-F1.

Then login and stop X with:
```
sudo /etc/init.d/gdm stop
```

Next, install your video driver.

Finally, restart X with:
```
sudo /etc/init.d/gdm start
```

Edit: hotstovejer got ther first :)

---

