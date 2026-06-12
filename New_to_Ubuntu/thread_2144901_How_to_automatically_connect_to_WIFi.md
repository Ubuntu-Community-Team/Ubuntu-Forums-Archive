---
title: "How to automatically connect to WIFi"
date: 2013-05-13
forum: New to Ubuntu
---

### Post by rootle on 2013-05-13
Hello, I don't know if this thread is in the right place, but I am a caveman in linux so.. I wasn't able to connect to wifi network, because all the time it said wrong key. 
After some tweaking I changed settings to WPA2 instead of WEP, and now I can connect to wifi, but after reboot it does not connect automatically. I have to go to "Connect to hidden wireless network" enter my linux password and only then it connects. Is there any way to connect to wifi automatically after reboot? P.S sorry for bad english

---

### Post by stylintile on 2013-05-13
Hello,
     You didn't say whether you are running Ubuntu or a different flavor, but in 12.04 with gnome fallback if I right click on the network manager icon in the panel, and select "edit connections...", select the wireless tab, select your network, then check the box to connect automatically.

Hope it helps

---

### Post by rootle on 2013-05-13
I am running Lubuntu 12.04 , connect automatically is already checked. The thing is that when I reboot it tries to connect and asks me to enter wifi password, but when I enter password it won't connect, because it thinks that password security (or how it is called) is WEP instead of WPA2.

---

### Post by stylintile on 2013-05-13
I remember I had some problems with that in 10.04, but I cant remember what finally fixed it.  I do remember that I had to disable IPv6, but I don't remember if that's what finally worked.  Hang around and I'm sure someone will come along with a solution.

Good Luck

---

### Post by squakie on 2013-05-13
Here's the thing I've noticed several times myself:  if you initially do something incorrect like a network key, network manager seems to use the saved definition - I.e., the bad one, and use it instead of a correct one.  I've always clicked on network manager, gone to edit, and removed the current definition for my wireless network.  Then when I try to connect the first time it will ask for the password again and it seems to work after that.  If you do delete the connection, be sure to set the always connect parameter again.

---

### Post by rootle on 2013-05-14
I deleted everything and tried again, I entered correct password, but there was no option to select wpa or wep. It just asked me for a password. And after reboot it asks me again, and still it thinks that the password is WEP. I hope you guys understand  what problem do I have

---

