---
title: "Keyboard layout not saved, changes after reboot"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by pelgrim on 2008-10-18
Whenever I boot ubuntu, my keyboard layout is set on qwerty.

I can change it in keyboard preferences to Belgian (Azerty),
but that will only stay until I reboot.
When I'm too fast to do this, it also changes back to qwerty.

This last events indicates some script file is running at startup
and changes my keyboard layout ?

How to solve this problem ?

---

### Post by Elfy on 2008-10-18
I don't know why this is happening, but it affected me as well.

I added the necessary to my xorg.conf and it has been fine since.

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.1810
gksudo gedit /etc/X11/xorg.conf
```

Change the input device of your xorg
> Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "be"

Mostly positive that be is correct code for Belgian azerty

---

### Post by tom4everitt on 2010-04-11
Hmm, having the same problem. 

It won't remember me deleting the USA keyboad layout, and although it does remember that I moved swedish to top, it still choses US on login. 

The xorg.conf didn't seem to solve it.

---

### Post by andreibranescu on 2010-05-05
> **tom4everitt said:**
> Hmm, having the same problem. 

It won't remember me deleting the USA keyboad layout, and although it does remember that I moved swedish to top, it still choses US on login. 

The xorg.conf didn't seem to solve it.

Same problem here, in Lucid Lynx.

---

### Post by desgua on 2010-07-04
Same problem, did someone find a solution?

---

### Post by warfacegod on 2010-07-04
Have you guys tried changing the Keyboard layout in the Log in Screen?

---

### Post by warfacegod on 2010-07-04
Another thought. Right click the Apps./Places/System menu> select Edit Menus> highlight Preferences in the left pane> right click Keyboard in the right pane> select Properties> add "gksudo" to the beginning of the Command:

Should read like this: gksudo gnome-keyboard-properties

---

### Post by desgua on 2010-07-04
Unfortunately neither of these ideas worked... Nevertheless Thank you very much. ;)

---

### Post by warfacegod on 2010-07-04
> **desgua said:**
> Unfortunately neither of these ideas worked... Nevertheless Thank you very much. ;)

Certainly! I'll post back if I think of or run into something else.

---

### Post by desgua on 2010-07-04
I think I got it. Thank's to warfacegod idea. 
First I let Ubuntu start and auto-login, then I *let the keyboard layout unchanged* and logout and then login again changing my layout at login screen. Now every time I auto-login the layout stay like what I wanted.

---

### Post by simosx on 2010-07-05
> **desgua said:**
> I think I got it. Thank's to warfacegod idea. 
First I let Ubuntu start and auto-login, then I *let the keyboard layout unchanged* and logout and then login again changing my layout at login screen. Now every time I auto-login the layout stay like what I wanted.

The OP has been running 8.10 which had a bug; if you autologin, your layout settings are not enabled at all. The workaround for that one was to edit xorg.conf.

In 9.04 and newer, this issue was fixed.

In your case you describe something interesting. Keyboard layouts work nowdays fine but you get the occasional user describing what you got. This has not been nailed down, so if we can have another user able to replicate what you describe above, this should help in fixing once and for all.

---

### Post by desgua on 2010-07-05
I will try to make this issue clear to understand and maybe to fix. 
I fresh instal Ubuntu 10.04 after have start from a previous burned cd. I had chose us international keyboard. Days after that I decided to change my layout to br even though it isn't my actual layout but I'm more used to it.
If others informations are needed just ask me.
Regards.

---

### Post by simosx on 2010-07-05
> **desgua said:**
> I will try to make this issue clear to understand and maybe to fix. 
I fresh instal Ubuntu 10.04 after have start from a previous burned cd. I had chose us international keyboard. Days after that I decided to change my layout to br even though it isn't my actual layout but I'm more used to it.
If others informations are needed just ask me.
Regards.

You are saying that you did an installation where you chose the US International layout. You can verify this in /etc/default/console-setup which saves the initial settings during installation. These are used when you create a new user account on your system.

Then, you replaced the US International layout with the Brazilian layout. So, you have a single layout now, which is different from the installation layout.

So, the problem is that when you restart the computer now, the system somehow remembers and replaced back to the initial US International keyboard layout. No matter how many times you change the keyboard layout, when you reboot you automagically get that initial installation keyboard layout. Is that a good description of the problem?

---

### Post by warfacegod on 2010-07-05
I thought desgua's was fixed. :confused:

---

### Post by gert cuykens on 2010-12-27
I did upgrade from 8.04 to 10.04 and have the same issue.

---

### Post by desgua on 2010-12-28
Simosx, 
Sorry I'm late. 
Yes this is exactly my problem.
It is fixed now. Look at post #10.
Thank you very much.
Best regards.

---

### Post by desgua on 2010-12-28
At post #10 I explaned what I did to fix it.

---

### Post by Wim Feijen on 2011-05-13
Thanks Warfacegod! 

It works for me, setting keyboard preferences while not logged in. :)

Wim

---

