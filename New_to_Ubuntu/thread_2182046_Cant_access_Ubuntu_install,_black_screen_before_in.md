---
title: "Cant access Ubuntu install, black screen before install menu"
date: 2013-10-19
forum: New to Ubuntu
---

### Post by 7xF6hnJ on 2013-10-19
Ok, so im really new to Ubuntu/Linux and all but i thought id give it a go. Now ive followed the instructions so far, burnt the iso to a disc correctly, changed my bios for it to boot first, and restarted my computer. The computer seems to post alright, the disc starts spinning and i get the purple screen with the little images down the bottom, now this is where it stops, i get a brief flashing cursor then nothing, the disc stops and the screen goes blank. I cant seem to find any errors about black screens before i even get to the menu and everything ive tried just returns the same result!

---

### Post by fantab on 2013-10-19
Different hardware behaves differently. So, tell us about your computer's hardware specs, like, Graphics Card, RAM, CPU etc.
Is this a laptop or desktop? Did it come pre-installed with any OS, what OS and version? All this information will help us understand the problem you are having and help you.

Meanwhile try NOMODEST. [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132). 
Nomodeset option forces Ubuntu to use opensource drivers for your Graphics card temporarily.

---

### Post by 7xF6hnJ on 2013-10-19
Okay, so the main reason i am trying to install Ubuntu is my computer runs a dual boot of windows 7/8 which are having errors and at the moment i cant boot my computer at all, stuck in a restore loop. The computer was most likely pre-installed with xp as it is a few years old.
I dont know the exact hardware specs for a few, however i do know it is a desktop with an Abit Ab9 pro motherboard, 4 lots of 2gb corsair RAM, Intel Core 2 CPU, Phoenix AwardBIOS, Gigabyte psu but i dont know what my graphics card is.
As for nomodeset, i would try it but i cant access the menu. Straight after the purple screen with the keyboard at the bottom i just get a flashing cursor and then nothing, even if i press a button.

---

### Post by fantab on 2013-10-20
Keep trying you should be able get the desired outcome. You have press F6 at the menu..

You say you are already having problem booting Windows. This could also mean that there could be some Hardware Problem, have you considered that? Why don't you check with some 'service center' tech to confirm if the hardware is in working condition?

---

### Post by 7xF6hnJ on 2013-10-20
Thats the thing i cant get any menus whatsoever, only the purple screen which different articles advised to press different buttons to no avail.

I have considered that it could be a hardware problem, however up until last night my computer was running smoothly. I did wonder though whether this was a BIOS issue, because when I was trying to install Ubuntu i changed a BIOS setting i shouldnt have. 

So i went and reset my BIOS by using the jumper and thats when my windows issue occured!

I tried restoring any original BIOS settings but as im not entirely sure what they all were i cant really do much.

---

### Post by fantab on 2013-10-20
> **7xF6hnJ said:**
> Thats the thing i cant get any menus whatsoever, only the purple screen which different articles advised to press different buttons to no avail.

I have considered that it could be a hardware problem, however up until last night my computer was running smoothly. I did wonder though whether this was a BIOS issue, because when I was **trying to install Ubuntu i changed a BIOS setting** i shouldnt have. 

So i went and reset my BIOS by using the jumper and thats when my windows issue occured!

I tried restoring any original BIOS settings but as im not entirely sure what they all were i cant really do much.

"...trying to install Ubuntu i changed a BIOS setting"
What exactly did you change?
Check to see if the jumper was replaced properly and in the right place.

Windows will have problem running when some BIOS settings are change after Windows was installed. Reinstalling Windows could be a good idea, if you don't know what all you changed or what were the original settings.

As for Ubuntu, confirm that you have Burned the .iso correctly to the Disk. Check if your downloaded .iso has correct [MD5Sum]("https://help.ubuntu.com/community/HowToMD5SUM").
At Ubuntu boot try [NOMODESET]("http://ubuntuforums.org/showthread.php?t=1613132")...

---

### Post by 7xF6hnJ on 2013-10-20
I was curious as to changing the power-on function however it didnt work and I resorted to resetting the BIOS. Yes the jumper is replaced correctly.

I would rather not have to reinstall as there are files on my harddrive i wish to keep. 

Thats why I was hoping to install Ubuntu as to access and back them up.

I'll check that it is burnt correctly now.

And what exactly do you mean by "At ubuntu boot"? Because i cant access the menu or the "grub" which the article refers to.

---

### Post by 7xF6hnJ on 2013-10-21
Ok so i have managed to solve the problem, i had to enable usb keyboard support to the BIOS to allow me to access the menu and use the NOMODESET command, thankyou fantab for your assistance!

---

### Post by fantab on 2013-10-21
Glad you figured it out...

Mark the thread as 'Solved' using Thread Tools.

---

