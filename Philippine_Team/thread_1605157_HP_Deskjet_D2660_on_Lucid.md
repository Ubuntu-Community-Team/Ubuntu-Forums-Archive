---
title: "HP Deskjet D2660 on Lucid"
date: 2010-10-24
forum: Philippine Team
---

### Post by Jechem on 2010-10-24
Hello,

I just bought an HP Deskjet D2660 printer. I've successfully installed it but the printout is different. When you use it to print colored pages it prints the black ones in brown color but if you choose grayscale mode it prints it in black color. It seems that it's not using the black cartridge when choosing the normal color mode. I've contacted the HP Customer Care and informed them of my problem and they replied "**I would like to bring it to your kind attention that, HP does not provide drivers for Ubuntu Operating System. There are no HP drivers for Ubuntu 10.04 Operating System. So, I would request you to contact Ubuntu Support regarding this.**" I told them I got the driver from HPLIP their official website! but this is their reply "**I would like to inform that, though the driver is an HP-developed solution, HP does not provide formal consumer or commercial support for this software.**" So why develop a software if you won't support it?

If anyone has any experience regarding this printer any advise would be greatly appreciated.

Thanks

---

### Post by aljoriz on 2010-10-25
here's your answer

go to the terminal

type: sudo apt-get install hplip-cups
enter your password

pag tapos na hanapin mo yung Printing icon either sa preference of sa administration.  Once clicked makikita mo yung printer mo (make sure to plug the printer) 

then right click on the HP icon.. properties under settings look for "Make and model" beside click the CHANGE icon.. 

press forward and look for the HPLIP-CUPS driver.  
 

YES, you are correct that the grayscale settings does not actually print grayscale but black. Once you have installed HLIP-CUPS you should be able to print the correct colors.  I own an HP D2660 also

---

### Post by Morgonte on 2010-10-25
> **aljoriz said:**
> 

pag tapos na hanapin mo yung Printing icon either sa preference of sa administration.  Once clicked makikita mo yung printer mo (make sure to plug the printer) 


:confused::confused::confused:

---

### Post by Jechem on 2010-10-26
aljoriz,

Thanks for your reply.

I've done that already a couple of times since last week but the printout is still not black when choosing normal color instead it prints the supposedly black letters in brownish black. The black print when in grayscale is really black but in normal color mode its a mix of the colors which makes it brown. I'm using hplip-cups 3.10.2. What version do you have installed that worked with your D2660? I've tried 3.9.10, 3.10.6 and 3.10.9 based on other answers from launchpad but all the same outcome. I've even tried it on Maverick but to no avail.

---

### Post by aljoriz on 2010-10-26
> **Morgonte said:**
> :confused::confused::confused:

preference OR sa admin pala yan

@thread starter im using hplip-cups 3.10.2 as the driver.  Using peppermint here based on Ubuntu 10.4 LTS code.

Try removing the color cartridge to see if it will give you brown.  I know its a pain but that's an easy work around.  BTW the HP drivers though comes directly from HP does not have a warranty, they are received "AS IS".  It's a standard on the opensource world.

---

### Post by Jechem on 2010-10-26
> **aljoriz said:**
> 

Try removing the color cartridge to see if it will give you brown.  I know its a pain but that's an easy work around.  BTW the HP drivers though comes directly from HP does not have a warranty, they are received "AS IS".  It's a standard on the opensource world.

I've tried that also but it doesn't print anything with only the black cartridge. I can print grayscale with only the black cartridge attached.

I've posted on launchpad also but it's been a week and there has been no reply so maybe I'm just the one experiencing this.:(

I think I'll just have to live with having brown letters instead.:mad:

Thanks anyway. I'll update if ever I find a solution to my problem.:wink::wink:

---

### Post by aljoriz on 2010-10-27
normal color settings combines the colors to make black.. which sounds reasonable but seeing you can print grayscale with black cart only parang ok na.  

Let us hope the next LTS will address this issue.

---

### Post by Jechem on 2010-10-27
I'll have to live with the brown "murag kabao nga na ughan ug lapuk" print.:lolflag: Its better than having no printout at all. 

Hopefully they will fix it in the next updates.

Anyways, salamat sa imong mga ideas.:P

---

### Post by Zaplux on 2011-02-04
Hello Jechem,

i have the same problem with my HP OfficeJet under Ubuntu 10.04.

Is your problem with your HP been resolved?

Thanks

Zaplux

---

### Post by Jechem on 2011-02-04
> **Zaplux said:**
> Hello Jechem,

i have the same problem with my HP OfficeJet under Ubuntu 10.04.

Is your problem with your HP been resolved?

Thanks

Zaplux

Zaplux,

The printout is still the same. It has not changed with the recent HPLIP and CUPS updates. There even isn't any reply from the HPLIP-Launchpad team regarding this problem. I think this problem only happens to a few people and it's not worth the time to make major changes to the program.:(

---

### Post by angheloko on 2011-02-08
Hi Jechem, strange... have you confirmed that it's not the printer itself? Na try mo na install sa ibang OS? From the site itself, kasama Linux sa compatible OS.

I think you should raise or escalate the issue, hindi lang sa launchpad team but especially sa HP customer service. It's not right to say something then not back it up... :-/

---

### Post by Jechem on 2011-02-08
> **Jechem said:**
> I've contacted the HP Customer Care and informed them of my problem and they replied "**I would like to bring it to your kind attention that, HP does not provide drivers for Ubuntu Operating System. There are no HP drivers for Ubuntu 10.04 Operating System. So, I would request you to contact Ubuntu Support regarding this.**" I told them I got the driver from HPLIP their official website! but this is their reply "**I would like to inform that, though the driver is an HP-developed solution, HP does not provide formal consumer or commercial support for this software.**"

angheloko,
I've contacted HP regarding this and their reply as quoted. This has been tried under Windows7 and it works fine.I've tried HPLIP-launchpad team because that is where they develop the drivers but to no avail. It's just one incident not worth looking into.

---

