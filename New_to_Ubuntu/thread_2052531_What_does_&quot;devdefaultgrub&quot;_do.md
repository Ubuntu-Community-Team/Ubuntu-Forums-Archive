---
title: "What does &quot;/dev/default/grub&quot; do?"
date: 2012-09-03
forum: New to Ubuntu
---

### Post by aef54 on 2012-09-03
In the file "/ect/default/grub" I changed the line:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```to:
```
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"
```Because somebody advised me to. 

Can somebody explain me what I just did? I already figured out that Grub is the boot loader. If I understand correctly, that is a file/script that manages the booting of the operating system. Is that correct?  Changing that option did something to the layout of the screens. What did I do exactly?

---

### Post by Bashing-om on 2012-09-03
aef54;
            Hi !
  You have done no harm to your system...
grub in simplest terms is the intermediate step between bios and getting the operating system up and going.

 With the deletion of the options "quiet and splash", it is probable that you are booting to a command line log-in/boot messages displayed on your console screen.

 Edit your /etc/default/grub file again and insert either/or terms back into the line before the nomodeset option. (gksudo).. save the file and update the config file with the command:
```
sudo update grub
```

Here is a starter link to learn grub:
[help.ubuntu.com/community/Grub2]("http://ubuntuforums.org/help.ubuntu.com/community/Grub2")

[INDENT]regards <==BDQ

[/INDENT]

---

### Post by NikTh on 2012-09-03
Hello , 

a correction is** /etc/**default/grub and not [COLOR=Red]/dev[/COLOR]/default/grub. 

Take a look here for the parameter you added : [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Thanks

---

### Post by aef54 on 2012-09-03
> **NikTh said:**
> Hello , 

a correction is** /etc/**default/grub and not [COLOR=Red]/dev[/COLOR]/default/grub. 

Take a look here for the parameter you added : [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Thanks
Whoops, you are totally right. My bad. 

Thanks for the replies guys.

---

