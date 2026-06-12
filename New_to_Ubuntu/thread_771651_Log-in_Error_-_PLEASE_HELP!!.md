---
title: "Log-in Error - PLEASE HELP!!"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by thebarefootmarauder on 2008-04-27
HELP!

When I try to log in I get this error message.

> /etc/gdm/Xsession: Beginning session setup...
Can't create dir /home/jill/Desktop
Can't create dir /home/jill/Templates
Can't create dir /home/jill/Public
Can't create dir /home/jill/Documents
Can't create dir /home/jill/Music
Can't create dir /home/jill/Pictures
Can't create dir /home/jill/Videos
Setting IM through im-switch for locale=en_US
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.

I can log in to failsafe terminal but that is it.

Would it be best to just put in a live cd and reinstall Ubuntu?
I feel like maybe my home folder is unmounted to my login account.

---

### Post by dondad on 2008-04-27
> **thebarefootmarauder said:**
> HELP!

When I try to log in I get this error message.



I can log in to failsafe terminal but that is it.

Would it be best to just put in a live cd and reinstall Ubuntu?
I feel like maybe my home folder is unmounted to my login account.

If you have a separate /home partition or no data in it that is irreplaceable, then I would probably just reinstall. What were you doing last before it quit booting? One thing that can cause these types of issues is to use sudo with a graphical application rather than gksudo. Sometime the ownership of files gets messed up and you cannot access them.

Also, if you do reinstall and don't currently have a separate /home partition, now would be the time to do that. It makes it much easier to reinstall or upgrade in the future as you will not lose data.

---

### Post by daimaru on 2008-04-27
maybe you can just login to safe mode and create a new user account. either via system->administration->Users and Groups or in terminal with "adduser" delete your old user profile add new one log into that one and pray it works :):lolflag:

---

### Post by thebarefootmarauder on 2008-04-27
> **daimaru said:**
> maybe you can just login to safe mode and create a new user account. either via system->administration->Users and Groups or in terminal with "adduser" delete your old user profile add new one log into that one and pray it works :):lolflag:

Unfortunately I can only log into the failsafe terminal - not the other safe mode.

---

### Post by thebarefootmarauder on 2008-04-27
> **dondad said:**
> If you have a separate /home partition or no data in it that is irreplaceable, then I would probably just reinstall. What were you doing last before it quit booting? One thing that can cause these types of issues is to use sudo with a graphical application rather than gksudo. Sometime the ownership of files gets messed up and you cannot access them.

Also, if you do reinstall and don't currently have a separate /home partition, now would be the time to do that. It makes it much easier to reinstall or upgrade in the future as you will not lose data.

Somehow the home folder was given read/write permissions to all users.  Upon log in it told me to fix that and something about 644 privelages? I attempted to do so by running a similar script to what I had run before ... something with chmod.  That didn't work and now I am where I am.

Most of my data is either on a flash drive or on my friend's external hard drive. If no one here had a solution, we were going to run a live cd, try and find the data. IF that didn't work, we're going to reinstall it - possibly recovering the data on a new external hard drive before doing so.  I would really like to fix the problem if it is a simple script, as there are a few things that I would be missing.

---

### Post by daimaru on 2008-04-27
> **thebarefootmarauder said:**
> Unfortunately I can only log into the failsafe terminal - not the other safe mode.
you can add user from terminal just do 
```
sudo adduser testuser
```enter your root password, enter the user name or just hit enter to use all the defaults. after that you have a new user called testuser which you can use to login and then change whatever you want.

I mean you'll be able to copy your /home/jill/ stuff to /home/testuser then delete jill and recreate a jill account.
```
mkdir jillbackup
sudo cp -r /home/jill/ /home/testuser/jillbackup/
```

---

### Post by thebarefootmarauder on 2008-04-27
> 
you can add user from terminal just do 

Code:
sudo adduser testuserenter your root password, enter the user name or just hit enter to use all the defaults. after that you have a new user called testuser which you can use to login and then change whatever you want.

I mean you'll be able to copy your /home/jill/ stuff to /home/testuser then delete jill and recreate a jill account.

Code:
mkdir jillbackup
sudo cp -r /home/jill/ /home/testuser/jillbackup/

I tried this.  I got logged on okay but there is no data in the folder.  Does that mean all of my files are gone?


I tried again with the -r (I missed it originally).  Now there is a folder with a lock symbol on it and when I open it, still no files.

---

### Post by daimaru on 2008-04-27
do you mean if you're in the testuser account  and you browse to /home/jill theres nothing there ? if so yeah you might have lost the data, but i would still recommend trying to boot live cd and checking if your files are there.

