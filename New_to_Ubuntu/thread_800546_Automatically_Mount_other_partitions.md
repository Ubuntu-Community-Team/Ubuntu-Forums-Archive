---
title: "Automatically Mount other partitions"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by speedemonV12 on 2008-05-19
Hi, i keep my music on my other partitions, other than the ubuntu partition, and i have my music libraries set to look to those folders. So when i boot up Ubuntu, and open my media player, i get no music until i click the drive from place in the ubuntu menu.. how can i set it to automatically mount the drive(s)?

---

### Post by autocrosser on 2008-05-20
It requires that you change your /etc/fstab file. I edit my file to mount partitions to /media--that way they are mounted easily & after you make a conf change, they will show on your desktop also.

First--let's look at your /etc/fstab file--post it & let's see.

second--look at ADD/REMOVE or Synaptic & install gconf (also called Configuration Editor)--if you don't have it installed--then install it.

---

### Post by speedemonV12 on 2008-05-20
this is the fstab file. 


```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=eb6de634-7280-48d1-8aad-eccac6f3908c /               ext3    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```


I have three partitions.. one for Mac, one for Windows, and one for Ubuntu, I would like to automatically mount Mac partition, windows, im indifferent to. 


i already have configuration editor installed

---

### Post by autocrosser on 2008-05-20
OK--the only thing there is your Ubuntu install (/ partition) & a cdrom

Are your media partitions removable, windows (fat32/NTFS) or networked?

---

### Post by autocrosser on 2008-05-20
Sorry--didn't read whole post--The mac partition--So fire up gparted & see what you partition table looks like. A screenshot would be nice---

---

### Post by speedemonV12 on 2008-05-20
here it is. 

