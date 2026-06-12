---
title: "Ubuntu 20.04: IceWM full dark theme ?"
date: 2022-03-25
forum: New to Ubuntu
---

### Post by maketopsite on 2022-03-25
Is it please possible to have full dark theme in IceWM ? Some parts of applications are  white / grey: PCManFM background, application menu bar background, terminal & web browser tabs background.

---

### Post by DuckHook on 2022-03-29
I've only dabbled with IceWM in the most cursory fashion so have only explored the shallowest config changes. I did not go as far as dark vs light theme, but I did use the following resources to find my way around:

[https://ice-wm.org/manual/](https://ice-wm.org/manual/)
[https://ice-wm.org/themes/](https://ice-wm.org/themes/)
[https://www.box-look.org/browse?cat=142&ord=latest](https://www.box-look.org/browse?cat=142&ord=latest)
[https://github.com/bbidulock/icewm-extra-themes/](https://github.com/bbidulock/icewm-extra-themes/)

It may well be that IceWM themes will not extend as far as PCManFM or other apps/utilities. If you install a Qt or GTK app, I can well imagine them taking their marching orders from Qt or GTK and ignoring the WM settings.

Here is a link from a long, long time ago in a galaxy far, far away, but you might be able to glean some useful settings out of it:

[https://www.psychocats.net/ubuntu/icewm](https://www.psychocats.net/ubuntu/icewm)

Sorry, can't be of further help. My explorations of it were very limited.

---

### Post by mastablasta on 2022-03-30
yes, it is posisble: [https://www.box-look.org/browse?cat=142&ord=latest](https://www.box-look.org/browse?cat=142&ord=latest)

++ maybe Arc-dark

---

### Post by maketopsite on 2022-04-04
> **DuckHook said:**
> I've only dabbled with IceWM in the most cursory fashion so have only explored the shallowest config changes. I did not go as far as dark vs light theme, but I did use the following resources to find my way around:

[https://ice-wm.org/manual/](https://ice-wm.org/manual/)
[https://ice-wm.org/themes/](https://ice-wm.org/themes/)
[https://www.box-look.org/browse?cat=142&ord=latest](https://www.box-look.org/browse?cat=142&ord=latest)
[https://github.com/bbidulock/icewm-extra-themes/](https://github.com/bbidulock/icewm-extra-themes/)

It may well be that IceWM themes will not extend as far as PCManFM or other apps/utilities. If you install a Qt or GTK app, I can well imagine them taking their marching orders from Qt or GTK and ignoring the WM settings.

Here is a link from a long, long time ago in a galaxy far, far away, but you might be able to glean some useful settings out of it:

[https://www.psychocats.net/ubuntu/icewm](https://www.psychocats.net/ubuntu/icewm)

Sorry, can't be of further help. My explorations of it were very limited.

Thank you I will read it little by little.

Themes are full dark in older Ubuntu version and in other distros so  maybe there is some change in functionality in Ubuntu 20.04. Maybe  switch from LXDE to LXQT ?

---

### Post by maketopsite on 2022-04-04
> **mastablasta said:**
> yes, it is posisble: [https://www.box-look.org/browse?cat=142&ord=latest](https://www.box-look.org/browse?cat=142&ord=latest)

++ maybe Arc-dark

I've tried Arc-dark but places I mentioned are still white.

---

### Post by TenPlus1 on 2022-04-04
IceWM themes at [https://www.box-look.org/browse?cat=142&ord=latest](https://www.box-look.org/browse?cat=142&ord=latest)

---

### Post by maketopsite on 2022-04-04
> **TenPlus1 said:**
> IceWM themes at [https://www.box-look.org/browse?cat=142&ord=latest](https://www.box-look.org/browse?cat=142&ord=latest)

I've tried IceMatcha-Dark-Pueril from this website but it is not full dark.

---

### Post by mastablasta on 2022-04-07
well for example web browser is not connected to OS and has it's own dark theme. you can have bright firefox and dark OS. same in widnows.

window manager defines windows and possibly some apps. the rest is up to desktops. for example KDE has nice dark theme where file manager and all system apps are dark. but rin nvidia settigns and they are white (aside form the border)

---

### Post by maketopsite on 2022-04-11
solved after selecting dark theme in [FONT=courier new]lxappearance[/FONT]. 

I hope [FONT=courier new]lxappearance[/FONT] will be supported for a long time.

---

