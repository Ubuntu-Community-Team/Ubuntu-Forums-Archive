---
title: "HOWTO: Full encrypted system: root, home, swap"
date: 2006-01-20
forum: Outdated Tutorials &amp; Tips
---

### Post by heitor_capovilla on 2006-01-20
[FONT=Arial, Helvetica][SIZE=4]**Ubuntu 5.10 (Breezy Badger) with encrypted Root, Home and Swap**[/SIZE][/FONT][I]
by Rudá Moura (ruda.moura@gmail.com)[/I]

This is the way I did to get an Ubuntu 5.10 (Breezy) with full encrypted file system: root (/), home and swap. Since Ubuntu installer does not support yet this option, this process concerns, first, installing Ubuntu on a temporary partition and then, inside that instalation, preparing all the encrypted partitions for the OS. The old root which I used in the beginning is turnt into a swap partition.

This fully encrypted filesystem method employs dm-crypt, linux kernel's devmapper and cryptography. The default algorithm is AES (aes-cbc-plain) with 256bits key. Mark that I am not a *connoceur* on the subject or even a *crypto freak*, I just can say that this worked for me.

[B]
Part 1: Ubuntu installation[/B]

Install Ubuntu with *server profile* with the following initial partitioning scheme:

[FONT=Courier New] /dev/hda1               /boot              100 MB  ext3
/dev/hda2 /                512 MB ext3 [/FONT]
 
Mark that 512 MB is really the shortest size you can set for a server type of installation. A complete Ubuntu installation requires at least 2.4 GB. Make your choice now. In addition, I created two more spaces to hold my future encrypted root and /home partitions, so as the following:

[FONT=Courier New]   /dev/hda3               future /                   10GB
 /dev/hda4 future /home 30GB [/FONT]

Set these partitions in the installer option for filesystem as "do not use the partition". Note that it is not absolutely necessary to have an exclusive /home partition, so this is optional since you can have only one partition for a whole encrypted system. Just ignores the alert about not having a swap partition and keep walking.

[B]
Part 2: Cryptography software installation[/B]

Configures your apt to use all the optional repositories which come with Ubuntu. This is done by modifying /etc/apt/sources.list, uncommenting all the “deb” repositories. Since you are on a terminal with no gedit or something like that, you will need a pure text editor such as Vi. If you know how to use it, don't care for the following explanation for begginers: to edit text files on a terminal using the Vi command, follow this example:
 
[FONT=Courier New] # vi /etc/apt/sources.list[/FONT] 

Press “i” to enter in the INSERT mode, make the alterations, press ESC to enter the COMMAND mode and then press SHIFT+zz (ZZ) to save and quit.

Just install the following additional packages: crypsetup 1.0.1, hashalot 0.3, initrd-tools 1.78 e cramfsprogs 1.1 with the command:

[FONT=Courier New]# apt-get install cryptsetup hashalot initrd-tools cramfsprogs[/FONT]

Important: **initrd-tools must be updated to 1.78 version**, because the original one that comes with Ubuntu has a severe bug which makes it unusable.


**Part 3: Creating the encrypted system**

Now it is time to create the cryptography devices. First, root: choose a trustworthy password, so that you will not end with a weak security implementation. Do not even use your personal login password. Observe that it is hard to change this password later (you would need to re-encrypt the full system again) and this is not explained in this article. The password for /home can be more weak, because it will be stored encrypted inside the file /etc/keys/home (remember that / is being fully encrypted). This is necessary to avoid that /home password would be asked at every boot in order to be mounted.

[FONT=Courier New]   # cryptsetup -y create root /dev/hda3
 # sha256 > /etc/keys/home
 # cryptsetup -d /etc/keys/home create home /dev/hda4 [/FONT]

The password for root will be asked twice, but the one for /home will be asked only one time and it does not provide confirmation! The partitions with support for cryptography will be available at /dev/mapper/. Now create the filesystem. I prefer the XFS filesystem (this is the one for high performance boxes created by Silicom Graphics, with no undelete policies and 64bit technology. Also there are not tools for windows which can be used to mount a xfs system – but who cares since now we are going to be encrypted!) You can use any filesystem supported by Ubuntu and the one everyone use is ext3, but that's a matter of taste.

[FONT=Courier New]   # mkfs -t xfs /dev/mapper/root
 # mkfs -t xfs /dev/mapper/home [/FONT]

Now mount the new partitions to /mnt and copy the old root to the new one at /mnt. This will be a perfect copy, preserving data, symbolic links and everything.

[FONT=Courier New]# mount /dev/mapper/root /mnt
 # mkdir /mnt/home
 # mount /dev/mapper/home /mnt/home
 # cp -axv / /mnt 
[/FONT]
The copy process took two minutes and a half for a server profile and sixteen for a complete installation. Mount /dev inside /mnt/dev to get access to the devices.

[FONT=Courier New]   # mount --bind /dev /mnt/dev  [/FONT]


**Part 4: Adjusts inside chroot**

Enter the encrypted system by using the chroot command and mount /boot, /proc and /sys:

[FONT=Courier New]# chroot /mnt
 # mount /boot
 # mount /proc
 # mount /sys  [/FONT]

This step **must be done **in order to fix a bug in Ubuntu, but do not ask me why..

[FONT=Courier New]# ln -sf /lib/libdevmapper.so.1.01 /lib/libdevmapper.so.1.00  [/FONT]

Edit /etc/crypttab and add the following lines:

[FONT=Courier New]root        /dev/hda3
 home /dev/hda4 /etc/keys/home 
[/FONT]
Edit /etc/fstab in order to change root to the new mounting point at /dev/mapper/root **and add a line for /home**. I did it this way:

[FONT=Courier New]   /dev/mapper/root        /       xfs     defaults           0  1
 /dev/mapper/home /home xfs defaults     0 2 [/FONT]

Edit /etc/kernel-img.conf and add the following line:

[FONT=Courier New]   ramdisk = /usr/sbin/mkinitrd  [/FONT]

Edit /boot/grub/menu.lst, search for kopt and change this line to:

[FONT=Courier New]   # kopt=root=/dev/mapper/root devfs=mount ro  [/FONT]

Note that the initial # should NOT be removed!

Asks it to reconfigure kernel so that it obtains a new file for grub and a new initrd image able to support cryptography.

[FONT=Courier New] # dpkg-reconfigure linux-image-2.6.12-9-386 [/FONT]

This command takes into consideration that the installed kernel is the original one from the installation, but if it is NOT the case, substitute it properly – for example, 686 instead of 386, or any other updated version.

[B]
Part 5: Finishing[/B]

Unmount all chroot file systems, quit chroot and reboot:

[FONT=Courier New]# umount -a
 # exit
 # reboot 
[/FONT]
If everything worked fine, your system will ask for the password in order to mount /root and then the boot process will continue. If you type a wrong password the system will not output any alert and will fail drastically, probably with a Kernel Panic.

[B]
Part 6: Encrypted Swap 

[/B] This process is like the other we done for /home, but the only difference is that the password will be different for every *boot*, since it will be read from /dev/random.
[FONT=Courier New]
 # cryptsetup create swap /dev/hda2 [/FONT]

Type any shit as password, since it will not be used by the user. 

Edit /etc/crypttab and add the line for swap:

[FONT=Courier New]   swap /dev/hda2 /dev/random swap  [/FONT]

Edit /etc/fstab and add the file for swap:

[FONT=Courier New]   /dev/mapper/swap none swap sw 0 0  [/FONT]

To enable swap immediately:

[FONT=Courier New]   # cryptsetup remove swap
 # /etc/init.d/cryptdisks start
 # swapon -a [/FONT]

From this moment your whole filesystem is encrypted. In order to turn your server instalation into a default and complete one, just do it:
[FONT=Courier New]
   # apt-get install ubuntu-desktop  [/FONT]

