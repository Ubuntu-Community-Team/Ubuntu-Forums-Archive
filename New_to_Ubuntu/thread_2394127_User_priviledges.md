---
title: "User priviledges"
date: 2018-06-12
forum: New to Ubuntu
---

### Post by ramanterola on 2018-06-12
Greetings Ubuntu fans!!! 

I now have a super noob question:   I am using Lubuntu 18.  How do I change priviledges based on the user currently logged in?   Starting with the menu,   User A gets all the menu options,   User B gets some of the menu options & cannot install software.    User A then needs to install the software and change the rights for user B to access the software.

How exactly can I do this?   I went in the "Advanced Settings" for the user, but I was not able to see any menu or menu tree configuration, etc.

As usual thank you in advanced for your time and knowledge sharing.

R

---

### Post by TheFu on 2018-06-12
Unix is multi-user from the ground up.  Linux is based on Linux, so it inherits those aspects.

The power to install software is the power to remove software and the power to make the system completely unusable.  Usually, it is best to have 1 account with those permissions.  During software installation, accounts can be altered, created and removed, so  it is a dangerous permission to allow for just any userid.

Almost all Unix permissions are traced back to file and directory permissions.  There are hundreds of tutorials. Google will find them. Any Unix tutorial works for any Linux, since they are the same at this level. Modifying permissions to installed applications is generally a terrible idea.  They get the permissions they do to properly have a secure system.  With an understanding of groups and userid permissions, you can create the ability for any userids to have access to whatever you want, provided you are the system admin.  Regular users can't modify these permissions. Tools that are only meant for admin use, aren't shown to regular userids.

Also, some permissions are dynamic and only allowed for the userid logged in first and controlling the primary session.  This is done to prevent someone from using a remote connection and playing video or audio from around the world.  

I'm not certain that what I wrote above is helpful.  If you need more information, [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) is a book about the way the OS works and explains the "why" things are the way they are, not just what to type. That is important.  Rest assured, there is almost always an extremely good reason for the way things are.   Before changing lots of settings or permissions, please make a few backups so you can put things back when they become broken.

---

### Post by ramanterola on 2018-06-13
Thank you [TheFu] for the input.   I can see where one can go crazy and lock things up. I would extra careful when settings these as I am adept at setting users & privileges in a windows environment.   

I am actually looking for a GUI that removes things like "System Tools" from the menu, preventing changes or additions to the panels, access to terminals, etc.   There is already a super user that will not be modified.

So...is there a GUI for Lubuntu 18.04 that will allow me to do this?

Thank you in advance for your time and expertise.

R

---

