---
title: "Having problems changing boot order in Grub"
date: 2014-08-10
forum: New to Ubuntu
---

### Post by Ringo Mountbatten on 2014-08-10
I'd like to make Windows the default in Grub and reduce the wait time to 2 seconds.

I'm trying to work through the articles [here]("http://askubuntu.com/questions/100232/how-do-i-change-the-grub-boot-order") and [here]("http://www.howtogeek.com/howto/43471/how-to-configure-the-linux-grub2-boot-menu-the-easy-way/").

Unfortunately I cannot get Grub Customizer to start. 

I have entered into the terminal

sudo add-apt-repository ppa:danielrichter2007/grub-customizer
sudo apt-get update
sudo apt-get install grub-customizer

and it seemed to have installed something. However when I search my computer for 'grub' or look through all my installed applications, nothing shows up for grub or grub customizer.

Then I tried typing gksudo grub-customizer in the terminal. This asked me for my password, but after I entered it nothing else happened.

This is on Ubuntu 14.04, with Grub 2.02, dual booting with Windows 8.1

edit - I managed to do it by manually editing the config file as described by Marve [here]("http://askubuntu.com/questions/100232/how-do-i-change-the-grub-boot-order").

---

