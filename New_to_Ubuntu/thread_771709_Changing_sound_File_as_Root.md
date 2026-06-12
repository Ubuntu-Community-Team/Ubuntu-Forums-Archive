---
title: "Changing sound File as Root"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by pardesi on 2008-04-27
i want to add some files at usr/share/sound ....The tutorial asks me to eenter as root ...how do i do that?

---

### Post by Tatty on 2008-04-27
In ubuntu it is not recommended to log in as root because doing so represents a massive security risk.

What you need to do is simply preface the commands with sudo.  This gives you temporary root powers to allow you to make changes to your system.

*For example* if you were trying to make a directory in root and tried ```
mkdir /test
``` It would fail because you do not have persission to add a directory to root.  To add this directory you would need to do ```
sudo mkdir test
``` It would then ask you for your password (the one you use to login) then it would process the command as root.

If you are still confused then please give us a link/post the instructions you are following.

---

### Post by pardesi on 2008-04-27
i want to copy some sound files as instrcuted [here]("http://www.howtoforge.com/mac4lin_make_linux_look_like_a_mac_p4")
can u tell me in detail please how to copy the files to the /usr/share/sounds

---

### Post by Tatty on 2008-04-27
Ok ive had a look at the instructions and the easiest way for you to do this is to open a terminal and type ```
gksu nautilus
```

This will open a file browser which has root privilages.  Be careful you dont accidentally change anything you dont mean to in this window as you have full access to the system here.

Then just drag and drop the files to where you need them.

---

