---
title: "KeePassX how to reset default (Master Key) password"
date: 2012-11-18
forum: New to Ubuntu
---

### Post by gmaildan on 2012-11-18
Well, i lost the KeePassX default password.

* I don't need to retrieve it *, there were just some pass inside i dont need...

But i can not reset. I Need it working or Ubuntu One and other programs gives an error if i cancel the KeePassX when it prompts me for the default pass.

I tryed sudo apt-get --purge remove keepassx

(the purge should remove all configurations, right? WRONG, it does not. Is this a bug? We uninstall something with --purge remove and it leaves garbage on the system???)

Not even with --purge remove, i install it again and it asks for the same master key default password.

I tryed to google and to look in keepassx homepage and didnt see nothing that helps me.

So PLEASE someone gimme a hand. I can't use ubuntu software central sincronization nor ubuntu one and other stuff gives me error if i cancel the key password window.

---

### Post by drmrgd on 2012-11-18
I might be wrong about this, but I don't think that KeePass is directly linked to Ubuntu One and other applications (at least I've never seen settings like this on my computer).  Is it possible that you're confusing KeePass with the Gnome System Wallet (or whatever it's called these days)?  That's usually linked to things like that (if you choose so that is).  

As I use Kubuntu with a different system, I don't know specifically how to reset.  Found this, though, which seems helpful:

[http://hustatyova.blogspot.com/2012/04/ubuntu-change-reset-keyring-password.html](http://hustatyova.blogspot.com/2012/04/ubuntu-change-reset-keyring-password.html)

EDIT: Also found these which are a little more detailed in case the easy solution above does not work:

[http://askubuntu.com/questions/65281/how-to-recover-reset-forgotten-gnome-keyring-password](http://askubuntu.com/questions/65281/how-to-recover-reset-forgotten-gnome-keyring-password)
[https://help.ubuntu.com/12.04/ubuntu-help/user-forgottenpassword.html](https://help.ubuntu.com/12.04/ubuntu-help/user-forgottenpassword.html) (info at the bottom).

---

### Post by Mr_JMM on 2012-11-18
+1 for thinking you're mistaking the Gnome Keyring password manager.

---

### Post by squakie on 2012-11-18
+1, however I would like to add a little something:  removing a package doesn't do things like remove configuration files that might reside in your home folder.  Use the file manager, go to view and click the view hidden files option, then look for folders that start with ".", or other files that may have been hidden.  Chances are there is either a folder with files or at a minimum a config file hiding in your home folder.  When you purge and re-install it keeps those OLD folders and files.  You may want to try deleting those and then reinstalling.

EDIT:  realized this sounded like you should delete all hidden files and folders, and obviously this is something you should NOT do!  What I meant was to delete any hidden files/folders for keepassx.  Sorry if I was unclear about that! ;)

---

### Post by stinkeye on 2012-11-19
Not clear how your keepassx problem relates to ubuntu one.
But here is how to create a new database in keepassx.   

The first dialogue window is just for loading a database if you have "Remember last open file" in preferences.
These preferences are not removed when purging or reinstalling.
If you press cancel then keepassx will load for creating a new database with a new masterkey.  

[SIZE="3"]**or**[/SIZE]

You could Backup/move your keepassx config folder.
Copy and paste in terminal....
```
mv ~/.config/keepassx ~/.config/keepassx.old
```

Then start keepassx which will no longer show the dialogue to load a database until you create one.

---

### Post by squakie on 2012-11-19
I'm glad you clarified that!  I went back and re-read my post and realized that while what I was thinking was correct, how I worded it made it sound like deleting ALL the hidden files and folders, and obviously that is something NOT to do, so I appreciate you explaining things better than I did.  ;)

---

