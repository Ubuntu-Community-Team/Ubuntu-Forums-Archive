---
title: "Internet works in Ubuntu, but not windows??"
date: 2013-02-06
forum: New to Ubuntu
---

### Post by BTXNick on 2013-02-06
I've had my computer for a little over a year. Since I've had it, I've not been able to connect to my school's WPA2 enterprise WiFi connection OR using an Ethernet cable using windows. However, it does work on every single other WiFi connection I've used. I've also always had Ubuntu dual booted, and just used Ubuntu at school.

Well now I have to have a windows OS for a class in which I have to use Excel 2010 and install another windows only program. No exceptions. The program has to have internet access to work, so this is an issue. I also have to download quizzes and take them in excel in class. So I really need to get WiFi/Internet working. 

I thought it was maybe because I had a crappy wireless card, but then why would it work when in Ubuntu? 

When I use an ethernet cable and WiFi it says the DNS server is not responding. 
This is what I'm basically looking at:
[http://i.imgur.com/jHNYrmH.png?1?3975](http://i.imgur.com/jHNYrmH.png?1?3975)
[http://i.imgur.com/t6BnlSH.png?1](http://i.imgur.com/t6BnlSH.png?1)

I took it to the IT people here at my school a while back and they messed with it for about 2 hours, downloaded some drivers, did an IP renew, and still no dice. They basically had no answer for me. I really need to get this figured out because it is really damn annoying and if I have to buy an entirely new computer I will be furious, and I don't have any money for that at all. 

Any help is appreciated. Also, is there anywhere else you folks think I could ask this question and maybe get some more responses? I know this is a linux forum and this is windows problem, but I'm pretty desperate.

---

### Post by Mark Phelps on 2013-02-06
IF this is Windows 7, you might be able to get some feedback if you post this on a Windows 7 forum -- sevenforums.com -- especially since this is not a dual-boot or Linux problem.

---

### Post by kanikilu on 2013-02-06
[http://www.sevenforums.com/](http://www.sevenforums.com/) :p

Googled your network name (TTUnet) and see that you are at Texas Tech, and looked up instructions from them. Have you followed these instructions to the letter?

[http://www.depts.ttu.edu/ithelpcentral/solutions/wireless/wpa2/windows_7.php](http://www.depts.ttu.edu/ithelpcentral/solutions/wireless/wpa2/windows_7.php)

My work has a very similar WiFi setup using 802.1x enterprise authentication, and sometimes on Windows (and Mac), I have to go in and remove the saved network profile and re-add it using the Control Panel method on the above instructions (scroll down until you see "alternative solution").

On my network, a commonly skipped step is the Protected EAP properties about the server certificate and authorities. Also, not sure if it applies there, but here there is a Windows update that helps some users connect - the needed Trusted Root Certification Authority is not listed until after the update. So, while at home or somewhere you can get online, check for updates.

As for wired network, do you know if your school has any MAC address filtering to restrict who can just come up and plug in? My university did that, and the ethernet adapter had to be registered with them for it to work...

---

### Post by BTXNick on 2013-02-06
> **kanikilu said:**
> [http://www.sevenforums.com/](http://www.sevenforums.com/) :p

Googled your network name (TTUnet) and see that you are at Texas Tech, and looked up instructions from them. Have you followed these instructions to the letter?

[http://www.depts.ttu.edu/ithelpcentral/solutions/wireless/wpa2/windows_7.php](http://www.depts.ttu.edu/ithelpcentral/solutions/wireless/wpa2/windows_7.php)

My work has a very similar WiFi setup using 802.1x enterprise authentication, and sometimes on Windows (and Mac), I have to go in and remove the saved network profile and re-add it using the Control Panel method on the above instructions (scroll down until you see "alternative solution").

On my network, a commonly skipped step is the Protected EAP properties about the server certificate and authorities. Also, not sure if it applies there, but here there is a Windows update that helps some users connect - the needed Trusted Root Certification Authority is not listed until after the update. So, while at home or somewhere you can get online, check for updates.

I've followed those instructions numerous times to the T and no dice. 

> As for wired network, do you know if your school has any MAC address filtering to restrict who can just come up and plug in? My university did that, and the ethernet adapter had to be registered with them for it to work...

I don't think so. Wouldn't that not allow me to connect in Ubuntu as well though? And I can connect easily in Ubuntu.

---

### Post by kanikilu on 2013-02-06
> **BTXNick said:**
> Wouldn't that not allow me to connect in Ubuntu as well though? And I can connect easily in Ubuntu. Right - missed that in the OP. I don't know, sorry...

---

