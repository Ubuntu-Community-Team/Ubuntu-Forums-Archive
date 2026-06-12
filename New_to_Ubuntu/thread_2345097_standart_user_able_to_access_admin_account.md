---
title: "standart user able to access admin account"
date: 2016-11-30
forum: New to Ubuntu
---

### Post by sn0m on 2016-11-30
Hi Guys, I created a stadard account for my son in my computer via user accounts in settings. However I have found out that he can access, delete or create files into the admin account?
Is there a way of stopping this?
Thanks
Koli

---

### Post by QIII on 2016-11-30
Hello!

How long ago did you create this account?  How savvy is your son?  How often does he have unattended access to the machine?

---

### Post by SeijiSensei on 2016-11-30
The only "admin" account in Unix is "root" with home directory /root.  I doubt he is writing to that.

Do you mean he can write into your account?  That's pretty surprising with default permissions.  If you want to protect your own account from all prying eyes, use this:
```

cd /home
sudo chmod g-rwx,a-rwx -R yourusername

```
Enter your password when prompted.  Now only yourusername can access the files in that account's home directory.  The command removes (-) the read, write, and execute privileges (rwx) from both members of your group (g) and all other users (a). The -R switch tells the command to "recurse" down the entire tree of subdirectories in the account and apply the changes to everything it finds.

Is it possible you somehow gave your son sudo ("admin") permissions when you created the account?  Try this check:
```

grep sudo /etc/group

```
You should see only your username after the final colon.  If he is also there, run "sudo nano /etc/group", find the appropriate line, and delete his username.  Then save the file with Ctrl-X and Yes.

---

### Post by sn0m on 2016-11-30
He is not that savy, he's just learning linux and is only 9 years old. I wanted to show him how secure the linux is, ie he cant access or delete files/directories of my account, the admin from his account but well, found out that he could. I did check ls -l and it is all there under my name...find it funny. Ideally do not want him to access or be able to delete files in my account..

I created his account via settings, standard account.

grep sudo /etc/group produces only my name, not his.
I think this is like a security thing as a standard user should not be able to access or delete admin files..

---

### Post by SeijiSensei on 2016-11-30
Ubuntu's "sharing" ethic applies to the creation of users' home directories.  They are assigned g+rx,a+rx permissions by default, meaning that all users can list and read any files in anyone's account.  Other distributions, especially those oriented toward servers like RedHat and its offspring, use the default permissions I suggested, full permissions for the directory's owner and none for anyone else.

I don't know how he can write into your home directory.  Even the default permissions don't allow that.

You can make the default permissions for any future accounts more restrictive if you like.  Use "sudo nano /etc/adduser.conf" and change the line 
```

DIR_MODE=0755

```
to
```

DIR_MODE=0700

```
700 is the [equivalent]("https://help.ubuntu.com/community/FilePermissions") of u+rwx,g-rwx,a-rwx which I gave you before.

---

### Post by sn0m on 2016-11-30
Ha ha  this is turning into a nightmare
sudo chmod g-rwx,a-rwx -R my_username has completely brink walled my home directory....wont let me access from guest, or my sons account...oups

---

### Post by SeijiSensei on 2016-11-30
Yes, that was the point.  

If you want to let others see what's in your home directory, then you can reverse the change with
```

cd /home
sudo g+rx,a+rx -R yourusername

```

Are you really certain that your son could create and delete files in your home directory?  That shouldn't be possible on a default Ubuntu installation.

If you go back to this more open route, you should consider creating a private subdirectory inside your home.
```

cd /home/yourusername
mkdir private
chmod 700 private

```
Anything you put there will only be readable by your account.  If you want to make it less obvious, use "**.**private" instead.  Then it will be a "hidden" file and not appear in directory listings by default.

---

### Post by sn0m on 2016-11-30
Hi
thanks for your help
sudo chmod g+rx,a+rx -R myusername did the trick, now I can access my /home folder from my sons account, but somehow i don't seem to be able to log onto my account, if I try it comes back to splash scree...
Thanks
Koli

---

### Post by kpatz on 2016-11-30
Who owns your home directory?  It should be your username.  Do```
cd /home
ls -ld yourusername
```
and post the output.  It should look something like:
```
yourusername@catzfs01:/home$ ls -ld yourusername
drwxr-xr-x 42 **yourusername yourusername** 97 Nov 30 14:10 yourusername
yourusername@catzfs01:/home$
```

If it's owned by something else, run ```
sudo chown -R yourusername:yourusername /home/yourusername
```

Double check that your son's home directory is owned by his account as well.

---

### Post by sn0m on 2016-11-30
Hi thanks for your message. No luck with your instructions. It seems that I have the right permission but still unable to log on onto my account. I've backed up the home directory and doing a clean install. Thanks

---

