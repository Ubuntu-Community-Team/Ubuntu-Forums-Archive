---
title: "screen gray, no controls, desktop files showing.  Now login does not work"
date: 2015-05-09
forum: New to Ubuntu
---

### Post by milanandme on 2015-05-09
I came to the computer one day and saw that the whole screen was greyed.  I had not done anything to the computer before this except the usual browsing and email.  This  was not just one window, as sometimes happens when the processor is busy  or something else is keeping the program from working.  Nothing  worked.  So, I pushed and held the power key until it turned off.  When  it turned back on I got the desktop background and file icons on the  desktop.  However there were no control icons around the edges of the  screen.  Hmm.  So, how and I supposed to do anything, I thought.  So, I  went to another computer and started searching for topics concerning my  problem.  I learned a lot about keyboard commands.  I found one article  that talked about what to do when Ubuntu freezes.  It started with  instructions for when a window freezes and then went on to the mouse  (which was not my problem), then when nothing seems to work but a  terminal is available.  Well, I could not get a terminal either, in the  usual way (Alt-Ctl T).  However they gave me an alternate to Alt-Ctl T  which was Alt-Ctl F2.  That did not work.  Then they mentioned Alt-Ctl  F1 to get a login.  I did this and logged in but it gave an error  message "signature not found in user keyring perhaps try the interactive  ecryptfs-mount-private.  (my memory is a little weak about this  point.)  I also had a boot-repair disk and I put that into the CD drive  and booted with the disk in the drive.  That did not do anything for my  problem.  I found a keyboard sequence of Alt-PrintScreen held down while  typing R, E, I, S, U, B.  Well, this worked but when I got back to the  GUI the desktop was the same as before.

Fortunately there was a  directory on my desktop which I could open with the mouse.  This gave me  a file browser function.  From this I was able to copy my "home"  directory to an external hard drive.  That being done, I decided to try  to reinstall Ubuntu 14.10.  Oh, I had upgraded to 14.10 recently because  a calendar program called california would not work with Ubuntu 14.04.   I wonder if this new version of Ubuntu is the problem.

I put the  Ubuntu 14.10 DVD in the drive and turned the computer on.  I chose to  reinstall 14.10 so that all of my files could be kept.  This seemed to  work.  So, I was hopeful.  However, when I logged in the screen went  back to the login screen again.  Hmm.  Not good.  I tried another  password, thinking that I might have used the wrong password but I got  the message that the password was incorrect.  I did not get that message  the previous time.  So, I think I have the right password but for some  reason the program is not opening up.

So I pressed Alt-Ctl F1 to  get the terminal login.  When I tried to login I got the message  "signature not found in user keyring perhaps try the interactive  ecryptfs-mount-private (or something like that.  Actually at this point  my memory is weak.  I can not remember everything I did to get this  message.)  I searched on the web for this problem and found a page which  recommended typing this in a terminal: ecryptfs-rewrap-passphrase  /home/.ecryptfs/$USER/.ecryptfs/wrapped-passphrase.  I typed this and  got a response which I do not remember but it was not bad nor good, I  think.  Then I logged in on the terminal and the login was accepted  (same as I typed on the GUI).  However when I pressed Ctl-Alt Delete, I  went back to the GUI login screen which did not work, as before.   Actually this login did not say that the password was incorrect but the  screen went blank for a second and then came back as the same login screen.

Then  there was another command that was recommended: sudo dpkg -P  ecryptfs-utils.  I typed this and something happened (not an error) but  it did not seem to solve my problem.

So, I do not have any other  ideas as of this time.  Dumb computer!!!

---

### Post by leunam12 on 2015-05-09
If you just copied your home directory as in drag and drop copying or using cp then you have a permission problem and that is why you can't login. The correct way of doing this (copying your home folder) is with rsync, tar or some backup utility such as dejadup or redobackup or clonezilla.

If you made a backup of your old installation before re-installing, restore it and copy your home folder like this```
sudo rsync -aXS --exclude='/*/.gvfs' /home/. /media/<your external hard drive>/
```install Ubuntu again and restore with the same command (of course when you restore your source is going to be your external hard drive and your destination is going to be your actual home folder)

