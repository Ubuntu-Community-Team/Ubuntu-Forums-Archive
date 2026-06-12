---
title: "Starting onboard keyboard with bash script"
date: 2019-09-25
forum: Programming Talk
---

### Post by eddienguyen on 2019-09-25
Hey there.


Idk if i'm right here but i try to write a little bash script for my mothers laptop with xubuntu. The problem she have is after every version update the keyboard isn't working anymore. To help her solve this problem by her self i wanted to write a small script.


Code:
#!/bin/bash
xfce4-terminal -e "sudo dpkg-reconfigure keyboard-configuration" &
onboard
wait
killall onboard
exit 0
This should open the keyboard reconfiguration assistant and the onboard keyboard for navigating and enter sudo password.


If i run it with bash -x i get this output:
Code:
bash -x testrun
+ onboard
+ xfce4-terminal -e 'sudo dpkg-reconfigure keyboard-configuration'
21:36:42.063 WARNING Config: mousetweaks GSettings schema not found, mousetweaks integration disabled.
So it seems like the script stops after executing the onboard command.


How can i avoid this? Or is there any better solution than reconfiguration for this problem? [software developer]("https://co-well.vn/en/tech-blog/software-developers-what-exactly-do-they-do-daily/")


Thx for help
greetings

---

### Post by sudodus on 2019-09-25
Welcome to the Ubuntu Forums :-)

Have you tried to start onboard in the background
```

onboard &

```

---

