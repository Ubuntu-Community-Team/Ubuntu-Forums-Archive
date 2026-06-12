---
title: "Changing Order of Default OS in Grub?"
date: 2014-02-24
forum: New to Ubuntu
---

### Post by JeQhdMD on 2014-02-24
Hello, just finished installing Ubuntu 13.10 on 2 PC's already running Kubuntu LTS and Windows 7.  Currently, the default OS that's loaded is Kubuntu.  I will continue to use Kubuntu as default OS on business laptop, but the family much prefers the Unity desktop for everyday use on our main desktop PC.   How do I re-enable Kubuntu loading as default OS on the laptop?

(btw - I'm amazed at how much progress is evident in Unity since the first rendition.  Also like what I'm reading about 14.04 - - thanks Canonical!)

[IMG][IMG]http://i.imgur.com/lRkn9Hf.png[/IMG][/IMG]

---

### Post by sudodus on 2014-02-24
See the following link, and change the variable **GRUB_DEFAULT=**

[https://help.ubuntu.com/community/Grub2/Setup#A.2BAC8-etc.2BAC8-default.2BAC8-grub](https://help.ubuntu.com/community/Grub2/Setup#A.2BAC8-etc.2BAC8-default.2BAC8-grub)

---

### Post by oldfred on 2014-02-24
Is this what you are looking for. At login screen you choose default desktop.

 How to choose Display manager sessions -  by kanasnoob 
[http://ubuntuforums.org/showthread.php?t=2184682&p=12929682#post12929682](http://ubuntuforums.org/showthread.php?t=2184682&p=12929682#post12929682)

Edit 
If two separate installs then sudodus' answer is more correct.

---

### Post by ajgreeny on 2014-02-24
Presumably at the moment Ubuntu's grub is in control.

If you boot to Kubuntu from the Ubuntu grub and then run the command ```
sudo grub-install /dev/sda
``` grub from Kubuntu will gain control and will put Kubuntu as the default OS. This assumes /dev/sda is the priority disk in your bootup.

---

### Post by JeQhdMD on 2014-02-26
Great fixes - thanks to all.   Will use these again in future updates.

---

