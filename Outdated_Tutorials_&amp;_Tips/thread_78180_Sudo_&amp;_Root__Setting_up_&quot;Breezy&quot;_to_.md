---
title: "Sudo &amp; Root:  Setting up &quot;Breezy&quot; to use both"
date: 2005-10-17
forum: Outdated Tutorials &amp; Tips
---

### Post by castaway on 2005-10-17
If an expert install of "Breezy" is performed and a (1) root password and a (2) user-name and user password are entered during setup, many of the specially written Ubuntu menu items are not available to the user.  And there is no way root can access them on the user's menu.  Those programs that request a password will accept neither the root password nor the user password.

If a default install of "Breezy" is performed, the user is able to access all of the menus, sometimes having to enter the user password first.  However, working at the terminal becomes an exercise in frustation for the Debian user who must constantly try to remember when and when not to preface a terminal command with "sudo."  (Root is not available!)

There is an alternative.  "Breezy" can be set up so that the user can access all the menu items, including those which require user passords.  Yet he can also work as root at a terminal in the same manner as he would in basic Debian -- by issuing the "su" command.  The following instructions show you how.

*****Installing Ubuntu 5.10*****

1)  Install Ubuntu as *expert*:  Boot the cd-rom.  At the boot screen prompt "boot," type "expert" (without quotation marks) and hit <Enter>.

2)  When the install program asks for a root password, enter a password.  

3)  Create a "normal user account":  enter both a user-name and a user password.

4)  When installation is complete, sign in with the user-name and password and proceed to the following section.

*****Modifying your "expert" Ubuntu 5.10 installation so that "sudo" also works*****

All the following tasks are carried out at a root prompt after opening the terminal.  

1)  At the terminal prompt enter:
    
       ```
su
```

    When requested for the password, enter the root password.


2)  Add a new group, admin, to the group file:
       
       ```
groupadd   admin 
```

2)  Add the user-name to the admin group:

       ```
adduser   user-name    admin
```

4)  Add the new group, admin, to the sudoers file and assign it root privleges:

       Start the special editing program for the sudoers file:

             ```
visudo
```

       Use the down arrow to go to bottom of the file and add:

             ```
 %admin    ALL=(ALL)    ALL

```
       Hit <Ctrl>+<X> to exit.
       Hit <Y> to save the file.
       Hit <Enter> to confirm the file name and leave the visudo program.

That's all!

---

### Post by Azrael on 2005-10-18
Well said!

If you get tired of typing passwords you could also use:
[FONT=monospace][/FONT][FONT=monospace]
[/FONT]%admin    ALL=NOPASSWD:    ALL

instead of:
[FONT=monospace]
[/FONT]%admin    ALL=(ALL)    ALL

(insert WARNING: SECURITY ALERT here, yada yada)

---

### Post by Conq on 2005-10-18
Or you can do it really simple:

```
sudo bash
```

and you'll have a root-shell.

---

### Post by Binnikemasken on 2005-10-24
And if you haven't installed Ubuntu through "expert"?
How can I add the admin privileges?

---

### Post by Mustard on 2005-10-24
[QUOTE=Binnikemasken]And if you haven't installed Ubuntu through "expert"?
How can I add the admin privileges?[/QUOTE]

Default install gives admin privileges to the first created user account by default.

---

