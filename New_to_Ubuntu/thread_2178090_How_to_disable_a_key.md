---
title: "How to disable a key"
date: 2013-10-01
forum: New to Ubuntu
---

### Post by ex1t on 2013-10-01
Okay so I am having an issue with my keyboard on my laptop, it's going faulty, there is a certain that is constantly being pressed and at first using xmodmap has helped, but it seems as if the issue is still going on.  I have come to the understanding it was whatever key keycode 112 is, which for me appears to be pageup - even though when I right click the highlighted menu goes down.  So I used  ```
xmodmap -e 'keycode 112='
``` and the issue continued, so I did the following -again- to find out what was wrong;  ```
xev
``` and recieved this output ```
 KeyPress event, serial 80, synthetic NO, window 0x5000001,     root 0x262, subw 0x0, time 118525837, (-208,178), root:(1031,685),     state 0x10, keycode 112 (keysym 0x0, NoSymbol), same_screen YES,     XLookupString gives 0 bytes:      XmbLookupString gives 0 bytes:      XFilterEvent returns: False 
```  I have no idea why it constantly is doing this, maybe it is actually that the key is stuck (even though I removed the key itself and tried to clean it) but if I removed what it should do than I don't know how it's still interacting with me, maybe someone can enlighten me on this situation.   thanks in advance~

---

### Post by Vakman on 2013-10-02
Try ```
xmodmap -e "keycode 112 = 0x0000"
```

---

### Post by ex1t on 2013-10-02
> **Vakman said:**
> Try ```
xmodmap -e "keycode 121 = 0x0000"
```

I used this (but keycode 112 instead lol) and so far for the past 3 hours, I have had no issues. Really got my idea that this may of been the more proper way that I should of followed. Thanks, hopefully it will work continuously, I will update this thread with an edit later on to say if it has fully fixed the issue I have had. 

Thanks again;

ps : Ubuntu fixed my computer a ton, Windows **was** destroying it. So, big ups to the devs, thanks a ton. :)


Edit: This has been the successful fix for the entire issue, has been a good amount of time since doing that with no rebooting or anything else, and my problem has been solved. :) Thanks for letting me know how to use xmodmap properly lol

---

### Post by Vakman on 2013-10-12
Haha, no worries, sorry about the typo but glad you noticed it.
Mark thread as solved :)

---

