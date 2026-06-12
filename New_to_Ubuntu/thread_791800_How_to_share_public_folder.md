---
title: "How to share public folder"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by DawnDisciple on 2008-05-12
I am trying to share my public folder across the network but Ubuntu is tell me once again that I don't own it, I would like to know who does own it.:)

---

### Post by Paqman on 2008-05-12
If you right-click on any folder you can check the permissions. In your case I suspect the folder is owned by "root" which means that to make any changes to it you would need to use sudo.

If you want to take permanent ownership of a folder you can use the command chown in the terminal, to tweak the permissions of the folder a bit more finely you can use chmod. Google it or search these forums for more info about how permissions/chown/chmod works.

It's actually a really great security system once you get used to it.

---

### Post by hyper_ch on 2008-05-12
how do you try to share and what folder are you trying to share?

---

### Post by DawnDisciple on 2008-05-12
> **hyper_ch said:**
> how do you try to share and what folder are you trying to share?

I am trying to share the folder called Public, if I right click on Public I get the sharing option in the menu, but when I try to aply I get stopped there.
I want to share the folder as I would in windows where we can share files over our home network.

---

### Post by ace007 on 2008-05-12
Could you be specific about what the error is.  We cant be sure what the problem is exactly until we know.  Anything else is speculation.


To see who owns a folder cd into the directory and use ls -l.  If the public folder is on the root.

```

cd /Public
ls -l

```

---

### Post by DawnDisciple on 2008-05-12
> **ace007 said:**
> Could you be specific about what the error is.  We cant be sure what the problem is exactly until we know.  Anything else is speculation.


To see who owns a folder cd into the directory and use ls -l.  If the public folder is on the root.

```

cd /Public
ls -l

```

No error really, I just get told that I don't have permissions to share the folder named public and for the life of me I can't find a way to give myself permissions or ownership.

---

### Post by ZabiGG on 2008-05-12
Check out this thread:

