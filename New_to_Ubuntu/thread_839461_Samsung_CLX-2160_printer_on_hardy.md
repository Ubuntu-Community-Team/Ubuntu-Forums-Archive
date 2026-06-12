---
title: "Samsung CLX-2160 printer on hardy"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by loza on 2008-06-24
Hello

I am having trouble with this printer and want to delete or uninstall the drivers from Hardy.

Can someone tell me how to do this please?
Cheers
loza:confused:

---

### Post by phidia on 2008-06-24
If you open (click on) the System>Admin>Printing menu item you should get a interactive window that will aloow you to select that printer and delete it.
That will accomplish what you want.
If you want to learn more about how your printer is supported in linux check out openprinting.org.

---

### Post by loza on 2008-06-26
Thank for the reply.

I have managed to delete the printers and start again but I get some really confusing report from xsane say that there is no scanner detected. However it is there as it is part of the printer!

if I run the xsane-find-scanner command it tells me theres a scanner from samsung but when I run xsane it does not detect it.

any ideas anyone...:(

loza

---

### Post by spandon on 2008-06-27
Hi 1oza,
I to have just aquired a CLX-2160 Printer and had the same problem as yourself.
The automatically installed printer driver for this printer in Ubuntu (i am using Ubuntu 8.04)works perfectly as a printer, but the Scanner did not work for me also.
I searched the threads on here and also contacted Samsung, and between them I came to the conclusion that what was needed was to download the Samsung driver and install it that way.
This I did, and once I installed it, there was a Samsung Unified Printer Configurator icon on the Desktop also an entry in the Applications Menu for this printer.
I also found out that the driver needs to be re-directed to be able to use the USB please see the item here, which I also did (delete the asterisk from 4 lines) [http://ubuntuforums.org/showpost.php?p=4776310&postcount=114](http://ubuntuforums.org/showpost.php?p=4776310&postcount=114) .
After doing this I tested out the Configurator, and still the Scanner was not recognised, then I re-read the Samsung instructions, PRESS the "scan to" button on the printer panel THEN select scan and the scanner worked perfectly.
Hope this helps you?
don

---

### Post by loza on 2008-06-30
Thanks Spandon

I shall give this a shot and report back! 

thanks again one and all! :)

loza

---

### Post by loza on 2008-06-30
Thanks guys it working again!!!! GREAT!

And thanks spandon for a hint to the xsane fix - that has troubled me for sometime!

loza

---

