---
title: "Bash script question (permission privileges)"
date: 2008-06-24
forum: Programming Talk
---

### Post by dresnu on 2008-06-24
Hello, I'm trying to write a script to switch my laptop's brightness. The idea is to have an executable that when launched changes the brightness from full to dim and the opposite, like a cycling program.
Now I have little experience in bash programming so I need some help. This is what I have written so far:
```
#!/bin/bash
#

if [ `cat /proc/acpi/video/VGA/LCD/brightness | grep current | awk '{printf("%1d\n", $2)}'`==35 ]; then
        echo 90 | dd of=/proc/acpi/video/VGA/LCD/brightness
else
	echo 35 | dd of=/proc/acpi/video/VGA/LCD/brightness
fi

exit

```

(35 - 90 are the two values I would like be able to cycle through)

The main problem is that to execute the echo commands I need to have superuser privileges from the command line (a simple sudo gives permission denied, so I need to do sudo bash first) and I don't know how to incorporate this in the script.
I don't mind having to launch the script with a sudo/kdesu command in order to make it work but I don't want to change any permission privileges to the brightness file.

Thanks in advance.

---

### Post by _sphinx_ on 2008-06-24
Use the following```
echo <password>|sudo -S <command>
```
to execute a command under the root previlages through the script. But use it carefully.

---

### Post by ad_267 on 2008-06-24
If you want to run this from a launcher you can use gksudo to bring up a dialog box to enter your password. I guess that could be annoying if you are doing this often though.

---

### Post by geirha on 2008-06-24
Your if-expression can be shortened a bit by using only awk, like in the code-section below. I've also added a couple of examples of how to use (gk)sudo to write to a file using root privileges.
[php]
if [ `awk '/current/ {printf("%1d\n", $2)}' /proc/acpi/video/VGA/LCD/brightness` == 35 ]; then
  echo 90 | sudo dd of=/proc/acpi/video/VGA/LCD/brightness
  echo 90 | sudo tee /proc/acpi/video/VGA/LCD/brightness
  gksudo -- bash -c 'echo 90 >/proc/acpi/video/VGA/LCD/brightness'
[/php]

EDIT:
One would expect gksudo to behave just like sudo (except asking for passwords differently), however, sudo will pass on stdin to its application, while gksudo will not, so in the above examples, sudo can not be replaced with gksudo. (the gksudo one can be replaced by sudo though)

---

### Post by dresnu on 2008-06-24
Thanks to all! I did it with a mixture of both sudo -S and gksudo by having: ```
echo <password>|sudo -S gksudo -- bash -c 'echo 90 >/proc/acpi/video/VGA/LCD/brightness'
```

This way I don't have to type the password everytime; I don't have any major safety concerns as I'm the only user on this pc.

Special thanks to geirha for polishing my code! :-)

PS: works also with ```
echo <password>|sudo -S echo 90 | sudo tee /proc/acpi/video/VGA/LCD/brightness
``` but not with "sudo dd" which gives permission denied error.

---

