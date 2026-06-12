---
title: "Firewall help needed"
date: 2012-01-14
forum: New to Ubuntu
---

### Post by cliveT on 2012-01-14
Hi guys - I`m thinking "Firewall"

What do I need to do? 

I turn it on using gufw but I don`t add any rules or change anything else, I am presuming that the ufw knows what to do! So when I log off and then return and log on again the firewall is showing turned off again - what do I need to do please, I have searched and read the info the links give but I don`t really know anymore from them!

I just want a simple set up where the firewall is on and doing its job.

Please help

regards

Clive

---

### Post by BlinkinCat on 2012-01-14
Hi,

You could start here -

  [https://wiki.ubuntu.com/UncomplicatedFirewall](https://wiki.ubuntu.com/UncomplicatedFirewall)

---

### Post by uRock on 2012-01-14
I am not sure why GUFW is resetting to disabled, but you open a terminal and run the following command to enable UFW, which is the same firewall. 
```
sudo ufw enable
```
The following can be run at any time to show the tatus of the firewall.
```
sudo ufw status
```
I just enabled my firewall via GUFW and after closing it, it appears to be "off" when I reopen it. Once I unlock GUFW I can see that the firewall is in fact enabled. I think it is odd that wrote the latest version of GUFW in such a manner.

---

### Post by cliveT on 2012-01-14
I`m using 11.10

I first have to unlock the firewall then enter my password and click "Authenticate" then I turn on the firewall!

Then if I close the GUFW dialog box or indeed log off, then log on or just check the ufw status again - it shows status firewall "off"again.

I don't understand this - if I give my permission then turn on the firewall -should it not "stay" on!

---

### Post by BlinkinCat on 2012-01-14
I'm sorry if I wasn't much of a help - :( I misread your needs.

---

### Post by uRock on 2012-01-14
> **cliveT said:**
> I`m using 11.10

I first have to unlock the firewall then enter my password and click "Authenticate" then I turn on the firewall!

Then if I close the GUFW dialog box or indeed log off, then log on or just check the ufw status again - it shows status firewall "off"again.

I don't understand this - if I give my permission then turn on the firewall -should it not "stay" on!
It should stay on. I am using 11.10 as well. I just logged out, then back in again and it is acting properly, though I still find it odd that it does not show the proper status as "on" until I unlock it.

---

### Post by duke.tim on 2012-01-14
try doing what urock said

```
sudo ufw enable
```

Even if you log out that should keep ufw enabled.

---

### Post by cliveT on 2012-01-14
I just enabled  my firewall via GUFW and after closing it, it appears to be "off" when I  reopen it. Once I unlock GUFW I can see that the firewall is in fact  enabled. I think it is odd that wrote the latest version of GUFW in such  a manner. 		                   		 		 			  			 				 					Attached Thumbnails 					 					 [[IMG]http://ubuntuforums.org/attachment.php?attachmentid=210864&stc=1&thumb=1&d=1326579330[/IMG]]("http://ubuntuforums.org/attachment.php?attachmentid=210864&d=1326579330")    [[IMG]http://ubuntuforums.org/attachment.php?attachmentid=210865&stc=1&thumb=1&d=1326579330[/IMG]]("http://ubuntuforums.org/attachment.php?attachmentid=210865&d=1326579330")  

Yes I am finding the same when I unlock the gufw it does show that the firewall is on - so it must be OK, its just a bit misleading though -don't you think?

---

### Post by cliveT on 2012-01-14
uRock,uRock.tim - yes ive done that in command line and all is well_ _great thanks guys
[U]
[/U]

---

### Post by uRock on 2012-01-14
> **cliveT said:**
> Yes I am finding the same when I unlock the gufw it does show that the firewall is on - so it must be OK, its just a bit misleading though -don't you think?

I agree. I will search to see if there is a bug report already made for this.

---

### Post by cliveT on 2012-01-14
lovely, thanks for that.:D

---

### Post by BlinkinCat on 2012-01-14
```
sudo ufw status
```does return "active" if firewall is operating correctly although I agree that there appears to be room for improvement.

---

### Post by uRock on 2012-01-14
I have created a bug report for this issue. Members, please click "this bug effects you". [https://bugs.launchpad.net/ubuntu/+source/gui-ufw/+bug/916624](https://bugs.launchpad.net/ubuntu/+source/gui-ufw/+bug/916624)

---

### Post by sammiev on 2012-01-14
That is normal and has been like that forever. As soon as you add the password to make changes, it shows it's active.

---

### Post by uRock on 2012-01-14
> **sammiev said:**
> That is normal and has been like that forever. As soon as you add the password to make changes, it shows it's active.

I don't think the older versions were as likely to confuse because they didn't have the On/Off slider button.

---

### Post by costales on 2012-01-18
Hi! :) I'm a Gufw developer.
ufw need the password for know the current status, then I think Gufw need the password too for know the current status.
I think the Gufw behavior is right :O
Best regards and thanks.

---

### Post by mcduck on 2012-01-18
> **costales said:**
> Hi! :) I'm a Gufw developer.
ufw need the password for know the current status, then I think Gufw need the password too for know the current status.
I think the Gufw behavior is right :O
Best regards and thanks.

I have to agree with this. Firewall configuration and also the status of the firewall, are administation tasks. Which is why GUFW requires admin password before you can change the settings, or even see what the current status.

...on the other hand I do also understand that this could be confusing from a typical home user's perspective. So even though I see the current behaviour as correct, perhaps showing the firewall status (enabled/disabled) but not any rules or other detailed information unless the GUFW tool is unlocked would be a good idea. That would require some changes in the GUFW interface design to work well, though. (maybe just show a Window to tell you that the firewall is enabled, and a button for unlocking, and only once unlocked bring up the current GUFW window.)

---