[[IMG]http://img246.imageshack.us/img246/7243/screenshotdevsdagpartedwc5.th.png[/IMG]](http://img246.imageshack.us/my.php?image=screenshotdevsdagpartedwc5.png)

---

### Post by autocrosser on 2008-05-20
Depending on how your mac partition is formatted you should have very little problem adding it to your fstab (remember you need to edit it as root).

The guide I've used is: [http://ubuntuforums.org/showthread.php?t=283131&highlight=edit+fstab](http://ubuntuforums.org/showthread.php?t=283131&highlight=edit+fstab)

When you look at the gparted info, it will tell you what things are formatted with--It's a given that the windows will be fat32 or NTFS and you know that your Ubuntu is at /dev/sda3--so it should be very easy to find the mac.

Look at the guide to setup your fstab & then in Config Editor--Tic Apps & scroll down to Nautilus--Tic it & in Desktop check volumes_visible--you can do any other editing you want at that time.

After you are happy with the fstab, you will need to reboot to see changes. The config editor changes happen in real time, but fstab is only read at boot.

---

### Post by autocrosser on 2008-05-20
OK /dev/sda2 is your target & you should also make sure that you have everything needed to read hfs+. 

Open Synaptic & search for hfs---install hfsplus & hfsutils

---

### Post by autocrosser on 2008-05-20
You could just try adding:  /dev/sda2  /media/Macintosh HD  hfs+ defaults 0 0

That is simpler than the UUID way--I think you can't easily get a UUID for a hfs+ partition

After you edit the fstab, double-check it & then check in /media that there is a "Macintosh HD"---if not, as root add a folder & name it "Macintosh HD"

---

### Post by speedemonV12 on 2008-05-22
> **autocrosser said:**
> You could just try adding:  /dev/sda2  /media/Macintosh HD  hfs+ defaults 0 0

That is simpler than the UUID way--I think you can't easily get a UUID for a hfs+ partition

After you edit the fstab, double-check it & then check in /media that there is a "Macintosh HD"---if not, as root add a folder & name it "Macintosh HD"

where do i add this line in the fstab file? anywhere?

/dev/sda2  /media/Macintosh HD  hfs+ defaults 0 0

---

### Post by autocrosser on 2008-05-22
I would put on the line after the UUID for your main drive.



> **speedemonV12 said:**
> where do i add this line in the fstab file? anywhere?

/dev/sda2  /media/Macintosh HD  hfs+ defaults 0 0

---

### Post by speedemonV12 on 2008-05-23
done and it worked ! thanks a lot!

---

### Post by autocrosser on 2008-05-23
Glad to know I helped---Have a great day!!

---

### Post by speedemonV12 on 2008-05-24
ok, so turns out that it only worked for the one time.. now i get this error everytime that i try to mount it:

[[IMG]http://img139.imageshack.us/img139/1050/screenshotal2.th.png[/IMG]](http://img139.imageshack.us/my.php?image=screenshotal2.png)

and this is what my fstab file looks like.. exactly the way you told me to do it:

[[IMG]http://img357.imageshack.us/img357/7/screenshotfstabetcgeditel7.th.png[/IMG]](http://img357.imageshack.us/my.php?image=screenshotfstabetcgeditel7.png)

any ideas?

---

### Post by autocrosser on 2008-05-24
Yes--looks like fstab is not liking Macintosh HD--try changing it to just Macintosh or Macintosh_HD--I think that the space is the problem--remember to edit the fstab entry & the /media entry also (they both must be the same).

Then reboot to check the changes---

---

### Post by speedemonV12 on 2008-05-24
now i get the error that i am not privaledged to mount the drive/...

---

### Post by smarks on 2008-05-24
I am having an issue with my video card and in dire need of help. i dont know why this isnt working. this is what i get.

sh: Can't open NVIDIA-Linux-173.08-x86-pkg1.run

I read somewhere to do this and its not working.

smarks@smarks:~$ cd desktop
bash: cd: desktop: No such file or directory

If i trying to run the file in terminal it comes up but naturally its wont work. I just wanna install the driver Please Help.

---

### Post by autocrosser on 2008-05-24
> **speedemonV12 said:**
> now i get the error that i am not privaledged to mount the drive/...

Did you edit fstab as root? If so, open a nautilus window as root & goto /media--Right-click on the drive & look a properties--if permissions are root, change them to your user. Then try opening the drive as your user.

---

### Post by autocrosser on 2008-05-24
> **smarks said:**
> I am having an issue with my video card and in dire need of help. i dont know why this isnt working. this is what i get.

sh: Can't open NVIDIA-Linux-173.08-x86-pkg1.run

I read somewhere to do this and its not working.

smarks@smarks:~$ cd desktop
bash: cd: desktop: No such file or directory

If i trying to run the file in terminal it comes up but naturally its wont work. I just wanna install the driver Please Help.


There is a very good tutorial in the Tutorials & Tips forum on doing that---I'll say that you should be calling cd /home/"your user"/desktop for the correct full way to do it....or try cd /desktop.

---

### Post by smarks on 2008-05-24
yes permission are set to me Owner. I have looked all over the place. I have also tried /home/user/desktop sh /NVIDIA-blah blah. i get this

smarks@smarks:~$ sudo sh NVIDIA-Linux-173.08-x86-pkg1.run
[sudo] password for smarks: 
sh: Can't open NVIDIA-Linux-173.08-x86-pkg1.run

this too
smarks@smarks:~$ sh /home/smarks/desktop/NVIDIA-Linux-173.08-x86-pkg1.run
sh: Can't open /home/smarks/desktop/NVIDIA-Linux-173.08-x86-pkg1.run

---

### Post by smarks on 2008-05-24
smarks@smarks:~$ cd /home/smarks/desktop
bash: cd: /home/smarks/desktop: No such file or directory
smarks@smarks:~$ cd /desktop
bash: cd: /desktop: No such file or directory
also
smarks@smarks:~$ cd /home/smarks/desktop/NVIDIA-Linux-173.08-x86-pkg1.run
bash: cd: /home/smarks/desktop/NVIDIA-Linux-173.08-x86-pkg1.run: No such file or directory

---

### Post by speedemonV12 on 2008-05-26
Edit: deleted.

---

### Post by speedemonV12 on 2008-05-26
> **autocrosser said:**
> Did you edit fstab as root? If so, open a nautilus window as root & goto /media--Right-click on the drive & look a properties--if permissions are root, change them to your user. Then try opening the drive as your user.

hey, i edited the fstab as root, and make the MacintoshHD folder as root also. It would not allow  me to make the folder without being root. So i changed permissions the owner of the folder, and the group of the folder MacintoshDH in /Media to me, and it still doesnt work.. anything else?

---

### Post by autocrosser on 2008-05-26
Hmmmm---I open nautilus as root & nav to the /media folder---right-click on the folder I want to change permissions on (after I make it as root)--use "Properties" & click the permissions tab--then change all permissions to my user---not root.

---

### Post by speedemonV12 on 2008-05-29
ya, still says i dont have permission to mount the drive.. any suggestions?

---

### Post by siimer on 2008-05-29
Hey,

I am a total greenhorn when it comes to Linux and Ubuntu.

I have tried basically all of the offered solutions, but none of them has worked. Actually it has only turned up to be even worse, now i cant access the Storage (NTFS) space at all :P

I am using the "storage" both in windows and ubuntu, at least trying to :)

The error message is the following:

siim@Manufaktuur:~$ sudo mount -a
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda2': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda2 /media/sda2 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda2 /media/sda2 ntfs-3g defaults,force 0 0
mount: special device /dev/disk/by-uuid/83e745c9-e97e-4f07-aca2-d13b4ebf2b8c does not exist
mount: special device /dev/disk/by-uuid/F4E1-19EC does not exist
mount: special device /dev/hda1 does not exist
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda6': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda6 /media/Storage -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda6 /media/Storage ntfs-3g defaults,force 0 0


I have tried both of those options but they also dont work:p

Is there somebody who can help?

---

### Post by autocrosser on 2008-06-01
Hi speedemonV12--

Let's try something--Open a terminal & do sudo nautilus--then nav to the /media folder & see if you can use the the MacintoshHD folder. ( I assume that it's mounted there) If so, good--it's mounting on startup..

I forgot a line in fstab (if it is really mounting at start), instead of: /dev/sda2  /media/Macintosh HD  hfs+ defaults 0 0

Let's do: /dev/sda2  /media/Macintosh HD  hfs+ user, auto 0 0 (copy-paste it exactly as it is here)

& see if you can get into it---For more info on mount & fstab--open a terminal & do:  man mount or man fstab

---

### Post by autocrosser on 2008-06-01
Hi siimer--

You need to boot Windoze & use your drive--you had a unclean shutdown on it & it is flagged to not be used. You can also use ckdisk on it--I'm not sure as to the exact way of doing that during a Windows boot.... 

I normally use a EXT3 partition to share between the two--If you google EXT3 for Windows, there is a nice little extension that "allows" Windows to see EXT2/3 partitions (in Windows, your EXT3 will be read as EXT2)--that way, you can be "native" with your storage & do regular fsck work with it.

There is a bit of /etc/fstab work to do when you change it--after formatting/partitioning, you need to edit the /fstab file to reflect the change...As I have noted above, you can just write a line that would look "sort-of" like this--- /dev/sda6  /media/Storage  ext3  user, auto 0 2 ( the 2 at the end allows native fsck checks at boot time)

---

### Post by billybisson on 2008-11-09
Hi Guys,

I am new to Ubuntu forums and don't know how to start a fresh thread.

The question is related to mounting HFS+ partitions.

When I installed Ubuntu on my Mac Book and sorted out reFIT, it recognised the Mac OS HFS+ partition and mounting it was trivial, simply click on the HFS+ drive under my computer in gnome, it gave me read only access.

After mounting it, I right clicked to look at the preferences and saw the permissions tab was empty? I then looked under the Volume tab and tried to be clever and change the details part from ro to rw. It said the changes will not be activated until remounting, which I tried and now it gives me an error, not able to mount that partition. The problem is the Volume tab no longer appears under preferences when I right click on the Mac OS X HD icon, I guess because it is not mounted. But because I can't mount it I can't change the details. 

How do I revert to the previous set up? I looked under fstab before meddling and noticed no entry for the HFS+ partition, so without having to add a fstab entry, how do I change back to the previous settings?

I could see no help under gconf-editor - it had an entry under HFS (no HFS+) but the details and UUID part were all empty?

Can someone please tell me how to revert to the status quo setup for HFS+ drives without having to add entries under fstab because I wish not to automount the Mac OS X partition on boot up.

Thanks

---

### Post by nerver on 2008-11-25
billybisson:

Unfortunately I don't know how you can revert it back, but I do know how you can mount the drive. If you have everything installed on your system to read/write to an hfs filesystem then you could do the following:
In a terminal:

step 1:

sudo fdisk -l
 which will give you a list of all your partitions. Find your hfs partition (should be /dev/xxxx )

step 2:

make a directory to mount to:

sudo mkdir /mount/point 

(ie sudo mkdir /media/HFSDrive)

Step 3:

sudo mount -t auto /dev/xxxx /mount/point

and just replace "/dev/xxxx with the hfs parition you located in step 1 and replace /mount/point with the location you created in step 2)

I hope this all works. Let me know if you run into any trouble.

Cheers,
-Sean

---

