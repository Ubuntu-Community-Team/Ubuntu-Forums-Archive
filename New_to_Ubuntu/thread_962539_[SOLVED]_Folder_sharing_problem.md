---
title: "[SOLVED] Folder sharing problem"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by boof1988 on 2008-10-29
I'm trying to share a folder, [COLOR="Blue"]to all users of Ubuntu on this desktop machine[/COLOR], in /home.  'root' is the current "owner" of this folder.

This is the machine:
[LIST]
[*]AMD64 Processor
[*]OS is Ubuntu 8.04.1
[*]/home (own separate partition) filesystem is reiserfs
[*]It's a dual-boot machine with WinxP
[/LIST]

When I typed "shares-admin" in Terminal, the following warning displayed:

```
(shares-admin:9073): Gtk-WARNING **: Unknown property: GtkComboBox.items
```

The first time this warning occurred, an option box said I needed file-sharing applications installed and gave two options [NFS(unix) and SMB(windows)] and so I had both installed.

The second time the warning appeared but the "Shared Folders" dialog did open.  I selected "add folder", selected the folder to share, unchecked "read only" and clicked "share".

When I open /home in Nautilus, I can only view and copy the contents.  I would like the contents to be viewable/editable/deletable for myself and one other user.  Can someone help me share the folder and understand the warning?  If someone could help me understand how it's determined who gets the permissions, that would be helpful.

If there is a way I can do this in Terminal (using chown?), that would be fine, I like to learn new stuff and how to have more control over stuff.  I've read the results of:

```
info chown
```

and I still not comfortable doing it myself.

Thanks!

---

### Post by yman on 2008-10-29
Are you trying to share /home/yman, or /home/yman/public?
(the above directory paths are examples)

Are you trying to share it with another user on the same system, across the network, or with the WinXP system that's on the same machine?

---

### Post by Sarmacid on 2008-10-29
Using ls -al will show you the permissions the user, group, and everybody else has over that file/directory in that order. To change those permissions, you can use chmod. If you have more users, I'd suggest creating a group, add the 2 users you want sharing the folder, give full permissions to those users and none for everybody else.

---

### Post by boof1988 on 2008-10-29
> **yman said:**
> Are you trying to share /home/yman, or /home/yman/public?
(the above directory paths are examples)

I'm trying to share (sharedfolder) /home/sharedfolder.  Aha... Do I have to be logged in as 'root' or use sudo/gksudo to share this folder?

> **yman said:**
> Are you trying to share it with another user on the same system, across the network, or with the WinXP system that's on the same machine?

Eventually I want to share it on my home network, for now I just want to share it with both users on the same system (computer).

Thanks for the questions.  I tried to clarify in the OP.

---

### Post by tarps87 on 2008-10-29
The way you are trying to do it is setting up a share on a network hence the samba warning.
The quickest way is the chmod command:

```
sudo chmod a+rw fileName
```
This allows read and write access to all users

a = all
u = user
g = group
o = other

+ = add privilege
- = remove privilege

r = read
w = write
x = execute

more information on chmod can be found by using```
man chmod
```

```
ls -l
``` will list all file/folders and there permsions

I beleve you can also right click and change this in propeties

the command chown will change ownership
```
man chown
```
For more details

Hope this helps

---

### Post by boof1988 on 2008-10-29
> **Sarmacid said:**
> Using ls -al will show you the permissions the user, group, and everybody else has over that file/directory in that order. To change those permissions, you can use chmod. If you have more users, I'd suggest creating a group, add the 2 users you want sharing the folder, give full permissions to those users and none for everybody else.

Here's the results of <ls -al>:

```
bs@kpdesktop:/home$ ls -al
total 2
drwxr-xr-x  6 root root  128 2008-10-27 20:04 .
drwxr-xr-x 23 root root  704 2008-10-29 07:05 ..
drwxr-xr-x 34 bs   bs   1456 2008-10-29 11:23 bs
drwxr-xr-x  3 root root   80 2008-10-27 20:04 sharekpd

```

