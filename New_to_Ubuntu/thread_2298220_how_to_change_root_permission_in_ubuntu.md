---
title: "how to change root permission in ubuntu"
date: 2015-10-09
forum: New to Ubuntu
---

### Post by shanna on 2015-10-09
im new here i want to know how to change the root permission in all folders so i can apply themes icons etc can anyone pls help about this and guide me 

thanks

---

### Post by sandyd on 2015-10-09
A little explanation on why files are owned by root, and why we shouldn't change that.

In Ubuntu, system files are generally owned by a user and a group for security reasons.
When the permissions (see below) of files and folders are set properly, this can prevent unauthorized users and applications from viewing, executing, or writing to the files/folders. You will find that some system files are owned by "root", which is the primary system user.

If your trying to install themes in /usr/share/themes, you will need temporarily escalate your account to have the privileges of the "root" user.

Run the following in the terminal
```
sudo -H nemo

```
After typing the password, you now have a nemo window open that allows you to write to all folders.

WARNING:
Please do not use sudo -H nemo to extract, create, or modify files in your home folder. Files created/modified by nemo while running as the "root" user will be owned by root, and you will not be able to modify them with your normal user account. The same warning applies to running other applications under sudo as well.

---

### Post by buzzingrobot on 2015-10-11
Linux has this system of file ownership and permissions because it is, at heart, a multi-user system.  That means your Linux system is capable of supporting multiple users simultaneously. So, some way of preventing users with interfering with the files of another user is necessary.  The value of the ownership and permissions system extends throughout the system, too, particularly about security.

Themes and icons can be installed in the user's home folder. Create  ".themes" and ".icons" folders in your home folder. (Files and folders that begin with a '.' are treated as hidden to reduce clutter, etc.  The file manager has an option to show them.) Copy the extracted theme and icon folders there.  You won't be asked for a password and you won't need to use sudo. Caveat:  Some themes and icons may not display correctly unless they are located in /usr/share/themes or /usr/share/icons.

---

