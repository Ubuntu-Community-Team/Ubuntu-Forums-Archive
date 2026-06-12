---
title: "HOWTO: Backup nightly via rsync"
date: 2007-12-13
forum: Outdated Tutorials &amp; Tips
---

### Post by altonbr on 2007-12-13
[SIZE=4]**_Preamble_**[/SIZE]
As a Linux System Administrator, I've had to keep two servers in synchronization, either nightly or every couple of hours. The term is 'mirror' and can be seen in use when downloading Ubuntu .iso files from localized servers, say from a Cambodian server when the main server is in Britain. (You may not know this, but that's how it works, using pretty much the same script you see below).

[SIZE=3]_Why should I use this script?_[/SIZE]
You don't have to be a Linux System Administrator to enjoy the beautiful interoperability benefits of Linux, you can put it to use right at home!

Use this script to backup your entire family's data, every night, by using a central server and making the server 'pull' everyone's documents to it.

[SIZE=3]_How do I use this script?_[/SIZE]
How? Well if you purchase a 500GB server, then you could potentially backup five family member's computers if they each had a 100GB hard drive.

Simply use this script with the 'install' argument five times on the server and it will create five keys, one for each of your family members.

You need to setup either DNS names for the computers or static IP addresses for each computer.

I won't go into great detail on how to do this in *every* situation, but for a home network, you can change the IP address of one of your computers to a static IP address like this:
```
gksu gedit /etc/network/interfaces
```**Before:**
> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
**After:**
> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp

iface eth0 inet static
address 192.168.1.10 # computer1 = 192.168.1.10, computer2 = 192.168.1.11, computer3 = 192.168.1.12, etc.
netmask 255.255.255.0
gateway 192.168.1.1As for the Linux System Administrators, I don't need to tell you how useful this script is :P

[SIZE=3]_Any alternatives?_[/SIZE]
Of course! I'm not the first person to need file-synchronization or mirroring, but I feel most comfortable writing my own scripts so I know what's going on and can control the encryption strength.

