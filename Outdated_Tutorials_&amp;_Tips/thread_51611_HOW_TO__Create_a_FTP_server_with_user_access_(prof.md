---
title: "HOW TO : Create a FTP server with user access (proftpd)"
date: 2005-07-24
forum: Outdated Tutorials &amp; Tips
---

### Post by frodon on 2005-07-24
[COLOR="Red"][SIZE="2"]This thread is obsolete but there is useful support in, refer to the breezy one now : [/SIZE]
[SIZE="3"][http://www.ubuntuforums.org/showthread.php?p=429783#post429783 ]("http://www.ubuntuforums.org/showthread.php?p=429783#post429783")[/SIZE]
Thank you :D 
[/COLOR]

I created this How to for people who want to share files with friends using FTP protocol, like FTPservU under windows. The way i give you is not the only one, I hope my How to is enough clear.
This FTP server will allow only users with the good password (persons to whom you gave the password and username). So you will be sure that only known persons will access your FTP server.
[B]
[SIZE=3]1- [/SIZE][/B] Install proftpd with synaptic or with this command : ```
sudo apt-get install proftpd
```
**[SIZE=3]2-[/SIZE]** Add this line in /etc/shells file (sudo gedit /etc/shells to open the file) :```
/bin/false
``` Create a /home/FTP-shared directory : ```
cd /home
sudo mkdir FTP-shared
``` Create a user named **userftp** which will be used only for ftp access. This user don't need a valid shell (more secure) therefore select /bin/false shell for **userftp** and /home/FTP-shared as home directory (property button in user and group window).
To make this section clearer, i give you the equivalent command line to create the user : ```
sudo useradd userftp -p your_password -d /home/FTP-shared -s /bin/false
``` In FTP-shared directory create a **download** and an **upload** directory : ```
cd /home/FTP-shared/
sudo mkdir download
sudo mkdir upload
```Now we have to set the good permissions for these directories : ```
cd /home
sudo chmod 755 FTP-shared
cd FTP-shared
sudo chmod 755 download
sudo chmod 777 upload
```
**[SIZE=3]3-[/SIZE]** OK, now go to the proftpd configuration file :  ```
sudo gedit /etc/proftpd.conf
```and edit your proftpd.conf file like that if it fit to your need :
```
# To really apply changes reload proftpd after modifications.
AllowOverwrite on
AuthAliasOnly on

# Choose here the user alias you want !!!!
UserAlias sauron userftp

ServerName			"ChezFrodon"
ServerType 			standalone
DeferWelcome			on

MultilineRFC2228 on
DefaultServer			on
ShowSymlinks			off

TimeoutNoTransfer 600
TimeoutStalled 100
TimeoutIdle 2200

DisplayFirstChdir               .message
ListOptions                	"-l"

RequireValidShell 		off

TimeoutLogin 20

RootLogin 			off

# It's better for debug to create log files ;-)
ExtendedLog 			/var/log/ftp.log
TransferLog 			/var/log/xferlog
SystemLog			/var/log/syslog.log

#DenyFilter			\*.*/

# I don't choose to use /etc/ftpusers file (set inside the users you want to ban, not useful for me)
UseFtpUsers off

# Allow to restart a download
AllowStoreRestart		on

# Port 21 is the standard FTP port, so don't use it for security reasons (choose here the port you want)
Port				1980

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances 8

# Set the user and group that the server normally runs at.
User                  nobody
Group                 nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022	022

PersistentPasswd		off

MaxClients 8
MaxClientsPerHost 8
MaxClientsPerUser 8
MaxHostsPerUser 8

# Display a message after a successful login
AccessGrantMsg "welcome !!!"
# This message is displayed for each access good or not
ServerIdent                  on       "you're at home"

# Set /home/FTP-shared directory as home directory
DefaultRoot /home/FTP-shared

# Lock all the users in home directory, ***** really important *****
DefaultRoot ~

MaxLoginAttempts    5

#VALID LOGINS
<Limit LOGIN>
AllowUser userftp
DenyALL
</Limit>

<Directory /home/FTP-shared>
Umask 022 022
AllowOverwrite off
	<Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory>

<Directory /home/FTP-shared/download/*>
Umask 022 022
AllowOverwrite off
	<Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory>

<Directory> /home/FTP-shared/upload/>
Umask 022 022
AllowOverwrite on
	<Limit READ RMD DELE>
      	DenyAll
    	</Limit>

    	<Limit STOR CWD MKD>
      	AllowAll
    	</Limit>
</Directory>
```
Ok you have done proftpd configuration. Your server is on port 1980 (in this exemple) and the access parameters are 
user : sauron
password : the one you've set for **userftp**

**[SIZE=3]4-[/SIZE]** To start/stop/restart your server : ```
sudo /etc/init.d/proftpd start
sudo /etc/init.d/proftpd stop
sudo /etc/init.d/proftpd restart
```To perform a syntax check of your proftpd.conf file : ```
sudo proftpd -td5
```To know who is connected on your server in realtime use "ftptop" command (use "t" caracter to swich to rate display), you can also use the "ftpwho" command.
other informations [here](http://www.frankandjacq.com/ubuntuguide/5.04/index.html#ftpserver) 


[SIZE=6]**Misc**[/SIZE]
[SIZE=3]**_ProftpTools 1.0_**[/SIZE]
ProftpTools is a script I wrote thanks to swoop's feedback. This script allow you to start/stop proftpd, mount/unmount auto/manually directories, show your IP, ... and all of that with a **GUI** in order to use proftpd in a really easy way !
To install ProftpTools, download ProftpTools_v1-0.tar.gz (at the bottom of the page) and untar it where you want and then move the ProftpTools file in /usr/bin : ```
tar -xzvf ProftpTools_v1-0.tar.gz
cd ProftpTools_v1-0/
sudo mv ProftpTools /usr/bin/
```Then add this line in your **.bashrc** (it's in your home directory : gedit /home/username/.bashrc) file in order to specify what is the ProftpTools directory path, YOU MUST REMOVE THE "/" CHARACTER at the end of the path. I give you an exemple if your ProftpTools directory is in your home directory : ```
ProftpTools_dir=/home/username/ProftpTools_v1-0
export ProftpTools_dir
```Now all you have to do is to type **ProftpTools** in a terminal and  .... enjoy  :smile: 
You need **zenity** installed to use this script.

Don't hesitate to post in this thread or send me PM to report bugs, ask new features, correct my english, suggest improvement  ;-)  and thank you to give me feedback about this tool.

[SIZE=3]_**useful trick**_[/SIZE] :
This trick is integrated in ProftpTools.
If you don't want (like me  ;-) ) to use space in your /home directory, and use space on another hard drive, or if you just want to share a directory from another partition ...   you can mount the directory you want in your **download** or **upload** directory without changing anything in proftpd.conf file, use these commands : ```
sudo mount -o bind the_directory_you_want_to_share /home/FTP-shared/download
or
sudo mount -o bind the_directory_you_want_to_use_for_upload /home/FTP-shared/upload
```This command **will not** overwrite the directory, the idea is just to mount a directory in another one without overwritng anything, so when someone will log in your server he will see and use the mounted directory if you have mounted one. To unmout a directory (download directory for exemple): ```
sudo umount /home/FTP-shared/download
```**Permanent mount :** 
If you don't want to re-mount your directories after a reboot you can add a line in fstab file like that (sudo gedit /etc/fstab to open the file) : ```
the_directory_to_mount /home/FTP-shared/download vfat bind 0 0
```thanks **reet**  ;-) 

If you want to create other directories in **FTP-shared**, think to add it in proftpd.conf file.
Don't hesitate to test yourself your server using gFTP for exemple, it's really helpful to debug your server.

[SIZE=3]_**Other stuff**_[/SIZE]
**If you have a router** you should read [that](http://www.proftpd.org/localsite/Userguide/linked/x862.html), it describe the 2 commands to add in proftpd.conf and why. 
If you have a dynamic DNS have a look [here](http://www.frankandjacq.com/ubuntuguide/5.04/index.html#assignhostnametodynamicip), you can also use [ddclient](http://linux.cudeso.be/linuxdoc/ddclient.php)(maybe easier for newbies).  
Most of informations you're looking for are [here](http://www.proftpd.org/) 
To get more debug informations : [http://www.proftpd.org/localsite/Userguide/linked/x1058.html](http://www.proftpd.org/localsite/Userguide/linked/x1058.html)
You can specify a specific passive port range using [PassivePorts](http://www.proftpd.org/localsite/Userguide/linked/config_ref_PassivePorts.html)  command, it's very useful when you use a [firewall](http://www.proftpd.org/localsite/Userguide/linked/x294.html)  in order to know which ports to allow.



Thanks for feedback, and sorry if my english is sometimes really bad :roll: 

Don't hesitate to post questions about proftpd in this thread.

---

### Post by vassie on 2005-07-25
Thanks for the How To, btw you can always use ddclient for dynamic DNS, it is very easy to use.

Ben

---

### Post by frodon on 2005-07-25
[QUOTE=vassie]Thanks for the How To, btw you can always use ddclient for dynamic DNS, it is very easy to use.

Ben[/QUOTE]
Thanks for the remark, I've  added a link in misc section.

---

### Post by WetWilly on 2005-07-27
What about defining passive port ranges!?

---

### Post by frodon on 2005-07-27
What do you mean by "passive port range", can you explain what you want to do (or to know) ? (maybe I don't have this knowledge and it's why I don't understand what you mean)

---

### Post by WetWilly on 2005-07-30
well. some ftp clients usually connect in passive mode, and then u need more ports open than just 21. in some servers for winblows I've seen the possibillty to decide which numbers these ports should use.

---

### Post by frodon on 2005-07-30
Ok I understand what you mean.
You can use the [PassivePorts](http://www.proftpd.org/localsite/Userguide/linked/config_ref_PassivePorts.html)  command in order to specify a specific port range for passive ports (very useful if you use a firewall in order to allow these ports).
You can set your server to port 1980 (as in the exemple) and set also passive port range ... up to you ... it depends of your need.
so thanks for the question  ;-) , I will add a line about it in misc section.

---

### Post by da_unruled on 2005-07-30
[QUOTE=frodon]Ok I understand what you mean.
You can use the [PassivePorts](http://www.proftpd.org/localsite/Userguide/linked/config_ref_PassivePorts.html)  command in order to specify a specific port range for passive ports (very useful if you use a firewall in order to allow these ports).
You can set your server to port 1980 (as in the exemple) and set also passive port range ... up to you ... it depends of your need.
so thanks for the question  ;-) , I will add a line about it in misc section.[/QUOTE]
 can anyone help me? I was trying to install the ftpserver and run into some weird trouble, now Im stuck without admin priviledges or something weird like that...
[http://ubuntuforums.org/showthread.php?p=279152#post279152](http://ubuntuforums.org/showthread.php?p=279152#post279152)

---

### Post by n!x on 2005-08-25
[QUOTE=frodon]
2- Create a user named **userftp** which will be used only for ftp access. Go to System>Administration>Group & Users (sorry for the name i have a french version). Give the minimum rights for this user, this user don't need a shell (for security reasons). [/QUOTE]

How do I do that in the shell? I'm connected to the Ubuntu box through ssh.

I have added a user (userftp), but how do I give the new user rights?

Thanks!

---

### Post by dabear on 2005-08-25
Nice guide, how can I make it so that every user on the system can login, upload, make folders and download from their home directory?

---

### Post by frodon on 2005-08-25
> **dabear]Nice guide, how can I make it so that every user on the system can login, upload, make folders and download from their home directory?[/QUOTE]
Well.

When you say "every user on the system" you mean every user connected to the FTP server or every ubuntu users you have defined on your computer ?
The **upload** directory allow users to create folders and write, isn't it what you want to do ?

Could you give me some details about what you want to do exactly and why, it would be easier for me or someone to help you   said:**
> How do I do that in the shell? I'm connected to the Ubuntu box through ssh.

I have added a user (userftp), but how do I give the new user rights?

Thanks!

I guess you used the [useradd](http://www.ss64.com/bash/useradd.html) command, by default the rights are set to the minimum, use -p option for password, -d option to specify the home direstory .... I would use something like that ```
useradd userftp -p your_password -d /home/FTP-shared -s /bin/false
```

---

### Post by cragmonkey on 2005-09-07
why can't I find proftpd when I do an apt-get?

---

### Post by leteci on 2005-09-12
ftp server is running. I enter "chmod -R 666 fdisk". Then I try to connect to ftp and get message: 
530-Unable to set anonymous privileges.
530 Login incorrect.
Login failed.

Why? If I enter "chomd -R 775 fdisk" works ok.

---

### Post by frodon on 2005-09-12
[QUOTE=cragmonkey]why can't I find proftpd when I do an apt-get?[/QUOTE]You should have a [repository](http://ubuntuguide.org/#extrarepositories)  problem.[QUOTE=leteci]ftp server is running. I enter "chmod -R 666 fdisk". Then I try to connect to ftp and get message: 
530-Unable to set anonymous privileges.
530 Login incorrect.
Login failed.

Why? If I enter "chomd -R 775 fdisk" works ok.[/QUOTE]Could you explain a little bit more what is your problem. fdisk is a directory you added in your FTP server ? If it's a configuration problem please join your proftpd.conf file. 
Generally you get a "530 error" when there's a difference between your system configuration (path, rights, ...) and your proftpd configuration.

---

### Post by leteci on 2005-09-12
I configure ftp server with this guide.
"fdisk" is my directory for ftp server. For DL and UL files is the same directory!
When i set the permission for this directory with command chmod 666, i get error message 530 when i try to connect to ft pserver from internet! If I change privilege of "fdisk" directory with chmod 775, then i can conncet to ftp server!

---

### Post by frodon on 2005-09-12
I guess that you configured this directory as the upload directory in the guide. So i think you have this behaviour because MKDIR commands which are allowed in your proftpd.conf file require +x rights, so if you don't set +x sytem rights for this directory there's a mismatch between the system config and your proftpd config which generate the 530 error. Also you said that you tried with 775 rights and it works but with 775 rights you souldn't be able to write in your fdisk directory (do a test), if you want to write in your fdisk directory you need 777 rights.
Hope my answer fits to your need.

---

### Post by America's Reject on 2005-09-12
[QUOTE=dabear]Nice guide, how can I make it so that every user on the system can login, upload, make folders and download from their home directory?[/QUOTE]
 what would be the address, my ip?

---

### Post by frodon on 2005-09-13
yes, your IP or your domain name ([DNS](http://ubuntuguide.org/#assignhostnametodynamicip) )if you have set one.

---

### Post by leteci on 2005-09-14
can you please check configuration file? i try 777 rights but still get 530 error. 
What i want is, that user can see only this directory and subs! Rights for execute must be disabled, only read and write.

---

### Post by frodon on 2005-09-14
First, why do you want to disable +x rights for your ftp directory, +x rights are needed to a directory if you want to enter in, a directory is always executable. Set +x rights to your ftp folder doen't mean that incoming files will be executable. With the configuration i gave, all the incoming files have only read permission for group and users. Therefore you don't have any reasons to disable +x right for the ftp directory and nobody will be able to enter in with +x disable.

If i understand well you would like to allow your friends to download and upload in this directory, so you should modify the directory section like that : ```
<Directory /disk2/ftp/>
Umask 022 022
AllowOverwrite on
	<Limit READ RMD DELE>
	DenyAll
	</Limit>
       <Limit STOR CWD MKD>
      	AllowAll
    	</Limit>
</Directory>
```

Keep this directory with 777 rights (incoming file will have 644 rights therefore don't worry  ;-) ).
Also you have to check if "/disk2/ftp" is the **exact** path because any small path error will generate a 530 error on login, i insist on this point (it's a common error).

Let me know if you still have problems.

---

### Post by leteci on 2005-09-14
i change exactly as you told me. Now, when i try to connect get this error message:
Connection closed by remote host!

---

### Post by frodon on 2005-09-14
Ok, i didn't see last time but following this guide you should have created a user called koseze in your case and should have a /home/koseze directory, as i read in your proftpd.conf you didn't create your ftp directory in /home/koseze, up to you but tell me before what you made different from the guide, you will get better support.
What i advice, if you're agree, is to put your ftp (it's the name of your directory, i'm right ?) directory in the /home/koseze folder, don't forget to do a "sudo chmod 777 /home/koseze" and then correct the directory section of proftpd like that : ```
<Directory /home/koseze/ftp/>
Umask 022 022
AllowOverwrite on
	<Limit READ RMD DELE>
	DenyAll
	</Limit>
       <Limit STOR CWD MKD>
      	AllowAll
    	</Limit>
</Directory>
```If you stiil have problem, try to give me the maximum details, it shouldn't be so complicated (i know several persons which follow this guide without any problems).
Check if you have well created your koseze user (password, home directory).
In the misc section i expain how to mount the directory you want in your /home/koseze/ftp folder if you want to use your disk2 space.

---

### Post by leteci on 2005-09-14
i have two disk in my computer! On first is system ubuntu and home directories of users. User koseze has home/koseze directory! I want to use second disk for ftp users. This disk is mounted and i create disk2/ftp? If i open filesystem there is disk2 directory and subdirectory ftp. Is this a problem in configuration,  because i don't use home directory?

---

### Post by Swoop on 2005-09-14
Followed and works just fine.

Quick, and hopefully easy question:

I want to mont some various directories for my ftp user, like t says i can mount them 1 at a time apparently. Is there an EASY way to set it up so that it automatically gives the ftp user access to read from a couple of dirs, that are NOT in that particular home folder.
I have my documents in my own home dir, but i want to share them via the ftp account.. how really ?

Im used to using guis for configuring my ftp on win hehe.. hard to get used to using non-gui based :(

BTW: is there a gui for controlling proftpd or configuring it ?

And thanks for the guide.. works great !

---

### Post by frodon on 2005-09-14
[QUOTE=leteci]i have two disk in my computer! On first is system ubuntu and home directories of users. User koseze has home/koseze directory! I want to use second disk for ftp users. This disk is mounted and i create disk2/ftp? If i open filesystem there is disk2 directory and subdirectory ftp. Is this a problem in configuration,  because i don't use home directory?[/QUOTE]No it's not a big problem but in the proftpd.conf file i use a useful command to lock the user in the home directory (for security reasons) that's why i advised you to use a /home/koseze/ftp/ directory and then when you use the FTP server you run this command : ```
sudo mount -o bind /disk2/ftp/ /home/koseze/ftp
``` and your disk2/ftp directory is mounted in /home/koseze/ftp, with this way you use the /disk2/ftp memory space (each downloaded or uploaded file will be located here) and keep your config in home directory so you take advantage of the DefaultRoot ~ command which lock the user in the home directory.
I think it fit to your need.

Swoop with the sudo -o bind command you will be able to share the directory you want even if it is not on the ubuntu partition, the sudo -o bind command **will not** overwrite the content of your /home/FTP-shared/download or upload directory, it's just a secure way to share folders from other partitions, so the your friends will see and use the directory you have mounted (use sudo umount /home/FTP-shared/download to unmount the directory). 
You can add more directories in FTP-shared folders (called video, music, ...) just create them, give the good rights (755 for a download directory) and add the corresponding directory section like that for a download directory : ```
<Directory /home/FTP-shared/your_new_directory/*>
Umask 022 022
AllowOverwrite off
	<Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory>
```There is a GUI for proftpd called **gproftpd** but be careful you need to run it as root to handle proftpd and you can easily do wrong things, also the level of security is lower than in the guide.you could also run it as simple user, so you won't be able to modify proftp.conf file (more secure i think) but you will be able to see what happen on your server with a GUI. Remember that the **ftptop** command allow the same thing but in a terminal, try it before download gproftpd (the "t" character allow you to see the download rate).

Well i hope i gave you enougth informations !!!!  :)

---

### Post by reet on 2005-09-14
Hello and thanks for this helpful HowTo.

I am wondering if you could help me out with my FTP server. Everything is working great except when I mount a directory to /download or /upload I don't want to have to do this everytime I boot my computer. Would you know the proper lines to add to the fstab to mount a dir to a different location on every boot?

---

### Post by homerj742 on 2005-09-14
Frodon, You have posted a great tutorial on how to setup the proftpd server.

However, I am very very new to setting up ftp servers and even newer to working on linux. 

I have configured the samba server and can share files with windows PC's in my workgroup. 

However, after setting up the ftp server, I'm not granted access. I simply type in ft://ipaddress of my linux box and get denied. 

I have made sure that my router is forwarding port 1980 to the linux box. 

my dyndns client is configured as it returns the proper IP address. the sub domain I'm trying to use is aamir.is-a-geek.com

If you have any suggestions of what might be wrong, or what I should look into, I would greatly appreciate it! Thank you :)

---

### Post by frodon on 2005-09-15
**Homeri742** you should use a ftp client like **gftp** to login your ftp server it's really easier, however if you still trying to login your server with your web browser type the address like that : [ftp://username@aamir.is-a-geek.com:1980](ftp://username@aamir.is-a-geek.com:1980) or with your IP [ftp://xxx.xxx.xx.xxx:1980](ftp://xxx.xxx.xx.xxx:1980). You just forgot to specify the port.

**reet** it's a really good question  :smile: , in my case i use a script but use the fstab file is also a good way to make that automatic. I never did that but it shouldn't be difficult, try to add a line in the same spirit of the lines which mount your drives. I will make some tests this evening about that.
Don't forget to tell me if you find the answer because i would like to add that in the guide, i think it will interest many people.

Thanks for the idea reet  ;-)

---

### Post by homerj742 on 2005-09-15
That did it Frodon! I appreciate it, I totally didn't specify the port. 

Now the only trouble is I can't login! haha, I must've forgotten the password. I'll see what I can do when I get home. If I'm still having trouble, is it cool if I post my proftpd.conf file?

Again, I appreciate the help :)

---

### Post by Swoop on 2005-09-15
**Frodon** : Thanks for the support.
It's not working exactly like i want it to.

I have batched together a small script to start, and one to stop the server. If people are interested i shall gladly share them here. And if somebody with more experience can perhaps modify them to a single file, that runs with the start/stop command or something ti would be cool.

Let me know if you want me to post the small scripts here...

What it does basically is start the server, mount the directories i want mounted and echo out some nice lines saying its being done .. just for fun.
The stop script of course does the opposite, of closing the server and unmounting the directories ..

---

### Post by frodon on 2005-09-15
Swoop, i like when people help to improve a HOWTO !! :) , thank you for that. So i think it's a great idea to add a script to this guide to run/stop proftpd and mount directories. 
so send me your script i will have a look at it and add it in misc section.
Have you tried to make an alias in .bashrc file for your start on stop scripts, for example ftpstart and ftptop therfore all you have to do is to type ftpstart or ftpstop in a terminal to run the script, it might be a good idea ?
I give you an exemple of a bash alias : ```
alias ftpstart '/usr/bin/ftpstart.bash'
```

I will look forward your script,  thank you again.

---

### Post by homerj742 on 2005-09-15
Frodon,

I cannot login to my ftp server. 
I have created a user on my Kubuntu machine named **ftpuser**.
Any help would be greatly appreciated.
here is my proftpd.conf file:

```
# To really apply changes reload proftpd after modifications.
AllowOverwrite on
AuthAliasOnly on

# Choose here the user alias you want !!!!
UserAlias music ftpuser

ServerName			"mecca"
ServerType 			standalone
DeferWelcome			on

MultilineRFC2228 on
DefaultServer			on
ShowSymlinks			off

TimeoutNoTransfer 600
TimeoutStalled 100
TimeoutIdle 2200

DisplayFirstChdir               .message
ListOptions                	"-l"

RequireValidShell 		off

TimeoutLogin 20

RootLogin 			off

# It's better for debug to create log files ;)
ExtendedLog 			/var/log/ftp.log
TransferLog 			/var/log/xferlog
SystemLog			/var/log/syslog.log

#DenyFilter			\*.*/

# I don't choose to use /etc/ftpusers file (set inside the users you want to ban, not useful for me)
UseFtpUsers off

# Allow to restart a download
AllowStoreRestart		on

# Port 21 is the standard FTP port, so don't use it for security reasons (choose here the port you want)
Port				1980

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances 8

# Set the user and group that the server normally runs at.
User                  nobody
Group                 nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022	022

PersistentPasswd		off

MaxClients 8
MaxClientsPerHost 8
MaxClientsPerUser 8
MaxHostsPerUser 8

# Display a message after a successful login
AccessGrantMsg "welcome !!!"
# This message is displayed for each access good or not
ServerIdent                  on       "you're at home"

# Set /home/FTP-shared directory as home directory
DefaultRoot /home/FTP-shared

# Lock all the users in home directory, ***** really important *****
DefaultRoot ~

MaxLoginAttempts    5

#VALID LOGINS
<Limit LOGIN>
AllowUser ftpuser
DenyALL
</Limit>

<Directory /home/FTP-shared>
Umask 022 022
AllowOverwrite off
	<Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory>

<Directory /home/FTP-shared/download/*>
Umask 022 022
AllowOverwrite off
	<Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory>

<Directory> /home/FTP-shared/upload/>
Umask 022 022
AllowOverwrite on
	<Limit READ RMD DELE>
      	DenyAll
    	</Limit>

    	<Limit STOR CWD MKD>
      	AllowAll
    	</Limit>
</Directory>


```

---

### Post by reet on 2005-09-15
[QUOTE=frodon]**reet** it's a really good question  :smile: , in my case i use a script but use the fstab file is also a good way to make that automatic. I never did that but it shouldn't be difficult, try to add a line in the same spirit of the lines which mount your drives. I will make some tests this evening about that.
Don't forget to tell me if you find the answer because i would like to add that in the guide, i think it will interest many people.[/QUOTE]
Something along the lines of this seems to work, although ROX doesn't like it very much (thinks that it is not yet mounted therefore tries to mount it). Of course if you use a different filesystem type you should adjust the fstab to your preference.
```
/home/reet/incoming /home/FTPshared/upload reiserfs bind 0 0
```
Note: This must occur in your fstab after your main filesystems are mounted.

---

### Post by Swoop on 2005-09-16
[QUOTE=frodon]Swoop, i like when people help to improve a HOWTO !! :) , thank you for that. So i think it's a great idea to add a script to this guide to run/stop proftpd and mount directories. 
so send me your script i will have a look at it and add it in misc section.
Have you tried to make an alias in .bashrc file for your start on stop scripts, for example ftpstart and ftptop therfore all you have to do is to type ftpstart or ftpstop in a terminal to run the script, it might be a good idea ?
I give you an exemple of a bash alias : ```
alias ftpstart '/usr/bin/ftpstart.bash'
```

I will look forward your script,  thank you again.[/QUOTE]

Great idea.. i will be adding that shortly hehe.. in 5 mins in fact ;)
Im sending you the simple scripts now... :D

Swoop

---

### Post by frodon on 2005-09-16
[QUOTE=reet]Something along the lines of this seems to work, although ROX doesn't like it very much (thinks that it is not yet mounted therefore tries to mount it). Of course if you use a different filesystem type you should adjust the fstab to your preference.[/QUOTE]Thanks **reet** i will test that this evening and it in the guide.
Thank you for the effort.  :smile: 
[QUOTE=homerj742]Frodon,

I cannot login to my ftp server. 
I have created a user on my Kubuntu machine named **ftpuser**.
Any help would be greatly appreciated.
here is my proftpd.conf file:[/QUOTE]**homerj742** When you say you cannot login, could you explain a little bit more, a useful information is to give, for exemple, the gftp log informations in order to know what step you didn't pass. Tell me also what you type exactly in gftp, if you use a domain name try to login directly with your IP, and again check if the directory names are the same in proftpd.conf and your system (often result in a 530 error).

---

### Post by homerj742 on 2005-09-16
[QUOTE=frodon]Thanks **reet** i will test that this evening and it in the guide.
Thank you for the effort.  :smile: 
**homerj742** When you say you cannot login, could you explain a little bit more, a useful information is to give, for exemple, the gftp log informations in order to know what step you didn't pass. Tell me also what you type exactly in gftp, if you use a domain name try to login directly with your IP, and again check if the directory names are the same in proftpd.conf and your system (often result in a 530 error).[/QUOTE]
 Frodon, 

I was getting a 530 login error. Upon entering my username/passwd I would get the welcome message, then invalid password. 

But all of a sudden, the password gets accepted this morning. I don't know how or why haha, however this is my NEW problem:

I copied this from FileZilla status window:

```
Status:	Connecting to aamir.is-a-geek.com:1980 ...
Status:	Connected with aamir.is-a-geek.com:1980. Waiting for welcome message...
Response:	220 you're at home
Command:	USER music
Response:	331 Password required for music.
Command:	PASS *****
Response:	230 welcome !!!
Command:	FEAT
Response:	211-Features:
Response:	211-MDTM
Response:	211-REST STREAM
Response:	211-SIZE
Response:	211 End
Command:	SYST
Response:	215 UNIX Type: L8
Status:	Connected
Status:	Retrieving directory listing...
Command:	PWD
Response:	257 "/" is current directory.
Command:	TYPE A
Response:	200 Type set to A
Command:	PASV
Response:	227 Entering Passive Mode (192,168,0,102,128,129).
Command:	LIST
Error:	Disconnected from server
Error:	Could not retrieve directory listing
Error:	Timeout detected!

```

if you want me to download gftp (is it available for windows) I can try logging in from there and post the error.

---

### Post by frodon on 2005-09-16
Well, i already met this error, it sounds like a system rights problem. Run again these commands :```
cd /home
sudo chmod 755 FTP-shared
cd FTP-shared
sudo chmod 755 download
sudo chmod 777 upload
```At this step you're login in the server however filezilla didn't receive the information which describe what folders you shared that's why i first think to a directory rights problem. I'm not in front of my computer so i can't do some tests and try to generate this error to help you in best way, sorry  O:) .

---

### Post by homerj742 on 2005-09-16
[QUOTE=frodon]Well, i already met this error, it sounds like a system rights problem. Run again these commands :```
cd /home
sudo chmod 755 FTP-shared
cd FTP-shared
sudo chmod 755 download
sudo chmod 777 upload
```At this step you're login in the server however filezilla didn't receive the information which describe what folders you shared that's why i first think to a directory rights problem. I'm not in front of my computer so i can't do some tests and try to generate this error to help you in best way, sorry  O:) .[/QUOTE]
 Thanks I will try that when I get home from work! 

If you want to test it later when you are infront of your computer you can

go to [ftp://aamir.is-a-geek.com:1980](ftp://aamir.is-a-geek.com:1980)

username: music


(Yeah that's right, i posted my password! :) )

---

### Post by leteci on 2005-09-16
Ttp works! thanks Frodon! 
If I use sudo mount -o bind old-dir new-dir command works until i restart computer.
Where do i have to save this command, and what exactly do i have to enter? Fstab maybe? thanks

---

### Post by frodon on 2005-09-16
[QUOTE=homerj742]Thanks I will try that when I get home from work! 

If you want to test it later when you are infront of your computer you can
[/QUOTE]I think you should change your password now   :) . I just going to try to generate this error with my own server to know exactly what could generate this error. Don't forget to tell me if your server works.[QUOTE=leteci]Ttp works! thanks Frodon! 
If I use sudo mount -o bind old-dir new-dir command works until i restart computer.
Where do i have to save this command, and what exactly do i have to enter? Fstab maybe? thanks[/QUOTE]The lines to add in fstab will coming soon in misc section and also useful scripts (swoop's idea  ;-) ) to start/stop mount/umout directories therefore you will be able to choose the way you prefer. Some fstab lines is the best way if you always want to share the same directories.
So have a look to the mick section tomorrow  ;-) .

---

### Post by homerj742 on 2005-09-16
Thanks man! I will change the password, right now there is no important information on there so its not a worry. 

Besides, I think I can trust fellow Kubuntu/Ubuntu users :)

The server is up and running, I actually just tried using Filezilla from the office. and got the same message. so hopefully we can figure out what the problem is.

Again, I really appreciate your help. you rock Frodon!

---

### Post by homerj742 on 2005-09-16
Also, is it ok, to chmod all the folders with the '777' command? Or would that cause problems as well?

---

### Post by frodon on 2005-09-16
I chmod 777 the FTP-shared folder because when someone is connected in your server, he is as a simple user that's why you need to give user rights, but for download directory 775 rights are enough because nobody will need to write in this directory (you can also give 777 rights for this directory if you want). The problem for proftpd is more too restrictive rights than too permisive rights.
Generally (it's just my point of view, maybe i'm wrong) there is no security issue to have all folder with 777 rights (my fat32 partitions have 777 rights),  but you may need to make groups and make some folder read only if several users use your computer and if you don't want some users to be able modify your personal folders, it's more a question of organisation.

---

### Post by thomax on 2005-09-16
Very nice howto, very usefull, thanx alot :)

---

### Post by homerj742 on 2005-09-16
Ok cool, I'm the only one using this PC. The reason I saw 777 rights is because I have those folders mapped onto my windows XP machine and i want to be able to do whatever i want to them at any given time. 

But first, I will try your method of changing the folders permissions and see if I can access them via an FTP client. my proftpd.conf looks ok right?

Test out the FTP when you get a chance! Thanks :)

---

### Post by homerj742 on 2005-09-16
[QUOTE=homerj742]Ok cool, I'm the only one using this PC. The reason I saw 777 rights is because I have those folders mapped onto my windows XP machine and i want to be able to do whatever i want to them at any given time. 

But first, I will try your method of changing the folders permissions and see if I can access them via an FTP client. my proftpd.conf looks ok right?

Test out the FTP when you get a chance! Thanks :)[/QUOTE]
 Tried the chmod and it still isn't accessing the directory files. 

The folders were created in the right place.  /home/FTP-shared

---

### Post by homerj742 on 2005-09-18
[QUOTE=homerj742]Tried the chmod and it still isn't accessing the directory files. 

The folders were created in the right place.  /home/FTP-shared[/QUOTE]
 I used the "AllowForeignAddress on" command and I'm able to access my files :)

i'm behind a router/firewall. So I guess that address will let other computers see the IP. great news! Now I'm going to upload all my music on there!

---

### Post by fsshl on 2005-09-18
E: Couldn't find package proftpd

after I type in the first command you list on the article(sudo apt-get install proftpd)

please help,eric

---

### Post by Swoop on 2005-09-18
Try making sure you have the correct repositories available ... 

[http://www.ubuntuguide.org/#installftpserver](http://www.ubuntuguide.org/#installftpserver)

there is a link showing how to make sure you have the correct repositories available for the apt-get command :D

---

### Post by fsshl on 2005-09-18
in the second step, addusr,  my desktop did not have as Frodon describe (system, administation, user/group), my desktop is regular user but I may access by the top manu by computer, system configuration, user/group
then it pompt out asking root password, I type it in , it reply wrong password for root
(if anyone can help me or tell me why it is not work, in the login shell too, if I type in root and its password which work in regular termianl's su from regular user it also not work)
but I can using termianl to su into root accout
so I just add regular user as

adduser userftp

I am not yet try(I tried but change it back), Frodon's   adding  /bin/false           in  /etc/shells  

so I do not know how to execute the following step

 and select this shell for userftp (property button in user and group window).

like to see anyone 's advice
eric

---

### Post by frodon on 2005-09-18
[QUOTE=fsshl]in the second step, addusr,  my desktop did not have as Frodon describe (system, administation, user/group), my desktop is regular user but I may access by the top manu by computer, system configuration, user/group
then it pompt out asking root password, I type it in , it reply wrong password for root[/QUOTE]Open your /etc/schells file with this command : ```
sudo gedit /etc/shells
``` and add the /bin/false as the guide tells you.
Then to create your userftp in a terminal use this command : ```
sudo useradd userftp -p your_password -d /home/FTP-shared -s /bin/false
```
It seems that you have a root password problem, maybe you could create a thread for your problem, it might be better to get help on root password problem.
Don't forget to use the search field of the forum, there's already some [threads](http://www.ubuntuforums.org/showthread.php?t=62379&highlight=password+problem)  about that.

Don't hesitate to post other questions if you have problem using proftpd.

Good luck  ;-)

---

### Post by fsshl on 2005-09-18
I tried:

~ $ sudo useradd user2ftp -p river0 -d /home/FTP-shared -s /bin/false

and modify
/etc/proftpd.conf


#VALID LOGINS
<Limit LOGIN>
AllowUser user2ftp
DenyALL
</Limit>


then use my other computer [ftp://ip:1980](ftp://ip:1980)

window xp promp out a login window
then I type in username:  user2ftp
                     password:   river0

but  it response could not login ftp server as username password specified

please help

---

### Post by homerj742 on 2005-09-18
[QUOTE=homerj742]I used the "AllowForeignAddress on" command and I'm able to access my files :)

i'm behind a router/firewall. So I guess that address will let other computers see the IP. great news! Now I'm going to upload all my music on there![/QUOTE]


Nevermind that last post. I'm able to connect from within the LAN, but NOT outside the LAN. I get a "Could not Retrieve Directory Listing" error. 

But hey, it's better than nothing for now!

---

### Post by fsshl on 2005-09-19
[QUOTE=fsshl]

then use my other computer [ftp://ip:1980](ftp://ip:1980)

window xp promp out a login window
then I type in username:  user2ftp
                     password:   river0

but  it response could not login ftp server as username password specified

[/QUOTE]
 I ever using cygwin on xp,
ftp 69.145.90.142:1980
it response no such address
ftp 69.145.90.142
it response connect refused
assume that 69.145.90.142 is my current ip address
looking for any advancer's help or advice, thanks in advance

---

### Post by frodon on 2005-09-19
[QUOTE=homerj742]Nevermind that last post. I'm able to connect from within the LAN, but NOT outside the LAN. I get a "Could not Retrieve Directory Listing" error. 

But hey, it's better than nothing for now![/QUOTE]You just need to open the port 1980 with your router, if you can connect yourself and not outside the LAN it should be a firewall/router issue.
If you run firestarter think to open the good port or allow the incoming IP of your friend.[QUOTE=fsshl]I ever using cygwin on xp,
ftp 69.145.90.142:1980
it response no such address
ftp 69.145.90.142
it response connect refused
assume that 69.145.90.142 is my current ip address
looking for any advancer's help or advice, thanks in advance[/QUOTE]Look also your firewall(s)/router, trying to connect yourself on the server with the same computer which run the server is the easiest way to debug it. For an external access, the person who try to login your server have to allow his port for ftp and you to.
So my first advice is to try to connect your server with the computer which run the server and also try to login with a ftp client like gftp in order to give me the log informations on login which will help me for support.

---

### Post by fsshl on 2005-09-19
I am using my window xp laptop which connect to internet by wireless 802.11g,  it do not have router, I do not know isp's side, I only know that isp filter all ports on my laptop. I use this laptop to do [ftp://ip:1980](ftp://ip:1980) from ie6 's address
it worked [ftp://ftp.netscape.com](ftp://ftp.netscape.com)
is this laptop should install gftp and setup ftpserver too?

the other computer install and start proftp is connected through cable modem isp is bresnan.net, I guess it probably did not filter anything, at least webserver port 80.  that is one I modify proftpd.conf file. setup user2ftp,  and FTP-share(after I create that FTP-share directory, it really show on my ls command is blue "ftp", not FTP-share)

  welcome advancer's advice, and if possible using experimental commands rather than english concept.

---

### Post by fsshl on 2005-09-19
Hi Frodon, I just run nmap on my ftppro ubuntu linux computer, it showed only port 80 open, others are closed.  hope this help you debug

---

### Post by frodon on 2005-09-19
[QUOTE=fsshl]I am using my window xp laptop which connect to internet by wireless 802.11g,  it do not have router, I do not know isp's side, I only know that isp filter all ports on my laptop. I use this laptop to do [ftp://ip:1980](ftp://ip:1980) from ie6 's address
it worked [ftp://ftp.netscape.com](ftp://ftp.netscape.com)
is this laptop should install gftp and setup ftpserver too?
concept.[/QUOTE]under windows you could use filezilla for exemple, however i guess you run a firewall on your laptop and you must allow ftp protocol on the port 1980.
What i advice you was to use the computer which run proftpd, install gftp on it (if you didn't already install it) and then open gftp on this computer to check if you can login. I advice that because when you try to connect to your ftp server from the same computer which run this server, you will be sure that if you can login your problem come from network/LAN/firewall and not the server itself. It will take you 2 min and will allow to know what kind of problem you have.

---

### Post by frodon on 2005-09-19
[SIZE=6]ProftpTools 1.0 is now available ![/SIZE]
see the misc section of the guide.

---

### Post by homerj742 on 2005-09-19
[QUOTE=frodon][SIZE=6]ProftpTools 1.0 is now available ![/SIZE]
see the misc section of the guide.[/QUOTE]
 What's proftp Tools?

---

### Post by fsshl on 2005-09-19
I tried to install gftp, but it need gftp-text, which depend on gftp-common, then when I tried to install gftp-common, it response it already install, so I can not install gftp (if anyone know how to make it work, please let me know)

to run ftp to access my ftp server on same machine, do you have any command?
I did: ftp localhost
it response connection refuse
I did : ftp localhost:1980
it response unknown host localhost:1980

my laptop using window xp do not have any firewall, 

as last paragraph mentioned, my ubuntulinux computer's isp bresnan.net block all ports except port 80.

looking to hear from advancer's advice again

---

### Post by homerj742 on 2005-09-19
```
Status:	Connecting to aamir.is-a-geek.com:1980 ...
Status:	Connected with aamir.is-a-geek.com:1980. Waiting for welcome message...
Response:	220 you're at home
Command:	USER music
Response:	331 Password required for music.
Command:	PASS *****
Response:	230 welcome !!!
Command:	FEAT
Response:	211-Features:
Response:	211-MDTM
Response:	211-REST STREAM
Response:	211-SIZE
Response:	211 End
Command:	SYST
Response:	215 UNIX Type: L8
Status:	Connected
Status:	Retrieving directory listing...
Command:	PWD
Response:	257 "/" is current directory.
Command:	TYPE A
Response:	200 Type set to A
Command:	PASV
Response:	227 Entering Passive Mode (192,168,0,102,23,173).
Command:	LIST
Error:	Transfer channel can't be opened. Reason: A connection attempt failed because the connected party did not properly respond after a period of time, or established connection failed because connected host has failed to respond.
Error:	Could not retrieve directory listing
Command:	PWD
Error:	Timeout detected!
```

This is what Filezilla gives me when I'm outside my LAN.

---

### Post by frodon on 2005-09-19
**fsshl** you can use your webbrowser on your linux computer to connect yourself on your server. Could you post your proftpd.conf file ?

**homerj742** are you behind a [NAT](http://www.ubuntuforums.org/showthread.php?t=39566&highlight=proftpd+nat)  router, maybe you need to add a [PassivePorts](http://www.proftpd.org/localsite/Userguide/linked/config_ref_PassivePorts.html)  line. How your local network is link to internet, NAT router, connection share ?

---

### Post by homerj742 on 2005-09-19
I'm connected via an old D-Link router. DHCP built right in, and I'm sure a NAT. 

I believe I have port 1980 opened up on it already (forwarding to my FTP server).  

I either have to add a PassivePorts line (and open them up on my router) OR, a MasqueradeAddress line. 

Check out this line: Response:	227 Entering Passive Mode (192,168,0,102,23,173).

That is my INTERNAL IP address for my server (192.168.0.102). 
I should REALLY be seeing my EXTERNAL IP.

---

### Post by homerj742 on 2005-09-19
Added PassivePorts

and MasqueradeAddress ftp.mydomain.com

and it works! Finally! Thanks for all the help Frodon :)

---

### Post by fsshl on 2005-09-19
I tried at my ubuntu linux computer's(the one install and start proftpd) firefox browser, type in 
[ftp://localhost](ftp://localhost)
it response, connection refuse

type in :      
[ftp://localhost:1980](ftp://localhost:1980)
it response, 530 login incorrect


highly appreciate your help again

---

### Post by fsshl on 2005-09-19
my /etc/proftpd.conf

---------------------------------------------------------------------------------------------------------------------------------
# This is a basic ProFTPD configuration file (rename it to 
# 'proftpd.conf' for actual use.  It establishes a single server
# and a single anonymous login.  It assumes that you have a user/group
# "nobody/nogroup" and "ftp" for normal operation and anon.

ServerName			"Debian999"
ServerType			standalone
DeferWelcome			on

MultilineRFC2228		on
DefaultServer			on
ShowSymlinks			off
AllowOverwrite			on
AuthAliasOnly			on
UserAlias sauron user2ftp

TimeoutNoTransfer		600
TimeoutStalled			100
TimeoutIdle			2200

DisplayLogin                    welcome.msg
DisplayFirstChdir               .message
ListOptions                	"-l"

DenyFilter			\*.*/

# Uncomment this if you are using NIS or LDAP to retrieve passwords:
#PersistentPasswd		off

# Uncomment this if you would use TLS module:
#TLSEngine 			on

# Uncomment this if you would use quota module:
#Quotas				on

# Uncomment this if you would use ratio module:
#Ratios				on

# Port 21 is the standard FTP port.
#Port				21

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances			30

# Set the user and group that the server normally runs at.
User				nobody
Group				nogroup

<Directory /*>
# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
  Umask				022  022
# Normally, we want files to be overwriteable.
  AllowOverwrite		on
</Directory>

# A basic anonymous configuration, no upload directories.

# <Anonymous ~ftp>
#   User				ftp
#   Group				nogroup
#   # We want clients to be able to login with "anonymous" as well as "ftp"
#   UserAlias			anonymous ftp
#   # Cosmetic changes, all files belongs to ftp user
#   DirFakeUser	on ftp
#   DirFakeGroup on ftp
# 
#   RequireValidShell		off
# 
#   # Limit the maximum number of anonymous logins
#   MaxClients			10
# 
#   # We want 'welcome.msg' displayed at login, and '.message' displayed
#   # in each newly chdired directory.
#   DisplayLogin			welcome.msg
#   DisplayFirstChdir		.message
# 
#   # Limit WRITE everywhere in the anonymous chroot
#   <Directory *>
#     <Limit WRITE>
#       DenyAll
#     </Limit>
#   </Directory>
# 
#   # Uncomment this if you're brave.
#   # <Directory incoming>
#   #   # Umask 022 is a good standard umask to prevent new files and dirs
#   #   # (second parm) from being group and world writable.
#   #   Umask				022  022
#   #            <Limit READ WRITE>
#   #            DenyAll
#   #            </Limit>
#   #            <Limit STOR>
#   #            AllowAll
#   #            </Limit>
#   # </Directory>
# 
# </Anonymous>

RequireValidShell 		off

TimeoutLogin 20

RootLogin 			off

# It's better for debug to create log files ;)
ExtendedLog 			/var/log/ftp.log
TransferLog 			/var/log/xferlog
SystemLog			/var/log/syslog.log

#DenyFilter			\*.*/

# I don't choose to use /etc/ftpusers file (set inside the users you want to ban, not useful for me)
UseFtpUsers off

# Allow to restart a download
AllowStoreRestart		on

# Port 21 is the standard FTP port, so don't use it for security reasons (choose here the port you want)
Port				1980

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances 8

# Set the user and group that the server normally runs at.
User                  nobody
Group                 nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022	022

PersistentPasswd		off

MaxClients 8
MaxClientsPerHost 8
MaxClientsPerUser 8
MaxHostsPerUser 8

# Display a message after a successful login
AccessGrantMsg "welcome !!!"
# This message is displayed for each access good or not
ServerIdent                  on       "you're at home"

# Set /home/FTP-shared directory as home directory
DefaultRoot /home/ftp

# Lock all the users in home directory, ***** really important *****
DefaultRoot ~

MaxLoginAttempts    5

#VALID LOGINS
<Limit LOGIN>
AllowUser user2ftp
DenyALL
</Limit>

<Directory /home/ftp>
Umask 022 022
AllowOverwrite off
	<Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory>

<Directory /home/ftp/download/*>
Umask 022 022
AllowOverwrite off
	<Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory>

<Directory> /home/ftp/upload/>
Umask 022 022
AllowOverwrite on
	<Limit READ RMD DELE>
      	DenyAll
    	</Limit>

    	<Limit STOR CWD MKD>
      	AllowAll
    	</Limit>
</Directory>

---

### Post by frodon on 2005-09-20
[QUOTE=fsshl]I tried at my ubuntu linux computer's(the one install and start proftpd) firefox browser, type in 
[ftp://localhost](ftp://localhost)
it response, connection refuse
type in :      
[ftp://localhost:1980](ftp://localhost:1980)
it response, 530 login incorrect
highly appreciate your help again[/QUOTE]I already talk about 530 error in this thread, generally you get this error when there is mismatch between path in proftpd.conf and path in the system, or when folder rights are too restrictive compared to proftpd.conf.
So check your ftp directories paths and check the rights you gave for these directories.

---

### Post by synstar on 2005-09-20
Excellent tutorial Fordon & all involved.

I have some strange problems which you may be able to help me with.

Problem one: - When I connect  to the server over the LAN, it works fine, however inside the upload folder the user can make a directory and also delete that directory or any other directory in the uploads folder.  This only occurs via an ftp client such as WS_FTP but not via the Windows browser (permissions denied when deleting).

I have setup the permission following the tutorial.

<Directory> /home/FTP-shared/upload/>
Umask 022 022
AllowOverwrite on
	**<Limit READ RMD DELE>**  <--------- [COLOR=DarkRed]denyall to delete, then why?[/COLOR]
      	DenyAll
    	</Limit>

    	<Limit STOR CWD MKD>
      	AllowAll
    	</Limit>
</Directory>

Problem two: - I can connect to the server via the web using Windows Explorer but it is extremely slow.  (It's quite slow over the LAN to?)  Eventually it fails with permissions to folder error.  Although it does request me for a username and password, therefore a connection was made.

Can anyone help?

---

### Post by frodon on 2005-09-20
You understand really well ! in my guide i disabled the delete operation in upload directory to prevent accidentally erase coming from a user connected on the server. Of course if you don't want this behaviour you could modify  the upload directory section like that : ```
<Directory> /home/FTP-shared/upload/>
Umask 022 022
AllowOverwrite on
<Limit READ> 
DenyAll
</Limit>

<Limit STOR CWD MKD DELE RMD>
AllowAll
</Limit>
</Directory>
```Problem two : For connection problem, it would be dificult to help you without the log of a ftp client (gftp for linux, filezilla for windows for exemple).

---

### Post by fsshl on 2005-09-20
[
So check your ftp directories paths and check the rights you gave for these directories.[/QUOTE]
 so what is that check mean?
do you want me to 
chmod 777 /home
cd /home
chmod 777 ftp
?
or any thing else?

(I tried, but it still show same 530 error)

---

### Post by frodon on 2005-09-20
For the rights just follow the guide and check that you have 775 rights for FTP-shared and download directories, and 777 for upload diectory.
And compare the paths you wrote in proftps.conf in directory with the paths on your computer. For exemple if on your computer the path is /home/user/FTP-shared and you wrote /home/user/Ftp-shared you will get a 530 error on login.

---

### Post by fsshl on 2005-09-20
drwxrwxrwx    5 root     staff        4096 2005-09-18 12:41 home
drwxr-xr-x    2 root     root         4096 2005-09-17 01:28 initrd
lrwxrwxrwx    1 root     root           29 2005-09-17 01:31 initrd.img -> boot/initrd.img-2.6.8.1-3-386
drwxr-xr-x   13 root     root         8192 2005-09-17 00:56 lib
drwxr-xr-x    2 root     root        49152 2005-09-17 01:27 lost+found
drwxr-xr-x    4 root     root         4096 2005-09-17 01:27 media
drwxr-xr-x    2 root     root         4096 2004-09-25 08:07 mnt
drwxr-xr-x    2 root     root         4096 2005-09-17 01:28 opt
dr-xr-xr-x  152 root     root            0 2005-09-17 20:06 proc
drwxr-xr-x   10 root     root         4096 2005-09-18 20:09 root
drwxr-xr-x    2 root     root         4096 2005-09-17 00:45 sbin
drwxr-xr-x    2 root     root         4096 2005-09-17 01:28 srv
drwxr-xr-x    9 root     root            0 2005-09-17 20:06 sys
drwxrwxrwt   11 root     root         4096 2005-09-20 06:25 tmp
drwxr-xr-x   12 root     root         4096 2005-09-17 01:30 usr
drwxr-xr-x   15 root     root         4096 2005-09-17 00:55 var
lrwxrwxrwx    1 root     root           26 2005-09-17 01:31 vmlinuz -> boot/vmlinuz-2.6.8.1-3-386
root@etutor:/ # ls -l home
total 12
drwxr-xr-x   14 fsshl    fsshl        4096 2005-09-20 10:57 fsshl
drwxrwxrwx    4 ftp      nogroup      4096 2005-09-18 15:20 ftp
drwxr-xr-x    2 userftp  userftp      4096 2005-09-18 12:41 userftp
root@etutor:/ # ls -l home/ftp
total 12
drwxr-xr-x    2 root     root         4096 2005-09-18 15:20 download
drwxrwxrwx    2 root     root         4096 2005-09-18 15:20 upload
-rw-r--r--    1 root     root          166 2004-08-13 16:08 welcome.msg
root@etutor:/ #

------------------------------------------------------------------------------------------------------------
my /home   and     my /home/ftp
all be chmod 777
and upload download is also what you mentioned

my proftpd is printed on last page in this thread is
ftpserverroot at /home/ftp
(please reference, to make sure I did not say loosely)

so I am pretty sure they are match

in my desktop as regular user, I found gFTP 2.0.17 from gnome menu

-------------------------------------------
gFTP 2.0.17, Copyright (C) 1998-2003 Brian Masney <masneyb@gftp.org>. If you have any questions, comments, or suggestions about this program, please feel free to email them to me. You can always find out the latest news about gFTP from my website at [http://www.gftp.org/](http://www.gftp.org/)
gFTP comes with ABSOLUTELY NO WARRANTY; for details, see the COPYING file. This is free software, and you are welcome to redistribute it under certain conditions; for details, see the COPYING file
Transfer Files: This feature is not available using this protocol
Looking up localhost
Trying localhost.localdomain:1980
Connected to localhost:1980
220 you're at home
USER user2ftp

331 Password required for user2ftp.
PASS xxxx
530 Login incorrect.
Disconnecting from site localhost
---------------------------------------------------------(this is what I tried)-----------------------------------
hope to see any advice again

---

### Post by frodon on 2005-09-20
OK, your problem is just you use the wrong username. The line **UserAlias sauron userftp** in  proftpd.conf specify an alias for the user name you created, this allow to prevent telnet access. Therefore to connect to the server you must use the alias name, in your proftpd.conf file the alias is **sauron** but you can change it if you want.
So just use the alias name for connection  ;-)

---

### Post by Sophisto on 2005-09-21
Hi Trying to use Profttools. I unpacked it to ~/olof/ProftpTools_v1-0 and added the following line in my bashrc: setenv ProftpTools_dir /home/finn/olof/ProftpTools_v1-0

however when I open a shell I get the following message: bash: setenv: command not found

Any suggestions?

---

### Post by synstar on 2005-09-21
[QUOTE=Sophisto]Hi Trying to use Profttools. I unpacked it to ~/olof/ProftpTools_v1-0 and added the following line in my bashrc: setenv ProftpTools_dir /home/finn/olof/ProftpTools_v1-0

however when I open a shell I get the following message: bash: setenv: command not found

Any suggestions?[/QUOTE]

I get this message above too?

Also, i get this message when i connect over the web...the client is smartFTP

[COLOR=DarkRed]215 UNIX Type: L8
    FEAT
211-Features:
211-MDTM
211-REST STREAM
211-SIZE
211 End
    TYPE I
200 Type set to I
    REST 0
350 Restarting at 0. Send STORE or RETRIEVE to initiate transfer
    PWD
257 "/" is current directory.
    PASV
227 Entering Passive Mode (192,168,0,13,146,40).
    Opening data connection to 192.168.0.13 Port: 37416
    LIST -aL
    Timeout (20s).
    Active Help: [http://www.smartftp.com/support/kb/index.php/74](http://www.smartftp.com/support/kb/index.php/74)
    Client closed the connection.
    Automatic failover of data connection mode from "Passive Mode (PASV)" to "Active Mode (PORT)".[/COLOR]

Looks like some kind of firewall problem but i have the port 1860 open.  I also have tried active port and passive mode on the client.  Im stuck now, so all help is appreciated.  

I am also on IM - [email]charlie126@hotmail.com[/email] 

Thanks

---

### Post by frodon on 2005-09-21
[QUOTE=Sophisto]Hi Trying to use Profttools. I unpacked it to ~/olof/ProftpTools_v1-0 and added the following line in my bashrc: setenv ProftpTools_dir /home/finn/olof/ProftpTools_v1-0

however when I open a shell I get the following message: bash: setenv: command not found

Any suggestions?[/QUOTE]Ok, all my apologies, i use tcsh shell at home and to set environment variable in .bashrc file you must use these 2 lines : ```
ProftpTools_dir=/home/finn/olof/ProftpTools_v1-0
export ProftpTools_dir
```Thanks for feedback about ProftpTools.

**Synstart** for your connection problem, if you have a router look at homerj742's solution. Also to connect to the server you need to open the good port in both computer, the computer which run the server and the computer you use to connect to the server.

---

### Post by Sophisto on 2005-09-21
Ok thanks its working fine now!

Thanks for such a nice guide!

---

### Post by synstar on 2005-09-21
> **Synstart** for your connection problem, if you have a router look at homerj742's solution. Also to connect to the server you need to open the good port in both computer, the computer which run the server and the computer you use to connect to the server.

If i add these two lines onto my config : -

PassivePorts 60000 60100

MasqueradeAddress YourSiteName.com

what port would i use to connect? as its a range...?  Do i still connect to the port i orignally set? mydyndns.org.address:1860?

Thanks, you a star!  O:)

---

### Post by frodon on 2005-09-21
[QUOTE=synstar]If i add these two lines onto my config : -

PassivePorts 60000 60100

MasqueradeAddress YourSiteName.com

what port would i use to connect? as its a range...?  Do i still connect to the port i orignally set? mydyndns.org.address:1860?

Thanks, you a star!  O:)[/QUOTE]Yes you will still connected on the originaly port, passive port range is useful for PSAV mode. You will get more information [here](http://www.proftpd.org/localsite/Userguide/linked/config_ref_PassivePorts.html), and about firewall issues [here](http://www.proftpd.org/localsite/Userguide/linked/x294.html) .

Is it working ?

---

### Post by synstar on 2005-09-21
[QUOTE=frodon]Yes you will still connected on the originaly port, passive port range is useful for PSAV mode. You will get more information [here](http://www.proftpd.org/localsite/Userguide/linked/config_ref_PassivePorts.html), and about firewall issues [here](http://www.proftpd.org/localsite/Userguide/linked/x294.html) .

Is it working ?[/QUOTE]
 Will let you know, at work at the moment..

Thanks for the response.....

---

### Post by synstar on 2005-09-21
OK,

I have managed to get users to connect...(still a little slow).  Within the uploads folder people can upload fine but i don't want people to be able to delete any content.  I cant see how this is possible, i have the following code below: - 

<Directory> /home/ftphome/upload/>
Umask 022 022
AllowOverwrite on
	<Limit  READ>
      	DenyAll
    	</Limit>

    	[COLOR=DarkRed]<Limit STOR CWD MKD DELE RMD> [/COLOR]  <----what should i set here?
      	AllowAll
    	</Limit>
</Directory>


thanks

---

### Post by frodon on 2005-09-21
Set it like that : ```
<Directory> /home/ftphome/upload/>
Umask 022 022
AllowOverwrite on
<Limit READ DELE RMD>
DenyAll
</Limit>

<Limit STOR CWD MKD> 
AllowAll
</Limit>
</Directory>
```

---

### Post by makisupa123 on 2005-09-26
Strange problem...or possibly just an ID10T error on my part...Users can upload but not download.  I have the eact same proftd.config file as in your initial post save the server name and a user.  Check it out:

```
# To really apply changes reload proftpd after modifications.
AllowOverwrite on
AuthAliasOnly on

# Choose here the user alias you want !!!!
UserAlias bro userftp

PassivePorts 60000 60100

ServerName			"MakFTP"
ServerType 			standalone
DeferWelcome			on

MultilineRFC2228 on
DefaultServer			on
ShowSymlinks			off

TimeoutNoTransfer 600
TimeoutStalled 100
TimeoutIdle 2200

DisplayFirstChdir               .message
ListOptions                	"-l"

RequireValidShell 		off

TimeoutLogin 20

RootLogin 			off

# It's better for debug to create log files ;-)
ExtendedLog 			/var/log/ftp.log
TransferLog 			/var/log/xferlog
SystemLog			/var/log/syslog.log

#DenyFilter			\*.*/

# I don't choose to use /etc/ftpusers file (set inside the users you want to ban, not useful for me)
UseFtpUsers off

# Allow to restart a download
AllowStoreRestart		on

# Port 21 is the standard FTP port, so don't use it for security reasons (choose here the port you want)
Port				21

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances 8

# Set the user and group that the server normally runs at.
User                  nobody
Group                 nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022	022

PersistentPasswd		off

MaxClients 8
MaxClientsPerHost 8
MaxClientsPerUser 8
MaxHostsPerUser 8

# Display a message after a successful login
AccessGrantMsg "welcome !!!"
# This message is displayed for each access good or not
ServerIdent                  on       "you're at home"

# Set /home/FTP-shared directory as home directory
DefaultRoot /home/FTP-shared

# Lock all the users in home directory, ***** really important *****
DefaultRoot ~

MaxLoginAttempts    5

#VALID LOGINS
<Limit LOGIN>
AllowUser userftp bro
DenyALL
</Limit>

<Directory /home/FTP-shared>
Umask 022 022
AllowOverwrite off
	<Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory>

<Directory /home/FTP-shared/download/*>
Umask 022 022
AllowOverwrite off
	<Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory>

<Directory> /home/FTP-shared/upload/>
Umask 022 022
AllowOverwrite on
	<Limit READ RMD DELE>
      	DenyAll
    	</Limit>

    	<Limit STOR CWD MKD>
      	AllowAll
    	</Limit>
</Directory>
```

anytime you attempt to download you get 550...etc. :Permission denied.  I know I'm missing something entirely obvious...

Thanks,

/mak

---

### Post by frodon on 2005-09-27
As the error message tell it, you have a permission problem, generally it's not the proftpd.conf fault. Check that you have well followed the end of the section **2** of the guide. Also if you can't download only maybe the problem come from the rights you set for your partition in fstab, can you write on your partition as a simple user ?

---

### Post by Sophisto on 2005-09-27
Hi! Thanks again for a nice guide! 

I was just wondering if it would be possible to set up various accounts for different people for example one that has access to everything. I think that should just be a matter of mounting all partitions to one user..so i suppose my question is how do you add more than one user? 

Thanks

---

### Post by makisupa123 on 2005-09-27
Frodon,

Thanks for your reply.  Don't know how those files got moved over to FTP-shared folder but the permissions (several levels deep) were seriously jacked.  

Thanks,

/mak

---

### Post by frodon on 2005-09-27
[QUOTE=Sophisto]Hi! Thanks again for a nice guide! 

I was just wondering if it would be possible to set up various accounts for different people for example one that has access to everything. I think that should just be a matter of mounting all partitions to one user..so i suppose my question is how do you add more than one user? 

Thanks[/QUOTE]The only interest to set several users, is to see with ftptop command which of your friend is connected and my guide allow 8 connections with the same user so it's not really useful to create another user.
However it's your choice and i will tell you how to add a new user who will be allowed to access your server.
First create your new user with /home/username/FTP-shared as home directory : ```
sudo useradd new_user -p your_password -d /home/FTP-shared -s /bin/false
```and add the following line
 in proftpd.conf : ```
UserAlias new_alias new_user
```and then modify the limit login section like that : ```
#VALID LOGINS
<Limit LOGIN>
AllowUser userftp
AllowUser new_user
DenyALL
</Limit>
```
Hope it works quickly ;)

---

### Post by Sophisto on 2005-09-27
Ok... What I actually wanted was to be able to access my computer away from home... but Ive managed that now.. by just adding my own username to the proftp.conf file.... However I was wondering if you guys think that is too dangerous?

Finn

---

### Post by frodon on 2005-09-27
I think what you want is a remote desktop, and it's not really secure. But if you just want to create a user for your use only which will see one or more directories where you have mounted in your partitions, i can't answer right now because i have to make some tests at home but it's possible.
Let me know if i understand well your need.

EDIT : ok i will have a look to a secure way to do that, if you just want to see your data partitions i would use another way. When you login with your own user, do you see (or can you see) your linux partition ? if yes it might be dangerous.

---

### Post by Sophisto on 2005-09-27
A remote desktop -  yes thats what I wanted. Now when I log on (with my own username) I can see my home folder (not my linux partition). 

I did first try with just adding a new user and mount the necessary partitions. That worked fine but I was never able to upload things and I think thats due to the fact that most of my files are assigned to myself and not the user I created and I dont want to change the mod for all the files I have on my harddrive...

---

### Post by frodon on 2005-09-27
A remote desktop is something different that you talk about, you seem to only want to access your data partition through the ftp server.
So let me come back home (in 4-5 h) and i will give you a secure way to do that, basicly i would create as many directories as partitions i have in FTP-shared directory then give 777 rights for these directories and finally allow only a specific user to see these directories.
I think you understand now the advantage to keep all the ftp stuff in FTP-shared, it's clean and secure.

---

### Post by Sophisto on 2005-09-27
Ok.. sounds good... im not really sure how to do what you just explain with allowing specific users to see different directories.. Anyway Ill let you get back to work (or whatever you are up to) and talk to you later when you get back...

Thanks a lot

/Finn

---

### Post by homerj742 on 2005-09-27
I have a NEW issue :lol

ok here's the deal. I'm able to upload files into my upload directory, but some people cannot upload. They get a timeout, or no proper permissions error.

So why would some people be able to upload and some people cannot? (lets count out end user error haha)

Does it have something to do with active and passive ports? Is there a way I can have ALL transfers be done with the active port? In my case 1980?

---

### Post by homerj742 on 2005-09-27
Also I'd like to mention I only have one passive port open. (My router is a pain, I cannot open a range of ports, I have to open them one at a time!) could this also be the problem?

---

### Post by frodon on 2005-09-27
Strange problem **homer742** ! In the guide there is some lines which set the maximum number of users at 8, you could have some problems if more than 8 persons want to connect to your server at the same time, if it's the case just increase this number in the proftpd.conf file, also the proftpd [forum]("http://forums.proftpd.org/phpBB2/search.php?mode=results") is really helpful.

Sorry, no more ideas for the moment :???:

---

### Post by homerj742 on 2005-09-27
You know I always appreciate the input Frodon! 

I will check the config file, I think it's set to 8, but believe me, so few people know about it, I'm lucky if it gets one hit a day.

That's why I was thinking maybe it's a passive ports issue, since I only allowed one port to be used for passive mode. (I can't open up that many ports on the router lol).

OR, it could be a different issue all together, something on the end user's side.

---

### Post by fsshl on 2005-09-27
[QUOTE=frodon]OK, your problem is just you use the wrong username. The line **UserAlias sauron userftp** in  proftpd.conf specify an alias for the user name you created, this allow to prevent telnet access. Therefore to connect to the server you must use the alias name, in your proftpd.conf file the alias is **sauron** but you can change it if you want.
So just use the alias name for connection  ;-)[/QUOTE]
----------------------------------------------------------------------------------------------------------------------------
thanks your reply, but after I install new kernel 2.6.12-9
it keep reponse login incorrect
I used "sauron" "river0", my proftpd.conf only modify from user2ftp back to yours userftp
what may go wrong?
--------------------------------------------------(in the test, from same machine using gftp, it worked--------------------
------it worked from outside's xp ie6 url address too.   I do not know why at beginning of install of both newkernel and new setup ftpserver is not work. but I did not lieing---------------------------------------------------------------------------------------------------

---

### Post by frodon on 2005-09-27
[QUOTE=Sophisto]Ok.. sounds good... im not really sure how to do what you just explain with allowing specific users to see different directories.. Anyway Ill let you get back to work (or whatever you are up to) and talk to you later when you get back...

Thanks a lot

/Finn[/QUOTE]Ok i don't found a good way to hide a directories so follow your way and just create in your home directory a specific directory to mount in your partition and give 777 rights to this directory, i think you will be able to upload.
Check that you can't go out your home directory, if not i think it's not so dangerous except if someone get your username and your password.

---

### Post by Sophisto on 2005-09-28
Ok... have don that now.. working fine.. thanks for looking into it!

/Finn

---

### Post by frodon on 2005-09-28
Cool !
Also i think i have found a good way now to hide files and i will test it tonight, i think it might be better to not use your personnal user and home directory. Are you still interested ?

Thank you for your really interesting question.

---

### Post by Sophisto on 2005-09-28
Yes you are probably right. What I did was just to create a new user in the same way as you described in your guide.. and then mount the necessary partitions to that user's home... But yes if you could find out a way to hide files so that only some users would be able to access them Id be interested to know how to do that!

/Finn

---

### Post by homerj742 on 2005-10-04
Ok, I have IP Check installed on my Kubuntu machine. However, whenever the IP changes, my proftpd requires a restart in order to resolve the new IP address. 

Is this normal? Is there anyway where I don't have to manually restart proftpd?

---

### Post by frodon on 2005-10-05
Sorry to ask that but what is "IP check" ?

---

### Post by homerj742 on 2005-10-05
It's like DynDNS client! But for Kubuntu, it's in the kynaptic!

---

### Post by lreyes6 on 2005-10-07
Ok very nice guide... now one question... how i undo all if i don't need it any more? jeje 

thanks

---

### Post by renebs on 2005-10-07
Hi,

Your howto is really good, it really helped.  

I've followed it trough but I still can't have access to my computer. I try to login whti gFTP like you recommended for homerj742, If I can remember correctly. 

My gFTP log is this:

"Trying [COLOR="#ff0000"]myip:myport[/COLOR]
Cannot connect to [COLOR="Red"]myip[/COLOR]: Connection refused"

(where I've changed my real ip and port used).

I know it must be a problem NOT with the configuration you give but with the FIREWALL. Any way. I spent a few hours already looking over the forum and google, call me stupid but I haven't been able to find the config for that. 

I have the firestarter running. I tried it with it stoped. Same result.

Any help you could provide?

---

### Post by linkunderscore on 2005-10-07
220 you're at home
USER link

331 Password required for link.
PASS xxxx
530 Login incorrect.

:( I can't login to my FTP :( 

How can i fix this?

---

### Post by frodon on 2005-10-08
[QUOTE=lreyes6]Ok very nice guide... now one question... how i undo all if i don't need it any more? jeje 

thanks[/QUOTE]Uninstall proftpd with synaptic, delete the user you have created in System>Administration>User and group, and delete the repertories you created with the **sudo rm** command.[QUOTE=renebs]I know it must be a problem NOT with the configuration you give but with the FIREWALL. Any way. I spent a few hours already looking over the forum and google, call me stupid but I haven't been able to find the config for that. 

I have the firestarter running. I tried it with it stoped. Same result.

Any help you could provide?[/QUOTE]Ok don't worry you're not alone, in order to help you i will need more details about your problem, use "atach files" button in your reply to give me your proftpd.conf file, then give me the exact log of gFTP and what you enter exactly in the fields. As usual check the rights you gave for the repertories but it not seems to be your problem.
So try to be as precise as possible in your reply.[QUOTE=linkunderscore]220 you're at home
USER link

331 Password required for link.
PASS xxxx
530 Login incorrect.

:( I can't login to my FTP :( 

How can i fix this?[/QUOTE]Ok, 530 error is the most common problem, it means that you probably have a configuration problem. Read the whole thread first because we already talked about this error and then if you still have some configurations problem, as i say to renebs, atach your proftpd.conf in the reply and give me the more details you can. Also think to change your password just to check if it's not the problem.

---

### Post by renebs on 2005-10-08
Hi Frodon,

THanks for your help. My proftpd.conf and the log gftp created are attached. 
I've tried with the IP and nameserver.

Have to tell you that my gftp is crashing all the time (it fails and locks, have to xkill it and try again :-( ).

I have uploaded a screenshot to show what I have filled in the fields (namely, my ip, my port 1991, my user: userftp). 

Thansk

---

### Post by frodon on 2005-10-08
Hum ..., i made some tests and it seems that your server is not running and it's why you get this error message.
Therefore if i'm right there is 2 possibilities :
1 - You didn't start your server, start it with this command : ```
sudo /etc/init.d/proftpd start
```2 - You have a syntax error in your proftpd.conf file.The server start running only if your proftpd.conf file has no syntax errors. So check the syntax of proftpd.conf : ```
sudo proftpd -td5
```

---

### Post by renebs on 2005-10-08
Just remembered I am using Ubuntu 5.10, does it make much difference? 


[QUOTE=frodon]Hum ..., i made some tests and it seems that your server is not running and it's why you get this error message.
[/QUOTE]

Hi Frodon, again thanks for the patience. 

I've executed the commands you suggested, take a look to see the output:


```
root@renebs:/home/renebs# /etc/init.d/proftpd start
ProFTPd is started from inetd/xinetd.
```

Don't know what that means, does it means that it is runing? If not can I start it withou rebooting the system? 

Anyway I have ProftpTools installed I've run the command, here is the output:

```
renebs@renebs:~$ ProftpTools
Start
ProFTPd is started from inetd/xinetd.
[\CODE}

After that I've tried again to connect, received the same output "connection refused".

[CODE]root@renebs:/home/renebs# proftpd -td5
Checking syntax of configuration file
 - mod_tls/2.0.7: using OpenSSL 0.9.7g 11 Apr 2005
 - parsing '/etc/proftpd.conf' configuration
 - Compiling deny regex '\*.*/'.
 - Allocated deny regex at location 0x814dc68.
 - <Directory /home/ftp-shared>: adding section for resolved path 
'/home/ftp-shared'
 - <Directory /home/ftp-shared/download/*>: adding section for resolved 
path '/home/ftp-shared/download/*'
 - <Directory /home/ftp-shared/upload/>: adding section for resolved 
path '/home/ftp-shared/upload'
renebs.impa.br - 
renebs.impa.br - Config for Debian:
renebs.impa.br - /home/ftp-shared
renebs.impa.br -  /home/ftp-shared/download/*
renebs.impa.br -   Limit
renebs.impa.br -    DenyAll
renebs.impa.br -   Umask
renebs.impa.br -   DirUmask
renebs.impa.br -   AllowOverwrite
renebs.impa.br -   ShowSymlinks
renebs.impa.br -   DisplayLogin
renebs.impa.br -   DisplayFirstChdir
renebs.impa.br -   ListOptions
renebs.impa.br -   TransferLog
renebs.impa.br -   DenyFilter
renebs.impa.br -   AllowStoreRestart
renebs.impa.br -   MaxClients
renebs.impa.br -   MaxClientsPerHost
renebs.impa.br -   MaxClientsPerUser
renebs.impa.br -   MaxHostsPerUser
renebs.impa.br -   AccessGrantMsg
renebs.impa.br -  /home/ftp-shared/upload
renebs.impa.br -   Limit
renebs.impa.br -    AllowAll
renebs.impa.br -   Limit
renebs.impa.br -    DenyAll
renebs.impa.br -   Umask
renebs.impa.br -   DirUmask
renebs.impa.br -   AllowOverwrite
renebs.impa.br -   ShowSymlinks
renebs.impa.br -   DisplayLogin
renebs.impa.br -   DisplayFirstChdir
renebs.impa.br -   ListOptions
renebs.impa.br -   TransferLog
renebs.impa.br -   DenyFilter
renebs.impa.br -   AllowStoreRestart
renebs.impa.br -   MaxClients
renebs.impa.br -   MaxClientsPerHost
renebs.impa.br -   MaxClientsPerUser
renebs.impa.br -   MaxHostsPerUser
renebs.impa.br -   AccessGrantMsg
renebs.impa.br -  Limit
renebs.impa.br -   DenyAll
renebs.impa.br -  Umask
renebs.impa.br -  DirUmask
renebs.impa.br -  AllowOverwrite
renebs.impa.br -  ShowSymlinks
renebs.impa.br -  DisplayLogin
renebs.impa.br -  DisplayFirstChdir
renebs.impa.br -  ListOptions
renebs.impa.br -  TransferLog
renebs.impa.br -  DenyFilter
renebs.impa.br -  AllowStoreRestart
renebs.impa.br -  MaxClients
renebs.impa.br -  MaxClientsPerHost
renebs.impa.br -  MaxClientsPerUser
renebs.impa.br -  MaxHostsPerUser
renebs.impa.br -  AccessGrantMsg
renebs.impa.br - Limit
renebs.impa.br -  AllowUser
renebs.impa.br -  DenyAll
renebs.impa.br - DeferWelcome
renebs.impa.br - DefaultServer
renebs.impa.br - ShowSymlinks
renebs.impa.br - TimeoutNoTransfer
renebs.impa.br - TimeoutStalled
renebs.impa.br - TimeoutIdle
renebs.impa.br - DisplayLogin
renebs.impa.br - DisplayFirstChdir
renebs.impa.br - ListOptions
renebs.impa.br - ExtendedLog
renebs.impa.br - TransferLog
renebs.impa.br - DenyFilter
renebs.impa.br - DefaultRoot
renebs.impa.br - IdentLookups
renebs.impa.br - ServerIdent
renebs.impa.br - AllowStoreRestart
renebs.impa.br - UserID
renebs.impa.br - UserName
renebs.impa.br - GroupID
renebs.impa.br - GroupName
renebs.impa.br - Umask
renebs.impa.br - DirUmask
renebs.impa.br - MaxClients
renebs.impa.br - MaxClientsPerHost
renebs.impa.br - MaxClientsPerUser
renebs.impa.br - MaxHostsPerUser
renebs.impa.br - AccessGrantMsg
renebs.impa.br - ServerIdent
renebs.impa.br - DefaultRoot
renebs.impa.br - DefaultRoot
renebs.impa.br - MaxLoginAttempts
renebs.impa.br - AllowOverwrite
Syntax check complete.
root@renebs:/home/renebs# 

```

Thanks for the help.

---

### Post by frodon on 2005-10-08
I saw that you set **inetd** for **ServerType** parameter in your proftpd.conf file and it should be the problem, replace **inetd** by **standalone**.
Another advice, i saw that you don't use alias name as i describe it in the guide, it's ok but the useralias way prevents telnet access. However you can live without that, up to you.

---

### Post by renebs on 2005-10-10
Frodon, Thanks very much,

It works now. I've changed the inetd for standalone and added the useralias as you recomended. 

Thank you a LOT  for the manual.

---

### Post by giopas on 2005-10-18
Hi!

I'm trying to set proftpd, but I had some problems:

1. I would like to share a folder placed in an other non-default directory (/media/hda5/holiday_pictures) with some friends of mine, but I don't want to leave anonymous access. So, I need to create an ftp account (i.e., "friend") WITH password (i.e., "pass") in order to give them just that folder.
For doing it, it think I just have to create the new account like there is in the first page of that 3d. Is that right, or there are errors doin'it ('couse I read in the prevous pages some corrections, but I'm not sure that the header post has been updated)

2. I would like to share DIFFERENT others folders, in particulary, some folders inside my EXTERNAL USB ARCHIVE.
This archive is automatically detected by Ubuntu at startup or when I decide to plug it, for this reason it's not defined in the fstab file.
The problem is that, even if I decide to set just a folder of that hd archive like ftphome, I can't start the ftp session, 'couse proftpd "can't set home directory".
What have I to do? Is it possible to share these folders as well? Is that possible to share different folders in the same time?

3. I can't find anywhere proftpdtools.... where can I find it?

thnx a lot: I really need your help!

enjoy, ;)
giopas

---

### Post by frodon on 2005-10-19
The header post is up to date, however i gave some support for peoples who want specific configurations but you're not concerned.

1 - The HOWTO seems to fit to your needs so just follow it.

2 - The idea of this howto is to create a secure ftp space thanks to a specific home directory, and then you have 2 choice :
You can copy in the download directory what you want to share or mount inside the directory you want (even your /media/hda5/holiday_pictures directory) see misc section for that.
The idea is not to share directly the directory you want but mount this directory in the secure ftp space (FTP-shared home directory in the howto), the result is the same but you do it in a secure way because you're sure to lock all users in the FTP-shared directory.

3 - proftpdtools is a scripts i wrote with a GUI to mount directories in a easy way (/media/hda5/holiday_pictures in /home/FTP-shared/download in your case ;-) ) and start/restart proftpd and also other stuff.  You can download it at the bottom of the header post.

Feel free to post some questions about proftpdtools if you don't understand how to use it or if you need more help.

---

### Post by giopas on 2005-10-19
Thnx a lot: I think I fixed most of the problems I had with your help! :p 

Unfortunately, I have still someone of 'em:

1. I can't access in the ftp directory with the created user:
```
useradd amici -p amici -d /home/FTP-shared -s /bin/false
```
the login is correct: "amici", but the password is not accepted "amici". Why? I've also tryed to change the password in system -> users -> etc.. but without success.

2. I decided to use the same directories in your example, but I've a problem launching ProftpdTools:
```
mv ProftpTools /usr/bin/
```
after that, I put the ProftpTools directory in /home/giopas/ and changed:
```
gedit /home/giopas/.bashrc
```
with the following line:
```
ProftpTools_dir=/home/giopas/ProftpTools_v1-0/
export ProftpTools_dir
```
after that if I write in the shell "ProftpTools", nothing happened...
Obviously, I've zenity installed...

I'm sure that I did some mistakes, but I can't figure it! :( 

enjoy, ;)
giopas

---

### Post by frodon on 2005-10-19
1 - Just try another password in the System>Administration>USER&group window and it should work, sometimes when you create the user with command line the password is not reconize, i don't know why.

2 - Maybe the file are not executable so execute these commands : ```
sudo chmod +x /usr/bin/ProftpTools
sudo chmod +x /home/giopas/ProftpTools_v1-0/*
```
3 - Don't forget to read the whole thread there is already a lot of support. Also as i always say : test your server yourself with gFTP or any other FTP client then if it doesn't work give me the gFTP log informations and use attached file parameter to give me your proftpd.conf file, because without that i will not be able to help you.

Feel free to post as many questions as you want but read the whole thread before ;)

---

### Post by SlugO on 2005-10-19
I know you've covered the 530 error (login incorrect) a couple of times in this thread but I just can't get rid of it. I have a DSL and no routers that I know of. Although IP sniffing web pages seem to get my IP wrong... I've tried to setup proftpd (and also vsftpd) a couple of times with no luck. My configuration file is exactly the same as in your example at the moment.

Here's what gFTP says:```
Connected to 192.168.11.2:1980
220 you're at home
USER sauron

331 Password required for sauron.
PASS xxxx
530 Login incorrect.
Disconnecting from site 192.168.11.2
```

The password is correct, I've added the user and I've setup directory permissions with straight copy-paste from the example. Also installed (and now uninstalled) Firestarter and opened gate 1980. And still no luck :???:

Any ideas?

---

### Post by giopas on 2005-10-19
Hi Frodon... yeah, I couldn't figure out the problem.

Of course I read all precedent posts, but... ok, I ask you to check the error in my config files ...please!! :( 

the problems now ('couse I couldn't do the next step: automatically mount some others fat32 directories in the download folders) are:

1. login access:
I've manually changed the pass ("amici") to the aliasuser account ("amici"); I've tryed to reboot; I've of course restarted proftpd, but it doesn't works.

2. PrftpdTools launching:
I really can't understand where is the problem... :confused: 

I've attached the files, hope you can kindly help me. Thnx a bunch!

enjoy, ;)
giopas

---

### Post by frodon on 2005-10-20
[QUOTE=SlugO]The password is correct, I've added the user and I've setup directory permissions with straight copy-paste from the example. Also installed (and now uninstalled) Firestarter and opened gate 1980. And still no luck :???:

Any ideas?[/QUOTE]Well, if you really sure that your password is good (you test it with other aplication or login gnome with it) it should be a really stupid thing, like a difference between the real path of the directory and the path you set in proftpd.conf. For exemple if you've created your directory and called it fTP-shared instead of FTP-shared you get 530 error. Search for small mistakes like that, you could also send me your proftpd.conf but if you just copied the one i gave in the guide i won't need it.

Good luck and don't hesitate to post ;)

---

### Post by frodon on 2005-10-20
[QUOTE=giopas]Hi Frodon... yeah, I couldn't figure out the problem.

Of course I read all precedent posts, but... ok, I ask you to check the error in my config files ...please!! :( 

the problems now ('couse I couldn't do the next step: automatically mount some others fat32 directories in the download folders) are:

1. login access:
I've manually changed the pass ("amici") to the aliasuser account ("amici"); I've tryed to reboot; I've of course restarted proftpd, but it doesn't works.

2. PrftpdTools launching:
I really can't understand where is the problem... :confused: 

I've attached the files, hope you can kindly help me. Thnx a bunch!

enjoy, ;)
giopas[/QUOTE]Ok, seeing your configuration file i have some questions :
1 - The user you created should be **userftp** and the alias name you chose is amici. I confirm that if the user you created is called amici it's not good, if it's the case delete this user and create the **usertfp** user as specified in the guide.

2 - First of all, test your server yourself with gftp and give me the log infos if doesn't work. I think it's easier to take the problems one by one ;)

---

### Post by giopas on 2005-10-20
thnx again Frodon! :)

I've tryed to change the username alias from "amici" to "sauron", but nothing changed testing the whole with gftp (what of course I've done even before).
I'm becoming your nightmare! :D

Ok I write you step by step the procedure I followed, in order to let you understand how... I'm stupid. ;)

1. >  Install proftpd with synaptic or with this command: ```
sudo apt-get install proftpd
```
of course done.

2. > Add this line in /etc/shells file (sudo gedit /etc/shells to open the file) : ```
/bin/false
```
done, as you see in the /etc/shells file I attached you

3. >  Create a /home/FTP-shared directory :```
cd /home
sudo mkdir FTP-shared
```
done

4. >  Create a user named userftp which will be used only for ftp access. This user don't need a valid shell (more secure) therefore select /bin/false shell for userftp and /home/FTP-shared as home directory (property button in user and group window).
To make this section clearer, i give you the equivalent command line to create the user :```
sudo useradd userftp -p your_password -d /home/FTP-shared -s /bin/false
```
following your example I did:
```
sudo useradd userftp -p amici -d /home/FTP-shared -s /bin/false
```
so, the password should be "amici" (that it's not my root password)

5. > In FTP-shared directory create a download and an upload directory: ```
cd /home/FTP-shared/
sudo mkdir download
sudo mkdir upload
```
Now we have to set the good permissions for these directories :
```
cd /home
sudo chmod 755 FTP-shared
cd FTP-shared
sudo chmod 755 download
sudo chmod 777 upload
```
done

6. > OK, now go to the proftpd configuration file :
```
sudo gedit /etc/proftpd.conf
```
done. I attach my proftpd.conf file, that should be tha same as yours.

7. > Ok you have done proftpd configuration. Your server is on port 1980 (in this exemple) and the access parameters are
user : sauron
password : the one you've set for userftp
so, my login should be: "sauron" and the password: "amici".

8. I've started the demon with:
```
sudo /etc/init.d/proftpd start
```

9. I checked if the syntax is correct with:
```
sudo proftpd -td5
```
and everything seems good.

10. then, I downloaded your proftpdtools, unrared, put the whole folder in /giopas/home but putting the ProftpTools file in /usr/bin/.

11. I edited the file .bashrc with exactely the following line (as you looked in the precedent post attachment:
[coded]ProftpTools_dir=/home/giopas/ProftpTools_v1-0
export ProftpTools_dir[/code]
but I didn't understand what does it meen:
>  file in order to specify what is the ProftpTools directory path, YOU MUST REMOVE THE "/" CHARACTER at the end of the path
or maybe, it's exactelly what I did ;)

12. I know that I got zenity installed on my pc and it is up to date.

Ok, everything seems (to me) done as you wrote, but when I open gftp, I write my ip (the external one or the internal: 127.0.0.1), I enter "souron" like login, and "amici" like password using the 1980 port, gftp says:
```
Ricerca di 1.81.202.97
Tentativo di connessione a 1.81.202.97:1980
Connesso a 1.81.202.97:1980
220 you're at home
USER sauron

331 Password required for sauron.
PASS xxxx
530 Login incorrect.
Disconnessione dal sito 1.81.202.97
```
yeah, the ip it's a nat ip, but it's not a problem 'couse I just need to use this ftp inside the nat (created by my provider).

what else? I attach the setting of the ftpuser I created.

Thnx really a lot!!!

---

### Post by frodon on 2005-10-20
Really strange all seems good, if you tested to access with the same computer which run the server the problem is not due to your nat.
Try to change password, just to test that's not the problem. the ifconfig command will show your IP.
You could try to get more debug infos : [http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-Debugging.html](http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-Debugging.html)
and also have a look in the proftpd forum with "530 error" keyword: [http://forums.proftpd.org/phpBB2/search.php?mode=results](http://forums.proftpd.org/phpBB2/search.php?mode=results)

---

### Post by SlugO on 2005-10-20
Hmm, this is strange... I can't log in with the new user```
janne@mylly:~$ sudo useradd userftp -p [my pass] -d /home/FTP-shared -s /bin/false
janne@mylly:~$ su userftp
Password:
su: Authentication failure
Sorry.

```

Also tried adding userftp with the graphical application but still couldn't log in.
What's wrong here...?

---

### Post by giopas on 2005-10-21
I Frodon!

yesterday, I went home and I tryed again, just for chance, to login with gftp in local, and it worked!

I dont know what changed, but... now it works... even the folder mounting!!! :KS

Thnx a lot, really!!

enjoy, ;)
giopas

---

### Post by frodon on 2005-10-21
[QUOTE=SlugO]Hmm, this is strange... I can't log in with the new user```
janne@mylly:~$ sudo useradd userftp -p [my pass] -d /home/FTP-shared -s /bin/false
janne@mylly:~$ su userftp
Password:
su: Authentication failure
Sorry.

```

Also tried adding userftp with the graphical application but still couldn't log in.
What's wrong here...?[/QUOTE]Your problem seems to be the user creation, try to delete and create again the user with the graphical application. 
I think it's the only problem you have, however i don't think that you did something wrong creating the user ... it's strange.

---

### Post by SlugO on 2005-10-21
Nevermind, I got it working simply by doing sudo passwd userftp :D

---

### Post by giopas on 2005-10-21
Frodon, I've just the last problem (I didn't think it would be useful for other readers to split my "case problem" in 2 different 3ds):

I configured the automount system of ProtpdTools, and it perfectely works with "normal" folders (that from an other fat32 partition of the same internal hd). But when I try to automount folders from an external hd (always in fat32), the automount works properely (in fact if I go to /home/FTP-Shared/Download/ I can see that folders and open'em), but from gftp I obtain the following message:
```
CWD /download/Video

550 /download/Video: Permission denied
```
I think it's a matter of reading permission from external boxes, 'couse in the past (before reading your guide) I'd tryed to configure a folder placed in that external box like "home" for anonymous ftp hosts but without success.

The created folder in /home/FTP-Shared/Download/ are: "777" the 2 "normal folders", and 700 the other 2 folders from the usb hard drive. I tryed to change the permission with chmod, but I couldn't. What do you think should I have to do?

thnx again, and again, and again :( 

giopas

---

### Post by frodon on 2005-10-21
Ok, you need 755 (minimum) rights for your external usb drive, chmod don't work because rights for external drives are set by the mount command as far as i know.
So my question is what mount command did you use to mount your external drive partition ?
Maybe you use a line in your fstab file to mount it, if it's the case attach your fstab file.

---

### Post by SlugO on 2005-10-21
Argh! Now I can connect to the server but my friend can't :???:
He just gets a Connection timed out with his ftp program...

What could be causing this? :confused:

---

### Post by frodon on 2005-10-21
It's a firewall problem i think, if you use firestarter, open the port 1980 or allow your friend IP.
So tell me if you run a firewall or if you have router.

---

### Post by SlugO on 2005-10-21
Didn't use a firewall but just installed Firestarter. Added the port and my friend's IP to policy but didn't help.
I don't think that I have a router. Just a normal DSL modem and a WiFi station.. :???:

Actually I had the same kind of problem when I made a server in Windows with Filezilla, others couldn't connect.

---

### Post by giopas on 2005-10-21
My external is automatically mounted by the system at boot, or whenever I plug it. So, maybe the problem is that ubuntu automatically mount usb devices with 700 permission set.

What's your suggest then? :confused: 

tnx,
giopas

---

### Post by giopas on 2005-10-21
slugo, maybe you have to forward the 1980 port through your wi-fi station (that is a router as well... just.... wire-less ;) ).

So, you have to take care to allow the target port even through the firewall, even through the wireless station.

enjoy, ;)
giopas

ps: maybe you've even to take a look if your privider block some ports by default that you have manually unblock (like the usual p2p ports...)

---

### Post by frodon on 2005-10-21
[QUOTE=giopas]My external is automatically mounted by the system at boot, or whenever I plug it. So, maybe the problem is that ubuntu automatically mount usb devices with 700 permission set.

What's your suggest then? :confused: 

tnx,
giopas[/QUOTE]Try to run these commands : ```
sudo umount parition_path
sudo mount -o rw /dev/usb1 destination_path
```Maybe you plugged your USB drive in usb2 or usb3 port so modify the second line corresponding to the usb port you use. I'm not sure it works (i never used a USB drive on my computer)

---

### Post by giopas on 2005-10-21
I've written the External archive in my fstab:
```
/dev/sda5	/media/EXTERNAL		vfat		umask=000		0	0
```
but it still doesn't work.

So, the problem looks like the same as I posted [here](http://www.ubuntuforums.org/showthread.php?t=66467&highlight=fstab+external+usb). This is not just my own problem, as we can see [here](http://www.ubuntuforums.org/showthread.php?t=60765&highlight=fstab+external+usb), and that meens that is not possible (or is quite difficoult) to enter from remote (ftp, samba or apache) inside external usb archive.

The strange thing is that I've no problem at all sharing my external usb files with amule... so the problem is definitely about permissions...

is that possible to set a 770 permission to vfat external hard drive? :???: 

thnx

giopas

---

### Post by SlugO on 2005-10-21
You were right Giopas, I had to also configure WiFi since it's a router. Didn't realize this before...

I changed the computer's IP to static and forwarded the port 1980. Also added PassivePorts and MasqueradeAddress (only noticed it now). Still doesn't work though :(

Should I masquerade my address as the same one that my WiFi router has or just random? And is it okay to choose passiveports as 1980-3000 or do I have to use that example range of over 60000? And do I also have to forward all of these ports from my router? And what port should I tell a client to connect to? :confused: 

Who ever knew FTP could be so simple...

---

### Post by giopas on 2005-10-21
Wifi forwarding setting is always a problem...

I don't have a wireless connection at the moment, but I think it'is like a common router: you have just to allow the port you chose or, if there is, just add your ip address to the DMZ (demilitary zone), so that you don't have to became crazy looking for special settings...

However, take in mind that your wireless router, changing your ip, don't let others connect to you just typing your external (public) ip...
I've noticed that in the first post Frodon has given to us some solutions, try to follow'em.

enjoy, ;)
giopas

---

### Post by tspec on 2005-10-27
Hi Frodon, 
Thanks for this guide, it's very helpful. I myself have also been getting these 530 login errors and couldn't for the life of me figure out why. After a while I've worked out that work you need to do in order to fix the 530 login error  (well at least it worked for me... maybe it'll work for others) was to type in sudo passwd "username" - press enter then type "existing_password". For some reason that suddenly allowed all accounts i did that for to be able to log in via FTP.

---

### Post by frodon on 2005-10-27
ho, thanks a lot !
Maybe the sudo passwd command make the password able to handle sudo commands, if it's the case i wouldn't advice it for security reasons. Could you check that the password you use for ftp doesn't work with sudo commands.

I appreciate a lot your feedback tspec :D

---

### Post by tspec on 2005-10-27
hmm you lost me there :) actually i messed up my last post a bit, i've fixed it though. It's actually sudo passwd userftp (then press enter), it then prompts you for a new password for userftp, just type your existing one in then reconfirm it... after I did that everything started working. I had the username and password correct before I did this but for some reason it just wouldn't work until I ran the sudo passwd command to basically reconfirm the password. Anyway I hope that helps at least a few people out :)

---

### Post by frodon on 2005-10-27
lol, OK i understand what you did and yes this will help because many persons get this error, so if it solve the problem for some other persons i will add a line about it in the guide.
Again thank you, posts like that help a lot for support.

---

### Post by Dany on 2005-11-10
Thanx alot for a great guide :)

For all u ppl who have dificulties logging in with an added user and only can do it as anonymous or ftp user without a password, try add the user in  system/administration/user&groups  instead of doing it with a command. 

ex.
user = guest1
root(home directory) = /home/FTP-shared
chell = /bin/false

If it it does not work check chmod of the in this case  FTP-shared directory.

btw  no-ip is a great client for ip mask and very easy to config.

---

