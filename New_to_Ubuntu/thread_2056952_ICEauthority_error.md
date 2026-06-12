---
title: "ICEauthority error"
date: 2012-09-12
forum: New to Ubuntu
---

### Post by rem18 on 2012-09-12
Running 11.10...I changed password and then changed it back.
Now when I log on with passwrod after a few seconds I get the following message.
Could not update ICEauthority file  /home/username/.ICEauthority with only option to log out.

I have tried several sudo and chmod commands and everytime it gives me a doesnt exist answer.
Its as if I lost my home folder etc.
I have seen various solutions proposed around.
But would like maybe to start from scratch on this one
Anyone resolved this?
Thanks

---

### Post by oldfred on 2012-09-12
Did you also change username?

.dmrc errors- drs305
[http://ubuntuforums.org/showthread.php?p=6161267](http://ubuntuforums.org/showthread.php?p=6161267)
.ICEauthority errors
[http://ubuntuforums.org/showthread.php?t=1590835](http://ubuntuforums.org/showthread.php?t=1590835)
chmod 755 /home/username
sudo chown $USER:$USER /home/username/.ICEauthority
sudo chmod 644 /home/username/.ICEauthority
sudo chmod 644 $HOME/.ICEauthority
look at the permissions on ~/.Xauthority, too. It often gets changed when ~/.ICEauthority gets changed. The same fix applies.

---

### Post by rem18 on 2012-09-12
Thanks. So I ran
chown *[COLOR=DarkRed]username[/COLOR]* /home/*[COLOR=DarkRed]username[/COLOR]*/.dmrc 
got no such file or directory

same for 
sudo chmod 600 $HOME/.ICEauthority

ls -la $HOME/.ICEauthority
got no such file or directory

sudo chown $USER:$USER /home/username/.ICEauthority
got chown: missing operand after antony:antony/home/antony/ICEauthority

sudo chmod 644 /home/username/.ICEauthority
got chmod: cannot access  '/antony/.ICEauthority' no such file or directory

sudo chmod 644 $HOME/.ICEauthority
again No such file or directory

How do I look at the permissions?

Thnaks antony

---

### Post by NikTh on 2012-09-12
> **oldfred said:**
> 
look at the permissions **on ~/.Xauthority, too**. It often gets changed when ~/.ICEauthority gets changed. **The same fix applies**.

Based on upon.. 

try 

```
sudo chown antony:antony  ~/.Xauthority
``` 

Thanks

---

### Post by rem18 on 2012-09-13
sudo chown antony:antony  ~/.Xauthority

asks for password after which I get
'/home/antony/.xauthority' No such File or directory

---

### Post by NikTh on 2012-09-13
Hi , 

you know , these two files .Xauthority and .ICEauthority , even if you delete them , re-created . It seems weird how you lost these files . Maybe you moved your /home directory or something ?  Is the "route" /home/antony/ exists ? 
What is in /home ? 
```
ls /home
```

I suggest to boot from recovery mode and click on root 

then give first this command ```
mount -o remount,rw /
```and then change your password again with this command 
```
passwd antony
```it will ask you to confirm twice your new UNIX password. Then reboot and see if something fixed. 

Thanks

---

### Post by rem18 on 2012-09-13
Yeah this is what I said in the negining its as if 
my home got moved or something 
but how if all I did was change the password?

ls /home
gives antony
ls /home/antony (in case you meant that)
gives Access-Your-Private-Data.desktop   README.txt
then back to antony@antony

---

### Post by rem18 on 2012-09-13
I tried sudo bash and got root@antony then tried    


mount -o remount,rw /
but it just took me back to root@antony
I entered 
passwd antony anyay and updated passwrd rebooted
 and used new password.
got same message
Could not update ICEauthority file  /home/username/.ICEauthority 
with only option to log out.

---

### Post by steeldriver on 2012-09-13
The only thing I can think of here is that your entire /home/anthony directory is unwriteable - either because of permissions or because the whole partition (or disk) is full - you can check with

```
df -h
```

```
ls -l /home
```

---

### Post by rem18 on 2012-09-13
no its not full
all I did was change the password and then change it back thats all

---

### Post by rem18 on 2012-09-13
/dev/sda8 use 23%
 all others 1%

---

### Post by NikTh on 2012-09-13
Hi , 
please give the result of 

```
ls -ld /home/antony/ 
cat /home/antony/Access-Your-Private-Data.desktop
cat /home/antony/README.txt
```

Thanks

---

### Post by rem18 on 2012-09-13
ls -ld /home/antony/ 
= dr-x------ 3 antony antony 4096 2011-12-29 21.37 /home/antony/

 cat /home/antony/Access-Your-Private-Data.desktop
_Name=Access Your Private Data
-Genericname=Access Your Private Data
Exec=/usr/bin/ecryptfs-mount-private
Terminal=true
Type=Application
Categories=System;Security;
X-Ubuntu-Gettext-Domain=encryptfs-utils

cat /home/antony/README.txt
THIS DIRECTORY HAS BEEN UNMOUNTED TO PROTECT YOUR DATA.

From the  desktop, click on:
"Access Your Private Data"

or

From the command line. run:
ecryptfs-mount-private

NB.To be safe I am not trying any of these commands till you advise
Thanks

---

### Post by NikTh on 2012-09-13
Hi , 

ok , now try this command 

```
sudo mv ~/Access-Your-Private-Data.desktop /etc/xdg/autostart/
``` 

Hopefully above command will solve your problem. 

Thanks

---

### Post by rem18 on 2012-09-14
Hi Thanks for that
I did it it asked me for the password but after just took me back to antony@antony
I switched off and re-booted entered password etc but still got could not update ICEauthority
Thanks

---

### Post by NikTh on 2012-09-14
Hi , 
file moved ? 
```
ls -l /home/antony/ 
```_**IF no****t**_ , try to move the file from Recovery Mode 

Click root 
then 
```
mount -o remount,rw / 
mv ~/Access-Your-Private-Data.desktop /etc/xdg/autostart/
```and change again your password with 
```
passwd antony
```Reboot to see. 

Thanks

---

### Post by rem18 on 2012-09-14
ls -l /home/antony/
5396053 Access-Your-Private-Data.desktop 5396052 README.txt
antony@antony

I prefer you advise me clearly how or what you mean by click root
Thanks

---

### Post by rem18 on 2012-09-14
do you mean to write sudo before the command you gave me or to write sudo bash?

---

### Post by NikTh on 2012-09-14
Hi , 

you must boot from [Recovery Mode] to follow what I wrote before. 

From grub menu select the [Recovery Mode] . Then select  ROOT and then follow the commands with order 

```
mount -o remount,rw /
mv ~/Access-Your-Private-Data.desktop /etc/xdg/autostart/
```and then 
```
passwd antony
```change your password again . Twice confirmation needed. 

Then give this command to reboot 
```
reboot
```Thanks

---

### Post by rem18 on 2012-09-14
NIK its what you mean about select root that I am not clear about
Then select  ROOT......
thanks

---

### Post by NikTh on 2012-09-14
Yes . 
When you boot in recovery mode you will be prompted  by a menu to select what you want. 
There you must select ROOT . You will see it. 

You will not have any desktop environment there so Be-careful with the commands. Write them down to a paper and execute them with the order I gave them. 

Everything matters when you execute a command. Spaces , dots , backslashes.. 

_**Tip:**_ You can use Tab key to auto-fill the paths. 

Example 
```
mv ~/Acc^Tab
```^Tab means that you press Tab key at this point. This will auto-fill the name for you. 
> mv ~/Acc^Tab = ~/Access-Your-Private-Data.desktopI hope not confusing you. 

Thanks

---

### Post by rem18 on 2012-09-14
NIK OK now I understand about how you want me to go to the root now.
However  I can write
mv ~/Acc^Tab

But the only TAB I have on the keyboard is the one on l\h\s 
of keyboard but when I press it and after hit return I says mv: missing destination 
file operand after '/root/Ac^

I dont have a problem to copy your instructions as I am using 
a different pc for your instructions to the one that has the problem
My problem now if to make the tab or do mean something else?
Also you have changed the instructions of what you want me to do?
Thanks

---

### Post by rem18 on 2012-09-14
For your information I tried the instructions you gave me before
mount -o remount,rw /
gave result re-mounted
but
 mv ~/Access-Your-Private-Data.desktop /etc/xdg/autostart/
gave mv: cannot stat

---

### Post by NikTh on 2012-09-14
> **rem18 said:**
> For your information I tried the instructions you gave me before
mount -o remount,rw /
gave result re-mounted
but
 mv ~/Access-Your-Private-Data.desktop /etc/xdg/autostart/
gave mv: cannot stat

Hi , 
I don't know if this is my mistake. Maybe you must give the full path. 
**Again : Be careful when your write commands . All matters. Capital , backslashes , dots ...etc. If one dot missing then the mv command cannot find the file to move.**

```
mv /home/antony/Access-Your-Private-Data.desktop /etc/xdg/autostart/
```An alternative method could be ```
 cp /home/antony/Access-Your-Private-Data.desktop /etc/xdg/autostart/
``` **and IF and ONLY IF** cp command NOT return any error , then you can remove-delete the file ```
rm /home/antony/Access-Your-Private-Data.desktop
```That we want to achieve is to mv(move) the file Access-Your-Private-Data.desktop to the path that belongs. 

I assume (but I am not sure) you , somehow , accidentally moved this file in your /home directory. 
Also I assume that you have been encrypted your /home directory. 
This .desktop file , has a command inside that must executed at startup .
> **rem18 said:**
> 
 cat /home/antony/Access-Your-Private-Data.desktop
_Name=Access Your Private Data
-Genericname=Access Your Private Data
**Exec=/usr/bin/ecryptfs-mount-private**
Terminal=true
Type=Application
Categories=System;Security;
X-Ubuntu-Gettext-Domain=encryptfs-utils

> **rem18 said:**
> 
I dont have a problem to copy your instructions as I am using 
a different pc for your instructions to the one that has the problem
My problem now if to make the tab or do mean something else?

If you have no problem to copy the instructions then , forger about Tab key. 
Tab key is another story. Its a facility that you can use to fill automatically paths/names in Terminal.
> **rem18 said:**
> Also you have changed the instructions of what you want me to do?

No, the instructions are the same. The general idea is to move that file , from your /home to /etc/xdg/autostart/

---

### Post by Gone fishing on 2012-09-14
Something is odd what is your user name? what is the name of your home directory? remember Linux is case specific? I would chown the whole of your home directory recurisively using the -R switch

---

### Post by rem18 on 2012-09-15
@GoneFishing.
As I said all I did was change my login password and then change it back again and after it gave me this error.
I did not do anything but shut down after re-setting the password
I did not touch any directories or anything else.
The only thing I did do was the fast shutdown on this laptop by holding down off uotton
Can you write me out the specific code so I dont make any error
Thanks

---

### Post by rem18 on 2012-09-15
OK
mv /home/antony/Access-Your-Private-Data.desktop /etc/xdg/autostart/
gives cannot stat no such file or directory
An alternative method could be  	Code:
 	 cp /home/antony/Access-Your-Private-Data.desktop /etc/xdg/autostart/
gives cannot stat no such file or directory 

 **and IF and ONLY IF** cp command NOT return any error , then you can remove-delete the file 

I think form what we did before we are sure the data is there right also becuase just changing the password wouldnt cancel it.
Maybe its time to upgrade the laptop from 11.10 to 12.04 and first copy my data what do you guys think?
I have to go and get another external HD as I am short of space but maybe this is the answer now and you guys want to advise me how to do it safely to preserve the most data and permissions?
Alternatively I could copy the data into the w7 partition I have on this laptop as there is plenty of space there and Ubuntu shouldnt touch w7 I Think
What do you think?
Thanks

---

### Post by NikTh on 2012-09-15
> **rem18 said:**
> 
Alternatively I could copy the data into the w7 partition I have on this laptop as there is plenty of space there and Ubuntu shouldnt touch w7 I Think
What do you think?
Thanks

Hi , 
yes you can do this alternative . Copy your important data to W7 partition and then install Ubuntu 12.04 from a Live CD/Usb. It would be a GOOD IDEA to NOT UPGRADE. Fresh Install is much better (especially in your situation). 

And DO NOT encrypt your /home directory during installation nor after. 
If you want you can encrypt one folder to keep your secrets  :) 

Good Luck 

[CENTER]Thanks
[/CENTER]

---

### Post by rem18 on 2012-09-15
I just tried to login as  other to at least use that laptop to download the 12.04 64b but it hangs
Please advise how to create a new user. So I can at least use the laptop to download Ubuntu 64b
Thanks

---

### Post by rem18 on 2012-09-15
@Nik
First we are sure the home directory is there right?
Second it wont be inaccessible or somethingonce copied over an launched on new system? If its encrypted etc?
Third please advise me how to copy it over to w7 partition safely thanks
Fourth as I wrote at the moment I cant access login as antony was only user

---

### Post by rem18 on 2012-09-15
Just thinking what about the  very longsecurity paraphrase that Ubuntu asks you to make? Would that be of any use ?
I have that

---

### Post by NikTh on 2012-09-15
> **rem18 said:**
> @Nik
First we are sure the home directory is there right?
Second it wont be inaccessible or somethingonce copied over an launched on new system? If its encrypted etc?
Third please advise me how to copy it over to w7 partition safely thanks
Fourth as I wrote at the moment I cant access login as antony was only user

Yes , you have right. I didn't think of that. 

You cannot access your files if are encrypted. Neither from LiveCD. EncryptFS is a powerful tool. 

Try to do something else.. 

When you are in login screen press Ctrl+Alt+F2 to revert in Console. (Black screen). Login there with username & password and the give these commands

```
sudo service lightdm stop 
sudo ecryptfs-mount-private
sudo service lightdm start
``` 

Try to login again. 

Thanks

---

### Post by rem18 on 2012-09-15
Hello yes 
So I entered
sudo service lightdm stop 
asked for passwrod which I entered
=Uknown instance:

 sudo ecryptfs-mount-private
= Enter your login passphrase
I tried entering my paraphrase 
but that wasnt accepted and after it gave me 
error: your passphrase is incorrect

---

### Post by rem18 on 2012-09-15
On my passphrase I have an 0 with a dot in the middle..I cant remember if I did this to undicate a zero or if maybe there is a symbol with this? do you know of one?

---

### Post by NikTh on 2012-09-15
> **rem18 said:**
> Hello yes 
So I entered
sudo service lightdm stop 
asked for passwrod which I entered
=Uknown instance:

 sudo ecryptfs-mount-private
= Enter your login passphrase
I tried entering my paraphrase 
but that wasnt accepted and after it gave me 
error: your passphrase is incorrect

Hi , 

you know ... if you  manage to give your passphrasse correctly , then I think your problem solved. It will be not necessary to re-install Ubuntu. 

A zero with dot in the middle ? 
Maybe another language ? 
Or maybe you mean this @  (Shift + 2 in my pc).

---

### Post by rem18 on 2012-09-15
I seem plagued with problems....
My password phrase that I kept is not accepted maybe I wrote it down wrong I dont know.
I think this article below is probably the solution but as my luck would have it this laptop has duel graphics so I cant see the live cd desktop due to a driver problem (I need to install the Radeon driver each time I install or update).
Take a look
[http://askubuntu.com/questions/38336/how-do-i-recover-my-data-from-an-encrypted-home-directory](http://askubuntu.com/questions/38336/how-do-i-recover-my-data-from-an-encrypted-home-directory)

Let me know if you can think of a solution for me to see the live cd desktop to try this method if not I will have to give up and install over and loose everything since last backup.
Is there a way to save my home folder from being overwitten somewhere in case eventually I find a solution?
Thanks

---

### Post by NikTh on 2012-09-16
Hi ,

> **rem18 said:**
> I think this article below is probably the solution but as my luck would have it this laptop has duel graphics so I cant see the live cd desktop due to a driver problem (I need to install the Radeon driver each time I install or update).
Take a look
[http://askubuntu.com/questions/38336/how-do-i-recover-my-data-from-an-encrypted-home-directory](http://askubuntu.com/questions/38336/how-do-i-recover-my-data-from-an-encrypted-home-directory)

Yes , this is a hack . I never used it , but it seems good. 

> **rem18 said:**
> Let me know if you can think of a solution for me to see the live cd desktop to try this method if not I will have to give up and install over and loose everything since last backup.
Is there a way to save my home folder from being overwitten somewhere in case eventually I find a solution?


If you have problems with your graphics in LiveCD , then try the NOMODESET boot option.
See here how : [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

OR 

try another LiveCD . (Ubuntu 12.10 , or 11.10) 

Thanks

---

### Post by rem18 on 2012-09-16
Nik thanks for that link
But I already know about nomodset
But it brings me to ubuntu@ubuntu and I dont know where to go from there
thanks

---

### Post by rem18 on 2012-09-16
I solved this now I hooked the laptop up to a HDMI ona TV and can see the live cd desktop.
Remember this if you get a black screen
But even following the proceedure it tells me my login password is wrong???!!!

---

### Post by NikTh on 2012-09-16
Hi , 
> **rem18 said:**
> 
But even following the proceedure it tells me my login password is wrong???!!!
> **NikTh said:**
> Hi ,
**I never used it **, but it seems good. 

As you can see , I told you that I never used it and for that I cannot help you with this specific hack. 

Although I believe that encrypt-fs is a strong tool and you cannot "crack" it so easy. 

Did you try to move the file to the /etc/xdg/autostart/ ? 

Just mount the drive where ubuntu installation is , and then connect to your /home and move the file 

e.g (I assume that Ubuntu installation is on /dev/sda2) 

```
sudo mount /dev/sda2 /mnt
cd /mnt 
sudo mv home/antony/Access-Your-Private-Data.desktop etc/xdg/autostart/ 
```be careful here cuz etc and home are listed UNDER /mnt , so the backslash in front of etc (/etc) or home(/home)  **will not do the job we want**.
Just give the commands with the order I gave them , but find the correct /dev/sd? for your Ubuntu installation. 
You can see it with ```
sudo fdisk -l
```In case that you cannot find the file (Access-Your-Private-Data.desktop) or mv command gives error , then give here the results of 
```
ls home/
ls home/antony
``` Of course FIRST you must be connected to /mnt 
```
sudo mount /dev/sda2 /mnt 
cd /mnt 
ls home/ 
ls home/antony/
```Thanks

---

### Post by rem18 on 2012-09-17
Hi
In the crack  for live cd I was able to do everything accept that it would not recognise the login password  for the directory even if it works for root etc.
I could find the directory media/XXXXXXXXXXXXXXX/home/antony/private etc
So its there

Anyway back to what you told me  so I drop down to root...I believe its sd8 that I have.
Its the Linux directory right?
sudo mount /dev/sda2 /mnt
Get=It gives me dev/sda8/already mounted or busy cd /mnt  sudo mv home/antony/Access-Your-Private-Data.desktop etc/xdg/autostart/
cannot stat no such file or directory

I reality I have downloaded 12.04 64b as I thought to give up. It would be nice to save the last home directory but we are doing a lot of work without sucess.
If you have an idea how to save the home directory data it would be nice but I think I need permissions,
Regards

---

### Post by rem18 on 2012-09-17
ls  home/  =  cannot....no such.......
ls home/antony = no such

---

### Post by oldfred on 2012-09-17
Spaces and order are important. Normally after any command you need a space. And paths have to be valid. So home/ is not valid.

fred@fred-Precise:~$ ls home/
ls: cannot access home/: No such file or directory
fred@fred-Precise:~$ ls /home
fred

---

### Post by NikTh on 2012-09-17
> **oldfred said:**
> Spaces and order are important. Normally after any command you need a space. And paths have to be valid. So home/ is not valid.

fred@fred-Precise:~$ ls home/
ls: cannot access home/: No such file or directory
fred@fred-Precise:~$ ls /home
fred

Inside the /mnt directory (consider /mnt as /root) you can give the command ```
ls home/ 
```do this in your current install 

```
cd / 
ls home/
```> **rem18 said:**
> 
Anyway back to what you told me  so I drop down to root...I believe its sd8 that I have.
Its the Linux directory right?
sudo mount /dev/sda2 /mnt
Get=It gives me dev/sda8/already mounted or busy cd /mnt  sudo mv  home/antony/Access-Your-Private-Data.desktop etc/xdg/autostart/
cannot stat no such file or directory

Please follow these : 

1. Boot from the LiveCD/Usb you have
2. Click "Try Ubuntu" 
3. Open a terminal and give this command
```
sudo fdisk -l
```Post the results back here.

Thanks

---

### Post by rem18 on 2012-09-17
cd /  ls home/

= antony in blue
then back to root
Will try the cd test now revert in a while.

@Fred
Fred dont judge me by the pastings here 
on laptop I triple check if it doesnt give 
a result but its ard to write code all the time 
of course so mistakes can happen

---

### Post by rem18 on 2012-09-17
@nik
in live cd
sudo fdisk -l
= a whole list of partitions from dev/sda1 to sda9
What do you want me to do now?
Thanks

---

### Post by rem18 on 2012-09-17
I think  I want to now just install 12.04 so if I can save my old home folder thats nice

Maybe its worth an over install attempt first rather than a clean isntall
Maybe it would recover my files if I use same user name and password?
But at least  I might have my programmes and settings?

If not I can still run a clean install after
thanks

---

### Post by NikTh on 2012-09-17
Hi , 
If you are tired you can do a fresh install . I doubt if you can recover your encrypted data after a fresh install. 

If everything are encrypted , then you cannot save anything. Either your data or configurations files or settings. You must De-crypt first and then you can save. 

Yes give the results here. Post them inside [noparse]```
 brackets 
```[/noparse] 

**[noparse]```
The Results Here
```[/noparse]**

Thanks

---

### Post by rem18 on 2012-09-17
@nik
Lets try one more time if you have an idea

I sent you the result
What did you need after
in live cd
sudo fdisk -l
= a whole list of partitions from dev/sda1 to sda9
What do you want me to do now?
Thanks

---

### Post by NikTh on 2012-09-17
> **rem18 said:**
> @nik
Lets try one more time if you have an idea

I sent you the result
What did you need after
in live cd
sudo fdisk -l
= a whole list of partitions from dev/sda1 to sda9
What do you want me to do now?
Thanks

Give the results here and we will see.

do not forget : Put the results between [noparse]```
brackets
```[/noparse]

Thanks

---

### Post by rem18 on 2012-09-17
ahh you need them all? its a lot and in live cd I dont think I can do a screen shot maybe I need to take a photo.

---

### Post by NikTh on 2012-09-17
> **rem18 said:**
> ahh you need them all? its a lot and in live cd I dont think I can do a screen shot maybe I need to take a photo.

> **rem18 said:**
> I solved this now I hooked the laptop up to a HDMI ona TV and can see the live cd desktop.
Remember this if you get a black screen

Why ,photo ? 

Just copy-paste the results from terminal in here. 

You said you sovled the problem with screen.

---

### Post by rem18 on 2012-09-17
No I am using another laptop that one is not working now as I cant access login can I?
here I include a photo jpeg to see ok?

---

### Post by NikTh on 2012-09-17
> **rem18 said:**
> No I am using another laptop that one is not working now as I cant access login can I?
Hi,

Well , lets clarify some things , cuz either I misunderstood or you misunderstood.

Do you have a LiveCD or LiveUsb of Ubuntu ? LiveCD or Usb it means the CD or Usb where you installed Ubuntu. 

IF yes , then boot from there. Put the CD or USb in Corrupted Laptop and boot from there. 

After a successful boot , click "Try Ubuntu" and open a terminal and post here the results of , sudo fdisk -l. 

You can open Firefox and post here anything you want , Yes  from a LiveCD or Usb (Firefox included). 

Can you do that ?

Thanks

---

### Post by rem18 on 2012-09-17
Nik there is no wifi in live cd.
So I saved it to a text file and now I paste it here OK?

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xc469f6b2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   482551807   241172480    7  HPFS/NTFS/exFAT
/dev/sda3       482553854  1201666047   359556097    f  W95 Ext'd (LBA)
Partition 3 does not start on physical sector boundary.
/dev/sda4      1201666048  1250263039    24298496   27  Hidden NTFS WinRE
/dev/sda5       482553856   842109951   179778048    7  HPFS/NTFS/exFAT
/dev/sda6      1194369024  1201666047     3648512   82  Linux swap / Solaris
/dev/sda7      1187072000  1194366975     3647488   82  Linux swap / Solaris
/dev/sda8       842110976  1179760639   168824832   83  Linux
/dev/sda9      1179762688  1187059711     3648512   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by NikTh on 2012-09-17
Ok , 

as you are there now , I mean LiveCD in problematic Laptop , do as follows and give the results back here (save them in .txt as you did) 

```
sudo mount /dev/sda8 /mnt 
ls /mnt 
``` 

Thanks

---

### Post by rem18 on 2012-09-17
here you are
ubuntu@ubuntu:~$ sudo mount /dev/sda8 /mnt
ubuntu@ubuntu:~$ ls /mnt
bin    dev   initrd.img      lib64       mnt   root  selinux  tmp  vmlinuz
boot   etc   initrd.img.old  lost+found  opt   run   srv      usr  vmlinuz.old
cdrom  home  lib             media       proc  sbin  sys      var  work
ubuntu@ubuntu:~$

---

### Post by NikTh on 2012-09-17
Continue with 
```
cd /mnt/home/
ls
```

---

### Post by rem18 on 2012-09-17
ubuntu@ubuntu:~$ cd /mnt/home
ubuntu@ubuntu:/mnt/home$ ls
antony
ubuntu@ubuntu:/mnt/home$

---

### Post by NikTh on 2012-09-17
```
cd antony && ls
```

---

### Post by rem18 on 2012-09-17
ubuntu@ubuntu:~$ cd /mnt/home
ubuntu@ubuntu:/mnt/home$ ls
antony
ubuntu@ubuntu:/mnt/home$ cd antony && ls
bash: cd: antony: Permission denied
ubuntu@ubuntu:/mnt/home$ ^C
ubuntu@ubuntu:/mnt/home$

---

### Post by NikTh on 2012-09-17
```
sudo -i 
cd antony 
ls
```

---

### Post by rem18 on 2012-09-17
ubuntu@ubuntu:~$ cd /mnt/home
ubuntu@ubuntu:/mnt/home$ ls
antony
ubuntu@ubuntu:/mnt/home$ cd antony && ls
bash: cd: antony: Permission denied
ubuntu@ubuntu:/mnt/home$ ^C
ubuntu@ubuntu:/mnt/home$ sudo -i
root@ubuntu:~# cd antony
-bash: cd: antony: No such file or directory
root@ubuntu:~# ls
root@ubuntu:~#

---

### Post by NikTh on 2012-09-17
```
cd /mnt/home/antony/
ls
```

---

### Post by rem18 on 2012-09-17
ubuntu@ubuntu:~$ cd /mnt/home
ubuntu@ubuntu:/mnt/home$ ls
antony
ubuntu@ubuntu:/mnt/home$ cd antony && ls
bash: cd: antony: Permission denied
ubuntu@ubuntu:/mnt/home$ ^C
ubuntu@ubuntu:/mnt/home$ sudo -i
root@ubuntu:~# cd antony
-bash: cd: antony: No such file or directory
root@ubuntu:~# ls
root@ubuntu:~# sudo -i
root@ubuntu:~# cd antony
-bash: cd: antony: No such file or directory

root@ubuntu:~# cd /mnt/home/antony/
root@ubuntu:/mnt/home/antony# ls
README.txt
root@ubuntu:/mnt/home/antony# ^C
root@ubuntu:/mnt/home/antony#

---

### Post by NikTh on 2012-09-17
> **rem18 said:**
> 
```
root@ubuntu:~# cd /mnt/home/antony/
root@ubuntu:/mnt/home/antony# ls
README.txt
```

I cannot see the .desktop file. Where is it ? disappeared ? (Access-Your-Private-Data.desktop)

lets see 
```
ls /mnt/etc/xdg/autostart | grep -i access
```or 

```
sudo -i 
cd /mnt 
find -name Data.desktop
```

---

### Post by rem18 on 2012-09-17
Hi I did them both for you

root@ubuntu:/mnt/home/antony# ls /mnt/etc/xdg/autostart | grep -i access
Access-Your-Private-Data.desktop
root@ubuntu:/mnt/home/antony# 
root@ubuntu:/mnt/home/antony# sudo -i
root@ubuntu:~# cd /mnt
root@ubuntu:/mnt# find -name Data.desktop
root@ubuntu:/mnt#

---

### Post by NikTh on 2012-09-17
> **rem18 said:**
> ```

root@ubuntu:/mnt/home/antony# ls /mnt/etc/xdg/autostart | grep -i access
Access-Your-Private-Data.desktop
```

It seems that , somehow you successfully moved the file to the right place. 

I cannot help anymore. Logically you have no problem now , except that you must know your Passphrase (encrypt-fs password) to access your data. 

That was my goal 
> **NikTh said:**
> The general idea is to move that file , from your /home to /etc/xdg/autostart/

We succeed it . 

From now on , I cannot help to recover your data IF you don't know your Passphrase.

Thanks

---

### Post by rem18 on 2012-09-17
I have the passphrase but it doesnt work it seems but I just saw that the 0(zero) in terminal is the zero with dot in middle and I have that in my passphrase so maybe thats the answer to why I cant get passphrase to work
Do you think that it is sensitive to this symbol?
Can you remind me how to try and get to the situation to enter passphrase again please?
Thanks

---

### Post by NikTh on 2012-09-17
> **rem18 said:**
> I have the passphrase but it doesnt work it seems but I just saw that the 0(zero) in terminal is the zero with dot in middle and I have that in my passphrase so maybe thats the answer to why I cant get passphrase to work
Do you think that it is sensitive to this symbol? 
Of course is sensitive. To all symbols , numbers , Capitals or anything else. 
The symbol O with dot in the middle in terminal, is zero. 

> **rem18 said:**
> Can you remind me how to try and get to the situation to enter passphrase again please?


Now that you have the file in right place , logically you will have no problem. It will just ask you for the password (Passphrase). 

Or else ,you must run bellow command to the terminal 
```
sudo ecryptfs-mount-private
```Be cause of sudo , you must give both passwords. First yours (as admin) and then it will ask you for the Passphrase. 

Thanks (Good Luck)

---

### Post by rem18 on 2012-09-17
No
sudo ecryptfs-mount-private
gives encrypted private directory is not setuo properly

---

### Post by rem18 on 2012-09-17
No
sudo ecryptfs-mount-private
gives encrypted private directory is not setup properly

---

### Post by rem18 on 2012-09-17
so let me expalin better
It finds the encrypted directory and asks me for my login passphrase but when I use it says its wrong.......

ubuntu@ubuntu:/media$ sudo ecryptfs-recover-private
INFO: Searching for encrypted private directories (this might take a while)...
INFO: Found [/mnt/home/.ecryptfs/antony/.Private].
Try to recover this directory? [Y/n]: y
INFO: Enter your LOGIN passphrase...
Passphrase:

---

### Post by NikTh on 2012-09-17
> **rem18 said:**
> so let me expalin better
It finds the encrypted directory and asks me for my login passphrase but when I use it says its wrong.......

ubuntu@ubuntu:/media$ sudo ecryptfs-recover-private
INFO: Searching for encrypted private directories (this might take a while)...
INFO: Found [/mnt/home/.ecryptfs/antony/.Private].
Try to recover this directory? [Y/n]: y
INFO: Enter your LOGIN passphrase...
Passphrase:

I assume that above is from LiveCD. Cuz I see /mnt/home/.......... 

So try to use the hack  from askubuntu.com . 

Create a user with the same name (antony) and then logout and login with this username. 
Then give again the command ```
sudo ecryptfs-recover-private
``` and try the Passphrase again. 

Thanks

---

### Post by rem18 on 2012-09-18
Hi  Nik
So I did that again
I under livecd I created an admin user with same name and password as my original
after finding the directory It asks for my login password 
NB LOGIN password not mount password
I give it
it says error look here

antony@ubuntu:~$ sudo ecryptfs-recover-private
INFO: Searching for encrypted private directories (this might take a while)...
INFO: Found [/media/b2e6686c-4054-498b-a40f-f1235530aeb0/home/.ecryptfs/antony/.Private].
Try to recover this directory? [Y/n]: y
INFO: Enter your LOGIN passphrase...
Passphrase: 
Error: Unwrapping passphrase and inserting into the user session keyring failed [-5]
Info: Check the system log for more information from libecryptfs
antony@ubuntu:~$ 

so lets go back to the  begining.
I changed my 6 digit login password to an 8 digit one  for antony then after a few minutes I changed it back again.
I know it accepted this as it it needs password to set new one right.
I powered down as a fast power off just holding the power button on this laptop.. I do it always for all laptops as then everything is back when I power on and Ubuntu does this sooo well.
Later I switched on and logged in and If it didnt like the login password now it would have stopped me in login not have gone on for 1m right?after 1m it gives this ICEauthority message.
So it looks like the login password was ok but it couldnt find ICE.

So we have seen the directory is there as its listed also above media/b2xxxxxxxxxxx
I can use my login password for root too
But it wont accept it now for the home encrypt
But it doesnt ask me for the mount password which I have (the 32digit one created by ubuntu).
Also this mount password is a bugger as I wrote it on a paper but its so complicated that I am not even 100% sure of my own handwriting.. So I suggest to everyone to print it rather than write it by hand..

Ok is this all now clear
Any suggestions out there?

---

### Post by rem18 on 2012-09-19
@Nik
I have solved this.
The problem was with 11.10 in some way.
I had given up so I put the 12.04 cd in to start the new installation.
Well I thought that I would just try the proceedure 1 more time.

ubuntu@ubuntu:/media$ sudo ecryptfs-recover-private
INFO: Searching for encrypted private directories (this might take a while)...
INFO: Found [/mnt/home/.ecryptfs/antony/.Private].
Try to recover this directory? [Y/n]: y

Well with the 12.04 live cd it all went correctly  and offered me the chance to use my mount passphrase at last
And I just copied the home directory into my w7 partition while I re-installed.
So the lesson is use the 12.04 live cd even if you are running 11.10 etc.
Alls well that ends well.

Nik if you read this let me know and thanks for your all your efforts.

---

### Post by NikTh on 2012-09-19
Hi , 
VERY GOOD news. !!! 

Glad you solved it. 

Thanks

---

