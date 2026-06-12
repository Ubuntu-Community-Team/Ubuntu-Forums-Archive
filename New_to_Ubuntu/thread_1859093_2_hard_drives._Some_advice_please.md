---
title: "2 hard drives. Some advice please"
date: 2011-10-13
forum: New to Ubuntu
---

### Post by barauc on 2011-10-13
Hi, I have an old pc with two 20GB hard drives. For testing purposes I have Linux Mint installed on one and Ubuntu on the other.

Decided to go with Ubuntu and now I need help uninstalling Mint and make that drive part of Ubuntu because I want to store my music on it. Not sure what to do.

Thanks.

---

### Post by ikt on 2011-10-13
> **barauc said:**
> Decided to go with Ubuntu and now I need help uninstalling Mint and make that drive part of Ubuntu because I want to store my music on it. Not sure what to do.

You should be able to see the linux mint drive from ubuntu, then you just select all the files on the linux mint drive and delete.

---

### Post by sadaruwan12 on 2011-10-13
For your problem this link will help you if there any help needed ask me I've done this and it's working like a charm.

My Blog [Link]("http://myfossness.blogspot.com/2010/08/how-to-install-new-hard-disk-with-anuto.html")

---

### Post by ezramorris on 2011-10-13
Alternatively you could use the inbuilt Disk Utility and either format or delete and recreate a new partition on that drive.

P.S. Welcome to Ubuntu Forums! :-)

---

### Post by barauc on 2011-10-14
Thanks everyone. I formatted the volume but now there is only one file called "lost and found." Can I now just right click on the drive and create new folders like Music, Documents etc?

I tried to follow your advice Sadaruwan12, but everytime I type anything in terminal it asks for a password and I do not know how to do that because if I type in my password it does not accept it. Did Google but did not find a answer yet. Maybe you can help.

Thanks

---

### Post by ezramorris on 2011-10-14
> **barauc said:**
> Can I now just right click on the drive and create new folders like Music, Documents etc?

Yes.

---

### Post by barauc on 2011-10-16
Thanks for the reply ezramorris. I created a folder on the formatted drive by right clicking and choosing new folder naming it Music. Then I transferred some music from my vista pc and imported that into Banshee.

Everything works fine until I switch off or restart my computer. Banshee and Vlc player does not remember the location of the files and every time I start my computer I have to import music again.

If I import music from the same drive Ubuntu is installed on I do not have this problem. 

Any ideas?

Thanks

---

### Post by -kg- on 2011-10-16
You'll need to add that partition to your fstab file.

[How to fstab]("http://ubuntuforums.org/showthread.php?t=283131")

---

### Post by barauc on 2011-10-16
Thanks kg, followed your links and got more confused. I just upgraded to ubuntu 11.10 and noticed in the disk utility that this drive is mounted at /media/new volume.

I noticed that the post you send me to is rather old. Is everything still relevant to 11.10?

Can this not be automated. As I've mentioned in the post above my terminal keeps asking for a pastword and when I type it in nothing happens.

Thanks

---

### Post by ezramorris on 2011-10-16
> **barauc said:**
> As I've mentioned in the post above my terminal keeps asking for a pastword and when I type it in nothing happens.

The password does not show up (as asterisks etc.) as you type it, but it will accept it.

Ezra.

---

### Post by ezramorris on 2011-10-16
pysdm is mentioned in that other thread, and I would recommend it if you want a graphical way to achieve this.

[LIST=1]
[*]Once installed, launch Storage Device Manager, by searching for it in the launcher.* Down the left hand side, you should see all your disks.
[*]Expand the correct drive, then click on the correct partition. If the application asks to configure it, allow it to do so.
[*]By default, the mountpoint should be set as /media/<device name>. This is fine unless you specifically want it to mount elsewhere.
[*]Next, click "Assistant". "The file system is mounted at boot time" should already be checked. Ensure that no other boxes on the "Mounting" tab are checked.
[*]In order to allow you to write to the filesystem, check "Owner user of the filesystem" and enter your username in the check box.
[*]Click OK, then apply and close.
[*]Next time you reboot, the drive should automount!
[/LIST]

* If you have an older version of Ubuntu, it will be in one of the menus, but I'm not sure which!

Ezra.

---

### Post by barauc on 2011-10-17
Thanks ezra, followed your advice and installed pysdm but get error message on startup. I have a few more things that i'm struggling with and I think I should start a new thread and list them all, or should I just continue here?

Thanks

---

