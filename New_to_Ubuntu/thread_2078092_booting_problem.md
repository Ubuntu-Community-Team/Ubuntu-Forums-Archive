---
title: "booting problem"
date: 2012-10-30
forum: New to Ubuntu
---

### Post by VcRam on 2012-10-30
Hey can any one please help me. and please don't say that it already had so many threads because those haven't helped me a lot really.
I had a dual boot on my system.... i tried to uninstall Linux from my system with a third party software, after doing that i tried do deleted the  volume consisted by Ubuntu, but when i restarted my pc it shows an error..
GRUB Loading stage 1.5
GRUB loading. please wait...
Error 17

now i made my usb port bootable as my cd drive not functioning properly, I downloaded some other version of linux but still not booting.. i used super grub disk   , its gives me foolowing option..
Default
Super Grub Disk Try to detect boot device and boot distro_menu .lst
Windows(advanced)
boot master boot record(MBR)
show partition boot slice....

and so on, at the bottom of this it says press[tab] to edit option
i tried different command like
bootrec.exe
but it says kernel image not found.. what should I do.. please anyone help me... I have an inspron 1545.. i had four drive c, d , e ,f.. window 7 was installed on drive c.. and linux on d.. when i tried to uninstalled Ubuntu  i was log into window 7... please any one help me. I am really in a big trouble...:(

---

### Post by NikTh on 2012-10-30
Hi , 
did you try with boot-repair program ? 
2nd option from Live Ubuntu CD/USB
[https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu](https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu)

Also you can paste here the link with boot-info.

Thanks

---

### Post by VcRam on 2012-10-30
how can I use all these when i Can't even start my laptop...? its not even booting...

---

### Post by VcRam on 2012-10-30
actually i installed super grub disk with unetbootin on my usb... but as i expalined earlier, its mot helping me.. its gives the option, which i already mentioned...

---

### Post by danelwillis on 2012-10-30
An easy option, you can make a bootable usb with a linux distro an install it along side any other OS you are using an it should fix the grub but your still Dual-booting wat other OS are you using?

---

### Post by newb85 on 2012-10-30
> **VcRam said:**
> how can I use all these when i Can't even start my laptop...? its not even booting...

You can boot from a USB, right?  You can install and run Boot Repair in a Live session.

---

### Post by VcRam on 2012-10-30
i didn't get u, if u asking me to make usb bootable. Actually that is not a problem, i have made it bootable so many time with different option like slax, super grub , window and all. But after that i don't have any clue. Coz it saying kernel image not found. I was using window 7 and ubuntu both

---

### Post by danelwillis on 2012-10-30
Ok if you want the easy solution, install a new copy of linux distro it will fix the boot errors an it will work along side of windows aswell as another Linux OS it should fix the grub by installing a fresh copy i had this problem before it takes a bit longer but its nearly always guaranted to work, well for me anyway

---

### Post by VcRam on 2012-10-30
danelwills linux distro? Its another version of linux? Actually don't have much knowledge of linux. It can be booted with usb as well, because as i said earlier cd dive not working and can u please give me the distro download link?

---

### Post by danelwillis on 2012-10-30
VcRam when i say distro i mean OS like ubuntu 12.10 or Kubuntu 12.10 its a diffrent version of linux i use kubuntu as oppose to ubuntu

---

### Post by VcRam on 2012-10-30
danelwills i will try with this,but whenever i made my usb bootable, i did it with 3rd party software like wubi, unetbootin. Hope these will install linux on pendrive.

---

### Post by NikTh on 2012-10-30
> **VcRam said:**
> danelwills i will try with this,but whenever i made my usb bootable, i did it with 3rd party software like wubi, unetbootin. Hope these will install linux on pendrive.

Unetbootin will make your USB bootable automatically. 

You will need the .iso image of Ubuntu 
[http://releases.ubuntu.com/12.04/](http://releases.ubuntu.com/12.04/)

Unetbootin program
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

And a USB-flash 2GB , formated Fat32 filesystem. 

Of course to create all these , you will need an Operation System where works . Windows are good as well. 

Then boot from liveUSB click the first option "Default" and run boot-repair. 

Thanks

---

### Post by VcRam on 2012-10-30
NikTh the link u gave me have so many download link.. i don't know which one to download....? i mean i know the configuration of my system.. still a lot of confusen.. iso file will be enough to boot and fix the problem...?  mine is 32 bit system. i tried with super grub.. but didn't worked out for me..... aS i mentioned u complete problem...

---

### Post by NikTh on 2012-10-30
> **VcRam said:**
> NikTh the link u gave me have so many download link.. i don't know which one to download....? i mean i know the configuration of my system.. still a lot of confusen.. iso file will be enough to boot and fix the problem...?  mine is 32 bit system. i tried with super grub.. but didn't worked out for me..... aS i mentioned u complete problem...

If your system is 32bit (the installed-corrupted I mean) then download the 
[PC (Intel x86) desktop CD]("http://releases.ubuntu.com/12.04/ubuntu-12.04.1-desktop-i386.iso")

If you create a bootable usb with this iso , then boot from there and click the first option **Default** you can use the boot-repair program , the second option , look here: 
[https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu](https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu)

to install and use the Boot-Repair. Click the [Recommended Repair] and do not forget to give here the link that boot-repair will create. A link with useful informations. 

Thanks

---

### Post by VcRam on 2012-10-31
hey nikth thanks man... my problem is solved.... thanks a lot....:) but one thing actually I don't want to use ubuntu now... I want to use only window, and I am afraid if I again try to delete it, i l be in a trouble.....  it is taking some space on hard disk.. so can u please tell me a proper way to do it..... anyway  thanks again.... thank u so much...

---

