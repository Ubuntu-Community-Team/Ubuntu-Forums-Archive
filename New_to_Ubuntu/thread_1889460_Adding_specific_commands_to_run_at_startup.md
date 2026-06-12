---
title: "Adding specific commands to run at startup"
date: 2011-12-01
forum: New to Ubuntu
---

### Post by new123 on 2011-12-01
I made many apps to run at startup, just copied some of them from /usr/share/applications to /home/myusername/.config/autostart, but I wonder how to make specific commands to run at startup, I tried making a script like this:
```
#!/bin/bash
lxterminal
```Saved as .sh and moved it to /home/myusername/.config/autostart but LXTerminal won't start at startup..

---

### Post by Lars Noodén on 2011-12-01
If you mean when you have logged in, then you can put your script in [font=Courier New].xsessionrc[/font]

If you mean system startup, then you can put your script in [font=Courier New]/etc/rc.local[/font]

---

### Post by new123 on 2011-12-01
> **Lars Noodén said:**
> If you mean when you have logged in, then you can put your script in [FONT=Courier New].xsessionrc[/FONT]

If you mean system startup, then you can put your script in [FONT=Courier New]/etc/rc.local[/FONT]
I meant when I logged in, but I can't find .xsessionrc.. where is it?

---

### Post by Lars Noodén on 2011-12-01
> **new123 said:**
> I meant when I logged in, but I can't find .xsessionrc.. where is it?

You have to make one.  It goes in your home directory:

```

gedit ~/.xessionrc

```

---

### Post by new123 on 2011-12-01
> **Lars Noodén said:**
> You have to make one.  It goes in your home directory:

```

gedit ~/.xessionrc

```
I did it, now the only thing that loads at startup when I login is lxterminal (in which I cant type), no panel, no icons, nothing else..
Luckly, I have my WinXP so I can inform you about that..

Edit: I deleted (in tty) previusly made .xsessionrc, now I can login again

---

### Post by Jacobonbuntu on 2011-12-01
...why not do it the easy way:

Dash > startup items > add > new > make your command ?

---

### Post by new123 on 2011-12-01
> **Jacobonbuntu said:**
> ...why not do it the easy way:

Dash > startup items > add > new > make your command ?
Because I use _L_ubuntu.. There is no GUI to add command that will be run at startup..

---

### Post by Lars Noodén on 2011-12-01
> **Jacobonbuntu said:**
> ...why not do it the easy way:

Dash > startup items > add > new > make your command ?

How did you know to do that?  There seems to be no way to figure that out by chance.

---

### Post by Jacobonbuntu on 2011-12-01
> **new123 said:**
> Because I use _L_ubuntu.. There is no GUI to add command that will be run at startup..


oops, excuse me :oops:

---

### Post by new123 on 2011-12-06
I fixed this by doing next:
(For LXTerminal)
1. make lxterminal.desktop in ~/.config/autostart/
2. write next in that file:
```
[Desktop Entry]
Encoding=UTF-8
Type=Application
Name=LXTerminal
Exec=lxterminal
StartupNotify=true
```
:)

---

