---
title: "Modifying my files"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by richg on 2008-07-15
Hello All

I have started using Ubuntu 8.04 full time and I am having a problem modifying my personal files I downloaded from an external hard drive. I was saving the files to my external hard drive as Root when I was running Freespire 2.0.8 and I suspect that has something to do with it. Quite a few files are from my 98SE days but I never had any issues before.
How do I make it possible to access and modify All my files, hopefully in one or two key strokes. I am not very good at playing with the operating system software.
Thanks.

Rich

---

### Post by Vivaldi Gloria on 2008-07-15
> **richg said:**
> Hello All

I have started using Ubuntu 8.04 full time and I am having a problem modifying my personal files I downloaded from an external hard drive. I was saving the files to my external hard drive as Root when I was running Freespire 2.0.8 and I suspect that has something to do with it. Quite a few files are from my 98SE days but I never had any issues before.
How do I make it possible to access and modify All my files, hopefully in one or two key strokes. I am not very good at playing with the operating system software.
Thanks.

Rich

Try this. Press ALT+F2 and start

```
gksudo nautilus.
```

This will give you a nautilus window with root rights. You should be able to do whatever you want.

---

### Post by rustyz on 2008-07-15
rich, do you mean files such as photos/docs/music files?

do you see a lock on the file icon if you moved the files to the desktop...

and are permissions access denied?

if so, post back, have a solution!

rz

---

### Post by richg on 2008-07-15
Some JPGs, some DOCs. Just not all.

Rich

---

### Post by rustyz on 2008-07-16
if your files are locked, and you cant change permissions, its a new distros problem...
what has worked for me...

1- take the files and put then in a .tar.gz archive file, then copy and move them...

2- or the long version, do this...

[http://ubuntuforums.org/showpost.php?p=5353553&postcount=25](http://ubuntuforums.org/showpost.php?p=5353553&postcount=25)

---

### Post by Barrucadu on 2008-07-16
Plug the drive in:

```
sudo chmod 777 -R /media/name_of_the_drive
sudo chown your_username:users -R /media/name_of_the_drive
```

---

### Post by richg on 2008-07-16
Thanks for trying all but that is techie stuff. Ubuntu users should not have to do that stuff. Ubuntu is mature enough and should be able to handle files with no ownership issues. My EEE 4g PC with Xandros handles the external files just fine with no ownership issues. I will figure out something easier. I usually do.
You techies forget that running the OS is easy for you. not so for users.

Rich

---

### Post by snowpine on 2008-07-16
> **richg said:**
> Thanks for trying all but that is techie stuff. Ubuntu users should not have to do that stuff. Ubuntu is mature enough and should be able to handle files with no ownership issues. My EEE 4g PC with Xandros handles the external files just fine with no ownership issues. I will figure out something easier. I usually do.
You techies forget that running the OS is easy for you. not so for users.

Rich

Rich, 'gksudo nautilus' is not techie stuff. It's two words. You can do it! :)

I understand your frustration, but remember that there are important security features at work here. Giving the user rights over all files at any time by default is, in my opinion, a dangerous design for an operating system. Using 'gksudo' temporarily makes you the superuser and allows you to do what you want.

---

