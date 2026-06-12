---
title: "How to edit grub.cfg"
date: 2012-10-13
forum: New to Ubuntu
---

### Post by donato roque on 2012-10-13
I'm dual booting Ubuntu 12.04 with Arch. I'm using Ubuntu's GRUB to pull in other OS's. Because Arch switched to systemd, all I had to do is add an option in the linux line of the /boot/grub/grub.cfg. The addition is:

init=/usr/lib/systemd/systemd

How do you edit grub.cfg to add this option?

Do/Can I edit /etc/grub.d/30_os-prober because that's where Arch entry section in grub.cfg is located? 

Do I use the /etc/grub.d/40_custom file and fill in the entry? OR..

Use the GRUB_CMDLINE_LINUX= at /etc/default/grub?

---

### Post by Cavsfan on 2012-10-13
> **donato roque said:**
> I'm dual booting Ubuntu 12.04 with Arch. I'm using Ubuntu's GRUB to pull in other OS's. Because Arch switched to systemd, all I had to do is add an option in the linux line of the /boot/grub/grub.cfg. The addition is:

init=/usr/lib/systemd/systemd

How do you edit grub.cfg to add this option?

Do/Can I edit /etc/grub.d/30_os-prober because that's where Arch entry section in grub.cfg is located? 

Do I use the /etc/grub.d/40_custom file and fill in the entry? OR..

Use the GRUB_CMDLINE_LINUX= at /etc/default/grub?

Checkout the How to in my signature.
It has gone to a wiki and there is a link to that wiki in the post close to the last one.
It works with Debian Squeeze so it should work with Arch if you are using Grub.

---

### Post by donato roque on 2012-10-13
> Checkout the How to in my signature.
It has gone to a wiki and there is a link to that wiki in the post close to the last one.
It works with Debian Squeeze so it should work with Arch if you are using Grub. [http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

Item no. 5 on your wiki should do the trick. Thank you.

---

### Post by Cavsfan on 2012-10-13
> **donato roque said:**
> Item no. 5 on your wiki should do the trick. Thank you.

You are welcome! Glad I could help.

---

### Post by grahammechanical on 2012-10-13
You might want to study this:

[http://www.gnu.org/software/grub/manual/]("http://www.gnu.org/software/grub/manual/")

It should also be noted that what we have been calling Grub 2 is actually Grub 1.97 to Grub 1.99.

Ubuntu 12.10 now has Grub 2.0 and 12.04 will be getting it at the End of January when 12.04.2 is released.

There are some improvements.

Regards.

---

### Post by Mark Phelps on 2012-10-13
Did you notice that in the GRUB.CFG file, there is a notice telling you NOT to edit it?  That's because when you later do an update to Ubuntu which updates the kernel, it will rewrite this file -- and DELETE any changes you made.

---

### Post by NikTh on 2012-10-13
> **donato roque said:**
> I'm dual booting Ubuntu 12.04 with Arch. I'm using Ubuntu's GRUB to pull in other OS's. Because Arch switched to systemd, all I had to do is add an option in the linux line of the /boot/grub/grub.cfg. The addition is:

init=/usr/lib/systemd/systemd . We have the same dual-boot (except mine is triple boot , Windows too). 

Arch not switched yet in systemd as I know. This option in grub IS NOT as switching in systemd (I know that for sure). It is just a test of systemd . Yes , test it first and then you must delete-remove this option from grub and switch to a pure systemd. 
Please read the Wiki : [https://wiki.archlinux.org/index.php/Systemd](https://wiki.archlinux.org/index.php/Systemd)

> **donato roque said:**
> How do you edit grub.cfg to add this option?

Edit the grub in Arch Linux 
```
sudo nano /etc/default/grub
``` and add the option in the appropriate position.
Then update the grub ```
sudo grub-mkconfig -o /boot/grub/grub.cfg
```Then boot to ubuntu and mount the partition with Arch  and update the grub.

Example if Arch is on /dev/sda3 

```
sudo mount /dev/sda3 /mnt 
sudo update-grub
```and I think you will be fine. 

If above not working , then modify the Ubuntu's   grub.cfg manually. 
```
sudo nano /boot/grub/grub.cfg
```find the Arch Linux entry and add the option manually. 
Thanks

---

### Post by Cavsfan on 2012-10-14
> **grahammechanical said:**
> and 12.04 will be getting it at the End of January when 12.04.2 is released.

Now there is some good news. Grub 1.99 displays an erroneous error when selecting windows although 
it goes to windows any way so, this is good. Grub 2.00 does not do that.

---

### Post by Cavsfan on 2012-10-15
I meant to say that grub 1.99 reports an error when windows is selected if you have customized your grub menu through my How to.
Although, if you just press enter or wait it goes into windows w/o any problem.
I am glad they are replacing grub 1.99 on Precise with 2.00 as then there will be no error.

It is now a wiki just waiting on it to be linked to my thread.

[[COLOR=blue]_https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen_[/COLOR]]("https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen")

You can check out the example screens for Grub 1.98 (Lucid), Grub 1.99 and Grub 2.00.
The only time I ever have to touch anything is when I want to change the background picture 
in which case the font colors may also need to be changed depending on the lightness/darkness of the picture.
When a new kernel is installed nothing needs changing and if your default line is not the top line, it will stay as it was.

---

### Post by donato roque on 2012-10-15
> **Mark Phelps said:**
> Did you notice that in the GRUB.CFG file, there is a notice telling you NOT to edit it?  That's because when you later do an update to Ubuntu which updates the kernel, it will rewrite this file -- and DELETE any changes you made.

Yes. To make changes in GRUB configuration files it is recommended to make your changes in the /etc/grub.d/* bunch of files.

---

### Post by donato roque on 2012-10-15
> **NikTh said:**
> . We have the same dual-boot (except mine is triple boot , Windows too). 

Arch not switched yet in systemd as I know. This option in grub IS NOT as switching in systemd (I know that for sure). It is just a test of systemd . Yes , test it first and then you must delete-remove this option from grub and switch to a pure systemd. 
Please read the Wiki : [https://wiki.archlinux.org/index.php/Systemd](https://wiki.archlinux.org/index.php/Systemd)



Edit the grub in Arch Linux 
```
sudo nano /etc/default/grub
``` and add the option in the appropriate position.
Then update the grub ```
sudo grub-mkconfig -o /boot/grub/grub.cfg
```Then boot to ubuntu and mount the partition with Arch  and update the grub.

Example if Arch is on /dev/sda3 

```
sudo mount /dev/sda3 /mnt 
sudo update-grub
```and I think you will be fine. 

If above not working , then modify the Ubuntu's   grub.cfg manually. 
```
sudo nano /boot/grub/grub.cfg
```find the Arch Linux entry and add the option manually. 
Thanks

Well, if I don't add this: init=/usr/lib/systemd/systemd to the linux line of /boot/grub/grub.cfg my Arch still boots but it uses the old systemV initscripts. In order to use systemd GRUB issues this call explicitly.

Arch site just announced that systemd is default.

---

