---
title: "Cloning Ubuntu to Different Computer Hardware"
date: 2007-08-14
forum: Outdated Tutorials &amp; Tips
---

### Post by JimSooke on 2007-08-14
[SIZE="6"]
Cloning Ubuntu to Different Computer Hardware[/SIZE]

[SIZE="5"]Introduction[/SIZE]

Hi!  Welcome to a guide for cloning a Ubuntu software configuration to a computer with a different hardware configuration.  I configured a Ubuntu operating system (Edgy Eft) with multiple testbeds and and a set of development software that worked well together, but to do this required a lot of time and energy.  I needed to reproduce this configuration on a system with more memory and hard disk as time went on, so let me explain how I did it. 

During my research, I came across an excellent article on how to backup your system using the tar command (BackupYourSystem/TAR in this forum).  At first I thought I had found my answer, only to discover that after I had un-tarred the files, I couldn't reboot the target system.  I liked the tar approach, and the concepts in this article, so I just modified to solve my problem!  I would suggest reading this BackupYourSystem article first, then continue on with this one.  I am not going to repeat the explanations and description that are in the article, but since this approach is derived, they do apply. 

In order to clone a system to a different hardware platform, I used the same process, but had to make sure that I did not clone any hardware specific files or the new clone would probably not even boot.  I looked at the Linux filesystem and the directories under / in Ubuntu and decided on the ones that I thought I would need to clone the software configuration and only tarred those.  The directories I chose were:  etc, home, opt, tmp, usr, and var.  I also excluded the cloning tar file itself!

[SIZE="5"]Step 1 - Preparing to Clone[/SIZE]
 
Step 1A - Before you can clone your system, you will need to do a basic install of Ubuntu on the target machine.  The version of Ubuntu must match the version of Ubuntu on the source machine that is being cloned.  Make sure that you give this target computer a unique name on the network so samba can recognize it, then give it a unique initial user to prevent confusion. 
 
[SIZE="3"]Command Line Approach[/SIZE]
 
Step 1B - To create shared folders via the Shared Folders menu, you type ```
shares-admin
``` into the command line, and the Shared Folders window appears.  Click on Shared Folders, and the Install Sharing Services window will come up.  Press install services, and provide the user password.  You will get a message that the services have been installed properly and you can close the window.  Before you do, you will want to add a share to your home directory.  To do this, chose the '+Add' button on the top right of the form, and you will get a screen with the home directory share filled in for samba (smb) sharing.  Click 'Okay' and the share will be set up.
[SIZE="3"]
GUI Approach[/SIZE]
 
Step 1B - Once the system is installed on the hard disk, the CD removed, and the user logged on, then the share services need to be installed.  To do this, go to the System tab at the top left  and then the Administration menu, and finally the Shared Folders entry.  Click on Shared Folders, and the Install Sharing Services window will come up.  Press install services, and provide the user password.  You will get a message that the services have been installed properly and you can close the window.  Before you do, you will want to add a share to your home directory.  To do this, chose the '+Add' button on the top right of the form, and you will get a screen with the home directory share filled in for samba (smb) sharing.  Click 'Okay' and the share will be set up.

Step 1C - To prepare the source computer, you will want to remove any unneeded files, especially large ones because they will take longer to tar, transfer and untar and make the tar file that much bigger.  Also, any personal data you don't want cloned to the target computer should be removed as well!  The clone will look exactly like the source computer when we are finished.

[SIZE="5"]Cloning[/SIZE]
 
Now, we are ready to clone the source system and get it running on the target computer.  In order to do this, we will need to make a tar file of certain directories, transfer this tar file to the target machine, and then un-tar it. 

[SIZE="5"]Step 2 - Creating the Tar File [/SIZE]

[SIZE="3"]Command Line Approach[/SIZE]
 
