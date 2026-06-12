---
title: "admin password not working for lower user"
date: 2012-11-08
forum: New to Ubuntu
---

### Post by win22lin on 2012-11-08
I have ubuntu natty narwhal, 11.04 I believe.   Installed it myself and feel it was setup correctly, all my tests seemed to confirmed this.  I have an admin user and a lower rights user, the lower doesn't require  password.

Now when I want to do anything requiring admin rights in the lower user account, the admin password doesn't work.  I was wanting to add another folder to the pictures directory.  I have recently tried a few other things and the same issue of this password stops it.  When I log into the admin user account, the password works fine.  I attempted to change the admin password from in the admin user account and it reported that my passwords were "too alike"; in reality they were significantly different.  This issue isn't a caps lock.  What can I do from here?

If I log into the admin user, as I understand it, I can't add programs or add/change folders/files in the lower user; is that correct?

---

### Post by Mr_JMM on 2012-11-08
The whole point of a restricted user is to restrict what that user can do.
That's not to say I've not been irked by something similar.

I have always logged in to an admin account, created the necessary folders etc. and re-assigned permissions to the correct user after.
Use terminal to do above though, I find it much simpler and quicker.

If there's a simpler way then hope someone comes up with it but this should get you by until then.

---

### Post by win22lin on 2012-11-08
Uh,  I know about running necessary programs using admin-password;  either in terminal or "run as admin" context menu.  What is happening is  that the original setup password that i have used in the beginning is  not working anymore.  When I log into the admin account it does let me  log in, so the pw is still valid there.  

If I want to add a new program or change some small thing (in  the restricted rights account) I can't do it if it requires a password.

I tried to reset the password but it wont let me.  I assume that I  will have to establish a new admin account and delete the old one.

---

### Post by bab1 on 2012-11-08
> **win22lin said:**
> I have ubuntu natty narwhal, 11.04 I believe.   Installed it myself and feel it was setup correctly, all my tests seemed to confirmed this.  I have an admin user and a lower rights user, the lower doesn't require  password.

Now when I want to do anything requiring admin rights in the lower user account, the admin password doesn't work.  I was wanting to add another folder to the pictures directory.  I have recently tried a few other things and the same issue of this password stops it.  When I log into the admin user account, the password works fine.  I attempted to change the admin password from in the admin user account and it reported that my passwords were "too alike"; in reality they were significantly different.  This issue isn't a caps lock.  What can I do from here?

If I log into the admin user, as I understand it, I can't add programs or add/change folders/files in the lower user; is that correct?

The only difference between a user that has sudo rights (i.e.admin user) and a regular user (i.e. "lower user") is just that -- the ability to use sudo to issue commands as the *root* user.  The *root* user is the user rights are what you need to change permissions on any file or folder.

I always login with my user account. When I need to run a process as root (user) I use sudo to achieve that.  An example would be this```
sudo fdisk -l
```

Why do you feel you need a second user that can't use sudo during use?  In addition, why would you set this up and then want to have sudo rights from a user that you explicitly denied those rights to?

What do you think the "lower user" is for?  I would read the information on sudo located [**_[COLOR="Blue"]here[/COLOR]_**]("https://help.ubuntu.com/community/RootSudo") or one of [**_[COLOR="Blue"]these[/COLOR]_**]("https://www.google.com/search?q=ubuntu+sudo&btnG=Go!") sites.

---

### Post by Paqman on 2012-11-08
> **win22lin said:**
> 
If I log into the admin user, as I understand it, I can't add programs or add/change folders/files in the lower user; is that correct?

No, that's no correct. A user with access to sudo can do anything, including install and remove software, or mess about with files in another user's home folder.

However, just because a user has the ability to elevate their privileges doesn't mean they're running as root all the time. This is not like Windows of old, where an "admin account" was a security risk. Under Ubuntu's security model a user only takes on admin powers when they're required, and only for a short time. After making whatever changes required elevated privileges the user goes back to being a normal user automatically.

Most Ubuntu users use a single account with sudo rights. This is a bit different to the traditional Linux method of having separate root and normal user accounts.

---

### Post by newb85 on 2012-11-08
> **win22lin said:**
> Uh,  I know about running necessary programs using admin-password;  either in terminal or "run as admin" context menu.  What is happening is  that the original setup password that i have used in the beginning is  not working anymore.  When I log into the admin account it does let me  log in, so the pw is still valid there.  

If I want to add a new program or change some small thing (in  the restricted rights account) I can't do it if it requires a password.

I tried to reset the password but it wont let me.  I assume that I  will have to establish a new admin account and delete the old one.

An admin's password will never work in a restricted user's account, or any other account, for that matter.

