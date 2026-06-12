---
title: "Ubuntu wont boot blinking cursor"
date: 2013-07-11
forum: New to Ubuntu
---

### Post by lisamarcell on 2013-07-11
I used Wubi to complete a dual boot with Windows Vista. Everything went fine (I thought), but when I tried to reboot the computer, I scrolled down to Ubuntu, hit enter and then nothing. I got a blank screen with a blinking cursor. I tried to hit shift, while it was booting, but nothing will happen. I have used Ubuntu before, but never had to work on it, my cousin did everything for me. Can someone please help me. Thanks

---

### Post by fosterD on 2013-07-11
hi, I have experienced something similar, not sure if it does apply to  you. In my case, I had problems with the login screen. What I did was  reinstall and reconfigure lightdm.
Press Ctrl-Alt-F1 and login with your username and password
then
> sudo apt-get install --reinstall lightdm
sudo dpkg-reconfigure lightdm
sudo reboot
hope this can solve your problem

---

