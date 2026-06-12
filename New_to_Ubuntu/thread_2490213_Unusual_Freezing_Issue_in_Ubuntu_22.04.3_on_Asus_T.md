---
title: "Unusual Freezing Issue in Ubuntu 22.04.3 on Asus TUF Gaming Laptop with Nvidia GTX 16"
date: 2023-08-26
forum: New to Ubuntu
---

### Post by gianlucamirci on 2023-08-26
Hello everyone,


I'm facing an odd problem with my Ubuntu 22.04.3 installation on my 2020 Asus TUF Gaming laptop, equipped with a 10th generation Intel Core CPU and an Nvidia GTX 1650 graphics card.


The issue is that my system seems to freeze briefly every 23-24 seconds. Everything becomes unresponsive for a short moment and then continues normally. This happens consistently and doesn't appear to be tied to any specific application I'm using.


I've tried seeking online help but so far haven't found a solution. I've monitored the system monitor and didn't notice any unusual spikes in system resources during these freeze moments.


Here are some steps I've already taken:


I've ensured that I have the latest Nvidia drivers installed via "Software and Updates."
I've checked the power management settings and didn't find anything out of the ordinary.
My system doesn't appear to be overheating, and the cooling is functioning normally.
I'm using the latest stable kernel for Ubuntu 22.04.3.
I'm not very familiar with log files and how to interpret them, so I haven't looked into /var/log files.


Has anyone else experienced a similar issue or has any insight into what might be causing this? Any suggestions to resolve this problem would be greatly appreciated.


Thank you for your assistance!


Best regards,
Luca

---

### Post by oldfred on 2023-08-26
My old laptop with only 1.5GB of RAM would go gray for a bit when it was using swap as hard drive was very slow.

I am sure your system has plenty of RAM.
But check RAM & swap use with this when it does freeze.
[I]free -hm

[/I]You can check log files
sudo grep -Ei 'warn|error' /var/log/*g
I still get a page of output, some commands have "error" in the name, and many warnings are not critical.

---