The following sources were checked for writing this article: crypsetup(8), crypttab(5), [_[COLOR=#000080]http://www.saout.de/tikiwiki/tiki-index.php?page=HOWTO[/COLOR]_]("http://www.saout.de/tikiwiki/tiki-index.php?page=HOWTO")
  [SIZE=2]
Translation from Brazilian Portuguese to English: Heitor Capovilla ([/SIZE][EMAIL="heitorcapovilla@hotmail.com"]_[SIZE=2][COLOR=#000080]heitorcapovilla@hotmail.com[/COLOR][/SIZE]_[/EMAIL][SIZE=2])[/SIZE]

---

### Post by sockrebel on 2006-02-03
this is awesome! thanks!

how would i change this if i only wanted to encrypt home directory (/home/user) and swap, but not root ?

i understand how to do that in theory, but not sure exactly which lines to add, which to change, and which to remove.

tia

---

### Post by i3dmaster on 2006-02-03
Wonderful Howto! Thanks for sharing!

---

### Post by cutOff on 2006-02-03
Woow amazing howto. Good job. 

Thanks a lot.

---

### Post by angrylittleman on 2006-02-04
I have heard that if I do this on my laptop, I will lose my suspend function because the kernel cannot resume from a suspend to disk from an encypted partion.  Can anyone comment?  I would love to have full encrytion on my laptop.  As a second question, how many people are running this setup?

thanks!

---

### Post by docomo on 2006-02-05
Great guide! If anyone is double booting with Windows there is a good program called FreeOTFE that can mount partitions encrypted under Linux:

[http://www.FreeOTFE.org/](http://www.FreeOTFE.org/)

And there is an ext2/3 driver for Windows as well.

angrylittleman: I am running a similar setup on a desktop machine with encrypted root and swap, but I have no separate home partition.

---

### Post by atoponce on 2006-02-05
Excellent how-to!  Added to [doc.gwos.org]("http://doc.gwos.org").  Thanks for sharing!

[http://doc.gwos.org/index.php/EncryptedFilesystem]("http://doc.gwos.org/index.php/EncryptedFilesystem")

---

### Post by docomo on 2006-02-05
Two things to add:

I am using a swedish keyboard and when I get prompted for the password the swedish key layout is not yet active. Instead the layout is the standard english one. This means that not all the keys are where I expect them to be. Anyone know how to fix this?

Also, in case somebody doesn't already get this, you need a *good* password for this to be really secure. This means a long one, say 20 characters, with no real words or names and preferably including numbers, upper-case letters, and other types of characters. 

Of course, that depends on who you are trying to protect yourself against. That is if you are trying to hide your pr0n collection from your mom, this is not a big deal, but if you are a spy or something, it definitely is. In the latter case, you might want to think about using cipher=aes-cbc-essiv:sha256 instead of the defaults although I'm guessing that would mean a slightly increased cpu load.

---

### Post by acid2000 on 2006-02-12
I'm interested in storing the encryption keys on a USB thumb drive. I understand this would be pretty easy for /home and obviously swap but it would require an unencrypted root. 

Is there a way to do it with an encrypted root?

---

### Post by SaLoMoN on 2006-02-13
I have a similar problem like docomo. My German key layout is not loaded when i want to enter my password. In the German keyboard layout Z and Y are exchanged. Is there any possibilty to load a kernek module or something else for german language before asking for the password?

---

### Post by imagine on 2006-02-13
[QUOTE=heitor_capovilla]Since you are on a terminal with no gedit or something like that, you will need a pure text editor such as Vi. If you know how to use it, don't care for the following explanation for begginers: to edit text files on a terminal using the Vi command, follow this example:[/QUOTE]
I think for beginners or people familiar with editors like GEdit, nano is a better choice than vi. At least I managed to use nano without reading any manpages.
Run *nano example.txt*, modify the file as you would in Gedit, and then press Ctrl+X, as explained on the bottom of the screen. If you made any changes, nano will ask you if you want to save the file and where to save it.

Pressing F1 opens the help of nano.

[QUOTE=heitor_capovilla]This process is like the other we done for /home, but the only difference is that the password will be different for every boot, since it will be read from /dev/random.

 # cryptsetup create swap /dev/hda2

Type any shit as password, since it will not be used by the user.[/QUOTE]
You can provide the -d switch to specify a keyfile (/dev/urandom in this case), so you don't have to give a password first just to overwrite it later with a keyfile.
```
# cryptsetup -d /dev/urandom create swap /dev/hda2
```

[QUOTE=heitor_capovilla]# dpkg-reconfigure linux-image-2.6.12-9-386 

This command takes into consideration that the installed kernel is the original one from the installation, but if it is NOT the case, substitute it properly &#8211; for example, 686 instead of 386, or any other updated version.[/QUOTE]
Use *uname* instead:
```
# dpkg-reconfigure linux-image-$(uname -r)
```

This way you don't have to bother about the version of the running kernel. Uname gets it for you.

---

### Post by imagine on 2006-02-13
[QUOTE=sockrebel]how would i change this if i only wanted to encrypt home directory (/home/user) and swap, but not root ?[/QUOTE]
Did you check the link [1] at the bottom of the first posting?

If you don't want to encrypt / then this becomes pretty easy. You can skip 
most of the steps, ie you don't have to create a temporary root first and you don't have to bother about an initial ramdisk.

In my example I assume the partition you want to use for /home is /dev/hdz1.

Just set up your system, backup /home if necessary, apt-get cryptsetup, create your encrypted partition with```
sudo cryptsetup -y create aFancyName /dev/hdz1
``` create a filesystem on it with ```
mkfs -t filesystemYouWantToUse /dev/mapper/aFancyName
``` mount the partition and add it to /etc/fstab and /etc/crypttab, so it's decrypted and mounted at boot. See the first posting for details.


If you have any specific question, feel free to ask.


It's basically the same as heitor_capovilla already posted in his guide, you just should avoid to use a key stored in /etc/keys/home, because /etc isn't encrypted in your example.



[http://www.saout.de/tikiwiki/tiki-index.php?page=HOWTO](http://www.saout.de/tikiwiki/tiki-index.php?page=HOWTO) chapter 3

---

### Post by Glarbl_Blarbl on 2006-02-16
[QUOTE=angrylittleman]I have heard that if I do this on my laptop, I will lose my suspend function because the kernel cannot resume from a suspend to disk from an encypted partion.  Can anyone comment?  I would love to have full encrytion on my laptop.  As a second question, how many people are running this setup?

thanks![/QUOTE]

I tried this out on a Dell Inspiron 5100, and the answer seems to be yes, unfortunately.  I fired it up with no problems (ok, one little typo that was easily fixed and answered the question of what ln -sf libdevmapper ... does)..  Surfed around a little on the web and then had to go to work.

I figured I'd try out hibernate from the gnome logout menu...   Sure enough, /home never mounted again - complaining about a "bad magic number"...  Maybe I was missing something in the how-to, but I was not able to make a new encrypted /home tree without starting from a fresh install...  Next, I guess I'll try the hardware suspend-to-disk  button -  I have my doubts, since none of the other Fn combos have worked so far, and it probably just triggers a windows app anyway.

Oh well, I never could get Gnome and Firefox to remember what web pages I had going anyway.  Might as well just make up a custom .xsession file instead, I seem to recall seeing a how-to for that around here somewheres..  

-
g

---

### Post by lateo on 2006-02-17
thx for this howto :-)

i'm asking myself : aren't there problems to access/decrypt data in case you have to reinstall or want to change your OS? :-k

---

### Post by angrylittleman on 2006-02-18
Glarbl_Blarbl - Bummer.  I have full suspend to disk working on my laptop and I really need that more than I need full encryption (well, I would *like* them both :P ).  thanks for the input, Can anyone else confirm this?

Thanks

---

### Post by josh34 on 2006-02-19
Will a moderator please delete this?

---

### Post by josh34 on 2006-02-19
Will a moderator please delete this?

---

### Post by josh34 on 2006-02-19
When I do this: 
# dpkg-reconfigure linux-image-2.6.12-9-386

I get this:
'root' does not have a valid block device in /etc/crypttab
Failed to create initrd image

What should go in the following colums of /etc/crypttab:
# <target device> <source device> <key file> <options>

Thanks a million,
Josh

P.S. I created all 4 partitions as primary, is that okay?

Update:

I added the following to /etc/crypttab:
root /dev/hda3
home /dev/hda4 /etc/keys/home
(I didn't use the tab key, I merely entered it exactly as shown above.)

After I did that, the kernel reconfigured just fine, so I rebooted.

Now the computer comes up and asks for the passphrase. I enter it and press enter. The "_" continues blinking and the screen doesn't change. Then after 10 or 15 minutes all the text goes away and the screen is blank, but the computer is still on. I let it sit for 30-45 more minutes and it still had a blank screen, so I just turned it off. Any help would be great!

Thanks Again,
Josh

---

### Post by josh34 on 2006-02-20
I don't want to bump this, but I really need help. Please read my last post and try to help if you can.

Thanks,
Josh

---

### Post by PSIman on 2006-02-20
Hi! i did everything like you wrote in this how to, but it doesn't work. 
After rebooting i can enter the passphrase, but i just get this reply: 
> 
[4294729.507000]VFS: Can't find ext3 filesystem on dev dm-0 
[4294729.542000]cramfs: wrong magic 
mount: mont point dev does not exist 
pivot_root: No such file or directory 
/sbin/init:428: cannot open /dev/console : No such file 
[4294729.563000] Kernel panic - not syncing : Attempted to kill init ! 
[4294729.563000] 
 
Has anyone an idea what to do ? I tried the root passphrase with the english and the german layout. Thanks for your attention :) 
Oh, no idea if it is important, but i installed the system from a kubuntu dvd (of course in the server mode, as you wrote).

---

### Post by josh34 on 2006-02-20
At least you get confirmation that you did something wrong. I enter my password and the computer doesn't do anything. I have been asking for help (read my other posts), but no one seems to know what went wrong.

Thanks,
Josh

---

### Post by kubuntu2k6 on 2006-02-24
hello! after upgrading my kernel I now have to type the passphrase twice at boot, maybe overlooked something... :confused: Anyone else experienced this? I don't want to have to type the passphrase more than once. any ideas how to fix this?

---

### Post by Glarbl_Blarbl on 2006-03-02
[QUOTE=kubuntu2k6]hello! after upgrading my kernel I now have to type the passphrase twice at boot, maybe overlooked something... :confused: Anyone else experienced this? I don't want to have to type the passphrase more than once. any ideas how to fix this?[/QUOTE]

I experienced the same problem the first time I followed this howto...  Then after I tried the suspend to disk and subsequently reinstalled it went away.

Not much help, I know.

One other thing: I tried doing an apt-get dist-upgrade to dapper and totally fried my setup...  I probably could have salvaged it with a week or two of research and trial/error, but I can't live without a laptop for that long :/

Why the hell I didn't make a backup first I'll never know..  Oh well, three months of my mailing list account down the tubes..  So my advice to everyone reading this: put down the crack pipe and back up your shit before you go trying to upgrade your encrypted system!

-
g

---

### Post by angrylittleman on 2006-03-02
Glarbl_Blarbl - so suspend to disk did not work for you either?  My system suspends now (unencrypted) but I don't want to reinstall unless I am sure that it will work correctly.

---

### Post by Glarbl_Blarbl on 2006-03-05
[QUOTE=angrylittleman]Glarbl_Blarbl - so suspend to disk did not work for you either?  My system suspends now (unencrypted) but I don't want to reinstall unless I am sure that it will work correctly.[/QUOTE]


AngryLittleMan:
Umm... I was the same one who posted re: suspend to disk before :} ...  Not a separate confirmation, sorry..  

Specifically, what happened after I rebooted from suspend to disk was this:

entered the root passphrase
waited a few seconds and was dropped into the fsck recovery mode... Tried to manually mount the /dev/mapper/home dir and had no joy  (actually tried this a few times to rule out typos).

I tried to simply reformat/encrypt the partition but for some reason it never worked properly until I started from a fresh install, maybe I should have chrooted first?  Obviously a lot of this topic flies straight over my head...  This is the first time I have tried to do any encryption on a system-wide basis.


hth,
g

---

### Post by angrylittleman on 2006-03-05
Glarbl Blarbl- Sorry, I was a little excited about reading asking this question.  My bad on not remembering your previous post. 

ALM

---

### Post by biasquez on 2006-03-11
____ERROR____
[4294729.507000]VFS: Can't find ext3 filesystem on dev dm-0
[4294729.542000]cramfs: wrong magic
mount: mont point dev does not exist
pivot_root: No such file or directory
/sbin/init:428: cannot open /dev/console : No such file
[4294729.563000] Kernel panic - not syncing : Attempted to kill init !
[4294729.563000] 


i have this problem but i don't have an idea about it. i tried to set manual password and to set password into file /etc/keys/root like setting about /home.
PLZ, HELP! tHZ

---

### Post by michwill on 2006-03-12
how exactly do you select "server profile"?

---

### Post by josh34 on 2006-03-12
[QUOTE=michwill]how exactly do you select "server profile"?[/QUOTE]

To select a "server profile" during instalation, boot from the Ubuntu install CD and when the prompt appears, type "server" and then hit enter.

---

### Post by michwill on 2006-03-12
[QUOTE=josh34]To select a "server profile" during instalation, boot from the Ubuntu install CD and when the prompt appears, type "server" and then hit enter.[/QUOTE]


Alright, got it, now I can't get "cryptsetup" to install.  apt-get is telling me that it "couldn't stat source package list" and that cryptsetup has no installation candidate.  Any suggestions?

Thanks for the reply

---

### Post by michwill on 2006-03-12
forgot to 'apt-get update'. . .

---

### Post by kubuntu2k6 on 2006-03-14
anyway, anyone got this working after a dist-upgrade? (dapper) after upgrading kernels etc. how did you do it?

---

### Post by zatarc on 2006-03-14
[QUOTE=kubuntu2k6]anyway, anyone got this working after a dist-upgrade? (dapper) after upgrading kernels etc. how did you do it?[/QUOTE]

I did. Or actually I figured out this wasn't going to work with the Dapper kernel (2.6.15) and used another way. 

_The first problem:_ Kernels >= 2.6.13 no longer use devfs to create the device files in /dev, they use udev. The version of mkinitrd (which creates the initial ramdisk for our cryptoroot-setup) that ships with Dapper relies upon devfs and thus won't work. However, you can use mkinitramfs instead, which seems to be the new standard anyway. I think it comes down to changing a line in [FONT="Times New Roman"]/etc/kernel-img.conf[/FONT]:
[FONT="Times New Roman"]ramdisk = /usr/sbin/mkinitrd[/FONT]
should read
[FONT="Times New Roman"]ramdisk = /usr/sbin/mkinitramfs[/FONT]
No promises though, I actually built my ramdisk with the [FONT="Times New Roman"]update-initramfs -u ALL[/FONT] command. 

_The second problem:_ The version of mkinitramfs that ships with Dapper doesn't have any cryptoroot support built in. Fortunately, someone [wrote a guide]("http://blog.jpoetry.com/2006/02/15/bis-auf-die-wurzeln-verschluesselt/") (in german, I'm afraid) and [some scripts]("http://misc.jpoetry.net/crypto_root/cryptsetup_script.tar.gz") to handle the cryptoroot stuff from within an initramfs. There are a few differences to the HOWTO here, f.i. the author uses aes-cbc-essiv:sha256 as ciphers, LUKS and doesn't bother with chroot, but even without being able to read german you can identify the commands he uses, especially when you compare to the guide in the Ubuntu forums. Still...maybe someone could do a translation? 

Regards

- zatarc

ubuntu user since today. :)

Edit 20060315: 
That german article also discusses keymaps, if I got that right you have to [FONT="Times New Roman"]install-keymap[/FONT] your prefered keymap before building the initramfs. Doesn't seem to have all that much of an effect though, special characters still don't work properly. If you want to use them, I recommend building the initramfs, creating the empty cryptoroot without any filesystem or whatever and then doing a reboot to test if your password works at boottime. You better know your way around grub to boot back into the temporary root if you want to try that one, though. ;-)

---

### Post by kubuntu2k6 on 2006-03-15
thank you very much zatarc for the information... interesting (even though I have a lot to learn about mkinitramfs and the german language) :)

---

### Post by lazy_runner on 2006-03-18
Hello to all!

First this topic sounds very interesting to me. Many thanks for this guide. :) 

