---
title: "Printer driver"
date: 2013-02-03
forum: New to Ubuntu
---

### Post by briar rabbit on 2013-02-03
Hello,

I am trying to get a Canon BJC 80 Printer to run on my Lucid.

I downloaded and extracted 'gutenprint-5.2.9.tar.bz2' however, my BJC 80 properties still show 'CUPS+Gutenprint v5.2.5 Simplified' as the driver.

I have searched and downloaded a few things that have not helped.  I think this newer version of 'gutenprint' will work if I can get it to the printer.

How can I get the newer version of 'gutenprint' to show up in the printers driver properties?

Thanks

---

### Post by Mark Phelps on 2013-02-04
Did you try using "localhost:631" in a Browser to bring up the printer to see if you can select the new driver?

---

### Post by briar rabbit on 2013-02-04
Thanks Mark,

I just now looked in "localhost:631" and could not find anything but I'm not sure what to look for.  'driver' 'update' 'properties' and anything posted that sounds like it would be similar.

I have had a little luck since posting for help.  Here are a little more details.

When I connect and turn on the BJC 80 it tries to connect over and over endlessly - it 'stutters' is what someone called it.

When I would go into the printer properties I could see that the printer was not 'enabled' so I checked 'enable' this stopped the 'stutter but it would not stay.  Eventually for what ever reason now it will stay 'enabled'.

However, when I connect and turn on the printer it goes back to 'stuttering'.  Now, to stop the 'stuttering' I click 'print test page' in the printer properties window.  I take the paper out before it prints, then I delete the print job.
  Now the printer is recognised and quietly awaits a real print job.
This seems like the long way of doing things however it is getting better.

But why do the properties not show the updated 'gutenprint'?

observational note:
Every time I have a problem with my PC and look to the Internet for answers it amazes me at how much so many people are doing to advance Linux.  If it weren't for so few with so much money making products not just for endless profit but for consistent control the people would have an OS with limitless potential.

---

### Post by Mark Phelps on 2013-02-04
When you go into CUPS there will be a properties page somewhere (or maybe, setup) that will allow you to see which driver is selected.  

When I recently installed my HP from CUPS, there was a long list of drivers.

Also, you should go into Synaptic Package Manager and see which version of Gutenprint it shows as installed.

---

### Post by briar rabbit on 2013-02-04
Hello Mark and thanks again for your time,

The 'CUPS' properties says "Canon BJC-80 - CUPS+Gutenprint v5.2.5 Simplified".

I have tried 12 different drivers from different suggestions off the internet including here on the forums.  They were already listed as choices in the driver data base in my printer properties.

The Synaptic PM shows "cups-driver-gutenprint  5.2.5-Oubuntu1.1".  When I try to get the "Mark for Upgrade" it is greyed out.

I downloaded the 5.2.9 version guten but it is not showing up.

Eventually with help I will get there - just frustrating now.

---

