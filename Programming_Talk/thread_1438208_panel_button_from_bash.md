---
title: "panel button from bash?"
date: 2010-03-24
forum: Programming Talk
---

### Post by matchett808 on 2010-03-24
Is there a way to add a panel button from bash?

This is a bit of a two parter but also...If I have made a proggy and want to share, then how do I?

---

### Post by matchett808 on 2010-03-24
ok, so quick update, I have worked out that to add the button I need to created a file in the ~/.gnome2/panel2.d/default/launchers/ directory, but nothing happens? would it be more likely to work if I restarted? I really dont want it to need a restart its such a minor programme! lol

---

### Post by matchett808 on 2010-03-25
bump

---

### Post by louis--taylor on 2010-03-25
> ...I have made a proggy...By this I am assuming you mean a program, or shell script :)

If you think the program could be useful for anyone else, put it on launchpad [https://launchpad.net/](https://launchpad.net/)
If you just need to share between a couple of people, try dropbox ([https://www.dropbox.com](https://www.dropbox.com))

Note: It is not polite to blatantly bump threads :(

---

### Post by lavinog on 2010-03-26
You shouldn't automatically install launchers onto panels.
You can't always assume that the user is using a panel.
You should add a menu item...let the user add it to the panel if they want.

It looks like you can add files to ~/.gnome2/panel2.d/default/launchers

---

