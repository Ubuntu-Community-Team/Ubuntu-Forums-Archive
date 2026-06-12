---
title: "ADSL modem and Terminal command problem"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by bamdad on 2008-08-24
hey there everyone i've just joined the ubuntu community yesterday and i have installed 8.04

i've been trying to install my Planet ADSL USB modem which happens to work with the access runner. i followed the help presented in 
[https://help.ubuntu.com/community/UsbAdslModem/AccessRunner ]("https://help.ubuntu.com/community/UsbAdslModem/AccessRunner")
 
but once i type in :

cxacrufw-extract ~/CnxEtU.sys ~/cxacru-fw.bin

it tells me that "cxacrufw-extract" is not a commands and not recognized. can anyone tell me what im doin wrong?:confused:

---

### Post by matthewbrave on 2008-08-24
> **bamdad said:**
>  

cxacrufw-extract ~/CnxEtU.sys ~/cxacru-fw.bin



are you typing in the capitals and not just typing in lower case.

eg capital 'C' is totally different than lower case 'c'

cxacrufw-extract ~/CnxEtU.sys ~/cxacru-fw.bin

is totallt different to:

cxacrufw-extract ~/cnxetu.sys ~/cxacru-fw.bin

---

### Post by bamdad on 2008-08-24
yea i have typed exactly the way that its told in the help link. the first line executed perfectly but it doesnt recognize 

cxacrufw-extract

---

### Post by matthewbrave on 2008-08-24
well it is beyond me, cos all i can think of is the capitals. i am sort of new to linux as well!

---

### Post by bamdad on 2008-08-24
thanks man, guess ill just keep trying since this sounds pretty wierd

---

### Post by bamdad on 2008-08-24
im wondering, what does this cxacrufw-extract mean exactly? i've been searching forums and helps but i cant find anything...

---

### Post by Cheesehead on 2008-08-24
Did you *install* anything (package or file) described in the instructions before trying the command?

You must install the code that tells the computer how to execute the command.

Get the code from [http://sourceforge.net/project/showfiles.php?group_id=47406](http://sourceforge.net/project/showfiles.php?group_id=47406) - click on the little clipboard symbol for instructions.

---

### Post by bamdad on 2008-08-25
yea i noticed the package and tried to install it today but im facing the new problem. as mentioned in the help page. there are two packages one of the is the CVS itself and another one belongs to Nicolas Wheeler. i've been trying to install the CVS but all the read me files were in spanish and the translations were presented online and since im trying all this to get online then i cant understand a thing from the read me. then i took my chances on Nicolas package but there's no info on what i really have to do .. .i mean there are 5 or 6 links in the page and only one of them works which is a tar.gz file. i opened it but there was only a makefile and no readme or instructions except a couple license and copyright texts. could you guys help me out here? i feel like running in circles 

[http://revu.tauware.de/details.py?upid=2426 . ]("http://revu.tauware.de/details.py?upid=2426")

---