I suggest you switch your restricted account to an admin account.

---

### Post by win22lin on 2012-11-08
Okay that is the snag, it is just one more security level and not only does it apply to the windoz crowd but I have heard some linux people doing it as well.  I just assumed it was commonly known, maybe not liked by the majority.

The issue is that the admin password worked and now it doesn't.  Regardless of how I run ubuntu, the facility is there and I should be able to use it.

If I had allot of things to do I would certainly log in as admin and do them.  

Can ubuntu share files between user accounts?  Can the admin account change/move files and folders in a lower user account?

---

### Post by bab1 on 2012-11-08
> **win22lin said:**
> Okay that is the snag, it is just one more security level and not only does it apply to the windoz crowd but I have heard some linux people doing it as well.  I just assumed it was commonly known, maybe not liked by the majority.

The issue is that the admin password worked and now it doesn't.  Regardless of how I run ubuntu, the facility is there and I should be able to use it.

If I had allot of things to do I would certainly log in as admin and do them.  

Can ubuntu share files between user accounts?  Can the admin account change/move files and folders in a lower user account?

We've been trying to tell you -- There is no admin account.  Any user that has sudo rights can assume root powers.  Root has complete control over the system.  Admin in this case is a verb not a noun.

---

### Post by win22lin on 2012-11-08
yes, i got out-typed.  Not so fast with the keyboard, here

---

### Post by deadflowr on 2012-11-08
You can use the su command to switch users.

```
su username
```

Use the password of the user you're going to use.

But it's by far simpler just to log into an Administrator account.

Linux is a permission based system.

[https://help.ubuntu.com/community/FilePermissions]("https://help.ubuntu.com/community/FilePermissions")

Once you get used to how permissions are applied, sharing between various users is quite simple.

By default, Ubuntu gives permission for user folders/files as owner=all, group=access, and other=access.
Only the owner of any file/folder can change the permissions, without escalated privileges.

---

### Post by bab1 on 2012-11-08
> **win22lin said:**
> The issue is that the admin password worked and now it doesn't.  Regardless of how I run ubuntu, the facility is there and I should be able to use it.
To use sudo you have to be a user that is a sudoer.  The first user created with an Ubuntu install has administration abilities via sudo.  Does this user still exist and have a valid password? > 

If I had allot of things to do I would certainly log in as admin and do them.  
If you installed Ubunutu then the first user you created should be your account whatever you named it.  Remember, the name is only a name.  If you named it admin then the account name is admin.> 
Can ubuntu share files between user accounts?  Can the admin account change/move files and folders in a lower user account?
You can set Ubuntu up anyway you want to.  There is no concept of a "lower user"  There are only 3 types of accounts.  They are ```
root user = root (the super user)
mortal users = users with a login (or not if suppressed)
system users = accounts set up to run specific processes
```
For example there is a system use called *syslog * and another called *avahi*.  These users can't login (no interactive abilities).

What you are really asking about is "elevated permissions" for sudo and the ability to manipulate files that you don't own.  Any user that is a sudoer can do that.  In reality all these users do is  use root powers for the command they are using.  Root is the only user that has no restrictions.  Root can change permissions and change ownership of files and directories it doesn't own.

---

### Post by bab1 on 2012-11-08
> **deadflowr said:**
> You can use the su command to switch users.

```
su username
```

Use the password of the user you're going to use.

But it's by far simpler just to log into an Administrator account.

Linux is a permission based system.

[https://help.ubuntu.com/community/FilePermissions]("https://help.ubuntu.com/community/FilePermissions")

Once you get used to how permissions are applied, sharing between various users is quite simple.

By default, Ubuntu gives permission for user folders/files as owner=all, group=access, and other=access.
Only the owner of any file/folder can change the permissions, without escalated privileges.
To be accurate: Ubuntu since 12.04 sets the default permissions as ```

files       = owner rw  group = rw  others = r
directories = owner rwX group = rwX others = rX

```

---

### Post by newb85 on 2012-11-08
To be more succinct, there is no one specific admin account.  Every user account ("mortal user", in bab1's terms) must be set to one of two account types: Standard and Administrator.  Any number of accounts (greater than zero) may be set as Administrator accounts.  The difference between Administrator and Standard accounts is only that an Administrator may temporarily elevate their privileges to superuser (through sudo or gksudo), allowing them to add/remove programs and modify system files, and essentially giving them free reign of the system (including manipulating files in other user's home folders).

There really is no good reason to force yourself into a standard user account.  Even when logged into an administrator account, you don't have any more privileges than a standard user unless you elevate your privileges.

My suggestion is that you log in as the user set as Administrator and change the account you normally use to an Administrator account, too.

---

