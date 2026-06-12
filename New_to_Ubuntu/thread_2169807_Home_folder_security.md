---
title: "Home folder security"
date: 2013-08-23
forum: New to Ubuntu
---

### Post by sccjono on 2013-08-23
Hello all,

I have been using Ubuntu for a few weeks now as my first foray in to Linux and I really love it. However I came across something recently which confuses me. Someone wants to borrow my laptop for a few days. Its someone I trust however I don't really want them having access to my home folder as all my work is kept there. The obvious thing to me was to create a new user for her, which I did. But when I logged in as her to test it, I was able to navigate to my home folder and access documents etc with no problem. I only have Windows to go by but surely your home folder shouldn't be accessible to to other users by default?

Jon

---

### Post by newb85 on 2013-08-23
I believe the default is to let others view, but not edit, files in your home directory.  If course, that can be changed.

---

### Post by GreatDanton on 2013-08-23
It depends on what he/she needs. If he/she needs it only for browsing on the internet, reading mails (gmail) etc..., then I think guest account will be perfect. Just tried it and I was not able to acces home directory from guest account.

---

### Post by baker-quin on 2013-08-23
[SIZE=2]I don't know if this helps or not but it just seems like there should be a way to password protect your home folder. I went to the home folder properties and perhaps if you on the others section to "none" this would make it inaccessible to her. I havent tried it but it may work. 