If you didn't backup, then there is a lesson to be learned: always backup before attempting something like this. If this is the case, then I don't know how to fix your problem but take a look at this thread and see if it helps you solve your problem or search for "ubuntu fix home permissions"
[http://serverfault.com/questions/35076/need-to-fix-file-permissions-in-a-users-home-directory](http://serverfault.com/questions/35076/need-to-fix-file-permissions-in-a-users-home-directory).

---

### Post by milanandme on 2015-05-11
Leunam12,
Thank you for your reply.  I think I need some more help, however.

First of all, I did not understand your reasoning for restoring the "previous" backup.  I did copy the "home" folder but with "copy/paste" from the GUI.  This was not using the programs that you mentioned.  So, I guess I did not backup the installation before reinstalling Ubuntu.  However I thought I would  try reinstalling ubuntu as you suggested and choosing a "revert back to the previous installation" option if available.  I did not know what to expect from the Ubuntu 12.10 disk.

When I put the disk in the drive and restarted the computer I got a series of screens.  I took a picture of each one but those picture files are too big to attach here.  I will just tell you what they said.  First there was the screen that gave me options of Try Ubuntu without installing, Install Ubuntu, OEM, Check disk for errors.  I selected Install.  Then language: English, next internet: not now, next requirements for installation: all met.  Then a screen came up that said, This computer already has Ubuntu 14.10 installed on it.  What do you want to do?  The "Reinstall" option was grayed out.  Maybe that was because I already chose that option once before.  At the bottom there was an option, "Something else".  The other options would have destroyed my data.  So, I chose "Something else".  However, this resulted in a screen that had lots of busy graphics (something about drives, partitions, etc) and an "Install" button.  At this point I got "wet feet".  (Oh, I did do something that gave me a pop-up window that said that there was no root directory defined.)  So, I hit the back button.  Well, that took me "back" however, eventually I selected "Cancel".  This resulted in a "normal" Ubuntu desktop (almost).  So, I thought I would try your idea of resyncing the home directory from the external hard drive with the current computer.  I opened a terminal and typed the command that you wrote for me.  However, I got no request for a password.  The response was another prompt, just the directory name ending with a dollar sign ($). Nothing.  So, I opened the Settings window and looked at Users.  There was nothing there.  Not my name, just "My Account" with a dash (-) after the user name.

So, I think this is not fixed.  Do you have any other ideas?  Thanks, milanandme

---

### Post by leunam12 on 2015-05-11
Ok, this is what I meant:

1-If you copied your home folder using copy and paste, installed a fresh Ubuntu and then copied back your home folder to your new installation your system is going to boot but you are not going to be able to login because the home folder permissions are messed up.

2-From your last post I can tell that you did not make a backup of your old installation before attempting to reinstall Ubuntu, therefore disregard all I said about restoring the backup and using rsync to copy your home folder. there is no way you can do this now. It's just something to keep in mind for the future if you ever have to copy your home folder again, don't copy and paste.

3- I would Try to fix the home folder permissions, follow the instructions on the link at the bottom of my first post and see if that works. You may have to boot into recovery mode to do this.
Follow these instructions to boot into recovery.

[http://askubuntu.com/questions/150367/how-do-i-boot-into-recovery-mode](http://askubuntu.com/questions/150367/how-do-i-boot-into-recovery-mode)

also you may try this other link to see if you can fix your permissions that way. I'm just trying to help you but I make no guarantees that any of this is going to work.

[http://askubuntu.com/questions/454576/cant-login-to-ubuntu-14-04-after-upgrade](http://askubuntu.com/questions/454576/cant-login-to-ubuntu-14-04-after-upgrade)

---

### Post by milanandme on 2015-05-11
Leunam12,

Well, thank you again.  However, I think I will "throw in the towel" and just overwrite everything with a new Ubuntu 14.10 installation.  I was able to boot to the recovery mode but not change the permissions.  The "find" command could not find my home directory.  When I did a dir command all that was there was Desktop, VirtualBox\ and VMs.  I could "cd" to Desktop but not to VMs.  I got a message that VMs did not exist.  When I tried to "cd" to VirtualBox\, I got a different kind of prompt from which I could not recover, without holding the power button down.  So, I think my "home" directory is gone.

I am thinking that I will just copy and paste my data to the new installation.  I will probably have to reinstall all application programs.  If you have any suggestions or tips on this, please let me know.

Thanks again, milanandme

---

### Post by leunam12 on 2015-05-12
what happened was that you where in the /root directory, if you type "cd .." or "cd /" (without quotation marks) and press enter then you will be able to see your home directory when you do dir or ls.

Also keep in mind that an example like this (found on one of the links that I posted):```
find /home/user -type f -exec chmod 0664 {} \;
```you must replace the word "user" with your user name.

---

### Post by milanandme on 2015-05-12
leunam12,

Wow!  This actually worked.  However, I still have a problem.  First, what worked was that I was able to log into my computer.  I got the usual desktop and controls.  What is not "my old computer" is the file system contents.  I have directories like, Desktop, Documents, Downloads, etc. but there is nothing in them.  What happened to my old data?  Of course, I have a copy of my old "home" directory on an external hard drive but if this setting of permissions was the only problem, then why do I not have my whole file system back?  Well, if you can tell me how to get it back, I do not really need to know why I do not have it now.  Should I just copy and paste my saved "home" directory onto the new "home" directory, replacing everything or is there something else that I should do?

Thanks again for your help.  - milanandme

---

### Post by leunam12 on 2015-05-13
I have no idea why your old content is not there, but If you still have it, then copy it to your new installation.

---

### Post by milanandme on 2015-05-16
leunam12,

I found that there is still a lot of data on my hard  drive.  Since there does not seem to be a way for me to use this data,  do you think I should overwrite it by using the Ubuntu 12.10 disk, or is  there something that I can do to use this data?

Thanks, milanandme

---

### Post by leunam12 on 2015-05-16
What data is that and what happens if you try to use it? Besides, why do you want to install Ubuntu 12.10 which is not supported anymore?

---

### Post by milanandme on 2015-05-19
leunam12,

I found a bug report that may explain why I can not use my storage space.  [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)
There is a fix for this bug.  I emailed the "fixer" but no reply yet.  I suspect that the fix is to the basic Ubuntu software and not a solution for someone who has experienced the problem, but I am not sure.  Maybe I will learn this if the "fixer" replies to my email.

I did not know that 14.10 is out of date.  However, I did get a pop-up recently saying that there is a new version.  Maybe I will download the full installation software for the new version and burn a DVD so that I can wipe my hard drive, if necessary.

Thanks,
milanandme

---

### Post by milanandme on 2015-05-19
leunam12,

I found a bug that may explain why I can not use the data on my hard drive.  [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

I wrote to the person responsible for fixing this bug but I have not gotten a reply yet.  The fix may be to the Ubuntu software only and not a solution for me, who have this problem.

I did not know that 14.10 was not the latest version of Ubuntu.  I did notice, however, that I got a pop-up saying that a newer version was available.  Maybe I will download the full software and burn a DVD.  Then I can wipe my hard drive if necessary.

Thanks,
milanandme

---

