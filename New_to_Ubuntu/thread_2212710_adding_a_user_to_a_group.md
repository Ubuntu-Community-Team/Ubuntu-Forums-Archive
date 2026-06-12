---
title: "adding a user to a group"
date: 2014-03-22
forum: New to Ubuntu
---

### Post by sniper8752 on 2014-03-22
I am trying to add bob, to the user group, accounting, using this command:
```
sudo usermod -a -G accounting bob
```
I do a ls -l on /home, and it tells me that the owner is bob, and the group, root.
I do a 
```
groups bob
```
and I get this:
```
bob: accounting sftpusers departments
```
Why is he part of the group, but yet, not showing up when I do the listing?

---

### Post by steeldriver on 2014-03-22
New group membership only takes effect at login - either log out and back in again or at least start a new login shell

```

su - bob
groups bob

```

Why is your /home owned by bob? It should be root:root

---

### Post by sniper8752 on 2014-03-22
I logged out, and logged back in, and when I run ls -l, it still shows root owns it for the group.  and when I do a ls -l, for home, it shows root:root.

---

### Post by Iowan on 2014-03-22
It's curious that bob isn't a member of the group bob.
Root should own /home, but bob should own /home/bob.
Adding bob to a group won't necessary change group ownership of previously created directories.

---

### Post by sniper8752 on 2014-03-22
I guess I do not understand why there needs to be a group, bob.  why would he not be a part of the accounting group?
root does own /home.  i did a ls -l, and for home: root:root.

---

