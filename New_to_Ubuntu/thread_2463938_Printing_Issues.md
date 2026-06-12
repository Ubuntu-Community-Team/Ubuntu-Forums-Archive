---
title: "Printing Issues"
date: 2021-06-21
forum: New to Ubuntu
---

### Post by jackdusty on 2021-06-21
[FONT=Verdana]Hi[/FONT][FONT=Verdana]

As you might have seen my previous posting you will realise I am an experienced IT Technician but with absolutely no experience of Linux in any shape or flavour. I have a questions about printing please, I have a Canon laser printer that is connected by a network and has an IP address.
When I add the printer by IP address it downloads the drivers and installs them for me - so far so good - just like Windows does.
When I try sending a print to the print it sys "Printer Not Started" it also states I can only print test only documents.

Help please

Thanks


Jack[/FONT]

---

### Post by kurt18947 on 2021-06-21
Hello Jack

I'm certainly no expert but have a couple thoughts. First I would see if I had the app "system-config-printer" installed. If not, I'd install it from the repository. Launch it and see if it tells you anything interesting such as making sure the printer is enabled. Second, I would probably install the drivers from Canon. My experience with the drivers installed automatically is that sometimes they work and sometimes they don't, at least not as well as I expect. Linux uses something called CUPS which is quite powerful but I am not at all familiar with it. Here are Canon's Linux drivers:

[https://www.usa.canon.com/internet/portal/us/home/support/details/printers/small-office-home-office-printers/mb2720?tab=drivers_downloads](https://www.usa.canon.com/internet/portal/us/home/support/details/printers/small-office-home-office-printers/mb2720?tab=drivers_downloads)

Not all Canon printers have Linux support, you'll want to check by model if you use that method. I used a model I've looked at in the past.

---

