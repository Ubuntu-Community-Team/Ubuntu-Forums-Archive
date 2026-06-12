---
title: "Microsoft Dynamics issue"
date: 2012-08-22
forum: New to Ubuntu
---

### Post by Stephenkboyer on 2012-08-22
Hello, I am put Ubuntu 12.04 on my Dell Latitude E6520 laptop and I am having two different issues.
 
1) I cannot connect using the Dell Wireless 5630 EVDO-HSPA Mobile Mini-Card Modem. I actually downloaded the copy of Ubuntu 12 from the Dell website so its supposed to have all the right drivers. Everything seems to work but I cannot get connected. I checked to see how it was set up in Win7 and made sure it was set up the same way. It is a company furnished laptop and I don't have the Verizon account info but the username and p/w for network connection are blank and it's supposed to be set to DHCP. Is there a way I can use mimic the network connection from the Win7 site of the laptop.
 
2) I need to be able to access Microsoft Dynamic CRM for my job. When I try to sign into the server it says I have to have IE7 or better and that my browser isn't supported. I was told to try installing PlayonLinux and download IE8. I did that and Im able to run IE8 but when I try loging into the server with my credentials it keeps me an 401 error. I guess my question is can I fix this issue in wine or is there a way I can fake IE7 or better using Firefox, Chrome or something els?
 
Thanks for any help
Stephen

---

### Post by Lisiano on 2012-08-22
[LIST=1]
[*]There was some sort of software that could snif out the information used to connect, but could you tell me how exactly does it connect? PPTP?
[*]You can use a useragent spoofer, [here is one for Chrome]("https://chrome.google.com/webstore/detail/djflhoibgkdhkhhcedjiklpkjnoahfmg"), you can find one for Firefox using it's own plugin search
[/LIST]

---

### Post by Stephenkboyer on 2012-08-22
It says shows that I'm connected through PPP.

---

### Post by Lisiano on 2012-08-22
Try using this utility [http://www.nirsoft.net/utils/dialupass.html](http://www.nirsoft.net/utils/dialupass.html)
Once you open it in Windows with Admin rights, you will see a dump of all network credentials. I am not sure if this is the tool you want. Oh and a side note. If you have an antivirus then it might get tripped, but I can assure you that there is nothing malicious in the tool, the antivirus will trip only because the tool is able to display this information.

---

