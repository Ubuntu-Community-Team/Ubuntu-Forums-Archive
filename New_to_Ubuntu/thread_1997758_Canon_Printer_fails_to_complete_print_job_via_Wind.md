---
title: "Canon Printer fails to complete print job via Windows XP"
date: 2012-06-05
forum: New to Ubuntu
---

### Post by quintoc72 on 2012-06-05
Hello,
I am very new to Linux/Ubuntu. I am having a problem with printing that I cannot find a similar instance of looking other posts.

I initially tried out Ubuntuon my laptop with various desktops through WUBI and was able to get a test print page after setting up my printer (the printer is a Canon Pixma iP4200 connected via USB to a Windows XP machine). Then, I did a regular install of Xubuntu. Now, when I try to print the test page, my laptop says it sent the print job, the printer starts to click and whir, and the power light flashes to show it is working, but nothing ever happens except the following error comes up on the windows xp machine:[INDENT]An error has occurred when printing the following print job. Click cancel to stop printing.
Job: Remote Downlevel Document
[/INDENT]The printer continues to flash the  power light until I reset it by unplugging it.

Some more info:

[LIST]
[*]I have connected to the printer by navigating as follows: Applications menu: System: Printing to bring up the "Printing - Local host" window.  From there I click the plus sign and click on "Network Printer" and then click on "Windows Printer via Samba".
[*]In the text box next to the text "smb://" I have on one occasion typed the name of the windows computer and on another typed the ip address of the computer on the network, then clicked browse and selected my printer, and clicked "forward.
[*]The system then searches for drivers, where I click on "Canon" and then the model number "Pixma iP4200" and the following driver (the only one listed) is selected:
[LIST]
[*]Canon Pixma iP4200 – CUPS+Gutenprint v5.2.8-pre1 [en]
[/LIST]
 
[*]I click "apply", approve the name of the printer and then it asks if I want a test page, upon which I get the symptoms mentioned at the beginning of my post.
[*]My laptop connects to the network wirelessly.
[*]I have not problems accessing the internet.
[*]I am able to view all shared files on the windows machine.
[*]The printer itself is shared on the windows side. As mentioned, it starts to make noises as it will print, but then hangs up. Then I have to unplug it to reset it.
[*]The printer works fine from the Windows machine.
[/LIST]
I hope that is enough information. I tried to be thorough based on the types of questions helpers in other posts  usually seem to ask.

Thank you for your help.

---

### Post by daemoncycler on 2012-08-20
Hi,
Just came across your thread because I had this issue sometime back but forgot what had done to correct it & came to find the answer again.  Anyway if you haven't already discovered the problem is most likely that you have *Enabled Bidirectional Printing Support* & need to disable it on the Windows XP machine.

see this thread [https://help.ubuntu.com/community/WindowsXPPrinter]("https://help.ubuntu.com/community/WindowsXPPrinter")

**Disable Bidirectional Printing Support**
If the printer is configured in Windows with bidirectional support enabled, issues may occur where the printer stalls when starting to print. To resolve this disable bidirectional support:

Choose Start > Control panel > Printers & Faxes.

Right-click on the printer and choose Properties.

Select the Ports tab.

Uncheck Enable bidirectional support and click OK.

---

### Post by daemoncycler on 2012-08-24
Just found out the hard way that disabling bidirectional print support means that you're knocking down two way communication between your PC & printer.  If for instance you use the PC to check ink levels.

I will from now on only disable it when I need to print from the Lubuntu machine - not too often.

---

