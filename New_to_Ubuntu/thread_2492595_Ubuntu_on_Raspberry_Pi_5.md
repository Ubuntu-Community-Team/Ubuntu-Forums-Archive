---
title: "Ubuntu on Raspberry Pi 5"
date: 2023-11-16
forum: New to Ubuntu
---

### Post by technodinosaur on 2023-11-16
Hello, 
My goal is to run a full bitcoin node on my Pi 5. I flashed the Ubuntu Server on an nvme drive. Using the terminal on a Mac, (arp -a) I'm able to see the IP address on my network of the Pi. When flashing the latest Ubuntu to the drive I set up a username and hostname and password. 

Using the ssh command in the terminal ssh username@IPaddress I get the message: connect to host @ the ip address and port number: Operation timed out.  

  What did I miss? Any help is appreciated. Thanks

---

### Post by TheFu on 2023-11-16
a) did you install ssh-server?
b) is the firewall open for the ssh connection on both sides?

Just because something is possible, that doesn't make it a good idea.  Running bitcoin mining on a Raspberry pi is almost a joke.  Heck, running bitcoin mining on a powerful x86-64 CPU is almost a joke these days.  People doing mining have 4x$1000 Nvidia GPUs in their rigs.  The days of getting 32 $20 ASICs powered over USB to use for mining are 15 yrs ago.  Every 1.5 yrs, the "work" needed to find a solution for a bitcoin doubles. I'll leave it to you to figure that out.  [https://forums.raspberrypi.com/viewtopic.php?t=30660](https://forums.raspberrypi.com/viewtopic.php?t=30660) has some comments from 2013. It is only more futile these days.

But if this is just a social thing and you don't really expect to ever find a bitcoin, go for it.

---

### Post by technodinosaur on 2023-11-16
> **TheFu said:**
> a) did you install ssh-server?
b) is the firewall open for the ssh connection on both sides?

Just because something is possible, that doesn't make it a good idea.  Running bitcoin mining on a Raspberry pi is almost a joke.  Heck, running bitcoin mining on a powerful x86-64 CPU is almost a joke these days.  People doing mining have 4x$1000 Nvidia GPUs in their rigs.  The days of getting 32 $20 ASICs powered over USB to use for mining are 15 yrs ago.  Every 1.5 yrs, the "work" needed to find a solution for a bitcoin doubles. I'll leave it to you to figure that out.  [https://forums.raspberrypi.com/viewtopic.php?t=30660](https://forums.raspberrypi.com/viewtopic.php?t=30660) has some comments from 2013. It is only more futile these days.

But if this is just a social thing and you don't really expect to ever find a bitcoin, go for it.

Yes, as far as I know ssh is installed and for ssh-server I checked using sudo -l. It returned "All".
I allowed ssh connection when flashing the SSD using Raspberry Pi Imager. I don't have anything blocking incoming connections but I also don't have the Pi specified to allow connecting through the firewall. Should I disconnect the firewall and then try? 


I must not have made myself clear, I want to have a full copy of the blockchain downloaded, I'm not interested in mining in the least.

Thanks for your response.

---

### Post by technodinosaur on 2023-11-17
I've resolved my problem. Started from scratch and learned a bit more.

---

