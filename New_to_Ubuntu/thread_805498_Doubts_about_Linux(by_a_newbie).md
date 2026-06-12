---
title: "Doubts about Linux(by a newbie)"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by 7raTEYdCql on 2008-05-24
I am at present a newbie to Ubuntu and Linux. So i thought that in order to improve my knowledge i started reading this book.
Wox Publications:"Beginning Unix" by Paul Love, Joe Merlino, Jeremy.C.Reed, Craig Zimmerman,Paul Weinstin

On reading the first few chapters i stumbled upon some doubts and needed some help.
Thought that this is the right place to post them:
Here they are:

1)I didnt understand the concept of users.When there are multiple users using the same machine then is there additional space on the hard disk allocated for them. If not then where is the space occupied by the new users home directory where does it go.
Another thing is that i didnt understand the concept of group.According to me a group is a collection of users.So when i sign into my account at the startup screen suppose i want to sign into my account in a diffent group. How do i do that? I have only one space to type my username and then my password.Or is it that when i login to my account i am automatically logged in to all the groups.

2)Is there any difference in the man and info pages.

3)I typed the who command on my machine and i couldnt understand the output.
This is the Output i got on my machine. What does it mean?(I frankly never understood a word of this.)
```

mehrzad   tty7       2008-06-19  10:38  (:0)
mehrzad   pts/0      2008-06-19  11:08  (:0.0)

```

4)How do i becme the superuse of my comp.I type ```
sudo -i
``` to become the superuser.Or am i supposed to type ```
su
```.

---

### Post by quelx on 2008-05-24
> 1)I didnt understand the concept of users.When there are multiple users using the same machine then is there additional space on the hard disk allocated for them. If not then where is the space occupied by the new users home directory where does it go.
Another thing is that i didnt understand the concept of group.According to me a group is a collection of users.So when i sign into my account at the startup screen suppose i want to sign into my account in a diffent group. How do i do that? I have only one space to type my username and then my password.Or is it that when i login to my account i am automatically logged in to all the groups.



Unless you are using disk quotas all the users share all the space upto the available space on the drive, if one of them gets greedy the rest suffer.

[http://www.debianadmin.com/implement-and-manage-disk-quotas-in-linux.html](http://www.debianadmin.com/implement-and-manage-disk-quotas-in-linux.html)

Groups allow multiple users to have access to a shared resource, for instance the initial user is a member of the **admin** group so you have access to run **sudo** and **gksudo**.  Members of the **video** group can make changes to and read from the video device, **cdrom** can write CD/DVD's using the attached drive.  Take a look at /dev/scd* those nodes are owned by root:cdrom, root is the owner and cdrom is the group, so any user who is a member of cdrom can access that device.  The nice thing about groups is you can be a member of many of them and get their rights at the same time.  From the terminal execute **groups** to see which groups you are member off.  Whatever priveledges those groups have your user also has on that system.  If you create a new user you can grant and limit access based on the groups they belong to.

> 2)Is there any difference in the man and info pages.

don't know the answer to that one.

> mehrzad   tty7       2008-06-19  10:38  (:0)
username |where they are logged in from |date and time they logged in| which display they are using

tt7 is virtual terminal 7 where the gui runs, you have 6 others (just try **CTRL-ALT-F1** and see that there are 6 consoles (**F1-F6** (tt1-6) running.  **ALT-F7** will get you back to the gui.

pts/0 is a virtual console started when you run a console in the gui (gnome-terminal for instance)

> 4)How do i becme the superuse of my comp.I type

You should always **not** need to *become* the superuser, it is a best practice to simply run command with superuser priveledges, just prepend **sudo** to the command you need to run as root

---

### Post by warbread on 2008-05-24
> **i.mehrzad said:**
> 
1)I didnt understand the concept of users.When there are multiple users using the same machine then is there additional space on the hard disk allocated for them. If not then where is the space occupied by the new users home directory where does it go.
Another thing is that i didnt understand the concept of group.According to me a group is a collection of users.So when i sign into my account at the startup screen suppose i want to sign into my account in a diffent group. How do i do that? I have only one space to type my username and then my password.Or is it that when i login to my account i am automatically logged in to all the groups.



Every user on the computer has their own folder in /home.  /home can be where ever you'd like to put it; on the same partition at the root (/) directory, on a different partition, on a different hard drive or even on a USB pen drive.  A directory takes up space if there's information "inside" it.  

Groups are a little out-there for people coming from single user systems.  Users get assigned to groups in order to secure certain files, folders and devices.  By default, the first user on an Ubuntu install has administrator privileges, and so can do anything.  Other users that you add later will just be "users".  They can't open anything that requires one to be an administrator.  For instance, you are a member of the group 'Audio'.  If you were not, you wouldn't be able to use your sound card because it's an audio device.  Your name is also a group, and this allows you to enter your home folder and edit the files in there.  User 'Franklin' cannot enter because he is of the wrong group.  

To clarify this, imagine what a bouncer does at a club.  "Only let in paying customers."  "Give attractive young women more attention."  "Keep the cops busy while I stash this coke."  Instead of pointing to each and every person and deciding what to do, the bouncer is ordered to make a generalization based on properties that place these people within a group.

---

### Post by 3rdalbum on 2008-05-24
2. There is a difference between man pages and info pages. Man pages are just a formatted text file. Info pages are more like a proper manual, with hypertext links between topics. Sometimes, when you try to get an info page, the Info system sees that there is no info page, and just displays the man page.

3. The "who" command lists who is logged into your system. Right now, your user account (mehrzad) is logged in. The date and time are probably when the account logged in. I'm not sure why there are two entries, but it's probably normal.

4. Ubuntu works differently to other distributions. All other distributions use "su" - so you type su to become root, then you can perform commands as root. Ubuntu works through sudo, which elevates you to root for one command only (the one you type on the same line as "sudo").

Typing sudo -i starts a root terminal in Ubuntu.

You might find that some commands work differently on GNU/Linux than in the book, as Linux is not Unix. If you can borrow a book specifically on Ubuntu, you might have an easier time as it will be most likely written for newbies.

---

### Post by 7raTEYdCql on 2008-05-25
I read this somewhere that th "su: command is used to "Switch User", and when the 'user' to be switched to is not specified then the command interprets it as "switch to root".

Although i am not sure i will need confirmation on this.

Thanking you all anyway for your repies.

---

### Post by Bigtime_Scrub on 2008-05-25
> **i.mehrzad said:**
> I read this somewhere that th "su: command is used to "Switch User", and when the 'user' to be switched to is not specified then the command interprets it as "switch to root".

Although i am not sure i will need confirmation on this.

Thanking you all anyway for your repies.

Ive always understood it to be "su = substitute user" or "super user."

From what Ive learned playing with Debian and Fedora, su is an equivalent to sudo -i. I only use sudo -i with Ubuntu when i have lots of different things that need sudo.

---

### Post by perce on 2008-05-25
> **i.mehrzad said:**
> I read this somewhere that th "su: command is used to "Switch User", and when the 'user' to be switched to is not specified then the command interprets it as "switch to root".

Although i am not sure i will need confirmation on this.



yes. If you have user pippo and user pluto in you computer, and pippo types su pluto he is asked for pluto's password, and if he enters it correctly, he becomes pluto.

---

