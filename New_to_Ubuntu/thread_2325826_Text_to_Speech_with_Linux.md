---
title: "Text to Speech with Linux"
date: 2016-05-25
forum: New to Ubuntu
---

### Post by Norman_L_Bliss on 2016-05-25
[h=3]I am trying toinstall Text to Speech software and am flowing this video (FreeText to Speech with Linux – YouTube). I got this error:[/h]norman@norman-GA-770T-USB3:~$apt-get install festival


E: Could not openlock file /var/lib/dpkg/lock - open (13: Permission denied)


E: Unable to lockthe administration directory (/var/lib/dpkg/), are you root?


How can I fix this? 
Thank you

---

### Post by Impavidus on 2016-05-25
You have to run that command as root:```
sudo apt-get install festival
```

---

### Post by vipulkumar7 on 2016-05-25
Since you are not a root user mode, $ sign indicates you are into a normal user. > norman@norman-GA-770T-USB3:~_**$**_
so kindly use

```
 sudo apt-get update; sudo apt-get install festival 
```

---

### Post by Norman_L_Bliss on 2016-05-26
Finally I have itworking. I put together a page on text to speech. If you see anychanges I need to make let me know. thank you [http://www.backyardpit.us/text-to-speech/](http://www.backyardpit.us/text-to-speech/)

---

### Post by Mark Phelps on 2016-05-26
Interesting page -- but the slogan (for the working poor) is not one I would have chosen to typify Ubuntu.

The fact that Ubuntu is free is really (IMHO) a minor part of its attractiveness.  Much more important to me (and to many other Ubuntu users) are the facts that it is **_NOT _**MS Windows, does not come with the preinstalled Win10 "spyware", and does not force you into running MS stuff like the Windows Store apps and second-rate apps like Edge.

Maybe (it's just a suggestion and I'm sure others have better ones), you should think about changing the slogan to something like "Celebrating freedom from Microsoft" -- to give it a more positive feel, and more appropriate for those of us who are not "workin" or "poor".

---

### Post by Norman_L_Bliss on 2016-05-29
[COLOR=#000000]Got it, thanks. "Celebrating Freedom From Microsoft"[/COLOR]

---

