---
title: "Restrict User Access to Programs/Administration"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by lurch2012 on 2008-09-24
I've used Ubuntu on my home PC for years. Love it. Absolutely love it. I've recently obtained a position as a Library IT guy. I'd like to be able to have a couple of Ubuntu boxes in the children's lab, but I've run into a problem. I need to be able to set access levels for a user "Child" and "Parent". Here is an outline of what I'd like to have available for the two users>

Child should only have access to the following>
Education program group
Graphics program group
Games program group
>I'm debating about access to Home folder

Parents should have access to the above as well as>
Internet program group

None of the users (besides me, of course) should have access to the administration or preferences. 

Basically, I need this machine locked down for users besides myself.

On our Windows XP/Vista machines the above is handled using Group Policy, but I have not found an equivalent for Ubuntu.

Is there a package out there that helps in these situations or is there a setting I'm just missing? If I need 

Any help is greatly appreciated!

---

### Post by mikewhatever on 2008-09-24
Take a look under System->Admin->Uers and Groups. If highlight a user and click Preperties, the second tab, user privileges, has lots of options to disable.
As for programs, simply edit the menu for each user leaving only the programs you want them to access.

---

### Post by MikeEvans on 2008-09-24
Once you configure the menus the way you want you can change the permissions on the menu config file so the children can't mess it up.  You can take ownership of it and give the children read and execute permission.  Something like this:
```

chown -R your_account:children_account /home/children_username/.config/menus

chmod -R 751 /home/children_username/.config/menus
```

After that they would get an error if they tried to change the menus.  mikewhatever was correct about the other security options you asked about.

---

### Post by lurch2012 on 2008-09-24
Thanks, guys! Done and done!

---

### Post by lurch2012 on 2008-09-25
Okay...I did all of the above, and have the desktops exactly the way I want them to stay. After performing the code above in the terminal, there were no errors. However, if I log in as a child, I'm still able to add and move menus. Any ideas? Is there a way to automatically clear configuration changes to the desktop on logout?

---

### Post by mikewhatever on 2008-09-25
Let's see what the permissions are now. Can you post the output of the following:
> ls -l /home/children_username/.config/menus



---

### Post by silverglade00 on 2008-09-25
You might want to also check out sabayon in the repos. It lets you set up a desktop for users in a graphical way and then applies that to /etc/skel so each new user gets the settings. It might help.

---

### Post by lurch2012 on 2008-09-25
> **mikewhatever said:**
> Let's see what the permissions are now. Can you post the output of the following:
```

npladmin@edubuntu1:~$ ls -l /home/child/.config/menus
total 120
-rwxr-x--x 1 npladmin child  994 2008-09-24 12:06 applications.menu
-rwxr-x--x 1 npladmin child 3122 2008-09-24 12:06 settings.menu
-rwxr-x--x 1 npladmin child 1074 2008-09-24 11:15 settings.menu.undo-10
-rwxr-x--x 1 npladmin child 1157 2008-09-24 11:15 settings.menu.undo-11
-rwxr-x--x 1 npladmin child 1237 2008-09-24 11:15 settings.menu.undo-12
-rwxr-x--x 1 npladmin child 1318 2008-09-24 11:15 settings.menu.undo-13
-rwxr-x--x 1 npladmin child 1396 2008-09-24 11:15 settings.menu.undo-14
-rwxr-x--x 1 npladmin child 1396 2008-09-24 11:15 settings.menu.undo-15
-rwxr-x--x 1 npladmin child 1470 2008-09-24 11:15 settings.menu.undo-16
-rwxr-x--x 1 npladmin child 1551 2008-09-24 11:15 settings.menu.undo-17
-rwxr-x--x 1 npladmin child 1619 2008-09-24 11:15 settings.menu.undo-18
-rwxr-x--x 1 npladmin child 1696 2008-09-24 11:15 settings.menu.undo-19
-rwxr-x--x 1 npladmin child 1772 2008-09-24 12:03 settings.menu.undo-20
-rwxr-x--x 1 npladmin child 1859 2008-09-24 12:03 settings.menu.undo-21
-rwxr-x--x 1 npladmin child 1935 2008-09-24 12:03 settings.menu.undo-22
-rwxr-x--x 1 npladmin child 2013 2008-09-24 12:03 settings.menu.undo-23
-rwxr-x--x 1 npladmin child 2088 2008-09-24 12:03 settings.menu.undo-24
-rwxr-x--x 1 npladmin child 2088 2008-09-24 12:03 settings.menu.undo-25
-rwxr-x--x 1 npladmin child 2276 2008-09-24 12:03 settings.menu.undo-26
-rwxr-x--x 1 npladmin child 2344 2008-09-24 12:03 settings.menu.undo-27
-rwxr-x--x 1 npladmin child 2419 2008-09-24 12:03 settings.menu.undo-28
-rwxr-x--x 1 npladmin child 2485 2008-09-24 12:03 settings.menu.undo-29
-rwxr-x--x 1 npladmin child 2550 2008-09-24 12:03 settings.menu.undo-30
-rwxr-x--x 1 npladmin child 2621 2008-09-24 12:03 settings.menu.undo-31
-rwxr-x--x 1 npladmin child 2707 2008-09-24 12:03 settings.menu.undo-32
-rwxr-x--x 1 npladmin child 2773 2008-09-24 12:03 settings.menu.undo-33
-rwxr-x--x 1 npladmin child 2847 2008-09-24 12:03 settings.menu.undo-34
-rwxr-x--x 1 npladmin child 2925 2008-09-24 12:03 settings.menu.undo-35
-rwxr-x--x 1 npladmin child 2987 2008-09-24 12:03 settings.menu.undo-36
-rwxr-x--x 1 npladmin child 3059 2008-09-24 12:03 settings.menu.undo-37

```

---

### Post by lurch2012 on 2008-09-25
> **silverglade00 said:**
> You might want to also check out sabayon in the repos. It lets you set up a desktop for users in a graphical way and then applies that to /etc/skel so each new user gets the settings. It might help.

Thanks for the tip! I'm having trouble getting sabayon to remain stable (crashes when I attempt to save changes), but it is a really good tool. Might have to try it on my home box.

---

### Post by mikewhatever on 2008-09-28
The permissions show that that child group can read and execute. What if you chmod it again using with 744 permissions, letting other read only access.

---

### Post by ajreyes2010 on 2010-04-18
Nice one. Thanks.

---

