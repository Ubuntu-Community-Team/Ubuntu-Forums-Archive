---
title: "HowTo: Wireless Radio Software Switch"
date: 2006-11-21
forum: Outdated Tutorials &amp; Tips
---

### Post by elektronaut on 2006-11-21
[EDIT:] This thread was renamed as the problem is solved and now it's kind of a HowTo.
--------------------------------------------------------------------------------------

Hi,

I want to enable and disable my wireless card using the wlan switch. So I wrote a script that needs root privileges as it needs write access to a sysfs file. For those interested, here's the script:
```
#!/bin/bash
# this is the script /usr/local/bin/3945-toggle-state

STATE=$(cat /sys/bus/pci/drivers/ipw3945/*/rf_kill)

if [ "$STATE" == 1 ]
then
        echo 0 > /sys/bus/pci/drivers/ipw3945/*/rf_kill
else
        echo 1 > /sys/bus/pci/drivers/ipw3945/*/rf_kill
fi

exit 0
```
In order to avoid entering the sudo password each time, I added this to /etc/sudoers **(Be careful and use visudo, otherwise you could get into trouble)**:
```
me ALL=NOPASSWD: /usr/local/bin/3945-toggle-state
```
So far, so good: This works if I call the script in the terminal. But as I wanted to attach it to the wlan switch, I found out it's keycode using 'tail -f /var/log/messages' and set it to another value 'sudo setkeycodes e055 149'. Then I added an entry in the configuration file for xbindkeys, xbindkeysrc.scm: ```
(xbindkey '("m:0x0" "c:149") "sudo /usr/local/bin/3945-toggle-state")
```But it doesn't work. If I replace the call to the script with some other command, gaim for example, it works: The program is called upon activation of the switch. But not my script. Why is this so?

[EDIT:] ](*,) I guess I just stared too long at the screen... There was an error in the path. I corrected this now, so you can use it as a HowTo 8) Everything is working now :D

---

### Post by elektronaut on 2006-12-03
One thing still puzzles me: I have this in /etc/rc.local:
```
setkeycodes e055 213

```
and this in ~/.xbindkeysrc.scm:
```
(xbindkey '("m:0x0" "c:118") "sudo /usr/local/bin/3945-toggle-state")
```
and it works though the keycodes are different. I found out about the keycode using 'xev'. How does it come that the keycode is set to 118 and not 213?

---