The Ubuntu Desktop guide (what appears when you press the help button) says this on files,
[/SIZE][COLOR=#6C6C6C][FONT=sans-serif][h=2][SIZE=2]Files[/SIZE][/h][/FONT][/COLOR]
[COLOR=#3C3C3C][FONT=sans-serif][SIZE=2]You can set the permissions for the file owner, the group owner, and all other users of the system. For your files, you are the owner, and you can give yourself read-only or read-and-write permission. Set a file to read-only if you don't want to accidentally change it.[/SIZE]
[SIZE=2]Every user on your computer belongs to a group. On home computers, it is common for each user to have their own group, and group permissions are not often used. In corporate environments, groups are sometimes used for departments or projects. As well as having an owner, each file belongs to a group. You can set the file's group and control the permissions for all users in that group. You can only set the file's group to a group you belong to.[/SIZE]
[SIZE=2]You can also set the permissions for users other than the owner and those in the file's group.[/SIZE]
[SIZE=2]If the file is a program, such as a script, you must select [COLOR=#6C6C6C]Allow executing file as program[/COLOR] to run it. Even with this option selected, the file manager may still open the file in an application or ask you what to do. See [Executable text files]("xref:nautilus-behavior#executable")for more information.[/SIZE]

[/FONT][/COLOR]
[SIZE=2][COLOR=#3C3C3C][FONT=sans-serif]
Also on folders, 
[/FONT][/COLOR][/SIZE][COLOR=#6C6C6C][FONT=sans-serif][h=2][SIZE=2]Folders[/SIZE][/h][/FONT][/COLOR]
[COLOR=#3C3C3C][FONT=sans-serif][SIZE=2]You can set permissions on folders for the owner, group, and other users. See the details of file permissions above for an explanation of owners, groups, and other users.[/SIZE]
[SIZE=2]The permissions you can set for a folder are different from those you can set for a file.[/SIZE]
[SIZE=2][COLOR=#6C6C6C]None[/COLOR][/SIZE][SIZE=2]The user will not even be able to see what files are in the folder.[/SIZE]
[SIZE=2][COLOR=#6C6C6C]List files only[/COLOR][/SIZE][SIZE=2]The user will be able to see what files are in the folder, but will not be able to open, create, or delete files.[/SIZE]
[SIZE=2][COLOR=#6C6C6C]Access files[/COLOR][/SIZE][SIZE=2]The user will be able to open files in the folder (provided they have permission to do so on the particular file), but will not be able to create new files or delete files.[/SIZE]
[SIZE=2][COLOR=#6C6C6C]Create and delete files[/COLOR][/SIZE][SIZE=2]The user will have full access to the folder, including opening, creating, and deleting files.[/SIZE]



[SIZE=2]You can also quickly set the file permissions for all the files in the folder by using the [COLOR=#6C6C6C]File access[/COLOR] drop-down lists and the [COLOR=#6C6C6C]Execute[/COLOR] option. Leave the drop-down lists as [COLOR=#6C6C6C]---[/COLOR] for no change, or the [COLOR=#6C6C6C]Execute[/COLOR] check box in the indeterminate state (a horizontal line across it).[/SIZE]
[SIZE=2]If you click [COLOR=#6C6C6C]Apply Permissions to Enclosed Files[/COLOR], the file manager will adjust the read, write, and execute permissions of contained files based on the [COLOR=#6C6C6C]File access[/COLOR] and [COLOR=#6C6C6C]Execute[/COLOR] options you set. It will also change the permissions of contained folders to match the permissions of that folder. Permissions for enclosed files are applied to files in subfolders as well, to any depth.

Hope this helped!

Quinton[/SIZE]

[/FONT][/COLOR]

---

### Post by Morbius1 on 2013-08-23
```
chmod 770 /home/morbius
```
[COLOR=#0000cd]*Change morbius to your own user name.*[/COLOR]

She will know you have a home directory but if she tries to access it ( even to see what's inside ) she will get a permission denied error.

Now if you gave her sudo privileges then you have more to worry about than her accessing your home directory ;)

**[COLOR=#0000cd]EDIT[/COLOR]**: [COLOR=#0000cd]Resist the temptation to do a recursive chmod ( as in chmod -R 770 /path/to/file ) or if you are doing this graphically DO NOT choose: [/COLOR][COLOR=#0000cd][/COLOR][COLOR=#0000cd][FONT=sans-serif][SIZE=2]Apply Permissions to Enclosed Files[/SIZE][/FONT][/COLOR][COLOR=#0000cd]. It's unnecessary since file access is done via the path to something. Put a roadblock up anywhere along the path to an object prevents access to anything beyond it.[/COLOR]

---

### Post by baker-quin on 2013-08-23
[COLOR=#000000]Morbius1[/COLOR]
[COLOR=#000000][INDENT]**Re: Home folder security**
Code:
chmod 770 /home/morbius
[COLOR=#0000cd]*Change morbius to your own user name.*[/COLOR]
[/INDENT][/COLOR]


See... I have no idea what this command even does. Would you mind explaining it to me? Also how would you undo it?

---

### Post by ajgreeny on 2013-08-23
That command will mean that only you as  user and root will be able to access your /home. I think, however, that it needs to be a recursive command, ie, chmod -R 770 /home/morbius

---

### Post by Morbius1 on 2013-08-23
770

Each digit in that sequence refers to a different user. The first is user, the second is group, and the third is others ( everyone else ). 

The numbers have meaning:
1 = Execute ( for a file it means what it says but for a folder it means to traverse - to open it to see what's inside )
2 = Write
4 = Read

They are additive so a 5 = Execute + Read ( 1+4 ), a 7 = Execute + Write + Read ( 1+2+4 ).

If you want top stop everyone ( except root of course and yourself ) from seeing anything within your home directory you can either use 750 or 770 or even 700. The important one with respect to this topic is the last digit. Making it 0 means it has no permissions to "others". Everyone other than you is "others".

So set it to 750, 770, or 700 before you send it off with someone else then undo it when you get it back: chmod 775 or chmod 755
[COLOR=#0000cd]* The second digit in this context really doesn't matter since owner = group on your home directory.*[/COLOR]

And you don't want it to be recursive for 2 reasons:

[1] It is not necessary - you don't access a file directly - you access it through it's path.

So let's say I have a file that has permissions of 666. That would be a bad thing if someone else could access it directly but they can't. They have to go though /home/morbius to get to the file. If I set permissions on /home/morbius to block everyone other than me then no one but me will even see that I have a file.

[2] [COLOR=#0000cd]Besides, You certainly don't do recursive chmod'ing using octal permissions:[/COLOR]
```
chmod -R 770 /home/morbius
```
Octal chmod isn't smart enough to differentiate a file from a directory so it will apply 770 to every file as well as every folder. You just made every file in my home directory executable and that is not a good thing.

This is all that's necessary:
```
chmod 770 /home/morbius
```

---

### Post by The Cog on 2013-08-24
> **ajgreeny said:**
> I think, however, that it needs to be a recursive command, ie, chmod -R 770 /home/morbius
[COLOR="#B22222"][SIZE=3]**Nooooooo!**[/SIZE][/COLOR]
Do **NOT** use the -r to make it recursive. This will make a right mess of lots of things. It is enough to change the permissions of the home directory so that other users can't get into it. Because they can't get into that directory, they can't get to see anything underneath either.

You need to use sudo to use that command though, and I would be inclined to only allow read to members of the user's group like this:
```
sudo chmod 750 /home/morbius
```

---

### Post by Morbius1 on 2013-08-24
Not at all clear to me why one needs to invoke a chmod as sudo on one's own home directory since it's clearly owned by that user - but it certainly won't do any harm. 

It's also not clear to me why you would need to keep the group a 5 instead of a 7 unless you are in the habit of adding different users to your own group - but it's not enough to get into an argument about.

What's really not clear to me is why this thread wont end - the machine has left the building - it's in the hands of the woman he promised it to - it's too late now :)

---

### Post by The Cog on 2013-08-24
> Not at all clear to me why one needs to invoke a chmod as sudo on one's own home directory since it's clearly owned by that user - but it certainly won't do any harm. 
Actually, although your home folder is owned by you, changing its permissions requires writing toits containing directry /etc/home, which is only writeable by root. Try it.

---

### Post by Morbius1 on 2013-08-24
> **The Cog said:**
> Actually, although your home folder is owned by you, changing its permissions requires writing toits containing directry /etc/home, which is only writeable by root. Try it.
Are you just having a bad day?

** Last time I checked your home directory is off /home. There is no /etc/home. 

** Speaking of "Try it":

Chech your current permissions:
```
ls -dl $HOME
```
Change permissions without sudo:
```
chmod 750 $HOME
```
Check permissions again:
```
ls -dl $HOME
```
> morbius@vubuntu1304:~$ ls -dl $HOME
drwxr-xr-x 20 morbius morbius 4096 Aug 24 18:34 /home/morbius
morbius@vubuntu1304:~$ chmod 750 $HOME
morbius@vubuntu1304:~$ ls -dl $HOME
drwxr-x--- 20 morbius morbius 4096 Aug 24 18:34 /home/morbius
morbius@vubuntu1304:~$ 
And I managed to be able to do that even though I have no write permissions to the containing folder:
> morbius@vubuntu1304:~$ ls -dl /home
drwxr-xr-x 6 root root 4096 Jun 12 17:57 /home


I'm not makin' this stuff up people.

---

### Post by The Cog on 2013-08-25
> **Morbius1 said:**
> Are you just having a bad day?
It seems that I was.

I don't know where the /etc came from. That was right out of nowhere.

As for changing the permissions with chmod - I just learned something. I have known for years that you can't rename a file/folder without write permissions to its containing folder. And indeed, I just tried renaming my home folder and I have to use sudo to do it. But as you say, I can chmod it without sudo. That has me surprised. It goes against an assumption that I have "known" for years. I suppose I should have tried it myself before suggesting that you should. I wonder where the file/folder properties are stored. Renaming a file bumps the timestamp on its containing folder, but changing a file's attributes does not bump the file's or the folder's timestamp.

---

### Post by Morbius1 on 2013-08-25
> **The Cog said:**
> It seems that I was.

I don't know where the /etc came from. That was right out of nowhere.

As for changing the permissions with chmod - I just learned something. I have known for years that you can't rename a file/folder without write permissions to its containing folder. And indeed, I just tried renaming my home folder and I have to use sudo to do it. But as you say, I can chmod it without sudo. That has me surprised. It goes against an assumption that I have "known" for years. I suppose I should have tried it myself before suggesting that you should. I wonder where the file/folder properties are stored. Renaming a file bumps the timestamp on its containing folder, but changing a file's attributes does not bump the file's or the folder's timestamp.
It's probably some inode / metadata process that I wouldn't understand if it was explained to me using monosyllabic words.

The way I've rationalized it to myself is a directory holds the names and corresponding inode numbers of it's content as well as data about itself such as ownership, permissions, etc..

Changing the name of a subdirectoy means the parent directory's list of it's content has to be updated and that means the process doing the renaming must have write access to the parent. Changing permissions of a sudirectory doesn't alter anything on the parent.

But I'm self-taught so ... :D

---

### Post by ajgreeny on 2013-08-25
> **The Cog said:**
> [COLOR=#B22222][SIZE=3]**Nooooooo!**[/SIZE][/COLOR]
Do **NOT** use the -r to make it recursive. This will make a right mess of lots of things. It is enough to change the permissions of the home directory so that other users can't get into it. Because they can't get into that directory, they can't get to see anything underneath either.

You need to use sudo to use that command though, and I would be inclined to only allow read to members of the user's group like this:
```
sudo chmod 750 /home/morbius
```

Never mind the posts that follow this one; I am thankfull for the info on my recursive suggestion.

Thanks to both of you!

---

### Post by sccjono on 2013-08-26
Thank you everyone for participating in this. I have performed the chmod that morbius recommended and it worked perfectly. Just to be clear even guest_account could see my home folder which to me just didn't make sense but if that's the way it works, then so be it.

Thanks again,

jono

---

