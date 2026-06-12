---
title: "[SOLVED] Password Protecting?"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by sonnyrme on 2008-06-10
Hi All. I am new to Ubuntu. I need to find out what I need to do this. Any help will be a Godsend.
Say I have a folder on my desktop made by Tax Cut. I want to save this folder for a while, but do not need prying eyes looking at it. How, or can I, password protect just that folder. I know with WinZip I could compress and password protect it. But I am not real handy with the Linux alternatives. Downright Ignorant to be truthful. Can any one help me with this. I have several different folders with private info  I need to secure.
Thank you for any help you can give on this. :confused:

---

### Post by bluepowder7 on 2008-06-10
the quick-n-dirty solution is to make them hidden folders.  rename and put a dot at the very beginning.  then hit Ctrl-H once or twice to toggle the view and make sure it actually IS hidden.

---

### Post by iaculallad on 2008-06-10
With just the "bare" Ubuntu installation, you cannot password-protect your folders. Create another user profile (for others to use) if you really want your folder to be safe from prying eyes. And just be sure that you own the root password.

---

### Post by sonnyrme on 2008-06-11
bluepowder7. You the man! I like quick & dirty. It works! This is all I need. Thank you so much.
iaculallad, thank you for your help too.
Quick question...how do I mark this as solved?

---

### Post by bluepowder7 on 2008-06-11
Thread Tools up top.

---

### Post by Rhubarb on 2008-06-11
If you're running Ubuntu 8.04, it's possible to encrypt your files using gpg.
Applications --> Accessories --> Passwords and Encryption Keys
Click on New to generate a key of your own (this can take from 5 min to an hour to generate).

Now just right click on a file / folder, then select encrypt.

To decrypt, right click on the encrypted file, then select decrypt.

---

### Post by fenian on 2008-06-11
You can also use file roller to make password protected archives of your sensitive file.To do this open a terminal and enter...

> file-roller

the archive manger window will open.Follow these steps to create password protected archive...

1-Click the new icon in the upper left corner (another window will open)
2-Choose a Name for the zip archive and use the menu to Navigate to where you want to save the archive.
3-From the Archive type menu at the bottom of the window choose zip and then click the new button in the bottom right corner.
4-From the edit menu select password and enter desired password.
5-Click the add files or add folder icon to add files and folders to archive.
6-Your files should now be in password protected zip files.

The problem with simply hiding the folders is that all anyone has to do o see them is press ctrl-h or select show hidden files from the view menu.

---

