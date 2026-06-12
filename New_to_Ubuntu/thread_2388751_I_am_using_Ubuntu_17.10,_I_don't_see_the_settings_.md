---
title: "I am using Ubuntu 17.10, I don't see the settings icon(cog)  in the log in screen..."
date: 2018-04-06
forum: New to Ubuntu
---

### Post by automate-stuff on 2018-04-06
[COLOR=#000000][COLOR=#000000]
[/COLOR][/COLOR][h=2]17.10, Suspending, restarting, powering off or accessing settings results in a hang.[/h][COLOR=#000000][COLOR=#000000]

echo $DESKTOP_SESSION[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]ubuntu[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]echo $XDG_SESSION_TYPE[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]x11





I am using the xorg graphics driver.

some say it has to do with login manager using wayland.

I tried disabling wayland in [/COLOR][/COLOR][COLOR=#111111][FONT=Consolas]/etc/gdm3/custom.conf

[/FONT][/COLOR][COLOR=#000000][COLOR=#000000]then There would be no log in screen, It would auto log-in, computer suspends but hangs when I try to get back in....[/COLOR][/COLOR]




I just want to switch to xorg and I am told i should choose the "Ubuntu on Xorg" at log in screen...The problem is I dont have any settings icon on my login screen..How do i get this back ?

---

### Post by Frogs Hair on 2018-04-06
Select the area next to the user image with the computer name and you'll find the cog with listed sessions on the bottom right.17.10 uses GDM rather than Light DM.

---

### Post by automate-stuff on 2018-04-06
amir@Gauss:~$ echo $DESKTOP_SESSION
ubuntu
amir@Gauss:~$ echo $XDG_SESSION_TYPE
x11



Here is the problem , Desktop session is Wayland but XDG session is xorg ... how do i change desktop session to xorg ?

---

### Post by automate-stuff on 2018-04-06
> **Frogs Hair said:**
> Select the area next to the user image with the computer name and you'll find the cog with listed sessions on the bottom right.17.10 uses GDM rather than Light DM.


This doesn't work at all...My original problem is that I cannot suspend,restart or shut down after I log in...Computer hangs...It also hangs when I am trying to access settings...By What i have read , I should change the desktop session to xorg...but there is no cog in the login screen...and what you said didnt work...

---

### Post by Frogs Hair on 2018-04-06
If you don't see the options in the screen shot below I'm not sure what's wrong. Are you using auto login ?

---

### Post by automate-stuff on 2018-04-06
no

---

### Post by Frogs Hair on 2018-04-06
Did you reboot or are you just logging out  and back in ?

---

### Post by QIII on 2018-04-06
And it might be helpful if you could post an image of what you DO see.  Take a snapshot with your phone if need be.

---

### Post by automate-stuff on 2018-04-06
I reboot everytime...here is the picture :

[https://ibb.co/eQT0XH](https://ibb.co/eQT0XH)

---

### Post by Frogs Hair on 2018-04-06
try the following. ```
sudo dpkg-reconfigure gdm3
``` ```
sudo reboot
```

---

### Post by automate-stuff on 2018-04-06
> **Frogs Hair said:**
> try the following. ```
sudo dpkg-reconfigure gdm3
``` ```
sudo reboot
```

Doesn't work...


Tried upgrading to kernel v4.16, still cant suspend, restart or power off...

---

### Post by automate-stuff on 2018-04-06
[COLOR=#000000][INDENT]I also tried switching to lightdm ... there I can change between wayland and xorg ... there is a button that allows me to do it....but it hangs when I try to log in(hit the login button).[/INDENT]


[/COLOR]
[COLOR=#000000][B][RIGHT][/RIGHT]
[/B][/COLOR]

---

