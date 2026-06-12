---
title: "Screen flashes on boot and takes long time to boot up"
date: 2019-12-19
forum: New to Ubuntu
---

### Post by tomjpalamattam on 2019-12-19
I am new to ubuntu and ubuntu forums so kindly excuse me for any mistakes i make. I tried dual booting ubuntu with win 10 and while booting ubuntu, ubuntu boot screen flashes with some code in the background. After booting the blinking stops and everything is fine

---

### Post by cpt-ankitsharma on 2019-12-21
There is nothing wrong with it. But if you dont want to see the code during bootup do the following steps:

1. You are going to open up the file /etc/default/grub, you can use vim or any other text editor of choice. I have used nano here assuming you are new.

> sudo nano /etc/default/grub

2. Find this line GRUB_CMDLINE_LINUX_DEFAULT

make sure that its set to

> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

Save and Exit

3. Run this command

> sudo update-grub

This is going to save and update your grub.

4. Reboot

You should not see any code. The screen might still flash. Its just your Xorg (Display Driver) getting activated.

---

