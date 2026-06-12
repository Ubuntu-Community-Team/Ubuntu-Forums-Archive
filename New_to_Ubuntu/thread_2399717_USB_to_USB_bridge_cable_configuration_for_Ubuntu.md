---
title: "USB to USB bridge cable configuration for Ubuntu"
date: 2018-08-29
forum: New to Ubuntu
---

### Post by ashutoshmehta55 on 2018-08-29
Windows is ahead of Ubuntu to have 2 pc's or laptops connected together by USB to USB cable for data transfer. What is stand from Linux on this front?

---

### Post by wildmanne39 on 2018-08-29
Are you making a statement or asking a question? if you are asking a question can you please clarify what you want to know?

Thanks

---

### Post by ashutoshmehta55 on 2018-08-29
Asking question! I am using Ubuntu and want to do transfer data using USB-USB cable between 2 laptops.

Thanks

---

### Post by Holger_Gehrke on 2018-08-29
Let me ask the duck about "usb bridge cable ubuntu" ...

This gives me one hit right [here]("https://ubuntuforums.org/showthread.php?t=1166375") on this forum back from the days when this was current tech (2008), and that links to [this page]("http://www.linux-usb.org/usbnet/") about the usbnet kernel driver. Back then most computers didn't have gigabit Ethernet, so USB 2.0 with its speed of 480 mbs seemed like a good alternative. Nowadays most computers do have gigabit Ethernet onboard, so a short network cable is probably a better alternative.

Holger

---

### Post by dmccracken on 2019-03-05
There are several scenarios in which a USB bridge might be useful. Many devices have a USB port but not an Ethernet port. My situation, which brought me to this discussion, is that I have Windows and Linux computers on a local Ethernet with addresses assigned by the DHCP router in my WAN modem. All of the computers can communicate locally via Samba as well as remotely through the modem using the DHCP addresses but only if they join the Windows network before attaching to the WAN. This can only be done by disconnecting the WAN and rebooting all computers. Then the WAN can be reconnected. This is a lot to go through just to transfer a few files. Unfortunately, I haven't found an answer. The two links suggested by Holger_Gehrke don't provide clear guidance for anything but a USB-Ethernet adapter, which is not a bridge cable.

---

### Post by jdeca57 on 2019-03-05
> **dmccracken said:**
> There are several scenarios in which a USB bridge might be useful. Many devices have a USB port but not an Ethernet port..
True, but most of these devices connect via WiFi. A computer with only an usb connector that's like a usb stick?

> **dmccracken said:**
> My situation, which brought me to this discussion, is that I have Windows and Linux computers on a local Ethernet with addresses assigned by the DHCP router in my WAN modem. All of the computers can communicate locally via Samba as well as remotely through the modem using the DHCP addresses but only if they join the Windows network before attaching to the WAN.
So you can share data with Samba. The question that remains is what the problem is. No Samba under Ubuntu? Why do you need an usb connector between PC's?

---

### Post by #&amp;thj^% on 2019-03-05
I have personally seen this one work; [https://www.usbgear.com/link/](https://www.usbgear.com/link/)
To be clear the 2 laptops had Arch installed. (That said it should work also with most newer Linux Systems)
And I also agree with the others>>>share data with Samba

@ dmccracken To my knowledge he did nothing special, but hook the USB 2.0 link Cable that i showed in the link to both machines.
This may help also: [http://www.linux-usb.org/usbnet/#t-host](http://www.linux-usb.org/usbnet/#t-host)
him610 has a nice set-up option in post#10
Sorry to hear about the SAMBA problems.

---

### Post by him610 on 2019-03-05
Takes me back to the days (pre-USB) when I used a null modem serial (RS-232) cable to move data from one machine to another. I'm glad we have affordable network capabilities now.

---

### Post by dmccracken on 2019-03-07
To 1fallen. Thanks for the link but it only talks about Windows. If you could be more specific about how it applies to Arch it might be more useful. Regarding the issue of Samba, perhaps I was not clear in my original post. The problem is that, when the WAN is connected, the DHCP-WAN router assigns IP addresses that don't work with Samba. Only by disconnecting the WAN and rebooting all of the computers does Samba work. You might think that using ftp to the assigned IP addresses would solve the problem but the firewall blocks this and there isn't a simple solution because addresses assigned by the router are not predictable. I suspect that there is an Ethernet solution but a USB bridge might be easier. I didn't want to high-jack ashutoshmehta55's question but only to point out that alternatives may not really answer the question.

---

### Post by him610 on 2019-03-08
Problem: Need to move data between 2 computers, each with only USB connectors
Proposed Solution
Parts:
2 each USB to RJ45 adapter [https://www.amazon.com/Cable-Matters-Ethernet-Adapter-Supporting/dp/B00ET4KHJ2]("https://www.amazon.com/Cable-Matters-Ethernet-Adapter-Supporting/dp/B00ET4KHJ2")
1 each Cat5 internet crossover cable terminated with RJ45 connectors [https://www.belkin.com/us/p/P-A3X126/]("https://www.belkin.com/us/p/P-A3X126/")
Procedure:
Connect 1 each adapter, USB to RJ45, to a USB port on each of the computers
Connect Cat5 internet crossover cable to each of the USB to RJ45 connectors
Set up and configure a peer-to-peer network between the two computers

---

