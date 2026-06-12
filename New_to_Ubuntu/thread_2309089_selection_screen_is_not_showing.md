---
title: "selection screen is not showing"
date: 2016-01-07
forum: New to Ubuntu
---

### Post by shivank1969 on 2016-01-07
I was using windows 8.1 and then afterwards, I install [COLOR=#000000][FONT=Ubuntu Mono]Ubuntu 14.04[/FONT][/COLOR] next to windows 8.1. Both of them windows and ubuntu works perfectly for approx 4 months. Then after that one day, I was working on windows and then suddenly a blue screen pops with a message "Your PC ran into a problem and need to restart" and then restart fails and also it was asking for recovery media. But I press the power button to shutdown the laptop and then when I restart it there was no selection screen. It automatically opens the windows. There is no way to go to ubuntu. How to resolve the problem? 
Thanks in advance.

---

### Post by leunam12 on 2016-01-08
First thing is to check if your hard drive is failing. If it's failing it has to be replaced. If your hard drive is not failing, then download a program to open the memory dump that was created when you got the blue screen of death. See what caused the problem and if it can be fixed. Now, none of this is going to solve your GRUB problem but it will prevent other problems in the future including loss of data.

If you just want to restore GRUB run boot-repair.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