To create the tar file, you will have to open up a terminal window.  To do this, go to Applications > Accessories >Terminal and click.  The terminal window starts out in your home directory.    Let's assume you are in your home directory (~).  In order to tar the directories we need, you will have to become root.  To do this type in sudo -s.  When prompted, enter your  administrator account password, and you will be acting as root.  The tar file will include the /etc, /home, /opt, /tmp, /usr, and /var directories and subdirectories, and the tar file itself needs to be kept from being included. So the command to tar the directories looks like this:

```
tar -cvzf ~/clone.tgz --exclude ~/clone.tgz  /etc /home /opt /tmp /usr /var
```

The parts of the command are:
 
tar - the command itself
 
-cvzf - c means create, v means verbose, so the file names will appear on the screen as they are added, z means compress the file with gzip, f means the next  argument is the name of the file to put the results in.
 
~/clone.tgz - this is the name of the file that will contain the tar results.  ~/ indicates that the file will be created in the home directory.
 
--exclude - means that the tar file should not include the next file name
 
~/clone.tgz - so we are not including the tar file itself in the tar
 
/etc /home /opt /tmp /usr /var - these are the directories and their subdirectories that will be included in the tar file
 
The tar file, clone.tgz is now in your home directory, ready to be placed on the target computer.  You can check this by entering

 ```
ls ~/clone.tgz
```

  This will display the tar file name.
 
[SIZE="3"]GUI Approach[/SIZE]
 
To create the tar file using the GUI desktop, you will have to be logged in as root.  To do this, go to System > Administration > Login Window.  Enter admin password.  Login Window Preferences window will open.  Click on the Security tab.  Check the Allow local system administrator login.  Close the window.  (I would recommend that after you create the tar file that you return to this window and un-check this option.)
 
Now you must switch to the root account.  Go to System >  Quit and chose Switch user in the window that appears.  A login window will appear.  Login in as root using the administrator password.
 
Next we are going to create the tar file.  To do this, you must go to Applications > Accessories > Archive Manager.  Click on the new icon.  The new window will appear.  Type in clone.tgz in the name field, the save in field will default to your home directory, and display the Archive type list, and select tar compressed with gzip, then click on the new icon.

A archive input window will appear.  We will use this window to enter the directories we want as well as exclude clone.tar.gz itself.
 
Go to the edit tab, and select Add a folder by clicking on it.  Double-click on File System under Places, and then locate and select 'etc'.  Check the exclude symbolic link button.  Click on the add button.  Repeat for 'opt', 'tmp', 'usr', and 'var' and 'home'.  When you are adding home, also exclude ~/clone.tar.gz before adding.
 
Once you are done, you can close the archive window.  You have created the tar file clone.tar.gz in your home directory.  You are now ready to place the tar file into the target computer.

[SIZE="5"]Step 3 - Transferring the Tar File to the Target Computer [/SIZE]

[SIZE="3"]Command Line Approach[/SIZE]
 
There are a number of ways to transfer the tar file to the target computer.  I am going to use the 'netcat' method identified in BackupYourSystem/TAR. 

To use netcat the target computer must be setup to receive the netcat transmission, and then the source computer can be used to send the transmission. 

Step 3A - To setup the target computer to receive the transmission use the following command:

```
nc -l -p 1024 > ~/clone.tgz
```

The parts of the command are:
 
 nc - the command itself

 -l - means listen mode

 -p - means the next parameter is the port to listen on
 1024 - is the port to listen on

 > - means create and direct the output to the file with the name that follows

 ~/clone.tgz - means copy the tar file into clone.tgz in the target machine's home directory
 
Step 3B - Next you send the tar file to the target computer from the source computer by using the following command
 
```
cat clone.tgz | nc -q 0*** insert receiving host name or IP address*** 1024
```

The parts of the command are:
 
 cat- reads the file (next parameter) and prints it to the standard output

 clone.tgz - cat will read our tar file

  | - pipe directs the output to the netcat command

 nc - the command itself

 -q - means quit after the EOF

 0 - number of seconds of delay

 1024 - is the port to listen on receiving host name or IP address - means create and direct the output to the file with the name that follows

 ~/clone.tgz - means copy the tar file into clone.tgz in the target machine's home directory
 
