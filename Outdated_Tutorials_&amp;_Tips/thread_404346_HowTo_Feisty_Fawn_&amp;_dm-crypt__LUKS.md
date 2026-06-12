---
title: "HowTo: Feisty Fawn &amp; dm-crypt / LUKS"
date: 2007-04-08
forum: Outdated Tutorials &amp; Tips
---

### Post by hyper_ch on 2007-04-08
**I. Introduction**

***Motivation***

Security is today one of the key aspects in our daily life - sometimes concious, sometimes unconcious. Security has many aspects and one of them is computer security or security of your or your business' computer data.

In this tutorial I will show how to encrypt a whole disk drive using (X)ubuntu Feisty, dm-crypt and LUKS.

I have gathered this information from various sources and put it all together. Those are:
- [http://www.hermann-uwe.de/blog/howto-disk-encryption-with-dm-crypt-luks-and-debian]("http://www.hermann-uwe.de/blog/howto-disk-encryption-with-dm-crypt-luks-and-debian")
- [https://systemausfall.org/wikis/howto/CryptoPartitionHowTo]("https://systemausfall.org/wikis/howto/CryptoPartitionHowTo")
- amayera in the #ubuntu channel on irc.freenode.org

***Warning***

This tutorial will destroy any data on the harddisk that you use. It is adviced to be very careful which harddisk you enter. Do not use it to encrypt your harddisk where you have Linux installed. The primary aim is to encrypt an additional harddisk that is used for date storage.

***Some legal considerations***

There are other encryption methods available. Foremost probably to mention is true-crypt which offers a greater extend of plausible deniabilty by having two levels of encryption. The idea behind that is, that if someone see that you have a large drive/partition with only jitter on it that sort of looks like deleted data this person may come to the conclusion that it is an encrypted partition/drive. In this case you may be forced (by a judge or some bad-guys) to reveal the access to that encrypted partition/drive. So instead of giving access to the really high confidential data you only give access to less confidential data. This inspector can't tell for sure if that is truly all information on that disk.

So far to that idea. I however believe, that if you have a 2-level encryption the other party will never believe that you have given out all the keywords for all 2nd level encrypted files. While the idea is good I just think you won't be trusted that you have given all information and this renders it all useless again...

However for me plausible deniability is not that important. Living in Europe in a country that has ratified the European Charter of Human Rights I have basic freedoms granted to me among the right to remain silent without facing any negative consequence (well, this only plays a role in criminal proceedings).

This means a court ordering me to give out the password to activate the encrypted drive has no negative consquences for me. If it does anyway I can appeal to the European Court of Human Right, residing in Strasbourg, and very likely it will consider such an act as breach of the Charter and convict the according state.

While in criminal proceedings it must be proved that you as an individual did commit an wrongful act it is different in civil law proceedings. In some countries you can be held liable for the information that passes through your internet account without you knowing that this happens and without you doing anything. In that case no evidence on your harddisk will be needed (well, if there is evidence found, it's even better...) and hence an encrypted drive will not protect you in this matter.

Due to this I concentrate myself on encryption provided by dm-crypt and LUKS which does not offer such advanced plausible deniability with multi-levels of encrypted data.

* Notice: As I am a graduate law student here in Switzerland I can mostly speak for legal considerations concerning Switzerland. In other countries (in Europe) it may be a bit different but the basic principles and their effects for the guaranteed freedom of people in contracting states remain the same. Also the terms I used very likely aren't the correct legal terms in English however they should be looked at as a mean to get the idea accross of why I think that multi-level encryption has not a big impact here in Europe. The above statements are in no way to be considered as legal practice as each case is different.

**II. Install necessary software**

As stated above, I use Xubuntu Feisty for this. This may also work on older *buntu releases and very likely also other debian-based distributions.

Install the necessary software:
```
sudo aptitude install cryptsetup hashalot
```

**III. Prepare your harddisk**

We are going to add random data to your harddisk. This will make it impossible to guess how much hidden data is actually on it. I'm using for this the *dd-method* and this will take quite a while:
```
sudo dd if=/dev/urandom of=/dev/HARDDISK
```
Replace HARDDISK with your actual one e.g. hda or hdb or sda or sdb or ....

For my 160Gb drive here's the output:
```
hyper@xubi:/dev$ sudo dd if=/dev/urandom of=/dev/hda
dd: writing to `/dev/hda': No space left on device
312581809+0 records in
312581808+0 records out
160041885696 bytes (160 GB) copied, 90679.8 seconds, 1.8 MB/s
```

**IV. Load some kernel modules**

In order to make use of dm-crypt we have to load a few kernel modules.
```
sudo modprobe aes
```
```
sudo modprobe dm-crypt
```
```
sudo modprobe dm_mod
```

If you want them to load at bootup, then you have to edit */etc/modules*
```
sudo nano /etc/modules
```
and you add at the end of the file this:
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
fuse
lp
aes
dm-crypt
dm_mod
```

*fuse* and *lp* were in my file by default. It may be, that yours doesn't have those two in there or additional ones. Just add *aes*, *dm-crypt* and *dm_mod* to this file. Exit nano by pressing *ctrl-x*. You will then be asked if you want to save the modified file. Hit *Enter *twice. Once for saving it and once for setting the name of the file.

**V. Create the crypto partition**

In order to create the crypto partition execute the following command:
```
sudo cryptsetup luksFormat /dev/HARDDISK
```

**VI. Mapping the crypto partition**

Now you have to map the crypto partition:
```
sudo cryptsetup luksOpen /dev/HARDDISK DEVICENAME
```
The partition is now mapped to /dev/mapper/DEVICENAME

**VII. Format the crypto partition**

```
sudo mkfs.ext3 /dev/mapper/DEVICENAME
```

**VIII. Mount the partition**

First create a mounting point:
```
sudo mkdir /media/DEVICENAME
```

Then mount the partition to the mounting point:
```
sudo mount /dev/mapper/HARDDISK /media/DEVICENAME
```

In case you have unmounted the partition for some reason and want to mount it later on again, you don't have to create the filesystem anymore. So just execute *sudo cryptesetup luksOpen /dev/HARDDISK DEVICENAME* and sudo mount */dev/mapper/HARDDISK /media/DEVICENAME*

**IX. Mount at bootup**

In order to mount the partition at bootup you have to edit the */etc/crypttab* and add the following:
```
DEVICENAME	/dev/HARDDISK	none	luks,check=ext2,retry=5
```
And of course you also have to add it to the */etc/fstab* file. Add this there:
```
# CryptoDevices
/dev/mapper/DEVICENAME	/media/HARDDISK	auto	defaults	0	0
```

Upon boot you will be prompted to enter the password you have assigned to this encrypted device. You will be asked max. 5 times if you enter the wrong one* retry=5*. If you fail to provide the correct password the system will boot without mounting that drive. You can however still manually mount it. See above section VIII.

**X. Add/Remove keys**

You can add more keys to an encrypted partition or also remove keys.
To add a key execute:
```
sudo cryptsetup luksAddKey /dev/HARDDISK
```
To remove a key use this:
```
sudo cryptsetup luksDelKey /dev/HARDDISK
```

**XI. Unmount the partition**

With the dmsetup command you can display devicemappings. Is one of the active then anyone can access it, even if it is not mounted. You just need to have to necessary rights. In this state the device is sort of decrypted.
In order to prevent this, you can run the following command to correctly unmount the device:
```
sudo umount /media/DEVICENAME && sudo cryptsetup luksClose HARDDISK
```

I created for this a little shell script which does what I need.
Edit *~/umount.sh *with nano and enter the following code:
```
#!/bin/bash
sudo umount /media/DEVICENAME &amp;&amp; sudo cryptsetup luksClose HARDDISK
```

Then make the file executable:
```
sudo chmod a+x ~/umount.sh
```

Finally create a launcher (start icon...) for it. In Xfce I use this:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=29255&d=1176043306[/IMG]

**XII. Final notes**

Well, now you have your own encrypted partition. You can have a look at the different switches for dm-crypt and luks and maybe use some alternate. I used in this tutorial a complete harddisk as I had problems achieving the setup with just a partition on a harddisk. However I didn't try to hard as I wanted my whole harddisk encrypted.
If you power down the computer or just cut the power off then the harddisk will become unmounted and the mapper will be removed. Enjoy!

---

### Post by honeydew on 2007-05-08
what kernel are you using? I updated from edgy to feisty and I am getting this error...

$ sudo modprobe aes dm-crypt dm_mod
FATAL: Error inserting aes (/lib/modules/2.6.20-15-generic/kernel/crypto/aes.ko): Unknown symbol in module, or unknown parameter (see dmesg)

this is the last line of the dmesg..

[117014.944000] aes: Unknown parameter `dm-crypt'


any ideas? Im thinking it has todo with my kernel version.. 

$ uname -r
2.6.20-15-generic

thanks in advance.. I look forward to getting this working.

---

### Post by hyper_ch on 2007-05-09
My mistake... the three modules have to be loaded seperately

```

sudo modeprobe aes

```


```

sudo modeprobe dm-crypt

```


```

sudo modeprobe dm_mod

```

---

### Post by honeydew on 2007-05-09
w00t! great success \\:D/   I was easily able to change the mount point to my home directory..  so now my laptop has a encrypted home yippie! Im not noticing any effects on my processor..  so far I am quite pleased! =]

thanks! nd be well!

---

### Post by hyper_ch on 2007-05-09
Well, I encountered one problem so far... I didn't create a partition on my harddisk and I was able to luksformat the drive... that worked all fine until I re-setup my computer last weekend... I couldn't access it anymore. It kept telling mit it's not a luks-device...
but then, before I do something like this I always make a backup :) so now I have created a partition to use with it... :)

---

### Post by kuja on 2007-05-16
> **honeydew said:**
> w00t! great success \\:D/   I was easily able to change the mount point to my home directory..  so now my laptop has a encrypted home yippie! Im not noticing any effects on my processor..  so far I am quite pleased! =]

thanks! nd be well!
You will if you do any *Large* file operations. Trust me. I was moving around a few gig the other day and it had one of my cores at about  70% the whole time. Forget what the process was called, but it was something dm-crypt related.

---

### Post by tahnok on 2007-05-17
I can see my encrypted partition fine, but In order for me to write to the disk I need to be root. 
Is there any way that I can either allow myself write privileges or deny non-root users read privileges?

Nice tutorial by the way, it worked great!

---

### Post by hyper_ch on 2007-05-18
Once you have loaded the drive and mounted it at the appropriate place you can just change the ownership of it.

Assuming your username ist TEST and you did mount the drive at /media/dmdrive you open up a terminal and enter this:

```

sudo chown -R TEST.TEST /media/dmdrive

```

This will change the ownership of the directory and all files and subdirectories within it to your user and group (just in case you already have put some stuff as root in there) [-R = recursively].

---

### Post by tahnok on 2007-05-18
Thanks!
Just a note though, I had to add dm-mod, not dm_mod to the modules file.

---

### Post by logical_thought on 2007-06-01
I'm having problems with creation of the encrypted partition. I get these results

```

sudo cryptsetup luksFormat /dev/sda

WARNING!
========
This will overwrite data on /dev/sda irrevocably.

Are you sure? (Type uppercase yes): YES
Enter LUKS passphrase: 
Verify passphrase: 
Unable to make device node for 'temporary-cryptsetup-5894'
Failed to write to key storage.
Command failed.

```

And all following tries get this result:

```

sudo cryptsetup luksFormat /dev/sda

WARNING!
========
This will overwrite data on /dev/sda irrevocably.

Are you sure? (Type uppercase yes): YES
Enter LUKS passphrase: 
Verify passphrase: 
Unable to make device node for 'temporary-cryptsetup-6047'
Failed to write to key storage.
Command failed: device-mapper: remove ioctl failed: Device or resource busy

```

I loaded all the modules, and lsmod confirmed that.

---

### Post by hyper_ch on 2007-06-02
What happens if you partition the drive first and then create an encrypted partition (instead of using hda --> using hda1 (or whatever the partition number is...)

---

### Post by logical_thought on 2007-06-02
Same thing happens.

---

### Post by hyper_ch on 2007-06-03
that is strange :)

---

### Post by traaf on 2007-10-07
i created an encrypted partition using dm-crypt, mounted at boot with a prompt for the passphrase, it's working quite fine

i just have a little problem, with feisty, my hard drives are mounted in random order

my /etc/crypttab :
```
# <target name> <source device>         <key file>      <options>
Stockage        /dev/sdb1       none    checkargs=ext3,tries=5

```

but sometimes, this drive is recognized as sdb, sometimes as sdc ...
so mounting the encrypted volume fails 
is it possible to use uuid or label in /etc/cryptab ?

---

### Post by bodhi.zazen on 2008-05-11
I know this is an "old" how-to, but it comes up on a google search.

In Ubuntu 8.04 (hardy) the name of the kernel module was changed from aes to aes_common :

```
[COLOR=red][B]modprobe aes
WARNING: Error inserting padlock_aes (/lib/modules/2.6.24-16-generic/kernel/drivers/crypto/padlock-aes.ko): No such device[/B][/COLOR]
```Instead, modprobe aes_common:
```
[COLOR=blue]**modprobe aes_generic**[/COLOR]
```

---

### Post by barry99705 on 2008-06-10
I'm getting the command failed thing.  Anybody know how to fix that?  I'm running 8.04 with all the updates installed.

```
barry@Box:~$ sudo cryptsetup luksFormat /dev/sdb1

WARNING!
========
This will overwrite data on /dev/sdb1 irrevocably.

Are you sure? (Type uppercase yes): Yes
Command failed.

```

Same if I try,
```
barry@Box:~$ sudo cryptsetup luksFormat /dev/sdb

WARNING!
========
This will overwrite data on /dev/sdb irrevocably.

Are you sure? (Type uppercase yes): Yes
Command failed.

```

---

### Post by hyper_ch on 2008-06-11
Reading helps:
> 
(Type uppercase yes)


---

### Post by barry99705 on 2008-06-11
> **hyper_ch said:**
> Reading helps:

Son of a ](*,)!!!   Man, that's freaking funny!  I've been beating my head against this for three days.

---

### Post by hyper_ch on 2008-06-11
lol ;)

normally it does not matter you can you type just a "y" and press enter. BUT because it will destroy all information (or sort of destroy everything) they made it a little bit harder ;)

---

### Post by barry99705 on 2008-06-11
> **hyper_ch said:**
> lol ;)

normally it does not matter you can you type just a "y" and press enter. BUT because it will destroy all information (or sort of destroy everything) they made it a little bit harder ;)

Yea, and I was reading it as Yes, and not YES.  Oh well, works now, though I've broken something else installing a theme.  Think I've got it straightened out though.

---

### Post by pnti on 2009-08-15
sudo cryptsetup luksDelKey /dev/HARDDISK key_number

Please update your instruction :-) .

---

### Post by youshoulduseunix on 2010-10-31
If you're using full disk encryption, and you're just trying to change the password of your existing system, you can do the following:

1) download any live Linux CD that has the "cryptsetup" utility available (I used Backtrack 4).

2) boot into the live CD, and open a terminal window

3) run this command to see your LUKS info:  
[INDENT]cryptsetup luksDump /dev/<your LUKS partition>[/INDENT]

4) you should have several available key slots. add your new password to one of them like this:
[INDENT]cryptsetup luksAddKey /dev/<your LUKS partition>[/INDENT]

5) you can run the command from step 3 again to verify. then reboot and verify that your new password works. Your old password should also still work at this point. 

6) to remove the old password, simply repeat steps 1 & 2, and run the following command to delete the old key (be sure to select the old keyslot!):
[INDENT]cryptsetup luksKillSlot /dev/<your LUKS partition>  <slot number>[/INDENT]

repeat step 3 to verify. you should now find that your old key no longer works. That's it!
:guitar:

---

### Post by lisati on 2010-10-31
Thread closed: necromancy & thread originally related to a 3-year-old release of Ubuntu

---