I am bs and I want 'sharekpd' to have unlimited access to myself and one  other user yet to be created.

I created a group (gpsharekpd) and added myself to it.  The other user is not created yet.

Will create the other user and report back.  I need to look up (or you could tell me) how to use chmod to change permissions.

---

### Post by Sarmacid on 2008-10-29
Based on tarps87's post:

```
sudo chmod -R a+w sharekpd
```

Will give users in the group writing permissions, wich is what you're missing
```
d|rwx|r-x|r-x
```
That means it's a directory, readable/writable/executable by your user, readable/executable by the group, readable/executable by everyone else.

---

### Post by tarps87 on 2008-10-29
Quick explination of the output of ls -al
drwxr-xr-x
d = directory
next there are three set of three:
rwxr-xr-x
1st three = user
2nd three = group
3rd three = other

r = read
w = write
x = execute

If the folder is owned by root you will need to use sudo, if it is owned or you have write access you do not need to use sudo

root root are the owner and group in that order
for you home folder bs
drwxr-xr-x 34 bs   bs   1456 2008-10-29 11:23 bs
you are the owner and it is in the group bs also only you have write access

---

### Post by yman on 2008-10-29
> **boof1988 said:**
> I'm trying to share (sharedfolder) /home/sharedfolder.  Aha... Do I have to be logged in as 'root' or use sudo/gksudo to share this folder?

Yes.

However, I think you fail to understand the purpose and proper use of /home. I wrote a long reply but my college's annoying authentication system caused it all to get lost.

/home holds the personal home folders of all users on the system. A home folder is where a user stores personal files and settings. To create a home folder manually just in order to share some files doesn't sound like following best practices to me. Perhaps it would be better to create a folder inside your home folder and use that for sharing? This could for instance be the folder Public, so then you'd be sharing /home/boof1988/Public.

EDIT: /home = C:\Documents and Settings
/home/yman = C:\Documents and Settings\yman
/root = C:\Documents and Settings\Administrator (I think)

> 
Eventually I want to share it on my home network, for now I just want to share it with both users on the same system (computer).

Thanks for the questions.  I tried to clarify in the OP.
Sharing over the network (presumably with Windows computers) isn't the same as sharing with other users of the same system. To share with other users on the same system, create a group and give that group read and write access to the folder you want to share. To share over the network right-click on the folder, select "Sharing Options" from the context menu, and choose the options that suit you.

---

### Post by boof1988 on 2008-10-29
> **Sarmacid said:**
> Based on tarps87's post:

```
sudo chmod -R a+w sharekpd
```

Will give users in the group writing permissions, wich is what you're missing

I did that and now sharekpd is rwxrwxrwx.  Sweet!  There wont be any 'other' users on the computer so the rwx for "other" is fine.  I'll log on as the other user and make sure they have access (they should).

> **Sarmacid said:**
> ```
d|rwx|r-x|r-x
```
That means it's a directory, readable/writable/executable by your user, readable/executable by the group, readable/executable by everyone else.

Thanks to Sarmacid and tarps87 for the help and explanations.

I'll try and figure out if I can remove the rwx for 'other users'.

Here's some popcorn...

:popcorn:

and a gold star...

:KS

Off-Topic...
[INDENT]"tarps" stands (in Naval Air lingo) for Tactical Air Reconnaissance Pod System :)[/INDENT]

---

### Post by boof1988 on 2008-10-29
> **yman said:**
> Yes.

However, I think you fail to understand the purpose and proper use of /home. I wrote a long reply but my college's annoying authentication system caused it all to get lost.

/home holds the personal home folders of all users on the system. A home folder is where a user stores personal files and settings. To create a home folder manually just in order to share some files doesn't sound like following best practices to me. Perhaps it would be better to create a folder inside your home folder and use that for sharing? This could for instance be the folder Public, so then you'd be sharing /home/boof1988/Public.

