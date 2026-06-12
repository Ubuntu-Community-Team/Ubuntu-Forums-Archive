---
title: "Can't see Shared Folder for File"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by arnold.pietersen on 2008-06-09
I have a file on a shared folder on WinXP. However, I wanted to attached a file and is not able to access it since there is no option to access the shared folder.  The only options I get are:

arnold
Desktop
File System

How do I access the file on the shared folder?

Any ideas?

---

### Post by burakerenn on 2008-06-09
Well I did not get the point clearly but if you're trying to see your shared folder on a windows machine you should use samba.

Try smb://ipAddressOfWindowsMachine/ in Location box on file browser.

---

### Post by Titan8990 on 2008-06-09
You will need to install SAMBA in order access shared Windows files. You can install SAMBA by typing the following into the terminal:

#sudo apt-get install samba


Here is a link to the official SAMBA documentation: [http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/](http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/)

---

### Post by arnold.pietersen on 2008-06-10
Dear Burakerenn and Titan8990

I can see the folder on the Win XP computer.  I am able to copy and move files between my laptop (Feisty) and the Win XP machine. 

However, when I am on my laptop and I want to send an attachment which is located on the Win XP machine I am not able to access the file from within the dialog box on my laptop.

For example in Win XP you would have an option: *Look In* in a dialog box and you would be able to navigate your way to a file you want.

I hope this explains it.

---

### Post by jonandrews on 2008-06-10
I've put an illustrated guide to integrating Ubuntu PC's into a Windows home network onto a website:

[www.europe.eclipse.co.uk/Ubuntu/](www.europe.eclipse.co.uk/Ubuntu/)


This may be helpful to you problem.

---

### Post by arnold.pietersen on 2008-06-10
Dear Jonandrews

I have seen the notes you have compiled.  It looks good, but does not solve my problem.  I can see/use/modify the information on the Win XP machine and can copy/move information between the laptop and the Win XP. No problem.

However, I am using my laptop (Feisty) to send an e-mail, but the file I want to attach is on the Win XP machine. Now I would click on the Attach option on the laptop.  There is nothing that will lead me to the file on the Win XP machine.  The only options appearing would be:
- arnold
- Desktop
- File System
Nothing that will allow me to get the file from the Win XP machine using the Attach dialog box.

The one way of doing it would be to copy the file from the Win XP machine onto the Desktop of the laptop and then attached it in the e-mail. Or if the file is on the USB stick, then the USB stick will appear under Places and one would be able to get the file.
 
Thanks for any help

---

### Post by burakerenn on 2008-06-10
Well I got what you mean and tried in evolution but strangely it's not working. It's probably a bug in open file menu. I tried in some other programs and none of them allow you select network or write smb://ip.

---

### Post by mgmiller on 2008-06-10
What you need to do is on the ubuntu machine, click Places > Network.  You will see your local network.  Click on the XP machine to bring up a window with all the shared files on it.  Navigate to the folder that contains the file you want to attach.  At the top of the window, click Bookmarks > Add Bookmark.

Now you will have a link to that spot in "Places" on your top panel.  If you have more than a few of these, a secondary list will open Places > Bookmarks > [your bookmarks listed here].

That being done, close and reopen Evolution.  Now when you click on file attachment, you should see the bookmark you just created in the column list on the left side.  Navigate to what you want to attach from there and you should be good to go.

---

