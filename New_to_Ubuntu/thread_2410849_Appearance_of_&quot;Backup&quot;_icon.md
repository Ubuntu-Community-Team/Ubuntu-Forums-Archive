---
title: "Appearance of &quot;Backup&quot; icon"
date: 2019-01-21
forum: New to Ubuntu
---

### Post by redpoppet on 2019-01-21
Hi everybody
My ubuntu 18.04 system had recently started to take longer to shutdown.  It happened once before and I identified the culprit as java that was running following an install of freenet that I was mucking around with.  Uninstalled freenet then all good.  I am not sure of the reason for the slower shutdown presently however.  What I have noticed appear that wasn't there before, is a small icon in the top right of screen near the network icon.  It looks not unlike my "files" icon, that is, a filing cabinet.  If I left or right click on it a box opens up with a bar that says "backing up".  This then gives way to  "Install packages" "In order to continue, the following packages need to installed:  duplicity".

I am not sure if this is slowing my shutdown but I'd like to know what this program is and get it off my screen.  I haven't installed "duplicity".  I should say that my slow shutdowns have just appeared witout me being able to identify anything that I have done such as installing something.  But that is a separate issue to my question.

Thanks for any responses that people may offer.

---

### Post by deadflowr on 2019-01-21
It is what is says it is, the default backup utility program Ubuntu uses.
You can open the program Backups from overview and set the what where and basic when (ie, daily or weekly) of the backups from there, as well as restore from older backups and run backups on demand.
I've not seen it want to run on shutdown, though. That's odd. Perhaps you set something without realizing it at some point.

If you do not want to use the default backups, then you can remove it, the program is called deja-dup. (But listed as Deja Dup Backup Tool in Software)

Plenty of user do remove it without fanfare or issues and replace it with something else.
What they replace it with is almost always a personal choice.
but definitely replace it with something.
Backups should be considered a requirement.

Here's a listing of various backup utilities available on Ubuntu.
[https://help.ubuntu.com/community/BackupYourSystem#Backup_Utilities]("https://help.ubuntu.com/community/BackupYourSystem#Backup_Utilities")
As well you can run a quick search of the forums for a few threads on the topic.

---

### Post by redpoppet on 2019-01-22
Thanks for that reply.  So that's what it is!  I have no idea why it is making it presence seen now on the top bar.  I haven't used back up before but I will.  Thanks for the heads up.

---

