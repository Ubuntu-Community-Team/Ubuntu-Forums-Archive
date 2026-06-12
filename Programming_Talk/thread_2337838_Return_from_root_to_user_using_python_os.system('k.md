---
title: "Return from root to user using python os.system('kill') not working"
date: 2016-09-22
forum: Programming Talk
---

### Post by bobby24 on 2016-09-22
[COLOR=#242729][FONT=Arial]I need to run a command from my python script as a root user (just sudo wont work), so I use os.system('sudo su') and am able to get root access. But again I need to return back to user . I tried os.system('exit'), but it still doesnt come out of root login to user login. I have to manually enter exit in the terminal to get back to user login. Can someone help me on how to do this in python ?

```
[/FONT][/COLOR][COLOR=#101094][FONT=Consolas]import[/FONT][/COLOR][COLOR=#303336][FONT=Consolas] os[/FONT][/COLOR]
[COLOR=#101094]import[/COLOR][COLOR=#303336] time
os[/COLOR][COLOR=#303336].[/COLOR][COLOR=#303336]system[/COLOR][COLOR=#303336]([/COLOR][COLOR=#7D2727]'clear'[/COLOR][COLOR=#303336])[/COLOR][COLOR=#303336] [/COLOR][COLOR=#858C93]#clear the terminal[/COLOR][COLOR=#303336]
os[/COLOR][COLOR=#303336].[/COLOR][COLOR=#303336]system[/COLOR][COLOR=#303336]([/COLOR][COLOR=#7D2727]'sudo eject /dev/sr0'[/COLOR][COLOR=#303336])[/COLOR][COLOR=#303336]
time[/COLOR][COLOR=#303336].[/COLOR][COLOR=#303336]sleep[/COLOR][COLOR=#303336]([/COLOR][COLOR=#7D2727]2[/COLOR][COLOR=#303336])[/COLOR][COLOR=#303336]
os[/COLOR][COLOR=#303336].[/COLOR][COLOR=#303336]system[/COLOR][COLOR=#303336]([/COLOR][COLOR=#7D2727]'sudo modprobe option'[/COLOR][COLOR=#303336])[/COLOR][COLOR=#303336]
time[/COLOR][COLOR=#303336].[/COLOR][COLOR=#303336]sleep[/COLOR][COLOR=#303336]([/COLOR][COLOR=#7D2727]2[/COLOR][COLOR=#303336])[/COLOR][COLOR=#303336]
os[/COLOR][COLOR=#303336].[/COLOR][COLOR=#303336]system[/COLOR][COLOR=#303336]([/COLOR][COLOR=#7D2727]'sudo su'[/COLOR][COLOR=#303336])[/COLOR][COLOR=#303336]
time[/COLOR][COLOR=#303336].[/COLOR][COLOR=#303336]sleep[/COLOR][COLOR=#303336]([/COLOR][COLOR=#7D2727]5[/COLOR][COLOR=#303336])[/COLOR][COLOR=#303336]
os[/COLOR][COLOR=#303336].[/COLOR][COLOR=#303336]system[/COLOR][COLOR=#303336]([/COLOR][COLOR=#7D2727]'echo 2001 7d0e > /sys/bus/usb-serial/drivers/option1/new_id'[/COLOR][COLOR=#303336])[/COLOR][COLOR=#303336]
time[/COLOR][COLOR=#303336].[/COLOR][COLOR=#303336]sleep[/COLOR][COLOR=#303336]([/COLOR][COLOR=#7D2727]2[/COLOR][COLOR=#303336])[/COLOR][COLOR=#303336] [/COLOR][COLOR=#303336][FONT=Consolas]os[/FONT][/COLOR][COLOR=#303336][FONT=Consolas].[/FONT][/COLOR][COLOR=#303336][FONT=Consolas]system[/FONT][/COLOR][COLOR=#303336][FONT=Consolas]([/FONT][/COLOR][COLOR=#7D2727][FONT=Consolas]'exit'[/FONT][/COLOR][COLOR=#303336][FONT=Consolas])[/FONT][/COLOR][COLOR=#242729][FONT=Arial]
```
[/FONT][/COLOR]

---

### Post by ian-weisser on 2016-09-22
I think your basic design is the problem.
'sudo' is designed to be a user-interactive command. Don't use it in a script or program.

One simple answer is to use 'sudo' during invocation to run the script as root.
Another answer, for more complex situations, is to for a user-level program to invoke a separate root-level program. Invocation and communication between the scripts is handled by dbus.

---

