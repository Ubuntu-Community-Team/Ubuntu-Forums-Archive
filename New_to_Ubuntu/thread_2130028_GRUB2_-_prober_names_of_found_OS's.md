---
title: "GRUB2 - prober names of found OS's"
date: 2013-03-28
forum: New to Ubuntu
---

### Post by zardoz1971 on 2013-03-28
I have multiboot pc with grub2. Prober is active so it finds linux and windows. But I would like it to give another title to found Windows OS, like "W8" for instance. Now, I now I can do it manually by changing file that grub makes, but it's not supposed to be done that way and every time I would run update-grub it would have to be done again.

So, is there a way to tell prober something like: when you find windows 8 name it W8?

---

### Post by deadflowr on 2013-03-28
You could look at this

[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

but I follow the basics of this

[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)

---

### Post by zardoz1971 on 2013-03-28
Sorry but that doesn't help. I don't want to use grub customizer but just edit script the right way.

---

### Post by deadflowr on 2013-03-28
> **zardoz1971 said:**
> Sorry but that doesn't help. I don't want to use grub customizer but just edit script the right way.

Then use a custom menu.

Your /etc/grub.d folder contains a file for customizing your system.

Unless you change the name of the system, OS-prober is going to keep grabbing the existing name of the windows system and use that.

Setting a custom menu will allow you to set the name you want, and keep it that way.

If you have inquiries about customizing grub, look over this thread:

[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)

---

### Post by grahammechanical on 2013-03-28
If you are serious about doing it the right way then you should download the Grub manual.

[http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/)

---

### Post by oldfred on 2013-03-28
Cavsfan converted thread to a help wiki.

 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
Older thread
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

You turn off os-prober and just copy entries you want into 40_custom (or 06_custom if you want them first).

      
 In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or turn off executeable bit
sudo chmod a-x /etc/grub.d/30_os-prober


 Copy the windows entries from this:
sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup
gedit /boot/grub/grub.cfg
Copy them to and edit only titles:
gksudo gedit /etc/grub.d/40_custom
Then do:
sudo update-grub

For more detail see cavsfan's thread posted several times previously or the wiki summary version.

---

