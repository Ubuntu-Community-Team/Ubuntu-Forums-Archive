---
title: "Login Screen Issue"
date: 2012-01-31
forum: New to Ubuntu
---

### Post by rondre on 2012-01-31
I'm new to Ubuntu and was messing around with trying to get Plasma widgets on my gnome desktop.  Somehow installing the plasma gtk (terminology?) changed my login screen to a KDE looking one and I can't figure out how to change it back.  I really like the default look with the login information on the left side, now it's kind of a cheesy window in the middle of the screen with the default kde background.

I'm thinking of uninstalling the kde stuff to see if that will fix it but not sure if that will work.  I've tried using the Ubuntu Tweak program as well and that doesn't seem to make any difference.  

Any help is appreciated!

---

### Post by JRV on 2012-01-31
You need to change the display manager.
The display manager you want is lightdm.
When I need to change the display manager I have found that the easiest way is to add another one. 
Then a text based menu will come up asking you which of the installed display managers you want to use.

Press <CTRL><ALT>T to open a terminal and enter the command:
```

sudo apt-get install xdm

```

The menu to select a display manager will appear, select lightdm.

Now remove xdm with the command:
```

sudo apt-get remove xdm

```

---

### Post by rgreener25 on 2012-01-31
This would be quicker and easier ```
sudo dpkg-reconfigure kdm
```

---

### Post by rondre on 2012-02-01
Thanks - had a friend visit from out of town last night so didn't get on the machine but will definitely try this tonight and will post what fixed it.

---

