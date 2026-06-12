---
title: "Lubuntu wire internet connection , ethernet , PPPoe problem solved"
date: 2021-08-20
forum: New to Ubuntu
---

### Post by ioanis on 2021-08-20
Hello
I have installed Lubuntu and i had a problem with wire internet connection that i have sollved :

From right bellow push Network pictogram / Edit connections - should appear a window with "Ethernet - Wired connection 1 ) / push + button to make a new connection / chose DSL/PPPoe  / Appear a Window with more tabs / at General tab check both options Automatically connect...  and  All users may connect / at DSL/PPPoe tab at Parent interface chose enp5s0 , than fill your Username and Password from  your internet provider / at Proxy tab at Method chose Automatic / push Save button from bottom . 
 
If still doesn't work , look at Wired connection , at IPV4 Settings tab note address , netmask and Gateway (Address :something like 121.0.1.7 , netmask : something like 23 , Gateway : something like 121.0.1.4 ) .
Reinstall Lubuntu from USB , at some point (in my case) appeared something like "Could not make DHCP settings " , than you have the option to make DHCP settings manually , chose that , it will ask address , netmask and gateway , fill the data that you have noted . If after install appears another ** Ethernet**  connection besides "Wired Connection"  (something with -enp5s0 ) just delete it (select and push - button) .[B] Don't delete Wired connection or DSL/PPoe connection . 
[/B]If you don't have DSL/PPPoe - make one with the steps mentioned above .Hope to help you [B].
[/B]All the best

---

### Post by ioanis on 2021-08-21
Every time i connect appears a new connection in Network Connection - Ethernet (something like ....enp5s0 besides Wired internet) My Solution is to delete this ...enp5s0 connections that was made by Linux . 
But still i didn't had internet.
My solution wich now worked : in Proxy (Netwok connection / DSL PPPOE - DSL connection 1 / Proxy ) choose at Method : None . In my post above i said to  choose  Automatic , but i guess was wrong . So choose NONE . 
Worked for me .
All the best

---

