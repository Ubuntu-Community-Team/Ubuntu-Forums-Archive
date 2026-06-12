---
title: "i have installed programs while logged in as root"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by trillions on 2008-08-19
but, when i log in as a normal user all my preferences are still the same.
i cant change any compiz settings, apply emerald themes, etc.
i cant access the VM i created in virtualbox...what do i do?
i swear if i fix this, i will never login as root ever again.

---

### Post by cariboo on 2008-08-19
You could try in a terminal:

```
sudo chown -R <user>.<user> /home/<user>/*
```

Where <user> is your username, and just to make sure the permissions are right:

```
sudo chmod -R 755 /home/<user>/*
```

You may get and error about .gvfs, just ignore it.

Jim

---

### Post by bingoUV on 2008-08-19
"still the same"?
So you installed programs, and changed preferences too as root?

Preferences are for a user. So you changed root's preferences. Fixing this is specific to the program. For compiz..
```

tar -cvzf ~/.compiz.tgz ~/.config/compiz
rm -r ~/.config/compiz
sudo cp -R /root/.config/compiz ~/.config/
sudo chown -R <user>:<user> ~/.config/compiz

```

---

### Post by trillions on 2008-08-19
"still the same"
meaning, the same as i left then, last time i was logged into the normal user.
i know i shouldnt have, but i was doing alot of things logged as "root". is there a way to apply all the changes i made in root to the normal user?
sry all the n00b stuff.
i love this OS, just having troubles adjusting

---

### Post by trillions on 2008-08-19
do i have to just reinstall all the programs again while logged in as a normal user?

---

### Post by bingoUV on 2008-08-19
> **trillions said:**
> is there a way to apply all the changes i made in root to the normal user?


that is what I wrote in my last post.

The programs you installed as root will remain installed. The change in preferences will have to be done again or transferred from root to normal user as explained in my last post. 

Change in preferences is specific to the user you are logged in as.

---

### Post by trillions on 2008-08-19
i have to change the preferences one application at a time?

i think i better just reinstall if thats the case, it would probably be faster.

---

### Post by scorp123 on 2008-08-19
> **trillions said:**
> i think i better just reinstall if thats the case, it would probably be faster. That's Windows thinking. It's not going to solve anything here, the settings will just remain the same.

See the other posting above, you were already given all information you need. Just transfer the settings over into your own account and voila you're done.

---

### Post by trillions on 2008-08-19
i look at your code and i weep. i know not what it means, nor what it does.
i copied it into terminal. it asked for my passwd. 

joshua@robot:~$ tar -cvzf ~/.compiz.tgz ~/.config/compiz
tar: Removing leading `/' from member names
/home/joshua/.config/compiz/
/home/joshua/.config/compiz/compizconfig/
/home/joshua/.config/compiz/compizconfig/config
joshua@robot:~$ rm -r ~/.config/compiz
joshua@robot:~$ sudo cp -R /root/.config/compiz ~/.config/
[sudo] password for joshua: 
joshua@robot:~$

not sure if anything happened or not.

all this just so i dont have to login as root...
ok, so, i suppose everything is in order except i cant get emerald to work. i have themes...they're installed, but when i click them to apply..nothing...

also, i still cannot access the virtual machine i created in virtualbox, i added myself to the group, but still nothing...

---

### Post by trillions on 2008-08-19
joshua@robot:~$ tar -cvzf ~/.emerald.tgz ~/.config/emerald
tar: Removing leading `/' from member names
tar: /home/joshua/.config/emerald: Cannot stat: No such file or directory
tar: Error exit delayed from previous errors
joshua@robot:~$ sudo cp -R /root/.config/emerald ~/.config/
[sudo] password for joshua: 
cp: cannot stat `/root/.config/emerald': No such file or directory
joshua@robot:~$ sudo chown -R root:joshua ~/.config/emerald
chown: cannot access `/home/joshua/.config/emerald': No such file or directory
joshua@robot:~$ 

is any of this correct?

---