Well, I have the following problem with the encryption: How can I make a backup of my encrypted home partition? :confused: 

By default partimage won't work if the partition to save is mounted. But I wasn't able to unmount the home partition. Don't know is that possible at all? :-k 

So I have tried it with partimage from a Knoppix CD, but because of the encryption I got a error message like "The file system of [/dev/hd-- (my home partition) ] is unknown, and is not supported".

There is also a option "-m --allowmnt  Don't fail if the partition is mounted. **Dangerous!**" in man partimage. But I've not tried that option yet because I don't know about what kind of danger it means.

Have someone any experience with the option -m so he can tell about it? I would be pleased about each helpful ideas. ;)

---

### Post by kubuntu2k6 on 2006-03-18
Hi, haven't used partimage with the '-m' option so don't know about that one.

If you add a user that lives outside the /home directory I don't think there should be any problems unmounting it.

If you can't use partimage to make a backup of your encrypted partition, how about 'dd'? For example something like this...

dd if=/dev/hda1 | gzip > my_disk_image.gz

zcat my_disk_image.gz | dd of=/dev/hda1

Well, the 'dd' command also copies empty blocks where partimage will only copy data from the used portions of the partition.

---

### Post by lazy_runner on 2006-03-19
Now I tried the partimage -m option myself, but there was the same failure message like above (file system is unknown ...). So that unfortunately won't work too.

