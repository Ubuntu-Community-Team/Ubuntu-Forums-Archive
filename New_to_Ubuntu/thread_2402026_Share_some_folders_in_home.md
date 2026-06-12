---
title: "Share some folders in home"
date: 2018-09-25
forum: New to Ubuntu
---

### Post by weirdygeekpsych on 2018-09-25
How can I share some folders in home.

Making it simple: 1 = adminstrator account, 2 = standard account

Now some folders in 1 home needs to be shared with 2.

I added sudo add group user 2 in 1 terminal

Now navigated to the 1 folder properties checked group list , still there is no presence of 2 in that list instead I see lot of other groups.

Also I tried to change the permission of particular folder in home of 1 in group section by giving read and write.

Once I close and reopen the permission dialog box, it still shows access files and not the thing I set earlier.

Why I can't share my folders?

I want to go the manual way, dont suggest samba

---

### Post by TheFu on 2018-09-25
Are they on the same computer or different computers?  What type of computers - which OS are they running?
Is there a central user authentication setup?

Regardless of the your answers, it isn't wise to share directories actually stored inside a HOME.  It is better to setup a directory elsewhere to hold that data and share it with the team.  This is for a number of reasons, some just for housekeeping and others for security reasons.

And samba might be the best solution. Can't tell without some facts first, but rest assured samba is seldom my first choice for this stuff.

---