**GUI** (Graphical User Interface)
_unison_: a file synchronization program used to sync files between two directories, either on one computer, or between a computer and another storage device. (I've never used it, but I heard its reliable)
```
sudo aptitude install unison unison-gtk
```**CLI** (Command Line)
_rsnapshot_: a filesystem snapshot utility for making backups of local and remote systems. The disk space required is just a little more than the space of one full backup, plus incrementals. (My program does not use incrementals).
```
sudo aptitude install rsnapshot
```[SIZE=4]**_Vocabulary_**[/SIZE]
[LIST]
[*]**ssh**: a network protocol that allows data to be exchanged using a secure channel (encryption) between two computers
[*]**rsync**: a software application for Linux which synchronizes files and directories from one location to another using minimal bandwidth (only transfers files (or parts of files) that don't exist)
[*]**mirror**: an exact copy of a data set
[*]**push**: to send (or give) data from one computer to another
[*]**pull**: to receive (or ask) for data from one computer to another
[/LIST]

[SIZE=4]**_Let's get started_**[/SIZE]
It has several flags and options, but some are hard-coded, so you may have to edit the script by hand.

[SIZE=4]**_Options_**[/SIZE]
General usage:
> ./rsync.sh ['uninstall' | 'install' | 'run'] ['push' | 'pull'] [local_dir] [remote_user] [remote_host] [remote_dir] [remote_ssh_port]Note: '[remote_ssh_port]' is usually 22 unless you change it from the default. If you don't know how to change the ssh port, its more than likely 22.

[SIZE=3]_install_[/SIZE]
Use this option if you want to setup an automated, nightly backup between one computer and another.
Arguments:> ./rsync.sh install [push | pull] [local_dir] [remote_user] [remote_host] [remote_dir] [remote_ssh_port]Example:> ./rsync.sh install pull /home/brett/ brett 192.168.1.2 /home/brett 2222
[LIST]
[*]Creates the following directories: $HOME/bin, $HOME/cron, $HOME/logs
[*]Creates 4096-bit RSA encryption key (illegal in the USA I think)
[*]Installs file to directories above
[/LIST]

[SIZE=3]_uninstall_[/SIZE]
Use this option if you want to remove a previously installed setup.
Arguments:> ./rsync.sh uninstall [remote_user] [remote_host]Example:> ./rsync.sh uninstall brett 192.168.1.2
[LIST]
[*]Removes cron-job
[*]Removes RSA key
[/LIST]

[SIZE=3]_run_[/SIZE]
Use this option if you want to run the program without installing anything. Good to use as a test and on a single-needs basis.
Arguments:> ./rsync.sh run [push | pull] [local_dir] [remote_user] [remote_host] [remote_dir] [remote_ssh_port]Example:> ./rsync.sh run pull /home/brett/ brett 192.168.1.2 /home/brett 2222
[LIST]
[*]Runs rsync with your parameters
[/LIST]

[SIZE=4]**_rsync.sh_**[/SIZE]
[http://github.com/brettalton/rsync-over-ssh/raw/master/rsync.sh](http://github.com/brettalton/rsync-over-ssh/raw/master/rsync.sh)

---

### Post by grim4593 on 2007-12-24
This was very useful!
I didn't actually use your script in conjunction with cron, but it let me come up with my own backup scheme. Thanks :D

---

### Post by altonbr on 2007-12-24
> **grim4593 said:**
> This was very useful!
I didn't actually use your script in conjunction with cron, but it let me come up with my own backup scheme. Thanks :D

Great! I was worried that this tutorial might be to complex, when really it's only a couple steps.

---

### Post by madk on 2007-12-31
I haven't tried this yet (just trying to figure out what's happening in your script) so I could be wrong, but don't you need the $BACKUPDIR variabe in your rsync-line?

It looks like you only define a destination and no source directory.

---

### Post by altonbr on 2007-12-31
> **madk said:**
> I haven't tried this yet (just trying to figure out what's happening in your script) so I could be wrong, but don't you need the $BACKUPDIR variabe in your rsync-line?

It looks like you only define a destination and no source directory.

Brutal. You're correct. Thank you and my apologizes.
```
rsync -avrz --delete --delete-excluded --exclude-from=$EXCLUDEFILE --log-file=$LOGFILE --rsh="ssh -p $SSHPORT -i /home/$USER/.ssh/backup" **$BACKUPDIR** $USER@$IPADDRESS:/home/$USER/backup/
```

---

### Post by neil.the.blue on 2008-05-18
The ssh-copy-id command is useful for copying the public key.

ssh-copy-id -i <path to key> user@host

---

### Post by altonbr on 2008-05-18
Yeah, but I needed to do logic checks and create folders as well.

I'm planning on re-writing this soon actually as it seems a bit scattered... It could really be made into one script.

---

### Post by Mister X on 2008-06-10
Thank you, very usefull!!

---

### Post by Toky on 2008-06-28
This is a pretty good contribution, but WHY would you recommend a passphrase-less key??????

I would just create a proper key with passphrase and have a ssh-agent running.  This would make it much much much secure/complete solution.

Passphrase-less Keys ARE THE DEVIL!!!

Of course I would do that for any communication across the cloud, if your backup is inside your house's LAN then its not that bad (although not the best practice).

Cheers!

---

### Post by eldragon on 2008-06-28
> **Toky said:**
> This is a pretty good contribution, but WHY would you recommend a passphrase-less key??????

I would just create a proper key with passphrase and have a ssh-agent running.  This would make it much much much secure/complete solution.

Passphrase-less Keys ARE THE DEVIL!!!

Of course I would do that for any communication across the cloud, if your backup is inside your house's LAN then its not that bad (although not the best practice).

Cheers!

if you need it to be automatic, you cannot have it requiring user input.

getting that off my chest. why on earth reinvent the wheel? there are dozen scripts already doing this. my favorite due to simplicity being rsnapshot.

good luck :D

---

### Post by altonbr on 2008-06-28
I rewrote this a little while ago to be a complete install/uninstall/run script. I'll post it here soon.

---

### Post by Toky on 2008-06-29
> **eldragon said:**
> if you need it to be automatic, you cannot have it requiring user input.


That's why I said to use a ssh-agent...google it

---

### Post by altonbr on 2008-06-29
Completely re-wrote the tutorial for a brand-new script.

---

### Post by Robert Easter on 2008-10-31
This sounds great, but one (so far) question arises:  with what kind of connection are we looking at connecting the two boxes?  Is this assuming a USB cable, LAN, Bluetooth..?

Pretend there is somebody who has two computers, desperately needs to keep them updated, and has zero tech-savvy or jargon knowledge.  Is it possible to advise such a person?

---

### Post by altonbr on 2008-11-03
> **Robert Easter said:**
> This sounds great, but one (so far) question arises:  with what kind of connection are we looking at connecting the two boxes?  Is this assuming a USB cable, LAN, Bluetooth..?

Ethernet cable and router.

> **Robert Easter said:**
> Pretend there is somebody who has two computers, desperately needs to keep them updated, and has zero tech-savvy or jargon knowledge.  Is it possible to advise such a person?

I wouldn't suggest this script as it requires every use of the command-line. If you're looking for a method that uses a point-and-click GUI, then I would suggest Unison (see my original post above).

There is absolutely nothing wrong with using Unison; I only wrote this hour because my job requires me to use the command line.

---

### Post by phoch_00 on 2008-11-06
First, let me say thanks for doing this. I'm very appreciative of your efforts.

Secondly - I have a question. What is the best way to do this for multiple directories? As an example, I have /home/paul to backup but I also have /media/sdb1/music to back up. In the old tutorial I basically just copied and pasted everything and did a quick replace, etc. to make it work. With this more comprehensive scripted approach I'm not sure how easy it is to do that!

Thanks again!


Paul

---

### Post by altonbr on 2008-11-07
> **phoch_00 said:**
> First, let me say thanks for doing this. I'm very appreciative of your efforts.
You're welcome!

> **phoch_00 said:**
> Secondly - I have a question. What is the best way to do this for multiple directories? As an example, I have /home/paul to backup but I also have /media/sdb1/music to back up. In the old tutorial I basically just copied and pasted everything and did a quick replace, etc. to make it work. With this more comprehensive scripted approach I'm not sure how easy it is to do that!
Very good question and I will add this to my main post above.

I actually asked this question myself a while back: [http://ubuntuforums.org/showthread.php?t=572543](http://ubuntuforums.org/showthread.php?t=572543)

If you want to backup multiple directories using rsync (and thus my script), it will look something like this:
```
./rsync.sh run [push | pull] localhost:'/home/paul /media/sdb1/music' [remote_user] [remote_host] [remote_dir] [remote_ssh_port] 
```

---

### Post by phoch_00 on 2008-11-11
Perfect! Thanks again.

---

### Post by HeartBT on 2008-11-14
Love this.  Nice script.  Now, lets say we need to keep two /var/www directories mirrored (easy with this script), BUT they are NOT on the same domain, in fact they are very distant.  DD-wrt on one end God only knows on the other. And bandwidth IS minimal on one leg.

Just hypothetically :rolleyes: how would you tackle that?  

Thanks again, wish this script was around a year ago, but then I would not have learned?  Who knows, but thanks.

---

### Post by mozkill on 2008-11-14
If you want to backup a server only once every few months then I much prefer using Clonezilla .   You can make a Clone of your hda  and turn it into a bootable complete recovery disk.

---

### Post by altonbr on 2008-11-16
> **HeartBT said:**
> Love this.  Nice script.  Now, lets say we need to keep two /var/www directories mirrored (easy with this script), BUT they are NOT on the same domain, in fact they are very distant.  DD-wrt on one end God only knows on the other. And bandwidth IS minimal on one leg.

Just hypothetically :rolleyes: how would you tackle that?  

Thanks again, wish this script was around a year ago, but then I would not have learned?  Who knows, but thanks.

I can only suggest heavy compression, fewer mirror cycles or increased bandwidth!

Other than that, you can't exactly make your data magically appear from one server to the other...

Basically ask yourself: "How often does the data truly need to be synced?", "How important is it that my data is synced X amount of times per month?", "Is my data important enough to purchase increased bandwidth on the one side?", etc.

Seems more like a logistics problem than a technical problem!

> **mozkill said:**
> If you want to backup a server only once every few months then I much prefer using Clonezilla .   You can make a Clone of your hda  and turn it into a bootable complete recovery disk.

The command *dd* also performs a low-level from disk to disk.

```
sudo dd if=/dev/sda of=/dev/sdb bs=10M conv=notrunc
```
where /dev/sda is the original SATA hard drive and /dev/sdb is the backup SATA hard drive.

---

### Post by rick-n-stl on 2008-11-20
Great Script!
I have a question.
I created a job that runs daily and it worked perfect.
I have a job that only needs to run on Saturdays, it backups up a different directory.  When I use the install script a second time it removes my first job.  Is there a way around this?

Thanks
Rick

---

### Post by Vinno on 2008-11-20
Good job!

---

### Post by altonbr on 2008-11-21
> **rick-n-stl said:**
> Great Script!
I have a question.
I created a job that runs daily and it worked perfect.
I have a job that only needs to run on Saturdays, it backups up a different directory.  When I use the install script a second time it removes my first job.  Is there a way around this?

Thanks
Rick

Just manually edit your crontab
```
export EDITOR=vim && crontab -e
```
*(replace 'vim' with an editor you're comfortable with, like 'gedit', 'kate' or 'mouse')*

Then copy the one line that is installed and edit that for your second job. Sorry, I made it so it only runs one cron script during the install, but if you know how to edit cron jobs, you should be able to add as many as you want.

Let me know if you have any problems!

---

### Post by rick-n-stl on 2008-11-21
Sounds good.
That's the way I ended up doing it, I just thought I might have missed something.

FYI, for others.  Webmin works very well for editing Cron jobs.

Thanks again,

Rick

---

### Post by rick-n-stl on 2008-11-21
Log files

One more question.  It look like the script creates a log file, but it doesn't seem to be working for me.  The log directory is there but it doesn't put anything in it.  

Our goal to to email the log files so we know what's going on.

Rick

---

### Post by HeartBT on 2008-11-21
> **altonbr said:**
> I can only suggest heavy compression, fewer mirror cycles or increased bandwidth!

Other than that, you can't exactly make your data magically appear from one server to the other...

Basically ask yourself: "How often does the data truly need to be synced?", "How important is it that my data is synced X amount of times per month?", "Is my data important enough to purchase increased bandwidth on the one side?", etc.

Seems more like a logistics problem than a technical problem!


I appreciate your reply.  Yes, it is a bit of a logistics problem, but it is also unresolvable as the one location is rather remote so is linked solely by satelite. Any increase in bandwidth is a serious financial obstacle.  The only reason for the "web" server is for the local intranet.  Mirror cycles could be, flexible.  In fact it is currently kept, kinda, mirrored by dragondrop on an as needed basis.

The reason that I asked the "hypothetical" was to see if I was on the right thought, and it appears that I was, with the compression.  I don't, however, have any experience with compressing an rsync, or sending it over the open net.  Do you have any thoughts, perhaps experience on that?  As the information is not horribly sensitive, would you recommend low/lower level encryption to save bandwidth? I'm not sure how much overhead encryption would have on the sync.

---

### Post by altonbr on 2008-11-22
> **rick-n-stl said:**
> Log files

One more question.  It look like the script creates a log file, but it doesn't seem to be working for me.  The log directory is there but it doesn't put anything in it.  

Our goal to to email the log files so we know what's going on.

Rick

Sorry Rick, I have the log commented out because it was throwing errors with CentOS. Apparently CentOS's rsync is unable to produce logs.

If you go into my code, as seen below, and remove the '#' before '--log-file=$LOCAL_LOG_FILE' (make sure to do it twice there), than your log file should be created as normal.

```
	# TODO: apperently Red Hat/Fedora/CentOS doesn't have the --log-file option in rsync, so I must add Debian/Ubuntu vs CentOS detection

	if [ "$METHOD" == "push" ]; then # local to remote
		rsync -avz --rsh="ssh -l $REMOTE_USER -p $REMOTE_SSH_PORT -i $LOCAL_KEY_FILE" --delete $LOCAL_DIR $REMOTE_USER@$REMOTE_HOST:$REMOTE_DIR # --log-file=$LOCAL_LOG_FILE
	elif [ "$METHOD" == "pull" ]; then # remote to local
		rsync -avz --rsh="ssh -l $REMOTE_USER -p $REMOTE_SSH_PORT -i $LOCAL_KEY_FILE" --delete $REMOTE_USER@$REMOTE_HOST:$REMOTE_DIR $LOCAL_DIR # --log-file=$LOCAL_LOG_FILE
```

I'll edit my script above to make it work with Ubuntu by default, but I'll leave that warning there for CentOS users.

---

### Post by altonbr on 2008-11-22
> **HeartBT said:**
> I appreciate your reply.  Yes, it is a bit of a logistics problem, but it is also unresolvable as the one location is rather remote so is linked solely by satelite. Any increase in bandwidth is a serious financial obstacle.  The only reason for the "web" server is for the local intranet.  Mirror cycles could be, flexible.  In fact it is currently kept, kinda, mirrored by dragondrop on an as needed basis.

The reason that I asked the "hypothetical" was to see if I was on the right thought, and it appears that I was, with the compression.  I don't, however, have any experience with compressing an rsync, or sending it over the open net.  Do you have any thoughts, perhaps experience on that?  As the information is not horribly sensitive, would you recommend low/lower level encryption to save bandwidth? I'm not sure how much overhead encryption would have on the sync.

Well the thing with rsync is that it only sends changes in files so if you don't change any of your files in a week, and you run rsync every weekend, it won't send any files or use any of your bandwidth (except a couple kB to compare the two servers). That's why it's better to use rsync than anything else, such as your manual dragging and dropping.

As for compression, rsync and ssh already compress bits when sending and receiving, but there are minor improvements you can do.

rsync has compression enabled when using the -z option (which is enabled in my script). To increase the compression however, you can add the flag```
--compress-level=9
``` to get the most compression possible. Keep in mind this takes more CPU power if that is a concern.

To increase ssh's compression, add ```
-o CompressionLevel=9
``` to any ssh commands.

I hope that helps!

---

### Post by rick-n-stl on 2008-11-26
Log files
Log files are now working.  It looks like it keeps the log files out there.  Can you tell me what I need to do to automaticaly delete them after like 7 days or some amount of time?

Thanks,

Rick

---

### Post by altonbr on 2008-11-26
> **rick-n-stl said:**
> Log files
Log files are now working.  It looks like it keeps the log files out there.  Can you tell me what I need to do to automaticaly delete them after like 7 days or some amount of time?

Thanks,

Rick

Depends, do you want it rotated so that always the last 7 days appear or do you just want all logs deleted every 7 days?

The later is easier, but the former is more convenient.

For the later, just add a cron job (as root) that run 'rm /path/to/logs/*' but for the former, you'll have to look into a program called 'cronolog'. It's a logfile rotator.

---

### Post by phoch_00 on 2009-02-27
I've used this script now for such a long time. It just works. Thanks sooooo much for writing this. I'm just finishing the build of a new box and implementing it yet again. It's really been great and wanted to say thanks.

---

### Post by altonbr on 2009-02-27
> **phoch_00 said:**
> I've used this script now for such a long time. It just works. Thanks sooooo much for writing this. I'm just finishing the build of a new box and implementing it yet again. It's really been great and wanted to say thanks.

You are very very welcome :) I appreciate the compliment!

---

### Post by rgotten on 2009-05-20
i have the following inquire, i am a newby with Ubuntu. i have an ubuntu server and windows clients, also have a network storage device...the data of my windows clients is being storage on the ubuntu server and is being access/seen by the windows computer, the network attach storage can be seen from the ubuntu server or from the windwos computer....i would like the server to do automatics copies fo the ubuntu server data into the network attach storage in a format that the windows computer on the network can access and see them..Wht is better...Synkron, Unison, rsync, etc...Remenber that i am a newby and your help will be greatly apprciated

rgotten

---

### Post by altonbr on 2009-05-20
> **rgotten said:**
> i have the following inquire, i am a newby with Ubuntu. i have an ubuntu server and windows clients, also have a network storage device...the data of my windows clients is being storage on the ubuntu server and is being access/seen by the windows computer, the network attach storage can be seen from the ubuntu server or from the windwos computer....i would like the server to do automatics copies fo the ubuntu server data into the network attach storage in a format that the windows computer on the network can access and see them..Wht is better...Synkron, Unison, rsync, etc...Remenber that i am a newby and your help will be greatly apprciated

rgotten

On your Ubuntu server, does it have a GUI or is it just text? If you have a GUI (e.g. you use your mouse and you point and click) one of the programs you listed may be best suited for your purposes.

The purpose of my script is to mirror data from one computer (or even folder) to another. This does not technically make backups, but what I do is copy the backup to a new folder with the date as a name (e.g. '20090520') but that involves a bit of programming/scripting.

If you're interested in that, I can easily help you with setting it up, but you'd probably be better to use a GUI program.

Which GUI program do I recommend? I'm sorry, I can't say as I've never used one for doing backups! Maybe someone else in this thread can help with that!

---

### Post by rgotten on 2009-05-20
> **altonbr said:**
> On your Ubuntu server, does it have a GUI or is it just text? If you have a GUI (e.g. you use your mouse and you point and click) one of the programs you listed may be best suited for your purposes.

The purpose of my script is to mirror data from one computer (or even folder) to another. This does not technically make backups, but what I do is copy the backup to a new folder with the date as a name (e.g. '20090520') but that involves a bit of programming/scripting.

If you're interested in that, I can easily help you with setting it up, but you'd probably be better to use a GUI program.

Which GUI program do I recommend? I'm sorry, I can't say as I've never used one for doing backups! Maybe someone else in this thread can help with that!

My Ubuntu server has the desktop version installed on top, but at the end when everything is on and working as i want, it is going to probably be  a server edition and access it thru Putty or webmin. Can  one of this GUI programs be run on a server edition of Ubuntu and still be access on my network as a GUI?, If i do the mirror as you mention, it will imply that for example if i have word documents, pdf files, jpeg in a folder called "test", it will be mirror to my network device storrage in nthe same way???, will i be able to see them as what there are from any computer in my network as this files?, Thanks

rgotten

---

### Post by renebs on 2009-08-13
Hi,

Thanks for the script and tutorial. I do have a question, if I want to include an exclude file/directories command, how can I go about modifying the script to do it. 

I have tried to follow the post of December 31st, 2007 03:49 PM, where this code appears:

```
rsync -avrz --delete --delete-excluded --exclude-from=$EXCLUDEFILE --log-file=$LOGFILE --rsh="ssh -p $SSHPORT -i /home/$USER/.ssh/backup" $BACKUPDIR $USER@$IPADDRESS:/home/$USER/backup/
```


But I haven't been successful (I did define the variable $EXCLUDEFILE, and the only thing I've added to the .rsync.sh file is --exclude-from=$EXCLUDEFILE (since the code above had different names for the variables). 

Thanks again for your tutorial.

---

### Post by matey3 on 2009-08-17
Hi I have a question about using rsync.

I used it like this;
rsync -avz -e web-server:/ /  (I setup ssh-keygen stuff so i wont have to log in)...
to copy over everything from one machine to another but the thing is that the /etc folder got copied over so the backup machine would not boot again, I had to manually change some of the things like hostname interfaces and other files back to original in order to boot, so

1-How could I make a mirror back up of our web server via network (web server is off site) without damaging the (local) backup server?
(I see $excludefiles but I dont know where to input that)?

2-the web-server is running 7.04 while the backup is running 8.10, would that work at all?
(considering some folders like /proc /dev others won't get copied over by default, but what about /boot directory? would that mess up the backup server by copying older Ubuntu files over from web-server)?

Thanks!

---

### Post by altonbr on 2009-08-18
> **renebs said:**
> Hi,

Thanks for the script and tutorial. I do have a question, if I want to include an exclude file/directories command, how can I go about modifying the script to do it. 

I have tried to follow the post of December 31st, 2007 03:49 PM, where this code appears:

```
rsync -avrz --delete --delete-excluded --exclude-from=$EXCLUDEFILE --log-file=$LOGFILE --rsh="ssh -p $SSHPORT -i /home/$USER/.ssh/backup" $BACKUPDIR $USER@$IPADDRESS:/home/$USER/backup/
```


But I haven't been successful (I did define the variable $EXCLUDEFILE, and the only thing I've added to the .rsync.sh file is --exclude-from=$EXCLUDEFILE (since the code above had different names for the variables). 

Thanks again for your tutorial.

So long as you write
```
EXCLUDEFILE=$HOME/excludefile.txt
```
before the code is executed, you should be fine.

Possibly the problem is that you're calling the file relatively and it's not finding it? Might I suggest an absolute path such as '/home/brett/exclude.txt' or '/var/cron/exclude.txt'

---

### Post by altonbr on 2009-08-18
> **matey3 said:**
> Hi I have a question about using rsync.

I used it like this;
rsync -avz -e web-server:/ /  (I setup ssh-keygen stuff so i wont have to log in)...
to copy over everything from one machine to another but the thing is that the /etc folder got copied over so the backup machine would not boot again, I had to manually change some of the things like hostname interfaces and other files back to original in order to boot, so

1-How could I make a mirror back up of our web server via network (web server is off site) without damaging the (local) backup server?
(I see $excludefiles but I dont know where to input that)?

2-the web-server is running 7.04 while the backup is running 8.10, would that work at all?
(considering some folders like /proc /dev others won't get copied over by default, but what about /boot directory? would that mess up the backup server by copying older Ubuntu files over from web-server)?

Thanks!

If you're running rsync as a one liner and not using my script, you can just add the exclude like this:
```
rsync --exclude-file=/home/user/exclude.txt
```
Where exclude.txt contains the folders you want to exclude.

My other question is: Why do you want to backup the server in its absolute entirety. Is there a special reason you need a hot copy of it? Usually you'll just want to backup configuration files, logs and your main files (/var/www if you're running a webserver).

As for 7.04 to 8.10, the difference is not a problem.

---

### Post by altonbr on 2010-06-03
I'm now hosting the project in a public repository over at [http://github.com/brettalton/rsync-over-ssh](http://github.com/brettalton/rsync-over-ssh). I'll still support the script here is anyone has any questions.

---

### Post by sphynx_25 on 2010-09-08
Hey there all, 

I'm actually trying to use rsync through cygwin on windows and I'm trying to make an exact copy of my data drive onto a second internal harddrive. I've never used rsync before and I was just wondering whether someone could show me the usage/what I should type for what I'm trying to do? I don't want to keep old and modified versions of each files, just be able to back up the contents of my data drive exactly.

Assistance on this would be greatly appreciated. Thanks!

---

### Post by altonbr on 2010-09-10
> **sphynx_25 said:**
> Hey there all, 

I'm actually trying to use rsync through cygwin on windows and I'm trying to make an exact copy of my data drive onto a second internal harddrive. I've never used rsync before and I was just wondering whether someone could show me the usage/what I should type for what I'm trying to do? I don't want to keep old and modified versions of each files, just be able to back up the contents of my data drive exactly.

Assistance on this would be greatly appreciated. Thanks!

I actually just wrote about a comical mishap that created performance issues on my machine when using rsync and the solution: [http://blog.brettalton.com/2010/09/10/performance-issues-and-rsync/](http://blog.brettalton.com/2010/09/10/performance-issues-and-rsync/)

Or you can use my script using the instructions in the first post: [http://ubuntuforums.org/showpost.php?p=3947493&postcount=1](http://ubuntuforums.org/showpost.php?p=3947493&postcount=1)

---

