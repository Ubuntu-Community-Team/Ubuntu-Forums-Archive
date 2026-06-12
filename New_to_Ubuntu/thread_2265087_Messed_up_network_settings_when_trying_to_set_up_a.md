---
title: "Messed up network settings when trying to set up a domain"
date: 2015-02-12
forum: New to Ubuntu
---

### Post by Rodrigo_Duarte on 2015-02-12
At work, we have a large network where you don't really need to login to use the internet, but then you won't also have access to printers and file sharing. So, when I first installed Ubuntu, all worked fine without any extra setting!


But.. as I am transitioning to Ubuntu, I tried inserting my Ubuntu into the domain so I could use our shared printer, but I definitely did something wrong, and now not even the internet is working. I remember of changing the /etc/hosts file. Where it's normally "127.0.0.1     localhost", I stupidly tried changing it to "127.0.0.1      mydomainaddress.ac.uk" ), and obviously it didnt work. So I wrote back just "127.0.0.1    localhost". And my internet is still not working!

I tried googling a way of reset all network settings to default but none worked. I tried:


sudo iptables -F
sudo ifdown eth0 && sudo ifup eth0
sudo service network-manager restart
dmesg | grep -e ath -e wlan

I know they're very random but I have been trying everything to have internet back on my Ubuntu and it's just impossible.

---

### Post by newbie-user on 2015-02-13
What exactly do you mean by "inserting my Ubuntu into the domain"? Are you talking about an active directory domain? DNS domain? Maybe just a vlan?

My first guess is that you got put on an untrusted vlan, which is why you don't have access to file sharing and printers.

---