[http://ubuntuforums.org/showthread.php?t=269330](http://ubuntuforums.org/showthread.php?t=269330)

found it very informative.

Cheers

---

### Post by DawnDisciple on 2008-05-12
> **ZabiGG said:**
> Check out this thread:

[http://ubuntuforums.org/showthread.php?t=269330](http://ubuntuforums.org/showthread.php?t=269330)

found it very informative.

Cheers

Thanks, but I don't think thats quite what I'm looking for...
[Drag a home or computer icon to panel] Don't have a clue what this means.
What is this nautilus?

---

### Post by sdowney717 on 2008-05-12
try this
at a terminal type 
sudo nautilus

then you might be able to use the gui to change permissions.

---

### Post by ace007 on 2008-05-12
Nautilus is the file manager that you use as default with Gnome.  When you are right clicking on the folder, the folder and window you see are nautilus.  By running the command...

```

gksudo nautilus

```

You will be running the file manager as the root.  That may solve the problem since Nautilus will see you now as someone with root permissions.

EDIT: the sudo command is the same as gksudo here

---

### Post by Ripfox on 2008-05-12
Actually you want to use 

> gksu nautilus

Running with "sudo" can occasionally cause problems I am told.

Did you try just logging out then back in after installing sharing services?

Try rebooting if that doesn't work, it's a known bug.

---

### Post by sdowney717 on 2008-05-12
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)
yes, I suppose gksudo is a little better.

---

### Post by Ripfox on 2008-05-12
> **sdowney717 said:**
> [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)
yes, I suppose gksudo is a little better.

I was told that 

> gksu nautilus

is even preferable to 

> gksudo nautilus

(I just learned this)

---

### Post by ace007 on 2008-05-12
gksu is actually just a front end GUI for gksudo

---

### Post by Ripfox on 2008-05-12
So...no difference then. Hmm, so many opinions. That sounds right though.

---

### Post by ZabiGG on 2008-05-12
I meant the third post from the top:

> **rbprogrammer said:**
> i'm the same way, but what i do to still maintain a level of security (especially from myself screwing up the system), i put myself into the group [admin] or [adm] or both and everytime i need to do something with a protected file that is used for root, i change the file's group to [admin] or [adm].

to change a group:
sudo chgrp admin /path/to/file/or/folder

to change permissions on that file/folder:
sudo chmod --- /path/to/file/or/folder

now the [---], the first dash is the owner, the second dash is the group and the last dash is everyone else.  each dash can have a 1,2,3,4,5,6, or 7.

4 = read
2 = write
1 = execute

the most common code that i use is 775, which for the:
owner - read, write, and execute access
group - read, write, and execute access
others - read and execute access

then the command would be:
sudo chmod 775 /path/to/file/or/folder

hope that helps........

---

### Post by bodhi.zazen on 2008-05-12
To start with it sounds as if you do not understand permissions ;

[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

============

Next, be careful ...

Do not go changing the permissions of system files, anything outside of home, unless you understand what you are doing.

Also be careful running nautilus with root permissions (gksu natuilus).

FYI gksu is a symbolic link to gksudo (so gksu == gksudo )

============

Best option then is to either:

1. Share a directory in your home directory.

2. Change the ownership and permissions of the public directory. 

If the full path to "/Public" is /Public you can :

```
sudo chown root.users /Public
sudo chmod 770 /Public
```

With that change you should be good to go.

---

### Post by TitanTiger on 2008-05-12
I did the change above (chown and chmod) and now the folder is locked and has an X next to it.  When I try to share the folder, it says it can't change the permissions for it.  In Properties, the owner shows as root and the group is users and says at the bottom "You are not the owner so you cannot change permissions."

---

### Post by DawnDisciple on 2008-05-13
Hello! For some strange reason I couldn't get any console/terminal commands to work, kept getting "command unknown" or no such file or folder, but in the end one did work and that was "gksudo nautilus" then I could gain permissions and make the folder public, nautilus is the equivalent of windows file manager, yes?.
I can see learning how to use Ubuntu is going to be a tad differcult. :)

At the moment I am having trouble getting to grips with the file system in Ubuntu, it's strange.

---

### Post by autigers1970 on 2008-05-13
I've tried everything on this thread and I'm still not gaining ownership of the folder.  Maybe I've done something wrong, but I'm not sure what.

---

### Post by bodhi.zazen on 2008-05-13
If you are having difficulty with permissions we need more information.

1. Can you post the output of (run as your user not root):

```
id
```

2. Permissions of the directory :

```
ls -l /path/to/directory/conatining/Public
```

for example if public is in /

ls -l /

if it is in home

ls -l ~

@ TitanTiger, my guess is you are not a member of the group "users"

@ autigers1970, insufficient information.

[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by TitanTiger on 2008-05-13
> **bodhi.zazen said:**
> If you are having difficulty with permissions we need more information.

1. Can you post the output of (run as your user not root):

```
id
```

2. Permissions of the directory :

```
ls -l /path/to/directory/conatining/Public
```

for example if public is in /

ls -l /

if it is in home

ls -l ~

@ TitanTiger, my guess is you are not a member of the group "users"

@ autigers1970, insufficient information.

[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

I will do this as soon as I get home this afternoon.  Thanks.

---

### Post by DawnDisciple on 2008-05-13
Well, I have managed that little problem, now to try the massive near imposable task of installing Quake wars. :)

---

### Post by TitanTiger on 2008-05-13
> **bodhi.zazen said:**
> If you are having difficulty with permissions we need more information.

1. Can you post the output of (run as your user not root):

```
id
```

**uid=1000(titantiger) gid=1000(titantiger) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),107(fuse),109(lpadmin),115(admin),1000(titantiger)**


> 2. Permissions of the directory :

```
ls -l /path/to/directory/conatining/Public
```

for example if public is in /

ls -l /

if it is in home

ls -l ~

**total 0**

---

### Post by TitanTiger on 2008-05-13
In the mean time, I installed samba and rebooted.  It finally worked.  My iMac can now see the shared folder on Ubuntu.

Forgive me if that was an obvious thing that should have been done before.  I'm a total n00b right now.

---

### Post by bodhi.zazen on 2008-05-13
The directory is "locked" because you are not in the users group. You can add yourself to the users group or assign ownership to a new group.

The command ls ..... did not work because you did not use the path to /Public.

Where is directory /Public located ?

---

### Post by DawnDisciple on 2008-05-14
> **bodhi.zazen said:**
> 
Where is directory /Public located ?

That is what I would like to know, what is the file structure in Ununtu?
in windows its C: windows, program files and the like, you know your programs are installed in program files, you know your system files are in windows, but with Ununtu I haven't a clue how its structured, it seems to change with the weather. :)

---

### Post by ZabiGG on 2008-05-14
There's all the info you need in the this thread, DD ;)

Happy reading,

[http://ubuntuforums.org/showthread.php?t=790485](http://ubuntuforums.org/showthread.php?t=790485)

ZabiGG

---

### Post by DawnDisciple on 2008-05-14
> **ZabiGG said:**
> There's all the info you need in the this thread, DD ;)

Happy reading,

[http://ubuntuforums.org/showthread.php?t=790485](http://ubuntuforums.org/showthread.php?t=790485)

ZabiGG

Very good, love it, thanks :)

---

### Post by Ichido on 2008-05-14
> **ace007 said:**
> Nautilus is the file manager that you use as default with Gnome.  When you are right clicking on the folder, the folder and window you see are nautilus.  By running the command...

```

gksudo nautilus

```

You will be running the file manager as the root.  That may solve the problem since Nautilus will see you now as someone with root permissions.

EDIT: the sudo command is the same as gksudo here

Is there a way to create an Icon/Link, that I can click on, to run Nautilus as root so I do not have to bring up a Terminal every time I need to do this?

I like the Gnome Commander better, so is there a way to run Gnome Commander as root?

---

### Post by plentyTypos on 2010-07-04
> **bodhi.zazen said:**
> If you are having difficulty with permissions we need more information.

1. Can you post the output of (run as your user not root):

```
id
```2. Permissions of the directory :

```
ls -l /path/to/directory/conatining/Public
```for example if public is in /

ls -l /

if it is in home

ls -l ~

@ TitanTiger, my guess is you are not a member of the group "users"

@ autigers1970, insufficient information.

[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)


I just thought to mention here that you should also be able to drag and drop folder icons to Terminal, in other words if a person is struggling with this unfamiliar command line way then using drag-and-drop can help. For example if you type into a terminal window:
ls -l 
(and please note that it should have a space at the and), then drag from a Nautilus window the icon of the folder you're trying to get info on, the path should end up there where you want it, eg:
ls -l '/home/someusername/Public'

In case it helps. I should add that I'm writing this from Ubuntu Lucid, but I'd imagine that this drag-and-drop way has worked in previous versions too.

---

### Post by plentyTypos on 2010-07-04
Oh and re dragging a folder onto the terminal window: if you're trying to get info for a folder with the "ls" command then you might add the "d" option, eg:
ls -ld '/home/ausername/Public'

You can type in terminal:
man ls
to read the manual ("man") for "ls".

---

### Post by zer010 on 2010-12-02
I was reading this thread in hopes of finding out what specific purpose the "Public" folder serves.  However, I kept noticing that a lot of people kept asking where the "Public" folder is.  It is quite simply this: ~/Public.  Is it just a pre-named folder that is useful as a place to start sharing files,  just as "Music" is a pre-named folder that is useful for storing music files?  I guess a better way to ask is, do any applications/features specifically point to or refer to ~/Public?

---

