---
title: "Ubuntu startup boot"
date: 2019-10-13
forum: New to Ubuntu
---

### Post by felix242 on 2019-10-13
I just installed ubuntu as a dual boot with windows and it takes a lot to start..... And i mean a lot more than ten minutes (no joke) but the thing is, it just got kinda stuck in a violet screen before it says "ubuntu" on the screen i dont think this is normal,  i also have to mention i installed it kinda weird, i installed it and everything was normal but for stupids reasons i tried to delete it, i also did a factory reset on windows, and installed ubuntu again....

---

### Post by ajgreeny on 2019-10-13
We need much more information to be able to help you.

What is the hardware to which you installed Ubuntu; command ```
inxi -Fzx
``` will tell us a lot more. 
What version of Ubuntu did you install?
What version of Windows do you currently have, and is it installed using MBR/BIOS or UEFI, the new firmware for just about every computer sold currently?
Please use **Code-Tags** for terminal output to show that text in a more readable format, the same as it is in the terminal, not as plain text. See my signature below for a **How-to**

It will be best to see exactly where you are at present so go to **Boot-Repair** in my signature below and follow the instructions there to run the Boot-Info-Script, from a live system if necessary.	 

**Do not run the default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system.

---

### Post by felix242 on 2019-10-13
Mi pc is a laptop acer aspire A315_41
AMD ryzen 5 with radeon vega 
The version of ubuntu is 19.04
Y installed it using the bios
I use windows 10

---

### Post by ajgreeny on 2019-10-13
Did that PC come with Win 10 pre-installed?  If so it will have been installed as a UEFI installation, and your Ubuntu should therefore also be installed using UEFI.

I am not sure this would make a difference to the speed of booting, but I think it does mean that you must currently be using the UEFI keypress to get to Ubuntu.

I have no experience of Ryzen CPUs and graphics, so will have to leave this to others to answer with a better solution for you.
It will still be worth running Boot-Repair as suggested in my first post as it will tell us a lot more.

---

### Post by yancek on 2019-10-13
I would suggest you read the Ubuntu documentation on dual booting with windows and compare it to what you did.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