### Post by Iowan on 2014-03-22
bob can be a member of multiple groups: the primary group and secondary groups.
[http://ubuntuforums.org/showthread.php?t=1688174](http://ubuntuforums.org/showthread.php?t=1688174)
Unless I've gotten myself confused, Ubuntu ordinarily creates a private group for each user.

---

### Post by bab1 on 2014-03-22
> **sniper8752 said:**
> I guess I do not understand why there needs to be a group, bob.  why would he not be a part of the accounting group?
root does own /home.  i did a ls -l, and for home: root:root.
That is the Linux way.  Unix has a primary group that is something like *staff* for normal users and *wheel *for admins.  In Debian (and therefore Ubuntu) the concept is for a *User Private Group*.  This makes user and group ownership the same, or, you could say there is only a need for *user* and *others*.

Adding a user to a group doesn't change the ownership of any file or directory objects.  The creator user and the primary group set the ownership.  You can, however, create an specific group inheritance by setting the SGID bit.

[COLOR="#0000FF"]Edit: See [here]("http://www-uxsup.csx.cam.ac.uk/pub/doc/redhat/redhat7/rhl-rg-en-7.0/s1-sysadmin-usr-grps.html") for for more information on UPG.[/COLOR]

---

### Post by sniper8752 on 2014-03-22
by default, it looks like the primary owner/group is root. although I did a [COLOR=#333333]cat /etc/group | cut -d: -f1, and it looks like there is a specific uid group number for each user.  but then if that is true, why does it say root for the /home/bob folder, when it should be bob for the group, and not root?[/COLOR] 
if I have a shared accounting folder then, would I add bob as a group user of accounting, then allow the group, accounting, which owns accounting, permission to access it, so then bob can access it?

---

### Post by bab1 on 2014-03-22
> **sniper8752 said:**
> by default, it looks like the primary owner/group is root. although I did a [COLOR=#333333]cat /etc/group | cut -d: -f1, and it looks like there is a specific uid group number for each user.  but then if that is true, why does it say root for the /home/bob folder, when it should be bob for the group, and not root?[/COLOR] 
if I have a shared accounting folder then, would I add bob as a group user of accounting, then allow the group, accounting, which owns accounting, permission to access it, so then bob can access it?

One Debian/Ubuntu systems the default ownership of /home is root:root.  The default ownership of /home/bob is bob:bob.  If this is not the case on your host then I would say it has been changed.

With Ubuntu, whatever you set a directory to has nothing to do with the ownership of the files/directories created below that directory.  At creation these objects are created with creator:creator ownership.  If you want to create a directory with the group as *accounting* and  have that inherited then you need to explicitly set that with chgrp and setting the SGID bit on the top most directory that you want (such as: /srv/data -- root:accounting)

---

### Post by sniper8752 on 2014-03-22
I see now that the defaults should be user:user.  I must have changed them.  
So to allow only particular users access to a shared, common folder, what would be the best way to do that?

---

### Post by bab1 on 2014-03-22
> **sniper8752 said:**
> I see now that the defaults should be user:user.  I must have changed them.  
So to allow only particular users access to a shared, common folder, what would be the best way to do that?
The best way to explain is to give you an example.  

First let's create the directory at /srv```

sudo mkdir /srv/data

```

Now we need to change the group to accounting
```
sudo chgrp accounting /srv/data
```

Now we need to make the /srv/data directory always use the accounting group as the group owner
```
sudo chmod 2775
```...the leading 2 sets the sgid bit for inheritance.

[COLOR="#0000FF"]Edit:  There is a bug in Ubuntu 13.10 regarding permissions.  If you are using this version of Ubuntu you need to apply an update to cure the bug.  Let me know if you need that.[/COLOR]

If you are working with a directory that has data in it then you need to use symbolic notation or you will set every file to executable in that branch of the file system.  To use symbolic chmod this is what you would use```

sudo chmod u=rwX,g=rwXs,o=rX /srv/data

```

Create files and directories inside of /srv/data and you will see the group is always accounting.

---

### Post by sniper8752 on 2014-03-22
Okay - thanks.  Seems to work.  I noticed that after I ran the chmod command, there was an 's' in the permissions.  What does this stand for?
and you may have answered this already, but I am able to only go into the accounting directory logged in as bob.  when i view the groups using ls -l on the home directory, he is root:root.  what specifies that he is part of accounting, giving him access?

---

### Post by Iowan on 2014-03-22
> **sniper8752 said:**
> ...what specifies that he is part of accounting, giving him access?The group membership you set up earlier. :)

---

### Post by bab1 on 2014-03-22
> **sniper8752 said:**
> Okay - thanks.  Seems to work.  I noticed that after I ran the chmod command, there was an 's' in the permissions.  What does this stand for?

That's the SGID bit that you set via the leading 2 in 2775.
> 
and you may have answered this already, but I am able to only go into the accounting directory logged in as bob.  when i view the groups using ls -l on the home directory, he is root:root.  what specifies that he is part of accounting, giving him access?
Iowan answered part of the question.  If you want other users to have access add them to the accounting group.  I have a question back.  What do you mean by this: *" when i view the groups using ls -l on the home directory, he is root:root."*?  If the data is indeed at /srv/data the ownership of that directory should be root:accounting.  This has nothing to do with the ownership of the home directory.  The home directory is not where you look to see what groups a user is a member of anyway.  You can do that with this command
```
id  bob
```

---

### Post by sniper8752 on 2014-03-23
I noticed that when I do a ls -l, it still shows root:root. But when I do id bob, it says the first group/gid is accounting.
Also, when I ftp to the server, bob can no longer access his folder, but everybody else's....

---

### Post by bab1 on 2014-03-23
> **sniper8752 said:**
> I noticed that when I do a ls -l, it still shows root:root.

Where are you using *ls -l*?  The command is to list the files and directories.  So what SPECIFICALLY are you listing? 
> 
But when I do id bob, it says the first group/gid is accounting.

It sounds like you made the _accounting_ group bob's primary group.  The user bob should always have the _primary group as bob_.
> 
Also, when I ftp to the server, bob can no longer access his folder, but everybody else's....
It's all in how you configured these things.

Post the output of ```
ls -l /home/bob
```

---

### Post by sniper8752 on 2014-03-23
> **bab1 said:**
> Where are you using *ls -l*?  The command is to list the files and directories.  So what SPECIFICALLY are you listing? 

It sounds like you made the _accounting_ group bob's primary group.  The user bob should always have the _primary group as bob_.

It's all in how you configured these things.

Post the output of ```
ls -l /home/bob
```
/home
didn't we change the group to accounting though?
[ATTACH=CONFIG]251415[/ATTACH]

---

### Post by Iowan on 2014-03-23
```
sudo usermod -a -G accounting bob
```

This command should have added **bob** to **accounting**

---

### Post by bab1 on 2014-03-23
> **sniper8752 said:**
> /home
didn't we change the group to accounting though?
[ATTACH=CONFIG]251415[/ATTACH]
Adding a user to a secondary group should not result in your primary group being root or accounting.  It should be bob.  Post the output of ```
id
```

Also post the output of ```
touch /home/bob/test.file
```

---

### Post by sniper8752 on 2014-03-23
I do a ls -l on /home, and it is still root:root.  And I think that he may have always been part of the accounting group?

---

### Post by bab1 on 2014-03-23
> **sniper8752 said:**
> I do a ls -l on /home, and it is still root:root.  And I think that he may have always been part of the accounting group?

Post the output of the commands I asked you to perform in the previous post.  We can only resolve this if you do that.

Cut and paste them into the editor.

---

### Post by sniper8752 on 2014-03-23
uid=1003(bob) gid=1004(accounting) groups=1004(accounting),1001(sftpusers),1007(departments)
For some reason, I am not able to "cd" to bob.  Right now, permissions for "others" are nothing (---).  Is that the problem?  Should it be something else?

---

### Post by bab1 on 2014-03-23
> **sniper8752 said:**
> ```
uid=1003(bob) gid=1004(accounting) groups=1004(accounting),1001(sftpusers),1007(departments)
```
For some reason, I am not able to "cd" to bob.  Right now, permissions for "others" are nothing (---).  Is that the problem?  Should it be something else?
The first thing I see that is wrong is that the primary group for the user *bob (uid=1003) * is not bob (gid=1003).  I would need to see what the ownership and permissions of the user bob's directory.  Post the output of ```
ls -ld /home/bob
```...this lists the directory (see the d) ownership.

Is bob a test user?  What is the output of this```
getent group 1000
```

---

### Post by sniper8752 on 2014-03-23
drwxr----- 4 root root 4096
test:x:1000
It is actually for a class assignment.

---

### Post by Iowan on 2014-03-23
Might need to change the primary group (back) for bob.

---

### Post by bab1 on 2014-03-23
> **sniper8752 said:**
> drwxr----- 4 root root 4096
test:x:1000
It is actually for a class assignment.


A couple of things.  The forum has rules against doing your homework for you.  I will advise but you need to be a part of the solution.  

Is this your machine?  Is test (uid=1000) the original user when you installed Ubuntu?  Let's put the output data in code brackets.  To do that you need to click on the [SIZE=4]**#**[/SIZE] icon at the top of the advanced editor.

If you want the user bob to be able to access the home directory you need to provide ownership rights as bob:bob.  Permissions are another matter.  The default is 770.  Since the user and group refer to the same account only that user has access. [COLOR="#0000FF"]Edit: I added a user the Debian way.  The permissions are 755 rather than 770.[/COLOR]

The user test should have the rights to modify the /home/bob directory via sudo.  What commands do you think should be used?  Indeed the user bob should have the primary group of bob with a gid that matches the uid number (e.g. 1003).

---

### Post by sniper8752 on 2014-03-23
> **bab1 said:**
> A couple of things.  The forum has rules against doing your homework for you.  I will advise but you need to be a part of the solution.  

Is this your machine?  What about the second piece of information I asked for?
This is not the assignment.  This is a very small part of it.  We are required to setup a network of servers/clients, and this is one of the many small issues that I am having.  I have a basic understanding, but am learning yet.  
test : x : 1000

---

### Post by bab1 on 2014-03-23
> **sniper8752 said:**
> This is not the assignment.  This is a very small part of it.  We are required to setup a network of servers/clients, and this is one of the many small issues that I am having.  I have a basic understanding, but am learning yet.  
test : x : 1000

The assignment is the entire thing.  I updated the previous post.  Re-read it.

---

### Post by sniper8752 on 2014-03-23
should I use chown bob:bob?

---

### Post by bab1 on 2014-03-23
> **sniper8752 said:**
> should I use chown bob:bob?The only user that can change the permission on that directory is root (via **S**witch **U**ser and **Do**).   You are applying it to a directory.  So it would be *sudo chown bob:bob <directory>*.  Do you know what the difference is between an absolute path and relative path re: the directory?  Before you change anything let me know.

You must be able to use sudo for this.  I would guess you need to log in as the user test.

---

### Post by Iowan on 2014-03-23
At the risk of getting too many cooks involved...
**chown **will fix the home directory, then you can fix the primary group with a command you've already used... just a different option.

---

### Post by bab1 on 2014-03-23
> **Iowan said:**
> At the risk of getting too many cooks involved...
**chown **will fix the home directory, then you can fix the primary group with a command you've already used... just a different option.
I'm trying to get the user to do his own homework here.  :-(    The chown command is only part of it, don't you agree?

---

### Post by sniper8752 on 2014-03-24
> **bab1 said:**
> The only user that can change the permission on that directory is root (via **S**witch **U**ser and **Do**).   You are applying it to a directory.  So it would be *sudo chown bob:bob <directory>*.  Do you know what the difference is between an absolute path and relative path re: the directory?  Before you change anything let me know.

You must be able to use sudo for this.  I would guess you need to log in as the user test.

it says invalid group when i do sudo chown bob:bob.  
and no, I am not sure.

---

### Post by bab1 on 2014-03-24
> **sniper8752 said:**
> it says invalid group when i do sudo chown bob:bob.  
and no, I am not sure.

Let's confirm that there is no user group named bob.  Post the output with this command```
getent group|grep 100
```

A path is absolute if the first character is a /; otherwise, it is a relative path. Relative to what?  The what is your current working directory.  If you are at /home then the directory bob contained in that /home directory and can be used like this to create a file:  *touch bob/test.txt*.  But if the user is in /home/john then the current working directory is /home/john.  The directory *bob* is not relative to the current working directory so t*ouch bob/test.txt* or any other command that uses a relative path like *bob/<somefile> *will fail.  On the other hand you can be in any working directory and use this: touch /home/bob/test.txt  When you use sudo chown you need to either use the absolute path or your current working directory must be /home.  You can fine what your current working directory is with this command```
pwd
```

The absolute vs relative path is explained a little more [here]("http://www.linuxnix.com/2012/07/abslute-path-vs-relative-path-in-linuxunix.html").

You can always use chown to just give the ownership of the directory to bob.  Something like [B]*sudo chown bob /home/bob * will work. to allow you to log in and use /home/bob.  You then would have to add the primary group of bob (gid=1003) back to the user bob.  That would allow you to assign the group bob to the user bob's account.  You do this first or after you change ownership.  The commands are slightly different if you add the group back first. Read the man pages ```
man chown
```

---

### Post by sniper8752 on 2014-03-24
I ran the command, and this is what I got.  It does not look like there is.

---

### Post by bab1 on 2014-03-24
> **sniper8752 said:**
> I ran the command, and this is what I got.  It does not look like there is.

Did you get rid of all the User Private Groups (groups with corresponding user names)?  Lets put the output in the code blocks like I showed you last night please.  It makes it much easier to read for me and others.

Post the output of this```
getent passwd|grep 1000
```

To add the bob group back you should use this```
sudo addgroup --gid 1003 bob
```...to make the group.

Then you can do this to make that group the primary group```
sudo usermod -g bob bob
```

Then you can change the group ownership on bob's home directory```
sudo chgrp bob /home/bob
```

---

### Post by sniper8752 on 2014-03-24
I don't recall removing them.  And I don't have guest tools installed, so I just had to use a screenshot.

---

### Post by bab1 on 2014-03-24
> **sniper8752 said:**
> I don't recall removing them.  And I don't have guest tools installed, so I just had to use a screenshot.

So this is a VM.  I sugesst you just kill it and start over then.

---

### Post by sniper8752 on 2014-03-24
And when I try to add the group, 1003 for bob, it says that it is already in use by ftpuser.   should i delete this user, then try again?

---

### Post by bab1 on 2014-03-24
> **sniper8752 said:**
> And when I try to add the group, 1003 for bob, it says that it is already in use.
See post #38

---

### Post by sniper8752 on 2014-03-24
Well, I've put a lot of hours into this.  Why should I kill it?  Would it be too much work to fix this?

EDIT:  I was able to add the group after removing the user.

---

### Post by steeldriver on 2014-03-24
There's no particular reason that the gid for group bob needs to be the same (1003) as the uid for user bob - it's just a convention. If you don't want to change the gid for ftpuser, you can create group bob without the --gid=1003 (letting the system choose the next available gid).

---

### Post by bab1 on 2014-03-24
> **sniper8752 said:**
> Well, I've put a lot of hours into this.  Why should I kill it?  Would it be too much work to fix this?

Yes it will take you longer to fix all of what is obviously wrong and you are going to keep bumping into stuff like this down the line.  The Debian/Ubuntu tools should be used for this kind of stuff.  For example when you created users you used the command **useradd**.  This is not the correct tool to use unless you manually add the options that Debian/Ubuntu have configured.  You should have used **adduser**.  Here is why```
adduser  and addgroup add users and groups to the system according to command line options
       and configuration information in /etc/adduser.conf.  ***They are friendlier front ends*** to the
       low  level  tools  like useradd, groupadd and usermod programs,[B][I] by default choosing Debian
       policy conformant UID and GID values, creating a home directory with  skeletal  configura&#8208;
       tion, running a custom script, and other features.[/I][/B]
```

Start over.  Install the system with you as the first account (the one used to install).  This will give your account the uid/gid of 1000.  Then we can redo what you need to have for the project.  I'm only going to say this one more time.  If you do things and then come back and ask "what did I do wrong", I'll stop responding.  It's far better to talk out what needs to be done so you understand completely before adding features that need to be redone.

Re-install with just the one user and come back.

Questions?

---

### Post by bab1 on 2014-03-24
> **steeldriver said:**
> There's no particular reason that the gid for group bob needs to be the same (1003) as the uid for user bob - it's just a convention. If you don't want to change the gid for ftpuser, you can create group bob without the --gid=1003 (letting the system choose the next available gid).
He's not using the Debian tools.  If you want to finish this be my guest.

[COLOR="#0000FF"]Edit: Remember -- This is a homework project and the forum does not want to be involved with giving answers to homework.[/COLOR]

---

### Post by sniper8752 on 2014-03-24
I think I may have gotten it to work.  The issue that remains yet, is that bob and marry are part of accounting.  They are both owned by the user (user:user), and they have their own user group ID.  marry has r-x for her group, but in filezilla, bob is still not able to access her directory.  shouldn't he be able to since they are of the same group, accounting?
EDIT:  Nevermind, I changed to chmod777, then to 750, and it seems to have reset it.  not sure why.

---

### Post by bab1 on 2014-03-24
> **sniper8752 said:**
> I think I may have gotten it to work.  The issue that remains yet, is that bob and marry are part of accounting.  They are both owned by the user (user:user), and they have their own user group ID.  marry has r-x for her group, but in filezilla, bob is still not able to access her directory.  shouldn't he be able to since they are of the same group, accounting?

They gain access if the file or directory has the group set as accounting and the proper permissions are set.  Being in the group accounting is only one part of the deal.  Once they are both part of the accounting group you need to set that group as the group owner on the object such as root:accounting with rwx (for dir) or rw (for file) permissions for the group.  The number 775 is user:group:others on a dir.  Likewise 664 is the same for a file.

---

### Post by sniper8752 on 2014-03-24
One last issue remains... When I add the following lines, I get a "network error: software caused connection abort".
sshd_config:
```
AllowGroups sftpusers sftp
Match Group sftpusers
ChrooDirectory %h
AllowTCPForwarding no
ForceCommand internal-sftp
```

I am trying to prevent the user from going outside of their home directory.

---

### Post by bab1 on 2014-03-24
> **sniper8752 said:**
> One last issue remains... When I add the following lines, I get a "network error: software caused connection abort".
sshd_config:
```
AllowGroups sftpusers sftp
Match Group sftpusers
ChrooDirectory %h
AllowTCPForwarding no
ForceCommand internal-sftp
```

I am trying to prevent the user from going outside of their home directory.

That's a different question altogether.  Start a new thread.

---

### Post by sniper8752 on 2014-03-24
Okay - thanks for your help everybody!

---

