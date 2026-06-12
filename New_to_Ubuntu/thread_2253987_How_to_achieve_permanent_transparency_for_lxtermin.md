---
title: "How to achieve permanent transparency for lxterminal?"
date: 2014-11-24
forum: New to Ubuntu
---

### Post by iums1 on 2014-11-24
Hi,

I set my lxterminal to transparent via right click > preferences > background  > set opacity value to zero but after i restart lxterminal the changes made are gone. I looked into the /home/username/.config/lxterminal/lxterminal.conf file but I can't find an entry for transparancy. How do I achieve permanent transparency?

---

### Post by vasa1 on 2014-11-24
I think lxterminal can't handle an opacity setting of 0. So set it at 2. That's virtually the same as 0 but that setting is remembered whereas 0 messes things up.

(*bgalpha* is the setting for transparency.)

Edit: also note that the transparency is "fake". By that I mean you'll see your background (wallpaper) and not the window below the terminal. To get true transparency, you'll need to run a compositing manager such as Compton.

---

### Post by iums1 on 2014-11-24
> **vasa1 said:**
> I think lxterminal can't handle an opacity setting of 0. So set it at 2. That's virtually the same as 0 but that setting is remembered whereas 0 messes things up.

(*bgalpha* is the setting for transparency.)

Edit: also note that the transparency is "fake". By that I mean you'll see your background (wallpaper) and not the window below the terminal. To get true transparency, you'll need to run a compositing manager such as Compton.

Thank you. Problem solved. I'm ok with fake transparency because I like efficiency. Real transparency takes more resources.

---

### Post by vasa1 on 2014-11-24
> **iums1 said:**
> Thank you. Problem solved. I'm ok with fake transparency because I like efficiency. Real transparency takes more resources.
I think like you :)

But how much resources are used by your compositing manager depends on how you set it up. I use it but very minimally: no shadows or blur effects, just transparency. If you feel like it, give Compton a try. My ~/.config/compton.conf is this:```
focus-exclude = ["n:a:Conky"]; # https://bbs.archlinux.org/viewtopic.php?pid=1293686#p1293686
inactive-opacity = 1.0;
inactive-dim = 0.2;
mark-ovredir-focused = true;
opacity-rule = [ 
				"60:name *= 'Mahjongg'",
				"70:name *= '- Google Chrome'"
				];
shadow = false;
no-dnd-shadow = true;
no-dock-shadow = true;
blur-background = false;
```
You probably won't need the opacity-rule bit!

I have this in my autostart:```
compton --config /home/vasa1/.config/compton.conf -b
```

And I'm using the Compton available from the software center, not from any ppa.

---

