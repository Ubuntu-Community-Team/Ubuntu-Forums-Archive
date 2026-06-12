---
title: "Terminal command instead of using gksudo nautilus for permissions"
date: 2015-09-15
forum: New to Ubuntu
---

### Post by OBJ on 2015-09-15
Hello, I have been using Ubuntu for almost a year now and took some getting used to, but getting around OK. Just had a question regarding drive/folder/file permissions and setting them.

I usually copy files from an external drive and once they are on the target drive, I just type in Terminal "gksudo nautilus" and get a nice little GUI as sudo to make any changes to the drive.

Once that command pops open a windows I just right click on the drive with the newly copied files,Go to Properties>Permissions>Change Permissions for Enclosed Files...
and the click on Change and my media server can then recognize the newly added media copied to it. Nothing else is changed from the drop down boxes..just going through those steps without changing anything does it.

So I have a way of doing things that works by following the above, but would like to learn Terminal better. What steps in Terminal would I use to accomplish the same as using the GUI above? Thank you for your help.

BTW Current Permissions according to the GUI of the target drive:

Owner: Me
Access: Create and delete files
Group: myusername 
Access: Access files 
Others
Access: Access Files

and in the Change Permissions for enclosed Files area:
Owner: Files>Read and Write   Folders>Create and delete files
Group: Files>Read and Write   Folders>Create and delete files
Others: Files>Read Only  Folders>Access files

---

### Post by Lars Noodén on 2015-09-15
It would be the [chmod](http://manpages.ubuntu.com/manpages/trusty/en/man1/chmod.1.html) utility.  The [file permissions](https://help.ubuntu.com/community/FilePermissions) can be expressed as octal numbers or the letters rwx for each of ugo.  See the tutorial link there.  The manual page is worth checking too.

```

man chmod

```

For each program there is a corresponding manual page and over time they start to make sense.  So they are worth checking, but they do vary greatly in quality in Ubuntu and the other Linux distros.  Other OSes like OpenBSD take documentation flaws as seriously as any other bug, so they have on average much better manual pages.   However, they are  always the place to check for authoritative information on what the program does and how it can be made to do it.

You'll definitely find using the terminal to be useful and eventually it will be easy.  At that point you can even start automating things with scripts.  Anything you type in the terminal can be put into a script and done again.  Also, the terminal is not fussy about whether you are sitting at the keyboard of the very same machine or logged in from somewhere else on the other side of the planet, so it is the best way to manage servers and larger numbers of other computers.

Have fun.

---

### Post by DuckHook on 2015-09-15
If I may make a suggestion that could save you some grief?

It seems like you have reached the point in your self-education where you are starting the process of delving into the "guts" of Linux&#8213;the terminal commands. If so, then I would strongly suggest that you set up a Virtual Machine, install a command line version of Linux in the VM and do all of your terminal explorations in that safe little sandbox. That way, you will not compromise your production box when you make mistakes. VMs have the added virtue of allowing you to make "snapshots", so that you can roll back your virtual OS to a previous state whenever you render it unusable (borking your OS is common when first starting out on the command line).

If you are not using your production machine to explore, then there is less danger, and indeed, there is something to be said for learning by breaking and fixing.

Just an option you might like.

---

