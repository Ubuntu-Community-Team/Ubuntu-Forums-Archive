---
title: "&quot;Failed To Execute Child Process&quot; Install problems HARDY"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by Sean4000 on 2008-05-15
Hello,

 I have a serious problem. I'm on hardy xubuntu 64. I am trying to install nuke, shake, Maya, pixel, and light zone but I get this message when i click the executables.::


Failed to open "Nuke5.0v1-5748-linux-x86-release-32-installer".
Failed to execute child process "/home/spburns/Desktop/Nuke5.0v1-5748-linux-x86-release-32-installer" (No such file or directory).

The message is the same for the other apps but the names of the aps change obviously.

I am at a loss and very upset because I need these apps up and running asap. 

Any help would be hot.

---

### Post by Xiong Chiamiov on 2008-05-15
How are you running the installers, through the GUI or the terminal?  Do they have permission to execute (properties -> permissions)?

---

### Post by Sean4000 on 2008-05-15
Through the GUI.

This has never been a problem and I suspect a bad update is to blame.

---

### Post by spiderbatdad on 2008-05-15
The 'executables' often need to be made executable. Try this from the terminal: Applications>>Accessories>>Terminal```
cd Nuke5.0v1-5748-linux-x86-release-32
```Or whatever the exact name of that folder is. This assumes the folder is in your /home directory, and not on your Desktop. Next:```
chmod a+x installer.sh
```or whatever is the exact name of the "installer" program inside the folder. Finally:```
./installer.sh
```

---

### Post by Sean4000 on 2008-05-15
This is not working. I am at a loss. I cannot drag the installer to my home folder. 

How do I log in as root? Would that help?

---

### Post by Sean4000 on 2008-05-15
As i extract the file it makes a folder icon that immediately turns into a square install icon with a wrench and sprocket picture on it.

---

### Post by Sean4000 on 2008-05-15
Thsi is kind of important. Bump.

---

### Post by spiderbatdad on 2008-05-15
Looks like a game? If it didn't cost $80.00 to join I would download it and try to run it on my installation.

---

### Post by Sean4000 on 2008-05-15
????? lol. Everything okay over there man?

---

### Post by spiderbatdad on 2008-05-15
Well...I went to try to get the program and give it a try to see what the problem was, but membership was required. It looked like the membership was $80.00. If I'm wrong let me know and I'll fetch the prog. to see if I can run it.

---

### Post by Sean4000 on 2008-05-15
Nuke:

[http://www.thefoundry.co.uk/pkg_downloads.aspx?ui=CBC2593A-2C9F-4EF9-84BE-C198B0171453](http://www.thefoundry.co.uk/pkg_downloads.aspx?ui=CBC2593A-2C9F-4EF9-84BE-C198B0171453)

---

### Post by spiderbatdad on 2008-05-15
K. downloaded the tar and extracted it on my desktop. Opened a terminal:
```
cd Desktop
sudo ./Nuke(hit the tab key to auto complete the file name.)
```
Installer ran and installed the program. Looks like a really cool app, unfortunately requires a product code which must be purchased or obtained by means not readily apparent to me.

---

### Post by Sean4000 on 2008-05-15
I got this when I ran the terminal:

spburns@spburns-desktop:~/Desktop$ sudo ./Nuke5.0v1-5748-linux-x86-release-32-installer 
sudo: unable to execute ./Nuke5.0v1-5748-linux-x86-release-32-installer: No such file or directory
spburns@spburns-desktop:~/Desktop$ 


Thank you for your help. I hope I can get this sorted out and get this running.

---

### Post by spiderbatdad on 2008-05-15
Is that installer file on your desktop?

---

### Post by Sean4000 on 2008-05-15
Yes it is.

---

### Post by spiderbatdad on 2008-05-15
ok. From the link you provided. I did not take the tar package shown. Instead, filled out the registration and returned with login information, then saved the tarball to my Desktop. Right clicked on package and selected 'extract here.' Then opened the terminal and cd'd into the Desktop, the launched the app with sudo ./Nuke.....

---

### Post by Sean4000 on 2008-05-15
I redownloaded it, extracted right to the desktop, cd Desktop, sudo ./Nuke etc, and still no.  This is a messed up monster.

And Nuke is an amazing piece of visual effects software.

spburns@spburns-desktop:~$ cd Desktop
spburns@spburns-desktop:~/Desktop$ sudo ./Nuke5.0v1-5748-linux-x86-release-32-installer 
sudo: unable to execute ./Nuke5.0v1-5748-linux-x86-release-32-installer: No such file or directory
spburns@spburns-desktop:~/Desktop$

---

### Post by spiderbatdad on 2008-05-15
I can't imagine why bash says the file doesn't exist. Does this user account have admin privileges under System>>Administration>>Users & Groups>>click user name>>User Privileges. Or run: ```
groups spburns
```and look for 'admin.'

---

### Post by Sean4000 on 2008-05-15
spburns@spburns-desktop:~$ groups spburns
spburns adm dialout cdrom floppy audio dip video plugdev fuse lpadmin admin
spburns@spburns-desktop:~$

---

### Post by spiderbatdad on 2008-05-15
try this:```
cd Desktop
sudo -s
./Nuke...
```

---

### Post by Sean4000 on 2008-05-15
spburns@spburns-desktop:~$ cd Desktop
spburns@spburns-desktop:~/Desktop$ sudo -s 
root@spburns-desktop:~/Desktop# ./Nuke5.0v1-5748-linux-x86-release-32-installer 
bash: ./Nuke5.0v1-5748-linux-x86-release-32-installer: No such file or directory
root@spburns-desktop:~/Desktop#

---

### Post by spiderbatdad on 2008-05-15
```
cd Desktop
ls -l
```

---

### Post by Sean4000 on 2008-05-15
spburns@spburns-desktop:~$ cd Desktop
spburns@spburns-desktop:~/Desktop$ ls -l
total 162636
-rw-r--r-- 1 spburns spburns    61381 2008-05-15 19:53 Lumiere_FeedingTheBaby_2.jpg
-rwxr-xr-x 1 spburns spburns 84196087 2008-02-21 06:32 Nuke5.0v1-5748-linux-x86-release-32-installer
-rw-r--r-- 1 spburns spburns 82069683 2008-05-15 14:41 Nuke5.0v1-linux-x86-release-32.tgz
-rw-r--r-- 1 spburns spburns    25447 2008-05-15 19:57 tux_baby.png

---

### Post by Sean4000 on 2008-05-15
Whatever this is..it is on my laptop. And that's an older install.

---

### Post by Sean4000 on 2008-05-15
where is the ubuntu irc sign up page?

---

### Post by Sean4000 on 2008-05-18
I'll be on later tonight!

---

### Post by convocator on 2008-06-14
Sean, did you ever get this to work? I'm having the same issue as you.

---

### Post by Sean4000 on 2008-06-14
This is going to sound odd but all I did was change my mouse and the problem went away. I ma not lying. I had an MS laser mouse and swapping it out for a logitech solved the issue.

I will be shocked if this is the same issue with your computer.

---

