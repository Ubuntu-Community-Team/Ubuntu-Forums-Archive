---
title: "wifi fails to connect"
date: 2012-11-12
forum: New to Ubuntu
---

### Post by nnjond on 2012-11-12
Hi,

My laptop has detected my new router, which is in the same room, and accepted the password on the back of the router. But doesn't establish the connection according to my browser. Instead it periodicly asks for the password.

Any advice please

---

### Post by Yougo on 2012-11-12
hi, first to get the silly questions out of the way:
-have you rebooted your laptop?
-have you reset your router?
-are you absolutely sure you typed the password correctly? no caps-lock? when entering the password, there is a checkbox that let's you show the password as you type.
-how is the signal strenth? do other devices connect ok?
-are there any nearby networks that could interfere?

on your laptop:
-open your network settings by clicking the bottom most item in the network menu. a window opens. go to the tab that says 'wireless' here you can add, edit and delete saved networks. you could try clearing the networks for a fresh start.

in your router:
- do you have acces to your router's settings? if yes, you couyld try a different channel, or a different protocol (WEP/WPA) be sure to do this while connected with a wire, as the wireless signal will be changed and you will lose connection (in case you used another device)

if none of the above worked, you may have a driver problem. for that, we need more info about:
- your ubuntu version. 
- your hardware, 
- your wireless card.

to get info on your wireless card, open a terminal and type:
```
sudo lshw -c network
```
give your password when prompted (you won't see the typing, but it's there, press enter when done)

copy and paste the resulting lines here.

---

### Post by nnjond on 2012-11-12
Solved. misspelt pswd.  Thanks alot

---

