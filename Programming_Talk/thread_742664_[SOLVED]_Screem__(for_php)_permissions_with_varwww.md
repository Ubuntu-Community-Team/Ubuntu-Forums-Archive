---
title: "[SOLVED] Screem  (for php) permissions with /var/www"
date: 2008-04-01
forum: Programming Talk
---

### Post by Griff on 2008-04-01
I need to do a lot of php work with screem and will need to be in /var/www.  Is it bad form to open screem as root so I don't have to sudo cp files there?  I am definitely not willing to change the permissions here to allow read/write access by anything.  What do most of you webpage people deal with your access problems?

Thanks,
Griff

---

### Post by kknd on 2008-04-01
> **Griff said:**
> I need to do a lot of php work with screem and will need to be in /var/www.  Is it bad form to open screem as root so I don't have to sudo cp files there?  I am definitely not willing to change the permissions here to allow read/write access by anything.  What do most of you webpage people deal with your access problems?

Thanks,
Griff

Create another folder on your home, and do a symbolic link of it to /var/www

Example:

mkdir /home/user/mywww
sudo ln -s  /home/user/mywww /var/www

---

### Post by mssever on 2008-04-01
> **Griff said:**
> I need to do a lot of php work with screem and will need to be in /var/www.  Is it bad form to open screem as root so I don't have to sudo cp files there?  I am definitely not willing to change the permissions here to allow read/write access by anything.  What do most of you webpage people deal with your access problems?Running as root is a bad idea if it can be avoided. And running screem as root can always be avoided (actually, running screem can always be avoided :)).

I do two things: First, I've changed my DocumentRoot to /home/myuser/webmaster, which is more convenient for me. You can set it to anything you like as long as the user www-data can read it (and execute it, if appropriate). Second, I've chown'd everything in my DocumentRoot to my user (in other words, my normal username owns all the files). That way, I don't have to jump through hoops to edit my files. And there are no security risks by doing this.

---

### Post by Griff on 2008-04-02
Thanks for the quick responses.  I had decided that running screem as root would be a bad idea.  In the interim I had made a little bash script that copied the files I was working on to /var/www.  I'm going to try what you've suggested now.
Thanks!
Griff

---

