---
title: "Problem with the Ati binary driver and xorg.conf"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by Asem on 2008-11-12
Hello every one,

I just installed Uubuntu 8.10 couple of days ago and i downloaded the ATI binary driver but it didnt work .
I have Radeon 9200 card and in ubuntu hardy the binary driver didnt support it but on the details of the driver that i downloaded i found my card listed there ,but after the reboot the pc run on the safe graphic mode.

Now i uninstalled the driver and the pc is normal again  but i need to know why the driver didnt work and why the default xorg.conf is empty ?

Good bye and have a nice day

---

### Post by mapes12 on 2008-11-13
If you are getting the correct screen resolution you need then I would suggest there is no need to bother with the drive. If not then please post again.

---

### Post by binbash on 2008-11-13
Dude you dont need any xorg file with new xorg.You will download : 

sudo apt-get install build-essential xorg-driver-fglrx and you have to give sudo aticonfig --initial command.


But dont forget to update your repos with sudo apt-get update && sudo apt-get upgrade

---

### Post by Asem on 2008-11-13
Thanks for the replies

binbash i tried your method and i get the output of the  sudo aticonfig --initial like this

uninitialised file found,
segmentation fault

and the pc switch to safe graphic mode after reboot 

may be [mapes12]("http://ubuntuforums.org/member.php?u=472717") is right i get the right resolution so i dont need a driver anyway but i can't help noticing that the performance is poor compared to that on windows.

Thanks again , bye

---

