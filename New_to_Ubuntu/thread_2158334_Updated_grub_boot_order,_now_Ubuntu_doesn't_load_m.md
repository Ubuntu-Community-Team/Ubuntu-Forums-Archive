---
title: "Updated grub boot order, now Ubuntu doesn't load my graphic drivers properly."
date: 2013-06-28
forum: New to Ubuntu
---

### Post by leotemp on 2013-06-28
So i just installed Ubuntu 12.0.4.2 LTS on my win7 box so it dual boots. Everything was going fine, even got my printer that wouldn't work in win-7 to run perfectly. One thing that bothered me was starting Windows by default when booting, so i - sudo gedit /etc/default/grub - then I changed the default boot option to 1 the second option on the boot menu which is "Ubuntu". Then I - sudo update-grub - it did some grinding and appeared to be all finished proper. So i reboot, Windows is still the default option, Okay, whatever *sigh*.. then after selecting Ubuntu it tells me that there's some issue with loading graphic drivers or something (sorry i wasn't paying attention :\ ) then the Ubuntu boot screen appears but there isn't the nice Ubuntu animated, loading image. On the login screen the desktop background is all crappy looking and white squares are all over the place, when i login the desktop is kind of grainy and stretched, I do front-end work so this won't do at all. I tried re-editing the grub file again and putting it back to the way it was but zero change. What the hell have i done and how do i fix it?

Thanks for any help in advance, you guys always pull my ass out of the fire somehow.

leotemp

---

### Post by jp734 on 2013-06-28
Usually there is an advanced boot option. Try clicking that and see if there is more than one kernel available for boot. Try the other one if there is.

---

### Post by leotemp on 2013-06-28
> **jp734 said:**
> Usually there is an advanced boot option. Try clicking that and see if there is more than one kernel available for boot. Try the other one if there is.

Um, where would these Advanced options be to click on them?

---

### Post by newb85 on 2013-06-28
Um... usually Ubuntu is the default in Grub.  Are you sure you didn't use the Windows Ubuntu installer?   That uses the Windows bootloader.

---

### Post by leotemp on 2013-06-28
> **newb85 said:**
> Um... usually Ubuntu is the default in Grub.  Are you sure you didn't use the Windows Ubuntu installer?   That uses the Windows bootloader.

Yes that is correct, I installed Ubuntu from within Windows 7.

---

### Post by leotemp on 2013-06-28
I think i understand now, if i wanted to alter the boot order of the OS i would need to do it from Windows as Windows created the boot partition or what have you? My problem is how do i undo the weird damage i somehow did by changing that single option in grub?

---

### Post by oldfred on 2013-06-28
Do you get grub menu? Then you should be able to manually select the first option or entry 0 in grub configuration. 

 [https://wiki.ubuntu.com/WubiGuide#How](https://wiki.ubuntu.com/WubiGuide#How) can I access my Wubi install and repair my install if it won%27t boot?

      
 Change boot order
[http://www.psychocats.net/ubuntu/wubi#bootorder](http://www.psychocats.net/ubuntu/wubi#bootorder)


 [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)
      
 bcdEdit - bcbc
[http://ubuntuforums.org/showpost.php?p=11927905&postcount=5](http://ubuntuforums.org/showpost.php?p=11927905&postcount=5)
[http://askubuntu.com/questions/145444/how-do-i-remove-the-extra-ubuntu-option-on-the-windows-boot-manager-menu](http://askubuntu.com/questions/145444/how-do-i-remove-the-extra-ubuntu-option-on-the-windows-boot-manager-menu)

I think if you cannot boot, you will need a live DVD or flash drive version of Ubuntu to mount and edit the wubi install or make whatever repairs are required.

      
 Also instructions for DVD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to flash or DVD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by leotemp on 2013-07-02
Thank you for this reply!

---

