---
title: "Problems after making a /home/ partition"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by KosmicheCam on 2008-09-25
Hi all, I am a newcomer to linux and am just spending some time trying to set everything up. After installing Ubuntu 8.04 LTS, I decided it was a good idea to move my /home/ folder to its own partition. I was careful to follow this guide:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Everything worked fine, and I don't think I messed up any commands, but I've had some problems after rebooting.

**1)** First I was unable to login as my username. I got the error *"User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. Users $HOME directory must be owned by user and not writable by other users."*.

When I pressed OK, I got this: *The GNOME session manager was unable to lock file '/home/justin/.ICEauthority'. Please report this as a GNOME bug. Sometimes this error may occur if the file's directory is unwriteable, you could try loggin in via the failsafe session and ensuring that it is.*

**2)** I was able to log into a failsafe terminal and change the home permissions with the help from [this post]("http://ubuntuforums.org/showthread.php?t=909815&highlight=dmrc").

**3)** Now I can log on, but the desktop has reverted back to a 'default' state/resolution. I have lost the Emerald theme manager etc. and am unable to write to my home folder. (Actually I'm not sure how to tell whether it worked moving this to its own partition!!?!)

Is anybody able to suggest what I might have done wrong?
Is there something I can do?

Thank you - ah, it's painful being new!

---

### Post by asmoore82 on 2008-09-25
What filesystem type is your new /home partition - it needs to be a true unix/linux filesystem that can store permissions.

If that is right, then it sounds like you just need to copy all of the files -
especially the hidden ones - from your old home to the new one.

---

### Post by KosmicheCam on 2008-09-25
First thanks for your quick reply!

The new partition (/dev/sdb7) is EXT3 format.

After partitioning (on the live cd) I mounted both of the partitions and backed up/copied files over using these commands:

sudo mkdir /old
sudo mount -t ext3 /dev/hda1 /old
sudo mkdir /new
sudo mount -t ext3 /dev/hda7 /new

cd /old/home
find . -depth -print0 | sudo cpio --null --sparse -pvd /new/
sudo mv /old/home /old/home_backup
sudo mkdir /old/home

Would this have been sufficient or should I do something else?

---

### Post by taladan on 2008-09-25
if you can get into the command line you need to chown your home directory back over to your user.  It's going to look something like this:

chown -R user:user /home/user

where 'user' is replaced by your username.

Tal

---

### Post by KosmicheCam on 2008-09-25
> chown -R user:user /home/user

Thanks Tal,
I tried this line but it gave me *"Operation not permitted"*

---

### Post by KosmicheCam on 2008-09-25
Ah hold on, whoops. Just tried

sudo chown -R camandclaire:camandclaire /home/camandclaire

Which as allowed me to write to the home folder. It hasn't restored the settings I had previously, but not sure if that is possible...

---

### Post by taladan on 2008-09-26
I don't know that it will restore any settings, but it should allow you to log in to the gdm now - if the only thing keeping that from happening was the unwritable file.  have you tried restarting and logging in as the user?

Tal

---

### Post by Tatty on 2008-09-26
you may find that there are some files which are supposed to be owned by root in your /home.

To get a list of all the files in your old home which are owned by root, simply cd to your old home directory and then run:

```
ls -Rlah | grep " root "
```

you will then have to go through each file and chown them back to root in your new home directory.  To find the path for each file use:

```
locate <filename>
```

Its a bit manual and tedious, but it ensures there are no permissions issues.

---

### Post by shafin on 2008-09-26
The better way to do it is to try:
sudo chown -R root:plugdev /home, this way, the new partition is open for the users of the group plugdev, of which you should be a member

---

### Post by KosmicheCam on 2008-09-27
> **Tatty said:**
> you may find that there are some files which are supposed to be owned by root in your /home.

To get a list of all the files in your old home which are owned by root, simply cd to your old home directory and then run:

```
ls -Rlah | grep " root "
```

you will then have to go through each file and chown them back to root in your new home directory.  To find the path for each file use:

```
locate <filename>
```

Its a bit manual and tedious, but it ensures there are no permissions issues.

I haven't really been experiencing any more problems since I last posted, but thought I had better double check like you said. I followed your instructions and got a list of files owned by root in the backed up /home dir on /. Here's what I got:

```
drwxr-xr-x  3 root         root         4.0K 2008-09-24 02:38 .
drwxr-xr-x 22 root         root         4.0K 2008-09-26 19:26 ..
drwxr-xr-x  3 root         root         4.0K 2008-09-24 02:38 ..

```

I understood what you said about finding the path of each file, but I don't know the chown commands to use, or which folder to be in when I type them. Could you please help me with some code?

Thanks.

---

### Post by KosmicheCam on 2008-09-27
> **shafin said:**
> The better way to do it is to try:
sudo chown -R root:plugdev /home, this way, the new partition is open for the users of the group plugdev, of which you should be a member

Oh no! After entering this line of code, I could no longer open up Firefox or file browsers, then when attempting to log back in I have discovered I'm locked out again! I am getting the same 2 error messages:

*"User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. Users $HOME directory must be owned by user and not writable by other users.".* and

*The GNOME session manager was unable to lock file '/home/justin/.ICEauthority'. Please report this as a GNOME bug. Sometimes this error may occur if the file's directory is unwriteable, you could try loggin in via the failsafe session and ensuring that it is.*

After the last time I had to re-setup my email and ALL settings. I really don't want to have to do this again! I'm not sure where I went wrong... I'm not blaming you Shafin. I'm the one who does not know what he is really doing yet... If anyone could hel pget me out of this tricky situation, I'd be in their debt!

Thanks in advance.

---

### Post by KosmicheCam on 2008-09-28
Ok, I repeated Taladan's advice (from post #4) and am able to log back in. No settings have changed - huzzah!

I'd still like to make sure all the permissions are in order though... How do I change the ownership of those couple of files I identified in the old /home?

Thank you.

---

### Post by steveneddy on 2008-09-28
Not to throw a wrench in all of this, but this is the recommended way of gaining ownership of your /home folder.

```
sudo chmod 644 /home/your_username/.dmrc
sudo chown your_username /home/your_username/.dmrc
sudo chmod -R 700 /home/your_username
sudo chown -R your_username /home/your_username


```

---

### Post by KosmicheCam on 2008-09-28
Ok, no worries.

---

