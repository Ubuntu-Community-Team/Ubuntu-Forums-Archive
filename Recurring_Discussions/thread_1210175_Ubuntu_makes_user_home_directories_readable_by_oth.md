---
title: "Ubuntu makes user home directories readable by other users"
date: 2009-07-09
forum: Recurring Discussions
---

### Post by Smartin on 2009-07-09
Hi,

Edit 2: This is getting scary... Mods have now seen fit to try to bury this in another forum...

The attitude is that nothing must change.

Edit: An overzealous mod has made this thread very confusing by merging several other threads

What this thread is about is exploring the logic behind the decision to make Ubuntu user's Home directories readable by anyone on the box.

This is the original posting:

[I]Hi,

It has recently come to my attention that Ubuntu Desktop sets user's Home folders up as readable by any other user on the box.

To me this is an utterly astonishing thing for a modern operating system to do. I have slept on it and I'm still stunned When I come across something which to me is so obviously off-the-scale insane but is a decision which has been taken by otherwise rational people, it makes me very curious about the logic they applied when the decision was made.

I can only assume that not enough people know about this issue or they would be up in arms about it. It would never have occurred to me that it was the case only I stumbled over it by a fluke.

I respect Ubuntu too much to let this one just go by. Ubuntu is the nearest thing we have to an effective weapon against Microsoft and this is an Achilles heel.

Ubuntu touts itself as 'Secure by design' and many sensible decisions have been taken in this regard: we all have separate user accounts, no services run by default, to log in you need to know a username *and* a password by default, etc, etc. All sensible and logical. There is even a 'sticky' at the top of the 'Security' forum saying words to the effect of 'Use strong passwords and change them regularly'.

Then all home folders are readable by anyone else on the box by default!!

What is the point of *any* password if this is the case?

I have been pointed to places like this
[http://brainstorm.ubuntu.com/idea/6106/](http://brainstorm.ubuntu.com/idea/6106/)
and read through the arguments. Some are saying it's not a security issue, it's a privacy issue. To me this is a red herring. A user's home folder should be private *and* secure, period.

I also see 'If someone boots up from a live CD they can read your home folder anyway, so what's the point?'

This is a ridiculous argument. It's like saying 'Don't bother wearing a seatbelt when you are driving, If you get hit by a 20-Tonne truck, you're dead anyway, so what's the point?'

Others are saying it's a convenience thing for people to share files. Well, that's certainly true

Having World-readable Home folders is totaly inconsistent with a modern OS! It needs to be fixed!

Of course we need shared folders but we can quite easily have both shared folders and Private and Secure Home folders. They are not exclusive.

To me, the sensible model is the OSX one: Home folders are readable but any folder within this is not, other than the Web/Apache folder and the Shared folder. This is logical, secure and private. It is also convenient in terms of sharing files.

In fact I would go one step further and have two folders within the Home folder: Private and Shared. Then the conventional folders under these. But I understand that this may be a step too far

Please explain to me the logic behind the current setup, if there is any.

*And* let's not go round the 'It's easy to fix, just do this that and the other' block, I'm talking about *Default settings*. It's important!

Discuss please

Simon[/I]

The mid-section may be of interest as background but please jump to about page three for my quest to understand why the decision was made to make home folders world readable.

**************************************************************************************

[I]Odd one this...

I was given an old computer by our local school. It only has a 40GB drive in it so I hooked up a 320GB USB drive to it.

My boot partition is now on the 40GB drive and *everything* else is on the 320GB drive. (I would have preferred everything to be on the 320GB but couldn't get the box to boot from it)

Now I find that when I create a new user on the box, they are able to traverse the whole file system without being jailed to their own home folder. All users seem to be able to do this.

Even the root folder has access rights given to 'Others'.

Is this because it's an external drive?

What's the permanent fix? It's a drag to have to set permissions on each user specially. Even if I fix user folders manually, what do I do about the root folder?

Thanks :-)

Simon[/I]

---

### Post by asmoore82 on 2009-07-09
the external drive is probably NTFS for Windoze -
all system and user folders in Linux should be a native format
such as ext3, reiserfs, or ext4.

---

### Post by Smartin on 2009-07-09
> **asmoore82 said:**
> the external drive is probably NTFS for Windoze -
all system and user folders in Linux should be a native format
such as ext3, reiserfs, or ext4.

asmoore82,

Thanks for your response...

The drive is formatted as ext3. I don't allow Windoze in the house...;)

It's something else...

Simon

---

### Post by michy99 on 2009-07-09
When you say that all users have access to the root folder, are you talking about / or /root? If you mean / then all users should have read and execute rights, but not write rights. What is the output of```
ls -ld /
```

---

### Post by Smartin on 2009-07-10
> **michy99 said:**
> When you say that all users have access to the root folder, are you talking about / or /root? If you mean / then all users should have read and execute rights, but not write rights. What is the output of```
ls -ld /
```

Michy99,

Thanks for chipping in.

This is beginning to ring bells now. I remember being astonished that users can roam around the Ubuntu file system at will before... It would never happen on my OSX box but let's not go there...;)

Edit: I take this back!! It is possible. I definitely can't see inside another user's folders inside their home folders though, let alone open a document.

ls -l / gives me 
```

rwxr-xr-x   2 root root  4096 2009-07-10 08:21 bin
drwxr-xr-x   4 root root  4096 2009-07-10 08:20 boot
lrwxrwxrwx   1 root root    11 2009-07-10 08:04 cdrom -> media/cdrom
drwxr-xr-x  16 root root  3960 2009-07-10 10:28 dev
drwxr-xr-x 124 root root  4096 2009-07-10 10:28 etc
drwxr-xr-x   4 root root  4096 2009-07-10 10:11 home
lrwxrwxrwx   1 root root    33 2009-07-10 08:20 initrd.img -> boot/initrd.img-2.6.28-11-generic
drwxr-xr-x  19 root root  4096 2009-07-10 08:21 lib
drwx------   2 root root 16384 2009-07-10 08:03 lost+found
drwxr-xr-x   4 root root  4096 2009-04-20 14:59 media
drwxr-xr-x   2 root root  4096 2009-04-13 10:33 mnt
drwxr-xr-x   2 root root  4096 2009-04-20 14:59 opt
dr-xr-xr-x 125 root root     0 2009-07-10 09:32 proc
drwx------   4 root root  4096 2009-07-10 09:32 root
drwxr-xr-x   2 root root  4096 2009-07-10 08:21 sbin
drwxr-xr-x   2 root root  4096 2009-03-06 16:21 selinux
drwxr-xr-x   2 root root  4096 2009-04-20 14:59 srv
drwxr-xr-x  12 root root     0 2009-07-10 09:32 sys
drwxrwxrwt  19 root root  4096 2009-07-10 10:28 tmp
drwxr-xr-x  11 root root  4096 2009-04-20 15:00 usr
drwxr-xr-x  15 root root  4096 2009-04-20 15:07 var
lrwxrwxrwx   1 root root    30 2009-07-10 08:20 vmlinuz -> boot/vmlinuz-2.6.28-11-generic

```
I confess to being a newb and knowing next to nothing about this but to my mind only 
/root and /lost+found have the correct permissions. No?
This may be as it should, and I find it incredible in itself, but the permissions in my home folder
```

drwxr-xr-x 2 myname myname 4096 2009-07-10 08:56 Desktop
drwxr-xr-x 2 myname myname 4096 2009-07-10 08:56 Documents
-rw-r--r-- 1 myname myname  357 2009-07-10 08:17 examples.desktop
drwxr-xr-x 2 myname myname 4096 2009-07-10 08:56 Music
drwxr-xr-x 2 myname myname 4096 2009-07-10 08:56 Pictures
drwxr-xr-x 2 myname myname 4096 2009-07-10 08:56 Public
drwxr-xr-x 2 myname myname 4096 2009-07-10 08:56 Templates
drwxr-xr-x 2 myname myname 4096 2009-07-10 08:56 Videos

```
seem to allow any other user to access all my files.

I have just tested this by creating a test user and saving a test file on my own desktop. The test user can open and read the document when logged in to their own account.

This is on a fresh install of Jaunty, installed since my first post to make *triply* sure everything is formatted as ext3.

How can this happen? What is the permanent fix?

Isn't it a security risk to allow all users access, in any way, to the root file system? It gives me a heads-up as to username/password for a start...

I'm sure this is user error but I'm still astonished/intrigued...

Help please!!:p

Simon

---

### Post by CatKiller on 2009-07-10
> **Smartin said:**
> the permissions in my home folder
seem to allow any other user to access all my files.

Yes. I don't know why it's like that, but a default install does allow each user to see the contents of each other user's Home folders. Just remove the read permission for group and others and you should be fine.
> 
Isn't it a security risk to allow all users access, in any way, to the root file system? It gives me a heads-up as to username/password for a start...How would one run the programs that are stored on the filesystem if one could not access the filesystem? And I have no idea how you might guess anyone's password from anything in the filesystem.

Knowing the username of other users when you already have access to the machine is pretty standard. You can have the login screen show you what they all look like too if you like.

It is possible to set your machine up to run as a kiosk if you want, but I doubt that it is.

---

### Post by Smartin on 2009-07-10
Catkiller,
> **CatKiller said:**
> Yes. I don't know why it's like that, but a default install does allow each user to see the contents of each other user's Home folders. Just remove the read permission for group and others and you should be fine.

So it seems... But surely actually being able to *read a document* isn't right??

I find it incredible that another user can even *see inside* my home folder! Incredible!

I understand it's easily remedied but it just shouldn't be that way.

> How would one run the programs that are stored on the filesystem if one could not access the filesystem? And I have no idea how you might guess anyone's password from anything in the filesystem.

Knowing the username of other users when you already have access to the machine is pretty standard. You can have the login screen show you what they all look like too if you like.

Surely running an application is different from actually roaming around the system? A malicious user could garner all sorts of useful info.

As to the username/password issue, the default is that you have to know *both* the username and the password to log in. This seems sensible. Once I can roam around the file system, I can see the username quite easily. 50% less secure in a moment. Very uncool.

As to being able to actually open another user's documents, that's plain ridiculous! Surely that's not intended. 

*Please* tell me I screwed up my install somehow or that it's due to my home folders being on an external disk. *Please*...

Simon

---

### Post by Mka on 2009-07-10
Try:
```
sudo chmod 700 /home/*
```

---

### Post by Smartin on 2009-07-10
> **Mka said:**
> Try:
```
sudo chmod 700 /home/*
```

Mka,

Thanks for that but my point is that it should absolutely not be necessary.

It's seriously making me re-evaluate whether I keep using Ubuntu as a Desktop OS.

... and I'm still convinced that I shouldn't be able to actually *open* another user's documents...

Everyone seems pretty cool about this. I'm stunned.

Simon

---

### Post by michy99 on 2009-07-10
If you have anything you want to keep private, you need to encrypt it. Even if you set your home folder to 700 and don't give other users admin privileges, all they have to do is boot from a live CD and they have access to anything on the disk. This is true of any operating system.

---

### Post by CatKiller on 2009-07-10
> **Smartin said:**
> Everyone seems pretty cool about this. I'm stunned.

It is the way it is. It's straightforward to change it (and you already know how).

There's not really much point banging on about it, is there?

---

### Post by Smartin on 2009-07-10
Guys,

You're beginning to freak me out here...

I'm coming to you with "Hey, I screwed something up. On a fresh install, other users have complete access to all the files in my Home directory. Help please!"

And I'm getting back "Dude, chill. That's the way it is. Fix it like this. Even if they couldn't read your stuff by default, all they'd need to do is boot the box from a CD and read your stuff that way, so what's the big deal?"

Did I post this in the wrong forum? Should it go in 'Security'?

S

---

### Post by michy99 on 2009-07-10
Maybe it should go in security, so they can explain to you the same things we already have.

---

### Post by Smartin on 2009-07-10
Hi,

I started this thread in 'General Help' but the guys in there are scaring me and I'm rubbing them up the wrong way... (Sorry Guys, not my intention)

This is the original thread:
[http://ubuntuforums.org/showthread.php?t=1208754](http://ubuntuforums.org/showthread.php?t=1208754)

Just to recap:

I have done this twice now so it's a repeatable issue on my setup.

After a clean install of Jaunty Desktop, a 'Test' user, logged in to the 'test' account, can read, repeat *read*, a test document I saved on my desktop when I was logged in to *my* account, the admin account.

I'm a newb but I'm not *such* a newb that I don't know that something is wrong here.

I'm assuming the installer isn't screwed so it must be something specific to my box. Could it be that the /boot and /swap partitions are on the internal disk and that the / directory is on an external USB drive? That's all I can think of but I *am* a newb so I'm hoping you guys can help me out.

Just so we don't go over old ground, I realise it's a straightforward thing to fix the permissions on my Home folder but my point is that *if I have to do that* after a fresh install, there is something funky going on.

This is my home folder permissions from the old thread:

```

drwxr-xr-x 2 myname myname 4096 2009-07-10 08:56 Desktop
drwxr-xr-x 2 myname myname 4096 2009-07-10 08:56 Documents
-rw-r--r-- 1 myname myname  357 2009-07-10 08:17 examples.desktop
drwxr-xr-x 2 myname myname 4096 2009-07-10 08:56 Music
drwxr-xr-x 2 myname myname 4096 2009-07-10 08:56 Pictures
drwxr-xr-x 2 myname myname 4096 2009-07-10 08:56 Public
drwxr-xr-x 2 myname myname 4096 2009-07-10 08:56 Templates
drwxr-xr-x 2 myname myname 4096 2009-07-10 08:56 Videos

```

Hope to get something more sensible than "This is all as it should be" because I know darned well that no other user should be able to read my docs unless they are logged in to my account, or booted from a live CD.

I'm sure it's my error or something specific to my box but *what* is it?

Simon

---

### Post by sisco311 on 2009-07-10
By default, users' home directories are readable by all users on the system.

```
sudo dpkg-reconfigure adduser
```

If memory serves, then if you use the Alternate Install CD you can choose if you want to have "system wide readable home directories" or not.

---

### Post by Smartin on 2009-07-10
> **sisco311 said:**
> By default, users' home directories are readable by all users on the system.

```
sudo dpkg-reconfigure adduser
```


sisco311,

Are you seriously telling me that it is quite usual for another user to be able to read all my docs?

What are user accounts for then? Customising the interface? ;)

C'mon... ;) Ubuntu would be a laughingstock.

S

---

### Post by sisco311 on 2009-07-10
> **Smartin said:**
> sisco311,

Are you seriously telling me that it is quite usual for another user to be able to read all my docs?

What are user accounts for then? Customising the interface? ;)

C'mon... ;) Ubuntu would be a laughingstock.

S
This is the **default** setting. One can always change the permissions on his/her home directory. 

If you don't like it you can vote [here]("http://brainstorm.ubuntu.com/idea/6106/").

---

### Post by Smartin on 2009-07-10
> **sisco311 said:**
> This is the **default** setting. One can always change the permissions on his/her home directory. 

If you don't like it you can vote [here]("http://brainstorm.ubuntu.com/idea/6106/").

sisco311,

Really appreciate the link.

I have, until now, been a real fanboy of Ubuntu but this is insane. If this issue has been known since March 2008 and nothing has been done about it, Ubuntu is not a serious Distribution to my mind.

Where can I go? What is a more security-minded distribution? Is the Ubuntu server as insane? 

S

---

### Post by sisco311 on 2009-07-10
> **Smartin said:**
> sisco311,

Really appreciate the link.

I have, until now, been a real fanboy of Ubuntu but this is insane. If this issue has been known since March 2008 and nothing has been done about it, Ubuntu is not a serious Distribution to my mind.

Where can I go? What is a more security-minded distribution? Is the Ubuntu server as insane? 

S

Both the "server" and "alternate" Ubuntu ISO-images provide the option to encrypt your home directory and/or to have "system wide readable home directories" or not.

---

### Post by Smartin on 2009-07-10
> **sisco311 said:**
> Both the "server" and "alternate" Ubuntu ISO-images provide the option to encrypt your home directory and/or to have "system wide readable home directories" or not.

sisco311,

Really appreciate that! I'm downloading it now.

I'm absolutely stunned that Ubuntu would have made such an insane decision though. It would be hilarious if it wasn't so tragic.

What's the point of the 'Public' folder when your *whole Home folder* is actually public?

Unbelievable...

S

---

### Post by sisco311 on 2009-07-10
What's so tragic? You only have to change the permissions on your home directory:
```
chmod 0700 ~
```

EDIT:
And you don't have to reinstall in order to encrypt your home directory/partition: [thread=510812]Ubuntu Security[/thread]

---

### Post by Smartin on 2009-07-10
> **sisco311 said:**
> What's so tragic? You only have to change the permissions on your home directory:
```
chmod 0700 ~
```

sisco311,

I find it tragic because I want to see Windoze consigned to the trashcan of history. If one of the main hopes to do this can't see that Home folders which are readable by anyone on the box by default, they *really* can't be taken seriously.

I'm struggling to think of an analogy as the situation is so surreal but it's a bit like checking in to a hotel and finding that the door to your room doesn't have a lock.

'Oh yes Sir, we do this so as not to inconvenience our guests. If you want the door to lock you need to pull this lever and press this button.'

