---
title: "No passwords/Could not update ICEauthorityfile?"
date: 2012-03-17
forum: New to Ubuntu
---

### Post by ohmygoats on 2012-03-17
((I think this might be the wrong forum, but I only installed Linux about a week ago, so I've no real idea what I'm doing?))

I installed Ubuntu 11.10 from a USB stick, and when creating a user account I was told to create a password, so I did. When looking at the system settings I noticed you could have no password, so I set every account on my laptop to no password.

Everything seemed to be mostly working fine, I could log on and off with no passwords, but when it asked for authority for something (like installing a program), it wouldn't accept me giving authority with no password, nor with the old password.

I restarted my laptop, to see if that would help, and when I tried logging back on to my account, there was the message "could not update ICEauthorityfile/home/computer/username/.ICEauthority" for every user account. I can only use the computer on guest session.

I tried restarting the computer again with grub boot (as advised by the internet), and opening the recovery menu. I then tried 'passwd username', and it told me my user account didn't exist. I rebooted again, and I can still see all the user accounts at the log-in screen, but they all display the same 'ICEfile' message, and I can still only log on to guest.

Guest session doesn't have the authority to view or store files, so I don't know if my files are still there, or if everything's gone.

Thank yoou in advance for any help, I'm entirely baffled. :(

---

### Post by critin on 2012-03-17
Password is needed for most everything, updates, installing, settings, etc.  We need our password to avoid problems.   When I was brand new, I also griped about them and wanted to turn mine off to log-in.  Now I have no problem typing in a few characters and moving on.  

I know this doesn't help with your issue, but next time you see a post from a newbie wanting to know how to turn his password off, you might want to advise him NOT to do it.  How many seconds does it take to type a few characters?
> 
When looking at the system settings I noticed you could have no password, so I set every account on my laptop to no password.You can have no password to log in only.  It's called automatic log-in in system settings, user acct.

> 
I don't know if my files are still there, or if everything's gone.

You haven't lost anything.

I'm sure someone will help you with proper commands to use on the terminal.

---

### Post by fabricator4 on 2012-03-17
> **ohmygoats said:**
> 
I tried restarting the computer again with grub boot (as advised by the internet), and opening the recovery menu. I then tried 'passwd username', and it told me my user account didn't exist. I rebooted again, and I can still see all the user accounts at the log-in screen, but they all display the same 'ICEfile' message, and I can still only log on to guest.
(

Your username does indeed exist, unless you deleted that user.  (It's not a good idea to delete your only admin user).  Inability to use the existing ICEauthority file is a pretty good indication that you don't have the correct permissions for the user account.  I think what happens, is that if you remove the password completely the account is disabled.

The correct format is indeed

passwd username

If the user has been removed from the admin group, you can add it again with:

usermod -a -G admin username

However the most likely scenario is that when you removed the password the account was locked out.  Unlock it with the command:

usermod -U username


If that doesn't work, try adding yet another admin user to see if that will get you going (eg username is adminuser):

useradd adminuser
passwd adminuser
usermod -a -G admin adminuser

It doesn't hurt to have a second admin user with a strong password that you can use to fix problems if you break your one and only login on the system.

There's some basic information on managing users with command line here:

[http://www.g-loaded.eu/2005/11/06/manage-users-from-the-command-line/](http://www.g-loaded.eu/2005/11/06/manage-users-from-the-command-line/)

You should use the man pages to see other options eg

man usermod

Note that it's pretty easy to mess up a user account with command like usermod if you don't know what you are doing (for example, if you don't use the -a switch it will remove that user from all groups EXCEPT the one you specify.

Chris

---

### Post by ohmygoats on 2012-03-18
Thank yooou for your answers, but I'm still having some trouble?

I tried the usermod and useradd commands, and both resulted in the message 'cannot lock /etc/passwd; try again later'. I also tried passwd, and was told 'invalid user ID'.

Thanks again :)

---

### Post by fabricator4 on 2012-03-18
> **ohmygoats said:**
> Thank yooou for your answers, but I'm still having some trouble?

I tried the usermod and useradd commands, and both resulted in the message 'cannot lock /etc/passwd; try again later'. I also tried passwd, and was told 'invalid user ID'.


Did you try the -U switch with usermod, or did that give you the "cannot lock" message as well?

Something seems well broken if this is the case.

Did you try making the new admin user account?

Chris

---

