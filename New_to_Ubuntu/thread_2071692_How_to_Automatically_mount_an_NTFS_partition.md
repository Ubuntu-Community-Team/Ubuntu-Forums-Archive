---
title: "How to Automatically mount an NTFS partition"
date: 2012-10-16
forum: New to Ubuntu
---

### Post by duttashantanu on 2012-10-16
Hello, I am using _*Ubuntu 12.04.01 precise pangolin*_. I have an NTFS partition which I need every time I start Ubuntu. So can you help me to create a startup program for mounting it?

INFO:-

[LIST=1]
[*] It is located in _**/dev/sda5**_.
[*]I have tried creating a program using '*mount*' on '*Startup Applications*'. But when trying the command in *Terminal *I got the answer : *You need to be root* but I could mount it from graphical interface as a regular user.
[*]I typed in *Terminal*, [FONT=Courier New]mount -t ntfs/dev/sda5 /media[/FONT] as it was in /media after mounting from graphical interface.
[/LIST]
Found solution in [https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions). Problem solved. Thank you.

---

