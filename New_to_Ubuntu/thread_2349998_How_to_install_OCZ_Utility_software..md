---
title: "How to install OCZ Utility software."
date: 2017-01-20
forum: New to Ubuntu
---

### Post by nevets68 on 2017-01-20
I have a OCZ trion ssd. I want to install the utility software that i downloaded from the OCZ website. It's called - SSDUtility_2.2.2645.tar.gz.  
When I open the folder , I see 3 items :

One folder called - linux 32
One called -  linux 64 

and a .rtf file - which talks about licensing. 

How do i proceed in installing the software?

---

### Post by Frogs Hair on 2017-01-20
When I click on the file in the 64 bit folder which is the OS I'm using there is a superuser required message. Try right clicking on the file and changing the permissions to read and write. I can test no further because I don't have this SSD.

---

### Post by SmilingInSeattle on 2017-01-29
1)  The SSD must first be connected via SATA to the controller.  If it's all ready mounted inside your computer, then that's done.  If you are testing it outside the desktop, then use an eSata port from your desktop to a spare eSATA bracket that has a regular SATA data connector on the back of it.  You can then power the drive with a power brick that has the SATA type power connecter attached.  (You can't test an external drive using a USB converter).

2) Using the terminal, navigate to the SSDUtility script under the appropriate bus size.

3) Execute the script with: sudo ./SSDUtility.  Starting with sudo will effectively take care of the "administrative rights" you found when you tried to execute it from a GUI.

4)  Your disk should show up in the window.

---

