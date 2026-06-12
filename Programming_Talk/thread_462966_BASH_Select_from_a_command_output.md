---
title: "BASH: Select from a command output"
date: 2007-06-03
forum: Programming Talk
---

### Post by daller on 2007-06-03
Hi there,

I would like a way to get a bash script output each line of the command "cat /sys/bus/usb/devices/*/product" as a select option! - It's meant as a way for the user to select the right input device...

The output looks like this:

Tablet WP5540U
UHCI Host Controller
UHCI Host Controller
UHCI Host Controller
EHCI Host Controller

Afterwards, the selected device should be inserted in this command:
---------------
sudo bash

echo 'BUS=="usb", KERNEL=="event*", SYSFS{product}=="XXXXX- ANSWER HERE -XXXXX", NAME="input/%k", SYMLINK+="tablet-event", MODE="0666"' >> /etc/udev/rules.d/010_local.rules

exit
---------------

How do i do this?

BTW: Why doesn't a "sudo echo" command work in this case?

And can the select option be overruled to select any option containing the word "tablet" - so that the user doesn't have to find it manually! - Only in the cases where "tablet" is not a part of the name...
Alternately, it could record the output from "cat /sys/bus/usb/devices/*/product" before and after the tablet is connected, and simply grap the diff?

---

### Post by ghostdog74 on 2007-06-03
```

cat /sys/bus/usb/devices/*/product | awk 'BEGIN{ while (getline line > 0) {
                                                    arr[++c] = line
                                                    print c")"line
                                                   }                                       
                                                   printf "Select option: "
                                                   getline choice < "/dev/tty" 
                                                   string = "BUS==\"usb\", KERNEL==\"event*\", SYSFS{product}==\"" 
                                                   string = string arr[choice] "\", NAME=\"input/%k\", "
                                                   string = string "SYMLINK+=\"tablet-event\", MODE=\"0666\""                                  
                                                   print string
                                                   print string > "/etc/udev/rules.d/010_local.rules"                                               
                                          }'

```

---

### Post by duff on 2007-06-03
> **daller said:**
> 
And can the select option be overruled to select any option containing the word "tablet" - so that the user doesn't have to find it manually! 

If your in a gnome environment, why not give **zenity** a shot...no typing required.
```
# cat /sys/bus/usb/devices/*/product | zenity --list  --column="Device"
```

---

### Post by Ramses de Norre on 2007-06-03
> **daller said:**
> BTW: Why doesn't a "sudo echo" command work in this case?

When you run ```
sudo echo test >> file
```the program "echo" is ran by sudo but the shell built-in ">>" is ran by your current shell which isn't influenced by the command (and thus the sudo) in front of the pipe.
So to achieve what you want you need to either run your shell as root as you're doing now or use a simple command instead of ">>" and run that with sudo.
The second option is much safer and such a program is built-in into every linux distro, it's called tee. Use the -a option to append, so the command would become ```
echo test | sudo tee -a file
```
And please don't run echo as root, that's totally redundant...

---

### Post by daller on 2007-06-03
> **duff said:**
> If your in a gnome environment, why not give **zenity** a shot...no typing required.
```
# cat /sys/bus/usb/devices/*/product | zenity --list  --column="Device"
```

I'm not running gnome, and I would like this to be a generic solution!

---

### Post by daller on 2007-06-03
> **ghostdog74 said:**
> ```

cat /sys/bus/usb/devices/*/product | awk 'BEGIN{ while (getline line > 0) {
                                                    arr[++c] = line
                                                    print c")"line
                                                   }                                       
                                                   printf "Select option: "
                                                   getline choice < "/dev/tty" 
                                                   string = "BUS==\"usb\", KERNEL==\"event*\", SYSFS{product}==\"" 
                                                   string = string arr[choice] "\", NAME=\"input/%k\", "
                                                   string = string "SYMLINK+=\"tablet-event\", MODE=\"0666\""                                  
                                                   print string
                                                   print string > "/etc/udev/rules.d/010_local.rules"                                               
                                          }'

```

Is there a way to make it selectable with button up/down? - Else than that, it's great!

---

