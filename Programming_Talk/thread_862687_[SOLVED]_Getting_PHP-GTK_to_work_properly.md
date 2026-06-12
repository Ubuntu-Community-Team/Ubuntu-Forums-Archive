---
title: "[SOLVED] Getting PHP-GTK to work properly"
date: 2008-07-17
forum: Programming Talk
---

### Post by King_Killa on 2008-07-17
Hello, I'm very new to linux, and I was wondering if maybe I'm doing something wrong here.

I installed php5, and then installed all of the files needed for php-gtk, the terminal stated that it was installed correctly. I also updated my php.ini file to add the extension.

The only problem is when I try to run the php-gtk demos, nothing happens.

These are the steps I used to install php-gtk:

```

sudo apt-get update 
sudo apt-get install php5-cli php5-dev php5-gd libgtk2.0-dev libglade2-dev 
sudo apt-get install build-essential 
sudo apt-get install cvs  
cvs -d :pserver:cvsread@cvs.php.net:/repository login 
cvs -d :pserver:cvsread@cvs.php.net:/repository co php-gtk 
cd /home/brandon/php-gtk 
./buildconf
./configure
make
sudo make install 

```

When I was done, I ran "php -m | grep php-gtk " to test the installation, and it returned "php-gtk".. but alas, no result from running the demo .php files.

I apologize if this has been resolved in another thread, I searched the forums but couldn't come up with anything that solved the issue.

---

### Post by King_Killa on 2008-07-18
I'm completely retarded. I was trying to simply run the script straight from the directory as an executable. It works fine when opened through the terminal.

---