EDIT: /home = C:\Documents and Settings
/home/yman = C:\Documents and Settings\yman
/root = C:\Documents and Settings\Administrator (I think)


Sharing over the network (presumably with Windows computers) isn't the same as sharing with other users of the same system. To share with other users on the same system, create a group and give that group read and write access to the folder you want to share. To share over the network right-click on the folder, select "Sharing Options" from the context menu, and choose the options that suit you.

Thanks for the advice.  I'm not to good at making good organizational or best-practice decisions.

Will try to absorb what you've said here and apply it.

I'll wait to apply the [Solved] to the thread until I have the sharing stuff in a "best practice" (I like that term) way.

Thanks so much.

---

### Post by boof1988 on 2008-10-29
Quick question...

The folder "sharekpd" (output of ls -al) now shows up in green highlight.  What does that indicate?

EDIT: I think I figured this out... The highlight means that "other" non-logged in users have some rwx access?

---

### Post by tarps87 on 2008-10-29
> **boof1988 said:**
> 
I'll try and figure out if I can remove the rwx for 'other users'.


To remove permissions use - instead of +
```
chmod o-rwx fileName
```

> **boof1988 said:**
> 
Off-Topic...
[INDENT]"tarps" stands (in Naval Air lingo) for Tactical Air Reconnaissance Pod System :)[/INDENT]

Learn something new everyday, just short for my last name :)

---

### Post by boof1988 on 2008-10-29
I copied the folder "sharekpd" and pasted it into bs/Public ("bs" is my user name).

Now I want to change the ownership to the other user "kp" (cause it's kp's stuff).  Oh... Now I see...  Files/folders are owned by a user "kp", "bs" or "root" but rwx privileges on these files can be created for groups, users and 'other'?

So...

To give ownership of folder "sharekpd" and it's subfiles to kp I use?:
```
chown -hR kp /sharekpd
```

Since I copied (instead of cut/paste) "sharekpd", I want to delete folder "sharekpd" and contents from /home.  I already checked in /home/bs for it and it is there (I also have the info on a CD).  Do I use?:

```
cd ..    {To get to /home: I've done this already}
dir    {To make sure "sharekpd" is located here: I've done this}
rm -sharekpd    {To delete(remove) "sharekpd" and contents from /home: I haven't done this yet}

```


References:
[[COLOR="Blue"]Basic Commands at Ubuntu Community[/COLOR]](https://help.ubuntu.com/community/UsingTheTerminal?action=show&redirect=BasicCommands)

---

### Post by Sarmacid on 2008-10-29
> chown -hR kp:mygroup sharekpdNot sure what the -h does, but you need to remove the '/', that's the root folder. From what I understood, the path is /home/bs/public/sharekpd. Change mygroup for the group you want the directory to be owned by.

```
cd ..    {To get to /home: I've done this already}
dir    {To make sure "sharekpd" is located here: I've done this}
rm -sharekpd    {To delete(remove) "sharekpd" and contents from /home: I haven't done this yet}
```

```
cd /home/ #same thing as cd .. in this case
ls #to list files
rm -r sharekpd #to remove the folder from your home
```
Next time you want to move something instead of copying it, you can use ```
mv file newdestination
```

> he folder "sharekpd" (output of ls -al) now shows up in green highlight. What does that indicate?
That's a way of indicating the permissions set. If you go to /usr/bin you'll see tons of green stuff, because they have execution permission.

---

### Post by boof1988 on 2008-10-29
Thanks again for the help.  This has been so instructuve.

I'm going to keep the previous folder of "sharekpd" in /home for a while to learn on and then I'll remove it.

I also learned that there can be more than one Terminal screen open and each can be operating in different directories (I like using the word "directories" better than "folders"... not sure if they're the same or not).

I mark it [SOLVED].

---

