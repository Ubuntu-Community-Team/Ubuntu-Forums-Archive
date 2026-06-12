---
title: "The issue about turning off the computer"
date: 2011-09-30
forum: New to Ubuntu
---

### Post by Acquisitio on 2011-09-30
Since I've installed Ubuntu I cannot turn off my computer. Whenever I turn it off something similar to this appears at the end of the process  and stays on monitor:



terminate...                                                                                                                                                                                 Asking all remining  processes to 
                                                    
 All processes ended within   seconds...                                                                                                                               OK
 Deconfiguring network interfaces ...                                                                                                                                        OK
 Deactivating swap...                                                                                                                                                                                            OK
 Unmonitoring weak file system...                                                                OK
 Will now halt                                                                                                 OK
System haltd



Also the green light on the PC stays on so I have to turn the computer off manually(looks like the computer continue working).Every single time. After I manage to turn it off(manually, as I already said)the green light on the PC continue blinking for hours.
But if I use Windows then I have no problems with turninig the computer off. With Windows it goes regularly. 
Where could be the problem?

---

### Post by WasMeHere on 2011-09-30
Hi Acquisitio,

System halted means that it has stopped, but the power has not been switched off. In this case you can switch it off by pressing the button shortly. 'Annoying but not really bad.'

If the system gets stuck, you can press the button for several seconds, and you may have bad luck and damage some file(s) on the hard disk. There is a better alternative explained here:
[HOWTO: _Linux Magic SysRq key (R-E-I-S-U-B: Reboot Even If System Utterly Broken)_]("http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=11299975").

Back to your system: The terminal command *poweroff* run as superuser *sudo*
```
sudo poweroff
``` should do what you want. Try if it works!

It could be a problem with the ACPI (Advanced Configuration and Power Interface) of your computer, that Ubuntu and your ACPI cannot shake hands.

---

### Post by WasMeHere on 2011-09-30
If *poweroff* does not work, I think it is a problem with the ACPI (Advanced Configuration and Power Interface) of your computer, that Ubuntu and your ACPI cannot shake hands.

---

