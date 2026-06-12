---
title: "Turn off animations in 12.04"
date: 2012-04-25
forum: New to Ubuntu
---

### Post by Stunt Double on 2012-04-25
I'm trying to turn off Window Animations in 12.04.
  When I went to MY UNITY, a warning came up that I was running in 2D mode and some features wouldn't be available. The DESKTOP tab does show that WINDOW ANIMATIONS is ON but it is grayed out so I can't switch it to OFF.
   Is there a script that I can run in the terminal to turn the animations OFF?
  Thanks

---

### Post by Curtis6767 on 2012-04-25
I don't know if this will work but it might.

Save your work.

Log out.

The 'log in' pop up will appear.

Click the Ubuntu logo.

In the drop down menu click Unity over Unity 2d.

Log in.

---

### Post by Stunt Double on 2012-04-25
It didn't work. 
It's an older computer and it automatically defaults to 2D.
But, now that I know the log-in drop-down menu is there, I can use Classic instead of Unity as needed. Maybe, there will be a fix in the future.
  Thanks

---

### Post by phendrome on 2012-04-28
We're talking about Lubuntu 12.04 correct?

You need to do the following:

[LIST=1]
[*]Open the Terminal
[*]Type **sudo leafpad ~/.config/openbox/lubuntu-rc.xml**
[*]Look for **<animateIconify>yes</animateIconify>**
[*]Change it to **<animateIconify>no</animateIconify>**
[*]Save the file and voila!
[/LIST]

---

