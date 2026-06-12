---
title: "Bash default boot changer [0-9] | [0-9][0-9]"
date: 2011-03-19
forum: Programming Talk
---

### Post by highspider on 2011-03-19
This code will display all your boot menus in number rows and you enter a number for what menu number (OS) you want as your default boot.

Idea robbed from here [http://ubuntuforums.org/showthread.php?p=10574434](http://ubuntuforums.org/showthread.php?p=10574434)

This it works fine for my ubuntu 10.10 with grub2 
```

#!/bin/bash
grep menuentry /boot/grub/grub.cfg | cut -b 1-11 --complement | cut -d "'" -f1 | cut -d "\"" -f 1 | nl --starting-line-number=0
read -p "Enter default boot number: " new
sudo sed -i 's/default='[0-9]'/default=\"'$new'\"/g' /boot/grub/grub.cfg

echo "New Defualt OS boot is:"
grep menuentry /boot/grub/grub.cfg | cut -b 1-11 --complement | cut -d "'" -f1 | cut -d "\"" -f 1 | nl --starting-line-number=0 | grep ^[[:space:]]*$new 

```pseudo code would be [COLOR=Green]while loop VAR is not 0-29 [/COLOR]
just a [COLOR=Red]number 1 or 2 digits[/COLOR]- range don't matter
```

#!/bin/bash
while [[ "$new" != [COLOR=Green][0-9] | [0-2][0-9][/COLOR] ]]; do
grep menuentry /boot/grub/grub.cfg | cut -b 1-11 --complement | cut -d "'" -f1 | cut -d "\"" -f 1 | nl --starting-line-number=0
read -p "Enter default boot number: " new
done
sudo sed -i 's/default='[COLOR=Red][0-9] | [0-2][0-9][/COLOR]'/default=\"'$new'\"/g' /boot/grub/grub.cfg

echo "New Defualt OS boot is:"
grep menuentry /boot/grub/grub.cfg | cut -b 1-11 --complement | cut -d "'" -f1 | cut -d "\"" -f 1 | nl --starting-line-number=0 | grep ^[[:space:]]*$new  

```

---

