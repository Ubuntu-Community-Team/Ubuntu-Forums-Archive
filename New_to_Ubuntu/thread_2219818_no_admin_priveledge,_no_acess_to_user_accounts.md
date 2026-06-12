---
title: "no admin priveledge, no acess to user accounts"
date: 2014-04-25
forum: New to Ubuntu
---

### Post by bootofbeer on 2014-04-25
*Now it appears that is no longer possible. Help please don't often need to use admin priveledges but recently I wanted to and found I could not as users was greyed out. I am currently using 14.04 lts and have recently loaded another instance of 13.10. All seem to have the same greyed out on users.My wife has 13.04 and that works just fine. Does this mean we can only have one user per system in future? I used to allow my wife access on my machine by giving her user priveledges. *

---

### Post by deadflowr on 2014-04-25
Did you remove your first user or change it from admin to standard at some point.
First user is always an admin, always has been.

You can make your user an admin, quite simply.
But you'll need to boot into recovery mode.
This is for resetting apassword, but it's actually helpful to do what I suggest
(as well as it has pictures, which are extremely helpful)
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

Now when following the link's guide, after you use the mount command, which reloads the file system read/write, instead of following the rest which is all about changing password, run this command
```
adduser yourusernamehere sudo
```
This will put the user into the sudo group which will give you admin ability.
type exit  and you should be good to go.
Good Luck.

---

### Post by bootofbeer on 2014-05-02
I tried that and must have done it correctly as password was changed successfully but still cant get into users on the settings screen It is greyed out and hangs if you try to access. I can't format a drive I wanted to clean up and if I go to permissions on the drive it says I am not the owner and it belongs to root.Help1 now what do I do?

---

### Post by deadflowr on 2014-05-02
> **bootofbeer said:**
> I tried that and must have done it correctly as password was changed successfully but still cant get into users on the settings screen It is greyed out and hangs if you try to access.

Is it hanging when you click on the lock symbol?

---

