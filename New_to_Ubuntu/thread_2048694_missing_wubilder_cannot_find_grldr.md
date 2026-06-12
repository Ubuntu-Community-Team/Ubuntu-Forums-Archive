---
title: "missing wubilder/ cannot find grldr"
date: 2012-08-27
forum: New to Ubuntu
---

### Post by desperate 101 on 2012-08-27
Not to sound like a total newb with Ubuntu, but i went thru the installation process. Everything worked fine until i robooted and selected to run Ubuntu. An error msgs pops up instantly saying "try hd 0,0 no wubild, try hd 0,1 NTFS5: 2 try hd 0,2 no wubild found. It also says cannot find grldr in all drives. Press ctr+alt+del to reset."
Now ive been thru most of the forums and its seemed to me that the problem was i didnt have a wubildr and wubuildr.mbr copied in my C:drive, so that was the first thing i checked. they were both there... 
I was then told to wait on reboot, and after a minute or 2 it would correct itself. sadly it did not.... ive tried this a few time now, but to no prevail. 
Upon closer reading of the forum sayin to copy wubildr files to c: drive, i noticed ppl were sayin to copy and paste "all 3" into c: drive. What is the 3rd one??? cuz all i have i c:drive is wubuildr and wubuilder.mbr.
Idk what the problem with this is, but Im sure one of u can help. Please note, that i dont understand most of ur lingo, and have a very basic gateway computer to do all this. very good at following step by step instructions. Oh, also i am running ubuntu thru wubi, and not using a cd nor a floppy drive. Any info fast and simple would be a great help. <3

---

### Post by Frogs Hair on 2012-08-27
Hello and Welcome

Take a look through the thread at the link until someone with more Wubi knowledge sees your thread . [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by desperate 101 on 2012-08-27
ive tried looking thru every thread u have on the subject and nothing seems to help.  i need help quick before i go with a different operating system all together...

---

### Post by zepub on 2013-05-26
Help me please.........Facing same problem...  Scene: I had Win7 and Ubuntu 12.10 that I installed with wubi-online, I could also see wubi in win7 installed program list... bt when I got win8 and installed I wanted win7 disappear... I loaded win8 and deleted the disk drive having win7 that also had wubi installed on... and now when I select Ubuntu it says the error mentioned above... try (hdo, 0/1/2/3/4/5/5): NTFS: no wubilder & cannot find GRLDR in all devices press ctrl+alt+del... do I need to put wubi in win8, bt how?

---

### Post by zepub on 2013-05-26
Help me please.........Facing same problem...  Scene: I had Win7 and Ubuntu 12.10 that I installed with wubi-online, I could also see wubi in win7 installed program list... bt when I got win8 and installed I wanted win7 disappear... I loaded win8 and deleted the disk drive having win7 that also had wubi installed on... and now when I select Ubuntu it says the error mentioned above... try (hdo, 0/1/2/3/4/5/5): NTFS: no wubilder & cannot find GRLDR in all devices press ctrl+alt+del... do I need to put wubi in win8, bt how?

---

### Post by bcbc on 2013-05-28
> **zepub said:**
> Help me please.........Facing same problem...  Scene: I had Win7 and Ubuntu 12.10 that I installed with wubi-online, I could also see wubi in win7 installed program list... bt when I got win8 and installed I wanted win7 disappear... I loaded win8 and deleted the disk drive having win7 that also had wubi installed on... and now when I select Ubuntu it says the error mentioned above... try (hdo, 0/1/2/3/4/5/5): NTFS: no wubilder & cannot find GRLDR in all devices press ctrl+alt+del... do I need to put wubi in win8, bt how?
Copy wubildr from the \ubuntu\winboot directory and put it in C:\wubildr

---

