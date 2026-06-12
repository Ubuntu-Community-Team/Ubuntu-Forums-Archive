---
title: "How do I install the game Tremulous?"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by dcdrac on 2008-07-31
I have jsut installed Ubuntu adn found that I cannot change ownership of folders and files, or permissions even follwoing what is in the help file what am i doing wrong?

Consequently I cannot get anything to save or install

---

### Post by tuxxy on 2008-07-31
Are you logged as guest, try right click the folder/icon select properties, then permissions

---

### Post by dcdrac on 2008-07-31
I have done all that, the permissions tab is all greyed out and stuck on ROOT

---

### Post by tuxxy on 2008-07-31
system > admin > users and groups

Check that you have the privileges to do so for this account

---

### Post by Darkade on 2008-07-31
You can do it in a terminal
```
sudo chown $useername $folder
```
will make you the owner of a folder, then you can change the permissions with
```
chmod 755 $folder
```
755 will give you total access to a folder (if you are the owner)
7=111 in binary first one is for reading second for writing last one for executing 
the first 7 are the permissions for the owner, the first 5 for the group and the the second 5 for everyone else's permissions...
can find a lot more, and better explained here
[http://www.ss64.com/bash/chown.html](http://www.ss64.com/bash/chown.html)
[http://www.ss64.com/bash/chmod.html](http://www.ss64.com/bash/chmod.html)

---

### Post by silkstone on 2008-07-31
What files are you trying to change the permissions for? You shouldn't need to change permissions for system files.

Files in your home folder - /home/yourusername/* - should be owned by you.

Are you saying that your home folder is owned by root?

---

### Post by dcdrac on 2008-07-31
sorry i do not know

---

### Post by dcdrac on 2008-07-31
it looks like the home directory is stuck on Root

---

### Post by halitech on 2008-07-31
ok, lets go back to basics for a minute. what folder or file are you looking at that you want to change ownership or permission of?

---

### Post by dcdrac on 2008-07-31
usr is the folder, and i opened a file in test editor and when i had finished i was told i od not have permissons to save it.

---

### Post by arpanaut on 2008-07-31
Have a read: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

But let me add that you shouldn't be altering files outside your Home folder UNLESS you really know what you are doing.
What are you trying to accomplish?

---

### Post by halitech on 2008-07-31
> **dcdrac said:**
> usr is the folder, and i opened a file in test editor and when i had finished i was told i od not have permissons to save it.

that would be why, /usr is outside of your home folder and with the way security (and the file system is set up) you, as a normal user do not have permission to do anything outside your home folder. Have a read on the previous link and hopefully you'll understand better

---

### Post by Darkade on 2008-07-31
/usr is a system folder, due to security you don't own it and that's fine.
if however you want to edit a file inside /usr you can type in a terminal

```
gksudo gedit /user/$file
```

however be aware that you must know what you are doing when editing a system file.

and halitech is so right! why didn't we first asked what folder/file did dcdrac wanted to change the permissions? :oops:

---

### Post by dcdrac on 2008-07-31
I am trying to install an app it gets so far and tells me i do not have permission to write to usr/local/ games and stops dead.

---

### Post by halitech on 2008-07-31
> **Darkade said:**
> /usr is a system folder, due to security you don't own it and that's fine.
if however you want to edit a file inside /usr you can type in a terminal

```
gksudo gedit /user/$file
```

however be aware that you must know what you are doing when editing a system file.

and halitech is so right! why didn't we first asked what folder/file did dcdrac wanted to change the permissions? :oops:

maybe I'm the only one thinking logically today ;)


> **dcdrac said:**
> I am trying to install an app it gets so far and tells me i do not have permission to write to usr/local/ games and stops dead.

what app is it you are trying to install?

---

### Post by dcdrac on 2008-07-31
Just a game , thing is is this goign to happen every time i try and put a new app on.

the game is tremulous

---

### Post by halitech on 2008-07-31
if it is an app from Synaptic then otehr then askign for your password once, no you shouldn't have any other issues. If it is something you are downloading from outside, then yes you may run into this again if all the files do not go in your home folder

---

### Post by aysiu on 2008-07-31
This is a good read for you:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by arpanaut on 2008-07-31
tremulous is in the repositories, should install prety seamlessly from Synaptic.

---

### Post by aysiu on 2008-07-31
You may want to go to System > Administration > Software Sources first to make sure the **Multiverse** repositories are enabled.

Then you can install Tremulous using Synaptic.

If you don't know how to use Synaptic Package Manager, read this:
[http://www.psychocats.net/ubuntu/installingsoftware#synaptic](http://www.psychocats.net/ubuntu/installingsoftware#synaptic)

---

### Post by ByteJuggler on 2008-07-31
/usr is a system folder which you won't by default have any permission to write to.  This is intentional.

You should only save files you create in the normal process of using your computer under your home folder, e.g. /home/joe or whatever (where "joe" is obviously replaced by your username.)  Click on "Places"->"Home Folder" and a windows in your home folder will open up.

If and when you need to edit files in system controlled locations, you should use "sudo" or "gksudo" to perform the command with administrator/root privileges.

Hope that helps.

Edit: sorry didn't read the entire thread before posting (so hence have repeated what others have said.)

---

### Post by ByteJuggler on 2008-07-31
> **dcdrac said:**
> Just a game , thing is is this goign to happen every time i try and put a new app on.

the game is tremulous

No, as a general rule you should not be manuanlly copying/installing games by hand.  Ubuntu has a very extensive and powerful package/software management system that takes care of installing, configuring and tracking software on your system.  You should always strongly prefer to try and get a native Ubuntu (or failing that Debian) package of the software you want to install, and then use the package management software (Synaptic etc.) to install it.

Tremulous is in the default Ubuntu repositories, so you should be using Synaptic (or possibly the simplified/simpler "Add/Remove Applications") to install it.

---

### Post by dcdrac on 2008-08-01
Thanks for all the replies i have learnt a lot and will have a play and sut off that old Unix commands book i have somehweree around here

---

