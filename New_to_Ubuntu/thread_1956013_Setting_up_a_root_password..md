---
title: "Setting up a root password."
date: 2012-04-10
forum: New to Ubuntu
---

### Post by openkamen on 2012-04-10
Hi, I am using different Linux distributions for some time.
Lately, I am reading allot about security issues on Ubuntu and user accounts, related to root access.
One thing keeps me confused.
Is it from security perspective necessary to set up a root password? 
On my Ubuntu 11.10 I have one administrators account set up and all other users have normal user accounts. (I did not set up root password)

---

### Post by MG&amp;TL on 2012-04-10
There is a user that is allowed to do anything on a linux distribution, *root*-on Ubuntu, by default you cannot login to root, you use sudo to temporarily access the root user's abilities.

For further information, see [the rootsudo page]("http://help.ubuntu.com/community/RootSudo")

---

### Post by sffvba[e0rt on 2012-04-10
Your admin account is basically your root account - [Some light reading]("https://help.ubuntu.com/community/RootSudo").


404

[SIZE="1"]*edit: Ninja'd :)*[/SIZE]

---

### Post by grahammechanical on 2012-04-10
If you read the link provided by not found, you will see that there are less security issues with Ubuntu than with other Linux distributions.

Setting up a root account opens up security issues. When you log in as root then anyone using your keyboard can do everything that you can do as root.

On Ubuntu even if someone uses my keyboard without my permission they cannot do any administrator tasks because I am basically  working as a standard user. If I need to work as administrator then I am asked to authenticate the task with my password. Once the task is complete I revert back to standard user. Much, much safer.

Regards.

---

### Post by Cheesemill on 2012-04-10
A bit more reading for you:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)
[http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)

---

### Post by anewguy on 2012-04-10
And also important for the person who thinks they'll be the "hero" here:

- it is against forum policies to post anything dealing with enabling the root account.  The post will be deleted and appropriate action taken against the person who posted it.


So......as others have said:

sudo

-or-

gksudo 

gksudo should be used on any edits of files that update any system files of any type.  I'm not hip on all the details, but there is a post in this forum about losing the proper ownership and/or permissions that can cause some processes to fail.

Dave ;)


EDIT:  Sorry cheesemill - I see your links are pointing to the pages explaining what I added.  Didn't mean to double-up.

---

### Post by haqking on 2012-04-10
> **anewguy said:**
> And also important for the person who thinks they'll be the "hero" here:

- it is against forum policies to post anything dealing with enabling the root account.  The post will be deleted and appropriate action taken against the person who posted it.


So......as others have said:

sudo

-or-

gksudo 

**gksudo should be used on any edits of files that update any system files of any type.  I'm not hip on all the details, but there is a post in this forum about losing the proper ownership and/or permissions that can cause some processes to fail**.

Dave ;)


EDIT:  Sorry cheesemill - I see your links are pointing to the pages explaining what I added.  Didn't mean to double-up.

no.

gksudo should be used for graphical apps or for example when using a graphical editor to edit system files such as gedit.

If you are editing system files in a CLI editor such as nano or vi you use sudo not gksudo.

gksudo is for graphical apps 

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)
[https://help.ubuntu.com/community/RootSudo#Graphical_sudo](https://help.ubuntu.com/community/RootSudo#Graphical_sudo)

Cheers

---

### Post by openkamen on 2012-04-10
Thank you for replying to my question. I did read all the sources you have mentioned (some time ago and now again). 
Now I understand much better what you said and what is written in documentation and manuals. 
I am not a native English speaker so it is easier to understand if I read twice. :p

---

### Post by anewguy on 2012-04-11
> **haqking said:**
> no.

gksudo should be used for graphical apps or for example when using a graphical editor to edit system files such as gedit.

If you are editing system files in a CLI editor such as nano or vi you use sudo not gksudo.

gksudo is for graphical apps 

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)
[https://help.ubuntu.com/community/RootSudo#Graphical_sudo](https://help.ubuntu.com/community/RootSudo#Graphical_sudo)

Cheers

Sorry I didn't put graphical in - I know that, was thinking that, obviously didn't type that.  I've always used the "g" to remind me it's for graphical.  Don't know why I didn't type what I was thinking.

---

### Post by haqking on 2012-04-11
> **anewguy said:**
> Sorry I didn't put graphical in - I know that, was thinking that, obviously didn't type that.  I've always used the "g" to remind me it's for graphical.  Don't know why I didn't type what I was thinking.

no worries, happens to me all the time, half the time i may as well type with my toes blindfolded ;-)

Peace

---

### Post by anewguy on 2012-04-11
> **haqking said:**
> .... half the time i may as well type with my toes blindfolded ;-)

I thought I was the only one who did that!  Someday I have to get ambitious enough to pick the keyboard up off the floor. ;)

---

