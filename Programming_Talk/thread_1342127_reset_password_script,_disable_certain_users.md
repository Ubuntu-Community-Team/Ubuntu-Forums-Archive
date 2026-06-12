---
title: "reset password script, disable certain users"
date: 2009-11-30
forum: Programming Talk
---

### Post by wilbbe01 on 2009-11-30
We have a system that is set to require password changes every 180 days.  Some of our users ignore the warnings until they are locked out of their accounts, and some users just completely forget their passwords without it actually expiring.  Not everyone at our company has access to this system.

Our goal is to create a solution for the helpdesk so they can reset passwords for users, but we don't want them to accidentally do a "sudo passwd some_nonexistent_user,"  "sudo passwd root," "sudo passwd," or "sudo passwd [a programmer's username]"  In order to limit this I created a script for resetting passwords where they can enter a users name and it will only change the password if the user exists.  (unfortunately they still could access passwd if they wnated to)

This method takes care of the first example of them accidentally creating an account for someone who really shouldn't have one, but they still have power to change any account that exists (root, my colleagues, etc) which they shouldn't.

Does anyone have an idea of how I might go about allowing the helpdesk password changing abilities, but only on some user accounts?  Ideally removing all access to everything except this password changing ability?  If there was a way to set some sort of a blacklist of users who the helpdesk user could not modify that would be perfect.  Kind of hard if I have to give them sudo access to passwd though....

Thanks.

---

### Post by Zugzwang on 2009-12-01
You could write a small program encapsulating the passwd functionality that performs the checks on whether the help desk person is actually allowed to change the password for the user and then runs "passwd <user>" if this is the case. 

Then flag the program with the setuid bit to make it run with root rights even if run by other people. Here's some mildly related example: [http://ubuntuforums.org/showpost.php?p=7669420&postcount=16](http://ubuntuforums.org/showpost.php?p=7669420&postcount=16)

According to some other posts, the "setuid" bit is usually ignored on scripts for security reasons, otherwise this would be the simpler solution.

---

### Post by wilbbe01 on 2009-12-14
Thank you Zugzwang for your suggestions.  I decided to use a pearl script instead of the bash one I had started.  At this point the pearl script checks to make sure the help desk can change the given username and generates a random password that they can type in the new and confirm boxes.  I was thinking that expect might be able to fully automate the process and remove the need to enter the password manually.  We do not currently have expect installed, but plans to upgrade to a new server are in place, so I may wait to install expect until the new server is built.

I also set the shell for the help desk user to my pearl script to ensure they cannot access anything but the script.

Thanks again for your suggestions.

---

