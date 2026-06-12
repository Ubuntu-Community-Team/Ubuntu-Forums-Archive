---
title: "sudo not working.... need help"
date: 2015-10-22
forum: New to Ubuntu
---

### Post by Abhishek_Rai on 2015-10-22
i was trying to edit my bash profile , and suddenly i got this message on screen. please help me my project stuck due to this. i am new to ubuntu. i attached the snap off that msg. 
[ATTACH=CONFIG]265103[/ATTACH]

---

### Post by howefield on 2015-10-22
Try this thread.

[http://ubuntuforums.org/showthread.php?t=2220910](http://ubuntuforums.org/showthread.php?t=2220910)

PS. It is usually better to copy/paste the terminal output into your post between code tags than it is to post an image of it..

---

### Post by buzzingrobot on 2015-10-22
Don't know what you did with .bash_profile to impact sudoers, but simply editing it would have no impact.  

Now, "su-" wasn't found because there is no command spelled "su-".  You were probably trying to use "su -" -- note the space -- but that won't work on Ubuntu because Ubuntu and its spins do not create a superuser aka root. Per 'man su':  > The su command is used to become another user during a login session.
       **Invoked without a username,** su defaults to becoming the superuser.

You don't need to use 'sudo' to edit or otherwise manipulate files in your home directory -- you own the files -- so the 'sudo' in "sudo nano ~/.bash_profile" is not needed. It should, though, just work as usual:  Prompt for a password and then go on.

---

### Post by mcduck on 2015-10-23
> **buzzingrobot said:**
> You don't need to use 'sudo' to edit or otherwise manipulate files in your home directory -- you own the files -- so the 'sudo' in "sudo nano ~/.bash_profile" is not needed. It should, though, just work as usual:  Prompt for a password and then go on.
It would work for editing the file, but it would also change the ownership of the ~/.bash_profile to root, which definitely wouldn't be a good thing. In worst case that user to not be able to log in any more.

So I'd rather say that you *shouldn't use* sudo for your own files than that you *don't need to* use it. ;)

---

