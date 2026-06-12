---
title: "microphone on."
date: 2008-09-19
forum: New to Ubuntu
---

### Post by Kuroda_Shun on 2008-09-19
I am worried I have a root kit on my laptop. I may be overly cautious but I have a IBM thinkpad T42 with a built in mic. I started getting feedback (whistle) when I put my finger over the mic. I know that recording audio is one of the features of a good trojan. I would like to verify my integrity somehow but do not know how.
A possible cause can be that I installed a bluetooth dongle to listen to music in my headphones. I went to system/preferences/sound to change the default sound capture. I didn't know what it was to begin with. I hope that changing that setting. I am wondering if changing that setting would cause the mic to work all the time.

---

### Post by k33bz on 2008-09-19
> **Kuroda_Shun said:**
> I am worried I have a root kit on my laptop. I may be overly cautious but I have a IBM thinkpad T42 with a built in mic. I started getting feedback (whistle) when I put my finger over the mic. I know that recording audio is one of the features of a good trojan. I would like to verify my integrity somehow but do not know how.
A possible cause can be that I installed a bluetooth dongle to listen to music in my headphones. I went to system/preferences/sound to change the default sound capture. I didn't know what it was to begin with. I hope that changing that setting. I am wondering if changing that setting would cause the mic to work all the time.

go to the terminal and type ```
alsamixer
```
from there you will be able to change all your audio settings. It sounds like you may have your mic boost up to high causing unwanted feed back of mic to speakers.

---

### Post by Kuroda_Shun on 2008-09-21
thats not it. I can right click on the speaker icon and open volume control and mute it. I can still listen to what I watch but the echo goes away. about 3 hours it's un muted.

---

### Post by vermoos on 2008-09-22
if you're paranoid about rootkits install rkhunter and run:

'sudo rkhunter -c' 

also; 
'unhide proc' to check for hidden processes
'sudo zenmap' to scan your own pc's address
'ifconfig' to get the address of your box

rkhunter gives 2 red flags (both for unhide); don't know what that means, but its best to run rkhunter after a clean install because it has to learn the files it scans.

---

### Post by sharks on 2008-09-22
i also had this problem.

---

