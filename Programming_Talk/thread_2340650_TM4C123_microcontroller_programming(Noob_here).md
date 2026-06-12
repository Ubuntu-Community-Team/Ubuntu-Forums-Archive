---
title: "TM4C123 microcontroller programming(Noob here)"
date: 2016-10-20
forum: Programming Talk
---

### Post by Roberto_Hernndez on 2016-10-20
Hi guys thanks in advance for any help that you might want to provide. I'm starting a new school embedded systems project related (also as Open Source environment project), but the micro controller required for this course is an IT TM4C123. According to the course syllabus the IDE is only available for Windows, nonetheless, I was able to install it using wine but I'm not quite sure if it's going to run properly due to the fact that the TM4C123 drivers are available only for Windows. Is there any way that I can install Windows drivers on Ubuntu 16.04? If you can provide any suggestions or any solution that'd be awesome.

This is the Official TI's drivers web page [http://www.ti.com/tool/stellaris_icdi_drivers](http://www.ti.com/tool/stellaris_icdi_drivers)

---

### Post by mcgbb on 2016-10-21
From last time I was playing with the Stellaris stuff from TI, their official IDE was Code Composer Studio.   It comes with everything already set up for their Stellaris and Tiva range though I think its limited in some ways for the free version. (see [http://processors.wiki.ti.com/index.php/Licensing_-_CCSv6](http://processors.wiki.ti.com/index.php/Licensing_-_CCSv6) for details).  
Code Composer is based on Eclipse and so is multi platform, and TI do a specific Linux distribution (requires 64bit Linux distro) which you can obtain from [http://processors.wiki.ti.com/index.php/Download_CCS](http://processors.wiki.ti.com/index.php/Download_CCS)
For using the ICDI under Linux; it looks like CCS comes with built in support for the ICDI, but also a quick Google seem to show that OpenOCD supports the TI ICDI.  There are many pages that could be useful, I've included a couple here.
[http://processors.wiki.ti.com/index.php/Stellaris_Launchpad_with_OpenOCD_and_Linux](http://processors.wiki.ti.com/index.php/Stellaris_Launchpad_with_OpenOCD_and_Linux)
[http://www.jann.cc/2012/12/11/getting_started_with_the_ti_stellaris_launchpad_on_linux.html](http://www.jann.cc/2012/12/11/getting_started_with_the_ti_stellaris_launchpad_on_linux.html)

Hope this is useful!

---

