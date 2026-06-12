---
title: "Back-Up Computer with common Home on External Drive"
date: 2017-03-03
forum: New to Ubuntu
---

### Post by mrbjnu on 2017-03-03
For fail safe reasons, i would like to have two different desktops computers (one active, one shelved) running ubuntu 16.04 LTS to point to the same external USB hard drive.  It seems this can this be done, but can it be done with each computer running under different Computer Name and/or User Name?  Would someone walk me through the steps?  My experience level is limited, old (Red Hat 8), and rusty.

---

### Post by &amp;KyT$0P# on 2017-03-03
Sure.  Just make sure that your two user accounts both have the same numeric uid and gid.  Run [FONT=Courier New]id[/FONT] in a Terminal to see your uid/gid.

---

### Post by SeijiSensei on 2017-03-04
Make sure the two computers have identical /etc/passwd, /etc/group, and /etc/shadow files.  These assign IDs to users and groups and handle standard authentication.

---

### Post by Geoffrey_Arndt on 2017-03-04
Just a short post about another alternative, that achieves file sharing if that's the main goal.   The easiest and safest way is something like Dropbox, in _combination with common local directories_ and using 7z _**local**_ encryption for sensitive data.    Just need same user ID & password on all devices.   Then can access files from phone, tablet, laptop, Pi, desktop etc.     But some are not trusting of public cloud - - so, perhaps NextCloud would be a better alternative in those cases.

---

### Post by SeijiSensei on 2017-03-04
I don't think file sharing is the point here.  I thought the OP wanted to have a spare machine around to which he could connect the /home filesystem in the event the main machine conked out.

---

### Post by mrbjnu on 2017-03-05
How do i change them if they are not the same number?
What is the significance of the numbers?

---

### Post by mrbjnu on 2017-03-05
Are you saying that both computers have to have the same password, group, and shadow?
I was hoping to put the external in the pathname like /Home/user_name/{external}.  This way
the two computers could work autonomously but only share the data on the {external} when
that individual computer was running. Maybe then i could even run a large flash drive in the
 back-up computer if there were updates or other changes needed and critical data was not.
Is any of this possible?

---

### Post by SeijiSensei on 2017-03-07
Sure, but now you're describing a different situation from what I envisioned in your original post.  Now you want to have both machines running simulaneously and sharing files between them?  If we're just talking about Linux boxes, then use NFS: [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

I'd mount the external drive outside the /home tree, say /data.  You could, if you want, create a symbolic link to the mounted drive inside /home/user to /data.

---

### Post by mrbjnu on 2017-03-08
I'm sorry for the confusion.  Maybe my question is more simple than you are expecting.

 What i am asking about is having two different computers that have their home directory as the external drive, but **_only one_** computer will be the Operational Computer at any one time.
The other will be in storage or running in test mode..._NOT_ connected to the external drive at all.
I know the external drive can be just plugged into either computer and it will be shown on the desk top as a USB icon.
But i would like the external drive to hold the data in the home directory of each computer ***only ***when it is the Operational Computer.
In other words when clicking on the desk top **Files** icon _*on either computer*_ the data from the external drive will be displayed in the Home window. (_When it is running as Operational with the external drive_)

I was hoping that this could be done with each computer having it's own unique computer name and user name.
Therefore if computer One is running as the Operational Computer _*with the external drive*_, then the home path would be /home/One/[*external data*] (as displayed with pwd) and clicking the **Files** icon would display the external drive data.
But if computer Two is running as the Operational Computer _*with the same external drive*_, then the home path would be /home/Two/[*external data*] (as displayed with pwd) and clicking the **Files** icon would display the external drive data.

I am looking for a _simple_ way (to set-up and use) to make sure that _**all** data is complete and updated_ in the _home directory_ on the Operational Computer no matter which computer is running as operational.
I hope this makes my question more clear.  It's kinda difficult to answer a question until it has been properly asked.  :(

---

