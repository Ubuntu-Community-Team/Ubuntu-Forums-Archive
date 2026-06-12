---
title: "[SOLVED] Permissions, Group, Owner, etc..."
date: 2008-08-31
forum: New to Ubuntu
---

### Post by solaceinsilence9 on 2008-08-31
Allllright, so im trying to set up some permissions for a partition on my hard drive so that only I can have read/write access and other can only read. I have the partition automatically mounted as a folder in Ubuntu located in my / folder. So, i went ahead and hit Alt+F2 to open up Run and typed gksudo nautilus so i could have root access... Went to the partition mounted as a folder and opened up the permissions tab under properties. I set each option as I wanted (Owner, Group, Other) and applied the changes. 

My problem is that the only way I can get the result that I want, I have to set read/write permissions for "Other". If I try to set read/write for "Owner" or even "Group" I still dont get read/write permission. By setting read/write for "Other" will I give other users the ability to read/write also? Or will that only affect my username? What is the differences between "Owner", "Group" and "Other"?

---

### Post by porchrat on 2008-08-31
If a file has group = bob's group and user = bob

Owner = bob

group = any user who belongs to bob's group (you can check that under the users sections of "system --> administration"

other = EVERYONE else

So yes changing the permissions of "other" would allow other people to access that drive

---

### Post by porchrat on 2008-08-31
Why don't you use the command line

type:

```
sudo chmod u=wrx name_of_mount_point_of_drive
sudo chmod og-wrx name_of_mount_point_of_drive
```

that should sort you out so that only the user that owns the driver can read it.

to make your user the owner type:
```
sudo chown USERNAME:USERNAME name_of_mount_point_of_drive
```

---

### Post by cwsnyder on 2008-08-31
You can also set permissions under your menu System >> Administration >> Users and Groups.  You may have to unlock to get permission to change the rights on this folder, if you are not listed as the Owner.  I would assign a Group name which is unique to the folder and make yourself as the owner and part of that group along with **root**.

Under Terminal, type > sudo chown *options* to change the owner or > sudo chgrp *options* to change the group.  Check man chown or man chgrp for more information on setting the options.

cwsnyder

---

### Post by solaceinsilence9 on 2008-08-31
> **porchrat said:**
> If a file has group = bob's group and user = bob

Owner = bob

group = any user who belongs to bob's group (you can check that under the users sections of "system --> administration"

other = EVERYONE else

So yes changing the permissions of "other" would allow other people to access that drive

Ok then so if my username is 'benjamin' and i belong to the group 'benjamin' and I want to give myself read/write permissions and all others just read permissions I need ONLY to give read/write permissions to "Owner" and "Group" making sure that benjamin is the "Owner" selected, and under "Other" just give read permissions. Correct?

If so, thats what I did, BUT I still am seeing the padlock on the folders in the partition... Which is strange because when I change "Others" to read/write I can do whatever I want... 

Further, I checked my username in the Groups area you mentioned and made sure that I am in the correct group...

Whats the deal?

---

### Post by cwsnyder on 2008-08-31
Is root a member of 'benjamin'?  Does owner 'benjamin' have Execute rights on the folder?  I believe Execute rights are needed on a folder to create new folders or files in the folder.

cwsnyder

---

### Post by solaceinsilence9 on 2008-08-31
> **cwsnyder said:**
> Is root a member of 'benjamin'?  Does owner 'benjamin' have Execute rights on the folder?  I believe Execute rights are needed on a folder to create new folders or files in the folder.

cwsnyder

root is a member of 'benjamin'... I have both the "Owner" and "Group" set like this:

Folder Access: Create and Delete Files
File Access: Read and Write

and "Other" set like this:


Folder Access: Access Files
File Access: Read-Only

Is there a way to set permissions in terminal? I thinking that might be easier than trying it using GNOME

---

### Post by ds[de] on 2008-09-01
> **solaceinsilence9 said:**
> Is there a way to set permissions in terminal? I thinking that might be easier than trying it using GNOME

Of course there is, it's called *chmod*.

I just stumbled upon a link in another thread 
```
http://www.zzee.com/solutions/how-to-use-chmod.shtml
```
so kudos goes to the original poster :-)

Issueing 'man chmod' in a terminal will give you all the information you need (and yes, doing things in a terminal is faster most of the time).


Regards,
ds[de]

---

### Post by solaceinsilence9 on 2008-09-01
> **'ds[de] said:**
> Of course there is, it's called *chmod*.

I just stumbled upon a link in another thread 
```
http://www.zzee.com/solutions/how-to-use-chmod.shtml
```
so kudos goes to the original poster :-)

Issueing 'man chmod' in a terminal will give you all the information you need (and yes, doing things in a terminal is faster most of the time).


Regards,
ds[de]

Oh mann, thanks so much! I would rather use terminal for most things in Ubuntu, but Im new to Linux so I've been learning bits and pieces here and there as I need.

---

