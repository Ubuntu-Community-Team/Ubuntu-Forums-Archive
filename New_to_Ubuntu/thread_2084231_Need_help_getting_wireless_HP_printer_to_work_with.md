---
title: "Need help getting wireless HP printer to work with Ubuntu 12.04"
date: 2012-11-14
forum: New to Ubuntu
---

### Post by Punchy71 on 2012-11-14
Hi
  I am currently running Ubuntu 12.04 (which I am new to) on a wireless laptop and was recently given a free printer. It is an HP Deskjet 3050. After much tinkering I have finally gotten it to print out a test page but I can't get it to connect to my computer's wireless home network so I can print from it. What are the steps necessary to get it to connect to my wireless laptop or wireless network router so I can print from it? I haven't got a users manual for it.

Thank you for any help

---

### Post by SysBoot on 2012-11-14
- connect to your printers ad hoc network
- Print a Network Config Page from the front of the printer. Note the printer's IP address.
- Type that IP address into a browser to reveal the printer's internal settings.
- Choose the Networking tab, then Wireless along the left side, then you can configure it to connect to your wireless network :) 
Below it what the adhoc webpage should look like:

---

### Post by Bartender on 2012-11-14
I'm sure the user's manual is available as a .pdf from the HP website

---

### Post by Bucky Ball on 2012-11-14
> **Bartender said:**
> I'm sure the user's manual is available as a .pdf from the HP website

+1. No doubt ... if not there somewhere. 

[http://www.dogpile.com/info.dogpl/search/web?fcoid=417&fcop=topnav&fpid=27&q=HP+Deskjet+3050+users+manual&ql=](http://www.dogpile.com/info.dogpl/search/web?fcoid=417&fcop=topnav&fpid=27&q=HP+Deskjet+3050+users+manual&ql=)

Took a couple of seconds. ;)

---

### Post by Punchy71 on 2012-11-15
Okay, I tried to type in the ip adress in a new browser window and nothing happens, the page simply won't load anything at all.

Then I downloaded the manual and followed the instructions to try to get the printer and router to recognize eachother over wifi and then went to print a test page and wouldn't print anything so I checked Ubuntu task tray printer icon and it shows my printer status as "pending- not connected?".

---

### Post by Bucky Ball on 2012-11-15
Have you tried, in the printing window, 'Add Printer' then 'Network Printer'. You need to give it a minute or two to have a look so be patient. Does your wireless printer pop up there?

---

### Post by quentinl on 2012-11-15
i have the same problem
i have looked through the settings and nothing that i understand

---

### Post by 23senick on 2012-11-15
I've had a couple of HP printers and found this was the best way to connect it. First connect the printer to the router through the printer's setting menu. That way you can specify its IP address. My router works from 168.whatever.01 upwards to .99. By manually setting the printer's address to the highest number it doesn't get changed periodically.  So it will be something like 168.183.2.99.  

Then through the HUD go into "printing," add printer, click on network printer, and in the network host (find) box, type that address (168...). 

Give it a couple of minutes and it should find your printer, then just follow the steps

---

### Post by Bucky Ball on 2012-11-16
> **quentinl said:**
> i have the same problem
i have looked through the settings and nothing that i understand

Are you using *exactly* the same printer?

---

### Post by kurt18947 on 2012-11-16
> **Punchy71 said:**
> Hi
  I am currently running Ubuntu 12.04 (which I am new to) on a wireless laptop and was recently given a free printer. It is an HP Deskjet 3050. After much tinkering I have finally gotten it to print out a test page but I can't get it to connect to my computer's wireless home network so I can print from it. What are the steps necessary to get it to connect to my wireless laptop or wireless network router so I can print from it? I haven't got a users manual for it.

Thank you for any help

Have you installed hplip & hplip-gui from the repositories?  Usually HP is quite simple to install/configure.

---

### Post by El Tito on 2012-11-16
I agree with Kurt. After installing hplip, no more problems printing/scanning with my hp 4500. Maybe for some stuff you have to struggle a little with commands, but nothing complicated. In my particular case, I use the hplip-gui to print and command line to scan.

Good luck.

---

### Post by ldsudduth on 2012-12-13
> **El Tito said:**
> I agree with Kurt. After installing hplip, no more problems printing/scanning with my hp 4500. Maybe for some stuff you have to struggle a little with commands, but nothing complicated. In my particular case, I use the hplip-gui to print and command line to scan.

Good luck.

I just loaded 12.04 on my laptop, replacing Windows 7 with Ubuntu Studio. This was the solution for me with my HP Deskjet 3050. My printer works like a charm.

Thank you Ubuntu Forums!

---

### Post by Bucky Ball on 2012-12-14
[B][I]Thread closed

Reason:[/I][/B] Problem solved a month ago and no need to resurrect thread, even though your thanks are appreciated and glad it worked for you both. HP is well supported now and the Linux community, I would imagine, supports them in turn. HPLip is about all you need for most stuff HP now.

Any further issues, please post a new thread. ;)

PS: @ Punchy71; I have marked the thread as solved. If you are still having the original problem and think it isn't fixed mark thread as 'Unsolved' from 'Thread Tools' at the top right of this page.

---