---

### Post by thebarefootmarauder on 2008-04-27
> **daimaru said:**
> do you mean if you're in the testuser account  and you browse to /home/jill theres nothing there ? if so yeah you might have lost the data, but i would still recommend trying to boot live cd and checking if your files are there.

When I tried the second time (with the -r command) I managed to get a folder with my documents in it.  I unlocked it using chmod.  It looks like all of my documents are there.  I don't know what happened to the rest of the stuff though.

---

### Post by daimaru on 2008-04-27
if you copy stuff you can use the commands chown and chgrp to change owner and group permissions to your current username:
```
sudo chown testuser *
sudo chgrp testuser *
```* for all files in the directory.

this will only change owner and group not permissions stuff like chmod 777 etc.
EDIT: don't know why your other files don't show up though...

---

### Post by thebarefootmarauder on 2008-04-27
> **daimaru said:**
> if you copy stuff you can use the commands chown and chgrp to change owner and group permissions to your current username:
```
sudo chown testuser *
sudo chgrp testuser *
```
* for all files in the directory.

this will only change owner and group not permissions stuff like chmod 777 etc.

I'm thinking maybe I wasn't patient enough for it to copy all of my stuff.  I'm running the original codes again with jillbackup2 then will use the codes above.

Hopefully this all works.  Thank you so much for your help.  I will post the outcome of above said plan.

---

### Post by daimaru on 2008-04-27
um sorry made a mistake there. it should read 
```
 sudo chown -R testuser *
sudo chgrp -R testuser *
```for recursive file changes

---

### Post by thebarefootmarauder on 2008-04-28
> **daimaru said:**
> um sorry made a mistake there. it should read 
```
 sudo chown -R testuser *
sudo chgrp -R testuser *
```for recursive file changes

Okay.  Still waiting to see if more of my files will be copied.  I think cause there are a lot of them it is taking a while.

The terminal isn't bringing up the testuser@jill-laptop etc. again.  Will it do that when it is finished copying?

---

### Post by dondad on 2008-04-28
Try this:

```

To fix file permissions after copying (works on home directory also DAMHIKT)

Navigate to the top file that you want to change along with everything below,

sudo chown -R username:username .

Note the dot

then 

sudo chmod -R u_rwx .

again, note the dot.

```

---

### Post by daimaru on 2008-04-28
> **thebarefootmarauder said:**
> Okay.  Still waiting to see if more of my files will be copied.  I think cause there are a lot of them it is taking a while.

The terminal isn't bringing up the testuser@jill-laptop etc. again.  Will it do that when it is finished copying?
while the files are beeing copied you will not get the prompt. only after it has finished copying you'll get the testuser@jill-laptop:~$ prompt again. so be patient, maybe it is working :)

you could have used the sudo cp -v -R somedir  option -v meaning verbose so it would have showed you the file progress.

okay I always mess this command up. You have to use 
sudo chown -R testuser /home/testuser/jillbackup2/ to change the permissions somehow the * thing does not seem to work. I just tried it omitting the -R option and it still recursively changed every file in that directory and its subdirectories ...  don't know why but hey it worked. .)

---

### Post by thebarefootmarauder on 2008-04-28
> **daimaru said:**
> while the files are beeing copied you will not get the prompt. only after it has finished copying you'll get the testuser@jill-laptop:~$ prompt again. so be patient, maybe it is working :)

you could have used the sudo cp -v -R somedir  option -v meaning verbose so it would have showed you the file progress.

Ah.  Then I do believe you will be the most successful person to work with my computer today.

Thank you so much.  Like before my impatience has gotten me into a world of trouble.  Good thing I double checked myself.  Hopefully all goes well this evening -fingers crossed.

---

### Post by thebarefootmarauder on 2008-04-28
> **dondad said:**
> Try this:

```

To fix file permissions after copying (works on home directory also DAMHIKT)

Navigate to the top file that you want to change along with everything below,

sudo chown -R username:username .

Note the dot

then 

sudo chmod -R u_rwx .

again, note the dot.

```

Thank you for this code and thank you to Daimaru for all your help.  All my files were retrieved and opened in the testuser account.

Thanks to you two, only my personal settings were lost by my stupidity.  Rest assured, I will not trying code again without supervised help.

Quick question - how do I cleanly delete my jill account and rename the testuser one?  It isn't that important, but I would like to clean house.

---

### Post by daimaru on 2008-04-30
I read something about usermod command to change your account name, but I never used it. Since i know nothing on this matter I guess it would be safer for you to google this matter or open a new post in the forums. 

I will try this tomorrow if i have time after work. So I can report back then.

---

