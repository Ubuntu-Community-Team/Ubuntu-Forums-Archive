---
title: "connecting multiple USB 3G modem from command line."
date: 2012-08-03
forum: New to Ubuntu
---

### Post by hugsnkisses on 2012-08-03
I am trying to connect multiple USB 3G modem (two, in my  case) in Ubuntu 12.04. 



I can do it graphically through  the Network Manager, but I'd like to replicate the process through the  command line.
  Here is the process that I am trying to emulate.
  
[LIST=1]
[*]Connect two 3G dongles, both huawei, Model No: E173Bu-1 (Service  provider: Airtel) and Model No: E173u-1(Service Provider: MTNL).
[*]The connections that I configured shouldn't have "connect automatically" checked in the Network Manager GUI.
[*]Now, from the Network Manager GUI, I am able to connect to both of them manually one after the other.
[*]I could see ppp0 and ppp1 connections established when I run ifconfig and also the routing table populated appropriately.
[/LIST]
  So far, so good.


I want to replicate the same scenario (without using the GUI) from the command line. 
(I need to write a script that does the exact samething.)

 I have tried the following:  

1. Connect two 3G dongles, both huawei, Model No: E173Bu-1(Service provider: Airtel) and Model No: E173u-1(Service Provider: MTNL). 
2. The connections that i configured shudn't have "connect automatically" checked in the Network Manager GUI. 
3. From the command line i tried the following command: nmcli con up id "Airtel"         

It gave the following error:  
$ nmcli con up id "Airtel"
 Active connection state: activating 
Active connection path: /org/freedesktop/NetworkManager/ActiveConnection/2 
state: unknown 
Error: Connection activation failed.

 I tried it again, and got this error:
  $ nmcli con up id "Airtel"[INDENT]   ** (process:3184): WARNING **: Could not initialize  NMActiveConnection /org/freedesktop/NetworkManager/ActiveConnection/3:  Method "GetAll"   with signature "s" on interface "org.freedesktop.DBus.Properties"   doesn't exist
      
Active connection state: unknown Active connection path:   /org/freedesktop/NetworkManager/ActiveConnection/3
      
** (process:3184): WARNING **: Could not create object for /org/freedesktop/NetworkManager/ActiveConnection/3: Method "GetAll"   with signature "s" on interface "org.freedesktop.DBus.Properties"   doesn't exist
 [/INDENT]The exact same thing happens if I try the same for the connection "MTNL."
    
P.S.
The first time I try gives the decent looking first error. i.e.,
  
$ nmcli con up id "Airtel"
 Active connection state: activating 
Active connection path: /org/freedesktop/NetworkManager/ActiveConnection/2 
state: unknown 
Error: Connection activation failed.

and on successive tries i keep getting the wierd looking error. i.e.,
  
$ nmcli con up id "Airtel"[INDENT]   ** (process:3184): WARNING **:  Could not initialize  NMActiveConnection  /org/freedesktop/NetworkManager/ActiveConnection/3:  Method "GetAll"    with signature "s" on interface "org.freedesktop.DBus.Properties"    doesn't exist
      
Active connection state: unknown Active connection path:   /org/freedesktop/NetworkManager/ActiveConnection/3
      
** (process:3184): WARNING **: Could not create object for  /org/freedesktop/NetworkManager/ActiveConnection/3: Method "GetAll"    with signature "s" on interface "org.freedesktop.DBus.Properties"    doesn't exist
 [/INDENT]I am using Ubuntu 12.04 on an Asus Eee PC seashell series notebook. (I only need a solution for this configuration only).

---

### Post by hugsnkisses on 2012-08-03
FYI,

nmcli works perfectly fine when there is only one 3G modem connected.

---

