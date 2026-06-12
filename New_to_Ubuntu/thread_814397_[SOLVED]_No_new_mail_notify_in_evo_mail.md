---
title: "[SOLVED] No new mail notify in evo mail?"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by discmaster on 2008-05-31
I am using Evolution 2.22.1.1, which came installed with 8.04. Following the directions from evo mail help file...There is no "New Mail Notification" tab/button/other that I can see.

What can I do to get informed of new mail arriving?>  

Since Evolution 2.2, a panel notification applet via D-BUS exists. Evolution itself is only able to play a sound file or to beep. Go to "Edit | Preferences | Mail Preferences | General | New Mail Notification". Note that esound must be running to be able to hear your sound file. Evolution 2.12 will support a system tray icon to inform you about new messages. 

---

### Post by sayakb on 2008-05-31
While closing, Close Evolution by pressing Ctrl+W to keep it running in background.

---

### Post by discmaster on 2008-05-31
> While closing, Close Evolution by pressing Ctrl+W to keep it running in background. Forgive me, but I don't quite understand. I am looking for a setting in evo mail that I can select a sound file/ play a beep, etc., to notify me of new mail. I can't find any settings in the preferences that allow me to do that. Am I missing something here?

Thanks!

---

### Post by discmaster on 2008-05-31
EUREKA!!! I have found how to do this!!!

This is how - **Message> Create Rule> Filter on Recipients **

I have several email identities set up on EVO, so I had to create filters for each one. But, it is working! I am able to select a different wav for each identity, so I can further narrow down which mail acct. I am receiving mail on.


Why EVO doesn't tell you how to do this is beyond me... :confused:

This is what is in the Evo FAQ -> Since Evolution 2.2, a panel notification applet via D-BUS exists. Evolution itself is only able to play a sound file or to beep. Go to "Edit | Preferences | Mail Preferences | General | New Mail Notification". Note that esound must be running to be able to hear your sound file. Evolution 2.12 will support a system tray icon to inform you about new messages. 


That doesn't work, at least not in my settings. Anyway, problem solved!!! I hope others are able to benefit from this.


Cheers, 

discmaster :)

---

