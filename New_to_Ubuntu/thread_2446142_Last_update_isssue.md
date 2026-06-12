---
title: "Last update isssue"
date: 2020-06-25
forum: New to Ubuntu
---

### Post by nikolajov on 2020-06-25
Hi i just updated my xubuntu os and after reseting on my dell lantitude d630 i can`t log in it just sends me back to the login screen. and when i try to log in for short time flashes the screen and gives a writing of [COLOR=#000000][FONT=&quot]leds dell::kbd_backlight: Setting an LED's brightness failed.
[/FONT][/COLOR][FONT=&quot]Could you help me please and thank you[/FONT][COLOR=#000000][FONT=&quot][/FONT][/COLOR]

---

### Post by ActionParsnip on 2020-06-25
If you press CTRL + ALT + F1 and log in there and run:
```

df -h

```

Do you have free space in your partitions? If not then you can clean some out with:
```

sudo apt clean

```

You can also make sure your user own's it's own home folder with:
```

sudo chown -R $USER $HOME

```
(You don't need to change the command, it uses BASH variables).

Once that has ran, run:
```

sudo reboot

```

Then log in as normal once the system is back up

HTH

---

