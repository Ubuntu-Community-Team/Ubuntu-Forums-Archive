---
title: "help me get installed on alienware m18x"
date: 2012-01-25
forum: New to Ubuntu
---

### Post by MasterShihoChief on 2012-01-25
I am required by my university class to use some form of linux distro. I used to use ubuntu a long time ago but ran into so many problems that i trashed it and went back to windows 7.

I have a new computer now and was hoping things would work better, but alas nothing works.

I tried running the kubuntu 11.10 installer and tried to use live cd but it crashed udevd on line 117. I was able to get around this using --acpi=off and that would get me at least to the desktop. 

I have premade /2 partitions. an 84gb partition for / and a 16gb(is 2x your memory still the rule of thumb) for a swap.

I tried installing and grub installer crashed and the installation failed. I guess its because there is still no raid 0 support? 

I also have problems with wireless not working. I have a killer wireless n 1103 which is a rebranded atheros. It sees networks but just gives me the middle finger. 

I also cant use any of my function keys, and audio is non existent.

Please help me ubuntu forums, your my only hope T_T

---

### Post by MasterShihoChief on 2012-01-25
so it seems the problem is grub. It herp derps, i tell it to install to the correct raid partition and it goes and instead of the long raid id and the name it goes to sda1. Any ideas to make grub play friendly?

---

### Post by holycow131415 on 2012-01-25
If you are just using it for your class, how about install virtualbox to run ubuntu in a virtual machine? That way you have no driver/grub/other problems. I would also just install xubuntu for a better interface.

[www.virtualbox.org](www.virtualbox.org)

---

### Post by MasterShihoChief on 2012-01-25
I have considered doing that but i would rather have kubuntu installed since i am a compsci major and their making me use it for a reason and i need to learn to use it. I also like kde better than gnome or whatever apple looking thing is in xubuntu. I have tried using windows installers like wubi or w.e its called but they dont install either.

I have tried the following things in this forum thread
[http://ubuntuforums.org/archive/index.php/t-1559762.html](http://ubuntuforums.org/archive/index.php/t-1559762.html)

however when i try mounting the raid it says its mounted or /mnt is busy. Grub also says that /dev/ isnt mounted when i try to install grub to the raid mapper. I have tried updating grub but then it says that no raid is found for <path to raid>/md-0 or dm-0 has no bios or whatever it is i forget(using windows 7 right now).

---

### Post by MasterShihoChief on 2012-01-26
yay! got it installed, grub loads and it sees windows 7 and ubuntu. I used the alternative disc btw.

oh noes.....a black screen with a blinking underscore....

recovery mode go!

Starting load fallback graphics devices -FAIL
then gets stuck after stopping system V run level compatibility.

i can ctrl alt f1 to login from the console but am basically unable to do anything after that. the 580m sli is not detected. it sees nvidia cards but doesnt know what they are. there is no xorg.conf file and it also sees the integrated intel card that is used as part of nvidia optimus. Oh btw function keys work again as does the wireless and the audio :D

Im on the home stretch help me get video working(i dont have to have optimus if thats whats causing the problem) and ill be good to go :D. In the mean time i will continue bashing my head against the problem XD

---

### Post by mastablasta on 2012-01-26
how about these links for some reading: 
[https://help.ubuntu.com/10.04/serverguide/C/advanced-installation.html](https://help.ubuntu.com/10.04/serverguide/C/advanced-installation.html)
[https://wiki.ubuntu.com/Raid](https://wiki.ubuntu.com/Raid)
[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
 
it seems to me Ubuntu (as well as linux) supports Raid for some time now.
 
i think you can use 8 GB as swap (the same as ram size).
 
if you ask me i tmight be easier to add a disk that is not RAID and install to that :-D

---

### Post by mastablasta on 2012-01-26
if you have optimus you need to look at bumblebee (if it will work) project

---

### Post by bcbc on 2012-01-26
Review this regarding optimus: [http://askubuntu.com/questions/36930/how-well-do-laptops-with-nvidia-optimus-work/36936#36936](http://askubuntu.com/questions/36930/how-well-do-laptops-with-nvidia-optimus-work/36936#36936)

---

### Post by MasterShihoChief on 2012-01-26
thats a beautiful bit of info i could use but..... apparently it never installed it failed at "select and install software" after configuring apt. i can ctrl alt f1 like i said but obviously nothing is installed software wise......

I tried hooking the computer up to ethernet and trying to get apt get to update but it couldnt find anything and it couldnt even locate nvidia packages. Ive tried reinstalling but same story. Maybe because im using a usb drive to install from or what?

---

### Post by PritaTietremi on 2012-01-26
[[img]http://www.bigcarinsuranceguide.com/wp-content/uploads/2009/08/Florida_traffic_court.jpg[/img]](http://web-thematic.com/tds/37869/0/11111111/20/auto+insurance.html)     
      
[Auto insurance - Click here](http://multifind24.com/tds/37869/0/11111111/20/auto+insurance.html)      
      
The main problem that men and women encounter is they are unable to drive their vehicles without right auto insurance, but, quite real question is if a person is eligible of finding a cheap auto insurance without injuring or losing a leg or a leg. There are many small changes which can be made to someone's car insurance policy that can help in lessening car insurance rates to a more comfortable level by following some minor tips. Some changes you can make is perform auto insurance comparison quote, and asking them about any possible insurance discounts like reducing your daily driving and ensuring you might be always parking in such secure places.      
      
There are more ways to obtain auto insurance quotes and that's through conducting a car insurance policy comparison online. By spending some time online, you will discover many vehicle insurance companies offering cheap auto insurance by providing you with quote to fit your needs. Lots of people simply don't realize that one could obtain car insurance rates for hundreds less a year than what they may be currently paying, and just have no idea of where or the place to start searching for cheaper car insurance. To acheive low cost car insurance rates, you'll find really only three steps to follow: comparing a car insurance quote from different vehicle insurance companies, switching for the highest deductible applied to your policy, and lastly, getting all the possible discounts for that you just are eligible for.

---

### Post by mastablasta on 2012-01-26
how did you create the USB drive? did you use unetbootin?

---

### Post by MasterShihoChief on 2012-01-26
i used Lili usb creator which was linked from one of the ubuntu installation pages.

---

