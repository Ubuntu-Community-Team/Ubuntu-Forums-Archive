---
title: "Nvidia 840m external monitor issue."
date: 2015-06-01
forum: New to Ubuntu
---

### Post by Henry_Kukk on 2015-06-01
Hello everybody,

I am rather new to linux systems and working with them. I have had an issue with my laptops dedicated 840m GPU for a while, finally got it working with xserver and it seems to do its job. However, when I connect my external monitor, either both(laptop and external) screens go black or after messing about and switching between GPU's i managed to get a corner on my external screen occupied by OS. Probably, since my laptop screen is 1366x768 & my external is 1920x1080, it fails to change my resolution for some reason. I can still move about with my cursor on the black area but the bar op top cuts off. However, if checking from xserver application, it seems to understand, that my monitor is 1920x1080. I am currently running the latest 352 nvidia driver, however I also had this issue with the former, 349 driver. Any help is sincerely appreciated. 

Best wishes,
Henry

---

### Post by dino99 on 2015-06-01
welcome to ubuntu ):P

you seems have installed the driver directly from nvidia source, which is not the common ubuntu usage. So i propose you some commands to set the ubuntu ways: from a terminal, run :

> sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo apt-get update
sudo apt-get purge nvidia*
sudo apt-get install -f
sudo apt-get install nvidia-346 (available into vivid archive only and up)
sudo reboot

---

### Post by Henry_Kukk on 2015-06-01
Thank you for the answer. Did all the steps, but it failed to solve my issue. I added a picture to make my issue clearer. [[IMG]http://imagizer.imageshack.us/v2/320x240q90/912/Uf72N4.jpg[/IMG]]("https://imageshack.com/i/pcUf72N4j")

EDIT:
> (nvidia-settings:2517): Gdk-WARNING **: nvidia-settings: Fatal IO error 11 (Resource temporarily unavailable) on X server \u0010\xd1\xe3\u0002.


Is what i get when trying to detect displays in xserver.

---

### Post by Henry_Kukk on 2015-06-03
Feeling lost :(. Can't seem to find a fix .

---

