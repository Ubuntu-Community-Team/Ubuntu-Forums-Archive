---
title: "Why am I denied permission to change files?"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by Oplix on 2008-11-13
I have Ubuntu 8.10 installed and I'm trying to replace the .png file of the little green running man for the log-out.

I have my image ready, I've read the instructions and know that all I have to do are make a backup of the running man, and replace him with an image of the same name. Problem is, I can't rename him to back him up. The option just doesn't light up when I right-click and is unavailable. I also can't delete him, getting a permission denied error. 

When I check the "Permissions" tab in my /usr properties, it says "You are not the owner, so you cannot change these permissions.".

This isn't a shared computer, and mine is the only account on it, so...

1) how do I get to delete and rename these files?
2) how do I get the system to accept my account as the computer's 'owner'?

Figured out how to do it through the terminal myself, but is there any way that I could remove this permission block?

---

### Post by muted1987 on 2008-11-13
press alt+f2 type gksudo nautilus and then change permissions so that your username can change them

---

### Post by jenkinbr on 2008-11-13
> **muted1987 said:**
> press alt+f2 type gksudo nautilus and then change permissions so that your username can change them
Or just do it from the root session of nautilus after typing gksu nautilus.

---

### Post by anotherdisciple on 2008-11-13
> **jenkinbr said:**
> Or just do it from the root session of nautilus after typing gksu nautilus.

I second this... they make system files belong to root for a reason... I'd just change them as root using gksudo.

---

### Post by muted1987 on 2008-11-13
thats actually what i ment but it obviously came out wrong

---

### Post by Bölvaður on 2008-11-13
> **anotherdisciple said:**
> I second this... they make system files belong to root for a reason... I'd just change them as root using gksudo.

I second this.
The reason for only root is able to access this area is that there are programs and settings which you wouldn't want other programs to be able to change them (viruses and other fun stuff).


But you dont have to edit the icons from /usr but from /home/user/.icons , where you do have access.. check that place out instead first. That place is for themes installed by user.

---

### Post by redseventyseven on 2008-11-13
> This isn't a shared computer, and mine is the only account on it, so...

1) how do I get to delete and rename these files?
2) how do I get the system to accept my account as the computer's 'owner'?

Figured out how to do it through the terminal myself, but is there any way that I could remove this permission block?

In a word, no.

Well, more accurately, yes there is, but it's not advised.

This is one of the differences between Linux and Windows - Windows gives users administrative privileges by default. While this may appear to have its advantages, in general, this is considered a Very Bad Idea.

Generally, if you're being given a "Permission Denied" error, it generally means that you're trying to modify a part of the system that affects all users who use it. The /usr folder is an example of this.

For things like icons, you can install them either system-wide (in which case they will go in the /usr/share/icons folder) or just for one user (in which they can be copied to the /home/[username]/.icons folder). Since, as you say, you're the only user, you can install them to your personal space rather than system-wide and it won't make any difference to you.

Separating the system space from your personal settings is one of the reasons why Linux is a more secure system than Windows. In the case of changing icons, it may seem like overkill, but when you consider that the alternative is the ability for programs to be installed willy-nilly without some kind of security check, it's a small price to pay. Besides, for preference-type settings like icons or graphic themes, there's usually a "user-only" equivalent way of doing things which has no danger of harming your system.

Edit: for further information as to why allowing root accounts is a bad idea, see: [http://brainstorm.ubuntu.com/idea/1448/](http://brainstorm.ubuntu.com/idea/1448/)

---

### Post by igknighted on 2008-11-13
Changing the permissions/ownerships of system files can render your system unbootable.  Just use sudo/gksudo when you want to edit them.  Permissions are fundamental to the system, not really something that you can avoid (nor would you want to).

Something like this (a theme) could be in userspace, rather than in a system file.  You could put the icon theme folder in /home/<username>/.icons as mentioned above and have full access to it.  Ubuntu doesn't do this by default because it is designed to be multiuser and for those who do have more than one user it needs to be protected (and available to all users).

---