### Post by ezramorris on 2011-10-17
> **barauc said:**
> Thanks ezra, followed your advice and installed pysdm but get error message on startup.

What error do you get?

Are you starting it from the launcher? You can do this by clicking on the Ubuntu icon at the top of the launcher, typing  [FONT="Courier New"]Storage Device Manager[/FONT] then clicking it.


> **barauc said:**
> I have a few more things that i'm struggling with and I think I should start a new thread and list them all, or should I just continue here?


It would probably be better to start a new thread.

Ezra.

---

### Post by barauc on 2011-10-17
Thanks Ezra, new thread here: [http://ubuntuforums.org/showthread.php?t=1862925](http://ubuntuforums.org/showthread.php?t=1862925)

---

### Post by ezramorris on 2011-10-17
> **barauc said:**
> Thanks Ezra, new thread here: [http://ubuntuforums.org/showthread.php?t=1862925](http://ubuntuforums.org/showthread.php?t=1862925)

As Q3 is related to this, I'll take a guess here:

Did you add anything to /etc/fstab before using pysdm? If so, it's possible that you could have the same disk listed twice.

To check/fix:

[LIST=1]
[*]Open a terminal and type: ```
gksudo gedit /etc/fstab
```
[*]Check that there is only one line for your partition. If there is two, delete the one you added manually.
[*]Save and exit.
[/LIST]

Ezra.

---

### Post by barauc on 2011-10-17
Hi Ezra, you were right, there were two entries in fstab. I deleted one but still get an error. Below is my fstab, can you see anything wrong?

sdb1-new volume is the drive I'm trying to mount.

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid  0  0  
# / was on /dev/sda1 during installation
UUID=7efefa99-055f-4193-b4ea-ee23e38b2c5d  /            ext4  errors=remount-ro    0  1  
# swap was on /dev/sda6 during installation
UUID=55a20981-5c1a-4651-83e9-fc23d037161b  none         swap  sw                   0  0  
/dev/sdb1                                  /media/New Volume  ext4  owner                0  0   

Since nobody has replied to my new thread yet, do you perhaps have any ideas about my booting problems? I'm used to having a disk in my dvd drive to get to grub, it is not really a problem, but why can I only boot through recovery mode?

Thanks

Bart

---

### Post by ezramorris on 2011-10-17
> **barauc said:**
> /dev/sdb1  /media/New Volume  ext4  owner  0  0   

It's best not to use a space in the mount point, else it will think that it is part of the next column:

```
/dev/sdb1  /media/NewVolume  ext4  owner  0  0   
```

If you insist on having a space, put in \040 instead:

```
/dev/sdb1  /media/New\040Volume  ext4  owner  0  0   
```

but I wouldn't recommend it.

Ezra.

---

### Post by egalvan on 2011-10-17
> **barauc said:**
> Hi Ezra, you were right, there were two entries in fstab. I deleted one but still get an error. Below is my fstab, can you see anything wrong?

sdb1-new volume is the drive I'm trying to mount.

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid  0  0  
# / was on /dev/sda1 during installation
UUID=7efefa99-055f-4193-b4ea-ee23e38b2c5d  /            ext4  errors=remount-ro    0  1  
# swap was on /dev/sda6 during installation
UUID=55a20981-5c1a-4651-83e9-fc23d037161b  none         swap  sw                   0  0  
**/dev/sdb1                                  /media/[COLOR="Red"]New Volume[/COLOR]  ext4  owner                0  0   **


If this was MY setup, i would change **New Volume** to something such as **music**...

> **/dev/sdb1                                  /media/[COLOR="Red"]music[/COLOR]  ext4  owner                0  0   **

file names with spaces are Windows-centric,
Unix/Linux prefers no spaces...

mounting volumes on /media should have them automatically show up on the desktop.

---

### Post by egalvan on 2011-10-17
I was perusing your other problem and found this

> 3. Until I installed PYSDM to mount my 2nd drive. Now when I boot from recovery I get this message:
 an error occured while mounting **[COLOR="Red"]/media/new[/COLOR]**. Press S to skip mounting or M for manual recovery.


as you can see,  using that space is giving Linux problems..

---

### Post by barauc on 2011-10-19
Thanks Ezra and everybody else for all your advice.

I installed Lubuntu for 2 reasons, lighter on resources for my old pc and it automatically mounts all mountable drives at start up.

Booting problems taken care of by using a universal usb installer progam which sets up Lebuntu to boot from usb. set bios to boot from usb-hdd and disabled all other boot options.

Now everything works beautifully!

Thank you

Bart

---

