---
title: "Mail Notification 5.4"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by rosswmcgee on 2008-11-01
I upgraded to 8.10 and all is well. On my other computer I did a clean install. Both use Mail Notification 5.4 installed via synoptic mgr. Normally an icon appears on my panel when mail arrives, I read it, delete it and then update the Mail Notification 5.4, then a small brown icon with a blue arrow replaces the envelope,untill new mail arrives. I have used this system for years. On the clean install a white envelope appears when mail arrives, but when I update it, the envelope disapears, but no little brown icon with an arrow replaces it. I have used my bag of tricks to no avail. Any one else have this experience?:)

---

### Post by ugm6hr on 2008-11-01
I use 5.4 on Hardy.

I believe this is the expected action of the applet (it didn't work properly in the previous version).

Let me explain:
1. The white envelope means there are unread messages.
2. The "small brown icon with blue arrow" means that Mail Notification could not connect to your POP mail server (and generally means your internet connection has not yet been established - I only get it at first boot).  I believe the icon is actually an arrow pointing at an intray.
3. No icon means no unread mail.

Hope this clears things up for you.

---

### Post by rosswmcgee on 2008-11-02
HMMMMMMMM! You may be correct I think the brown tab with blue pointer
means no mail, If I right click on it the options are to open mail reader or update, plus properties and etc. When mail arrives the brown tab turns to and envelope with the # of msgs indicated plus pop up msg description. I read the mail, then right click and update, the envelope then returns to the brown tab, waiting for new mail. So what I have done on the new install is to go to usr/bin/evolution and change the notifier to evolution
instead of mail-notification --sm-disable in the command line. I don't like it as well but it works. I am a creature of habit, so when one app is working  differently ,on the same OS I try and figure it out, but so far no luck. Acceptance is the key to happiness, I may just have to let it go.

---

### Post by rosswmcgee on 2008-11-06
I figured it out, by clickin on the status icon in properties and checking the update
the mail status, you will get the little brown icon with the blue check mark. The difference is that Hardy uses 5.4 and Ibex uses 4.1

---

### Post by rosswmcgee on 2009-05-31
This is an update since 9.04 Jaunty is now the OS.

On my upgraded computer the brown icon with the blue arrow idicates on my taskbar that there are no new messages, When mail arrives it notifies me and changes to white along with the indication of how many msgs. there are. This is the way I like it. It also flashes a quick glimpse of the mail content. 

On my clean install 9.04 I have been unable to accomplish this. Some of the time I get mail notification and the white envelope appears, but after a period of time it will disappear, or if I read the mail and then click on update the envelope disappears. Because notification is not consistent, probabably works 50% of the time, the only way I can see for sure if I have mail is to put the Evolution icon on my task bar and actually open Evolution. Is there a way to fix this? I do not think the way mail notifier works with Evolution in 9.04 is progress, I think well enough should have been left alone. I love Ubuntu and have moved up with every new release, my concern is that perhaps change for change sake is not always for the better. I also have to put the notifier icon on the task bar so that I can click launch which helps make sure notifier is working. So instead of one icon that does it all, I have two icons plus the envelope when mail arrives.

---

### Post by vickoxy on 2009-07-14
open gconf-editor, go to apps, mail-notification, and check always-display-icon.

See picture:

---

### Post by shubhanyu on 2010-02-06
When I select "Open the Latest Message" and when I click the icon upon arival of a new mail, it gives an error: unable to open the latest message. 

Any help, respected members? There must be something to open the mail.. default client is Evolution.. please help.

---

### Post by sefs on 2010-12-02
This is exactly my situation. 

Which was mail-notification icon disappears when there is no mail.

@vickoxy your solution works perfectly.  Thank you for that.

One other question... I want to replace the default icon with a nicer one.

Usually on my desktop I would replace the stock_inbox.png icon which is the one mail-notification uses.  This works for me in lucid on my desktop. But now I am trying it on my laptop it still uses the old icon (brown box with blue arrow).  Is there a way to change this icon.  

Thanks.

---

