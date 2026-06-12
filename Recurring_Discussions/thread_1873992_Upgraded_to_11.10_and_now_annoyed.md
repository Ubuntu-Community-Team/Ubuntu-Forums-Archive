---
title: "Upgraded to 11.10 and now annoyed"
date: 2011-11-02
forum: Recurring Discussions
---

### Post by Meadow of Flowers on 2011-11-02
Some time ago I upgraded from Ubuntu 10 to 11 and absolutely hated the Unity thing so after seraching for information on this forum on how to remove it, I carefully removed it. Today I upgraded to 11.10 and behold, Unity is back! Wht's more, I now have a 'guest' account that wasn't there before and does not appear in the /etc/passwd file.

How can I remove both PERMANENTLY please?

Oh, and what happened to all the system administration tools please? If I log in with a  Gnome session, I now only have Applications and Places and the application icons on the task(quick launch)bar are gone.

---

### Post by vicshrike on 2011-11-02
What do you want instead of Unity? Gnome3? Gnome2?

---

### Post by Meadow of Flowers on 2011-11-02
Yes the current version of Gnome would be fine - just the way it was in Ubuntu 10. Not sure whether it was version 2 or 3, either will do but the latest is probably preferable. Since I'm not using a touch display, Unity does not make sense.

I'm also concerned that the guest account could be used to attack the system. I don't need it so I would like to get rid of it.

---

### Post by raja.genupula on 2011-11-02
open your terminal and type ```
ccsm
``` in the opened window uncheck the unity checkbox , this will switch off the unity.

to delete the unwanted user acounts type

```
sudo deluser
```

All the best.

But Gnome-shell is also cool.If you wanna try it you can get from 

```
sudo apt-get install gnome-shell
```

All the best.

---

### Post by Rubi1200 on 2011-11-02
Thread moved.

---

### Post by Gremlinzzz on 2011-11-02
install Ubuntu 10.04 :popcorn:
Canonical intends to provide support for Ubuntu 10.04 until April 2013 for the desktop version, and until April 2015 for the server version.

---

### Post by Meadow of Flowers on 2011-11-02
raja, thanks. Unfortunately the command ccsm does not exist on my system. Aptitude is also broken so I can't don an apt search either. The nearest thing I could come up with is the ConQUAT library of utility functions. Is this the correct thing to install to get the ccsm command?

---

### Post by raja.genupula on 2011-11-02
to get that 

```
sudo apt-get install ccsm
```

---

### Post by Elfy on 2011-11-02
The package is compizconfig-settings-manager not ccsm - the command to run it from a terminal is ccsm

---

### Post by Ric_NYC on 2011-11-02
> **Gremlinzzz said:**
> install Ubuntu 10.04 :popcorn:
Canonical intends to provide support for Ubuntu 10.04 until April 2013 for the desktop version, and until April 2015 for the server version.

:popcorn::popcorn::popcorn:


YEAAAAHHH!!!!

---

### Post by cariboo on 2011-11-02
> **ihateunity said:**
> Some time ago I upgraded from Ubuntu 10 to 11 and absolutely hated the Unity thing so after seraching for information on this forum on how to remove it, I carefully removed it. Today I upgraded to 11.10 and behold, Unity is back! Wht's more, I now have a 'guest' account that wasn't there before and does not appear in the /etc/passwd file.

How can I remove both PERMANENTLY please?

Oh, and what happened to all the system administration tools please? If I log in with a  Gnome session, I now only have Applications and Places and the application icons on the task(quick launch)bar are gone.

It's pretty easy to set what the default DE is, and to remove the guest account. to set the desktop environment edit /etc/lightdm/lightdm.conf and change the following line in [SeatDefaults]:

```
user-session=ubuntu
```

change ubuntu to whatever session you want to be the default, for instance you can change it to **gnome classic** to get the two panel interface.

To remove the guest account from lightdm add the following line in /etc/lightdm/lightdm.conf [SeatDefaults]:

```
allow-guest=false
```

For customizing your Oneiric install have a look at:

[omgubuntu]("http://www.omgubuntu.co.uk/")

and

[webupd8]("http://www.webupd8.org/")

This is more of a support thread, than a recurring discussion.

---

### Post by BrokenKingpin on 2011-11-08
What not install one of the Ubuntu derivatives, such as Xubuntu?

---

