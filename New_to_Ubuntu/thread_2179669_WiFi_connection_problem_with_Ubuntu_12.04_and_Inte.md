---
title: "WiFi connection problem with Ubuntu 12.04 and Intel (R) Centrino (R) Advanced-N 6235"
date: 2013-10-09
forum: New to Ubuntu
---

### Post by Daniel_Ocando on 2013-10-09
Hello and Greetings to everyone at the Ubuntu Community,

I am an absolute beginner to Ubuntu and the Linux environment. I recently installed **Ubuntu 12.04.3** LTS alongside Windows 8 in my **Samsung 550P5C** (5.7GiB, Intel Core i5-3210M CPU @ 2.50GHzx4, 64-Bit). I could connect to the internet using a wireless connection perfectly the first few days. But now, even though I can connect to any wireless network, the Internet won't work (even though it works perfectly fine on Windows 8).

I have an Intel (R) Centrino (R) Advanced-N 6235 as my wireless driver.

I tried to re-install the drivers as shown in the following webpage: [http://wireless.kernel.org/en/users/Drivers/iwlwifi](http://wireless.kernel.org/en/users/Drivers/iwlwifi)
But sadly it still won't work.

I'd really appreciate some help!

Thanks in advance.

---

### Post by adithya2 on 2013-10-09
Try using this command in the terminal.Open terminal by using the shortcut Ctrl+Alt+T.
> rfkill list all
This command will show the status of the wireless and bluetooth drivers in Ubuntu.Post the terminal output in the forum.
Try also installing this software via the Command Line:
> sudo apt-get install nmcli
This will install the application to know about network connections and they can be controlled using CLI.(nmcli :Network Manager Command Line Interface).
This will not solve your problem but will give you a headstart  in diagnosing the problem.

---

### Post by Daniel_Ocando on 2013-10-09
Hello and thanks for the support! 

The first command you told me throwed me the next result:

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

Which I supposed says that everything is ok! But I couldn't install the application you suggested, the terminal throws me the next message:

XXXX sudo apt-get install nmcli
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package nmcli

What should I do next?

---

### Post by Daniel_Ocando on 2013-10-10
Ok. At the end of the day it was not a driver problem. But it was rather a DNS problem. I put my DNS server manually using the Network Settings, turned the Wi-Fi connection ON and OFF, played with it a little while until eventually an Internal Error Message from Ubuntu appeared and after I sent the error report the Wi-Fi went back to normal.

---

