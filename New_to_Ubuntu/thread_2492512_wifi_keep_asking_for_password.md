---
title: "wifi keep asking for password"
date: 2023-11-13
forum: New to Ubuntu
---

### Post by rifqilubis on 2023-11-13
So when im in my home1, it automatically connect. but when im in home2, its asked me to input password everytime.
what can i do to prevent  that from happening?

its should automatically saved in my pc. its working on windows. but on linux kubuntu. i don't know.

---

### Post by yancek on 2023-11-14
What do you mean by 'home1' and 'home2'?  A standard Linux system will have 1 /home directory and at least 1 user sub-directory so explain what you mean.

---

### Post by SeijiSensei on 2023-11-14
I think he is referring to two different physical locations.

Do you have the KDE Wallet enabled? It will encrypt and store passwords. 

I actually don't use Wallet. Instead I enter the password in System Settings > Connections > WiFi Security.

---

### Post by yancek on 2023-11-14
By home1 and home2 are you referring to 2 separate physical locations with different wifi connections?  Are you using Kubuntu installed to a hard drive on a laptop and if so, which version/release?  Different wifi connection information is stored in the directory /etc/NetworkManager/system-connections.  There should be a file for each connection you have used.  That's where they are on my Ubuntu, I don't know if Kubuntu has it.  If you are in range of a wifi connection, you should see it under System Settings/Wi-Fi.

---

### Post by rifqilubis on 2023-11-19
so for late reply. so live in 2 house.

first house (A), it will auto connect, but second house (B). It keep me asking for password, everytime i try to connect to wifi.

---

### Post by MAFoElffen on 2023-11-19
> **SeijiSensei said:**
> 
Do you have the KDE Wallet enabled? It will encrypt and store passwords. 

I actually don't use Wallet. Instead I enter the password in System Settings > Connections > WiFi Security.

And the answers to these questions? Did you try these?

---

