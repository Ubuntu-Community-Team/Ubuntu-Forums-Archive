---
title: "automount a network NAS drive folder"
date: 2013-04-15
forum: New to Ubuntu
---

### Post by docJ on 2013-04-15
Hi again,
my CrashPlan backup program needs to see my backup _destination_ folder just like it already sees my source partitions (in Nautilus, the Media folder shows my 3 internal data drives)  

I have read this thread ([http://ubuntuforums.org/showthread.php?t=1806455](http://ubuntuforums.org/showthread.php?t=1806455)), and it gives me a good general idea, but being so green at Ubuntu, I'm afraid I need more specific instructions for my own situation.

Anyone up for a little hand holding?

Thanks in advance !

---

### Post by papibe on 2013-04-15
Hi docJ.

Are you backing up to an internal local drive or to a network drive?

If local, could you post the results of this command?
```
sudo fdisk -l
```
For network, this one:
```
sudo smbtree
```
Regards.

---

### Post by docJ on 2013-04-15
Hi [**[COLOR=#C61919][B]papibe**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=774785") and thanks for helping me.
I wish to backup to an network drive, so I went with your 2nd command, but I have puzzling result; it keeps asking for:```
Enter root's password: 

```
It doesn't want to accept what I usually put ???

---

### Post by papibe on 2013-04-15
Just press enter, or running as you:
```
smbtree
```
Regards.

---

### Post by docJ on 2013-04-15
smbtree asked for my user p/w (as opposed to root's), but gave nothing back

Doing it with sudo in front, then a blank p/w worked and gave me this:
(BTW, is this normal? First time I ever had an issue with p/w)

```
MSHOME3
    \\DLINK-A52A8A           DNS-343
        \\DLINK-A52A8A\lp                 USB Printer
        \\DLINK-A52A8A\IPC$               IPC Service (DNS-343)
        \\DLINK-A52A8A\Volume_1           
        \\DLINK-A52A8A\web_page           Enter Our Web Page Setting
    \\UB3                    ub3 server (Samba, Ubuntu)
        \\UB3\S 0.6              
        \\UB3\U2                 
        \\UB3\V2                 
        \\UB3\T3                 
        \\UB3\IPC$               IPC Service (ub3 server (Samba, Ubuntu))
        \\UB3\print$             Printer Drivers
    \\J-L-2-PC               JL2
    \\CAROLE-7               
        \\CAROLE-7\Users              
        \\CAROLE-7\print$             Pilotes d&#8217;imprimantes
        \\CAROLE-7\IPC$               IPC distant
        \\CAROLE-7\Canon MP160 Printer    Canon MP160 Printer
        \\CAROLE-7\C$                 Partage par défaut
        \\CAROLE-7\ADMIN$             Administration à distance


```
The 3rd line (DLINK-A52A8A\Volume_1...) is the _parent_ folder where I wish to save my b/up, in there is a simple folder structure (Backup\UB3\), where UB3 is the intended target

---

### Post by papibe on 2013-04-15
> **docJ said:**
> is this normal?
Yes. Don't worry about it.
[QUOTE=docJ]The 3rd line (DLINK-A52A8A\Volume_1...) is the parent folder where I wish to save my b/up, in there is a simple folder structure (Backup\UB3\), where UB3 is the intended target[/QUOTE]
If I understand correctly, you want to run your backup locally in UB3, and save it to DLINK-A52A8A\Volume_1, is that it?

Regards.

---

### Post by docJ on 2013-04-15
Yes, with a slight twist,
I just installed this really nice CrashPlan backup sftwr on this computer, and it's already setup to backup the whole content of: 

        \\UB3\U2                          \\UB3\V2                          \\UB3\T3                 

All I have left to do is tell it where to send the backup to:

\\DLINK-A52A8A\Volume_1\Backup\UB3\

For that, this destination needs to be visible in the folder list of this computer, similar to media folder showing my 3 source partitions.

Hopefully this makes sense to you
(You may have noticed from smbtree that english is not my first language...;)

---

### Post by docJ on 2013-04-15
Also, if it helps to know, my d-link NAS a a fixed IP adress 192.168.0.32,
while "DLINK-A52A8A" is its kind-of user friendly name with "A52A8A" being the begining of its mac address

---

### Post by papibe on 2013-04-15
OK. Thanks.

First you need to install a package.

In 12.04+:
```
sudo apt-get install cifs-utils
```
Below that version:
```
sudo apt-get -s install smbfs
```
Then to mount the samba share:
```
sudo mount -t cifs  //DLINK-A52A8A/Volume_1/Backup/UB3  /path/to/local/mountpoint
```
Where the local mountpoint must exist locally as a directory.

Now you can set Crashplan to save backups to  /path/to/local/mountpoint

Hope it helps. Let us know how it goes.
Regards.

---

### Post by docJ on 2013-04-15
> **papibe said:**
> First you need to install a package.

In 12.04+:
```
sudo apt-get install cifs-utils
```

Simple enough, even for me

> Below that version:
??? Sorry, what do you mean?

> Where the local mountpoint must exist locally as a directory.

Now you can set Crashplan to save backups to  /path/to/local/mountpoint
I am lost, I do not want to save backup locally, I want to save them externally to the D-link NAS

Your instructions are certainly the right one, but I would prefer to be sure I understand 100%

And > /path/to/local/mountpoint
I don't actually copy this litterally in the command (?)

---

### Post by docJ on 2013-04-15
Step 1 is done, result below:
```
jlr@ub3:~$ sudo apt-get install cifs-utils
[sudo] password for jlr: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
cifs-utils is already the newest version.
cifs-utils set to manually installed.
The following packages were automatically installed and are no longer required:
  linux-headers-3.5.0-23-generic language-pack-kde-en linux-headers-3.5.0-23
  language-pack-kde-en-base
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jlr@ub3:~$ 


```

---

### Post by docJ on 2013-04-15
I think I got it !
I have 12.04 so what I did (step 1) was ok

By: ''Below that version'' you meant if I had older Ubuntu I would need to do step 2 instead (?)

Also, I think I realize what you mean by ''local mount point''; similar to seeing my 3 data drives in my ''media'' folder 

I will almost feel smart if I get 2 points here...:)

---

### Post by docJ on 2013-04-15
> **papibe said:**
> Then to mount the samba share:
```
sudo mount -t cifs  //DLINK-A52A8A/Volume_1/Backup/UB3  /path/to/local/mountpoint
```
Where the local mountpoint must exist locally as a directory.

Now you can set Crashplan to save backups to  /path/to/local/mountpoint


Providing I got my 2 points ;), I just need clarification on the last part
I am almost sure I need to replace this > /path/to/local/mountpoint
with something else, but I have no idea with what

---

### Post by papibe on 2013-04-15
> **docJ said:**
> I think I got it !
I have 12.04 so what I did (step 1) was ok
Yes.
> **docJ said:**
> By: ''Below that version'' you meant if I had older Ubuntu I would need to do step 2 instead (?)
Indeed. Had you had 10.04, you would have installed smbfs instead.

Regarding where the backup goes.

As far as I know, Crashplan does not directly support network targets. In this case you would need the support of a smb url. For instance:
```
smb://DLINK-A52A8A/Volume_1/Backup/UB3
```
Thus, in order to copy the backup to the NAS, you need to mount the remote directory so it looks like a regular local directory to Crashplan. When Crashplan copy the backups to '/path/to/local/mountpoint', it will be actually copy them on the NAS.

Does that help?
Regards.

---

### Post by docJ on 2013-04-15
Yes, totally, I give you back the 2 points for extraordinary patience !

So I run this as it is then?```
sudo mount -t cifs  //DLINK-A52A8A/Volume_1/Backup/UB3  /path/to/local/mountpoint
```

---

### Post by docJ on 2013-04-15
I guess not, :(
Here's what I got
```
Couldn't chdir to /path/to/local/mountpoint: No such file or directory
```

---

### Post by papibe on 2013-04-15
The name '/path/to/local/mountpoint' is just an example. You need to decide where to mount the remote directory, and how to name it.

For example:
```
sudo mkdir **/media/NAS**

sudo mount -t cifs  //DLINK-A52A8A/Volume_1/Backup/UB3  **/media/NAS**
```
Other example: using the /mnt directory. Check if it exists:
```
ls **/mnt**
```
If no errors are displays it measn that does exist. Then:
```
sudo mount -t cifs  //DLINK-A52A8A/Volume_1/Backup/UB3  **/mnt**
```
Regards.

---

### Post by docJ on 2013-04-15
Almost there...

```
jlr@ub3:~$ sudo mkdir /media/NAS
jlr@ub3:~$ sudo mount -t cifs  //DLINK-A52A8A/Volume_1/Backup/UB3  /media/NAS
mount error: could not resolve address for DLINK-A52A8A: Unknown error
```

---

### Post by papibe on 2013-04-15
It looks like you don't have a DNS that resolves local addresses.

Try using the NAS ip address instead of its name:
```
sudo mount -t cifs  //192.168.1.5/Volume_1/Backup/UB3  /media/NAS
```
Replace '192.168.1.51' with the actual NAS' ip address.

Let us know how it goes.
Regards.

---

### Post by docJ on 2013-04-15
If I use Nautilus to navigate to: 

Volume_1/Backup/UB3
then right-click and click properties, this is what I see:
Location: smb://dlink-a52a8a/volume_1/BackUp

I Notice 2 things, the smb in front and the lower caps on 
dlink-a52a8a
as opposed to terminal command result: DLINK-A52A8A (high caps)

Is this case sensitive?

---

### Post by docJ on 2013-04-15
> It looks like you don't have a DNS that resolves local addresses.


I setup the firewall day before yesterday, I must have forgot to add a rule

---

### Post by docJ on 2013-04-15
> **papibe said:**
> 
Try using the NAS ip address instead of its name:
```
sudo mount -t cifs  //192.168.1.5/Volume_1/Backup/UB3  /media/NAS
```
Replace '192.168.1.51' with the actual NAS' ip address.

Let us know how it goes.
Regards.

As I heard plenty of time before, when you run something and the terminal does not complain after, that's usually a good sign...
Fingers crossed,

---

### Post by docJ on 2013-04-15
Actually, it prompted for password
tried my usual, got this (also tried blank p/w; same thing)

```
jlr@ub3:~$ sudo mount -t cifs  //192.168.0.32/Volume_1/Backup/UB3  /media/NAS
Password: 
mount error(2): No such file or directory
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)


```

---

### Post by papibe on 2013-04-15
The first password is for sudo (your password). In case is there a second one, it is related to identify yourself on the NAS, i.e., the password that gives your user access to the samba share (it could be the same one).

Try this:
```
sudo mount -t cifs  //192.168.0.32/Volume_1/  /media/NAS
```
Regards.

---

### Post by docJ on 2013-04-15
Yes, it asked twice, I entered the same both times, no error this time, but nothing happenned also


```
jlr@ub3:~$ sudo mount -t cifs  //192.168.0.32/Volume_1/  /media/NAS
[sudo] password for jlr: 
Password: 


```

---

### Post by docJ on 2013-04-15
Do I need to test the mount, edit fstab, reboot, all of the above?

---

### Post by docJ on 2013-04-15
In Nautilus, there was the eject thing next to NAS folder, but I just rebooted and its not mounted anymore.
I think NAS folder should appear automatically on the launchpad, next to my 3 internal drive (proof they automount)

---

### Post by papibe on 2013-04-15
> **docJ said:**
> Do I need to test the mount, edit fstab, reboot, all of the above?
The mount we did was for the current session only. You need to add an entry to fstab in order to make it permanently.

The format is a little different. Take a look at this [thread]("http://ubuntuforums.org/showthread.php?t=2134029") and let us know if you need more help with that.
Regards.

---

### Post by docJ on 2013-04-15
I will need help with fstab, But This will have to wait for tomorrow
I just redid the session mount ```

sudo mount -t cifs  //192.168.0.32/Volume_1/  /media/NAS
```
NAS folder appears mounted in Nautilus, but still does not show up in the launchpad (because not automounted yet?)
And I tried doing small test backup with CrashPlan, it says its all good, but God knows where it sends the backup to, I have nothing to show in Volume_1/BackUp/UB3 , nor in /media/NAS for that matter

---

### Post by docJ on 2013-04-15
Actually Papibe, I'm gonna call it a night, my alarm clock goes off in less than 6 hrs...

Thanks a million, even if I dont have much to show for right now, we did make progress, no thanks to me...

Catch you later and thanks again

---

### Post by docJ on 2013-04-16
Back after about 5 hrs of shut eyes...

> **docJ said:**
> 
And I tried doing small test backup with CrashPlan, it says its all good, but God knows where it sends the backup to, I have nothing to show in Volume_1/BackUp/UB3 , nor in /media/NAS for that matter

I figured this out; My backup were being sent to Ubuntu's home folder, as within CrashPlan itself, I had not configured the destination properly. I just fiix that and the few test backup made previously were moved automatically from the "old" local home to the "new" network folder inside the NAS.

Se we did very good, yesterday evening, I was just too tired to realize it...

---

### Post by docJ on 2013-04-16
> **papibe said:**
> The mount we did was for the current session only. You need to add an entry to fstab in order to make it permanently.

The format is a little different. Take a look at this [thread]("http://ubuntuforums.org/showthread.php?t=2134029") and let us know if you need more help with that.
Regards.

I realize Papibe is likely asleep now, it being 3am (his timezone)

I beleive this is all I have left to do is automount the drive we created, it manually mounts just fine
Anyone else up for the challenge to walk me through it ?

---

### Post by docJ on 2013-04-16
Quoted from the suggested thread
> **papibe said:**
> You can create an entry on /etc/fstab.

Edit the file using this command:
```
gksudo gedit /etc/fstab
```
You need to add a line similar to this:
```
//servername/ShareName /path/to/mountpoint cifs  user=yourusername,uid=1000,gid=100  0  0
```
For more details take a look a this [tutorial]("https://help.ubuntu.com/community/Fstab").

Let us know how it goes.
Regards.

Mine would need to look something *like* this:

```
//192.168.0.32/Volume_1/  /media/NAS cifs  user=jlr,uid=1000,gid=100  0  0
```


Hopefully I edited the example ok with my network folder "linking to local, then my username
After that is uid , I beleive 90% I can just copy the example (?) 
If I open terminal and type id, it does show
uid=1000(jlr)
**gid=1000(jlr)**
groups=1000(jlr)
4(adm)
24(cdrom)
27(sudo)
38(dip)
46(plugdev)
109(lpadmin)
124(sambashare)

So I would need to do 
```
//192.168.0.32/Volume_1/  /media/NAS cifs  user=jlr,uid=1000,gid=**1000**  0  0
```

Lastly, the pair of zeros at the end seems consistent with the reference thread

---

### Post by docJ on 2013-04-16
I edited fstab, then tested the mount but there was no output
I restart the computer and it stops on a black screen with lots of white writing, with an extra line every 120 seconds

I force shut down, and the I can start the computer normally, but if I redo a restart, again, it hangs before shtting down at the black and white screen again

I have messed up...:icon_frown:

I need to type this from my other computer, but this is what I see on Ubuntu at the top left:

could not write bytes: Broken pipe
*checking battery state...
*Starting regular background program processing daemon
*Starting deferred execution scheduler
Starting CrashPlan Engine...Stopping anac(h)ronistic cron

sing standard setup
                           OK
                           *Stopping System V runlevel compatibility
* Starting CUPS printing spooler/server

ountall: Disconnect from Plymouth
                            acpid: exiting
Checking for running unattended-upgrades:
                                                         speed-dispatcher disabled; edit /etc/default/speech-dispatcher

Then there's a bunch of lines with a new one every 120 seconds ( I wont type them all but a few:

( 239.650252) ''echo 0 proc/sys/kernel/hung_task_timeout_sec''disables this message.
( 239.650396) INFO: task s20sendsigs:2388 blocked for more than 120 seconds.

Too long to type them all but in essence
The ones that start with echo 0 all end with: proc/sys/kernel/hung_task_timeout_sec''disables this message.
The ones that start with INFO: task alternate between:
 Xorg:1309 and s20sendsigs:2388

---

### Post by papibe on 2013-04-16
Try testing your fstab without rebooting your computer by running:
```
sudo mount -a
```
That way you could also paste the error messages here.

Regards.

---

### Post by docJ on 2013-04-16
Judging from the above, I would be tempted to restart, go back in fstab and remove the last line I put there...

---

### Post by docJ on 2013-04-16
> **papibe said:**
> Try testing your fstab without rebooting your computer by running:
```
sudo mount -a
```
That way you could also paste the error messages here.

Regards.

Thank God you're back, right now Ubuntu is ''trying to shutdown on the black screen I described, so I'm afraid I can't do much with it at the moment ( I am writing from my other computer)

---

### Post by docJ on 2013-04-16
I forced shutdown, now restarting

---

### Post by docJ on 2013-04-16
OK' back on Ubuntu (it starts up just fine, but won't shutdown properly
Testing the mount prompts for 2 p/w, then I see NAS device appear in the launchpad

---

### Post by papibe on 2013-04-16
To avoid the password request use a 'credentials' file.

Start by adding the credential option to the fstab entry:

```
//192.168.0.32/Volume_1/  /media/NAS cifs  **credentials=/home/jlr/.smbcredentials**,user=jlr,uid=1000,gid=1000  0  0
```
Then create the file:
```
gedit ~/.smbcredentials
```
Write this:
```
username=jlr
password=sharepassword
domain=MSHOME3
```
Replace 'sharepassword' with the password required to mount the share (the 2nd one, not the sudo one). Save the file.

Unmount the share by running:
```
sudo umount /media/NAS cifs
```
And then try mounting everything on fstab by doing this again:
```
sudo mount -a
```

Regards.

---

### Post by docJ on 2013-04-16
Just before I do, if instead of this line


```
//192.168.0.32/Volume_1/  /media/NAS cifs  user=jlr,uid=1000,gid=1000  0  0
```

I put this one instead:
```
//192.168.0.32/Volume_1/  /media/NAS cifs **guest**,uid=1000,  0  0
```

Could I avoid the rest of the steps?

---

### Post by papibe on 2013-04-16
That might work.

Try those changes and then:

Unmount the share by running:
```
sudo umount /media/NAS cifs
```
And then try mounting everything on fstab by doing this again:
```
sudo mount -a
```
Let us know how it goes.
Regards.

---

### Post by docJ on 2013-04-16
My syntax is good?

---

### Post by papibe on 2013-04-16
A comma was left behind... I would re add the gid option:
```
//192.168.0.32/Volume_1/  /media/NAS cifs guest,uid=1000,gid=1000  0  0
```

---

### Post by docJ on 2013-04-16
I assume it was, when I saved fstab, NAS icon on launchpad disapeared, which might explain:```
jlr@ub3:~$ sudo umount /media/NAS cifs
umount: cifs: not found


```

---

### Post by docJ on 2013-04-16
Dooooh!, be right back !

---

### Post by docJ on 2013-04-16
By the way, each time I enter test editor for fstab I notice 2 tabs, one with fstab, the other called untitled document, everytime I save the actual fstab and try to close, it ask where I want to save the empty untitled document

---

### Post by papibe on 2013-04-16
> **docJ said:**
> By the way, each time I enter test editor for fstab I notice 2 tabs, one with fstab, the other called untitled document, everytime I save the actual fstab and try to close, it ask where I want to save the empty untitled document

Yes. That's a known bug.

> **docJ said:**
> ```
jlr@ub3:~$ sudo umount /media/NAS cifs
umount: cifs: not found

```
My bad. The command is just:
```
sudo umount /media/NAS
```
Regards.

---

### Post by docJ on 2013-04-16
```
jlr@ub3:~$ sudo umount /media/NAS cifs
umount: cifs: not found
jlr@ub3:~$ sudo mount -a


```
testind mounting does nothing, no feedback, NAS device does not pop on the launchpad, its also invisible in Nautilus

---

### Post by docJ on 2013-04-16
> **papibe said:**
> Yes. That's a known bug.


My bad. The command is just:
```
sudo umount /media/NAS
```
Regards.

redid but with latest, same non-reaction
```
jlr@ub3:~$ sudo umount /media/NAS
jlr@ub3:~$ sudo mount -a


```

---

### Post by papibe on 2013-04-16
Double check if the mount was done or not, by listing the content of the directory:
```
ls /media/NAS
```
or by listing all mountpoints:
```
sudo mount -l
```
Regards.

---

### Post by docJ on 2013-04-16
they gave respectively```
jlr@ub3:~$ ls /media/NAS
BackUp  Workaround.txt


```

and```
jlr@ub3:~$ sudo mount -l
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sdb1 on /media/b type ext4 (rw) [t2]
/dev/sdc1 on /media/c type ext4 (rw) [U2]
/dev/sdd1 on /media/d type ext4 (rw) [V2]
/dev/sda6 on /home type ext4 (rw)
gvfs-fuse-daemon on /home/jlr/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jlr)
gvfs-fuse-daemon on /root/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev)
//192.168.0.32/Volume_1/ on /media/NAS type cifs (rw)
```

---

### Post by papibe on 2013-04-16
> **docJ said:**
> they gave respectively```
jlr@ub3:~$ ls /media/NAS
BackUp  Workaround.txt

```
and```
$ sudo mount -l
...
//192.168.0.32/Volume_1/ on /media/NAS type cifs (rw)
```
It's mounted!

---

### Post by docJ on 2013-04-16
I guess, although it did not pop on the launchpad, it does show as mounted in Nautilus

---

### Post by docJ on 2013-04-16
remember the crazy way it hung when shutting down an hour ago, do I dare try again?

---

### Post by docJ on 2013-04-16
I dared, and it still hangs trying to shutdown 
(so I'm back on Windows pc)

Ubunto does not shutdown since last fstab edit
I need to force shutdown

---

### Post by docJ on 2013-04-16
Good news, when I start it, all is well, and the network folder automount ! ! ! :popcorn::guitar:

Bad news, It wont shutdown or restart properly...:confused:

---

### Post by papibe on 2013-04-16
It looks like this [Bug #211631]("https://bugs.launchpad.net/ubuntu/+source/samba/+bug/211631")  is still present on 12.04 :(

Would you add a comment there reporting that?

For now, you could avoid the hang time, by unmounting the share manually before the shutdown:
```
sudo umount /media/NAS
```
Regards.

---

### Post by docJ on 2013-04-16
You are a God (or thin white Duke, if you prefer...)
I unmounted & rebooted and no problems!

---

### Post by docJ on 2013-04-16
> **papibe said:**
> It looks like this [Bug #211631]("https://bugs.launchpad.net/ubuntu/+source/samba/+bug/211631")  is still present on 12.04 :(

           [h=3]Bug Description[/h]   
    IMPORTANT: this bug has enough  information; please don't post _anything_ unless a developer asks for  specific feedback! 
By posting to this bug you only make it harder for a  developer to spot the gem comments. 
Please use the "me too feature" of  launchpad to signal that you are affected and would like to see this  fixed.


Me too feature of launchpad???

---

### Post by docJ on 2013-04-16
The moment of truth:
 I go to CrashPlan, select **Destinations**, then **Folders**
Available folders box is empty

I click **Select** (a folder), in the next **Select a directory** window, I navigate to **Media** folder, then **NAS**, then **BackUp**, click on **UB3**, and click **OK**.

It says **please wait** for 30 secs, then a red ball with exclamation mark appears and it says: **Unable to connect, check your network**.

:confused:

---

### Post by papibe on 2013-04-16
> **docJ said:**
> Me too feature of launchpad???
At the top of the page there an option that says:
```
This bug affects 119 people. Does this bug affect you?
```
Click there to mark the bug as "affecting" you.

Regards.

---

### Post by docJ on 2013-04-16
I just see: This bug affects 119 people.


Do we need to be logged-in to see: Does this bug affect you?

---

### Post by papibe on 2013-04-16
> **docJ said:**
> **Unable to connect, check your network**. :confused:
Make sure you have write access.

Create a file under that directory:
```
touch /media/NAS/BackUp/UB3/testfile
```
Regards.

---

### Post by docJ on 2013-04-16
Yes, it does work, I can see the testfile from Ubuntu and from other pc as well

Could be a CrashPlan specific issue

---

### Post by docJ on 2013-04-16
> **docJ said:**
> I just see: This bug affects 119 people.Do we need to be logged-in to see: Does this bug affect you?

Indeed we need to be logged in, so I registered, and now see the whole link
When I click it, I get a time out, please try again :confused:
We'll do,

In the meantime, I am marking this thread as Solved, although I still have an issue with CrashPlan, I beleive it to be unrelated to this thread about automounting network drive.

I wish to express truly heartfelt congratulation to Papibe for hanging on and being a model of patience and professionalism, 2 qualities a Linux noob like me cannot get enough of.

---

### Post by papibe on 2013-04-16
> **docJ said:**
> Yes, it does work, I can see the testfile from Ubuntu and from other pc as well

Could be a CrashPlan specific issue
If you can create a file, then it should be possible for another application (running as 'you' *) to create and copy files.

It could be a Crashplan configuration issue, but I'm afraid I'm not a familiar how Crashplan works.

As you suggested it, starting a new thread focused on Crashplan seems like a good idea. Feel free to link this one so other users can see what you've done so far.

Regards.

* EDIT: if Crashplan runs under another user, it just may be a permission problem, and then it could be solved in the mount options.

---

### Post by Zill on 2013-04-16
docJ:  An alternative to unmounting manually prior to shutdown is to use [autofs]("https://help.ubuntu.com/community/Autofs") rather than mount via fstab.  I had a similar problem with NFS mounts hanging on shutdown and autofs seemed to cure this.

See section [6.1. CIFS]("https://help.ubuntu.com/community/Autofs#CIFS") for info on how to configure autofs for CIFS mounts.

---

### Post by docJ on 2013-04-16
> **papibe said:**
>  if Crashplan runs under another user, it just may be a permission problem, and then it could be solved in the mount options.

Again, you never ceased to amaze me.
Back when I installed it, I vaguely remember a question about running it as regular user vs [COLOR=#ff0000]sudo[/COLOR]
Even if it was just 3 days ago, my memory of that is blurry, but I think I chose [COLOR=#ff0000]sudo[/COLOR] (but not 100% sure)
I just watched back the youtube Linux install video but saw no mention at all of having to choose user.

I did record 2 text files that were deemed important, **Directories** and **Start Scripts**

Important **directories**:
  Installation:
    /usr/local/crashplan
  Logs:
    /usr/local/crashplan/log
  Default archive location:
    /usr/local/var/crashplan

**Start Scripts**
 [COLOR=#ff0000]sudo[/COLOR] /usr/local/crashplan/bin/CrashPlanEngine start|stop
  /usr/local/crashplan/bin/CrashPlanDesktop

Under **Start Scripts**, it does state[COLOR=#ff0000]sudo[/COLOR][COLOR=#ff0000][/COLOR]

---

### Post by docJ on 2013-04-16
> **Zill said:**
> docJ:  An alternative to unmounting manually prior to shutdown is to use [autofs]("https://help.ubuntu.com/community/Autofs") rather than mount via fstab.  I had a similar problem with NFS mounts hanging on shutdown and autofs seemed to cure this.

See section [6.1. CIFS]("https://help.ubuntu.com/community/Autofs#CIFS") for info on how to configure autofs for CIFS mounts.

Thanks Zill, this looks just like what I need, but I wouldn't dare try what I don't understand (by a long shot)
I am at the sorry stage where I can barely copy/paste custom instructions.

---

### Post by docJ on 2013-04-16
> **papibe said:**
> if Crashplan runs under another user, it just may be a permission problem, and then it could be solved in the mount options.

Having no clue how to solve permission issue, I googled the CrashPlan error: Unable to connect, check your network

On their own support page, they mention firewall as possible cause and I did enable the simple firewall a few days back

I will disable it temporarly, reboot the computer and try CrashPlan again just to rule this out

---

### Post by docJ on 2013-04-16
Imagine that, CrashPlan is now backing up this computer as I type
It was a firewall issue; their website says I need to allow inbound and outbound TCP port 4242
We'll do and report back.

---

### Post by Zill on 2013-04-16
> **docJ said:**
> Thanks Zill, this looks just like what I need, but I wouldn't dare try what I don't understand (by a long shot)
I am at the sorry stage where I can barely copy/paste custom instructions.
Autofs isn't really as daunting as it sounds. ;-)  I posted instructions on what worked for me in post #3 of [this thread]("http://crunchbang.org/forums/viewtopic.php?id=24991").  Another user, RitterSport, then modified the instructions to work with his CIFS mount, showing his final line in post #6.  Hopefully, you will be able to modify the examples given to suit your particular configuration.

HTH.

---

### Post by docJ on 2013-04-16
Re-enabled the firewall and quickly added the allow rules and its still running strong
ETA for my initial backup? 5.6 days:) (a tad under 4Tb will do that)

Zill, off I go diving into your last links

---

### Post by docJ on 2013-04-16
To Zill,
I looked at *RitterSport*'s line, then mine; I'm sorry to say I dunno how to adapt the former to the later.
This makes me feel like i'm reading *Brain Surgery for Dummies*. It looks simple enough, but I can't seem to get myself to cut that red wiggly thing yet...

---

### Post by Zill on 2013-04-16
> **docJ said:**
> I looked at *RitterSport*'s line, then mine; I'm sorry to say I dunno how to adapt the former to the later...
Please post your (working!) fstab file and I will try to emulate this with the appropriate autofs code.
```
cat /etc/fstab
```
It is late here so I am off to bed now - I will take a look at the code tomorrow.  Bye for now.

---

### Post by docJ on 2013-04-16
Thanks for your offer, I guess you only needed the last line, but just in case...

As far as mutual time zone, I'm -5:00 from you I beleive...

```
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=dd45ac45-5856-4fed-9747-77d73c1be122 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=77d98a43-673a-458e-83fd-a34bb24147a9 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=1cf17074-3d96-49c2-89b3-11ec33498e90 none            swap    sw              0       0
UUID=9d1b8994-ab09-4d39-8db5-732ac340a791     /media/b     ext4     defaults    0     2
UUID=e4cb3ab6-1be1-4cbd-b01e-62e425c916bf     /media/c     ext4     defaults    0     2
UUID=9398f40a-c0b9-4fe9-9993-afb0cbe8bcbd     /media/d     ext4     defaults    0     2
//192.168.0.32/Volume_1/  /media/NAS cifs guest,uid=1000,gid=1000  0  0


```

---

### Post by Zill on 2013-04-17
docJ: I suggest you try the following but I must give the caveat that, as I only use Linux systems, I have no direct experience of Microsoft's SMB or CIFS. 

Open (as root) the existing /etc/fstab file eg.
```
sudo nano /etc/fstab
```
"comment-out" your existing CIFS mount(s) by adding a "#" at the start of the relevant line. eg.
```
# //192.168.0.32/Volume_1/  /media/NAS cifs guest,uid=1000,gid=1000  0  0
```
This line can then easily be re-enabled if required by editing and removing the "#".
Save the edited file with Ctrl-o and exit nano with Ctrl-x.

Unmount the existing CIFS mount:
```
sudo umount -a
```

Install autofs eg.
```
sudo apt-get install autofs
```

Open (as root) new file /etc/auto.master eg.
```
sudo nano /etc/auto.master
```

Assuming that you want the mounted directories under /media, add the following line at the end:
```
/media	/etc/auto.misc	--timeout  60	--ghost
```
Note that you can change the mount directory to one of your choice.  The "ghost" option ensures that even unmounted directories are always visible.  Remove this if you prefer to only see the directory when you enter the path to the mounted directory.
Save the file with Ctrl-o and exit with Ctrl-x.

Open (as root) new file /etc/auto.misc eg.
```
sudo nano /etc/auto.misc
```

Add a line at the end for your mount directory in a similar format to your /etc/fstab file eg:
```
NAS	-fstype=cifs,rw,uid=1000,gid=1000	://192.168.0.32/Volume_1
```
Save the file with Ctrl-o and exit with Ctrl-x.

Start the autofs service:
```
sudo service autofs restart
```

Autofs should now be running and if the PC is shutdown or restarted this service should start automatically.  Your CIFS mount should be visible and will show the contents when accessed either via a terminal or via the Nautilus GUI file manager.  Hopefully, the PC will now shutdown and/or restart without hanging. ;-)

If you hit any problems with this please post back with any error messages.

---

### Post by docJ on 2013-04-17
Thanks Zill,
 this looks like hard work you did (I appreciate it!), and I feel the need to better grasp quite a few things in there before I proceed. For starter, I see many of your sentences ending with eg. what does it mean?

I do have a (huge) initial backup in progress since yesterday evening, and with every % more completed, I breathe a little easier (I am at about 15% done, so with luck, this all important 1st backup should be over sometime this weekend).

I will post back more questions for my understanding/peace of mind's sake.

Later

---

### Post by Zill on 2013-04-17
> **docJ said:**
> ...For starter, I see many of your sentences ending with eg. what does it mean?...
Sorry, "eg" is just a British abbreviation meaning "for example".
[http://dictionary.cambridge.org/dictionary/british/e-g](http://dictionary.cambridge.org/dictionary/british/e-g)

Hopefully, the commands given should make sense but if you have any queries please post back.

---

### Post by Trevster on 2013-04-17
Hi docj, 

I have Crashplan working exactly like you want I believe. I have a Clearos box with samba shares that I mount locally on boot on an Ubuntu 12.04 desktop. The media/drive3 is a 3tb disk for Crashplan backups for several laptops. It's been awhile since I set this up.

I remember having problems with permissions and Crashplan not being able to write to the share and giving the couldn't connect error. I would make sure the permissions are correct before trying any network troubleshooting. Might have to change the owner etc.

The fstab I use is below. The user name and password for the share are not hidden which may or may not be an issue for you. I am no expert at this but it works fine.

Cheers.

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=d4a9343e-d91e-4671-a3df-665b464d579d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
#UUID=8a30c886-fcf4-49c0-b86f-cd5be7c168c1 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
//192.168.1.1/drive1 /media/drive1 cifs noperm,username=you,password=yourpassword,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
//192.168.1.1/drive2 /media/drive2 cifs noperm,username=you,password=yourpassword,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
//192.168.1.1/drive3 /media/drive3 cifs noperm,username=you,password=yourpassword,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```

---

