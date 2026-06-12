---
title: "[SOLVED] How to copy configuration from one user to another?"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by jeff_gobel on 2008-09-02
New to Ubuntu and loving it. I'm replacing several windows systems in my home with Ubuntu because I'm tired of spending hours maintaining and tracking down viruses and spyware (mostly on the kids' systems). 

Our computers are used almost exclusively for web access. I have one installation where I have configured the desktop, menus, theme, and panels exactly the way I want (removed almost everything except the browser, added some web links to the top panel, changed fonts, colors, background, etc.). 

How can I recreate the configuration changes on the other systems? 

Can't clone drives because the hardware varies. 

I tried using tar to backup everything in the home directory and restoring that on another system, but failed miserably. 

I did not keep track of all of the changes I made nor how I made them, so recreating them by hand on several systems would be a real pain. Seems if I had done all of the gconf changes from a command line I guess I could have created a script and ran that on the other systems? Would be hard to do now, though.

Any suggestions? 

Thanks much in advance, 

-Jeff

---

### Post by falcon61102 on 2008-09-03
I've got a Ubuntu install on a portable USB drive that I've used on a number of different computer systems with different hardware.  I've had to tweak it here and there for different hardware but it's rather adaptable.  I mention that because it may be a possibility to clone your install and use it on the other systems with minimal work to get everything just right.

EDIT: Nice background btw.

---

### Post by gmoney on 2008-09-03
I think you had the right idea with tar.  Here's a link to a previous post that has a very thorough walk through (howto) on backing up your entire system using tar:

[http://ubuntuforums.org/showthread.php?t=81311](http://ubuntuforums.org/showthread.php?t=81311)

---

### Post by jeff_gobel on 2008-09-03
> **falcon61102 said:**
> I've got a Ubuntu install on a portable USB drive that I've used on a number of different computer systems with different hardware.  I've had to tweak it here and there for different hardware but it's rather adaptable.  I mention that because it may be a possibility to clone your install and use it on the other systems with minimal work to get everything just right.

EDIT: Nice background btw.
Interesting. I never imagined that using the same install across multiple systems would work well, due to differences like amd vs intel, graphics cards, memory size, ide vs. sata, etc. However, the install boot CD seems to work on everything I've tried, so perhaps I should give it a shot. Appreciate the suggestion, thanks.

---

### Post by jeff_gobel on 2008-09-03
> **gmoney said:**
> I think you had the right idea with tar.  Here's a link to a previous post that has a very thorough walk through (howto) on backing up your entire system using tar:

[http://ubuntuforums.org/showthread.php?t=81311](http://ubuntuforums.org/showthread.php?t=81311)
Thanks. I was only tarring the user's home directory, maybe I need to backup the entire system. Will give it a try and see what happens. Appreciate it.

---

### Post by shae on 2008-09-03
Look into a program called remastersys which creates an install disk that has the customizations your computer has.  This however would require reinstalling on your other computers.  Plus this could be reused if you ever had to reinstall for another purpose.

---

### Post by cariboo on 2008-09-03
You should be able to tar up everything in the users home directory, including the hidden files and folders, that may be what your problem was the first time.

Open Nautilus (Places-->Home Folder) press Ctrl-h to reveal the hidden files and folders, select all the hidden files using Ctrl click. Next right click any file that is selected then click create archive.

This will create an archive of all the configuration files in the home directory.

Jim

---

### Post by jeff_gobel on 2008-09-03
> **shae said:**
> Look into a program called remastersys which creates an install disk that has the customizations your computer has.  This however would require reinstalling on your other computers.  Plus this could be reused if you ever had to reinstall for another purpose.
Just got through my first tests with remastersys. Very cool, espeically since I can boot from the CD. All of my customizations where there. Seems to be working, will do more testing. Thanks!

---

### Post by jeff_gobel on 2008-09-03
> **cariboo907 said:**
> You should be able to tar up everything in the users home directory, including the hidden files and folders, that may be what your problem was the first time.

Open Nautilus (Places-->Home Folder) press Ctrl-h to reveal the hidden files and folders, select all the hidden files using Ctrl click. Next right click any file that is selected then click create archive.

This will create an archive of all the configuration files in the home directory.

Jim
Certainly possible that I messed up the tar archive creation the first time. Will try it again as you suggest. I did not know that you could create the archive right from Nautilus; would be easier than the command line. I have much to learn. Thanks.

---

