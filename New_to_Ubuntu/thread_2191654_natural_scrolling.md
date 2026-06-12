---
title: "natural scrolling"
date: 2013-12-03
forum: New to Ubuntu
---

### Post by deaton25 on 2013-12-03
hi
i installed natural scrolling today on my ubuntu 12.04. i even have a little icon on top! and the app is posted on the application part of  ubuntu

but it doesn't work: the page still goes up when i scroll down! i don't use a mouse. just my two fingers on the keyboard
what am i doing wrong?

thanks for your time.

---

### Post by deaton25 on 2013-12-03
[COLOR=#000000]hi[/COLOR]
[COLOR=#000000]i installed natural scrolling today on my ubuntu 12.04. i even have a little icon on top! and the app is posted on the application part of ubuntu[/COLOR]

[COLOR=#000000]but it doesn't work: the page still goes up when i scroll down! i don't use a mouse. just my two fingers on the keyboard[/COLOR]
[COLOR=#000000]what am i doing wrong?[/COLOR]

[COLOR=#000000]thanks for your time.[/COLOR]

---

### Post by mörgæs on 2013-12-03
Please stop double-posting.
Merged.

---

### Post by monkeybrain20122 on 2013-12-03
I never experienced this issue in Unity. However, in gnome shell it did happen. I am not sure if this is appropriate in your case but you can try.
Install the dconf-editor via synaptic or sudo apt-get

Open it and go to org > gnome > settings-daemon >peripherals > touchpad and check  what is displayed in 'scroll method". In my case (Fedora) it was set to "natural scrolling" and when I scrolled down the screen went up. Changed that to edge scrolling and it behaved normally.

---

