---
title: "Close lid behavior problem"
date: 2022-02-10
forum: New to Ubuntu
---

### Post by ra-white on 2022-02-10
System: Ubuntu 20.04.3
Problem:
When I close lid the computer suspends itself.
When I open the lid again, it will automatically suspend itself after 30 seconds, despite typing on keyboard etc.

I have unsuccessfully tried the method to edit the file [COLOR=#000000][FONT=Monaco]sudo gedit /etc/systemd/logind.conf
[/FONT][/COLOR]After removing hash tag:

24 HandleLidSwitch=ignore
25 HandleLidSwitchExternalPower=ignore
26 HandleLidSwitchDocked=ignore


Could anyone please help me out here?

1. I don't want my laptop to suspend when I close the lid.
2. If I want my laptop to suspend/hibernate/shutdown when closing lid, I don't want it to automatically suspend after 30 seconds after re-opening lid.

Thanks

---

### Post by ra-white on 2022-02-11
Solved it now by follow the instructions STEP BY STEP:


1. sudo gedit /etc/systemd/logind.conf
2. Remove hashtag from row 24 and set to ignore
    HandleLidSwitch=ignore
3. sudo systemctl restart systemd-logind.service

Now, the screen got blank (with backlight on) and headphones disconnected.
Nothing happened.
I ctrl-alt-del and alt+f4
Laptop reboot
Problem solved \\:D/

---

