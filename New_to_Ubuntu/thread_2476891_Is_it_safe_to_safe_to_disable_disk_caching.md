---
title: "Is it safe to safe to disable disk caching?"
date: 2022-07-11
forum: New to Ubuntu
---

### Post by r2020r on 2022-07-11
I was copying 10GB files to a 32GB SD card(using on a SD card reader, connected to USB port) using FILE manager of Ubuntu 22.04. It copied at the speed of ~80Mb and completed in reasonable time. I tried to EJECT the card and it showed to the message to the effect "*...do not remove the device...*". This dialog when on and on. I did not measure the time but seemed to go on for **5minutes**. Seems all the data was kept in cache and took time to write to disk. 

I would prefer data consistency over speed. I do not mind waiting for copy to complete for 5minutes more.  So rather have OS actually write to disk instead of caching, and taking its own time to actually write to disk.. 

a) Is there a copy tool that **disables caching temporarily?**. 
    OR
b) Should I permanently disable the** caching at the disk level** by using tool like **hdparam**?

Which solution is better a or b. Please guide.

Thanks

---

### Post by Holger_Gehrke on 2022-07-11
Option b) would be mostly useless, since the effect you're seeing is mostly caused by caching in RAM and not by caching on the drive. I would try issuing a 'sync' command in the shell after the copying is finished, this should only return after all cached data is actually written.

Holger

---

