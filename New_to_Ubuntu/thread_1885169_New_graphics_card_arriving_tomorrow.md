---
title: "New graphics card arriving tomorrow"
date: 2011-11-22
forum: New to Ubuntu
---

### Post by Invasion on 2011-11-22
Hi, I have just made the jump to Ubuntu 11.10 from windows XP. My system is about 7 years old and as my new monitor has DVI I wanted to replace my graphics card which doesn't have DVI, with one that supports this connection. 

So today I have ordered a: 
**[SIZE=2]Nvidia GeForce GT 430 1024MB GDDR3 PCI-Express Graphics Card[/SIZE]**

Now I am concerned I am going to have troubles with this card? I was also thinking would it be easier to install the new card the reinstall Ubuntu 11.10 as I have everything backed up anyhow and it wouldn't take long to do ?


Any help on this would be really appreciated :)

Not sure if I posted this in correct section..please move if I haven't and accept my apologies ;)

---

### Post by lechien73 on 2011-11-22
Hi & welcome to the forums,

From what I understand, the NVidia card should work ok. You can install the restricted driver by going to System Settings -> Additional Drivers.

A fresh re-install is always good, so if you're happy to do that, then it would work too. The HDMI port on my NVidia card worked out of the box, so hopefully the DVI will too :)

---

### Post by BC59 on 2011-11-22
Your card is a lot younger than your computer, so sometimes there are compatibility problems, especially if your computer is not supporting the technology GDDR3.
You should ask your retailer about this.

About the second part of the question I think that is a good idea to uninstall the proprietary video card drivers you have and then try to put the card and boot.

Then you can search how to install the best drivers for your card.

---

### Post by JayKay3OOO on 2011-11-22
[http://ubuntuforums.org/showthread.php?t=1715911](http://ubuntuforums.org/showthread.php?t=1715911)

3rd post.

:P

---

### Post by oldfred on 2011-11-22
My system is 6 years old. I originally had a nVidia 7600 and 2 years ago I updated to a 9600GT. I also updated power supply to make sure I had enough power. I had no issues as both were nVidia.

If previous video was not using nvdia-current then on first boot you may need nomodeset.

Natty Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 
then
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

---

### Post by lolpenguin on 2011-11-23
Hey cool same card as me!:)
As mentioned before, your PC is a bit old some some compatability issues may occur. What motherboard and processor are you using?
EDIT: If compatability is not an issue then the card works fine.

---

### Post by Invasion on 2011-11-23
Thanks for the warm welcome and all the help really appreciated ;)


lolpenguin:My mother board is a ECS 945P-M3.
The processor is:Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz

On the motherboard side of things I can find the exact model listed on the ECS website I guess they made a batch of OEM boards  for Phillips Freevents MT1800 -that is what my system was when new- although the one listed on the site looks Identical from what I can make out. [http://www.ecs.com.tw/ECSWebSite/Product/Product_Detail.aspx?CategoryID=1&DetailID=680&DetailName=Feature&MenuID=1&LanID=0](http://www.ecs.com.tw/ECSWebSite/Product/Product_Detail.aspx?CategoryID=1&DetailID=680&DetailName=Feature&MenuID=1&LanID=0)

Just tracked my order and it will be with me within the next hour... lets hope compatibility isn't an issue..one things for sure I will soon find out!

---

### Post by Invasion on 2011-11-23
Well I am pleased to say..... no problems at all :) I installed the graphics card. Then did a fresh install, and everything is working fine..and I cant tell you what a relief that is lol 

Thanks again for the input on this really appreciated 
;)

---

### Post by wolfen69 on 2011-11-23
I'm using that exact same card, and it works great with the nvidia driver. Enjoy!

---

### Post by Invasion on 2011-11-23
> **wolfen69 said:**
> I'm using that exact same card, and it works great with the nvidia driver. Enjoy!
Yeah I am really pleased....as I said I really  thought I was going to have loads of trouble.
I just noticed under additional drivers that Im using:
 NVIDIA accelerated graphics drivers (version current)[recommended]

also listed is:


Nvidia accelerated graphics drivers (post release updates) (version current-updates)

Should I switch to this or just stay with the one running? 

Thanks :)

---

