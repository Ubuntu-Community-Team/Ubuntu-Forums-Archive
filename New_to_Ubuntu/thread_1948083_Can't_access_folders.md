---
title: "Can't access folders"
date: 2012-03-27
forum: New to Ubuntu
---

### Post by shico on 2012-03-27
Hi,
I'm using ubuntu and suddenly the start up takes a few minutes and i cant access the home folder or any other folders,and when i tried to access files from windows i couldn't :S plzzzz help there's a very important file i need :S

---

### Post by loolooyyyy on 2012-03-27
> **shico said:**
> Hi,
I'm using ubuntu and suddenly the start up takes a few minutes and i cant access the home folder or any other folders,and when i tried to access files from windows i couldn't :S plzzzz help there's a very important file i need :S

you should give us more information
did you change permissions of home folder?
and how are you trying to access files from windows? directly? windows can't do that you 
should use something like ext2fs, it will work for now to get your files
when you say you cant access files does that mean you can login?

good luck to you, and don't worry your files are safe :D

---

### Post by d4m1r on 2012-03-27
Windows by default is not able to read EXT3/4 partitions (which linux uses instead of NTFS).

Read about the software needed and download it here:

[http://www.ubuntugeek.com/how-to-read-ext3ext4-linux-partition-from-windows-7.html](http://www.ubuntugeek.com/how-to-read-ext3ext4-linux-partition-from-windows-7.html)

---

### Post by shico on 2012-03-27
I can login and can open any application but i can't open a folder and when i do it just freezes a while and then it does something like refresh and the operation is not completed, and i tried 'explore2fs' to access linux files but something was wrong when i opened the application the box was just blank and i cant find any folder to get the rest of the folders from it.
and whats with the few minutes before the start up of ubuntu its really annoying??
and i was able to find a way to save this file :D fortunately it was in the recent items of the files so i was able to drag it to a flash memory however i wasn't able to open the external drive nor the flash too :S it only worked when i dragged it
i really want to fix it without re-installing the whole system.. i wish this info. could be enough :)

---

### Post by shico on 2012-03-27
> **loolooyyyy said:**
> you should give us more information
did you change permissions of home folder?
and how are you trying to access files from windows? directly? windows can't do that you 
should use something like ext2fs, it will work for now to get your files
when you say you cant access files does that mean you can login?

good luck to you, and don't worry your files are safe :D

I can login and can open any application but i can't open a folder and when i do it just freezes a while and then it does something like refresh and the operation is not completed, and i tried 'explore2fs' to access linux files but something was wrong when i opened the application the box was just blank and i cant find any folder to get the rest of the folders from it.
and whats with the few minutes before the start up of ubuntu its really annoying??
and i was able to find a way to save this file :D fortunately it was in the recent items of the files so i was able to drag it to a flash memory however i wasn't able to open the external drive nor the flash too :S it only worked when i dragged it
i really want to fix it without re-installing the whole system.. i wish this info. could be enough :)

---

### Post by ijumpship on 2012-03-27
Welcome to Linux my friend and Most of all Ubuntu.We are good company.
But as said before, you will always have to be specific when you describe your problem.

Here are some key issues you should consider.
(1) Did you tell the system to encrypt your home folder?
(2) You can only access your folder from windows if you have set up a Samba Shares ([https://help.ubuntu.com/11.04/serverguide/C/samba-fileserver.html](https://help.ubuntu.com/11.04/serverguide/C/samba-fileserver.html))
(3) Linux is quite different from Windows.its focus is security,stability,and reliability.Since Windows Vista,there has been some attempt to reach these features,hence,you will see such things as separate programs and program(X86) folder and Access Controls list(ACL).You need permissions for everything in linux
 Try this  [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
(4) Just try and learn a little,"Windows Made me Feel Dumb"

(5) Just explicitly state what happen,eg. I am Using Ubuntu 11.10,I want to access the Video folder from my windows machine,I am using/not using a dual boot"whichever applies), When I go to either the windows machine/ubuntu this is what happen etc..
Just to say state as much as you can.
I once went to repair a computer,the person who made the call said "I just cannot get on the computer" only to realize,there was no web browser icon on the machine desktop. Today thanks to remote assistance its easier.  

So once again Welcome ,as you go along you will learn how to use logs to solve 75% of your problems.

Good luck and well come aboard after jumping ship

---

### Post by ijumpship on 2012-03-27
Oh.
just use boot cd that you load Ubuntu with ( go to bios and tell the boot sequence to be CD) and as long as you do not have an encrypt home folder you should see the drive and be able  to copy etc.

Make sure your thumb drive  or external drive is in when you are booting

try this beautiful girl's instruction.Although its to remove virus,you will find it helpful to locate your files too.
[http://www.youtube.com/watch?v=9h3q5ss40oY](http://www.youtube.com/watch?v=9h3q5ss40oY)

---

### Post by loolooyyyy on 2012-03-27
***totally irrelevant i guess, i just removed it...

---

### Post by audiomick on 2012-03-27
Schico, I would suggest having a look at the SMART data of your drive. Open the Hard Disk utility and have a look for the "show SMART data" option. The hard drive utility is in System> Administration on 10.04. The cursor is pointing to the SMART data option in my screenshot. It should be in the same place in the English version.

The reason I suggest this is that what you describe sounds like it could possibly be caused by a Hard Drive problem. If this is the case, you should be backing up your stuff as quickly as possible.

---

### Post by ijumpship on 2012-03-27
duplicate post

---

### Post by shico on 2012-03-27
thanks a lot ijumpship and i am really new to linux and its really my first time as well trying to get assistance through the internet.i will try to be more clear and specific, i use ubuntu 11.10 and my other system is windows vista and by the way it sucks and i did not install the ubuntu system but i used the wubi application and -if you must know- my windows was virused and i used the wubi at that time and i never had to login onto windows ever since, and it was working fine until today when something went wrong , and no i didn't use any system to encrypt my home folder but earlier today i used the ubuntu software center and installed something from the nautilus applications as i needed to change some formats to mp3 and then it didn't work so i uninstalled it and then it was fine for a few hours more then the whole system froze so i had to reboot the laptop but at that time the start up was taking too long (approx:3 mins) and then i was able to login as usual and i can access the internet and any other application but i can't access my home folder nor any of my desktop folders and when i try to access one of them it just freezes for a while and then they disappear and then appear again as if it was a refresh.
I'm really sorry if i can't provide more information to make it easier for help but as i told you i'm new and i'm trying to get familiar with it. 
and i'm afraid that the interface i wish to make between linux and windows could not be done because either windows is down or linux has a problem because i tried another program which is diskinternals and both programs i tried did not mention anything about samba shares but i will give it a shot :)
anyway thanks for your help

---

### Post by ijumpship on 2012-03-27
So this is great,have something to work with.

(1) Forget the samba shares discussion,I think you have two option.

Boot with a Ubuntu live CD and traverse your directory you should see your files.

If you get that nasty windows(Windows Vista/Windows 7) virus that is telling you that you have some virus and need to purchase  the antivirus then "Your headaches start".

(2) Remove your computer from the internet download clamav on a seperate machine and try cleaning it.The virus mess up the registry.

I cannot tell you much about removing windows virus.but use the Live CD to back up your files. and then I hope others will tell you how to fixed the MBR,boot sectors etc.

---

