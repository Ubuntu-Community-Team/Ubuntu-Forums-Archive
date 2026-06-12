---
title: "Still cant solve wireless problem"
date: 2011-10-26
forum: New to Ubuntu
---

### Post by dustysnakes on 2011-10-26
So I have been working on this problem for almost a week now.  I have a gateway M series laptop with a 4311 broadcom wireless adapter.  Just installed Ubuntu 11.10.  Now that thats out of the way....
I have gone through several options to make the device work the last of which being here  ubuntuforums.org/showthread.php?t=25683   that Jonny has posted.  This did make headway.  I can remove the STA driver that pulls up in settings and for the first time I now have at least an accknowledgement of wireless being there.  I have a greyed out Wireless networks and underneath a "device not ready (firmware missing).  Anyone have any more tips on this I have also tried toggling to the b43 driver to less avail.  I hate to keep pestering you guys with this noob stuff but I feel like the very definition of the word at present moment.

---

### Post by wolfen69 on 2011-10-26
Have you tried any of the tips in [this]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx") how to?

---

### Post by NattyLight on 2011-10-26
> **dustysnakes said:**
> So I have been working on this problem for almost a week now.  I have a gateway M series laptop with a 4311 broadcom wireless adapter.  Just installed Ubuntu 11.10.  Now that thats out of the way....
I have gone through several options to make the device work the last of which being here  ubuntuforums.org/showthread.php?t=25683   that Jonny has posted.  This did make headway.  I can remove the STA driver that pulls up in settings and for the first time I now have at least an accknowledgement of wireless being there.  I have a greyed out Wireless networks and underneath a &quot;device not ready (firmware missing).  Anyone have any more tips on this I have also tried toggling to the b43 driver to less avail.  I hate to keep pestering you guys with this noob stuff but I feel like the very definition of the word at present moment.

 Did you try installing the firmware - b43 - installer - lpphy from the Synaptic Package Manager?

---

### Post by NattyLight on 2011-10-26
> What worked for me was downloading the STA broadcom driver... after this the wireless button finally turned blue but I still couldnt get online? So I then hooked the ethernet cable to my laptop so I could get the Synaptic package and then within the SPM I searched for B43... I marked b43 firmware installer lyyphy and I believe the cutter as well. After doing that I was finally able to connect wirelessly!  My Broadcom is 4312 though so I am not sure if that will work for you? It is worth a try though!  From the other thread that you posted.

---

### Post by dustysnakes on 2011-10-26
unfortunately no such luck.  unless there is some terminal command I need to do afterwards that I haven't discovered.

---

### Post by NattyLight on 2011-10-27
So you DLed the STA driver, and installed B43 firmware installer lpphy, did you activate it? Is the other b43 firmware still marked as well? You *may* have to blacklist a driver that is keeping the b43 lyyphy from working?

---

### Post by dustysnakes on 2011-10-27
well ... :confused:  perhaps I am missing somthing here.  I dl'ed the b43 and the b43 cutter from synaptic and restarted.  However if I go to settings/additional drivers the only thing that comes up is the STA driver which is activated.  Sorry I'm sure this is kid stuff.

---

### Post by dustysnakes on 2011-10-27
You guys rock!  I am now currently browsing wireless.  As it turns out there were some issues in blacklist and also the lpphy version of the b43 driver did not work for me and I had to uninstall it and revert to the original.  Thanks very much to everyone that has helped me out on here.  Hopefully I can pay it forward when I learn a bit more about this system.

---

### Post by NattyLight on 2011-10-27
> **dustysnakes said:**
> You guys rock!  I am now currently browsing wireless.  As it turns out there were some issues in blacklist and also the lpphy version of the b43 driver did not work for me and I had to uninstall it and revert to the original.  Thanks very much to everyone that has helped me out on here.  Hopefully I can pay it forward when I learn a bit more about this system.

 Congrats! I felt your pain, for days I was struggling trying to get online and then finally I figured it out!

---

