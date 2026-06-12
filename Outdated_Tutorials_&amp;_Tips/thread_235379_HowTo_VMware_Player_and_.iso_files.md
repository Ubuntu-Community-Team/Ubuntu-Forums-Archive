---
title: "HowTo: VMware Player and .iso files"
date: 2006-08-13
forum: Outdated Tutorials &amp; Tips
---

### Post by shookmon on 2006-08-13
Since VMware Player doesn't allow you to change where the CD-Rom is connected to like Workstation does, you lose the ability to connect to different .iso files while the virtual machine is running.

The solution here is to create a second CD-ROM device in your .vmx file and have that device pointed to a symbolic link. This allows you to disconnect the 2nd CD-ROM, change the symbolic link, and reconnect the CD-ROM. Your new .iso gets mounted.

Here's the code to add if you have a more or less "standard" .vmx file:

```

# Settings for .iso CDROM drive
ide1:1.present = "TRUE"
ide1:1.startConnected = "FALSE"
ide1:1.autodetect = "FALSE"
ide1:1.deviceType = "cdrom-image"
ide1:1.filename = "/home/user/myCD.iso"

```

Then when you need to, use this code to change the symbolic link in a terminal:

```

user@Ubuntu:~$ ln -s -f [COLOR="Red"]/media/FIRELITETWO/VMwareTools/linux.iso[/COLOR] myCD.iso

```

Just change the text I have in Red with the actual location of your .iso file.

Hope this helps!!

---

### Post by dameat on 2008-04-11
Awesome tip - thanks! I knew there had to be a way around that limitation. Hooray for the power of linux!

---

