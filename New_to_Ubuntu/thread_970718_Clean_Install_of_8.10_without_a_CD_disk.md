---
title: "Clean Install of 8.10 without a CD disk"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by Settler on 2008-11-04
As the title says I want to clean Install 8.10 and format root directory and keep /home directory as it is. But I don't have any blank CD so what should I do?

Thanks

I have the alternate.amd64.iso will the live cd be needed?..

thanks again

---

### Post by stephanvaningen on 2008-11-04
You don't have a blank CD? You can create a startup USB, either via the function of another computer having 8.10 or via a procedure described on [www.pendrivelinux.com](www.pendrivelinux.com)

keeping the /home: you can create more than 1 partition, moving the /home to another partition make a mount-script after clean-install, or you can backup/restore the home before/after the install

---

### Post by Peter09 on 2008-11-04
The alternate CD is a text based installer, you do not need the live CD. You just do not get the option to run Ubuntu from the CD, it goes straight to the install process.

Sorry - thought you said that you had an alternate CD.

---

### Post by Paqman on 2008-11-04
Do you have Windows installed? If so you can use Wubi to install without a disk.

---

### Post by snowpine on 2008-11-04
You can use Unetbootin to transfer the .iso to a bootable USB thumb drive. This is exactly how I installed 8.10 to my eee (which has no CD drive).

---

### Post by Settler on 2008-11-04
I have Ubuntu 8.10 via upgrade. But I hate all the update process and prefer a clean install. So I'll try with the USB stick...

---

### Post by bodhi.zazen on 2008-11-04
[uhelp]community/Installation[/uhelp]

    [indent]There is a section on no CD ...[/indent]

Do you already have a separate /home partition ? If not, you will have to do that first.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by Settler on 2008-11-05
problem is solved

---

### Post by stephanvaningen on 2008-11-06
> **Settler said:**
> problem is solved

Ok, can you give feedback what you did? In that way another reader with the same problem can try your solution.
--
If all is good for you know, the please mark this thhread as solved *(Go to right-top 'thread tools' -> Mark this thread as solved)*

---

