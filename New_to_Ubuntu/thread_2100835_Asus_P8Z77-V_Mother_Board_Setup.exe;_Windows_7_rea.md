---
title: "Asus P8Z77-V Mother Board Setup.exe; Windows 7 ready"
date: 2013-01-02
forum: New to Ubuntu
---

### Post by REX746 on 2013-01-02
I have a newly custom-built cpu that I successfully loaded with Ubuntu 12.10 and upgraded to the latest kernel. The OS works great, no issues whatsoever with booting or connecting with the wireless network. However, I am still needing to set up the drivers for some of the components.
 

 It has an ASUS P8z77-V PRO motherboard installed and I am trying to utilize the Setup.exe from the MB Support CD in order to access the exclusive features of the MB. Of course, this motherboard/Setup is only “Windows 7 ready”. I have downloaded the “Wine Windows Program Loader” which has helped me to access some files on the MB Support CD, but the Setup.exe is still having error.
 

 By clicking on the Setup.exe (or dragging into the Terminal and hitting Enter) an error message comes up:  
 

 -AUSUHWIO.DLL-
  ! :  “Can't Open Kernel Mode Driver ASUSHWIO.sys”
 

 Clicking 'OK' :
 

 -ASCDDMI.DLL-
  “Can't Load ASUSHWIO.DLL”
 

 Clicking 'OK':  
 

 -Support CD Setup...-
  ! : “Can't Load ASCDDMI.DLL”
 

 

 I looked at the ASUS product support site and was not able to recognize the possible solution there. Wondering if I need to alter anything on the BIOS.
 

 Is there a modification/command that grants the Setup.exe kernel access? Are there other Linux/Ubuntu programs that will help with operating Windows Software such as this?


Thanks to anyone who can offer a suggestion and/or a solution!

---

### Post by oldos2er on 2013-01-03
With the exception of some wireless drivers, Windows drivers don't work on Linux. What are the components that aren't working?

---

### Post by Fahim Abdun-Nur on 2013-01-03
> **REX746 said:**
> I am still needing to set up the drivers for some of the components.

Which components are you having issues with? Typically I've never had to worry about drivers (well except some usb wifi dongles) on Ubuntu

---

### Post by Fahim Abdun-Nur on 2013-01-03
Asus doesn't seem to list any Linux drivers... [http://ca.asus.com/en/Motherboards/Intel_Socket_1155/P8Z77V/#download](http://ca.asus.com/en/Motherboards/Intel_Socket_1155/P8Z77V/#download)

---

### Post by Vakman on 2013-01-03
Why do you feel you have to install any additional drivers if all is working well?

---

### Post by audiomick on 2013-01-03
I went here, 

[http://usa.asus.com/Motherboards/Intel_Socket_1155/P8Z77V_PRO/#download]("http://usa.asus.com/Motherboards/Intel_Socket_1155/P8Z77V_PRO/#download")

which looks to be the download page for that MB. On the features tab, there are descriptions of all sorts of whizz bang. On the linked page, there is a download called "os limitations...". If you look at that, you will see that most of it seems to only work on Win7, most not on XP, and Vista is specifically excluded at the top of the page.

I think that what you are trying to access is something very specific, and probably not possible the way you are trying to access it. Whether you can get those features working in Linux most likely depends on whether someone in the Linux world has worked out a solution or not.

Tell us anyway: what is it precisely that you want to have working?

---

