---
title: "power interrupted, incomplete upgrade to 13.10"
date: 2013-11-18
forum: New to Ubuntu
---

### Post by sram180990 on 2013-11-18
hello guys
i am very new to ubuntu 
i have a problem that i have upgraded the ubuntu 13.04 to 13.10.
due to some power problem the installation was stopped.
so pls suggest me some ways to complete the full installation.

---

### Post by QIII on 2013-11-18
Please use more descriptive titles.  Titles such as "Help", "Problem", "Something is wrong" do not draw attention and others will often pass such threads by.

---

### Post by ian-weisser on 2013-11-18
Did the update fail during the *download* phase of the installation, or during the *install* phase of the installation?
The fix is different depending upon when the interruption occurred.

Backup all your data. The release-upgrade process is not meant to be interrupted, and you may wind up reinstalling.

Open a terminal.
Try the command [B]do-release-upgrade
[/B]If the command does not continue the interrupted downloading process, then try the command [B]sudo dpkg --configure -a
[/B]
If you get an error message, stop. Show us the entire session leading to the error message.

---

### Post by philinux on 2013-11-18
+1 to the above. However if you cannot login do the above from grub in recovery mode (with networking enabled).

---

### Post by sram180990 on 2013-11-18
the upgradation was stopped in installation phase so please suggest me some solution due to that my cd drive is not been detected and bluetooth is also not responding and giving me the message no adaptor is found eventhough i have installed the blueman v1.23 still not working properly. so please suggest me some solution

---

### Post by ian-weisser on 2013-11-18
What is the complete result of **sudo dpkg --configure -a**  ?

---

### Post by sram180990 on 2013-11-19
it shows dpkg error  
dpkg: error processing oracle-jdk7-installer (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 oracle-java7-installer
 oracle-jdk7-installer

---

### Post by sram180990 on 2013-11-19
and is that better to take backup all data and installating it freshly or is there any solution

---

### Post by ian-weisser on 2013-11-19
I hope you have *already* backed up your data. As I wrote before, that was the first step and importantly so.

Do you to reinstall? It may be a fast and familiar way to fix the problem. 
Or do you want to fix the problem manually? Previously, that's what you seemed to want.
It's your system. You get to decide. Neither option is better or worse.

---

### Post by sram180990 on 2014-03-13
hello buddy 
Now can you give me the commands used in terminal
;)

---

### Post by ian-weisser on 2014-03-13
Can't really help you until you answer the questions first.

---