'But that's nuts! I have travelled all over the world and stayed in a million hotels. When I close the door, I expect it to lock behind me, without even having to turn a key. And if I do need to turn a key, I expect it to be obvious that I need to do that!'

'Well Sir, we are an alternative hotel... we like to make it easy for you to share all your possessions with your friends and family, should they happen to come along. It's *very* easy to lock the door should you want to Sir, you just pull this lever and push this button. Couldn't be simpler really.'

'Taxi!!'

A pretty unusual hotel...

I only have experience with OSX and think that Ubuntu has a few things to learn on this issue.

Does *any* other OS have the same defaults as Ubuntu?

Why do we have passwords for our accounts *By Default*? What's the point when our Home folders are all readable?

S

---

### Post by Smartin on 2009-07-10
> **sisco311 said:**
> By default, users' home directories are readable by all users on the system.

```
sudo dpkg-reconfigure adduser
```

sisco311,

This is a great tip. Can't thank you enough for it.

I still maintain I shouldn't have to do it though...

S

---

### Post by Smartin on 2009-07-10
Hi...

What's killing me now is that if the 'Powers that Be' at Ubuntu can make such an off-the-wall decision as to make Home directories readable by any Tom, Dick or Harry, what other crazy decisions have been made?

If I send an email, will it also go to another person chosen from my address book at random?

If I save a document in a folder, will a copy be saved in another user's account somewhere, as a backup?

Seriously, what else do I need to know?

S

---

### Post by Smartin on 2009-07-11
Hi,

It has recently come to my attention that Ubuntu Desktop sets user's Home folders up as readable by any other user on the box.

To me this is an utterly astonishing thing for a modern operating system to do. I have slept on it and I'm still stunned :) When I come across something which to me is so obviously off-the-scale insane but is a decision which has been taken by otherwise rational people, it makes me very curious about the logic they applied when the decision was made.

I can only assume that not enough people know about this issue or they would be up in arms about it. It would never have occurred to me that it was the case only I stumbled over it by a fluke.

I respect Ubuntu too much to let this one just go by. Ubuntu is the nearest thing we have to an effective weapon against Microsoft and this is an Achilles heel.

Ubuntu touts itself as 'Secure by design' and many sensible decisions have been taken in this regard: we all have separate user accounts, no services run by default, to log in you need to know a username *and* a password by default, etc, etc. All sensible and logical. There is even a 'sticky' at the top of the 'Security' forum saying words to the effect of 'Use strong passwords and change them regularly'.

Then all home folders are readable by anyone else on the box by default!!

What is the point of *any* password if this is the case?

I have been pointed to places like this
[http://brainstorm.ubuntu.com/idea/6106/](http://brainstorm.ubuntu.com/idea/6106/)
and read through the arguments. Some are saying it's not a security issue, it's a privacy issue. To me this is a red herring. A user's home folder should be private *and* secure, period.

I also see 'If someone boots up from a live CD they can read your home folder anyway, so what's the point?'

This is a ridiculous argument. It's like saying 'Don't bother wearing a seatbelt when you are driving, If you get hit by a 20-Tonne truck, you're dead anyway, so what's the point?'

Others are saying it's a convenience thing for people to share files. Well, that's certainly true :)

Having World-readable Home folders is totaly inconsistent with a modern OS! It needs to be fixed!

Of course we need shared folders but we can quite easily have both shared folders and Private and Secure Home folders. They are not exclusive.

To me, the sensible model is the OSX one: Home folders are readable but any folder within this is not, other than the Web/Apache folder and the Shared folder. This is logical, secure and private. It is also convenient in terms of sharing files.

In fact I would go one step further and have two folders within the Home folder: Private and Shared. Then the conventional folders under these. But I understand that this may be a step too far :)

Please explain to me the logic behind the current setup, if there is any.

*And* let's not go round the 'It's easy to fix, just do this that and the other' block, I'm talking about *Default settings*. It's important!

Discuss please :)

Simon

---

### Post by mikewhatever on 2009-07-11
Three problems with your arguments:
a) you are making a fuss out of nothing
b) you refuse to understand the difference between privacy and security
c) you are simply wrong

By default, the home folders are only readable by the owners and those belonging to the same group, not by anyone or the whole world, as the following argument of your's suggests.

> Having World-readable Home folders is totaly inconsistent with a modern OS! It needs to be fixed!

Instead of making false statements, try to explain why you think it is a security issue. Can a computer be exploited by a user reading another user's files? Furthermore, bare in mind that no matter what the default permissions are, any user with admin access can chmod/chown another home folder and own the files.

---

### Post by Smartin on 2009-07-11
> **mikewhatever said:**
> Three problems with your arguments:
a) you are making a fuss out of nothing
b) you refuse to understand the difference between privacy and security
c) you are simply wrong

By default, the home folders are only readable by the owners and those belonging to the same group, not by anyone or the whole world, as the following argument of your's suggest.



Instead of making false statements, try to explain why you think it is a security issue. Can a computer be exploited by a user reading another user's files? Furthermore, bare in mind that no matter what the default permissions are, any user with admin access can chmod/chown another home folder and own the files.

mikewhatever,

Thanks for your comment.

a) To you it may be nothing. To me Ubuntu's success is mega important. 
b) I understand the difference perfectly well and I think I made that clear in my original post.
c) I created an 'Unprivileged' test user and that user could read a document on my desktop. That's a nonsense. Try it for yourself.

It's *mainly* a privacy issue but it *is* also a security issue if a user has sensitive documents stored in their home folder. Even if it's login details to another box. Security isn't just about exploiting one particular box, it's a state of mind. Call it Privacy if you want but it's also about the security of *my documents*.

Yes I know I can encrypt things and yes I know I can change permissions but I shouldn't have to.

Most of all this issue makes a joke out of Ubuntu. Do you think a business of any sort would tolerate this? I don't.

The fact that the admin user can read anything is the 'Seatbelt' argument. A nonsense.

Please explain to me why we have account passwords when anyone can read anyone else's files?

I don't think I have made any false statements btw...?

S

---

### Post by mikewhatever on 2009-07-11
> **Smartin said:**
> ...

It's *mainly* a privacy issue but it *is* also a security issue if a user has sensitive documents stored in their home folder. Even if it's login details to another box.

Yes I know I can encrypt things and yes I know I can change permissions but I shouldn't have to.

Anyone with physical access to you computer can read and modify the files, no matter what the permissions are. The only way to protect the sensitive info is to have it encrypted. No, you don't have to do it, but that's the only way. Making your home folder accessible only by yourself does not protect from physical access.

> Most of all this issue makes a joke out of Ubuntu. Do you think a business of any sort would tolerate this? I don't.

Do you think it a good idea to give your business clients a false sense of privacy.

> The fact that the admin user can read anything is the 'Seatbelt' argument. A nonsense.

Well, the thing is, you don't have to be any kind of user, all you need is to have physical access, and, by the way, you like the word 'nonsense' way too much.

> Please explain to me why we have account passwords when anyone can read anyone else's files?

Isn't that the seatbelt kind of argument?

> I don't think I have made any false statements btw...?

S

The following statements are false:

> Please explain to me why we have account passwords whHaving World-readable Home folders is totaly inconsistent with a modern OS! It needs to be fixed! en anyone can read anyone else's files?
Having World-readable Home folders is totaly inconsistent with a modern OS! It needs to be fixed! 

Ubuntu doesn't have 'world readable' home folders by default.

