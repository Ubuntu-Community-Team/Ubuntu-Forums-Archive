---
title: "Disable touchpad while typing not working on ubuntu 18.04"
date: 2018-04-29
forum: New to Ubuntu
---

### Post by arcety on 2018-04-29
[COLOR=#111111][FONT=Ubuntu]I really love ubuntu 18.04 but something is driving me nuts. Everytime I'm typing and i accidentally touch the touchpad mycursor jups. On [another post]("https://askubuntu.com/questions/85065/how-to-lock-touchpad-while-typing") I found that this behavoir can be solved in two ways:[/FONT][/COLOR]

[LIST]
[*]By using syndaemon
[*]By using the touchbar-indicator plugin
[/LIST]
[COLOR=#111111][FONT=Ubuntu]But on my system both methods seem to fail. For the touchbar-indicator I just enabled the auto disable touchpad option but that doesn't do anything. Then I configured syndaemon as a startup application like this:[/FONT][/COLOR]
```
/bin/bash -c "sleep 15 && syndaemon -i .8 -K -t -R -d"
```[COLOR=#111111][FONT=Ubuntu]
If anyone knows what I can do about this behvaoir please tell me since I'm going mad. :p[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Thanks a lot in advance, Greetings, Rick[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]**System info:** - Intel® Core&#8482; i7-6700HQ CPU @ 2.60GHz × 8 - HP Zbook G3 Studion[/FONT][/COLOR]

---

### Post by mc4man on 2018-04-29
In a default 18.04 install disable-while-typing is enabled, the timeout seems to be 2 sec (barely in gedit, almost immediate in firefox, i.e cursor comes back right away
The setting is in dconf-editor > /org/gnome/desktop/peripherals/touchpad
If one wanted to raise the timeout in may need to be done in libinput somehow.

---

### Post by arcety on 2018-04-30
Thanks for your reply it helped me narrow down the problem. I solved my problem as follows:

1. By using this [forum post]("https://ubuntuforums.org/showthread.php?t=1150319") I fully reinstalled my xserver drivers.
2. I then reinstalled the drivers following this [forum post]("https://askubuntu.com/questions/908918/updated-from-16-04-to-16-10-the-keyboard-and-mouse-no-longer-works-after-gettin").
3. I then added the following command to my startup applications:
```
syndaemon -i .5 -K -t -R -d
```

---