Yes, the dd command also copies all empty blocks. I think because of this there will be a really huge image compared with one made by partimage. Somebody who has a large data partition could get a big space problem with the dd command images.

Nevertheless I will try out the dd command for the moment. It's in any case better then to have no backup of my data at all.

Thank you kubuntu2k6 for your suggestion. ;) 

But what about all the others use encrypted partitions? Doesn't no one of you save his data with a backup at all? I can't believe that. What's in case of any problems with the encryption? You know you will lost all your data of course if you don't have a backup. :cry:

---

### Post by pd77 on 2006-03-20
This HOWTO worked for me. Only thing is I see warnings about "unable to unlink device node" when unmounting the encrypted partitions on shutdown or reboot. Is this something I should worry about or can I ignore this? Anybody else seeing this or knows how to fix it?

-- 
pd

---

### Post by biasquez on 2006-03-21
this guide works. i tried to encrypt root with keyfile into /boot/keys/keyfile but doesn't work. help me!

---

### Post by docomo on 2006-03-24
[QUOTE=pd77]This HOWTO worked for me. Only thing is I see warnings about "unable to unlink device node" when unmounting the encrypted partitions on shutdown or reboot. Is this something I should worry about or can I ignore this? Anybody else seeing this or knows how to fix it?

-- 
pd[/QUOTE]

I see this as well and it hasn't caused any problems.

---

### Post by b0rsten on 2006-03-24
i used the german howto a couple of weeks ago...
it worked fine since the last dist-upgrade (dapper) today...

I'm no longer asked for my passphrase after showing the blue "splashscreen" ...
no errors and no possibility to boot :(

anyone the same problem?

---

### Post by michwill on 2006-03-24
With all the encryption going on, can someone tell me how to still implement my own boot proceedures and items?  For instance, I'd like to be able to make the computer BEEP at, say, specific password prompts.  Any ideas?

---

### Post by kubuntu2k6 on 2006-03-25
could someone make a dapper version of this howto?

---

### Post by SaLoMoN on 2006-03-25
> **zatarc]
_The first problem:_ Kernels >= 2.6.13 no longer use devfs to create the device files in /dev, they use udev. The version of mkinitrd (which creates the initial ramdisk for our cryptoroot-setup) that ships with Dapper relies upon devfs and thus won't work. However, you can use mkinitramfs instead, which seems to be the new standard anyway. I think it comes down to changing a line in [FONT="Times New Roman"]/etc/kernel-img.conf[/FONT]:
[FONT="Times New Roman"]ramdisk = /usr/sbin/mkinitrd[/FONT]
should read
[FONT="Times New Roman"]ramdisk = /usr/sbin/mkinitramfs[/FONT]
No promises though, I actually built my ramdisk with the [FONT="Times New Roman"]update-initramfs -u ALL[/FONT] command. 

_The second problem:_ The version of mkinitramfs that ships with Dapper doesn't have any cryptoroot support built in. Fortunately, someone [wrote a guide]("http://blog.jpoetry.com/2006/02/15/bis-auf-die-wurzeln-verschluesselt/") (in german, I'm afraid) and [some scripts]("http://misc.jpoetry.net/crypto_root/cryptsetup_script.tar.gz") to handle the cryptoroot stuff from within an initramfs. There are a few differences to the HOWTO here, f.i. the author uses aes-cbc-essiv:sha256 as ciphers, LUKS and doesn't bother with chroot, but even without being able to read german you can identify the commands he uses, especially when you compare to the guide in the Ubuntu forums. Still...maybe someone could do a translation? 
[/QUOTE]