When the transfer is done, our file clone.tgz will be in the home directory of the target machine.  Now it is time to un-tar the file.
 
[SIZE="3"]GUI Approach[/SIZE]
 
An easy approach to moving the files between machines is to setup shares and use samba to move the files.  It is beyond the scope of this discussion to explain how to use samba, but there is good information about that elsewhere on the Internet.  One such reference is [http://www.oreilly.com/catalog/samba2/book/toc.html](http://www.oreilly.com/catalog/samba2/book/toc.html).  Once samba is installed and ready to go (the basic installation of Edgy Eft Ubuntu all ready had samba up and running), go to Places > Connect to Server ... and the Connect to Server window will appear.  Select the Windows share server type and then put in the name of the target computer's name (note it must be sharing out its home directory).  
 
Select 'Connect' and an icon will appear on your desktop for the new share.  Double click on the icon, and you will  be prompted for the  any connection information required.  Once the 'Places' menu for this icon appears, you can open up a local home directory 'Places' window and just drag and drop the clone.tar.gz file from a Places window that shows the source computer's home directory to the Places window that shows the target computer's shared home directory.
 
You will be prompted for any other information the share needs to establish the connection (e.g., password).  Once the connection is established, you will see a Places window showing what is in the share on the machine you connected to.  When you connect to the target computer, you will see the home directory.  Open another Places window on the source computer, and drag and drop the tar file from the source to the target computer's Places window.  Depending on how large the files are, the copy could take several minutes.
[SIZE="5"]
Step 4 - Installing the Clone Files on the Target Computer [/SIZE]

[SIZE="3"]Command Line Approach[/SIZE]
 
Installing the files on the target computer is very similar to creating them,   The tar command is used again, only this time it is used to extract the files.
 
```
tar -xvpzf ~/clone.tgz -C /
```
 
The changes to the tar command for extracting the data are:
 
 xvpzf - x means extract the files, v means verbose so the file names will appear on the screen as they are extracted, p means keep ownership the same as the original files, z means uncompress the files, and f means the next argument is the name of the file to put the results in.

 ~/clone.tgz - ~ means the home directory, clone.tgz is the tar file to extract

 C - change directory to the one indicated next before extracting the files

 / - the root directory
 
Running the tar command to extract the files will take a little bit of time depending on how many and how big the files are.
 
[SIZE="5"]GUI Approach[/SIZE]
 
The same Archive Manager is used to extract the files as was used to create the files.  Go to Applications > Accessories > Archive Manager, then open the clone.tar.gz file we just copied to the target computer's home directory.  Select the Extract icon on the top row of icons.
 
Extract the files to 'File System' or '/'.  This will put them in their proper place in the file system.
 
[SIZE="5"]Step 5 - Completing the Install[/SIZE]
 
Once the install is completed, the target computer needs to be restarted for the changes to take effect.  The old user(s) you created when you first installed the basic Ubuntu configuration have been deleted, and the same users as existed on the source computer will now be the new users for the target computer.  You will need to check the users and make sure that you only leave the users that you want to be on the new target machine.  As well, you will need to change the name of the computer, because it will have the same name as the source computer, and if you are using samba or other network software, this will cause confusion. 
 
[SIZE="3"]Command Line Approach (Change host name)[/SIZE]
 
The way to change the host name using the command line is as follows: 

```
sudo gedit /etc/hostname 
```

Once the file opens in the editor, you can rename the hostname.  Avoid duplicates of host names already on the network.
 
[SIZE="3"]GUI Approach (Change host name)[/SIZE]
 
To change the host name using the GUI, go to the System menu > Administration > Networking > Network Settings, and on that page select the General tab.  This will provide you with a text field to change the host name. 
[SIZE="5"]
Some Things to Consider [/SIZE]

One thing to consider is files that are not in the included folders (/etc, /home, /opt, /tmp, /usr, /var) or their sub-folders.  For example, perhaps a backup file was added to one of root's folders.  This file will not be cloned over, or any changes that were made to device files.  Media files are not included, so any files that are related to the hardware, will still have to be configured if they weren't during the initial installation of Ubuntu.  Also check for any updates as some of the files that were cloned may not be up to date.  And most of all don't forget to tell your users, so they start using the new computer, and don't just continue to use the one they have gotten used to before.

[SIZE="5"]In Closing[/SIZE]
 
I tried not to repeat most of what was said in BackupYourSystem/TAR, but I did repeat what was needed so someone could clone their system and not have to read the other article to do it, since documents have a way of moving around on the Internet over time, and links become broken.  There are many ways to do this, but this was the method I used, and it worked for me.  It is not elegant, but it is simple and easy.  I hope this detailed explanation does not turn off experienced users, but the newbie is more likely to use this article, and the more detail the better when you are starting out.

---

### Post by ruibernardo on 2007-12-02
Hi,

I've found this tutorial and [https://help.ubuntu.com/community/BackupYourSystem/TAR](https://help.ubuntu.com/community/BackupYourSystem/TAR) very useful because I wanted to backup a server over the network to a workstation that doesn't have any server installed. 

I used the following command to make the backup (from the BackupYourSystem/TAR page)
```
# on the sending side:
tar -cvj --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt \
--exclude=/sys / | nc -q 0 WORKSTATION_IP

# on the receiving side:
nc -l -p 1024 > backup.tar.bz2
```I used this because the server disk is almost full and that command didn't create the backup file in the server (it was created only on the workstation).

I don't know much of netcat and pipes, so my question is: how can I make the reverse thing? I would like to know how to restore the backup without copying the backup file to the server (space is not enough for both backup file and restored content). 

Can it be done with tar/netcat and pipes like the backup was made?

Thanks in advance for any answers.

---

### Post by JimSooke on 2007-12-20
I did not write the article on tar backups, but I do believe there is an explanation there on how to use netcat to get the information back.  You can just look at the man pages as well, and see how to netcat back.  I am presuming that the machine you used for the backup was a linux box as well.  Hope this helps.

---

### Post by ruibernardo on 2007-12-20
Hi JimSooke,

I got it to work as I wanted (not copying the backup file to the restored system, running tar with netcat ouput): [[SOLVED] TAR, pipe and netcat - is it possible?]("http://ubuntuforums.org/showthread.php?p=3887846")

> **epimeteo said:**
> 

[SIZE=2]**To restore**[/SIZE]

On the receiver (with a LiveCD and the / partition mounted in /mnt/disk):
```
sudo -i
nc -l -p 1024 | tar -xvpjf - -C /mnt/disk
```On the sender:
```
cat backup.tar.bz2 | nc -q 0 receiver_ip.com 1024
```
It really was just a case of reversing the syntax of the backup command, but I was getting problems to do it.

I also updated that wiki article with the steps I took to make it work back then (still needs to be integrated to the main article, but the solution is there).

This thread helped me to understand a little more netcat and tar and how it works.

Thank you Jim.

---

### Post by eFundamental on 2008-03-19
Hi Jim

I' ve been given a job to clone a Ubuntu OS, and stuck at it for weeks trying to use cloning software such as Clonezilla which are not working. Your post really show me some light. 

I follow exactly your approach, but I could not start up my Ubuntu OS after restoring. The progress bar (with the Ubuntu Logo) actually stop at the last bar and don't move for hours. 

Do you face such problem?

Desprate,
eFundamental

---

### Post by JimSooke on 2008-03-20
I did not run into this exact problem, but some suggestions might be to check that the users are correct and the machine name is correct since this data is moved from the backup.

As well, as the notes said, there are some files, like multimedia files, and some hardware configuration files which may not match.  This is all I can think of right now to check.  I hope this helps.

---

