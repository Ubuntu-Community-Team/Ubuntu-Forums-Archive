---
title: "[SOLVED] Re-Enabling Administrator privilage"
date: 2008-09-29
forum: New to Ubuntu
---

### Post by cookiemonster2008 on 2008-09-29
I recently installed Ubuntu 8.04, and as I was looking around I noticed my user (the only user for the system) had "Administer the system" checked off in the privileges section. I had only heard/read a little about linux and I was under the impression that being logged in as admin/root were bad things. So I unchecked this box.

Now I'm noticing I can't do as much as before, such as changing the date/time. When I try to access this everything is grayed out except the "unlock" box. When I try to unlock it (which previously would just ask me to type in my password again and then worked fine) it sits for a bit, then I get the message "Could not authenticate. An unexpected error has occurred."

After a little reading it seems to me that maybe I should have NOT unchecked the "Administer the system" box. I found [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)  "Allowing other users to run sudo" I tried using the command as follows
```
sudo adduser jeff admin
``` 

and get the following error "jeff is not in the sudoers file.  This incident will be reported."

Can anyone shed a little light on what I should do, or what I may be doing wrong?

Thanks

---

### Post by wolfen69 on 2008-09-29
go to system>administration>users and groups. click unlock, then highlight your name and click properties. go to the user privileges and make sure administer the system is checked, and any other things you may want.

---

### Post by Pro-reason on 2008-09-29
I'm afraid you are a casualty of Ubuntu's approach to technical matters.  Ubuntu and GNOME have a policy of dumbing things down for newbies.  Unfortunately, this means that instead of giving you precise information (that the box that you unticked was for giving the user the ability to run things as root via the sudo command, and that without this ability no admin tasks could be carried out), it decided to imply that the box actually made your user an administrator all the time.

Unless you have another user in the sudoers list, you cannot fix the system now.  Unless... you boot from a live CD and fix it from there.  If you Google for it, I'm sure you can find a guide.

> **wolfen69 said:**
> go to system>administration>users and groups. click unlock, then highlight your name and click properties. go to the user privileges and make sure administer the system is checked, and any other things you may want.

But how will that work?  How can he unlock it if he is not a sudoer?

---

### Post by cookiemonster2008 on 2008-09-29
I tried going into System->Administration->users and Groups and "unlocking" but I get the same error as I mentioned above "Could not authenticate. An unexpected error has occurred."

Thankfully I still have my Live CD (tried to give it away to get a co-worker hooked but Windows has to strong of a hold on him). I'll try and see what I can find, thanks Pro-reason I'll definitely do some research before un-checking any more random boxes.

---

### Post by Pro-reason on 2008-09-29
This might help: [http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo).

---

### Post by cariboo on 2008-09-29
The physcocats tutorial is excellent if you have a problem with sudo, but the OP only needs to add himself to the admin group to be able to use sudo again. Restart your computer in recovery mode and select the root prompt then at the prompt type:

```
adduser username admin
```

Where username is your user name.

Jim

---

### Post by aysiu on 2008-09-29
Well, the Psychocats tutorial actually covers all aspects of fixing sudo (messed up /etc/sudoers, user not belonging to *admin* group).

To the OP, after you get this fixed, maybe you should vote for this Brainstorm idea:
[Idea #11107: Users and Groups should always make sure at least one user is in the admin group ](http://brainstorm.ubuntu.com/idea/11107/)

---

### Post by cookiemonster2008 on 2008-09-29
I just finished fixing the problem, thanks to the physcocats tutorial. It was simply a problem of adding myself to the Admin group. Thanks for all your help guys.

I am definitely going to vote for that brainstorm idea as well!

---

