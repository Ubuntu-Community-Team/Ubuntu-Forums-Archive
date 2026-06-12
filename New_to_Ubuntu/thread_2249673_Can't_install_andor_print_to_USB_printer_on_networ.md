---
title: "Can't install and/or print to USB printer on network"
date: 2014-10-23
forum: New to Ubuntu
---

### Post by snowmobiler on 2014-10-23
I have a Brother printer connected to a PC via USB running Ubuntu 14.04. Printer works. I installed the printer on 2 laptops running Ubuntu. Printer wouldn't work. I was told to use CUPS to 'publish' the printer. That worked and I was able to print from both laptops. The properties were automatically changed to something like ipps: . . . that was weeks ago. SInce then I changed the HD on one of the laptops to an SSD. Now when I went back to check the printing, no printer shows up on either laptop and I can't remember or figure out how to 'add' the printers again to the laptops. SHould it be 'network' should it be via 'URI' etc.? 

Before I just needed to get the printer published but now i can't seem to add the printer to the laptops and have the PC recognize it via CUPS. I have tried unchecking and then rechecking the 'share printers connected to this system". Also not sure if I should have 'print from internet' checked as well. I tried looking for my original post but can't find it. So sorry for re-asking a similar question.

---

### Post by snowmobiler on 2014-10-23
Just to update. I somehow got it to connect properly on one of the laptops. I ended up rebooting the PC. Now on the laptop it has a URI of 
ipps://{PC-name). local:631 etc. Which is what shows up in CUPS. 

After it printed out the waiting test pages and then I printed a new test page. I then tried to print something else out and it got all messed up again. Can't find printer. If I recall correctly, when I got this to work weeks ago, I was having trouble with laptop like I said. When I got it to work using CUPS, I went to enter the info on the other laptop, but the printer was automatically recognized. I didn't have to 'add'. 

At this point should I just delete the printer and re-install? Driving me crazy that it works then doesn't then does.

EDIT-- the other odd thing its doing on the one laptop, is after I install it using URI, then if I do something like reboot the PC, then I go to the laptop and there are 2 of them. Sometimes it says Brother-HL-2140- series and sometimes it just says HL-2140-series. According to CUPS, the printer queue is the first one so that is what I have been entering. I may have entered the second one previous so I dont know if just 'deleting' the printer on the laptop clears everything. one or the other shows up with a check mark but then it still can't find the printer. going nuts.

---

### Post by snowmobiler on 2014-10-24
I may have found the answer but i am not sure. Can anybody answer this? When using CUPS, do you have to have the Browser page open while trying to print from another machine? I read something that said the printer should just 'pop up' if CUPS is running and will disappear if you close CUPS. Maybe that's the goofy thing I have been doing without realizing it.

---

