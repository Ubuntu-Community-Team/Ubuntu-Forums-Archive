---
title: "Guest Account?"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by skymera on 2008-06-04
Hi,

My brother needs to do some research for his school work.
I didn't want him using my account so i created a new one called Guest.

How do i make it so the new Guest account can ONLY access Guest home and not mine aswell?

Can i limit which programs can be launched and also disable the terminal?

Thanks.

---

### Post by SunnyRabbiera on 2008-06-04
you can edit profiles with the users and groups app, I assume you know where it is as you set up the second account.
anyhow select your brothers new profile, and go to properties, then to the user privileges tab.
you can edit the profile in there.

---

### Post by Paqman on 2008-06-04
> **skymera said:**
> 
Can i limit which programs can be launched and also disable the terminal?


Unless you give him sudo access there's not much he can do with the terminal anyway. Just set up his account without the "administer the system" privilege ticked. That'll lock him out of the whole admin menu and prevent him from running anything as root.

If you want to go really crazy Policy Kit now gives you a pretty fine-grained level of control over user's privileges.

---

### Post by skymera on 2008-06-04
Thanks for both replies :)

---

### Post by mister_pink on 2008-06-04
> **skymera said:**
> Thanks for both replies :)
If you want other people to not even have read access to your home folder you'll need to change the permissions on it so its not world readable. Navigate to /home, get the properties up for your folder and go to permissions. The last drop down box should be changed to none, then click apply permissions to enclosed files. Done.

---

