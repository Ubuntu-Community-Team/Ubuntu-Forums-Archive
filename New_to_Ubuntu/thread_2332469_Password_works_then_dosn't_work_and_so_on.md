---
title: "Password works then dosn't work and so on???"
date: 2016-08-01
forum: New to Ubuntu
---

### Post by Franklin_J on 2016-08-01
I just reinstalled Ubuntu on double boot with Windows .  I set a good password which works fine to login to Ubunto at bootup, haowever, I just attempted to Install VCL MEDIA PLAYER from Ubuntu Software and used the same password for authentication and it failed failed failed.  What am I doing wrong???

---

### Post by kyrithis on 2016-08-01
Just to make sure, try using "su [YourUserName]" and then try and run the command.

---

### Post by deadflowr on 2016-08-01
Do you belong to the proper groups that allow for administrative functions?
open a terminal and run:
```
id
```
and see if your user belongs to the sudo group.

Not that that is the answer, but at least we can eliminate it if it is not.

---

### Post by sixgunSal on 2016-08-01
hello,   I've had the same problem the last few days.  I've just reinstalled Ubuntu when I try 3 times and have to start over.  I did that  "id" command but I'm not sure what it's telling me.  Is there a site or book or somewhere to learn this so I can look it up b4 asking dumb questions. Maybe a book for ubuntu for dummies...or maybe another one you might recommend.  thanks.

---

### Post by mook765 on 2016-08-01
The password is case sensitive. You would enter the wrong password, when caps lock is switched on...
Just an idea...
There are no dumb questions, just dumb answers...

---

### Post by yancek on 2016-08-01
>  					I just reinstalled Ubuntu on double boot with Windows .  I set a  good password which works fine to login to Ubunto at bootup

Is this a password you need to boot, BIOS password?  Or is it the password you created for the primary user you created during the install?  The second  one is what you would use as the primary user has root/administrator privileges.  What exactly does 'fialed' mean?  You need to be more explicit about what happens

---

### Post by Franklin_J on 2016-08-01
Hi thanks for  your response;  Actually I'm the only user/owner/administrator. Now I'm completely locked out of Ubuntu and Windows 10. Both OSs do not acknowledge my passwords period.  i'm currently using  a neighbors computer.  

Perhaps I should explain that  I have been subject of a remote takeover which I have been battling for the last week or so.  Yesterday I began to download and study advanced encryption technology and was locked out of both OSs.  I'm currently doing a 'diskpart clean all' and a clean double install.  Thanks again.

---

### Post by oldos2er on 2016-08-01
> Both OSs do not acknowledge my passwords Is this a laptop or desktop? Have you tried a different keyboard, if possible?

---

