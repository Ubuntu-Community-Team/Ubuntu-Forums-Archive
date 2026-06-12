---
title: "Need a foolproof way to install wine in 8.04"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by tahitiwibble on 2008-11-10
After a whole weekend of upgrading from 7.04 to 8.04 I finally got everything up and running - but talk about dazed and confused!!!

Please can someone tell me in simple terms how to get wine back.

In 7.04 I just "add/remove" wine and everything worked 100%. Now I don't even see the program in the Application menu!!!

---

### Post by Shwefty on 2008-11-10
In Add/Remove Programs, make sure that "All available applications" is the selected option under Show:, instead of "Canonical-maintained applications".  In 8.10 I just checked it out, Wine isn't under Canonical, but is under All.

---

### Post by tahitiwibble on 2008-11-10
> **Shwefty said:**
> In Add/Remove Programs, make sure that "All available applications" is the selected option under Show:, instead of "Canonical-maintained applications".  In 8.10 I just checked it out, Wine isn't under Canonical, but is under All.

I'm sorry, I should have explained that better. I **did** find and install wine, just like in 7.04, but nothing showed up afterwards in the "Application" menu to allow me to launch it.

---

### Post by Egi_Power on 2008-11-10
Hi!

You could try in System -> Preferences -> Main Menu:

Take it easy.

---

### Post by Kellemora on 2008-11-10
Hi TW

If it in fact installed and the WINE logo didn't appear in Applications, THEN, right click on applications, left click on Edit Menu's, left click on the arrow next to applications, then look down the list for WINE and put a checkmark in the BOX in front of the word WINE.

TTUL
Gary

---

### Post by tahitiwibble on 2008-11-10
> **Egi_Power said:**
> Take it easy.

:lolflag: I didn't think it showed that much.

I've had a **really** bad weekend with my Ubuntu upgrade.

This is what the terminal said;

dad@dad-desktop:~$ sudo apt-get install wine
[sudo] password for dad: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
wine is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 72 not upgraded.

I did try to install the Windows program I want to use a few minutes ago and it did install but won't run. I wonder if I should go back to the old version that I was using with 7.04?

---

### Post by tahitiwibble on 2008-11-10
> **Egi_Power said:**
> Hi!

You could try in System -> Preferences -> Main Menu:

Take it easy.

It's not there, the only indication that wine exists is the "Wine Windows Program Loader"

---

### Post by tahitiwibble on 2008-11-10
> **Kellemora said:**
> Hi TW

If it in fact installed and the WINE logo didn't appear in Applications, THEN, right click on applications, left click on Edit Menu's, left click on the arrow next to applications, then look down the list for WINE and put a checkmark in the BOX in front of the word WINE.

TTUL
Gary

Hi Gary,

I already tried that but to no avail. The strange thing is that in my HOME directory all the components are there, I did succeed in installing the program that I want to use in wine but the program won't run properly. Something seems to be missing during the installation.

---

### Post by tahitiwibble on 2008-11-11
I have spent days upgrading from 7.04 to 8.04. It's been a nightmare.

I have a very dear reference library that I would like to be able to use again in my old HD that contains my 7.04 system and home directory (I always save everything just in case things don't work). 

I have tried to install wine at least 8 times in my new 8.04 system and things do not go well at all (it seems to install itself invisibly, meaning that no icons appear anywhere on my Applications menu or elsewhere but the invisible .wine directory can be found in my home directory. I then try to install my reference library and things seem to install correctly but when I launch the .exe file it tells me that the program has encountered a problem and cannot continue. I have now deleted every trace of wine etc. from my hard drives.

My question is this; I have copied my old .wine file (with all the reference library files installed onto c: ) into my new 8.04 home directory and would like to install the same old version of wine 0.9.33 BUT when installing wine 0.9.33 I see the following message "Error: dependency is not satisfiable: libldap2" - Can I install this file somehow? Is it safe to do so? and How do I do that?

Thanks guys.

---

