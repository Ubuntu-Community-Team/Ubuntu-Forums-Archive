---
title: "AMD Unsupported hardware"
date: 2013-03-09
forum: New to Ubuntu
---

### Post by pccruzadas on 2013-03-09
I have installed some drivers manualy in order to run Second Life, now i have a worning on the bottom right cornner saying AMD Unsuported hardware. How can i get rid of this? Unbuntu.

---

### Post by deadflowr on 2013-03-09
What version of Ubuntu are you running?
What is the graphic card?
Which driver version did you install?

Here's a couple links for good measure:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by pccruzadas on 2013-03-09
> **deadflowr said:**
> What version of Ubuntu are you running?
What is the graphic card?
Which driver version did you install?

Here's a couple links for good measure:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Hi, my graphics card is an ATI Radeoan HD 5670, Unbuntu 12.10, I installed manualy:

sudo add-apt-repository ppa:makson96/fglrx
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install fglrx-legacy

These were the comands i entered in the terminal, i took these commands from a Second Life forum, because i couldn't run Second Life, now i can but i have this warning permanentely on the bottom right cornner of the screen

Thank you

---

### Post by pccruzadas on 2013-03-09
> **deadflowr said:**
> What version of Ubuntu are you running?
What is the graphic card?
Which driver version did you install?

Here's a couple links for good measure:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Ubuntu 12.10
ATI Radeon HD 5670
fglrx

Thank you

---

### Post by deadflowr on 2013-03-09
Your card should be using the normal fglrx drivers, which can be installed from the Ubuntu repos.
The legacy drivers are for the 4XXX series and older(3xxx,2xxx).

You can install the drivers in the additional drivers section of the software sources, which in in the system settings menu.

However, you would have to purge the ppa drivers.

I, personally avoid ppas, so purging them is something I'm only distantly aware of.

I found this page with a quick run of the commands needed to purge those drivers.

[http://www.ubuntuvibes.com/2012/10/how-to-install-amd-catalyst-legacy.html](http://www.ubuntuvibes.com/2012/10/how-to-install-amd-catalyst-legacy.html)

---

### Post by pccruzadas on 2013-03-09
> **deadflowr said:**
> Your card should be using the normal fglrx drivers, which can be installed from the Ubuntu repos.
The legacy drivers are for the 4XXX series and older(3xxx,2xxx).

You can install the drivers in the additional drivers section of the software sources, which in in the system settings menu.

However, you would have to purge the ppa drivers.

I, personally avoid ppas, so purging them is something I'm only distantly aware of.

I found this page with a quick run of the commands needed to purge those drivers.

[http://www.ubuntuvibes.com/2012/10/how-to-install-amd-catalyst-legacy.html](http://www.ubuntuvibes.com/2012/10/how-to-install-amd-catalyst-legacy.html)

I used the link you gave me and purged the ppa drivers like you said, but i still see them on the drivers setion. How do i get the Ubuntu Repository?

---

### Post by deadflowr on 2013-03-10
To get to the Ubuntu Driver section, open the system settings application and then go down to the section software sources.
Click on software sources and when that window opens move to the section Additional Drivers.
This is where the available non-free(closed-source drivers) can be easily installed or removed.
Best bet is to try the top most version, usually just fglrx. Other ones would be fglrx-updates.
To install, just click the version you want to install and select activate, the program will then download and install the drivers.
When installed, I think you then run the aticonfig --intialize command. Look over that in the How-to wiki I posted earlier.(second link)

---

