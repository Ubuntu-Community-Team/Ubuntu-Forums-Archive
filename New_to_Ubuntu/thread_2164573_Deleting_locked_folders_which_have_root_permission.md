---
title: "Deleting locked folders which have root permission"
date: 2013-08-01
forum: New to Ubuntu
---

### Post by cag337 on 2013-08-01
So I have an SD card that I by mistake wiped, so I used photorec to recover them. I set it up to recover them to my desktop. But then I realized that the folders it created have a lock image on them and the folders cannot be deleted. I am the admin user, but the folders say they belong to root. I know how to log in as root and that sudo before a command in terminal will basically do the same as it would if I was logged in to root. 

The folder names I want to delete are recup_dir.1 and recup_dir.2 both located on the desktop. Anyone know what I should type into terminal to delete them? I know rm is delete/ remove but I don't know what to type after it (which is why I gave file name/ where it is, so you can help). Thanks

---

### Post by kurja on 2013-08-01
Maybe easier to launch your file browser as root, that is, run ```
gksu nautilus
``` and you'll get a file browser window within which you'll have root privileges.

Remember that if you do something else, like create some other files from within that file browser window, they will end up being owned by root again.

---

### Post by cag337 on 2013-08-01
I don't know if it's too early to say this... but... I love you? Root's file system was different and didn't show my files, but I went to file system and did a search for the files I wanted to delete, and bingo! How do I go back to my file system? Just restart/ relog?

---

### Post by kurja on 2013-08-01
You're root only in the window that was opened by "gksu nautilus", just close that window and you're back to your normal environment.

There's no such thing as too much love =)

---

### Post by courseinmiracles2 on 2013-08-03
You should make this as solved...So much love!!

---

### Post by Bucky Ball on 2013-08-03
Please follow the link in my thread to mark this as solved.

@courseinmiracles2: Please make it clear how to mark threads as solved when advising to do this, especially for forum newcomers, as it is not as straightforward as it used to be (IMHO) as it was changed as part of the last forum upgrade. ;)

---

