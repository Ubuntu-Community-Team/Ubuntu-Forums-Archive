---
title: "Fresh Desktop on Login"
date: 2013-08-13
forum: New to Ubuntu
---

### Post by Kanefa on 2013-08-13
I am attempted to set up an environment where new user logs into the student account gets a clean account.  My approach has been to write a script that is called at logoff that deletes the dirty /home/student and then copies a clean copy of the student directory that I have set aside for this purpose.  

What I have found though is that this copy takes nearly 3 1/2 minutes. The directory .local is 3.2G and accounts for 99% of the size.  I'm currently not sure how to inspect it (I cannot sudo cd to it).  What exactly is contained in .local and can I treat it as a special case to speed things up?

---

### Post by TheFu on 2013-08-13
Have you considered using hardlinks and softlinks for the read-only parts? Of course, if the student can write to any directory, then they can delete the contents inside (just the file pointer, not the real contents).

Are programs really installed under the individual student's account? Why not globally in /usr/local or /opt?  Then you could just update the $PATH or mkdir ~/bin/ and do softlinks to the real program locations. Much faster.

I'd be surprised if doing this took more than 2 seconds.

---

### Post by Kanefa on 2013-08-13
The read-only files take a less than a second to move, so they are a non-issue.  

I have updated my post (see above).  All applications were installed through the Lubuntu Software Center.  I suspect each application is installed per user in .local.

Could I move .local outside its normal resting spot to a permanent location and create a softlink to its old location? Or does that sound dangerous?

---

### Post by TheFu on 2013-08-13
> **Kanefa said:**
> The read-only files take a less than a second to move, so they are a non-issue.  

I have updated my post (see above).  All applications were installed through the Lubuntu Software Center.  I suspect each application is installed per user in .local.

Could I move .local outside its normal resting spot to a permanent location and create a softlink to its old location? Or does that sound dangerous?

I would be S-H-O-C-K-E-D if any programs were installed under ~/.local/  Those are probably just cache files or local settings. Drop to the CLI and look at the tree. - there is a tools - "**tree**" that is very helpful ... or you can use **find . -type d**, if you prefer.  Settings shouldn't be more than 20M total. Look for image caches, video caches and the trash can used by whatever file manager you've been using. 

My ~/.local/share/Trash had 800MB inside.  Removed and 9.3M is the ~/.local size.  This HOME machine has been upgraded from 6.06 ... over the years top 10.04.  It will get a 12.04 upgrade/migration soon.

~/.local/share$ **du -sh ~/.local/share/***
Will let you see the directory hogs.

---

### Post by Kanefa on 2013-08-13
There are a number of things in .local/share/Trash that could be quite large.  I was able to see it w/ find . -type d.  However, I am unable to change directory to .local, even when I try sudo.  

How would you suggest emptying the trash?  I tried the following and it did nothing.

```
rm -rf ~/.local/share/Trash/files/*
```

---

### Post by TheFu on 2013-08-13
I don't use a GUI much and definitely do not use the standard GUI provided with Ubuntu, so my help won't be any real help to you. Yuck. 

If you can't get inside the directory, it seems you need to learn a little more about file permissions. 
[https://www.linux.com/learn/tutorials/309527-understanding-linux-file-permissions](https://www.linux.com/learn/tutorials/309527-understanding-linux-file-permissions) should help. Checking the **sudo** man page might let you see some options too.  **man sudo** will do that.

If you know that ~/.local/share/Trash/ is full of stuff you don't want, why not delete it?  BTW, do you understand the ~/ and ~user/  usage?  Might want to research that a little too. 

.local/ is relative to whatever the current directory is. That might be the same as ~/.local/ but it might not.

---

### Post by Kanefa on 2013-08-13
I am trying to delete it.  And no i don't know the difference.  That's why I am the "Absolute Beginners Section" and been working on the same problem for over 3 weeks.

---

### Post by TheFu on 2013-08-13
I apologize.  What is the userid for the specific directory you want to delete?

Better idea ... an example:
$ **sudo rm -rf ~student0001/.local/share/Trash/**

Does that make sense? There are lots of subtle things in that command. Highly recommended that you understand each part. Getting this wrong  could be bad.

---

### Post by tgalati4 on 2013-08-13
Why can't you give each student their own account?  That would be much easier than trying to mangle one account each time.  The other method would be to use a "guest" account which should revert to a clean account after each logout.

---

### Post by brabox on 2013-08-13
Doesn't the standard Lubuntu login screen contain a "guest mode" option? It's an account you can log in to giving you non-superuser rights. The user data created by a guest account gets deleted after it logs out.

---

### Post by TheFu on 2013-08-13
> **tgalati4 said:**
> Why can't you give each student their own account?  That would be much easier than trying to mangle one account each time.  The other method would be to use a "guest" account which should revert to a clean account after each logout.

There are many scenarios where a fresh account is desired.  One day training sessions for specific software is just a single example.

---

### Post by Kanefa on 2013-08-14
> **tgalati4 said:**
> Why can't you give each student their own account?  That would be much easier than trying to mangle one account each time.  The other method would be to use a "guest" account which should revert to a clean account after each logout.

There are ten computers and about 200 users.  Classes are taught with the computers and they are also used as a public lab after hours.  I cannot make individual accounts for each user.

The "guest" account is exactly what I need, but they've given you very little control to customize it.

---