### Post by bingoUV on 2008-08-19
After you have done the commands for transferring compiz settings to your user from root, restart compiz. Just hit ctrl-alt-baskspace and login again.

Virtualbox stores its virtual machines in the user's home directory, in ".VirtualBox". Home directory of root is /root. Home directory of any other user is /home/<user>, replacing <user> by the username. 

So for root, Virtualbox stores its virtual machines in /root/.VirtualBox. For any other user, it will be /home/<user>/.VirtualBox. Now, similar to the way we transferred settings for compiz, we go as follows
```

tar -cvzf ~/.VirtualBox.tgz ~/.VirtualBox
rm -r ~/.VirtualBox
sudo cp -R /root/.VirtualBox ~/
sudo chown -R <user>:<user> ~/.VirtualBox

```

The first step makes a backup in an archive ~/.VirtualBox.tgz, of the virtualbox settings for your normal user. Settings include the virtual machines.
Second step removes the virtualbox settings of the normal user. 
Third step copies root's settings to the normal user. Owner of root's settings file is root himeself. 
The fourth step makes the normal user the owner of these copied settings, so that the normal user now can use these settings.

Hope you notice the similarities in the steps for compiz and Virtualbox. Hope you also noticed the differenes. Hope you never login as root again.

You have to logout and login again after adding yourself to the group for virtualbox to work as expected.

---

### Post by bingoUV on 2008-08-19
> **trillions said:**
> joshua@robot:~$ tar -cvzf ~/.emerald.tgz ~/.config/emerald
tar: Removing leading `/' from member names
tar: /home/joshua/.config/emerald: Cannot stat: No such file or directory
tar: Error exit delayed from previous errors
joshua@robot:~$ sudo cp -R /root/.config/emerald ~/.config/
[sudo] password for joshua: 
cp: cannot stat `/root/.config/emerald': No such file or directory
joshua@robot:~$ sudo chown -R root:joshua ~/.config/emerald
chown: cannot access `/home/joshua/.config/emerald': No such file or directory
joshua@robot:~$ 

is any of this correct?

emerald does not seem to store its settings in ~/.config/emerald. Unless you know where emerald stores its settings you cannot transfer its settings from root to the normal user.

Hint: emerald stores its settings in ~/.emerald. ~ stands for home directory, /home/joshua in your case. By looking at the steps for virtualbox and compiz, transferring settings for emerald is left as an exercise to the reader.

To apply the transferred settings, ctrl-alt-backspace and login again.

---

### Post by trillions on 2008-08-19
ok, everything went well, except now when i open virtualbox i get this error message 

Could not create the default settings file '/home/joshua/.VirtualBox/VirtualBox.xml' (VERR_ACCESS_DENIED).


Result Code: 
0x80004005
Component: 
VirtualBox
Interface: 
IVirtualBox {2d3b9ea7-25f5-4f07-a8e1-7dd7e0dcf667}

---

### Post by trillions on 2008-08-19
emerald is working fine now! cheers!

---

### Post by scorp123 on 2008-08-19
> **trillions said:**
> Could not create the default settings file '/home/joshua/.VirtualBox/VirtualBox.xml' (VERR_ACCESS_DENIED). Check the permissions on that directory. Since you copied that stuff over from root's account it could still have root's permissions and not your's.

So, to find out what the permissions are - please type this stuff into a terminal: ```
ls -alR /home/joshua/.VirtualBox
``` ... Ideally all files should belong to user "joshua" (third column) and to group "joshua" (last column), and the permissions on all directories should say something like **[COLOR="Red"]drwx[/COLOR]r-xr-x** ... Only the first four letters are right now relevant for you:

d - this is a directory
r - you have permission to read there
w - you have permission to write there
x - you may execute things inside there; or in the case of directories: change into that directory

The letters after that concern the group you belong to, and then the last three letters concern "everyone else".

Please post the output of that "ls -alR" command here before you play around with permissions, OK? I am saying this because sometimes newcomers do a "overkill" and ruin everything by hastily setting the wrong permissions in all the wrong places .... So better post that output here and wait for feedback, OK? ;)

---

