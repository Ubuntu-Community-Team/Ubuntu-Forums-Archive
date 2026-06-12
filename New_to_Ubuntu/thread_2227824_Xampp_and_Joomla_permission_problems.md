---
title: "Xampp and Joomla permission problems"
date: 2014-06-04
forum: New to Ubuntu
---

### Post by swipisnt on 2014-06-04
Hello,
I installed xampp and joomla and looks it working but i have 1 big problem. by default xampp folder is /opt/lampp and i think it has root privilegies, so i cant make any changes in joomla because of that. i dont want to mess up with privilegies any more :) so maybe anyone know a good solution for that?

or just somehow need to install xamp to the home directory?

P.S. to install joomla i was using command 
```
sudo nautilus
```
to get in to file browser as root so i can copy joomla files into xampp folder (/opt/lampp/htdocs/)

Thanl You.

---

### Post by swipisnt on 2014-06-05
ok i see there is no help about it :) but i ask this one - how to change permisions to opt/lampp/htdocs folder and all subfolders and files permitions thats allows me freely copy modify move or create new files ? :)

---

### Post by Duncubuntu on 2014-06-05
These two lines should help you, and if you do web development, it might not hurt to read up on how to write your own bash scripts to make this a little more faster, I have a variation on this, I've also written scripts to build basic html templates for me.

```
find /opt/lampp/htdocs -type d -exec chmod 755 {} \;
```

```
find /opt/lampp/htdocs -type f -exec chmod 644 {} \;
```

What this does is it finds all types in the given path, then chmods those types accordingly.

-type 'f' for file, 'd' for directory

In a web dir you typically want 755 on folders, 644 on files with some exceptions.

This should fix your problem.

P.S, with my experience with Joomla, copy/paste is asking for trouble, although it will work most of the time depending on your set up.

Instead go into phpmyadmin, and export your joomla database, install a fresh Joomla in your desired dir, then import the database. Akeeba backup for Joomla can be helpful as well.

---

