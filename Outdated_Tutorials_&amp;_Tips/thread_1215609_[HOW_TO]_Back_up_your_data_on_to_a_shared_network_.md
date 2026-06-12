---
title: "[HOW TO] Back up your data on to a shared network drive"
date: 2009-07-17
forum: Outdated Tutorials &amp; Tips
---

### Post by chaanakya_chiraag on 2009-07-17
This should work on **any** version of Linux, although it has only been tested on (Ubuntu) Jaunty Jackalope and (Ubuntu) Karmic Koala.

**If using on a non-Debian Linux system, the commands here given for installing the software are not applicable.**  Please consult your distribution if you do not know how to install software.

I am going to show you how to back up your home directory (/home/username) to a remote drive shared on the network (ex. Lacie Ethernet BigDisk - 1TB) along with a list of installed packages and a list of sources.
Prerequisites: 
Step 1: Open up a Terminal window (Applications->Accessories->Terminal - don't be afraid :D ) and keep it open for the duration of this tutorial.

Step 2: Paste the following code into the Terminal window: ```
sudo aptitude install smbclient smbfs
```Setting up the backup: 
Step 1: Configure your network drive properly and make sure you can connect to it from the computer you wish to back up.  Also record the IP Address of the network disk.  **I am sorry, but I cannot help you set up your network drives.  There may be threads on the forum that can help you if you are having problems.**

Step 2: Create the mountpoint for the backup drive by pasting the following into the Terminal window you left open:
```
sudo mkdir /mnt/backup
```Step 3: Open up a new Text Editor window (Applications->Accessories->Text Editor)

Step 4: Copy the code below into the Text Editor window and save it as a shell script (File->Save As...->Select shell script as the file type):
```
#!/bin/bash
cd
yes "**your password here**" | sudo -S cp /etc/apt/sources.list .
dpkg --get-selections > installed-software 
yes "**your password here**" | sudo -S smbmount //IP address/share name /mnt/backup -o username=**username**,password=**password**,uid=1000,mask=000
#username and password are optional, so only input them if necessary.
rsync -arquz **--exclude=Music --exclude=Videos --exclude=Pictures --exclude=Dropbox --exclude=Examples --exclude=.VirtualBox --exclude=.beagle --exclude=.cache --exclude=.icons --exclude=.evolution --exclude=Skype\ Calls --exclude=tabla\ lessons --exclude=.thumbnails --delete /home/chiraag** /mnt/backup/
yes "**your password here**" | sudo -S smbumount /mnt/backup
exit
```Rsync options: a = archive (not sure what this does :D , but leave it on), r = recurse into directories, q = quiet (recommended - otherwise your Terminal window will fill with junk :D ), u = update (skip files that haven't been changed), z = compress (makes network backups faster, recommended)

Step 5: replace the **bolded items only!!!!!** with appropriate values.  For the rsync options, I would just change which paths you want excluded and **maybe** remove the ```
--delete
``` option.  **Keep in mind, if you delete the ```
--delete
``` option, no files deleted on your computer will be deleted on the back up hard disk!!!  This can lead to unnecessary bloating of your backup.**  Finally, make the script executable with ```
sudo chmod +x **/path/to/backup/script/you/just/created**
```  Replace **/path/to/backup/script/you/just/created** with the actual path.  To figure out this path, go to Places->Home and browse to the folder which contains the script.  Then, click on the little icon next to the buttons which show where you have been (the tooltip should say something pertaining to location).  The full path should be shown with slashes (/) between folder names.  Copy this long thing and paste it into the terminal instead of the /path/to/backup/script/you/just/created.

Step 6 [optional]: Install "Scheduled Tasks" with ```
sudo aptitude install gnome-schedule
``` (paste the code into the Terminal window) and schedule your backup script to run however often you wish!

TO RESTORE:  Simply change the rsync command in the script to read ```
rsync -arquz **--delete** /mnt/backup/ **/home/chiraag**
```  **KEEP IN MIND: IF YOU KEEP THE --delete OPTION, IT WILL DELETE ALL FILES THAT WERE NOT BACKED UP.  PLEASE TAKE CAUTION WHEN USING THIS WITH THE RESTORE SCRIPT.**  That's all, folks! :D
- Chiraag

---

### Post by danastasio on 2010-01-25
Nice howto,

If I wasn't having any problems connecting to my samba server using smbmount, i'd definatly use it!

I've bookmarked it just in case the server decides to start working the way i want it to XD

---

### Post by chaanakya_chiraag on 2010-01-26
Thanks!  Is there anything even remotely confusing (especially from the eye of a beginner)?  I want to make sure that nothing is ambiguous :)
- Chiraag

---

### Post by danastasio on 2010-01-26
It kept giving me syntax errors until i removed 
> needed to access network drive (if applicable)

I recommend putting that on a separate commented out line.

Other than that the script works really well, I keep getting permission errors, but thats the fault of the server. I'd defiantly recommend this to other users.

---

### Post by chaanakya_chiraag on 2010-01-26
Thanks!  I'll do that ASAP :)
- Chiraag

---

