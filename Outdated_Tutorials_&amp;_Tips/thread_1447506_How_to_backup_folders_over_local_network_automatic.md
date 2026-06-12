---
title: "How to backup folders over local network automatically using rsync and two computers"
date: 2010-04-05
forum: Outdated Tutorials &amp; Tips
---

### Post by Naggobot on 2010-04-05
[FONT=Arial][SIZE=2]**during the boot up of the second computer.**[/SIZE][/FONT]
 
 [FONT=Arial][SIZE=2]Motivation of this tutorial is to document the system I setup so that I do not need to re-find every piece of information later on. Hopefully someone else can also benefit from this document. 

I welcome any input on how to improve the setup and feel free to post also other comments. I need to admit that this document has been in process for more than a month and there fore some errors are possible. Please comment if you notice that something is wrong.  [/SIZE][/FONT]
 
 [FONT=Arial][SIZE=2]For similar and simpler backup tutorial using ssh see  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2][http://ubuntuforums.org/showthread.php?t=795668](http://ubuntuforums.org/showthread.php?t=795668)[/SIZE][/FONT]
[FONT=Arial][SIZE=2]For similar and simpler backup tutorial using separate disk[/SIZE][/FONT]
[FONT=Arial][SIZE=2][http://ubuntuforums.org/showthread.php?t=786410](http://ubuntuforums.org/showthread.php?t=786410)[/SIZE][/FONT]

 [FONT=Arial][SIZE=2]Steps covered in this document[/SIZE][/FONT]
 
[LIST=1]
[*][FONT=Arial][SIZE=2]**Make IP address of the computer you want to backup fixed using router DHCP reservation**[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]**Set up rsync daemon to the computer you want to backup**[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]**Setup rsync to the computer doing the backup**[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2][B]Setup the rsync to run when the computer starts up
[/B][/SIZE][/FONT]
[/LIST]
   [FONT=Arial][SIZE=2]**1. Make IP address of the computer you want to backup fixed using DHCP reservation**[/SIZE][/FONT]

 [FONT=Arial][SIZE=2]First step is to make computer IP adresse(s) static using the router DHCP reservation. Some other method can be used if  router does not support MAC address based DHCP reservation. [http://ubuntuforums.org/showthread.php?t=1426270](http://ubuntuforums.org/showthread.php?t=1426270) describes one method. IP address needs to be fixed at least for the computer which is backed up. [/SIZE][/FONT] 
 
 [FONT=Arial][SIZE=2]DHCP reservation is set up as follows[/SIZE][/FONT]

[FONT=Arial][SIZE=2]1.1. Find out how you can login to your router. For my router I need to open web browser and on to the address field I write [http://192.168.0.1]("http://192.168.0.1/").[/SIZE][/FONT]

[FONT=Arial][SIZE=2]Please note that this does not     necessarily work with your router.  There are other methods and some     devices may require tampering with subnet settings etc. Make sure     you understand how the login procedure works and if you need to     change some settings on your computer make sure you know what you     are changing and how to reverse those changes before making them.[/SIZE][/FONT]

[FONT=Arial][SIZE=2]1.2. Login to you router and find LAN     or Local area network settings or DHCP settings. Name may vary a bit     but there should be a section for these settings. You need to find a     section where your computer name, IP address and your computer MAC     address are listed. Copy the MAC address of your computer and     current IP that is assigned by router to your computer, use     paper or separate document[/SIZE][/FONT][FONT=Arial][SIZE=2]
[/SIZE][/FONT][INDENT][FONT=Arial][SIZE=1]Shortly (and probably quite inaccuratelly) IP address is like a hotel room that is assigned to you when you visit a hotel. If you are lucky you may end up with same room from visit to visit but there is no guarantee. Eventually you will end up in a different room when the room you usually use is taken by someone else. MAC address is like credit card number of your network card and it will not change just like your credit card number does not change when you are not checked in to your favorite hotel unless you lose the card and you have to get a new one. With DHCP filtering we tell the reception desk of the hotel (i.e. the router) to reserve indefinitely one room from the hotel and that room will be given only to person with matching credit card (i.e. network card).[/SIZE][/FONT]
[/INDENT][FONT=Arial][SIZE=2]1.3. Find DHCP Reservation section. This section should have some form of table where you can write up     your computer name, your current IP address and the MAC address of  your computer. See attachment for one example of the reservation table.  [/SIZE][/FONT]

  [FONT=Arial][SIZE=2]**2. Setup rsync-daemon to to the computer you want to backup **[/SIZE][/FONT] 
 
[FONT=Arial][SIZE=2]2.1. Open the computer you want to backup. 
[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]2.2. Follow instructions given in[/SIZE][/FONT] 
 
 [FONT=Arial][SIZE=2][https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)[/SIZE][/FONT]
 
[FONT=Arial][SIZE=2]in chapters installation and rsync daemon.  [/SIZE][/FONT]

 [FONT=Arial][SIZE=2]In my case I edited the  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]/etc/rsync.conf  [/SIZE][/FONT]
 
```
[FONT=Arial][SIZE=2]max connections = 2[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]  log file = /var/log/rsync.log[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]  timeout = 300[/SIZE][/FONT]
  
 [FONT=Arial][SIZE=2]  [share][/SIZE][/FONT]
 [FONT=Arial][SIZE=2]  comment = HomeFolder[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]  path = /home/MyHomefolderToBeBackedUp/[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]  read only = no[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]  list = yes[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]  uid = MyUserid[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]  gid = sambashare[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]  auth users = MyUserid[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]  secrets file = /etc/rsyncd.secrets[/SIZE][/FONT]
  
```[FONT=Arial][SIZE=2]

Now I have changed the parameters[/SIZE][/FONT] [FONT=Arial][SIZE=2]
[/SIZE][/FONT] 
 [FONT=Arial][SIZE=2]Comment, Path, uid, gid, auth users[/SIZE][/FONT]
  
[FONT=Arial][SIZE=2]to fit my needs so that comment parameter indicates that the [share] module is for my home folder, path  variable points to my home folder and uid (user id) parameter is my user id, gid (group id) parameter is    the user group sambashare. I admit that I am not 100% sure what these do and if you need all (probably not) but this works for me. I used the sambashare as group since I have samba installed and that particular group is available on both computers and home folders are shared through Samba.  [/SIZE][/FONT]
 
 [FONT=Arial][SIZE=2]**3. Setup rsync to the computer doing the backup**
[/SIZE][/FONT]
[FONT=Arial][SIZE=2]3.1. Open the computer that will store  the backup[/SIZE][/FONT]

[FONT=Arial][SIZE=2]3.2. Install rsync[/SIZE][/FONT]

[FONT=Arial][SIZE=2]I installed all of the packages mentioned in the rsync community documentation but just rsync should suffice.   To install packages I normally use synaptic with GUI but following should work also[/SIZE][/FONT]
 
 [FONT=Arial][SIZE=2]Open terminal and write:[/SIZE][/FONT]
 
 [FONT=Arial][SIZE=2]```
sudo apt-get install rsync
```[/SIZE][/FONT]

[FONT=Arial][SIZE=2]3.3 Create exclusion list for the backup script[/SIZE][/FONT][FONT=Arial][SIZE=2]
[/SIZE][/FONT]
[FONT=Arial][SIZE=2]In order to avoid unnecessary errors and copying of unnecessary data the rsync needs and exclusion list which can be used to tell rsync what to copy and what not to copy. Otherwise copying generates a lot of  errors since some of the hidden files in the home folder are not copyable except as root. Also there is no point to copy program specific settings.  [/SIZE][/FONT]

 [FONT=Arial][SIZE=2]Open terminal and type[/SIZE][/FONT]
[FONT=Arial][SIZE=2]
[/SIZE][/FONT]```
[FONT=Arial][SIZE=2]gksudo gedit /etc/rsyncexclude[/SIZE][/FONT]
 
```[FONT=Arial][SIZE=2]This will create a file named rsyncexclude to the /etc folder[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]For me the file contents are[/SIZE][/FONT]
 
```
[FONT=Arial][SIZE=2].*[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]*Crypt*[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]*Trash*[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]'My GCompris*'[/SIZE][/FONT]
 
```[FONT=Arial][SIZE=2].* tells rsync not to copy  hidden files and folders  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]*Crypt* tells rsync not to copy folders containing text string Crypt[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]*Trash* tells rsync not to copy folders containing text string Trash[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]'My GCompris*' tells rsync not to copy folders containing text string 'My GCompris'[/SIZE][/FONT]
 
 [FONT=Arial][SIZE=2]3.4. Create a password file 
[/SIZE][/FONT]
[FONT=Arial][SIZE=2]in terminal type[/SIZE][/FONT]

[FONT=Arial][SIZE=2]gksudo gedit /[/SIZE][/FONT][FONT=Arial][SIZE=2]etc/rsyncpasswd
[/SIZE][/FONT]
[FONT=Arial][SIZE=2] to create a file named rsyncpasswd and in to the gedit write the password you defined in to the [/SIZE][/FONT][FONT=Arial][SIZE=2] rsync.secrets file.[/SIZE][/FONT]

[FONT=Arial][SIZE=2]3.5. Make password file not world readable
[/SIZE][/FONT]
[FONT=Arial][SIZE=2]In order for the rsync to accept the file as password file it must not be world readable.  [/SIZE][/FONT]
 
 [FONT=Arial][SIZE=2]**I am not 100% sure** what chmod number I used but  [/SIZE][/FONT]
  [FONT=Arial][SIZE=2]```
sudo chmod 600 /etc/rsyncpasswd

```[/SIZE][/FONT][FONT=Arial][SIZE=2]
[/SIZE][/FONT][FONT=Arial][SIZE=2]
should do the trick. My rights list on terminal as follows [/SIZE][/FONT][FONT=Arial][SIZE=2] -rw-r----- 1 root root   10 2010-03-02 12:22 rsyncpasswd  [/SIZE][/FONT]
 
 [FONT=Arial][SIZE=2]type 
[/SIZE][/FONT]
```
ls -la /etc/rsyncpasswd 
```[FONT=Arial][SIZE=2]
[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]in to the terminal to get the previous output. The user rights are the first 10 digits and when they are as shown then the rsync accepts the password file.  [/SIZE][/FONT]
[FONT=Arial][SIZE=2]
**4. Setup rsync to run on when the         computer starts up**[/SIZE][/FONT][FONT=Arial][SIZE=2]
[/SIZE][/FONT]
[FONT=Arial][SIZE=2]This was the problematic part for me. In order to read the password file the rsync had to be run as root since only root can access the password file. On the other hand I did not want the rsync asking any input when it is run. I over came this by making a shell script to init.d[/SIZE][/FONT]
 
[FONT=Arial][SIZE=2]4.1 Create script file 
[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]open terminal and write[/SIZE][/FONT]
 
```
gksudo gedit /etc/init.d/myautobackupscript.sh
 
```[FONT=Arial][SIZE=2]Script contents for me are:[/SIZE][/FONT]
 
```
#!/bin/sh  
 rm '/home/myhomefolder/rsoperlog.txt'  
 sleep 60
 rsync -a --password-file='/etc/rsyncpasswd' --progress --log-file='/home/acer5020/rsoperlog.txt' --exclude-from='/etc/rsyncexclude' acer5020@192.168.0.101::share /home/acer5020/rsyncbackup/  
 exit(0)
 
```[FONT=Arial][SIZE=2]Now what this I have intended with this:  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]First line indicates that the file is a script[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]Second line removes the old log file from home directory.  [/SIZE][/FONT]
  [FONT=Arial][SIZE=2]Third line tells the script to wait 60 seconds. I added this for reasons I tell later[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]Fourth and fifth line are the rsync command which is wrapped here so that it can be read.[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]Sixth line hopefully tells the script to exit when the script is ready.   [/SIZE][/FONT]
 
 [FONT=Arial][SIZE=2]Now note that I do not have the commonly used / presented parameter -delete -zvv on the rsync command. Reasons for this are as follows[/SIZE][/FONT]
 
[LIST=1]
[*][FONT=Arial][SIZE=2]I do not want the rsync to delete     anything from the backup directory (-delete)[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]I do not want to compress the data     before sending since 99.9% of the data is digital photos already     compressed.[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]There is no point for verbose     since the script is run in background.      [/SIZE][/FONT]
[/LIST]
  [FONT=Arial][SIZE=2]This leaves me with the options[/SIZE][/FONT]
  
[LIST=1]
[*][FONT=Arial][SIZE=2]-a = create archive style backup     I.e maintain many attributes of the files[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]- -password-file = path to     password file[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]&#8211; progress = Indicate progress     (now this is probably totally unnecessary and I just noted it)[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]--log = write a logfile to     indicated folder and file name[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]--exclude-from = file to read     exclude parameters from[/SIZE][/FONT]
[/LIST]
  [FONT=Arial][SIZE=2]4.2. Make script executable[/SIZE][/FONT]
 
 [FONT=Arial][SIZE=2]I would add a cool code line here with sudo chmod u+x /etc/init.d/mybackupscript.sh command but since by surfing forums I find different variations of this command (u or a or none?) I shall describe the method I know works, but be warned no fast fingers and mistakes after you have started nautilus with sudo!. [/SIZE][/FONT]
 
 [FONT=Arial][SIZE=2]open terminal[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]type[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]gksudo nautilus[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]select filesystem from places menu &#8594; select etc folder &#8594; select init.d folder &#8594; select your script &#8594; right click the script &#8594; properties[/SIZE][/FONT]
 
 [FONT=Arial][SIZE=2]Right click the file and select tab permissions and mark the box by  &#8220;allow executing this file as program&#8221;[/SIZE][/FONT]
 
 [FONT=Arial][SIZE=2]Next add the script to startup, see instructions from this thread[/SIZE][/FONT]
 
 [FONT=Arial][SIZE=2][http://ubuntuforums.org/showthread.php?t=277997&highlight=script+at+startup](http://ubuntuforums.org/showthread.php?t=277997&highlight=script+at+startup)[/SIZE][/FONT]
 
**[FONT=Arial][SIZE=2]Some discussion[/SIZE][/FONT]**
[FONT=Arial][SIZE=2]
And at this point I need to point out that for the update-rc.d command the parameter *defaults* includes/replaces a lot configuration parameters that can be added to command and for a linux toddler/computer hobbyist like me the parameters are far from self explaining. 
[/SIZE][/FONT]
[FONT=Arial][SIZE=2]I would appreciate any input on how to make the script run as last script during the startup after login is ready and network is attached. 
[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]As previously noted on section 4.1 I added the sleep 60 parameter  to give user time to login and for the wireless to connect. I do not know if that is necessary but I suspect that it does not do any damage.  Better solution would be appreciated.  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]
**Final word**
This method is not secure since transmitted data is not encrypted. Use only in local network.

[B]Copyright
[/B]Above text of this post may be distributed under [Creative Commons Attribution Share Alike]("http://creativecommons.org/licenses/by-sa/3.0/") license**. **Attribution must be made to Ubuntu forums.  [/SIZE][/FONT]

---

### Post by Naggobot on 2011-06-05
I have migrated the backup script to Upstart

```


# Syncbackupmycomputer - 
# Backup automatically
# 
description    "synchronized backup of my other computer"

start on (started network-manager)

script
    rm '/home/myhome/rsoperlog.txt'
    sleep 90 
    nice -19 rsync -a --password-file='/etc/rsyncpasswd' --progress --log-file='/home/myhome/rsoperlog.txt' --exclude-from='/etc/rsyncexclude' myusername@192.168.0.101::share /home/myhome/rsyncbackup/
    exit 0
end script

[CODE]

This script is saved to 

[CODE]/etc/init
```and is named

```
mybackupscript.conf
```Note the .conf ending. 

Do not convert the script to executable. Sleep may not be required.

---

