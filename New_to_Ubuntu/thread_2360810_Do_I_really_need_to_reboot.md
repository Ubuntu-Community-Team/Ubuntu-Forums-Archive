---
title: "Do I really need to reboot?"
date: 2017-05-08
forum: New to Ubuntu
---

### Post by Tadaen_Sylvermane on 2017-05-08
I reboot to much. My uptimes on my server and laptop are almost comical, especially when factored against *nix / bsd legendary uptimes I've read about. I reboot after almost every update and I want to stop that. I want to get some good uptimes just because, no other reason. That and my server has become somewhat critical to my lan at home and a fair number of people are reliant on it for the internet and what not.

My question stems from the "System reboot required" message when I ssh into my server. Do I need to reboot for regular updates or only kernel updates? Does everything other than kernel updates update then restart their services during the update and I can leave it alone?

---

### Post by wildmanne39 on 2017-05-08
You do not have to restart your computer every time you update.

However some updates like for the kernel and other system update yes, however I found an application called ksplice that allows you to never reboot.
> Free Community Protection for Ubuntu Desktop and Fedora

Servers aren't the only systems needing protection. Oracle has made the kernel protections from Oracle Ksplice available for free to members of the Linux community for their desktop installations of Ubuntu and Fedora. Find out first hand the benefits of being protected by Oracle Ksplice.


[http://www.ksplice.com/](http://www.ksplice.com/)

---

### Post by exhile on 2017-05-08
Ubuntu 16.04 server can Livepatch without rebooting.


[https://www.ubuntu.com/server/livepatch]("https://www.ubuntu.com/server/livepatch")

---

### Post by poorguy on 2017-05-09
I've always reboot every time after updates although most things I've read says Linux doesn't require rebooting every time after updates.

In my case as with most one of those left over habits when Windows was the OS that was being used.

---

### Post by sp40140 on 2017-05-09
Few things: 
"legendary uptime" systems have dedicated System Admins looking after it (almost full time). Also, the initial os configuration, the quality of software running on it and patching schedules all need to be looked at.
As stable as Unix / linux systems are, it is generally good practice to reboot the system regularly. But on your own schedule. 
To do that, you can disable auto-update and perform updates / reboot may be once a month (just example) and re-boot at that time.
I have 20 years of exp in Financial industry, and one of the practices is that at least once a month, system admins get a weekend with servers to perform health check and patching and reboots. May be some (most) machines don't need to be, but it's like preventive care.

Now, if you just want long uptime for bragging rights (and there is nothing wrong with it), go for it. Disabling the auto-updates will help a lot with it. But might deprive your system of important security patches.

Along with kernel updates, there are other parts of the os which require reboot like init/systemd.
You just need to make informed decision based on your needs.

---

### Post by Tadaen_Sylvermane on 2017-05-09
Probably make a 4 week or monthly schedule. It isn't under heavy load but still want to keep it updated with the kernels and such. Thank you all for input.

---

### Post by mastablasta on 2017-05-10
the problem is with servers connected to internet. you have to patch them (and if you really need /want the uptime as mentioned use live patching). LAN servers are not that  much of an issue since there is no port open to them from outside. for example my RPi has Openelec on it. i update it every year or so when i have the time. i mean it is just playing media files (ok an donwloads database info, but can't do much more than that). 

but if they are serving the internet (have ports open) then it can be an issue.

i once got hacked on server 4 or 5 days after the vulnerability was known. i simly did the updates on weekend sometimes bi-weekly. by the time i got to patch the service, the server was already spamming others by email.

then it was a delete&restore session from a year old backup. tought me the value of good backups (though to be honest i though host had them) and timely patching.

---

