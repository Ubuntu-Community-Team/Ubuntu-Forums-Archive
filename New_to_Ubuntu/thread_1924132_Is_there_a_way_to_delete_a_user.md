---
title: "Is there a way to delete a user?"
date: 2012-02-12
forum: New to Ubuntu
---

### Post by TAspr on 2012-02-12
How do you do this?

---

### Post by anewguy on 2012-02-12
Try a Google, Yahoo, Bing, whatever search with

ubuntu delete a user

in the search string.

you can learn a lot just doing the correct searches.

---

### Post by thomsebastin on 2012-02-12
> **TAspr said:**
> How do you do this?
**Delete a user account**


   You can add multiple user accounts to your computer. See   [Add a new user account]("https://help.ubuntu.com/11.04/ubuntu-help/user-add.html") to learn how. If somebody is no longer using   your computer, you can delete that user's account.
 
[LIST=1]
[*]Click the icon at the very right of the panel and select System Settings.
[*]In the System section, click Users and Groups.
[*]Select the user you want to delete and click the Delete button.
[*]Type your password to make changes. You must be an administrative user to delete user   accounts.
[*]Each user has their own home folder for their files and settings.   You can choose to keep or delete the user's home folder. Delete the files   if you're sure they won't be used anymore and you need to free up disk   space. These files are permanently deleted. They can't be recovered. You   may want to back up the files to an external drive or CD before deleting   them.
[/LIST]

---

### Post by TAspr on 2012-02-12
I cannot delete the user..

See below for an explanation.  I cannot do anything to this user.

---

### Post by thomsebastin on 2012-02-12
> **TAspr said:**
> I cannot delete the user..

See below for an explanation.  I cannot do anything to this user.
try removing from command line **sudo userdel -r "name of th account to be deleted"**(exclude double quotes)..
This will remove both the user account and home directory, so use with caution.

---

### Post by nothingspecial on 2012-02-12
What happens if you click the minus button under the list of users?

---

### Post by TAspr on 2012-02-12
> **nothingspecial said:**
> What happens if you click the minus button under the list of users?

That Worked!  Thank you all for your help!

---

### Post by savanna on 2012-02-12
man deluser

---

### Post by nothingspecial on 2012-02-12
> **TAspr said:**
> That Worked!  Thank you all for your help!

You are welcome :)

---

