---
title: "[SOLVED] omnipotence"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by Zopiac on 2008-05-10
how do i get the ability to do whatever i want, say, edit files in the /usr directories and such, without even needing to enter a password every time?

---

### Post by markbusu on 2008-05-10
You will need to enable the root user to do this, since by default the root user is disabled in Ubuntu (or rather, doesn't have a password assigned)...

Have a look at the following... explains how to do this:

[http://www.debianadmin.com/enable-and-disable-ubuntu-root-password.html](http://www.debianadmin.com/enable-and-disable-ubuntu-root-password.html)

---

### Post by Kingsley on 2008-05-10
This should have the information you need.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by nynoah on 2008-05-10
If I were, I would not change anything.  Part of the Ubuntu Linux security is that you HAVE to use your password to modify certain directories.  It is the directories that are password protected that contain all your architectural files and such.  If there was no password you would then have no protection from malicious things.  You would be back to a windows world of "Every one and every program" being able to modify your computer.

---

### Post by markbusu on 2008-05-11
I would have to debate on that last comment... You have to take into consideration which system you would like to enable to Root User...

Therefore is it you machine at home... or your office Laptop...

I personally enabled the Root user on my Desktop machine at home... but not on my laptop...

However... this is just my opinion :P

---

### Post by nynoah on 2008-05-11
well it depends on whether he is the only person who touches his computer.  having to enter your password to change program directories is part of the security of Ubuntu Linux.  Take that away and you have stripped away another protection layer.  Its also a reminder to you that you are messing with a program directory, so be careful what you do.

---

### Post by ad_267 on 2008-05-11
You can use sudo -i to get a root terminal so you don't have to sudo every command. It can also be useful to create a launcher to run gksu nautilus.

---

### Post by nynoah on 2008-05-11
> **ad_267 said:**
> You can use sudo -i to get a root terminal so you don't have to sudo every command. It can also be useful to create a launcher to run gksu nautilus.

That is what I have on my computer.  I created a launcher for "gksudo nautilus"  After you launch that, everything that you do will be in sudo form.  If you don't want to create a launcher, just Alt-F2 and type Gksudo nautilus every time.  Its better to do that than take away your password protections.

---

### Post by Zopiac on 2008-05-11
well, really, all i want to do currently is to edit an icon for sauerbraten and nexuiz, which awn always shows, even though i pick another :/ but i can't edit them because they are in a /usr directory. however, i may want to access things later, too.

---

### Post by SunnyRabbiera on 2008-05-11
what you ask is not impossible, but it is unwise.
Remember the main reasons why windows has so many issues is because it enables root access by default.
I know entering the password all the time can be annoying, but believe me its for the better.

---

### Post by Zopiac on 2008-05-11
> **SunnyRabbiera said:**
> what you ask is not impossible, but it is unwise.
Remember the main reasons why windows has so many issues is because it enables root access by default.
I know entering the password all the time can be annoying, but believe me its for the better.

the thing is, it doesnt even ask for a password it just said that i am not allowed to do it.

---

### Post by SunnyRabbiera on 2008-05-11
> **Zopiac said:**
> the thing is, it doesnt even ask for a password it just said that i am not allowed to do it.

well you see if you are going to edit core files you have to do it in the terminal with sudo...
Like I said I understand that this is annoying from a windows user perspective but its better for you in the end.

---

### Post by nynoah on 2008-05-11
If you want to edit something like what you are trying to do, be careful.  Use sudo sparingly.

hit - alt-f2
then type - gksudo nautilus

This will open nautilus up as a super user.  You edit anything, but you can also edit your computer to oblivion if you do the wrong thing.  Just change the Icon that you want to change and get out of sudo nautilus.

---

### Post by atomkarinca on 2008-05-11
> **Zopiac said:**
> well, really, all i want to do currently is to edit an icon for sauerbraten and nexuiz, which awn always shows, even though i pick another :/ but i can't edit them because they are in a /usr directory. however, i may want to access things later, too.

Hit alt+f2 and type 

```
gksudo nautilus
```

You'll get a file browser with root previliges, you will be able to edit anything you open through this browser.

EDIT: beat me to it.

---

### Post by oldos2er on 2008-05-11
> **Zopiac said:**
> the thing is, it doesnt even ask for a password it just said that i am not allowed to do it.

 That is "working as designed." You need to use sudo or gksudo, then the system will ask for your password.

---

### Post by Zopiac on 2008-05-11
> **nynoah said:**
> If you want to edit something like what you are trying to do, be careful.  Use sudo sparingly.

hit - alt-f2
then type - gksudo nautilus

This will open nautilus up as a super user.  You edit anything, but you can also edit your computer to oblivion if you do the wrong thing.  Just change the Icon that you want to change and get out of sudo nautilus.

thanks a ton!

---

### Post by nowshining on 2008-05-11
actually u could of copied the icon and or icons files to ur desktop - make sure the permissions allow u to edit the file, do ur work there and then copy them back into the directory u need.

However make a copy of those copies incase something goes wrong and u want to convert back to the original files/icons.

---

