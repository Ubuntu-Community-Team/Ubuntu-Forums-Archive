---
title: "Problem with F-Spot"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by Dlizard on 2008-05-31
I can't burn my pictures to a CD using F-Spot. I click in "Photo", "Export to", and "CD...". A box called "Create CD pops up" showing the photos I selected. Everything looks OK, but when I click in the bottom "Export" the box "Transferring Pictures" opens up with this message on the downloading progression bar: "Error Transferring". Just above, in the same box there is a s cryptic message like: "System NullReferenceException: Object reference not set to an instance of an object at FSpotCDExport.UniqueName (Gnome.Vfs.Uri path, System.String.shortname... etc (I cannot copy and paste, and the message is pretty long, so I cut it here). 

As a beginner I am having a hard time with Ubuntu. Regarding pictures, I tried gThumb before, and got a differente error message that I posted on the forum (no answer so far). According to the book I bought to help with the MS => Linux transition, "Ubuntu for Non-Geeks", everything was supposed to be nice and easy. However, the reality is that things are getting pretty ugly as time goes by. 

I would appreciate any help.****

---

### Post by FuturePilot on 2008-05-31
Looks like you ran into this bug
[https://bugs.launchpad.net/f-spot/+bug/216997]("https://bugs.launchpad.net/f-spot/+bug/216997")

It's been fixed upstream so an update to fix it in Ubuntu should just be a matter of time. :)

---

### Post by Dlizard on 2008-05-31
> **FuturePilot said:**
> Looks like you ran into this bug
[https://bugs.launchpad.net/f-spot/+bug/216997]("https://bugs.launchpad.net/f-spot/+bug/216997")

It's been fixed upstream so an update to fix it in Ubuntu should just be a matter of time. :)

Hi, FPilot. I really appreciate your attention. Now, excuse my ignorance (well, I am absolute beginner  ), but what does the term "fixed upstream" mean in this context? Do you have any idea of how long it takes on average for a problem like that to be really fixed (I mean, not "upstream", but in our real-common-user-ubuntu-world)?  

Regards.

---

### Post by FuturePilot on 2008-05-31
Since Ubuntu is really just a bunch of separately developed applications packaged into a nice distribution, upstream refers to the version of the application from the F-Spot developers. So when I say it's been fixed upstream I mean that the F-Spot developers have released a new version with a fix for this bug in it. Now the people responsible for packaging F-Spot for Ubuntu just have to package up the new version and distribute it to the Ubuntu updates repository. The bug has been marked "Fix Committed" which means a version should be available for testing. (Packages need to be tested before before being allowed to be placed in the updates repository)
The update could take anywhere from a few days to a few weeks before it comes through.

I hope that explains it, I tried my best. ;)

---

### Post by commonplace on 2008-06-05
Actually, there's already a way to get the update, and it's very simple, too!

Open F-Spot, and go to Edit->Manage Extensions. Click on the Folder Export extension and hit the 'Disable' button. Once it's disabled, click on the Install Add-ins button. Hit 'Refresh' and then select the new Folder Export extension (it'll be version 0.4.3.1 instead of 0.4.3.0). Close F-Spot and re-open F-Spot and try your export again; it should work.

/Kevin

---

### Post by Dlizard on 2008-06-05
> **commonplace said:**
> Actually, there's already a way to get the update, and it's very simple, too!

Open F-Spot, and go to Edit->Manage Extensions. Click on the Folder Export extension and hit the 'Disable' button. Once it's disabled, click on the Install Add-ins button. Hit 'Refresh' and then select the new Folder Export extension (it'll be version 0.4.3.1 instead of 0.4.3.0). Close F-Spot and re-open F-Spot and try your export again; it should work.

/Kevin

Hi, I appreciate you attention. I tried your suggestion but unfortunately it didn't work. Got the same error message. BTW, I burned the pictures to a CD using a program called K3B. gThumb is not working either.

Tx.

---

### Post by MeTylerDurden on 2008-06-06
> **Dlizard said:**
> I can't burn my pictures to a CD using F-Spot. I click in "Photo", "Export to", and "CD...". A box called "Create CD pops up" showing the photos I selected. Everything looks OK, but when I click in the bottom "Export" the box "Transferring Pictures" opens up with this message on the downloading progression bar: "Error Transferring". Just above, in the same box there is a s cryptic message like: "System NullReferenceException: Object reference not set to an instance of an object at FSpotCDExport.UniqueName (Gnome.Vfs.Uri path, System.String.shortname... etc (I cannot copy and paste, and the message is pretty long, so I cut it here). 

As a beginner I am having a hard time with Ubuntu. Regarding pictures, I tried gThumb before, and got a differente error message that I posted on the forum (no answer so far). According to the book I bought to help with the MS => Linux transition, "Ubuntu for Non-Geeks", everything was supposed to be nice and easy. However, the reality is that things are getting pretty ugly as time goes by. 

I would appreciate any help.****

**_[FONT="Trebuchet MS"][SIZE="4"][COLOR="Orange"]I also got the same error message, but first wanted to say that all went well up to "export to cd".   This is my first time editing pictures-redeye, black and white, crop etc...   and I absolutely love it...    but when I went to save all my diligent work to cd it failed..        but then everything I have ever put to cd has failed so maybe someone out there is just overprotective of people getting things done in a lifetime !!GeeeSH[/I][/COLOR][/SIZE][/FONT]_**

---

