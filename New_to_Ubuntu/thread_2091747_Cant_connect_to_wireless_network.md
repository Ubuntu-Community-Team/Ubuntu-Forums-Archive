---
title: "Cant connect to wireless network"
date: 2012-12-06
forum: New to Ubuntu
---

### Post by KingB00zeR on 2012-12-06
Hi guys Im rather new to Linux and currently have Ubuntu 10.10 installed on one of my PC's and am experiencing difficulties in connecting to my home wifi network. I recently purchased a [SIZE=2]Realtek 8191SU wifi dongle and after many attemps have finally installed the drivers. For a while I thought the drivers weren't installed until I went to System->Administraion->Additional Drivers and found that the drivers are installed and in use. However when I click the connection at top of screen the wireless connection is saying "disconnected" and there is no networks available. What should I do?[/SIZE]

[SIZE=2]I better add that I can connect via a wired connection, but the PC is located too far from the modem for this to be possible all of the time.[/SIZE]

---

### Post by airplanesimen on 2012-12-06
> **KingB00zeR said:**
> Hi guys Im rather new to Linux and currently have Ubuntu 10.10 installed on one of my PC's and am experiencing difficulties in connecting to my home wifi network. I recently purchased a [SIZE=2]Realtek 8191SU wifi dongle and after many attemps have finally installed the drivers. For a while I thought the drivers weren't installed until I went to System->Administraion->Additional Drivers and found that the drivers are installed and in use. However when I click the connection at top of screen the wireless connection is saying "disconnected" and there is no networks available. What should I do?[/SIZE]

[SIZE=2]I better add that I can connect via a wired connection, but the PC is located too far from the modem for this to be possible all of the time.[/SIZE]
So you are saying that the wifi-dongle doesnt find any networks? Sorry, i guess i am not able to help so much, but could you maybe show the output of (in "terminal" ) 

```
 iwconfig 
```
and
```
ifconfig
```

?

Thanks!

---

### Post by COMECON on 2012-12-06
Try running this on a terminal and paste the output:
```
 lspci | grep -i wifi 
```

Remember to use the CODE tags between the output.

Catbuntu

---

### Post by verzx on 2012-12-06
This worked for one of my friends, he has the same wireless adapter. Good luck :)

[http://us.generation-nt.com/answer/ubuntu-10-04-64-bit-realtek-8191-8192-driver-help-197472891.html](http://us.generation-nt.com/answer/ubuntu-10-04-64-bit-realtek-8191-8192-driver-help-197472891.html)

---

### Post by gandaran on 2012-12-06
> **KingB00zeR said:**
> Hi guys Im rather new to Linux and currently have Ubuntu 10.10 installed on one of my PC's and am experiencing difficulties in connecting to my home wifi network. I recently purchased a [SIZE=2]Realtek 8191SU wifi dongle and after many attemps have finally installed the drivers. For a while I thought the drivers weren't installed until I went to System->Administraion->Additional Drivers and found that the drivers are installed and in use. However when I click the connection at top of screen the wireless connection is saying "disconnected" and there is no networks available. What should I do?[/SIZE]

[SIZE=2]I better add that I can connect via a wired connection, but the PC is located too far from the modem for this to be possible all of the time.[/SIZE]
update Ubuntu to a more recent version and the 8191SU adapter will work out of the box or if still prefer Ubuntu 10.10 there was no need to install the driver, all it needs is create a folder and download the necessary firmware, I have the same adapter (8191SU and 8188SU both use the same driver) and had the same problem on 10.10
this was my thread which helped fix the problem
[http://ubuntuforums.org/showthread.php?t=1667140](http://ubuntuforums.org/showthread.php?t=1667140)

---

