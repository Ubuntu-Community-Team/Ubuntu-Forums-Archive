---
title: "Prompt for Username and Password GDM"
date: 2010-08-10
forum: Outdated Tutorials &amp; Tips
---

### Post by MichealH on 2010-08-10
This is a tutorial on how to stop GDM from displaying the users on the login screen, requiring the username and password, and thus securing your User Account.

** [SIZE="4"]Its as easy as 3 steps![/SIZE] **

** Should work on the following**

 - 10.10, **(Dev)**
 - 10.04 LTS **(Current LTS)**
 - 9.10 **(Supported until April next year)**

**Step 1- Opening Gconf editor**

Press the keys (ALT+F2) and then tyoe in the box ```
gconf --editor
```

**Step 2- Finding the key and chnging it.**

Navigate to /apps/gdm/simple-greeter and check the checkbox next to "disable_user_list"

**Step 3- Logging out and testing new settings **

Log out and then if you see a box with Username: compared to just a list to choose from, you've done it. If It doesnt work on your version please tell me.

** Changelog**

** v 1 **

 - Initial release

---

