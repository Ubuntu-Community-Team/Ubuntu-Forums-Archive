---
title: "Noob thrown in at the deep end"
date: 2012-07-12
forum: New to Ubuntu
---

### Post by slinks on 2012-07-12
Hi,

I have been asked to fix a machine where the main drive which had 8.10 (?) on it has expired but fortunately the /home folders are all on a separate disk.

I replaced the dead disk and installed 12.04 on it and created an admin account. I then installed webmin and made accounts to match the original users and pointed the new accounts at the old user folders on the second disk.

This works while I am logged on and I switch user but I cannot log into any other account than the admin account I set up for myself from start up without getting an .ICEauthority file type failure.

I assuming that the system is looking for the /home file in the wrong place for the other accounts and the /home folder on the new disk just shrugs when looking for the account I set up to look at the other disk. I think this makes sense.

So, how do I get the machine to know where to look for these accounts? How do I make sure the old /homes disk is mounting on startup? how can I get this to work?

Any help will be really appreciated as I will need to sleep one day this week!

Thanks

---

### Post by steeldriver on 2012-07-12
I'm not familiar with webmin but it's possible that although your new accounts have the correct names and home dirs, the UIDs and/or GIDs don't match - what do you see if you

```
ls -l /home
```How did you mount the (old) home partition?

---

### Post by blackbird34 on 2012-07-12
There might also be a problem due to the fact that stuff may have changed in the way home is organized between Ubuntu 8.10 and Ubuntu 12.04... For example all the old Gnome 2 settings which are irrelevant for Unity/Gnome 3...

---

### Post by Paqman on 2012-07-12
You need to sort the permissions for the files in each user's home folder:
```
sudo chown -R username:username /home/username
```
...will do the trick.

The issue arises because while users may have the same name as before, they don't necessarily have the same UID, which is what the permissions system uses. The above command forces the permissions on the files to match those of the the appropriate user accounts.

You will obviously need to execute this command once for each user account you're trying to restore, which could be tedious if you've got large numbers. I'm sure someone with more bash-fu could find a way to automate it if that's what you need.

> **slinks said:**
> How do I make sure the old /homes disk is mounting on startup?

There needs to be an entry for it in the file /etc/fstab. This should have been set up when you installed, you'll need to add an entry if it's not there:

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by slinks on 2012-07-12
> **steeldriver said:**
> I'm not familiar with webmin but it's possible that although your new accounts have the correct names and home dirs, the UIDs and/or GIDs don't match - what do you see if you

```
ls -l /home
```How did you mount the (old) home partition?

I get this

total 4
drwxr-xr-x 25 jason jason 4096 Jul 12 23:41 jason


I have solved this now by going to the filesysten area in webmin and saving the /media/fs...   so that it starts on boot. I imagine it has done the fstab thing for me.

I am struggling with Samba. I can only connect to one account (not mine...) all accounts are samba users and all home files are shared but I can't get to them on a windows machine.

Any ideas?

---

### Post by steeldriver on 2012-07-12
so your old user accounts are on /media/whatever rather than remounted at /home? and 'jason' is the new primary account?

if that's the case then you would need to check the ownership and permissions on /media/whatever

I don't know enough about samba to advise you on that but if there are ownership and/or permission issues on the old home dirs imho you should sort those out before trying to get samba working

---