I upgraded to Dapper today and did all the steps your described here and anything else what has been described in the german guide (I'm german so i could understand, and you don't miss any information  said:**
> could someone make a dapper version of this howto? 
I would be very happy about that too ... my Ubuntu is not working anymore :(

---

### Post by n_i_c_k on 2006-03-30
[QUOTE=biasquez]____ERROR____
[4294729.507000]VFS: Can't find ext3 filesystem on dev dm-0
[4294729.542000]cramfs: wrong magic
mount: mont point dev does not exist
pivot_root: No such file or directory
/sbin/init:428: cannot open /dev/console : No such file
[4294729.563000] Kernel panic - not syncing : Attempted to kill init !
[4294729.563000] 


i have this problem but i don't have an idea about it. i tried to set manual password and to set password into file /etc/keys/root like setting about /home.
PLZ, HELP! tHZ[/QUOTE]

[QUOTE=PSIman]Hi! i did everything like you wrote in this how to, but it doesn't work. 
After rebooting i can enter the passphrase, but i just get this reply: 
 
Has anyone an idea what to do ? I tried the root passphrase with the english and the german layout. Thanks for your attention :) 
Oh, no idea if it is important, but i installed the system from a kubuntu dvd (of course in the server mode, as you wrote).[/QUOTE]

I think I hit the same error on my first attempt.  Going round again I noticed two things that might have caused it:
1) I had incorrectly edited the kernel opt line in /boot/grub/menu.lst and 
2) I had used "dpkg-reconfigure linux-image-$(uname -r)" which found the 2.6.12-9 kernel but not the -10 that I think got installed during or just after the install (I had apt-get dist-upgrade'ed).

In case it helps.

---

### Post by zatarc on 2006-03-31
[QUOTE=b0rsten]i used the german howto a couple of weeks ago...
it worked fine since the last dist-upgrade (dapper) today...

I'm no longer asked for my passphrase after showing the blue "splashscreen" ...
no errors and no possibility to boot :(

anyone the same problem?[/QUOTE]

I believe that during the dist-upgrade, a new initramfs was created. If you used the german howto, you should have a rescue partition so you can build the initramfs with full crypto support once again. It should also be possible to make the automatically built initramfs crypto-compatible. Are you sure the scripts and stuff are included in the initramfs directories within the cryptoroot so the build from within the cryptoroot will include them? 

Regards

- zatarc

---

### Post by mlbel on 2006-04-08
[QUOTE=b0rsten]i used the german howto a couple of weeks ago...
it worked fine since the last dist-upgrade (dapper) today...

I'm no longer asked for my passphrase after showing the blue "splashscreen" ...
no errors and no possibility to boot :(

anyone the same problem?[/QUOTE]

Yep, I tried various things and in the process accidently messed up everything, including the rescue system :D

BUT, I think its some problem with the CRYPOROOT starting script because I changed it a little (made all 4 important variables to constants) and executed directly and then it works, so what I am thinking now is, that it got some problems with the last if statement... and since it never executes the "cryptsetup luksOpen ..." its in an infinite loop.

Im reinstalling everything right now to check my theorey, will still take a while tho, if anyone can catch the auhor of the script in IRC, ask him please. =)


Edit:
Its some problem with udev not finding the root device... if anyone finds a solution, pls let us know. =)

Edit2:
Ok, I still haven't figured out a solution, but I used the first part of the german HOWTO and encrypted everything except the root partition. Ok, nothing special you might say, but its using LUKS... and my root parition isn't that important anyway.

What I got now is, when the system boots up, it waits for the USB stick which containins the key file... if I insert it, it creates a mount directory and mounts the USB stick in it. When that is done it processes /etc/crypttab and creates the LUKS devices and waits for all of them to appear in /dev/mapper/*. When they are all there the USB stick is unmounted and the directory gets deleted and I can remove the USB stick. (That part is a mod for /etc/init.d/cryptdisks)
Now the /etc/init.d/cryptdisks script can continue as normal and doesn't complain about missing devices anymore.

---

### Post by andrewsawyer on 2006-04-11
Hiya,

I hope someone can help me with this.

I have tried the how-to on my laptop using Dapper Daily (9th April).  I followed step by step, choosing 1Gb as my soon to be swap file, and doing a server style install.

My kernel version is 2.6.15-19-386.  All seemed well, however now when I reboot I get this:

```
Booting 'Ubuntu, kernel 2.6.15-19-386'

root (hd0,0)
Filesystem type is ext2fs, partition type 0x83
kernel /vmlinux-2.6.15-19-386 root=/dev/mapper/root devfs=mount ro quiet splash
[Linux-bzImage, setup=0x1e00, size=0x156859]
initrd /initrd.img-2.6.15-19-386
[Linux-initrd @ 0x1f115000, 0x5bb000 bytes]
savedefault
boot
Uncompressing Linux... Ok, booting the kernel.
Starting Ubuntu...
mount: unknown filesystem type `devfs`
Command failed: Invalid argument
umount: devfs: not mounted
pivot_root: No such file or directory
/sbin/init: 432: cannot open /dev/console: No such file
[4294674.507000] Kernel panic - not syncing: Attempted to kill init!
[4294674.507000]  
```

I was using ext3 for the boot partition as per example, and xfs for the new root/home (again as per example).

I don't get prompted or asked about a password at all during the boot up, and then it just locks after the kernel panic.

Any ideas?

---

### Post by b0rsten on 2006-04-12
[QUOTE=kubuntu2k6]could someone make a dapper version of this howto?[/QUOTE]

the german howto is working fine for dapper (using it for a month or so...)

---

### Post by kubuntu2k6 on 2006-04-12
[QUOTE=b0rsten]the german howto is working fine for dapper (using it for a month or so...)[/QUOTE]

Yea I believe you. I didn't try it because I don't know german, also iirc the howto involved LUKS. Using some script on that page to get crypto support into the initramfs didn't seem to difficult though. But since dapper was about to be released I thought they might fix the crypto til then and didn't bother to mess with it, and instead went on giving dapper a try without the encryption.

---

### Post by docomo on 2006-04-12
I searched around and it looks like some people are aware of the problems with using encrypted root in Dapper:

[https://launchpad.net/distros/ubuntu/+source/cryptsetup/+bug/21878](https://launchpad.net/distros/ubuntu/+source/cryptsetup/+bug/21878)

---

### Post by andrewsawyer on 2006-04-14
I don't speak German :-( so I'm having a bit of trouble with the Dapper encryption following the German how-to.  I really hope that someone might be able to tell me where I am going wrong?  I have (to a point) tried to combine the two threads to get an encrypted system but with no rescue partition.

This is what I have done so far:

```

dev      size      during   after     fs
hda1   100Mb   /boot     /boot (ext2)
hda2   1Gb       /           swap (ext3)
hda3   8Gb       non       /       (ext3)
hda4   rest       non        /home (ext3)

```

installed cryptsetup

```
cryptsetup -c aes-cbc-essiv:sha256 -y -s 256 luksFormat /dev/hda3
cryptsetup -c aes-cbc-essiv:sha256 -y -s 256 luksFormat /dev/hda4

```

```
nano /etc/crypttab
root /dev/hda3 none luks,retry=3,cipher=aes-cbc-essiv:sha256
home /dev/hda4 none luks,retry=3,cipher=aes-cbc-essiv:sha256
swap /dev/hda2 /dev/random swap
```

```
mkfs.ext3 /dev/mapper/root
mkfs.ext3 /dev/mapper/home

then edit fstab and add the following to the bottom:

/dev/mapper/root /mnt/root ext3 defaults 0 2
/dev/mapper/home /mnt/root/home ext3 defaults 0 2
/dev/mapper/swap swap swap sw 0 0
```

```

mkdir /mnt/root
mount -a
mkdir /mnt/root/home
mount -a

/etc/init.d/cryptdisks start
swapon -a
```
Download the script using wget and extract it into the root directory.

```
cp -avx / /mnt/root/
cp -avx /home/* /mnt/root/home/
```

Then open menu.lst in /boot/grub and find the # kopt entry.  Change it to:

```
# kopt=root=/dev/mapper/root cryptivice=/dev/hda3 ro
```

Then run update-grub followed by
```
update-initramfs -u ALL
```
and then update-grub again.  Then use dd to wipe out the home.key file and add it again
```
dd if=/dev/random of=/mnt/root/etc/keys/home.key bs=32 count=1
cryptsetup luksAddKey /dev/hda6 /mnt/root/etc/keys/home.key
```

Then reboot.  I get the prompt as per the image on the blog showing the secure fs bit and asking for my password, however when I write it in it just appears on the screen (not hidden) and hitting enter does nothing.

Obviously I don't yet have a swap file, however I was going to do this afterwards as I was going to use the old / system (hda2), which I can't do before the reboot.

Also, and just out of interest, it would be easy enough to make /boot sit on a usb key for another layer of security yes?  As in the system wouldn't boot without the USB key in.  I guess the downside of this would be that the system would have to be set in the bios to boot off a USB key, so people could use Knoppix or something.  Having said that they wouldn't get much as the hard disk would be encrypted anyway.

Would it be more secure to have the /boot on a USB key, or to have the bios set to only boot off the hard disk?

Anyway, if someone could see where I might have gone wrong then it would be much appreciated, and I'm sure there will be other people around that would like this info too.

Cheers,

Andy

---

### Post by docomo on 2006-04-16
> Would it be more secure to have the /boot on a USB key, or to have the bios set to only boot off the hard disk?

Well if you have the bios set to boot only off the hard disk or only off a USB drive, and you password protect the bios, then you prevent someone from booting from a Knoppix disc on your computer. But if someone has physical access to your machine they could also simply take out your harddrive and put it in another computer and boot, or they could reset the bios. And as you say they can't access your encrypted partition(s) anyway because you have used a good password that can't be brute forced or guessed!

I can speculate that using a USB drive as /boot would prevent the following attack:

Let's say someone breaks in to your house, then mounts your unencrypted /boot partition on your harddrive by either booting from a live cd on your computer, or by taking out the harddrive and putting it in another computer. They could then I guess theoretically modify your /boot to log the password when you type it and store it on the /boot partition. They then leave and leave no traces of themselves, and when you come home you boot your system as usual, the password gets stored on /boot, but everything looks normal so you don't suspect anything.

Sometime later they come back, access your /boot again, and find the stored password. They then steal your computer or just your harddrive as they are now able to decrypt everything using the password.

By using a USB drive that you carry around all the time, they will not be able to modify /boot that easily.

Another way would be to have a script on the encrypted partition that examines /boot and warns about any modifications and restores it to the original state.

Then again an attacker could achieve the same thing by installing a hardware keylogger in your computer.

---

### Post by andrewsawyer on 2006-04-16
Thanks Docomo,

I guess the only way to ensure that someone can't boot into Gnoppix or load up with any live-usb for that matter would be to have the bios set to boot from the HD only.  Once I have set the bios to boot from the USB stick it pretty much opens it up to that kind of attack - although the drive would be fully encrypted anyway.

It would like you say solve any problem with people messing with the /boot, and also unless someone knew that I was using an encrypted system with a removble /boot just turning the system on would result in an error as there would be no filesystem visable at all (if they didn't have the USB key).  Also with it being a laptop it would be pretty hard to put a hardware keylogger on/in without it being noticed.

Now if someone could give me a hand to see where I went wrong with the 'translation' of the German how-to I will be able to get it all up and running - and yes, I've already tried Babel-fish.

If anyone is interested on 'my master plan' it is this:

1 laptop with encrypted root, home and swap.  1 Lacie Carte Orange (8Gb USB disk the size of a credit card) containing the /boot section.  This is where (for me anyway) it gets interesting:

I want the USB disk to also be an Ubuntu Live-USB running Dapper.  I'm working on this at the mo.  It will also have a partition called casper-rw which will be encrypted and act as a persistent home for the Live-USB while also syncing with a number of diretories out of my laptop home when the laptop is booted.  The /boot section on the USB stick will have two options - boot the LiveUSB or boot the Laptop.

This way I get the security of my laptop being secure with a removable boot, and when I don't have access to my laptop, I will still have everything (email etc) available to me on my bootable LiveUSB version of Ubuntu.

Shouldn't be to hard to do assuming that I can get a Live USB booted off grub rather than syslinux or whatever.  I can just have two options in the boot menu - one for the LiveUSB and one for the Laptop.

Anyway, must go!  If someone could let me know about the German translation it would be much appreciated.

Andy

---

### Post by Glarbl_Blarbl on 2006-04-18
[QUOTE=kubuntu2k6]hello! after upgrading my kernel I now have to type the passphrase twice at boot... Anyone else experienced this? I don't want to have to type the passphrase more than once.[/QUOTE]

I guess since Kubuntu2k6 gave up on the encrypted root this won't help him - but maybe somebody else will be interested to know that only the second passphrase counts.  That is, you can just hit enter for the first occurrance and type your passphrase in as normal on the second.

I have no idea what caused it, but you could think of it as an extra security measure: just type some extra gibberish in for the first passphrase if somebody is looking at your fingers!

--
On a completely different note, has anyone else tried to run any graphics-intensive games on their encrypted systems?  I was able to get UT2004 to run acceptably for 10-15 minute stretches before it got totally bogged down..  Am I just silly for trying?

---

### Post by Glarbl_Blarbl on 2006-04-21
I think I know what the problem is..  For some reason the swap partition is not being mounted at boot time.  The only way I can get it to mount is the "enable swap immediately" part of step 6.  

I haven't tinkered much with boot scripts, so I really don't know what to search for to fix this issue.  Also, can anybody tell me an easier way than running top to check whether the swap mounted properly?

EDIT:  cat /proc/meminfo  ... duh!

---

### Post by cosmoshell on 2006-04-24
hey how can I encrypt my all my linux partions including swap without reinstalling ubuntu.?

---

### Post by dguido on 2006-04-27
Can someone please update the doc.gwos.org entry for this HOWTO for Dapper?

It is located here: [http://doc.gwos.org/index.php/Encrypted_Filesystem](http://doc.gwos.org/index.php/Encrypted_Filesystem)

---

### Post by andrewsawyer on 2006-04-28
[QUOTE=dguido]Can someone please update the doc.gwos.org entry for this HOWTO for Dapper?

It is located here: [http://doc.gwos.org/index.php/Encrypted_Filesystem](http://doc.gwos.org/index.php/Encrypted_Filesystem)[/QUOTE]

Please yes.  I posted earlier in this thread as I haven't been able to translate the German how-to and get encryption working on my laptop in Dapper.  If someone could update the current or even just do a direct translation from the German howto posted in this thread, it would be much appreciated.

---

### Post by Glarbl_Blarbl on 2006-04-29
Has anyone else had your swap partition fail to mount at boot time while running the encrypted setup?   Is this something that is likely to continue to be an issue in the Dapper version?  The confusing thing is that the boot output claims to mount the swap properly, I only noticed it after running top...  When I grepped swap through my logs it showed that swap hadn't been properly mounted for months.   I have no clue as to what I did to cause this..

Anyway, I wrote a small script today to check if the swap partition is mounted and if not it runs the three commands from the howto.

Here it is in case anybody else wants to use it.  You'll need to sudo to run it.

```
 
#!/bin/bash
# quickly setup and mount the swap partition, since it doesn't seem to happen at boot time.
# Written by J. Grant Boling

# check to see if swap is already running:

swapStat=`grep SwapTotal /proc/meminfo | gawk '{ print $2 }'`

if
    [ "$swapStat" != "0" ]; then
        echo "Swap is already mounted!  Exiting..."
        exit 1

    else

# if not already mounted, clear crypsetup's swap and mount swap.

        /sbin/cryptsetup remove swap
        /etc/init.d/cryptdisks start
        swapon -av

fi


swapStatNew=`grep SwapTotal /proc/meminfo | gawk '{ print $2 }'`
echo "Total Swap Memory: $swapStatNew kB"

exit 0

``` 
I looked around at the Debian reference site, and I'm pretty lost as to where I would paste this script in order to make sure that my swap comes up at boot.  I know that it would go in one of the rcS.* directories but I don't want to destroy my setup on accident.    Also, I'd probably need to make the script output fit in visually with the rest of the boot output.  In case it isn't obvious, I'm a total coding noob (though I have been using various flavors of Linux since Redhat 5.2 was new).

Should I just run my script on every boot until I upgrade to Dapper and just cross my fingers that this weirdness is fixed?  Also, is the "grep swaptotal" thing a big waste of time - that is, is there an environment variable which stores the size of the swap partition?

Thanks,
Grant

EDIT: Fixed another typo in the script.
EDIT2: Replaced the sed command with a more elegant gawk.  I'm learning more about scripting all the time!
UPDATE:  I decided to take this script and put it in root's .bash_profile , along with a function to ask whether I want to enable my ethernet connection and a third to display the free space on my disks.

---

### Post by Nuld on 2006-04-30
Can anyone tell me where the hibernate image is stored? If it is stored into the swap space, can I change this so that it is stored in an image file instead? I have read something about this some time ago, but I neither remember where nor if it applies to Ubuntu, too.

I'd like to store the image on an encrypted partition. Therefore, I need to know at which point during the system startup the hibernate image is being restored?

Thanks.

---

### Post by yusufm on 2006-05-18
If I only encrypt my home dir, and there are 5 users using the home dir, would each one have to use a common password to mount the home dir, or will their homedir be mounted automatically when they log in? also, i wanted to know if the password used to mount the encrypted homedir can be connected to thier normal password, so that when they change thier user password, they use the same value to mount the homedir.

Thanks.


[QUOTE=heitor_capovilla][FONT=Arial, Helvetica][SIZE=4]**Ubuntu 5.10 (Breezy Badger) with encrypted Root, Home and Swap**[/SIZE][/FONT][I]
by Rudá Moura (ruda.moura@gmail.com)[/I]

This is the way I did to get an Ubuntu 5.10 (Breezy) with full encrypted file system: root (/), home and swap. Since Ubuntu installer does not support yet this option, this process concerns, first, installing Ubuntu on a temporary partition and then, inside that instalation, preparing all the encrypted partitions for the OS. The old root which I used in the beginning is turnt into a swap partition.

This fully encrypted filesystem method employs dm-crypt, linux kernel's devmapper and cryptography. The default algorithm is AES (aes-cbc-plain) with 256bits key. Mark that I am not a *connoceur* on the subject or even a *crypto freak*, I just can say that this worked for me.

[B]
Part 1: Ubuntu installation[/B]

Install Ubuntu with *server profile* with the following initial partitioning scheme:

[FONT=Courier New] /dev/hda1               /boot              100 MB  ext3
/dev/hda2 /                512 MB ext3 [/FONT]
 
Mark that 512 MB is really the shortest size you can set for a server type of installation. A complete Ubuntu installation requires at least 2.4 GB. Make your choice now. In addition, I created two more spaces to hold my future encrypted root and /home partitions, so as the following:

[FONT=Courier New]   /dev/hda3               future /                   10GB
 /dev/hda4 future /home 30GB [/FONT]

Set these partitions in the installer option for filesystem as "do not use the partition". Note that it is not absolutely necessary to have an exclusive /home partition, so this is optional since you can have only one partition for a whole encrypted system. Just ignores the alert about not having a swap partition and keep walking.

[B]
Part 2: Cryptography software installation[/B]

Configures your apt to use all the optional repositories which come with Ubuntu. This is done by modifying /etc/apt/sources.list, uncommenting all the “deb” repositories. Since you are on a terminal with no gedit or something like that, you will need a pure text editor such as Vi. If you know how to use it, don't care for the following explanation for begginers: to edit text files on a terminal using the Vi command, follow this example:
 
[FONT=Courier New] # vi /etc/apt/sources.list[/FONT] 

Press “i” to enter in the INSERT mode, make the alterations, press ESC to enter the COMMAND mode and then press SHIFT+zz (ZZ) to save and quit.

Just install the following additional packages: crypsetup 1.0.1, hashalot 0.3, initrd-tools 1.78 e cramfsprogs 1.1 with the command:

[FONT=Courier New]# apt-get install cryptsetup hashalot initrd-tools cramfsprogs[/FONT]

Important: **initrd-tools must be updated to 1.78 version**, because the original one that comes with Ubuntu has a severe bug which makes it unusable.


**Part 3: Creating the encrypted system**

Now it is time to create the cryptography devices. First, root: choose a trustworthy password, so that you will not end with a weak security implementation. Do not even use your personal login password. Observe that it is hard to change this password later (you would need to re-encrypt the full system again) and this is not explained in this article. The password for /home can be more weak, because it will be stored encrypted inside the file /etc/keys/home (remember that / is being fully encrypted). This is necessary to avoid that /home password would be asked at every boot in order to be mounted.

[FONT=Courier New]   # cryptsetup -y create root /dev/hda3
 # sha256 > /etc/keys/home
 # cryptsetup -d /etc/keys/home create home /dev/hda4 [/FONT]

The password for root will be asked twice, but the one for /home will be asked only one time and it does not provide confirmation! The partitions with support for cryptography will be available at /dev/mapper/. Now create the filesystem. I prefer the XFS filesystem (this is the one for high performance boxes created by Silicom Graphics, with no undelete policies and 64bit technology. Also there are not tools for windows which can be used to mount a xfs system – but who cares since now we are going to be encrypted!) You can use any filesystem supported by Ubuntu and the one everyone use is ext3, but that's a matter of taste.

[FONT=Courier New]   # mkfs -t xfs /dev/mapper/root
 # mkfs -t xfs /dev/mapper/home [/FONT]

Now mount the new partitions to /mnt and copy the old root to the new one at /mnt. This will be a perfect copy, preserving data, symbolic links and everything.

[FONT=Courier New]# mount /dev/mapper/root /mnt
 # mkdir /mnt/home
 # mount /dev/mapper/home /mnt/home
 # cp -axv / /mnt 
[/FONT]
The copy process took two minutes and a half for a server profile and sixteen for a complete installation. Mount /dev inside /mnt/dev to get access to the devices.

[FONT=Courier New]   # mount --bind /dev /mnt/dev  [/FONT]


**Part 4: Adjusts inside chroot**

Enter the encrypted system by using the chroot command and mount /boot, /proc and /sys:

[FONT=Courier New]# chroot /mnt
 # mount /boot
 # mount /proc
 # mount /sys  [/FONT]

This step **must be done **in order to fix a bug in Ubuntu, but do not ask me why..

[FONT=Courier New]# ln -sf /lib/libdevmapper.so.1.01 /lib/libdevmapper.so.1.00  [/FONT]

Edit /etc/crypttab and add the following lines:

[FONT=Courier New]root        /dev/hda3
 home /dev/hda4 /etc/keys/home 
[/FONT]
Edit /etc/fstab in order to change root to the new mounting point at /dev/mapper/root **and add a line for /home**. I did it this way:

[FONT=Courier New]   /dev/mapper/root        /       xfs     defaults           0  1
 /dev/mapper/home /home xfs defaults     0 2 [/FONT]

Edit /etc/kernel-img.conf and add the following line:

[FONT=Courier New]   ramdisk = /usr/sbin/mkinitrd  [/FONT]

Edit /boot/grub/menu.lst, search for kopt and change this line to:

[FONT=Courier New]   # kopt=root=/dev/mapper/root devfs=mount ro  [/FONT]

Note that the initial # should NOT be removed!

Asks it to reconfigure kernel so that it obtains a new file for grub and a new initrd image able to support cryptography.

[FONT=Courier New] # dpkg-reconfigure linux-image-2.6.12-9-386 [/FONT]

This command takes into consideration that the installed kernel is the original one from the installation, but if it is NOT the case, substitute it properly – for example, 686 instead of 386, or any other updated version.

[B]
Part 5: Finishing[/B]

Unmount all chroot file systems, quit chroot and reboot:

[FONT=Courier New]# umount -a
 # exit
 # reboot 
[/FONT]
If everything worked fine, your system will ask for the password in order to mount /root and then the boot process will continue. If you type a wrong password the system will not output any alert and will fail drastically, probably with a Kernel Panic.

[B]
Part 6: Encrypted Swap 

[/B] This process is like the other we done for /home, but the only difference is that the password will be different for every *boot*, since it will be read from /dev/random.
[FONT=Courier New]
 # cryptsetup create swap /dev/hda2 [/FONT]

Type any shit as password, since it will not be used by the user. 

Edit /etc/crypttab and add the line for swap:

[FONT=Courier New]   swap /dev/hda2 /dev/random swap  [/FONT]

Edit /etc/fstab and add the file for swap:

[FONT=Courier New]   /dev/mapper/swap none swap sw 0 0  [/FONT]

To enable swap immediately:

[FONT=Courier New]   # cryptsetup remove swap
 # /etc/init.d/cryptdisks start
 # swapon -a [/FONT]

From this moment your whole filesystem is encrypted. In order to turn your server instalation into a default and complete one, just do it:
[FONT=Courier New]
   # apt-get install ubuntu-desktop  [/FONT]

The following sources were checked for writing this article: crypsetup(8), crypttab(5), [_[COLOR=#000080]http://www.saout.de/tikiwiki/tiki-index.php?page=HOWTO[/COLOR]_]("http://www.saout.de/tikiwiki/tiki-index.php?page=HOWTO")
  [SIZE=2]
Translation from Brazilian Portuguese to English: Heitor Capovilla ([/SIZE][EMAIL="heitorcapovilla@hotmail.com"]_[SIZE=2][COLOR=#000080]heitorcapovilla@hotmail.com[/COLOR][/SIZE]_[/EMAIL][SIZE=2])[/SIZE][/QUOTE]

---

### Post by MilkBoy on 2006-05-21
**_Disclaimer: I'm writing this out of memory, so it might not be completely correct, and you will need to improvise a little._**

**[SIZE="3"]Adapting the howto to Dapper Drake for encrypted root fs[/SIZE]**

The Breezy howto almost works on Dapper, but a few things need to be changed.

**Part 2:**
```
# apt-get install cryptsetup hashalot initramfs-tools
```

**Part 4:**
The libdevmapper version has been updated, so you need something like ```
ln -sf /lib/libdevmapper.so.1.02 /lib/libdevmapper.so.1.01
``` instead. If you get it wrong, mkinitramfs will tell you later on.

The */etc/kernel-img.conf* should have the line changed to ```
ramdisk = /usr/sbin/mkinitramfs
```

*/boot/grub/menu.lst* should not have the devfs-stuff added to the *kopt* line, but the root should be changed.

Before you build the new ramdisk, a few files needs to be created so that your system at least has a tiny chance to boot up. You can use the ones here as mentioned earlier in the thread [[http://misc.jpoetry.net/crypto_root/cryptsetup_script.tar.gz]](http://misc.jpoetry.net/crypto_root/cryptsetup_script.tar.gz]), or roll your own. One script is needed to make sure all important files are copied to the ramdisk, and another to create the encrypted volume before init tries to mount it.

Now you can issue the command to rebuild the ramdisk:```
# dpkg-reconfigure linux-image-`uname -r`
```

**In case of problems** (like there would be any ;))
mkinitramfs will by default include busybox, which means that if the kernel doesn't find the root fs, or something equally bad happends, it will drop to a shell. This is very handy for debugging if something goes wrong. You might want to
[LIST]
[*]check for missing modules to start with (I know I had to, but that might be because I did something wrong while playing with settings)
[*]make sure the cryptsetup program is executable
[*]test if you can create the encrypted volume by executing the cryptsetup program
[*]
[/LIST]

This is roughly what I did to get my oldish laptop to use an encrypted root filesystem. It might or might not work for other people, since I probably forgot to mention something cruicial.

EDIT: added link to mkinitramfs scripts and hooks

---

### Post by DROP on 2006-05-22
Is there any significant performance hit in using this?

---

### Post by MilkBoy on 2006-05-22
[QUOTE=DROP]Is there any significant performance hit in using this?[/QUOTE]
Depends on what you mean by significant. On my 800MHz PIII, booting and starting applications takes ~60% longer, but once it's up and running, there is only barely noticeable slowdowns. Ofc, applications that do lots of disk I/O would suffer much more than applications using only RAM.

---

### Post by s3ppel on 2006-05-22
Is the performance hit caused primarily by the processor, having to de/encrypt the disk I/O? In this case the upcoming dual core CPUs should be a lot faster...

---

### Post by jbtechie on 2006-05-25
Hello,

I'm trying to create a simple encrypted file system on my 256MB USB thumbdrive.  The thumbdrive is mounted at '/media/PUBLIC'.  I've tried three different ways with three different errors.  I have a feeling I'm missing something obvious.  I'm using Dapper with all updates and kernel: 2.6.15-23-386.  The following three code quotations are my three attempts.

```

# cryptsetup create backups /media/PUBLIC
Command failed: Incompatible libdevmapper 1.02.05 (2006-04-19)(compat) and kernel driver

```

```

# cryptsetup -c aes-cbc-essiv:sha256 -y -s 256 luksFormat /media/PUBLIC

WARNING!
========
This will overwrite data on /media/PUBLIC irrevocably.

Are you sure? (Type uppercase yes): YES
Enter LUKS passphrase:
Verify passphrase:
Failed to setup dm-crypt key mapping.
Check kernel for support for the aes-cbc-essiv:sha256 cipher spec and verify that /media/PUBLIC contains at least 258 sectors.
Failed to write to key storage.
Command failed.

```

```

# sha256 > /etc/keys/home
Enter passphrase:
# cryptsetup -d /etc/keys/home create home /media/PUBLIC
Command failed: BLKROGET failed on device: Inappropriate ioctl for device

```

---

### Post by jbtechie on 2006-05-26
It was something simple.  I was trying to make the encrypted filesystem on a mount instead of a drive or partition.  Now I can run
```

# cryptsetup -d /etc/keys/backup create backup /dev/sdd
# mount /dev/mapper/backup mnt/usb

```
successfully.  The incompatible libdevmapper was because I was forgetting to use 'sudo'.](*,) 

Also, the following works correctly now.
```

# cryptsetup -c aes-cbc-essiv:sha256 -y -s 256 luksFormat /dev/sdd

```

---

### Post by dgh on 2006-06-01
Could someone update this to completely work with Dapper 6.06?

---

### Post by BA53 on 2006-06-01
First thank you for your engagement, but I can't get the encryption working on Dapper Drake (worked before on Breezy).

I followed the additional steps (postet by MilkBoy), but during start up, he can't find the root device and drops me to a console after a while.

I would be really grateful, if anyone could try to complete the HowTo.

Thanks in advance!

---

### Post by dnovotny on 2006-06-02
[QUOTE=BA53]First thank you for your engagement, but I can't get the encryption working on Dapper Drake (worked before on Breezy).

I followed the additional steps (postet by MilkBoy), but during start up, he can't find the root device and drops me to a console after a while.

I would be really grateful, if anyone could try to complete the HowTo.

Thanks in advance![/QUOTE]

I am having this same issue, I used the command 
```
cryptsetup -c aes-cbc-essiv:sha256 -y -s 256 luksFormat /dev/hda3
```
to setup my encryption, and now when I start to boot, I get the problem where it can't find the root device.  Once it drops into the console, I can execute 
```
# cryptsetup luksOpen /dev/hda3 root
# exit

```
and it will resume booting just fine, and bring me up to my login prompt. (I haven't installed the ubuntu-desktop packages yet, wanna make sure I have all of this working right first.  

If anyone can help me to figure out how to make the system automatically issue the luksOpen command I would appreciate it.

---

### Post by dgh on 2006-06-02
Please, someone? This is the only thing that keeps me from installing Dapper :(.

I am sure that someone on this forum is capable to update this howto for Dapper.

---

### Post by paca on 2006-06-02
with the update of the howto i was able to boot the encrypted filesystem with an old kernel from breezy, seems that the ramdrive doesnt have everything in the 6.06... and the script to make the ramdrive include everythhing that is needed doesnt work either...

/P

---

### Post by lex1 on 2006-06-02
which kernel please not much hope with 6.06 thats not good news I was evenhoping for loop-aes. i still say that ubuntu is not as rock solid as sarge

---

### Post by josh34 on 2006-06-09
I don't mean to be a bother, but many of us need step by step instructions for 6.06, the instructions for 5.10 were great and another set like them would be awesome.

Thanks,
Josh

---

### Post by BA53 on 2006-06-09
I would also really appreciate that, because I still can't get it to work.

---

### Post by dgh on 2006-06-09
Please. Someone :-s

---

### Post by josh34 on 2006-06-15
Someone? Anyone?? Please...

We NEED a 6.06 version of this HOWTO.

Thanks,
Josh

---

### Post by dgh on 2006-06-16
I can't believe that there is not a single person in here who is capable to update this howto. Is Ubuntu community really this pathetic?

---

### Post by curuxz on 2006-06-17
[QUOTE=dgh]I can't believe that there is not a single person in here who is capable to update this howto. Is Ubuntu community really this pathetic?[/QUOTE]

we all want an update but chill out, also remember this is NOT the place to ask for howto's

---

### Post by xpmaniac4ever on 2006-06-17
I need this too. I would do the howto myself if I had the knowledge necessary. But don`t have it. :)

---

### Post by dgh on 2006-06-17
[QUOTE=curuxz]we all want an update but chill out, also remember this is NOT the place to ask for howto's[/QUOTE]

Well, maybe I overreacted a bit. Sorry about that. But can you believe how frustrating it is to keep using Windows only for this :D. I think there should be a more user friendly full disk encryption solution for Linux. In Windows you can just click "encrypt" and that's it :sad:. If you could choose to encrypt all disks when installing Ubuntu it would be perfect!

---

### Post by curuxz on 2006-06-18
yea but when you do that in windows its almost pointless since it can be hacked really simply.

---

### Post by dgh on 2006-06-18
[QUOTE=curuxz]yea but when you do that in windows its almost pointless since it can be hacked really simply.[/QUOTE]

I meant with third party application (DCPP for example). But you never know when dealing with closed source applications...

---

### Post by xoros on 2006-06-18
I assume you all have read this?

> A very good compromise is to encrypt all the folders that are likely to contain data as opposed to system files. These include /tmp, /home, /var, /temp (some systems have both) and the often overlooked /swap partition. On many systems this will also include /root, since that is the root user's desktop and is not stored in /home. Problem is if we lock this away and need to reboot the system without mounting the encrypted volume, we may find a system that doesn't work at all. Fortunately there are ways to overcome this, which we will (again) cover later.

So, how to encrypt all this stuff without having to enter five passphrases every time we restart? Some howtos suggest using one "master" partition (usually /home) that contains "key files" which are used to successively unlock the other partitions. There are a couple of problems with this method: first, if one of those files (usually filled with random gibberish so as to make them "unguessable") is damaged it can render the whole system useless until a restore operation is performed (and how often do YOU backup your system?) The other problem is it isn't really "secure" at all since any time your /home partition is mounted the "keys" to all those other partitions are available to anyone who can get access to your computer (even remotely). This is really only slightly different than using those post-its we mentioned earlier. 

Do any of these methods work on this page?
[https://wiki.ubuntu.com/EncryptedFilesystemHowto](https://wiki.ubuntu.com/EncryptedFilesystemHowto)

---

### Post by uptimebox on 2006-06-19
[https://wiki.ubuntu.com/EncryptedFilesystemHowto4](https://wiki.ubuntu.com/EncryptedFilesystemHowto4)

Encrypted root for Ubuntu 6.06 (Dapper Drake)

---

### Post by uptimebox on 2006-06-19
Since this howto related to Dapper, I have posted it in separate thread. I suppose it will show up after moderatorial approvement.

---

### Post by uptimebox on 2006-06-19
[http://ubuntuforums.org/showthread.php?t=199824](http://ubuntuforums.org/showthread.php?t=199824)

---

