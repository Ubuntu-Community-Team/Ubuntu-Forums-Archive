---
title: "panel restored  unexpectedly after reboot,need help!"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by problemshere on 2008-05-11
**Enviroment:**
ubuntu 8.04,gnome

**My trouble:**
I placed some application icons on the panel and set my Network Proxy through System--Preference--Network Proxy.After reboot,everything's gone.
No customized icons,No Proxy.
The panel just restore to the origin state of a new installation of ubuntu.

[COLOR="Red"]**The possible reason I think:**[/COLOR]
**This is what I have done before the issue happens:**
I reinstalled ubuntu 8.04 through CD and use command "sudo cp -R" to copy my backuped profile(also 8.04,installed through wubi) to /home.
I think this may cause a owner change of my profile to root.So customization of the panel can't be saved.

I don't think I can simply change the owner of all my profile under /home back to "me",which I'm wondering whether would cause some security issues.
Also,I want to know the configure file related to the panel.


Anyone can offer your help?
Thank you!
[COLOR="Red"][B]
You can find the solution at #6 below.[/B][/COLOR]

---

### Post by ladr0n on 2008-05-11
Yes, that probably is your problem.  Do
```
sudo chown USERNAME:USERNAME /home/USERNAME/*
``` to correct ownership of your home directory.

The permissions for almost every file in your home directory should be 644 (Read-write for you, read only for everyone else).  Do ```
sudo chmod 644 FILEPATH
``` for any files which still give you trouble.


In the future, use the --preserve (or -p) option on cp to preserve ownerships and timestamps.

---

### Post by problemshere on 2008-05-11
Thank you,ladr0n!
But it seems that doesn't work.

Assume my username is "me".
Following your suggestion,I excute:
```
sudo chown me:me /home/me/*
sudo chmod 644 /home/me/*

```

And then I place one icon on the panel.Reboot,the icon is still gone.


> **ladr0n said:**
> Yes, that probably is your problem.  Do
```
sudo chown USERNAME:USERNAME /home/USERNAME/*
``` to correct ownership of your home directory.

The permissions for almost every file in your home directory should be 644 (Read-write for you, read only for everyone else).  Do ```
sudo chmod 644 FILEPATH
``` for any files which still give you trouble.


In the future, use the --preserve (or -p) option on cp to preserve ownerships and timestamps.

---

### Post by sdennie on 2008-05-12
Ladron is correct however, I think the problem is that -R on chown and chmod don't apply to dotfiles.  I think you may have to do the following:

```

cd
sudo chown your_username:your_username `find .`
sudo chmod 0644 `find .`

```

The last line may be optional.

Edit:

And, actually, for good measure, you may want to issue:

```

find .

```

Before you do any of the sudo commands to make sure you think that it's going to do the right thing.

---

### Post by problemshere on 2008-05-12
I think you are right.

I test the code in a temporary folder and it works.The owner of every file and floder including dotfiles and subfiles has been changed.

[COLOR="Red"]**However**[/COLOR],when I do that in my /$HOME directory,it says:
sudo: unable to execute /bin/chown: Argument list too long

I think there are too many files for chown to handle.

---

### Post by sdennie on 2008-05-12
Oh.  That's unfortunate.  This should do the same thing though:

```

find . -exec chown username:username '{}' \;
find . -exec chmod 0644 '{}' \;

```

(I need to brush up on my "find" usage but, I think that's correct).

---

### Post by inportb on 2008-05-12
> **vor said:**
> Ladron is correct however, I think the problem is that -R on chown and chmod don't apply to dotfiles.

You are partially correct. The problem is with the *, which expands to non-dot files. You can test by running "echo *"

So my suggestion is: (and this always works for me)

```
sudo chown -R me:me /home/me
```

Note how I chown -R the whole directory. Unlike *, which is expanded by bash before the command is executed, the -R is handled by chown, which sees dotfiles too.

---

### Post by problemshere on 2008-05-12
> **vor said:**
> Oh.  That's unfortunate.  This should do the same thing though:

```

find . -exec chown username:username '{}' \;
find . -exec chmod 0644 '{}' \;

```

(I need to brush up on my "find" usage but, I think that's correct).


That works.
I think 
```
chmod 644
```
is unnecessary or you should do
```
sudo chmod u+X
```
after that.
If only you could browse your directory(such as your Desktop)

**[COLOR="Blue"]Thank you,vor and ladr0n![/COLOR]**

---

### Post by sdennie on 2008-05-12
That's a good point inportb.  It's the glob that's preventing the dotfiles from being picked up.  I hadn't thought of that.

---

