---
title: "Import/Export User Programs and Settings to New User"
date: 2015-09-06
forum: New to Ubuntu
---

### Post by viral2 on 2015-09-06
Hey,
I have an interesting question, as I am new to the linux environment I don't know if this is available or not.
I have installed xubuntu and my user is an Administrator by default.
I was working here and installed all the useful software and settings.
Now i had created a normal user. I want to import the software and settings from my previous user login to the new user login.
Is this possible? I didn't find anything matching on google.

If there is a relevant post please do share here
thank you

---

### Post by ajgreeny on 2015-09-07
What is the reason for making a non-admin user account?  Do you think it is safer to do that for the day-to day use of the OS than have a user with admin abilities logged in all the time?  Single user systems do not need to have a separate non-admin user in this way because for most of the time the admin user, though able to raise his abilities to that of the root account, is actually working with non-admin permissions.  If you are baffled by the fact that Ubuntu does not require a root account, (it is disabled by default in Ubuntu), have a read through the info at Root-Sudo in my signature which explains everything in more detail than I will here.

If you really do want to import everything including all the data files, ie docs, music, videos etc etc, that you have in the home of the admin user (the first user you made when installing), you can copy everything as admin user, including all the hidden folders and files in the home folder of the admin user to the home of the second, non-admin user.

You will then have to change ownership of everything in the second user's home, again from the admin account, with command ```
sudo chown -R *user*:*user* /home/*user*
``` where *user* in italics is the new second username.

If both users need to have access for read/write of the data files it is probably better to make a separate shared partition with permissions that allow both to read and write, but that is probably best left for another question once this first is answered.

---

