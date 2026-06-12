---
title: "[pc] no work in terminal as command"
date: 2013-03-20
forum: New to Ubuntu
---

### Post by auspot on 2013-03-20
this is part of what I was trying to do:  sudo cp -r $home  [problem is I know very little aboutr ubuntu]
thank you for any help

auspot

---

### Post by engineerarun on 2013-03-20
If your intention is to copy your home directory you should provide a destination where to copy the files. You should run -
sudo cp -r $HOME destination_directory

For any command, you can see the usage from the manpages. To do that, run
man command
For example: man cp

Arun
[http://oldpapyrus.wordpress.com/](http://oldpapyrus.wordpress.com/)

---

### Post by auspot on 2013-03-20
> **auspot said:**
> this is part of what I was trying to do:  sudo cp -r $home  [problem is I know very little aboutr ubuntu]
thank you for any help

auspot

this is what is happening when I try to use the cp

bill@bill-ET1831:~$ sudo cp-r $home/desktop/SlicknesS-black/usr/share/themes
[sudo] password for bill: 
sudo: cp-r: command not found
bill@bill-ET1831:~$

---

### Post by ManamiVixen on 2013-03-20
There has to be spaces in there seperating the two locations. :)
So it's actually "sudo cp -r /desktop/SlicknesS-black /usr/share/themes" $home isn't needed.

---

### Post by JKyleOKC on 2013-03-21
> **ManamiVixen said:**
> There has to be spaces in there seperating the two locations. :)
So it's actually "sudo cp -r [COLOR="#FF0000"]/[/COLOR]desktop/SlicknesS-black /usr/share/themes" $home isn't needed.That slash in front of "desktop" is an error unless you've created a non-standard directory tree. The usual desktop location is within $HOME (aka ~) and the directory name is capitalized, so it should be "~/Desktop/SlicknesS-black" or alternatively "Desktop/SlicknesS-black" if you have a standard system and are working in your home directory...

---

### Post by auspot on 2013-03-21
sudo cp-r $home/desktop/SlicknesS-black/usr/share/themes
sudo chmod 755 /usr/share/themes/SlicknesS-black/SslicknesS-black.jpg

This is what I was trying to do.  Copy from you tube video

Thanks for the info but nothing has worked so far.

my system does not reconize the cp command.  Is there a way to get system to work with the 
cp commnad?

auspot

---

### Post by auspot on 2013-03-21
os is ubuntu 12.04

---

### Post by ManamiVixen on 2013-03-21
sudo (SPACE) cp (SPACE) -r (SPACE) /home/(your user name)/Desktop/SlicknesS-black (SPACE) /usr/share/themes
sudo (SPACE) chmod (SPACE) 755 (SPACE) /usr/share/themes/SlicknesS-black/SslicknesS-black.jpg

---

### Post by auspot on 2013-03-29
Thanks for all the info.
I was copying from a video on youtube for the 4 or 5 things you want to do when you install ubuntu 12.04
I did not have any problems downloading 12.04 and copying to a disc and then loading to computer, worked fine.

Thanks
auspot

---

