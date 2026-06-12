---
title: "Installed Kubuntu-desktop: password works for login but not for sudo"
date: 2015-04-10
forum: New to Ubuntu
---

### Post by samuel_bird on 2015-04-10
I had unity desktop before and installed kubuntu-desktop. It worked in that I could log in to kubuntu, yet my password is rejected if I try to use sudo. I went back into unity and it still works there fine. Why is this? is there an easy fix?

Thanks in advance.

---

### Post by dino99 on 2015-04-10
still buggy kubuntu i suppose (you're not alone with that issue)

---

### Post by Geoffrey_Arndt on 2015-04-10
Did you actually install "Kubuntu" OR just installed the KDE desktop to run alongside Ubuntu Unity?  The **_best way to run KDE_** (by far imho) is to set up a partition for it, and then to install the full "distribution" versus just installing the desktop.   Nevertheless, your original "first user" password should also work for for all desktop (DE's) you have installed.

Did you have a look at the User settings in KDE, and see if your user ID is set up properly.   If you are using the same login name (user ID), is it listed in the "sudoer" group? (if not, add it there)).

PS 9d9 . . . for many users Kubuntu is very stable (and has been for years).   ALthough I like unity better, KDE is a remarkably good desktop.

---

### Post by samuel_bird on 2015-04-10
> **Geoffrey_Arndt said:**
> Did you actually install "Kubuntu" OR just installed the KDE desktop to run alongside Ubuntu Unity?  The **_best way to run KDE_** (by far imho) is to set up a partition for it, and then to install the full "distribution" versus just installing the desktop.   Nevertheless, your original "first user" password should also work for for all desktop (DE's) you have installed.

Did you have a look at the User settings in KDE, and see if your user ID is set up properly.   If you are using the same login name (user ID), is it listed in the "sudoer" group? (if not, add it there)).

PS 9d9 . . . for many users Kubuntu is very stable (and has been for years).   ALthough I like unity better, KDE is a remarkably good desktop.

How do I view the sudoers list in KDE if I cannot use sudo? 

How do I know if it is setup properly? I had a look at the user management utility and the password section is blank for my user. I tried to add one but you need sudo.

I am sorry if this is very naive.

EDIT: 

In response to your first question, I installed the kubuntu-desktop which I suppose is just KDE-desktop. Saying that, kubuntu logo appears when I boot up now - I dont mind but why is this?

---

### Post by samuel_bird on 2015-04-10
I had a look at the sudoers file back in unity and there are no specific users listed there. Is that a problem?

Update: I tried adding the line ```
 samuel ALL=(ALL)ALL 
``` to the sudoers file and restarting but that made no difference.

Update 2: I ran the command 'groups' in kde and it says I am sudo and admin.

FIXED: This is embarassing - the keyboard was set to US instead of UK, which I needed. Thanks for the help anyway.

---