Edit: You've started another thread with similar arguments just two days ago. What's the point of this one? [http://ubuntuforums.org/showthread.php?t=1208754](http://ubuntuforums.org/showthread.php?t=1208754)

---

### Post by lisati on 2009-07-11
The only sure-fire way I know of making any computer and the data stored on it absolutely secure is to disconnect it completely from the outside world and to put it in a place where no-one has physical access to it......

---

### Post by Smartin on 2009-07-11
> **mikewhatever said:**
> 

The following statements are false:

[quote]Please explain to me why we have account passwords whHaving World-readable Home folders is totaly inconsistent with a modern OS! It needs to be fixed! en anyone can read anyone else's files?
Having World-readable Home folders is totaly inconsistent with a modern OS! It needs to be fixed! [quote]

Ubuntu doesn't have 'world readable' home folders by default.

mikewhatever,

I'm repeating myself but I created an Unprivileged user and they could read a document on my desktop. This is with a fresh install of Jaunty. Please try it for yourself.

Do you know of any other OS which does this? I know OSX doesn't.

I would be *overjoyed* if you told me that there is something wrong with my install but I have done it twice now and have been told in other sections of these forums that it's the default behaviour. *Please* try it for yourself and then tell me what's wrong with my install.

S

---

### Post by Smartin on 2009-07-11
> **lisati said:**
> The only sure-fire way I know of making any computer and the data stored on it absolutely secure is to disconnect it completely from the outside world and to put it in a place where no-one has physical access to it......

Seatbelt argument.

Do you lock your front door when you leave your house?

I do, knowing full well that anyone who comes along could just put a rock through my window and enter that way. I *still* lock my doors because it's the sensible thing to do.

S

---

### Post by Smartin on 2009-07-11
I'm sorry the Mods don't see the difference between trying to fix a faulty install and exploring the logic behind making home folders world readable.

Merging the threads is confusing. Sorry

S

---

### Post by rookcifer on 2009-07-12
> **Smartin said:**
> sisco311,

Really appreciate the link.

I have, until now, been a real fanboy of Ubuntu but this is insane. If this issue has been known since March 2008 and nothing has been done about it, Ubuntu is not a serious Distribution to my mind.

Where can I go? What is a more security-minded distribution? Is the Ubuntu server as insane? 

S

Calm down.  As has been explained to you already, permissions don't matter when you have local users -- all a local user has to do is boot your machine from a livecd and he/she can read/write to ANY file on the system. All the permissions in the world will not stop him.  

The advent of livecd's has pretty much invalidated the old ways of securing local users.  It simply cannot be done anymore. This is true of OS X and 'doze too.  The only way to stop a local user with a livecd would be to have the machine locked in a vault where only you have the key.  In that case you can just "chmod 700 /home" and be done with it.  But as long as the local user has access to the CD drive, you can never stop him.

The only way to ensure he doesn't read your data, short of locking the machine in a vault, is to encrypt your files.

---

### Post by Smartin on 2009-07-12
> **rookcifer said:**
> Calm down.  As has been explained to you already, permissions don't matter when you have local users -- all a local user has to do is boot your machine from a livecd and he/she can read/write to ANY file on the system. All the permissions in the world will not stop him.  

The advent of livecd's has pretty much invalidated the old ways of securing local users.  It simply cannot be done anymore. This is true of OS X and 'doze too.  The only way to stop a local user with a livecd would be to have the machine locked in a vault where only you have the key.  In that case you can just "chmod 700 /home" and be done with it.  But as long as the local user has access to the CD drive, you can never stop him.

The only way to ensure he doesn't read your data, short of locking the machine in a vault, is to encrypt your files.

rookcifer,

I really appreciate you chipping in, especially as the mod screwed my thread so badly...

However, your argument is a spurious one...

Car manufacturers spend $zillions on making their cars safe in crashes under 30mph. Why? Because it covers most cases and is the sensible thing to do. They don't say, 'Hell, no-one can make a car safe in a crash at 150mph so we are not going to bother making ours safe at 30pmh'. It's a non-argument.

Users have a right to expect *at least the basics* to be right. The fact that the admin user *has* to be trusted doesn't mean that *all users on the box* have to be trusted. If the box is in *such* a hostile environment that the 'Live CD' issue comes into play, then the Bios etc need to be secured and the CD disabled.

Doesn't the fact that *even Windoze* secures home folders tell you anything?

To set defaults in the way they are just because the 'Worst possible case scenario' can't be covered is full-on bonkers!

S

---

### Post by aysiu on 2009-07-12
I happen to agree that this is a lousy default, but I don't think it's the end of the world as far as security and privacy are concerned. Mountain. Molehill.

I voted up [Idea #6106: Make so other people cant access your home directory](http://brainstorm.ubuntu.com/idea/6106/) but I'm not sure how much traction it'll get with developers.

In the meantime, you may find these posts helpful:
[Re: User /home perms](http://ubuntuforums.org/showpost.php?p=4461165&postcount=4)
[ Re: Security Warning: Users access to each other's home folders!!](http://ubuntuforums.org/showpost.php?p=1152219&postcount=4)
[Re: Home Directories readable to other users](http://ubuntuforums.org/showpost.php?p=4993153&postcount=4)

---

### Post by Smartin on 2009-07-12
> **aysiu said:**
> I happen to agree that this is a lousy default, but I don't think it's the end of the world as far as security and privacy are concerned. Mountain. Molehill.

I voted up [Idea #6106: Make so other people cant access your home directory](http://brainstorm.ubuntu.com/idea/6106/) but I'm not sure how much traction it'll get with developers.

In the meantime, you may find these posts helpful:
[Re: User /home perms](http://ubuntuforums.org/showpost.php?p=4461165&postcount=4)
[ Re: Security Warning: Users access to each other's home folders!!](http://ubuntuforums.org/showpost.php?p=1152219&postcount=4)
[Re: Home Directories readable to other users](http://ubuntuforums.org/showpost.php?p=4993153&postcount=4)

aysiu,

At least someone who agrees with me, at least in part :)

I *really* don't think this is making a mountain out of a molehill though. It fundamentally undermines the credibility of Ubuntu! To me that's a very serious thing.

The links you just posted were great. I'll read them through properly in a while but the gist seems to be that Ubuntu is only designed for an environment where *everyone* can be trusted. That's fine! But to design it in such a way and then say 'secure by design' is dishonest.

Ubuntu compounds this dishonesty by doing something which is *completely unexpected*. Mainstream OS's have private and secure home folders. If Ubuntu chooses not to do this, that's fine but it needs to make this *explicitly* clear.

As I've said earlier, if an email application was set up so it copied all outgoing mail to an address chosen at random from the user's addressbook, that's fine as long as the user knows that this is happening. The fact is that no-one would expect an email application to do this and it wouldn't occur to anyone to ask, 'Hey, does this application send my email to anyone other than my intended recipient?'. It's such an off-the-wall thing to happen that it would catch users unaware.

One of the links you sent said words to the effect that the decision has been made because it's assumed that the box is in a trusted, family situation. 'Honey, find those images in my Home directory would you?'

If the environment is so trusted, STICK YOUR PASSWORD ON THE SCREEN FOR GOD'S SAKE!! BUT DON'T RELEASE OUT AN OS WHICH IS *ONLY* SUITABLE FOR THIS ENVIRONMENT.

The link to the Brainstorm area is one I have seen before but the issue has been buried as you can see. It's no longer possible to vote for it. I re-posted it but it hasn't shown up. A less cynical person might think the Ubuntu team had an agenda, what with screwing this thread and all... ;)

S

---

### Post by aysiu on 2009-07-12
No, it is making a mountain out of a molehill. Sorry.

As I said before, I fully agree that this is a poor default, and users should expect privacy unless they decide to opt in to making files and folders available for viewing by family members, but this isn't a huge deal security-wise. It's not at all like posting up your password, which would allow people to *modify* your files and not just view them.

I would like to see the default changed, but I have no problems using Ubuntu in the meantime. If you would like to use something else, feel free to. There are plenty of Linux distros out there.

---

### Post by Smartin on 2009-07-12
> **mikewhatever said:**
> Three problems with your arguments:
c) you are simply wrong

By default, the home folders are only readable by the owners and those belonging to the same group, not by anyone or the whole world.


Mike,

What's the verdict? Did you try it for yourself?

It seems it really is the default to make Home folders world readable doesn't it?

S

---

### Post by Smartin on 2009-07-12
> **aysiu said:**
> No, it is making a mountain out of a molehill. Sorry.

As I said before, I fully agree that this is a poor default, and users should expect privacy unless they decide to opt in to making files and folders available for viewing by family members, but this isn't a huge deal security-wise. It's not at all like posting up your password, which would allow people to *modify* your files and not just view them.

I would like to see the default changed, but I have no problems using Ubuntu in the meantime. If you would like to use something else, feel free to. There are plenty of Linux distros out there.

aysiu,

It's a huge deal as regards the security of a user's documents. Call it Privacy if you want but whatever excuses you try to make, it's a shockingly poor decision.

You say it's not like posting your password but it seems that Ubuntu is designed for a *totally trusted, family environment* so what's the difference? Why have user accounts at all? Just have one account with separate folders for each family member.

Or are accounts only there to customise the working environment?

It's also a huge deal because it undermines Ubuntu's credibility. If this issue can slip through, what other issues do I need to be aware of? What other weird things are going on? How can anyone trust Ubuntu as anything than a toy OS. It gives the Linux nay-sayers a huge stick to beat us with... 'Hey did you know that (possibly) the *most popular* desktop Linux distribution, Ubuntu, doesn't even do something as basic as secure/make private a user's Home folder!!?? Ha! Clowns!. These Linux geeks are all the same, they expect you do do all the work to get a basic setup working. Stick with Windoze mate! Safest bet.'

Catastrophic.

The other thing is that there are *no downsides* to doing things properly.

This thread is really supposed to be about the logic behind the decision and it's got lost a bit...

I don't understand the upside of the current situation *or* the downsides of doing it properly.

Help me please.

S

---

### Post by Smartin on 2009-07-12
This thread is gold:

[http://thread.gmane.org/gmane.linux.ubuntu.devel/12422/focus=12448](http://thread.gmane.org/gmane.linux.ubuntu.devel/12422/focus=12448)

Someone else posted it earlier but I can't see who...

Take a while to read it through. It seems this issue can be a security risk as well as a privacy issue.

That thread seems to be from 2005. I'm stunned that the 'Convenience' argument won out over the security/privacy one and I really think it should be revisited. I am quite convinced that it's only lack of knowledge about this issue which prevents it from being fixed.

People are *assuming* Home folders are safe when they are not. It just isn't occurring to users that home folders are wide open.

Ubuntu in this state is only suitable for a *totally* trusted environment. There is no such environment.

The 'convenience' attitude is what opened the door to Windoze for so many viruses and they have now learned their lesson. It's way overdue that Ubuntu does too.

This is the age of identity theft etc. To have wide open home folders is ridiculous. It's not *just* about the security of one particular box, it's about securing people's privacy and lives.

There are *no* downsides to doing this properly, only upsides.

The fact that Ubuntu *Server* seems to do the same thing makes me want to weep....

S

---

### Post by Smartin on 2009-07-12
> **moodle said:**
> I love Ubuntu.  I love the philosophy behind it, the community that sustains it, and the way most things work so beautifully out of the box.  I am an Ubuntu convert, and would never consider going back to Windows.

David

David,

I'm 100% with you in terms of my love for the philosophy behind Ubuntu but forget all the issues with wi-fi, printing and screens etc...

Don't you think that the *main* issue which will prevent Ubuntu being taken seriously is one of Privacy and security?

Please have a look at my thread here

[http://ubuntuforums.org/showthread.php?t=1210175&page=3](http://ubuntuforums.org/showthread.php?t=1210175&page=3)

It starts at post #25 unfortunately as the mods are trying hard to bury the issue.

Please let me know what you think.

Simon

---

### Post by CatKiller on 2009-07-12
Give it a rest, man. Twenty-odd post on the subject, all saying exactly the same thing. The facts of the matter aren't going to change, no matter how much you whine to us about it. You aren't the only person that thinks it's a bad default, but all you're doing by banging on about it like this is alienating anyone that might be sympathetic to your point of view.

Grow up and get over it.

---

### Post by Smartin on 2009-07-12
> **CatKiller said:**
> Give it a rest, man. Twenty-odd post on the subject, all saying exactly the same thing. The facts of the matter aren't going to change, no matter how much you whine to us about it. You aren't the only person that thinks it's a bad default, but all you're doing by banging on about it like this is alienating anyone that might be sympathetic to your point of view.

Grow up and get over it.

CatKiller,

*Of course* things won't change when people have an attitude like yours.

Please tell me, how *do* we make a change to this?

Are you telling me it's written in stone somewhere, that Ubuntu is to remain an OS suitable *only* for a 100% trusted environment?

How will things change if people aren't willing to make a noise about it?

S

---

### Post by CatKiller on 2009-07-12
> **Smartin said:**
> How will things change if people aren't willing to make a noise about it?

Making a noise is not the same as making change. What do you think you're achieving by posting here? Do you think that the devs are frantically scouring this forum for suggestions from some random poster on how they can make Ubuntu better? They aren't.

Things won't change with an attitude like yours. All you are doing is wasting your effort on sound and fury. It's pointless. File bug reports. Promote aysiu's Brainstorm entry. Do something that will actually bring your concerns to someone that can do something about it. Banging on about it here is a waste of everyone's time. As I told you two days ago.

You've achieved nothing in the last two days. You got all the facts that you're going to get in the first hour.

---

### Post by Smartin on 2009-07-12
> **CatKiller said:**
> Making a noise is not the same as making change. What do you think you're achieving by posting here? Do you think that the devs are frantically scouring this forum for suggestions from some random poster on how they can make Ubuntu better? They aren't.

Things won't change with an attitude like yours. All you are doing is wasting your effort on sound and fury. It's pointless. File bug reports. Promote aysiu's Brainstorm entry. Do something that will actually bring your concerns to someone that can do something about it. Banging on about it here is a waste of everyone's time. As I told you two days ago.

You've achieved nothing in the last two days. You got all the facts that you're going to get in the first hour.

As I mentioned, aysiu's brainstorm entry has been buried. It can't be voted for. I posted my own but that's been buried as well.

This second thread was actually about exploring the logic behind the current decision. This got lost in everyone making excuses for the situation. There *is* no excuse for the current situation but I'm interested in knowing *how we got to where we are*. Big difference.

I thought it was a bug but it isn't so there's not much mileage there...

S

---

### Post by Closed_Port on 2009-07-12
> **Smartin said:**
> 
People are *assuming* Home folders are safe when they are not. It just isn't occurring to users that home folders are wide open.

I think that's the best argument for why this is a poor default. Users probably don't expect the default behavior, that is, that their files are readable by other users.

> **Smartin said:**
> 
This is the age of identity theft etc. To have wide open home folders is ridiculous. It's not *just* about the security of one particular box, it's about securing people's privacy and lives.

And though I agree with you on this being a bad default, here I have to vehemently disagree with you. You really are making a mountain out of a molehill. And you are not very precise when doing it. 

The home folders are not wide open, they are readable by other Users on the same box. While I, again, agree that this is a bad default, it is still a far cry from the home folders being wide open.

---

### Post by CatKiller on 2009-07-12
> **Smartin said:**
> This got lost in everyone making excuses for the situation.

I haven't seen anyone "make excuses for the situation". Anyone that's disagreed with you has only dialled back your exuberance on the topic. It **is** a bad default - many people have already said this - but your hyperbolic exaggerations are exactly that.

There are a number of decisions about the defaults that I don't like. This is one, as is the disabling of Ctrl-Alt-Backspace to kill the X Server. There are probably others, but those are the ones that I remember. Administering your own box is, and always must be, your own responsibility. If a setting isn't to your taste, change it. That's really what it comes down to.

As I've already pointed out, this isn't really achieving anything. You've said your bit, so move on. Seriously.

---

### Post by starcannon on 2009-07-12
> **Smartin said:**
> Mka,

Thanks for that but my point is that it should absolutely not be necessary.

It's seriously making me re-evaluate whether I keep using Ubuntu as a Desktop OS.

... and I'm still convinced that I shouldn't be able to actually *open* another user's documents...

Everyone seems pretty cool about this. I'm stunned.

Simon
I just fix my permissions, I agree that on this issue they are way to loose; but no biggy, just fix them to your tastes. If setting up software to meet your needs is a deal killer, then for the time being, there is no OS that is going to support your needs; one may have X values just the way you think they ought to be, and Y values will be all wrong; another still may have Y values dialed into your version of perfection, and X values will be all wrong; it is highly unlikely that your ever going to find an OS, or a Distribution of an OS that has it all setup to your personal standards and tastes. If you do find such an OS or Distribution of an OS, please PM me, I'd like to check it out myself.

GLAHF

---

### Post by Smartin on 2009-07-12
Guys,

No worries. I give up.

S

---

### Post by juancarlospaco on 2009-07-12
You don't configure your system before installed?, OMG!.

You can be pwned from the Grub, from LiveCD, from Pendrive Boot, from Network Boot, in that way.

:)

---

### Post by bodhi.zazen on 2009-07-13
I also prefer a private home but IMO it is not really a big deal. The fix takes less time to fix then it did to post in the first place.

I believe your thread was moved to recurring discussions as this topic has been discussed many times.

IMO, anything "sensitive" is best kept encrypted.

I would also point out that what you are really talking about is physical access and permissions of 750 or 700 are nor really any more "secure" then 755. The information on your system, including $HOME and /etc/shadow, are easily available if your system is not encrypted.

If you wish to limit access to information / files on your system :

1-10 Encryption, encryption, encryption.

11. SELinux / Apparmor.

---

### Post by lisati on 2009-07-13
> **Smartin said:**
> Seatbelt argument.

Do you lock your front door when you leave your house?

I do, knowing full well that anyone who comes along could just put a rock through my window and enter that way. I *still* lock my doors because it's the sensible thing to do.

S

I lock my doors when I go out, but that won't stop a determined burglar, even if did put the chain on the front door, and tracked down a key for the original lock on the laundry door which now has a Yale-type lock now for locking purposes. It's a shame that when the landlord replaced the door for the back porch (the original was beginning to rot) we ended up with one which wasn't locakable (some kind of new rule) - we would have two lockable doors to get through when going in the back way. A strange arrangement but that's the way the place was built.....


As for the discussion on the accesibility of a user's home folder, I'm the only user of my machines so I haven't really given it much thought....

---

### Post by eeperson on 2009-07-13
> **Smartin said:**
> sisco311,
I'm struggling to think of an analogy as the situation is so surreal but it's a bit like checking in to a hotel and finding that the door to your room doesn't have a lock.

'Oh yes Sir, we do this so as not to inconvenience our guests. If you want the door to lock you need to pull this lever and press this button.'

'But that's nuts! I have travelled all over the world and stayed in a million hotels. When I close the door, I expect it to lock behind me, without even having to turn a key. And if I do need to turn a key, I expect it to be obvious that I need to do that!'

'Well Sir, we are an alternative hotel... we like to make it easy for you to share all your possessions with your friends and family, should they happen to come along. It's *very* easy to lock the door should you want to Sir, you just pull this lever and push this button. Couldn't be simpler really.'

'Taxi!!'

A pretty unusual hotel...

I only have experience with OSX and think that Ubuntu has a few things to learn on this issue.

Does *any* other OS have the same defaults as Ubuntu?

Why do we have passwords for our accounts *By Default*? What's the point when our Home folders are all readable?

S

The ability to read another user's account IS NOT a security issue, as it does not make it any easier for a user to take control of another user's account.  However, it IS privacy issue.

To make your hotel analogy more accurate, the Ubuntu configuration would be like hotel that does have locks on the rooms (disabled write privileges) but has the curtains open (read privileges).  If you have something in your hotel room that you do not want others to see you simply close the curtains (disable read privileges).

Also, you should be aware that new folders created in an OSX home folder defaults to the same permissions as Ubuntu.

---

### Post by Smartin on 2009-07-14
> **eeperson said:**
> The ability to read another user's account IS NOT a security issue, as it does not make it any easier for a user to take control of another user's account.  However, it IS privacy issue.

eeperson,

I'm pursuing this issue in another way, just replying out of courtesy now...

The security/Privacy argument is splitting hairs. It's *definitely* a privacy issue and *can* be a security issue, not necessarily to the box concerned but to the User themselves, depending on what they have saved in their Home folder. We have to be concerned with both security *and* privacy. That's what a user has a right to expect.

> 
Also, you should be aware that new folders created in an OSX home folder defaults to the same permissions as Ubuntu.

I know.

My concern lies with the *default* installation.

The Home folder *has* to be read/write, or sharing will be killed. *All* folders *within* the Home folder should have correct permissions though. As OSX does.

If you change the default structure, that's up to you as a user. Ideally a user would be told 'Do you realise that the folder you are creating will be readable by anyone on this computer' if they created an additional folder within the Home folder. On Ubuntu this is not necessary as the whole thing is wide open.

Listen, I've got the message that pursuing this argument in the forums is a waste of time. People in the forums chose to roll over on this issue and that's fine. I'll find another front to fight this on. It needs to be changed for Ubuntu to be taken seriously and that's my prime concern.

S

---

### Post by Smartin on 2009-07-15
> **bodhi.zazen said:**
> I also prefer a private home but IMO it is not really a big deal. The fix takes less time to fix then it did to post in the first place.

bodhi,

Welcome. You are totally missing my point. The fact that it's an easy fix is not the issue.

What do you think Joe Average knows/cares about 'Permissions'? He just wants a sensible OS.
> 

I believe your thread was moved to recurring discussions as this topic has been discussed many times.

You are proving my point. The *very fact* that this has been raised so many times means that it's time you guys took notice

S

---

### Post by Smartin on 2009-07-15
> **eeperson said:**
> The ability to read another user's account IS NOT a security issue, as it does not make it any easier for a user to take control of another user's account.  However, it IS privacy issue.

This one has been bugging me...

We have to start thinking about security in a much wider context these days. The issue isn't *just* the box, it's the User's documents.

Just because you can't actually move/copy/paste another User's document doesn't mean you can't steal it. 

If you found a document called 'TheoryOfTheUniverse.txt' on Albert's computer, how long would it take to open it and write down 'E=MCsquared' on the back of your hand?

Did you steal the document or didn't you?

Albert is a brilliant physicist but why would he know anything about encrypting documents on his Ubuntu box? On his Windows box his document would have been reasonably safe.

Now you'll say "If you give someone physical access to your box, all bets are off."

Clearly this is true but it's still missing the point. Imagine this:

Peter has a great new game going on the family's Ubuntu box. His friend Joe comes around to play with it. After an hour or so Peter has had enough and goes into the garden to play ball.

Joe says "I'll just have one more game and then I'll join you!"

Peter leaves.

Instead of having another game, Joe goes snooping round the computer. He knows *nothing* about booting from live CD's or hacking Grub or any of that other BS.

He can however double click on Peter's Mom's home folder and have a look round.

In there he finds a document which makes it clear that Peter is adopted. Peter knows he is adopted but the family have chosen not to go public with the fact just yet.

Joe means no harm but he's a bigmouth. The adoption thing gets out at school and Peter is mercilessly bullied. 

This affects him for the rest of his life.

To the family, the fact that Peter was adopted was no secret. Why would they encrypt the relevant document, even *if* they knew anything about encryption, which they don't?

Ubuntu needs to *take a lead* in all matters of security/privacy/reliability. To be so far behind the curve on this matter is inexcusable.

*Even Windows* gets this right FFS.

S

---

### Post by gormac on 2009-07-15
1. Your example is no different than 'Joe' going through the desktop drawers and finding Peter's adoption papers there. Do you go shouting to the desktop manufacturer that you don't understand why their desktop's drawers aren't locked by default...and just anybody can read the documents stored in the drawers?

2. Your example also describes a highly unlikely chain of events (for example, it isn't much more unlikely that Joe is in fact capable of booting from a livecd and read the documents even if he had no permissions to do so). 

Also, as a counter-argument with another highly unlikely possibility: What if Joe finds a document in German describing the cure for cancer written by Peter's grandfather, which no one else has understood as no one in the family understand's German. Joe does and notifies the family and researchers of this important discovery saving billions of lives.

---

---

### Post by eeperson on 2009-07-15
> **Smartin said:**
> 
I'm pursuing this issue in another way, just replying out of courtesy now...

The security/Privacy argument is splitting hairs. It's *definitely* a privacy issue and *can* be a security issue, not necessarily to the box concerned but to the User themselves, depending on what they have saved in their Home folder. We have to be concerned with both security *and* privacy. That's what a user has a right to expect.


I know it may sound like splitting hairs but it is an important distinction to make when discussing COMPUTER security.  Privacy certainly can encapsulate security issues (such as is if someone stores their password in a public place).  However, a lack of privacy does no allow a malicious user to take control of the computer or another user's account (at least not without the user doing something foolish).

If you discuss it as a security issue in terms of Ubuntu, people will assume that you are discussing COMPUTER security.  Since this is not a COMPUTER security issue, it will be assumed that you are ignorant about how COMPUTER security works and you will not be taken seriously.  However, if you discuss this as a COMPUTER privacy issue (which this most definitely falls in to the category of) you will be taken much more seriously.  This is because Ubuntu development can only reasonably address concerns related to COMPUTER security and privacy.  The security of external systems is outside of the scope of what can reasonably addressed.

---

### Post by bodhi.zazen on 2009-07-15
> **Smartin said:**
> bodhi,

Welcome. You are totally missing my point. The fact that it's an easy fix is not the issue.

I am ? how ?

Your "security flaw" basically boils down to restricting access to $HOME from a user who has physical access to the system.

Your hypothesis is that one can plug this "security hole" by changing the default permissions of $HOME to either 750 or 700.

This hypothesis is false.

The point of passwords is to restrict remote access. Passwords, on any OS, as well as things like BIOS passwords, GRUB passwords, etc are easily defeated with physical access via a live CD or physically removing the hard drive.

Assuming one does not boot a live CD, passwords do restrict accounts, and can be further enhances with things such as acl, selinux, or apparmor. As has been mentioned ro access is not a computer security flaw, it does not in itself lead to escalation of privileges or root access. Most of / is available to users ro or rx. Only root has rwx to most of /

In order to solve this "security hole" (of physical access) you need to restrict physical access, use apparmor or selinux, and/or better yet use encryption.

This is true on EVERY OS - Ubuntu, Linux, OSX, Windows.

Your hypothesis that OSX is somehow more secure is also false.

And yes you can encrypt your $HOME directory or your entire Ubuntu installation if you so desire. Both options are easily available at the time of installation.

Last, yes security is a user's responsibility on any OS. Users who do not pay attention to security and privacy issues on ANY OS are vulnerable.

So again, the solution is not changing the defaults, but rather EDUCATION. You need to educate users on how to protect their privacy. If they will not listen to education, you really can not force it on them, at least not with anything short of forcing them to fully encrypt their system and force them to keep /boot on a removable device.

The truth of the matter, the "average" user does not use SELinux, Apparmor, or full system encryption. I have been encouraging such things and educating users for a long time now. How many people reading this pot do you think know what acl is ? How many use AppArmor ? SELinux? Encryption is probably the most common solution, still I bet most people do not fully encrypt their installations and put /boot on a separate, physically secured removable device.

It is because your hypothesis is false, both the permissions of 700 and your claim that OSX is somehow superior, that people do not take you seriously.

This discussion is in recurring discussions because it has been discussed many, many, many times and the conclusion of the discussion can be summarized in one word :

Encryption

The other part of the problem here, frankly, is you do not respect the decisions or choices of others. People understand what you are saying, the disagree with you, and for good reason. Did you ever stop in your Crusade to listen to what people are trying to tell you ?

> I also prefer a private home ...I saw several posts from people agreeing that they also prefer a private home.

Did you stop for a minute to consider perhaps it is you who is missing the point ?

---

### Post by lswb on 2009-07-15
smartin, I know this is small consolation, but YOU are RIGHT, those who argue that home directories should be rwxr-xr-x by defalt are WRONG, and the failure to mention this prominently during installation is also WRONG.

---

### Post by aysiu on 2009-07-15
> **lswb said:**
> smartin, I know this is small consolation, but YOU are RIGHT, those who argue that home directories should be rwxr-xr-x by defalt are WRONG, and the failure to mention this prominently during installation is also WRONG.
I agree with you completely on all counts.

But those who also think it is a huge deal and a security issue are also WRONG.

---

### Post by Smartin on 2009-07-15
> **gormac said:**
> 1. Your example is no different than 'Joe' going through the desktop drawers and finding Peter's adoption papers there. Do you go shouting to the desktop manufacturer that you don't understand why their desktop's drawers aren't locked by default...and just anybody can read the documents stored in the drawers?

 
Eh... why would anyone expect a drawer manufacturer to have the drawers locked by default?

> 2. Your example also describes a highly unlikely chain of events (for example, it isn't much more unlikely that Joe is in fact capable of booting from a livecd and read the documents even if he had no permissions to do so). 

Nope. He was already on the box playing games.

S

---

### Post by Smartin on 2009-07-15
> **eeperson said:**
> I know it may sound like splitting hairs but it is an important distinction to make when discussing COMPUTER security.  Privacy certainly can encapsulate security issues (such as is if someone stores their password in a public place).  However, a lack of privacy does no allow a malicious user to take control of the computer or another user's account (at least not without the user doing something foolish).

If you discuss it as a security issue in terms of Ubuntu, people will assume that you are discussing COMPUTER security.  Since this is not a COMPUTER security issue, it will be assumed that you are ignorant about how COMPUTER security works and you will not be taken seriously.  However, if you discuss this as a COMPUTER privacy issue (which this most definitely falls in to the category of) you will be taken much more seriously.  This is because Ubuntu development can only reasonably address concerns related to COMPUTER security and privacy.  The security of external systems is outside of the scope of what can reasonably addressed.

Given that both OSX *and Windows* have sensible security/privacy settings, I don't see how you can possibly make that argument stick.

S

---

### Post by Smartin on 2009-07-15
> **bodhi.zazen said:**
> I am ? how ?

Your "security flaw" basically boils down to restricting access to $HOME from a user who has physical access to the system.

Your hypothesis is that one can plug this "security hole" by changing the default permissions of $HOME to either 750 or 700.

This hypothesis is false.

You are not understanding me.

My dream is that the Ubuntu Desktop replaces Windows for the mainstream user. By 'mainstream user' I mean the kind of user who chooses a particular computer because it comes in a pretty colour. The kind of user who has their car serviced regularly but has no idea how to pop the hood and check the oil.

This kind of user has come to expect *sensible* default permissions within the home folder because this is what Windows has.

These users have no interest in the fact that some geek knows how to access their accounts. They just expect *basic* security measures to be in place.

If they find that anyone else on the box can read through their stuff, they lose all faith in the OS. The fact that it's an easy fix doesn't interest them. Their trust is gone. The fact that the box can be hacked using a Live CD doesn't interest them either because they have no clue that this is the case.

> The point of passwords is to restrict remote access.
Oh, please...:p

 > Passwords, on any OS, as well as things like BIOS passwords, GRUB passwords, etc are easily defeated with physical access via a live CD or physically removing the hard drive.

Assuming one does not boot a live CD, passwords do restrict accounts, and can be further enhances with things such as acl, selinux, or apparmor. As has been mentioned ro access is not a computer security flaw, it does not in itself lead to escalation of privileges or root access. Most of / is available to users ro or rx. Only root has rwx to most of /

In order to solve this "security hole" (of physical access) you need to restrict physical access, use apparmor or selinux, and/or better yet use encryption.

This is true on EVERY OS - Ubuntu, Linux, OSX, Windows.

And you are going to use this argument to persuade the mainstream user to migrate to Ubuntu?

I say again, the mainstream user is more interested in a pretty coloured box than any nonsense about how to properly secure their accounts. This is geekery. They are not geeks, they actually want Windows but it is broken in other ways and it's too expensive. They will move to Ubuntu if it looks Ok, works Ok and has sensible security/privacy.

The fist two are pretty much covered, as to the third point, Ubuntu isn't even in the ballpark in its present state.

> Your hypothesis that OSX is somehow more secure is also false.

My hypothesis is that OSX has better *basic* security. This is blatantly obvious.

> And yes you can encrypt your $HOME directory or your entire Ubuntu installation if you so desire. Both options are easily available at the time of installation.

Encrypting the home folder is asking for trouble in my opinion. If you forget your password or whatever, your stuff is gone for good. 

> Last, yes security is a user's responsibility on any OS. Users who do not pay attention to security and privacy issues on ANY OS are vulnerable.

To the *mainstream user*, *basic* security is expected. To them it's not their responsibility to take care of basic security. They don't have the first clue/interest in the subject.

> So again, the solution is not changing the defaults, but rather EDUCATION. You need to educate users on how to protect their privacy. If they will not listen to education, you really can not force it on them, at least not with anything short of forcing them to fully encrypt their system and force them to keep /boot on a removable device.

Good luck with the education thing! You think the mainstream user cares enough to be educated in the finer points of permissions and encryption?

" I gotta have permission to use my own computer?!" 

If you were a mechanic you'd be saying 'It's really important that you check the oil before *every trip*!"

"Screw that! Get my hands dirty? I wait until the red light comes on the dashboard. If the engine starts making too much noise I turn the radio up"

Let's get the mainstream user onside first *then* teach him the finer points of security. He won't listen to us if the basics aren't right.

"I'm supposed to listen to you about security when you let other people go through all my stuff by default? Get the log out of your own eye first buddy! Honey, where are my Vista install disks?!"

> The truth of the matter, the "average" user does not use SELinux, Apparmor, or full system encryption. I have been encouraging such things and educating users for a long time now. How many people reading this pot do you think know what acl is ? How many use AppArmor ? SELinux? Encryption is probably the most common solution, still I bet most people do not fully encrypt their installations and put /boot on a separate, physically secured removable device.

It is because your hypothesis is false, both the permissions of 700 and your claim that OSX is somehow superior, that people do not take you seriously.

This discussion is in recurring discussions because it has been discussed many, many, many times and the conclusion of the discussion can be summarized in one word :

Encryption

The other part of the problem here, frankly, is you do not respect the decisions or choices of others. People understand what you are saying, the disagree with you, and for good reason. Did you ever stop in your Crusade to listen to what people are trying to tell you ?

I saw several posts from people agreeing that they also prefer a private home.

Did you stop for a minute to consider perhaps it is you who is missing the point ?

I'm still waiting for a sensible argument as to why things are as they are. 

If I come across as disrespectful I really do sincerely apologise. I'm not a disrespectful person by nature.

Mark Shuttleworth's dream is one I share. He and the Ubuntu developers have my support and loyalty. *Blind* loyalty however is counter productive.

Sometimes even your best friend needs a kick in the pants. This is such an occasion.

S

---

### Post by Smartin on 2009-07-15
> **lswb said:**
> smartin, I know this is small consolation, but YOU are RIGHT, those who argue that home directories should be rwxr-xr-x by defalt are WRONG, and the failure to mention this prominently during installation is also WRONG.

Big Hug! ):P

:p

S

---

### Post by Smartin on 2009-07-15
> **aysiu said:**
> I agree with you completely on all counts.

But those who also think it is a huge deal and a security issue are also WRONG.

aysiu,

To me it's a huge deal when something so basic *may* dissuade a Windows user from using Ubuntu.

We've *got* to get the basics right. And by 'right' I mean acceptable to the mainstream user. Otherwise Linux will forever be thought of as a Geek's OS and that really would be a tragedy.

S

---

### Post by eeperson on 2009-07-15
> **Smartin said:**
> Given that both OSX *and Windows* have sensible security/privacy settings, I don't see how you can possibly make that argument stick.

S

The default settings on other operating systems is irrelevant to my comment.  I was not trying to argue about what the default settings should be.  I was merely trying address the differences between security and privacy.

For example, going back to the hotel analogy, if you keep your belongings in a locked hotel room with the curtains open (so anyone can see them), is your hotel room secure?  Is it private?  If you leave a piece of paper next to the window in your hotel room with login information to your bank account, is your hotel room unsecure or is your bank account unsecure?

I am not saying what the default permissions should be.  I am just trying to demonstrate that default read permissions in the home directory is not a computer security issue but a computer privacy issue.  The key words in the last sentence being 'computer'.  Admittedly a user could use their home directory to store sensitive information.  When they do this they are trying to leverage the computer privacy for security in some other system.  The Ubuntu devs cannot be responsible for the security of other systems but they can be responsible for the privacy of Ubuntu.

---

### Post by Smartin on 2009-07-15
> **eeperson said:**
> The default settings on other operating systems is irrelevant to my comment.  I was not trying to argue about what the default settings should be.  I was merely trying address the differences between security and privacy.

For example, going back to the hotel analogy, if you keep your belongings in a locked hotel room with the curtains open (so anyone can see them), is your hotel room secure?  Is it private?  If you leave a piece of paper next to the window in your hotel room with login information to your bank account, is your hotel room unsecure or is your bank account unsecure?

I am not saying what the default permissions should be.  I am just trying to demonstrate that default read permissions in the home directory is not a computer security issue but a computer privacy issue.  The key words in the last sentence being 'computer'.  Admittedly a user could use their home directory to store sensitive information.  When they do this they are trying to leverage the computer privacy for security in some other system.  

I absolutely take your point but I really think that the mainstream user deserves a wider interpretation of 'secure'.

To the mainstream user it's immaterial whether the security of the box has been breached or not. If someone can read their documents without a password the box is insecure. It has to be because their experience of Windows tells them to expect their documents to be 'secure'. They don't think 'private', they think 'secure'.

> 
The Ubuntu devs cannot be responsible for the security of other systems but they can be responsible for the privacy of Ubuntu.

And they are failing miserably at it.

S

---

### Post by John.Michael.Kane on 2009-07-15
Smartin

I am all for a good debate, however. IMHO the issue, is going in circles.

The problem as described has been thoroughly explained, and a manual fix was given. 

On top of that the problem cannot be fixed by forum members.

Barring any new information or theory on the problem.

The recourse available to you, for changing default settings, is to either write a brainstorm idea complete with a through reasoning why this needs to included out of the box.

Write up a blueprint on launchpad outlining why this needs to included out of the box.

Or

Submit a proposal for review by the Ubuntu Technical Board.

---

### Post by bapoumba on 2009-07-15
Temp closing for 24 hours. For the Staff: [http://ubuntuforums.org/showthread.php?t=1213667](http://ubuntuforums.org/showthread.php?t=1213667)

---

### Post by georgegerm on 2009-07-17
> **Smartin said:**
> David,

I'm 100% with you in terms of my love for the philosophy behind Ubuntu but forget all the issues with wi-fi, printing and screens etc...

Don't you think that the *main* issue which will prevent Ubuntu being taken seriously is one of Privacy and security?

Please have a look at my thread here

[http://ubuntuforums.org/showthread.php?t=1210175&page=3](http://ubuntuforums.org/showthread.php?t=1210175&page=3)

It starts at post #25 unfortunately as the mods are trying hard to bury the issue.

Please let me know what you think.

Simon

your thread is closed
i am schocked i did not read all of it but i will, and i must admit having no knowledge of this at all!!
for what i did read i find the comments to be simplifications of the issue, security is at times privacy and vice versa...
to state it is not a good idea for the home folder to be private from install on is in my opinion a sad response to a sad decision, it should all be as secure as possible without BEING RIDICULOUS !!
yes ill go a step further complete computer security is HAVING NONE, CONNECTED TO NOTHING !! naw i do not buy such silly arguments at all...
it seems a decision was made for the home folder to be readable by other users by default ,, thats an unprivate, unsecure way of going about things if it was avoidable..
i am a newbie so i do not speak about how to programm ubu i cannot, i am however a mature man with a lot of life behind and in front of me and i speak from the corner of common sense...
i can feel much sympathy for the ones against it being open by default indeed...
ps it is not a well known thing by the way, i am glad i found out
and no transparency for everyone is not a good thing, one should choose who can see what, and when (by default home = closed), regardless of the fact that some malicious people will always find ways of getting around this (that is not an excuse for not changing these settings)
reconsider please

---

### Post by aysiu on 2009-07-17
Not this again. Really.

It's already been stated many a time that lots of us agree it is a bad default, but Smartin is really blowing the problem out of proportion.

I have also linked to rationales for it (which I don't necessarily agree with personally) and a Brainstorm idea asking for the default to be changed.

What else do you want? Unless you can convince the developers to change the default, that's the default. Live with it, change it on your particular installation, or use another distro.

---

### Post by toupeiro on 2009-07-17
God,please people.  Rather than complain about it, learn about security and harden it yourself.

UMASK 077

stick it somewhere sourced by all accounts, even root, and be done with it.  or, understand your data and protect it a bit better.  a default 022 umask on a DESKTOP is fine.  It doesn't stop you from making a single directory or file more secure.

---

### Post by georgegerm on 2009-07-17
> **aysiu said:**
> Not this again. Really.

It's already been stated many a time that lots of us agree it is a bad default, but Smartin is really blowing the problem out of proportion.

I have also linked to rationales for it (which I don't necessarily agree with personally) and a Brainstorm idea asking for the default to be changed.

What else do you want? Unless you can convince the developers to change the default, that's the default. Live with it, change it on your particular installation, or use another distro.

please change the defaults if at all possible, if not thanks for trying anyway, and more thanks for taking this comment into consideration 
and please do not punish mr smartin he is just handling the open source way, pointing out something which he thinks can be improved, is important to him, and important for others to possibly know....
i will still use ubu if no change is done, taking care to close something i did not know, but do know now should be closed (in my opinion)
and above all else thanks for such a great product !
ps you can punish me with an all expenses paid trip to a great hotel in south africa, or anywhere else for that matter
:P

---

### Post by aysiu on 2009-07-17
> **georgegerm said:**
> please change the defaults if at all possible, You're talking to the wrong person. I am not a Ubuntu developer (or any developer, actually). I'd love for them to change the default, and I voted up that Brainstorm idea, but I don't think the Ubuntu devs are going to change it any time soon. > please do not punish mr smartin he is just handling the open source way, pointing out something which he thinks can be improved, is important to him, and important for others to possibly know.... I know Smartin means well, but that's not really the open source way. The open source way is to either fix it yourself, pay someone else to fix it, or use something else. You can ask nicely for someone else to fix it for free, but if that person doesn't want to fix it, you have to fix it yourself or use something else. My understanding is that Ubuntu and Debian are the only Linux distros that have this default.

---

### Post by lisati on 2009-07-17
One of the beauties of Ubuntu, and Linux in general, is the freedom to choose how to set up your own system. Sometimes this requires some learning, and sometimes this means the freedom to disagree (hopefully respectfully) with choices others have made.

---

### Post by zacktu on 2009-07-17
The originator of the thread implies that this is a fault of Ubuntu.  In my opinion the Ubuntu developers are just continuing the long-standing tradition of making one's home directory readable by everyone else on a Unix or linux system unless permissions have been changed to prevent that from happening.

---

### Post by georgegerm on 2009-07-17
I know Smartin means well, but that's not really the open source way. The open source way is to either fix it yourself, pay someone else to fix it, or use something else. You can ask nicely for someone else to fix it for free, but if that person doesn't want to fix it, you have to fix it yourself or use something else. My understanding is that Ubuntu and Debian are the only Linux distros that have this default.

thanx
i will like to disagree with limiting the open source way to only those 3 options....
i for one do not have the money or the knowledge to fix ubu at such a level, an other than asking nicelly for a fix which is the only remaining alternative, i believe and as a matter of fact i am sure that simply pointing out something (indeed pointing it out strongly), can also lead to positive results,,,
ubu prides itself on being for human beings i assume this by definition means also all of us humans not capable of using 2 of the 3 options, and not having much of chance achiving results with the 3rd directly, i would indeed strongly encourage people to simply speak out even if they are partly or completely wrong (which is not the case here).. that to me anyway seems to be more the open source spirit i so care about... but hey thats just me
to me ubu is not just a starter kit into linux, it is a permanent distro in my computer, i like the idea behind the os, or better said how i interpret the concept behind it
simply stated i believe ubu has people of great knowledge and abilities who share these with those of us of meager knowledge, they guide us into a state of comfort were we then can or maybe cannot contribute more to the mass effort
but time is money and the point has been made...
i also believe (not related to the subject matter) that being nice is an important issue, much too often relegated to economic principles......
open source is nice and so are you folk who so kindly help:KS

---

### Post by aysiu on 2009-07-17
Yes, asking nicely is one option, but I don't think Smartin has asked nicely.

This entitled outrage of "It has to be fixed now. This is unacceptable" doesn't really go far with developers unless it is a genuine security flaw and not just a less-than-ideal default.

And, as I said before, if you ask nicely, you can only *hope* the developers you ask will do what you ask. If they don't, you're left with only the other options--fork/fix it yourself, pay someone else to fix it, or just use something else altogether (another distro).

The proper way to communicate to the developers is through Brainstorm or Launchpad. This idea has already been posted on Brainstorm, so if you support the idea, vote for the brainstorm idea.

---

### Post by georgegerm on 2009-07-18
i understand....
it seems it is a bit out of proportion
that said i am gratefull hes made me aware of something i did not know, and as you i believe it should be changed... if an when possible (windblo$ does not sleep lol)
ps i voted guess for what ??????
thanx for making me wiser, all of ya!!!
the nice atheist fella down the road signs off

---

### Post by Smartin on 2009-07-19
> **aysiu said:**
> Yes, asking nicely is one option, but I don't think Smartin has asked nicely.


Just for the record, I wasn't asking for *anything*. I was asking *why* the defaults are as they are.

Then all hell broke loose...

S

---

### Post by Smartin on 2009-07-19
Guys,

(I don't understand how a poll came to be attached to the the thread I started... Not even sure this is my thread anymore...)

A while ago a contributor to the thread sent me a PM which made it clear that my tone was inappropriate and had upset them.

I want to publicly apologise for this.

The reputation of OS software and Ubuntu in particular, is just one of my 'buttons'. My argument/tone can get a bit ... eh... *robust*. 

I really do apologise.

Worse still, the person concerned felt bullied. This is super uncool of me. I am a wretch and I'm sorry.

We all need to stick together and I'm sorry if my tone has got in the way of this.

I still think the defaults are poor and that it is a big deal. One day it will change I'm sure.

S

---

### Post by saulgoode on 2009-07-20
For reasons of system security, admin accounts should not be readable by others. Aside from that, it is the system administrator's decision as to what level of privacy regular users should be afforded (and the default behavior doesn't matter to me).

---

### Post by Smartin on 2009-07-20
> **saulgoode said:**
> For reasons of system security, admin accounts should not be readable by others. Aside from that, it is the system administrator's decision as to what level of privacy regular users should be afforded (and the default behavior doesn't matter to me).

On my default install of 9.04, even the admin account was readable. I obviously thought it was an issue with my setup but was told it was supposed to be that way.

S

---

### Post by cariboo on 2009-07-21
You're wrong. See the screenshot. That is my regular user trying to cd in /root.

---

### Post by bodhi.zazen on 2009-07-21
I think he means admin = first user (with sudo -> root access) and not the root account itself.

---

### Post by cariboo on 2009-07-21
Well Duh!

---

### Post by Smartin on 2009-07-22
> **bodhi.zazen said:**
> I think he means admin = first user (with sudo -> root access) and not the root account itself.

Guys,

I mean a test user can read a document on the Admin user's desktop.

S

---

### Post by ssri on 2009-07-22
I'll just chime in my 2c here.  I agree with Smartin that the default setting is bad, and how this point is not made abundantly clear in the installer worse.  As such, the hotel, open curtain analogy does not seem be applicable here due to the fact of the obviousness seen in the analogy.  The person can plainly see the curtains are open, so she can close them if she desires some privacy conscience of this fact.  I do not think that someone running ubuntu for the first time is as equally aware as the person in the analogy.  For myself, I did not realize that this was the default until I started to add other users to a local machine running it.  Still, it was relatively easy to switch the settings to the desired privacy modes soon thereafter.  When everyone talks about how secure ubuntu is and that, I do not believe that it wrong for a newb to conflate this notion to mean that his home directory is safe from others users on his computer.

---

### Post by Smartin on 2009-07-22
> **ssri said:**
> I'll just chime in my 2c here.  I agree with Smartin that the default setting is bad, and how this point is not made abundantly clear in the installer worse.  As such, the hotel, open curtain analogy does not seem be applicable here due to the fact of the obviousness seen in the analogy.  The person can plainly see the curtains are open, so she can close them if she desires some privacy conscience of this fact.  I do not think that someone running ubuntu for the first time is as equally aware as the person in the analogy.  For myself, I did not realize that this was the default until I started to add other users to a local machine running it.  Still, it was relatively easy to switch the settings to the desired privacy modes soon thereafter.  When everyone talks about how secure ubuntu is and that, I do not believe that it wrong for a newb to conflate this notion to mean that his home directory is safe from others users on his computer.

ssri,

Thanks for that.

Judging from the couple of posts above, I'm now going back to wondering if there is something wrong with my install.

Some confusion seems to be setting in...

S

---

### Post by Mornedhel on 2009-07-22
I would like newcomers to learn Linux when they start using it, not blindly assuming everything is going to be just as in Windows.

So Windows defaults to having user homes unreadable to other standard users. OK, that's one way to do it.

Linux comes from a multi-user environment : at any point many users are expected to be logged on the same box and working with each other. The users were also expected to know how to manage their permissions (yes, there was one time everybody on a Linux box knew what chmod 644 meant) and to think about how they were managing them and who they wanted to be able to read their files. Making your documents non-world readable was an active decision and you had to trust the admin and the staff not to do anything else than what they were expected to do in the course of their job. People actually used the group rights. These were sane defaults, and they were carried on up to now.

Now that we cannot assume anymore that the users are educated or even want to be educated, now that Grandma being able to use Ubuntu is expected, now that the #1 bug in Launchpad is what it is, then another default might be considered.

But I don't think the current default is the end of the world. Rather, I would like the install process to ask explicitly which one of the two sane options (world-readable ~ and non-world-readable ~) is necessary. I *expect* my home folder to be world-readable because I have tried to educate myself on Linux permissions. I very much want this to still be a possibility.

The issue is definitely *not* one of security. It's one of privacy. Just because the end users don't know the difference doesn't make it otherwise.

---

### Post by issih on 2009-07-22
Hmmn, it is a bit dodgy, and probably should be changed, and definitely should be flagged up during install. The rest of this thread is just miscommunication and hyperbole (on both sides).

A better solution might be to offer encryption of home directories at install (using encryptfs) so that the problem goes away in a sensible and properly secure as well as private manner (I am assuming encryptfs is user specific here).

I really do despair of the" oh its not hard to fix..just do it yourself" attitude though... The default install is what we advertise ourselves with, its what every review is based on, its what every newbie sees and understands ubuntu to be until they learn better (which might be a long long time). If ubuntu wants to be a serious mainstream desktop OS (and whether you personally like it or not, that is the stated intention of this distro) then is needs to provide a well thought out, well designed default setup.

The "if you don't like it change it" attitude will not wash in this environment. I know why it exists, and understand its routes in OSS philosophy but for this project to succeed in its stated goals, it needs to be jettisoned.. quickly.

---

### Post by Smartin on 2009-07-22
> **Mornedhel said:**
> 
I would like the install process to ask explicitly which one of the two sane options (world-readable ~ and non-world-readable ~) is necessary. 



The thing is, it's not quite as simple as locking others *completely* out of the Home folder as  controlled sharing is obviously desirable.

>  The issue is definitely *not* one of security. It's one of privacy. Just because the end users don't know the difference doesn't make it otherwise.

Don't really want to do that one again... ;)

S

---

### Post by Smartin on 2009-07-22
> **issih said:**
> Hmmn, it is a bit dodgy, and probably should be changed, and definitely should be flagged up during install. The rest of this thread is just miscommunication and hyperbole (on both sides).

A better solution might be to offer encryption of home directories at install (using encryptfs) so that the problem goes away in a sensible and properly secure as well as private manner (I am assuming encryptfs is user specific here).

I really do despair of the" oh its not hard to fix..just do it yourself" attitude though... The default install is what we advertise ourselves with, its what every review is based on, its what every newbie sees and understands ubuntu to be until they learn better (which might be a long long time). If ubuntu wants to be a serious mainstream desktop OS (and whether you personally like it or not, that is the stated intention of this distro) then is needs to provide a well thought out, well designed default setup.

The "if you don't like it change it" attitude will not wash in this environment. I know why it exists, and understand its routes in OSS philosophy but for this project to succeed in its stated goals, it needs to be jettisoned.. quickly.

issih,

Thank you for that.

I really think the Ubuntu 'Powers That Be' need to start thinking outside the OS box and provide an environment which is familiar to Windows converts. They are 99% there already FGS.

Some people like to tinker with computers and some like things to 'just work'. The mainstream like things to 'Just Work'. *If* that is Ubuntu's audience, they need to make one or two minor changes. Nothing more.

S

---

### Post by Student Driver on 2009-07-22
Well, I for one was surprised that my daughter (6) could access my wife's files on the same laptop.  Neither my wife nor I thought that would be the case, and I immediately disabled my daughter's account until I could figure out what went "wrong."  Turns out, this is the default behavior, which I think is insane.  Considering that a user might have other mounts within his home directory, only to have another user in switch user mode traverse those as well isn't very cool at all.

So yes, I believe this should be changed.  I thought Red Hat and other distros didn't work like this (I will check my CentOS server at home) and this should be fixed.

---

### Post by Smartin on 2009-07-22
> **Student Driver said:**
> Well, I for one was surprised that my daughter (6) could access my wife's files on the same laptop.  Neither my wife nor I thought that would be the case, and I immediately disabled my daughter's account until I could figure out what went "wrong."  Turns out, this is the default behavior, which I think is insane.  Considering that a user might have other mounts within his home directory, only to have another user in switch user mode traverse those as well isn't very cool at all.

So yes, I believe this should be changed.  I thought Red Hat and other distros didn't work like this (I will check my CentOS server at home) and this should be fixed.

Student Driver,

Thanks for that one...

I'd be really interested to know what other distros do.

I'm guessing the server versions might be different from the Desktop versions though...

I was at first of the opinion that the server version ought to have 'Private Home' permissions, and still am, but at least a server admin is more likely to know the score here. On a 'Consumer' desktop OS, the fact that one user is the admin doesn't mean much in terms of the knowledge they have.

S

---

### Post by heyyy on 2009-07-22
although ubuntu is great, i agree with smartin 
and if it wasn't for him to mention it,i wouldn't "notice it"....
but being a newbe,could someone give some instructions in order to change this(setting my folders private)?

---

### Post by Tibuda on 2009-07-22
> **heyyy said:**
> although ubuntu is great, i agree with smartin 
and if it wasn't for him to mention it,i wouldn't "notice it"....
but being a newbe,could someone give some instructions in order to change this(setting my folders private)?

Open your home folder. Browse to /home directory. Right-click your user folder, and click properties. Open the "permissions" tab, disable access from group and others. You don't even neet root to do this. You can also use a one-line terminal command:```
chmod 700 $HOME
```

---

### Post by heyyy on 2009-07-22
> **danielrmt said:**
> Open your home folder. Browse to /home directory. Right-click your user folder, and click properties. Open the "permissions" tab, disable access from group and others. You don't even neet root to do this. You can also use a one-line terminal command:```
chmod 700 $HOME
```

thanks and one more think
i found a [link]("http://ubuntuforums.org/showpost.php?p=4461165&postcount=4") relative to the subject 
should i do this also?

---

### Post by Tibuda on 2009-07-22
> **heyyy said:**
> thanks and one more think
i found a [link]("http://ubuntuforums.org/showpost.php?p=4461165&postcount=4") relative to the subject 
should i do this also?

If you have removed the group permissions you don't really need to do that.

---

### Post by Smartin on 2009-07-22
> **danielrmt said:**
> Open your home folder. Browse to /home directory. Right-click your user folder, and click properties. Open the "permissions" tab, disable access from group and others. You don't even neet root to do this. You can also use a one-line terminal command:```
chmod 700 $HOME
```

danielrmt,

This completely kills any sharing though, right?

S

---

### Post by Tibuda on 2009-07-22
> **Smartin said:**
> danielrmt,

This completely kills any sharing though, right?

S

By your computer users, yes. By someone running a LiveCD or removing the harddisk, no.

---

### Post by aysiu on 2009-07-22
I'm not sure *chmod*ing the home directory will really be effective.

Won't that just change permissions on the currently existing files and folders within the home folder and not the newly created files and folders in that directory?

---

### Post by heyyy on 2009-07-22
> **danielrmt said:**
> If you have removed the group permissions you don't really need to do that.

ok 
one more thing in order to understand:
with the [link]("http://ubuntuforums.org/showpost.php?p=4461165&postcount=4") i provided before you make this kind of configuration default for all users,right?

---

### Post by Tibuda on 2009-07-22
> **aysiu said:**
> I'm not sure *chmod*ing the home directory will really be effective.

Won't that just change permissions on the currently existing files and folders within the home folder and not the newly created files and folders in that directory?

No. If a user can't access a folder parent, it won't access the subfolders. I have to keep my home 755 because I need the www-data user (Apache server) to be able to read /home/danielrmt/public_html. If my home is 700, it won't be able to.

A little experiment:
```
~$ mkdir /tmp/test
~$ mkdir /tmp/test/test2
~$ touch /tmp/test/test2/test3
~$ chmod 700 /tmp/test
~$ touch /tmp/test/test2/test4
~$ ls /tmp/test/test2 -l
total 0
-rw-r--r-- 1 danielrmt danielrmt 0 2009-07-22 16:27 test3
-rw-r--r-- 1 danielrmt danielrmt 0 2009-07-22 16:27 test4
~$ sudo -u guest ls /tmp/test/test2 -l
ls: cannot access /tmp/test/test2: Permission denied
~$ 
```

---

### Post by Student Driver on 2009-07-22
> **danielrmt said:**
> No. If a user can't access a folder parent, it won't access the subfolders. I have to keep my home 755 because I need the www-data user (Apache server) to be able to read /home/danielrmt/public_html. If my home is 700, it won't be able to.

A little experiment:
```
~$ mkdir /tmp/test
~$ mkdir /tmp/test/test2
~$ touch /tmp/test/test2/test3
~$ chmod 700 /tmp/test
~$ touch /tmp/test/test2/test4
~$ ls /tmp/test/test2 -l
total 0
-rw-r--r-- 1 danielrmt danielrmt 0 2009-07-22 16:27 test3
-rw-r--r-- 1 danielrmt danielrmt 0 2009-07-22 16:27 test4
~$ sudo -u guest ls /tmp/test/test2 -l
ls: cannot access /tmp/test/test2: Permission denied
~$ 
```

To further this, in Windows it's called "bypass traverse checking."  This is a security setting that allows someone to not have access to a parent directory, but access to a specific object nested several directories within.  If this is disabled, it forces Windows to evaluate the entire path (what Linux appears to do on distros I've used) before allowing access to an object.  I can see how someone might confuse this behavior with other operating systems.  

[http://technet.microsoft.com/en-us/library/cc976473.aspx]("http://technet.microsoft.com/en-us/library/cc976473.aspx")

In Linux, you use the execute bit on a directory to allow traversal (the "search bit").

[http://www.tuxfiles.org/linuxhelp/filepermissions.html]("http://www.tuxfiles.org/linuxhelp/filepermissions.html")

HTH

---

### Post by castrojo on 2009-07-22
[https://wiki.ubuntu.com/DebuggingSecurity#Permissive%20Home%20Directory%20Permissions](https://wiki.ubuntu.com/DebuggingSecurity#Permissive%20Home%20Directory%20Permissions)

---

### Post by aysiu on 2009-07-22
> **whiprush said:**
> [https://wiki.ubuntu.com/DebuggingSecurity#Permissive%20Home%20Directory%20Permissions](https://wiki.ubuntu.com/DebuggingSecurity#Permissive%20Home%20Directory%20Permissions)
From [the bug report](https://bugs.launchpad.net/ubuntu/+source/adduser/+bug/48734) linked to from your link: [quote=Colin Watson]I do maintain that the default is correct. On most multi-user systems, there is some level of cooperation (if not trust) among the users - they'll be members of the same family, or friends, or co-workers, or whatever - and it is useful for them to be able to share files reasonably conveniently (e-mail is an awful solution to this).[/quote] The proper way for them to conveniently share files is through a shared folder. That's what both Windows and Mac have, and it shouldn't be too difficult for Ubuntu to include one by default. /home/*username* would be 600, and /home/shared would be 666. > It's easier to create a private directory for the things you don't want to be public than it is to figure out how to open up your home directory so that just a few things can be read. Yes, agreed. The private directory is your /home/*username* directory, and the public one would be /home/shared or /home/public > (I use quite a lot of multi-user Unix systems on a regular basis, both at work and among my family and friends, and it's far more common for me to want things accessible to other users than it is for me to want them to be inaccessible.) That's great. Again, that can be achieved by dumping things in the public or shared folder. > By the way, to change the default for new users on an existing system, change DIR_MODE in /etc/adduser.conf. That's a helpful tip. Maybe advanced users who want to be permissive can change it to be more permissive, then? [quote=unggnu]Why not ask in the installer while the password and user name is set if the directory should be readable or not? One line with a checkbox and an explanation would be enough.[/quote] That would be annoying. Ubuntu is supposed to be about sensible defaults and not including a lot of extra questions during installation. The sensible default, of course, would be making the home directories *not* readable by other users. > I really think that it is better to just create a shared folder which is shown on the desktop and places instead of opening the home directory wide. I agree. > Btw. every experienced user knows how to change the home directory to make it less restrictive so it wouldn't bother them but it would be more secure for every one. I agree with this also.

The thing is, it's better to err or on the side of giving too little than giving too much without alerting the user. I prefer opt-in instead of opt-out. If I want to share stuff, I want to explicitly say "I want to share this." It doesn't make sense to say let's just share everything and then explicitly obscure things we do not want to share.

I also am not sure how useful 644 is for sharing, anyway.

If I am sharing, for example, music with a family member, if the music is in my /home/username/Music folder, that family member can access the music but can't add to it. So unless I am always in charge of adding music then one of the following scenarios would ensue: [list][*]Each user maintains her own music collection but we have to check with each other not to duplicate songs, and then we share our collections.[*]Each user maintains her own music collection, and we do not share collections, in which case, what's the point of 644?[*]One user maintains her own collection and any time another user wants to add to the collection, that user has to go through the maintainer to add a song. Annoying.[/list] All of those scenarios are annoying.

The obvious solution would be a shared folder.

/home/*username* would be 600 and contain documents that only *username* wants to access (read, write, possibly execute).

/home/shared would be 666 (or maybe 660) and contain documents that all users on the system (family members, co-workers) want to share with each other--documents they're co-editing, music collections, photos.

644 is impractical. It doesn't really allow for full sharing of files because others cannot modify your files--only read them. But it also doesn't really protect your files, since anyone can read them. It's like the worst of both worlds. If I'm going to be sharing files with people, I'd at least them to be able to modify and add files.

I know Smartin has tried to make me out to a bad guy in the thread, but I agree fully that this is a dumb default, and I've said so all along. My main objection to this thread was Smartin's tone and air of indignation that this was some huge security issue.

It is a dumb default and should be changed.

It isn't a huge security issue, though. If people have documents they want secured, they should encrypt those documents. But 644 is also completely useless for sharing purposes.

---

### Post by bodhi.zazen on 2009-07-22
Well,  666 would be evil for /home/shared :twisted:

---

### Post by bodhi.zazen on 2009-07-22
Setting up a shared directory is complex, and can get worse with increasing numbers of users and groups.

This is a (brief) overview of one way to do it :

[http://www.cyberciti.biz/faq/linux-setup-shared-directory/](http://www.cyberciti.biz/faq/linux-setup-shared-directory/)

But you need to watch the umask values of your users, write cron tasks to change ownership and permissions from time to time, watch for directories in shared directories, etc, and other things like that.

ACL is easier, but then you need to learn acl.

---

### Post by aysiu on 2009-07-22
> **bodhi.zazen said:**
> Setting up a shared directory is complex, and can get worse with increasing numbers of users and groups. Can you explain some of the complexities of it?

---

### Post by blur xc on 2009-07-22
I just want to know what you guys are doing w/ your computers, and where you are keeping them if you are so upset over this issue?  Do you keep your pc on the sidewalk on a busy street or something?  Geez...  I've been on windows for most my computing life, and I've always had read write access between the user accounts on our home computer.  There's nothing sensitive on any of them, and no one in our house is going to be doing anything malicious anyway, so who cares?

And even so, the fix is so simple, it's amazing that it is such an issue.  

Four our new computer, I tried to talk my wife into just setting up one shared user account, but she wants her own deal...so we will keep seperate accounts.  She's the one on the computer 99% of the time anyway, so most times when I need it I just use it under her account.  It's just easier than switching users all the time.  My 8yr old son has his account he'll switch into sometimes, but it's mostly just so he can set up his own wallpaper- transformers, pokemon, etc...  whatever he's into at the time.  When he's not on his user account, he's also just using my wife's.  I don't have any fears of anyone maliciously deleting file or screwing up our system.  I do a good enough job of doing that on my own.  :P

Heck, on our XP machine, we don't even have login passwords.  Just click on the username icon and call it good.

BM

---

### Post by aysiu on 2009-07-22
> **Barna Madau said:**
> I just want to know what you guys are doing w/ your computers, and where you are keeping them if you are so upset over this issue? > 
And even so, the fix is so simple, it's amazing that it is such an issue. I agree fully. It's much ado about very little. If this never gets fixed, I'm fine with it.

But it should still be fixed. It is a bad default. Not a huge issue. Not a security flaw. Just a bad default, and it should be changed to a good default.

---

### Post by bodhi.zazen on 2009-07-22
Well, 660 is perfect for files, directories need x , so 755 or 777

The problem is most people (who set up a shared directory) want one umask for shared files, and another for private files. The other problem is most people do not want a global share, so the want a group.

(As an aside, a umask is how one sets the default permissions of a new file. If you "touch foo" the file will be owned by you:your_current_group (default is primary) with permissions determined by your current umask).

So how to set a umask and how to manage groups. Do you change the users primary group (newgrp) to access shares ? Do you set a new umask ? etc.

So as a broader topic, setting a share is a larger can of worms then the defaults on $HOME.

See this thread (as an example): [**Permissions on a shared directory**]("http://ubuntuforums.org/showthread.php?t=145741")

There are several ways to try to make it as easy as possible, the link I gave is nice, so are acl. Some people make a specific group for shares and use scripts to change the ownership and permissions of files in a share.

Gets more interesting if it is a network share :twisted:

Personally I think ACL are the way to go.

[Linux.com :: Smart ACL management with Eiciel]("http://www.linux.com/feature/138169") (Eiciel is in the ubuntu repos, although you need to enable acl in fstab and reboot).

So it is complex as there are more choices / decisions to be made.

---

### Post by bodhi.zazen on 2009-07-22
> **Barna Madau said:**
> I just want to know what you guys are doing w/ your computers, and where you are keeping them if you are so upset over this issue?  Do you keep your pc on the sidewalk on a busy street or something?  Geez...  I've been on windows for most my computing life, and I've always had read write access between the user accounts on our home computer.  There's nothing sensitive on any of them, and no one in our house is going to be doing anything malicious anyway, so who cares?

And even so, the fix is so simple, it's amazing that it is such an issue.  

Four our new computer, I tried to talk my wife into just setting up one shared user account, but she wants her own deal...so we will keep seperate accounts.  She's the one on the computer 99% of the time anyway, so most times when I need it I just use it under her account.  It's just easier than switching users all the time.  My 8yr old son has his account he'll switch into sometimes, but it's mostly just so he can set up his own wallpaper- transformers, pokemon, etc...  whatever he's into at the time.  When he's not on his user account, he's also just using my wife's.  I don't have any fears of anyone maliciously deleting file or screwing up our system.  I do a good enough job of doing that on my own.  :P

Heck, on our XP machine, we don't even have login passwords.  Just click on the username icon and call it good.

BM

I am thinking for most users it is trivial, almost a non-issue, as you say.

For some users it is a big issue for a variety of reasons.

Of course if you change the default to 700 , all the people who want some kind of share in $HOME will complain - "The defaults of ubuntu broke ~/html" or ~/samba or ~/ftp or ~/family_pics or whatever.

So really there are no single set of defaults that will please everybody, I mean really.

Really, as with any OS, change the defaults if you do not like them. If you are trying a new OS **do not make assumptions on how it works**. If private home are important to you, make sure home is private and so on. Defaults only go so far, usually about 5 minutes =)

I have advised the OP in a series of (fairly long) PM on how to present his suggestion to the Ubuntu developers or the technical review board but do not know if he followed my advice. Discussing the issue on the forums is very very unlikely to change anything.

---

### Post by Smartin on 2009-07-23
> **aysiu said:**
> 

I know Smartin has tried to make me out to a bad guy in the thread


aysiu,

I'm just skimming through stuff for the moment but I have to comment on this one now.

It's totally unfair to say I have been making you out as a bad guy. *Nobody* in this is 'bad'. A group of people made what I think was a wrong call when they decided on the defaults. That's all.

My original post was asking *why* they made the decision.

My contention is that not enough people know about this and that it has an adverse effect on Ubuntu's reputation. That's all. 

No-one will die as a consequence of this. I confess to being one of these dorks who gets overexcited about OS and I will try hard to rein in my exuberance. I would like a change to be made to the defaults but I don't mean to infer that this is all your fault :)

When this is all forgotten about I hope we can all feel we are still friends. I don't expect a spirited argument to make enemies out of people.

I have already apologised for my tone. If you missed it, it's on page nine of the thread, post 82.

[http://ubuntuforums.org/showthread.php?t=1210175&page=9](http://ubuntuforums.org/showthread.php?t=1210175&page=9)

If you still feel I am somehow not being respectful to you, I would like to apologise again to you in particular. I'm sorry. I'll do my best to improve. It *is* very difficult to put across emotional meaning by text though. At least I find it so...

S

---

### Post by Mornedhel on 2009-07-23
> **Smartin said:**
> My contention is that not enough people know about this and that it has an adverse effect on Ubuntu's reputation.

I'm curious : if not enough people know about this, how can it have an effect on Ubuntu's reputation ? (Not trying to flame you, I just want to know how you reconcile both sentences.)

---

### Post by bodhi.zazen on 2009-07-23
> **Smartin said:**
> My original post was asking *why* they made the decision.

I think the why was already mentioned in this therad :

[https://wiki.ubuntu.com/DebuggingSecurity#Permissive%20Home%20Directory%20Permissions](https://wiki.ubuntu.com/DebuggingSecurity#Permissive%20Home%20Directory%20Permissions)

Have you given any though to perusing your concerns through the avenues I have advised ?

---

### Post by Smartin on 2009-07-23
> **Mornedhel said:**
> I'm curious : if not enough people know about this, how can it have an effect on Ubuntu's reputation ? (Not trying to flame you, I just want to know how you reconcile both sentences.)

Mornedhel,

(I'm going to be accused of Trolling and 'broken arguments' now...)

Because the effect on Ubuntu's reputation isn't necessarily proportional to how many people know about the issue.

I believe (and this seems to be borne out by several comments in this thread) that even people who have used Ubuntu for a while haven't realised that the permissions are the way they are, let alone new Windows converts. 

I also believe that when a potential Windows convert comes to realise the default permissions, their faith in Ubuntu will be undermined.

"Hey, I tried that Ubuntu thing yesterday!"

"Cool. What was it like?"

"Well... the install was easy... but... you know... they set my home folder up so anyone can read anything in there."

"No way...!!??"

"I swear. That's the default."

"Thanks for letting me know. I'm sticking to Windows."

We lost two potential converts, not just one.

The fact that it's easy to fix has nothing to do with it. It's such a basic expectation that they won't take the time to learn *how* to fix it. Facebook beckons. Why should they have to mess about with something so basic?

Would you trust the brakes of your family's car to someone who didn't know where the dip-stick for the oil was or what it was for? I don't think I would.

I'm not the only one who believes the 'It's not a security issue, it's a privacy one' is simplistic. Users expect the box to be secure and their documents to be private. To a consumer, this is one and the same thing. Call it 'Pricurity' if you like...

This issue seems to come up so often that when the mods spot it rearing it's head they move it to a dark corner of the forums. One which isn't even visible from the index page of the forums.

The decision has obviously been made and isn't going to change. At least not until enough people make enough noise about it.

If this issue was *clearly* not about 'Pricurity' I wouldn't be bothering with it but I am so worried that Ubuntu's reputation is suffering that I can't help myself.

I can't see the upside of the present situation or the downside of doing it the OSX way.

The OSX permissions are typically simple and elegant:

My Home folder is read/write by anyone, to allow sharing.

Inside there I have:
Desktop
Documents
Library
Movies
Pictures
Which are all locked to anyone but me.

Then I have a 'Public' folder which is readable by anyone. Within that there is a 'Drop box' which is write only.

I then also have a 'Sites' folder which is the Apache folder. 

Simple!

If I wanted to share all my files with everyone, I would put them all in the Public folder.

*Where* is the downside?

Anyway... there I go again. I expect the thread will be locked again now. Sorry.

S

---

### Post by Smartin on 2009-07-23
> **bodhi.zazen said:**
> I think the why was already mentioned in this therad :

[https://wiki.ubuntu.com/DebuggingSecurity#Permissive%20Home%20Directory%20Permissions](https://wiki.ubuntu.com/DebuggingSecurity#Permissive%20Home%20Directory%20Permissions)



Ok. Now we know.

I *still* think it should at least be flagged during the install. It's such an unexpected thing.

> Have you given any though to perusing your concerns through the avenues I have advised ?

There seems little point to be honest. As I just said in another post, the decision seems to be written in stone. Otherwise the issue wouldn't get buried in the 'Recurring Discussions' corner.

In any case, I think someone a bit more diplomatic than me would be better off doing it...:D

S

---

### Post by Mornedhel on 2009-07-23
Smartin: Thanks for clarifying what you meant. I still disagree about this being a "basic expectation", but I get your point.

> **Smartin]The OSX permissions are typically simple and elegant:

My Home folder is read/write by anyone, to allow sharing.[/QUOTE]

Your Home folder is world-writable ?! Now *this* I take issue with. World-readable is OK by me (that's only my opinion and yours may differ), but world-writable basically means you can DOS a user by filling up his quota. Are you certain about that ?

As for the issue of Pricurity, Linux won't take any lessons from an OS that historically encouraged every user to have a full administrator account and is still the main target, by far, for all kinds of malware.

[QUOTE=Smartin said:**
> As I just said in another post, the decision seems to be written in stone. Otherwise the issue wouldn't get buried in the 'Recurring Discussions' corner.

bodhi.zazen: See what I mean about rumors of disagreement being censored ? I'm not saying that Smartin is a troll, he is genuinely concerned, but I've come across Slashdot posts blatantly accusing Canonical of actively banning users and removing threads that criticized Canonical policies. (Slashdot is obviously not the definitive source for information and there are a lot of trolls there as well, but it's a good general indicator of the techy population's opinion.)

---

### Post by blur xc on 2009-07-23
> **Smartin said:**
> 
The OSX permissions are typically simple and elegant:

My Home folder is read/write by anyone, to allow sharing.

Inside there I have:
Desktop
Documents
Library
Movies
Pictures
Which are all locked to anyone but me.

Then I have a 'Public' folder which is also read/write by anyone. Within that there is a 'Drop box' which is write only.

I then also have a 'Sites' folder which is the Apache folder. 

Simple!

If I wanted to share all my files with everyone, I would put them all in the Public folder.

*Where* is the downside?

Anyway... there I go again. I expect the thread will be locked again now. Sorry.

S

I'm really curious, and trying to understand your pov-  How many computer users have regular access to your pc?  What environment is you computer in?  How do you handle other, non computer, sensitive documents (bills, credit card statements, etc.)?

I  think of ubuntu as a general home pc os.  Maybe for a public environment like schools or a busniess maybe another distro would be more applicable, but even so, in any of those environments I imagine you'd have a knowledgable system administrator that would tweak permisssions to whatever is appropriate.

The most sensitive documents on my pc are my photographs, from about the last 7 yrs on an external hard drive- and no one in my house is going to go around randomly deleting files.  

Someone with malicious intent could do me a lot more damage by stealing mail from my mailbox or coming into my house and taking credit card and bank statements than reading any random document in my home folder.

BM

---

### Post by Smartin on 2009-07-23
> **Mornedhel said:**
> Smartin: Thanks for clarifying what you meant. I still disagree about this being a "basic expectation", but I get your point.



Your Home folder is world-writable ?! Now *this* I take issue with. World-readable is OK by me (that's only my opinion and yours may differ), but world-writable basically means you can DOS a user by filling up his quota. Are you certain about that ?

No! Sorry. I just double checked and there are no writable folders other than the Drop box. I was making assumptions. My fault.

> As for the issue of Pricurity, Linux won't take any lessons from an OS that historically encouraged every user to have a full administrator account and is still the main target, by far, for all kinds of malware.

You mean OSX?

I personally think Ubuntu should shamelessly take anything which is good from any OS, regardless.


> bodhi.zazen: See what I mean about rumors of disagreement being censored ? I'm not saying that Smartin is a troll, he is genuinely concerned, but I've come across Slashdot posts blatantly accusing Canonical of actively banning users and removing threads that criticized Canonical policies. (Slashdot is obviously not the definitive source for information and there are a lot of trolls there as well, but it's a good general indicator of the techy population's opinion.)

So it's not just me being paranoid...

S

---

### Post by Mornedhel on 2009-07-23
> **Smartin said:**
> You mean OSX?

I would have thought "the main target for malware" would have correctly been identified as Windows. Your example dealt with Windows users.

> **Smartin said:**
> So it's not just me being paranoid...

All you can conclude from the fact that others have voiced such a concern is that at least one of the following propositions is true :

A there are trolls on Slashdot/the Internet
B there are paranoid people on Slashdot/the Internet
C the Ubuntu forums are being censored

Since A and B are provably true, C doesn't have to be.

---

### Post by Smartin on 2009-07-23
> **Barna Madau said:**
> I'm really curious, and trying to understand your pov-  How many computer users have regular access to your pc?  What environment is you computer in? 

A perfectly benign one. Very little chance of anyone wanting to steal anything from it.

> How do you handle other, non computer, sensitive documents (bills, credit card statements, etc.)?

I generally leave them strewn around the house for anyone to see :D

My point is quite simply this: I believe Windows converts expect different permissions. Once they find that Ubuntu has such a permissive setup, they will wonder what else is 'Wrong' with it.

Ubuntu has to be better than Windows in as many ways as possible, for it to become mainstream. The *basics* definitely have to be right. I think this is one of the basics.

I would personally love to put my weight behind another distro but I believe Ubuntu stands the best chance of toppling Windows. Therefore I stick with it.

S

---

### Post by Smartin on 2009-07-23
> **Mornedhel said:**
> I would have thought "the main target for malware" would have correctly been identified as Windows.

Me to but I was (wrongly) describing my OSX permissions...

>  Your example dealt with Windows users.

I'm *trying* not to appear to know *anything at all* abut Windows because I really don't. My dislike for MS runs so deep I wash my hands after touching anything with their name on it. Seriously.

I have however asked a few people and spout their responses.

> All you can conclude from the fact that others have voiced such a concern is that at least one of the following propositions is true :

A there are trolls on Slashdot/the Internet
B there are paranoid people on Slashdot/the Internet
C the Ubuntu forums are being censored

Since A and B are provably true, C doesn't have to be.

Don't quite follow that one :D

S

---

### Post by blur xc on 2009-07-23
> **Smartin said:**
> A perfectly benign one. Very little chance of anyone wanting to steal anything from it.



I generally leave them strewn around the house for anyone to see :D

My point is quite simply this: I believe Windows converts expect different permissions. Once they find that Ubuntu has such a permissive setup, they will wonder what else is 'Wrong' with it.

Ubuntu has to be better than Windows in as many ways as possible, for it to become mainstream. The *basics* definitely have to be right. I think this is one of the basics.

I would personally love to put my weight behind another distro but I believe Ubuntu stands the best chance of toppling Windows. Therefore I stick with it.

S

Honestly, being a windows user of many, many years, I don't think 99.9% of them have any idea what permissions are.  I didn't, except for in a work environment.  And it had nothing to do w/ my pc, but permissions to network folders.  What average computer illiterate pc user had network folders at home?

By default, most home users have full admin privileges anyway, and a lot of people (my house included) leave themselves logged in all day and all night anyway.  

Linuxes method of having all files owned by a specific user is already miles ahead of anything windows has to offer.

Like I said, I've been using windows for many years, and I still don't know how to change permissions- but I've been using Ubuntu for a few months and do...  That's what's important.  MS dictates to you how you should use your computer, and if there's anything else you need to know, it's only given out on a need to know basis, for a fee.  Ubuntu encourages the user to know everything, and gives them the power to do anything they want, for free.  All it takes is the desire to learn it.

BM

---

### Post by aysiu on 2009-07-23
Potential thread hijack moved to [another thread](http://ubuntuforums.org/showthread.php?p=7665219#post7665219).

---

### Post by Smartin on 2009-07-23
> **Barna Madau said:**
> Honestly, being a windows user of many, many years, I don't think 99.9% of them have any idea what permissions are.

Exactly. They just want things to work. Why should they have to learn about permissions?

If the defaults are sensible they don't need messing with.

>  MS dictates to you how you should use your computer, and if there's anything else you need to know, it's only given out on a need to know basis, for a fee. 
BM

Respectfully, aren't you contradicting yourself?

Isn't it Ubuntu which is forcing the user into changing things which they would normally take for granted?

(I'm coming across as a Windows advocate which is making me a bit queasy...)

S

---

### Post by blur xc on 2009-07-23
> **Smartin said:**
> Exactly. They just want things to work. Why should they have to learn about permissions?

If the defaults are sensible they don't need messing with.



Respectfully, aren't you contradicting yourself?

Isn't it Ubuntu which is forcing the user into changing things which they would normally take for granted?

(I'm coming across as a Windows advocate which is making me a bit queasy...)

S

ok- let me rephrase.  99.9% of windows users don't know what permissions are- generally only one one user account on their computer, and all have admin access and don't know it.  If they clicked some link to install something and they got the "You don't have access yada yada" they'd think something was wrong w/ their computer.

So- if you have one user account, no login password (just the cool XP login buddy icon), full admin privelages, how secure is that?  How is that better than the ubuntu default?

BM

---

### Post by murcherson on 2009-07-23
Ok i haven't read the arguments for or against and I really don't see the point of doing so. I have finally (after 4 attempts over the last 5 years) completely swapped OS from the Microsoft ship to something I am both comfortable and happy with. 

I am learning and having an amazing amount of fun with linux and especially Ubuntu. 

THEN THIS. I read the first post, tested it myself and I am now writing this reply. This will be my first and last comment on this issue. 

FIX IT. No justification against is applicable in my mind nor should it be. Not many things in this life are black and white but this is.

All reasonable measures of security should be applied as default. This most definitely includes granting each and every individual user a guaranteed level of privacy. Along side this is a guaranteed level of protection for minors. This is simple. 

As a community we have a beautiful, friendly and fun flagship OS to introduce the blinded masses to the freedom of open source. The ability to freely view all other users files by default can only be defined as a massive bear-trap in the path of joy.

Lead the way Ubuntu. Do not be dragged into arguments about what OS does what, who should be responsible or environment considerations. 

Let the choice to share amongst users be a fledgling administrators educational step and not a new users pitfall.

---

### Post by aysiu on 2009-07-24
> **murcherson said:**
> 
FIX IT. No justification against is applicable in my mind nor should it be. Not many things in this life are black and white but this is. No one participating in this thread has the power to change this, so I don't see what the point of your post is.

If you want to communicate your advocacy of this, vote for the idea on Brainstorm:
[Idea #6106: Make so other people cant access your home directory ](http://brainstorm.ubuntu.com/idea/6106/)

---

### Post by Smartin on 2009-07-24
> **murcherson said:**
> Ok i haven't read the arguments for or against and I really don't see the point of doing so. I have finally (after 4 attempts over the last 5 years) completely swapped OS from the Microsoft ship to something I am both comfortable and happy with. 

I am learning and having an amazing amount of fun with linux and especially Ubuntu. 

THEN THIS. I read the first post, tested it myself and I am now writing this reply. This will be my first and last comment on this issue. 

FIX IT. No justification against is applicable in my mind nor should it be. Not many things in this life are black and white but this is.

All reasonable measures of security should be applied as default. This most definitely includes granting each and every individual user a guaranteed level of privacy. Along side this is a guaranteed level of protection for minors. This is simple. 

As a community we have a beautiful, friendly and fun flagship OS to introduce the blinded masses to the freedom of open source. The ability to freely view all other users files by default can only be defined as a massive bear-trap in the path of joy.

Lead the way Ubuntu. Do not be dragged into arguments about what OS does what, who should be responsible or environment considerations. 

Let the choice to share amongst users be a fledgling administrators educational step and not a new users pitfall.

Hallelujah!

(Where have you been all this time? Stick around please) :D

S

---

### Post by Smartin on 2009-07-24
> **aysiu said:**
> No one participating in this thread has the power to change this, so I don't see what the point of your post is.

If you want to communicate your advocacy of this, vote for the idea on Brainstorm:
[Idea #6106: Make so other people cant access your home directory ](http://brainstorm.ubuntu.com/idea/6106/)

aysiu (My dear friend ) ;-)

It would be a real shame if we felt that only *some* people had influence over these things. One of the very great things about OS is The Community.

If the Ubuntu hierarchy is such that they won't take notice of the community, it will be to their very severe detriment.

I tried to post a new item in the brainstorming area but it never showed up. It added fuel to my conspiracy theory I'm afraid.

However... I do think those who are in agreement that a change should be made, should perhaps start a new thread and do a pre-brainstorm as to how the idea should be presented. Then it won't get diluted by loads of other suggestions when it does appear in the brainstorming area.

What say you? (I'm not hijacking my own thread btw... Please don't move this post if at all possible...)

S

---

### Post by Smartin on 2009-07-24
> **Barna Madau said:**
> ok- let me rephrase.  99.9% of windows users don't know what permissions are- generally only one one user account on their computer, and all have admin access and don't know it.  If they clicked some link to install something and they got the "You don't have access yada yada" they'd think something was wrong w/ their computer.

I'm not suggesting the admin user should get such a warning. The admin is the admin and should be able to do anything at all times, more or less.

As a security measure, my day-to-day account on my OSX box is a non-admin account for this very reason.

> So- if you have one user account, no login password (just the cool XP login buddy icon), full admin privelages, how secure is that?  How is that better than the ubuntu default?

BM

In that case you are in (what you believe to be) a 100% trusted environment and this whole thing *happens* not to apply to you.

I would argue that not only does the 100% trusted environment not exist but also that most families don't have one computer per family member and have to share the box.

S

---

### Post by aysiu on 2009-07-24
> **Smartin said:**
> aysiu (My dear friend ) ;-)

It would be a real shame if we felt that only *some* people had influence over these things. One of the very great things about OS is The Community. Well, I didn't say we don't have influence. I said we don't have the power to change it. If I had the power to change it, it'd be changed already. I would be Mark Shuttleworth. I would just tell the developers "Let's fix this permissions default. Do it now."

I don't have that power. I do, like you, have influence, however. And the way to use that influence is to promote the Brainstorm idea.

Making an extremely long thread in the Ubuntu Forums is not exercising influence, unless you use that thread to draw more attention to (and presumably votes for) the existing Brainstorm idea.

> If the Ubuntu hierarchy is such that they won't take notice of the community, it will be to their very severe detriment. They notice the community, but you have to go through proper channels--Brainstorm, in this instance. If they see enough Brainstorm votes for an idea, they're more likely to consider implementing it. If they see an extremely long thread in the Ubuntu Forums with most of the posts coming from one person (you), they're less likely to consider implementing it.

> I tried to post a new item in the brainstorming area but it never showed up. It added fuel to my conspiracy theory I'm afraid. Well, bringing drama to the situation does not help your case. There is no conspiracy. You're ascribing far too much importance to this supposed controversy. To the developers, there is no controversy. This isn't even on their radar. They think it's a sane default, and that's it. By voting up the Brainstorm idea, you're more likely to get them to reconsider it. There is no Ubuntu developer who woke up this morning and thought "Ah, how can we thwart Smartin's plans once more today?" 

And, as a Brainstorm moderator myself, I can assure you there is no conspiracy. When you propose an idea, it goes into Sandbox, and then moderators can decide whether it is a valid idea or not. Probably, *since the idea already exists*, another moderator decided it wasn't valid. And, frankly, if I'd gotten to it first, I *also* would have considered it invalid, **since the idea already exists**.

> However... I do think those who are in agreement that a change should be made, should perhaps start a new thread and do a pre-brainstorm as to how the idea should be presented. Then it won't get diluted by loads of other suggestions when it does appear in the brainstorming area. No, if a lot of people are in agreement it should be changed, they should vote up the **already-existing Brainstorm idea**.

---

### Post by izizzle on 2009-07-24
I don't know about the regular Ubuntu 9.04 install, but when I did the minimal install, it asked me if I wanted to encrypt my home directory. But, since I'm the only one that uses my computer, I said No.

---

### Post by heyyy on 2009-07-24
> **izizzle said:**
> I don't know about the regular Ubuntu 9.04 install, but when I did the minimal install, it asked me if I wanted to encrypt my home directory. But, since I'm the only one that uses my computer, I said No.

what do you mean when you say minimal install?
did you install with the alternative cd?

---

### Post by Elfy on 2009-07-24
minimal install is different than the alternate - [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by heyyy on 2009-07-24
> **forestpixie said:**
> minimal install is different than the alternate - [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

on the alternative you still install the whole os right?

---

### Post by Elfy on 2009-07-24
> on the alternative you still install the whole os right?yea you do

---

### Post by Smartin on 2009-07-24
> **aysiu said:**
> 
Making an extremely long thread in the Ubuntu Forums is not exercising influence, unless you use that thread to draw more attention to (and presumably votes for) the existing Brainstorm idea.

That will do for a start...

>  There is no Ubuntu developer who woke up this morning and thought "Ah, how can we thwart Smartin's plans once more today?" 

Are you *sure*...? :wink:

> And, as a Brainstorm moderator myself, I can assure you there is no conspiracy. When you propose an idea, it goes into Sandbox, and then moderators can decide whether it is a valid idea or not. Probably, *since the idea already exists*, another moderator decided it wasn't valid. And, frankly, if I'd gotten to it first, I *also* would have considered it invalid, **since the idea already exists**.

 No, if a lot of people are in agreement it should be changed, they should vote up the **already-existing Brainstorm idea**.

The only problem I have with the existing idea is that it doesn't seem very well presented. I wouldn't be able to do any better but *collectively* I'm sure we could.

I realise that the facility is there to add to the existing idea but that just seems to dilute the point. It gives the developers the 'They don't know what they want. Let's stick to the status quo' get-out.

No?

S

---

### Post by Smartin on 2009-07-24
> **aysiu said:**
> 

 No, if a lot of people are in agreement it should be changed, they should vote up the **already-existing Brainstorm idea**.

aysiu,

What has happened to the existing idea exactly?

[http://brainstorm.ubuntu.com/idea/6106/](http://brainstorm.ubuntu.com/idea/6106/)

 638 people appear to have voted for:

> Solution #1: Auto-generated solution of idea #6106
Written by Eldmannen the 30 Mar 08 at 16:57.
Ubuntu Brainstorm was updated in January 2009. Since the idea #6106 was submitted before this update, its rationale and solution are not separated. Please vote accordingly, and if you have the necessary rights, please separate the rationale from the solution. Thanks!

I don't understand that paragraph.

That's why I thought it was dead and buried...

S

---

### Post by aysiu on 2009-07-24
Right now, with only 600-some net positive votes, it isn't really giving the developers anything at all.

Also, the way Brainstorm is currently set up, there is a general problem, and then you tack on proposed solutions, so you can just add a solution to the problem. I did. So far I've got only one vote for it (mine).

---

### Post by aysiu on 2009-07-24
> **Smartin said:**
> aysiu,

What has happened to the existing idea exactly?

[http://brainstorm.ubuntu.com/idea/6106/](http://brainstorm.ubuntu.com/idea/6106/)

 638 people appear to have voted for:



I don't understand that paragraph.

That's why I thought it was dead and buried...

S Up to a certain point, Brainstorm was just ideas.

Then, after that point, it become problems and proposed solutions.

Since the original idea was presented before the problems/proposed solutions change, the first "proposed solution" is just a place-holder.

So I added a second proposed solution with an actual proposal. And, as I said before, so far it has only one vote.

---

### Post by Smartin on 2009-07-24
> **aysiu said:**
> 

So I added a second proposed solution with an actual proposal. And, as I said before, so far it has only one vote.

Doesn't that justify starting from scratch?

Clear a couple of things up for me:

1) You say in the Brainstorming entry:
> Right now, users have /home/username as 644, so anyone can read files in the directory but not write to files there.
It'd be better if /home/username was 600, restricting both read and write access, and then if another directory like /home/shared were 660 or 666 so users could truly share files they wanted to share (e.g., co-authored documents, music or photo collections).

Forgive my ignorance and the fact that I can't double check right now but aren't the current permissions on the Home folder 744?

*Shouldn't* it be 700? With the Shared folder 660/666? (Did bohdi say it is possible to do this? Can a folder within a folder which is 700 be 660?)

2) How many votes would be required for the developers to take serious notice?

3) How about asking for a 'Drop box'?

S

---

### Post by blur xc on 2009-07-24
> **Smartin said:**
>  In that case you are in (what you believe to be) a 100% trusted environment and this whole thing *happens* not to apply to you.

I would argue that not only does the 100% trusted environment not exist but also that most families don't have one computer per family member and have to share the box.

S

We are discussing default behaviors of different operating systems.  Whether or not the user thinks he's in a 100% trusted environment or not is irrelevant.  When a Joe Schmoe average computer illiterate user buys a windows box and turns it on for the first time, I'm arguing that more often that not, this ends up as the default configuration.  Admin user- no log in password.

You are stating that the default Ubuntu permissions in inferior to this default user model, to such a degree that you think you need to jump ship to another distro.  Ubuntu gives no one full admin privileges.  Gives ownership of files.  Windows does not.  The logic for your reasoning just doesn't click, especially when comparing one default to the other, Ubuntu is clearly superior, and the fix takes less than 10sec if it is such a concern to you.

I don't know mac, if mac is better, then fine.  I come from a windows background, and I don't know anyone (outside of a professional environment) that sets permissions or takes any attempts to secure their computers.

BM

---

### Post by koenn on 2009-07-24
I agree world-readable home directories are not a good idea. 
I agree that it's reasonable to expect sane defaults, and world-readable home directories is not a sane default.

I think this should be considered a security issue. For those who like to make a distinction between privacy and security : one of the 3 main goals of computer security is data **confidentiality**. Ties in pretty closely to privacy, doesn't it ? 

Like one of the commentors on the brainsorm idea said : it's not because I allow a friend or family member to use my computer, that I agree with them being able to go through my personal stuff. 
Not to mention households where the whole family has to share 1 computer, or something like that.


The debian-installer (used on ubuntu's mini and alternate CD) prompts for 'world readable homes or not ?' so it should be pretty easy to change the default to 'no' without too much trouble to the system as a whole.

Apparently the main rationale for the current permissive defaults is to make sharing easy ; however
- there's most likely a number of other ways to accomplish that
- on an operating system with a 'secure by default' reputation, one does not readily expect having to tweak a (too) permissive default, so the 'knowledgeable users will know they have to fix this, and how' argument doesn't hold much water imo. 


-----
Now, how do I get in brain storm - does it require yet another account or will an ubuntuforums or launchpad account do ? 
And what sort of brainstorm permissions does one need to rewrite that rationale , it could use some fixing.

---

### Post by Smartin on 2009-07-24
Forget this one... Blonde moment...

---

### Post by Mornedhel on 2009-07-24
> **Smartin said:**
> aysiu,

I just noticed something...

Correct me if I'm wrong here but if I sort the ideas in the Brainstorm area by 'Most popular ever'

[http://brainstorm.ubuntu.com/most_popular_ever/](http://brainstorm.ubuntu.com/most_popular_ever/)

The most popular idea has 8000 something votes and the second most popular has 39! What's going on? 

You read that wrong.

The most popular idea's most popular solution has 8k+ votes and the most popular idea's second most popular solution has 39.

If you scroll down you'll notice the second most popular idea, with its most popular solution at 7k+ votes.

---

### Post by Smartin on 2009-07-24
> **koenn said:**
> I agree world-readable home directories are a good idea. 
I agree that it's reasonable to expect sane defaults, and world-readable home directories is not a sane default.

Typo there?

> I think this should be considered a security issue. For those who like to make a distinction between privacy and security : one of the 3 main goals of computer security is data **confidentiality**. Ties in pretty closely to privacy, doesn't it ? 

Like one of the commentors on the brainsorm idea said : it's not because I allow a friend or family member to use my computer, that I agree with them being able to go through my personal stuff. 
Not to mention households where the whole family has to share 1 computer, or something like that.


The debian-installer (used on ubuntu's mini and alternate CD) prompts for 'world readable homes or not ?' so it should be pretty easy to change the default to 'no' without too much trouble to the system as a whole.

Apparently the main rationale for the current permissive defaults is to make sharing easy ; however
- there's most likely a number of other ways to accomplish that
- on an operating system with a 'secure by default' reputation, one does not readily expect having to tweak a (too) permissive default, so the 'knowledgeable users will know they have to fix this, and how' argument doesn't hold much water imo. 


-----
Now, how do I get in brain storm - does it require yet another account or will an ubuntuforums or launchpad account do ? 
And what sort of brainstorm permissions does one need to rewrite that rationale , it could use some fixing.

Thanks for your support.

S

---

### Post by koenn on 2009-07-24
> **Smartin said:**
> Typo there?

typo where ?

---

### Post by Smartin on 2009-07-24
> **Mornedhel said:**
> You read that wrong.

The most popular idea's most popular solution has 8k+ votes and the most popular idea's second most popular solution has 39.

If you scroll down you'll notice the second most popular idea, with its most popular solution at 7k+ votes.

Got it! Sorry.

S

---

### Post by Smartin on 2009-07-24
> **koenn said:**
> typo where ?

You said
> I agree world-readable home directories are a good idea.
I agree that it's reasonable to expect sane defaults, and world-readable home directories is not a sane default.

You seem to be saying that world-readable Homes *are* a good idea but they are *not* a sane default. Seems contradictory. Am I misunderstanding?

S

---

### Post by aysiu on 2009-07-24
> **Smartin said:**
> Doesn't that justify starting from scratch? It depends what you mean by "from scratch." If "from scratch" means proposing an entirely new description of the problem, that will probably not make it out of Sandbox. But if "from scratch" means proposing a new third solution in addition to the auto-generated one and my second solution, then go for it. No one's stopping you.

> Clear a couple of things up for me:

1) You say in the Brainstorming entry:


Forgive my ignorance and the fact that I can't double check right now but aren't the current permissions on the Home folder 744?

*Shouldn't* it be 700? With the Shared folder 660/666? (Did bohdi say it is possible to do this? Can a folder within a folder which is 700 be 660?) It doesn't really matter. The 7 means read/write/execute and 6 means read/write. The execute part I left out just for safety reasons (better not to give executable status unless needed on a case-by-case basis).

The main issue is with 6/7 (read-write/read-write-execute) v. 4 (read-only) or 0 (no-access).

And, yes, you can have different permissions on subfolders and files within subfolders. But that's not what I'm proposing. I don't want /home/*username1*/shared and /home/*username2*/shared

I want /home/shared

That one /home/shared directory is used by all users for files they want to share with other users and have other users be able to modify and add to.

/home/*username1* would be accessible only to *username1* by default.

> 2) How many votes would be required for the developers to take serious notice? I don't think there's a set number, but 600 is definitely too low.

> 3) How about asking for a 'Drop box'? It already exists. [DropBox is available for Ubuntu](http://www.getdropbox.com/downloading?os=lnx). And the Ubuntu Developers are working on their own version called [UbuntuOne](https://ubuntuone.com/).

---

### Post by aysiu on 2009-07-24
> **Smartin said:**
> You said


You seem to be saying that world-readable Homes *are* a good idea but they are *not* a sane default. Seems contradictory. Am I misunderstanding?

S
It's possible koenn made a typo, but I don't think it's necessarily contradictory.

I think it's a good idea to change the *sudo* timeout to 0. But I also think it is not a sane default. With a timeout of 0 by default, you're more likely to have people think "Why do I have to enter my password all the time? I just want to log in as root so I don't have to deal with this."

A timeout of 15 minutes is a good default for a balance between security and convenience. Of course, if you're overly paranoid about security, it is a good idea to change the timeout to 0.

---

### Post by Smartin on 2009-07-24
> **aysiu said:**
> It depends what you mean by "from scratch." If "from scratch" means proposing an entirely new description of the problem, that will probably not make it out of Sandbox. But if "from scratch" means proposing a new third solution in addition to the auto-generated one and my second solution, then go for it. No one's stopping you.

Fair enough.

> And, yes, you can have different permissions on subfolders and files within subfolders. But that's not what I'm proposing. I don't want /home/*username1*/shared and /home/*username2*/shared

I want /home/shared

That one /home/shared directory is used by all users for files they want to share with other users and have other users be able to modify and add to.

/home/*username1* would be accessible only to *username1* by default.

I *see*... OSX has *both* a 'global' shared folder and a 'user' shared folder. This seems cool to me. I would actually have a slightly different structure again though:

I would like to see a 'Public' folder which was read/write. Within that, two more folders: 'Published' which is read only and 'Drop Box' which is write only. Cover all the bases :-)

 > I don't think there's a set number, but 600 is definitely too low.

I can see that now. We'd need 5000 minimum probably.

 > It already exists. [DropBox is available for Ubuntu](http://www.getdropbox.com/downloading?os=lnx). And the Ubuntu Developers are working on their own version called [UbuntuOne](https://ubuntuone.com/).

Sorry... I meant a 'write only' folder.

Great news that Ubuntu is creating their own version of the commercial 'Drop Box'. Big selling point. Hope Mark gives the 'Drop Box' guys some Dineros in return for the idea though...

S

---

### Post by Smartin on 2009-07-24
> **aysiu said:**
> It's possible koenn made a typo, but I don't think it's necessarily contradictory.

I think it's a good idea to change the *sudo* timeout to 0. But I also think it is not a sane default. With a timeout of 0 by default, you're more likely to have people think "Why do I have to enter my password all the time? I just want to log in as root so I don't have to deal with this."

A timeout of 15 minutes is a good default for a balance between security and convenience. Of course, if you're overly paranoid about security, it is a good idea to change the timeout to 0.

Fair enough.

S

---

### Post by koenn on 2009-07-24
> **Smartin said:**
> You said


You seem to be saying that world-readable Homes *are* a good idea but they are *not* a sane default. Seems contradictory. Am I misunderstanding?

S
OK, got it. Typo indeed - changed my mind somewhere mid-sentence about how i was going to formulate it, and screwed up.

---

### Post by aysiu on 2009-07-24
> **Smartin said:**
> 
I *see*... OSX has *both* a 'global' shared folder and a 'user' shared folder. This seems cool to me. I would actually have a slightly different structure again though:

I would like to see a 'Public' folder which was read/write. Within that, two more folders: 'Published' which is read only and 'Drop Box' which is write only. Cover all the bases :-) Again, this is one of those "good idea" v. "sane defaults" issues.

In your situation, and maybe in a few other people's situations, having three separate shared folders may be useful, but as a default, it's extremely confusing to new users. I cannot imagine how many "Why do I have three shared folders?" threads would pop up in the Absolute Beginner section if that were the default.

> I can see that now. We'd need 5000 minimum probably. And just remember that that's only to get the developers to consider it. They are a stubborn bunch, and they may just say "Nah, we just want to keep it the way it is."

I've had plenty of my good ideas get shot down (consistency in password entry displayed feedback, consistency between Kubuntu and Ubuntu in number of default panels, auto-prompting for authentication for sudoers when dragging and dropping to system folders, making recovery mode less obvious).

Ultimately, in the world of open source, you can do one or more of the following, and that's it: [list][*]Ask developers nicely to change or fix something and hope they will[*]Fork the project and pay a developer to change or fix something[*]Fork the project and, as a developer yourself, change or fix something without asking others to do it for you[/list] In closed source, you have only the first option and not the other two.

And there are a lot of obstacles (in life in general, not just in Ubuntu development) to good ideas getting implemented. Sometimes it's just a matter of priorities (sounds good in theory, but it's not that urgent... we'll get to it eventually maybe), sometimes it's a matter of difficulty of implementation (sounds good in theory, but we'd have to redo the whole way we approach blah to get that to work, and sometimes it's a matter of politics (if we implemented that, it'd piss of the traditional user base).

---

### Post by blur xc on 2009-07-24
I ran across this thread and it's a good example of what I was saying regarding the default behavior of another OS with "better" default permissions (as proposed by the OP) than Ubuntu-

[http://ubuntuforums.org/showthread.php?p=7673145#post7673145](http://ubuntuforums.org/showthread.php?p=7673145#post7673145)

In a nutshell, a new user to Ubuntu is trying to give his normal user full root privileges, like he's used to having in his old OS.  That imo, is a FAR greater security risk than people having read access to others' home folders.

BM

---

### Post by lswb on 2009-07-24
> **Barna Madau said:**
> I ran across this thread and it's a good example of what I was saying regarding the default behavior of another OS with "better" default permissions (as proposed by the OP) than Ubuntu-

[http://ubuntuforums.org/showthread.php?p=7673145#post7673145](http://ubuntuforums.org/showthread.php?p=7673145#post7673145)

In a nutshell, a new user to Ubuntu is trying to give his normal user full root privileges, like he's used to having in his old OS.  That imo, is a FAR greater security risk than people having read access to others' home folders.

BM

The OP brought up a *privacy* issue, not security. He did not make any suggestion that a normal user should have root priviledges and that thread is really irrelevant to this issue. Actually the OP repeatedly stated that his view *increases* privacy (and perhaps security) I'm not trying to speak for Smartin, but I agree with the view, on this narrow issue of home directory permissions, that the default settings of Windows provide a normal user a greater degree of privacy than do the default settings of ubuntu.

---

### Post by aysiu on 2009-07-24
Yes, let's not derail this discussion. It has nothing to do with wanting to run as root.

---

### Post by Smartin on 2009-07-27
> **aysiu said:**
> Again, this is one of those "good idea" v. "sane defaults" issues.

In your situation, and maybe in a few other people's situations, having three separate shared folders may be useful, but as a default, it's extremely confusing to new users. I cannot imagine how many "Why do I have three shared folders?" threads would pop up in the Absolute Beginner section if that were the default.

Maybe...

> And just remember that that's only to get the developers to consider it. They are a stubborn bunch, and they may just say "Nah, we just want to keep it the way it is."

Hmmm... :-)

> 
And there are a lot of obstacles (in life in general, not just in Ubuntu development) to good ideas getting implemented. Sometimes it's just a matter of priorities (sounds good in theory, but it's not that urgent... we'll get to it eventually maybe), sometimes it's a matter of difficulty of implementation (sounds good in theory, but we'd have to redo the whole way we approach blah to get that to work, and sometimes it's a matter of politics (if we implemented that, it'd piss of the traditional user base).

The issue with the 'Traditional Userbase' is what's making Linux's transition into the mainstream so painful. I was hoping Ubuntu might be the exception to the rule. It *seems* to be doing so much to satisfy the mainstream and on the other hand seems determined to keep things as they always were.

S

---

### Post by Smartin on 2009-07-27
> **bodhi.zazen said:**
> I think the why was already mentioned in this therad :

[https://wiki.ubuntu.com/DebuggingSecurity#Permissive%20Home%20Directory%20Permissions](https://wiki.ubuntu.com/DebuggingSecurity#Permissive%20Home%20Directory%20Permissions)



I have realised why this one has been bugging me...

> 
Permissive Home Directory Permissions

By default, Ubuntu is designed to allow users to easily share files and help each other (see bug 48734). To support this, each user's default home directory is readable by all other users. Private files could be kept in the "Private" sub-directory

(Re-stating) I don't see a 'Private' folder. On the contrary, I have a 'Public' folder.

It is the presence of the 'Public' folder which led me to assume that every other folder was different, ie, non-public. The fact is that all folders are 'Public' so why have a separate folder named 'Public'?

Does anyone have a 'Private' folder?

S

---

### Post by bodhi.zazen on 2009-07-27
> **Smartin said:**
> I have realised why this one has been bugging me...



(Re-stating) I don't see a 'Private' folder. On the contrary, I have a 'Public' folder.

It is the presence of the 'Public' folder which led me to assume that every other folder was different, ie, non-public. The fact is that all folders are 'Public' so why have a separate folder named 'Public'?

Does anyone have a 'Private' folder?

S

Let me know if you need assistance with the detailed advice I gave you on how to effect a change.

If you do not wish to peruse proper channels, well that is the end I guess, the choice is up to you.

> **Smartin said:**
>  The issue with the 'Traditional Userbase' is what's making Linux's transition into the mainstream so painful. I was hoping Ubuntu might be the exception to the rule. It *seems* to be doing so much to satisfy the mainstream and on the other hand seems determined to keep things as they always were.

S

Otherwise, as I have also advised you, please do not insult the developers and the Ubuntu community in general. Such language is arrogant, demanding, and offensive, it really does not add much to further your argument and is off topic at best.

Why do you think if you bully and insult the reasons given by the developers furthers your cause?

You do not have to agree with every decision or opinion of others, but please learn to disagree in a less offensive way, otherwise you come across as simply trolling and not really interested in helping make a true change.

---

### Post by Bios Element on 2009-07-27
I can't be bothered to read this entire thread.

If you want security, Encrypt your home partition. Otherwise get over it. Without encryption it's simply an illusion of security which is just as silly. If you need help with it feel free to PM me. :)

---

### Post by aysiu on 2009-07-27
I agree with bodhi.zazen.

It's perfectly valid to want to change the defaults in Ubuntu, but if you're not willing to go through proper channels, you're hurting your own cause. Continually posting in this thread repetitions of earlier points does not suddenly spring the developers into action.

In fact, if I were a developer reading this thread, I would probably be less inclined to do anything about this.

---

### Post by Macchi on 2009-07-27
Sorry to jump into the middle of this long discussion, but my personal experience is that the majority of multi-user systems on organizations, business enterprises, small offices, etc is would assume the following:

1) A private User Account that is protected by a private password contains private data that is NOT readable by everyone else.

2) A Public folder contains data readable by anyone else in the same organisation or system (but not necessarily readable by the whole world!)

3) A Folder called "Private" or "Encrypted" or "Vault" etc would offer a higher level of security for the data.

This type of expected behaviour should be default for an OS that addresses wider user groups. Deviations from that may generate unnecessary calls to the support desk. Some of these principles could apply for a wide range of systems and users. Despite the fact that extremely confidential content is probably not completely safe in a multi-user environment.

---

### Post by aysiu on 2009-07-27
Macchi, how about voting for the Brainstorm then?
[Idea #6106: Make so other people cant access your home directory](http://brainstorm.ubuntu.com/idea/6106/)

---

### Post by Smartin on 2009-07-27
> **bodhi.zazen said:**
> Let me know if you need assistance with the detailed advice I gave you on how to effect a change.

If you do not wish to peruse proper channels, well that is the end I guess, the choice is up to you.



Otherwise, as I have also advised you, please do not insult the developers and the Ubuntu community in general. Such language is arrogant, demanding, and offensive, it really does not add much to further your argument and is off topic at best.

Why do you think if you bully and insult the reasons given by the developers furthers your cause?

You do not have to agree with every decision or opinion of others, but please learn to disagree in a less offensive way, otherwise you come across as simply trolling and not really interested in helping make a true change.

Whoa... In what way am I being insulting? What language is "arrogant, demanding, and offensive"?

Honestly, I'm not trying to be offensive. Apologies are obviously in order again.

Seriously, let's leave this whole thing. I'm beginning to regret ever mentioning it.

S

---

### Post by aysiu on 2009-07-27
I'm going to close this thread. It seems we're going in circles here.

Some are of the opinion it should be changed and it's urgent. Others are of the opinion it should be changed and it's not that urgent. Still others think it shouldn't be changed at all. Brainstorm ideas and Launchpad blueprints are the way to go if you want to present the idea to developers.

---

