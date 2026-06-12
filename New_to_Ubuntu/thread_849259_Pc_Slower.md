---
title: "Pc Slower"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by prap19 on 2008-07-04
Hey
   I am a newbie.:confusedMy UBUNTU version is 8.04.My speed of PC was good until i installed WINE,Then  i installed WAMP using wine.And now the PC has slower than before.I uninstalled WAMP but it still shows in Application->wine->programs->accesories->WAMP.
I have uninstalled it but still it shows start wamp server option, though it doesnt work.
So even when i just scroll down websites my desktop becomes black for some time.adn my music player also hangs a lot.I use amarock and it stops or hangs with no options working and songs is running in background.
Could you help me out plz?:confused:

---

### Post by ahzadjali on 2008-07-04
Yeh.. i am new to linux switched from windows vista, i too faced the same faith but this was only after updates of apache or some  update which i am not sure. cannot reinstall then had to update again, my laptop delays any application execution, looks like daemon execution delay.... not sure. 

Need some hint how to over come this slowness...

thanks

---

### Post by HermanAB on 2008-07-04
If you don't want to use Apache, then you should not install it, since it is a major resource hog.

'ps -e' will tell you whether the Apache httpd daemon is running.  If so, kill it.

---

### Post by prap19 on 2008-07-04
but i want to work on XAMPP i.e apcache server.i am learning PHP so i need to work on Apache.

---

### Post by shad0w_walker on 2008-07-04
Look into LAMP, AKA Linux Apache MySql and PHP, there is no need to be running all that stuff through wine.

---

