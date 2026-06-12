---
title: "Proper Web Server Permissions"
date: 2009-05-26
forum: Programming Talk
---

### Post by Crath on 2009-05-26
So I am currently running 9.04 server and have lampp setup and all is well, except I have yet again run into an issue ive hated during my entire web development career.

Permissions :(

I am able to log into my ftp client as my normal user account (not root, but an admin), and see all the files and open them to edit, but once I go to save them i dont have permission.  i understand how it works, the root made / moved the files there and I dont have rights to modify them, cool, but i'd like to make the account "shane" an owner as well, or whatever it takes to give that account writing privileges on those folders / sub files/folders

this is about the time I'd just get pissed off and chmod the entire htdocs directory to 777, but i think its time to learn the right way :)

thanks!

---

### Post by johnl on 2009-05-26
Hi,

This is how I usually set things up (where $WWWHOME is your webserver root dir).  I wouldn't suggest following this blindly but if you understand what I'm getting at it should give you an idea :)

chown -R myusername:www-data $WWWHOME
chmod g+S $WWWHOME

This changes all the files in your www root such that you are the owner, but the webserver is in the group that can access them (chown).
Also, any new files are created with the same user/group ownership (chmod).

You will then need to make sure that the group has the permissions it needs (read, write, etc).

chmod -R g+r $WWWHOME

Hope this helps.

---

