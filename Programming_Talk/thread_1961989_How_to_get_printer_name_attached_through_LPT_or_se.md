---
title: "How to get printer name attached through LPT or serial Port?"
date: 2012-04-20
forum: Programming Talk
---

### Post by Gurmeet Singh on 2012-04-20
Hi Experts,

How i can get the printer description which has been attached through LPT or Serial port?
I am able to get same information when attached with usb using lsusb and now i want to get the same info when attached through LPT or serial.

In case of MS Windows, When attached printer (PNP enabled and on LPT port) switched on then a ballon is displaying at right bottom of screen showing name of printer also i can get all the information from windows registry at path HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Enum\LPTENUM\NameofPrinter.

Please guide me how i can get same in ubuntu.

Thanks,
Gurmeet Singh

---

### Post by albandy on 2012-04-20
sudo hwinfo --printer

---

### Post by Gurmeet Singh on 2012-04-20
Thanks albandy.

I want to use any inbuilt command or tool which is coming with Ubuntu distribution.

Can i get the printer information from a C/C++ program like name, id etc attached through LPT port.

Thanks in advance.

---

### Post by CynicRus on 2012-04-20
In my opinion, you can read "/dev/lp0" or "/dev/ports" and get needed information manually.

---

### Post by albandy on 2012-04-20
I don't know but you can check hwinfo source code. I remember that in C exists the system instruction to launch system commands.

---

### Post by CynicRus on 2012-04-20
For launching system command in C function system() is used

---

### Post by Gurmeet Singh on 2012-04-21
Thanks all for your valuable response.

> In my opinion, you can read "/dev/lp0" or "/dev/ports" and get needed information manually. 	

When i am trying to read the /dev/lp0, i am getting permission error.
How i can read the /dev/lp0 in my c/c++ program?

Thanks.

---

### Post by CynicRus on 2012-04-23
[http://koders.com/c/fidC2E4C7C1EE64182E91E95E853281CCAB37D8BDD8.aspx?s=%2fdev%2flp0#L40]("http://koders.com/c/fidC2E4C7C1EE64182E91E95E853281CCAB37D8BDD8.aspx?s=%2fdev%2flp0#L40") - just read this source.

---

### Post by Gurmeet Singh on 2012-04-23
Thanks CynicRus.

I have seen the code and understood little bit.

Can i use the method given in below link instead? 

[https://wiki.ubuntu.com/DebuggingPrintingProblems#Parallel_port_printer](https://wiki.ubuntu.com/DebuggingPrintingProblems#Parallel_port_printer)


Thanks in advance.

---

### Post by CynicRus on 2012-04-23
You can for everyone. The main thing after all that work. Using basic tools Unix - this is Unix way. You can manually read / dev/lp0, or can call cat /dev/lp0 - this is the same. Just in the first case - a chance to make mistakes much more.

---

### Post by Gurmeet Singh on 2012-05-03
Thanks.

---

