---
title: "[HOWTO] Encrypt whole Feisty installation without reinstalling"
date: 2007-04-23
forum: Outdated Tutorials &amp; Tips
---

### Post by Kopfgeldjaeger on 2007-04-23
This describes how to encrypt a Ubuntu 7.04 (Feisty Fawn) installation. Because we work with a live cd, you can install Feisty and reboot (to test if it works, maybe more than one time [I got some strange error the first/second boot]). 

I recommend to "shred" your harddisk before that... You can do this with
```
sudo dd if=/dev/zero of=/dev/sda
```
This may took some hours. On a 300 GB drive, 4 or 5 hours (for me).

Most of this tutorial is from [this]("http://forum.ubuntuusers.de/topic/86498/") German thread.

The partitions (if it's not like that, you have to rethink a bit, but it is not difficult):

1.)
```

/dev/sda1: /boot: 100 to x MB. Filesystem does not really matter (I used ext3) 
/dev/sda2: swap, mine is 1GB
/dev/sda3: /, should be >=3GB, mine is 50GB :)
/dev/sda4: /home, size doesn't matter, but it should be enough.. Some GB are already enough, mine is 100GB
```
If you have /boot on your / partition, we can just copy the filez later
2.) Software/modules

Become root with
```
sudo su
```
Install software and load modules (you need "universe"-repository:
```

modprobe aes
modprobe dm-crypt
modprobe dm-mod
apt-get update
apt-get install cryptsetup
```

3.)
We work in /media and need three folders:
```

cd /media
mkdir boot root home
```

Now mount the partitions.
```
mount /dev/sda1 boot
mount /dev/sda3 root
mount /dev/sda4 home
```


If /boot is on your root partition:
```

cp -ax root/boot/* boot/*
umount boot
rm -rf boot root/boot
```

Now we save the data on / temporary to /home (this partition should be big enough, of course you can use another partition if you want)

```
mkdir home/root
cp -ax root/* home/root
umount root
```

4.) The first partition (= /) is being encrypted now!

```
cryptsetup -c aes-cbc-essiv:sha256 -y -s 256 luksFormat /dev/sda3
```
Type uppercase "YES" and choose a good password. Maybe the password will be the greatest weakness later...
If you get an error, modprobe the modules above or unmount sda3.
We open the partition, format it (NOT your old root partition!) with ext3 (what takes some time) and mount it:

```
cryptsetup luksOpen /dev/sda3 root
mkfs.ext3 /dev/mapper/root
mount /dev/mapper/root root
```

Now we copy the /-data on the home partition back and delete the root-files on the home partition

```
cp -ax home/root/* root
rm -rf home/root
```

The same with the home partition:

```
mkdir root/backup
cp -ax home/* root/backup
umount home
cryptsetup -c aes-cbc-essiv:sha256 -y -s 256 luksFormat /dev/sda4
cryptsetup luksOpen /dev/sda4 home
mkfs.ext3 /dev/mapper/home
mount /dev/mapper/home home
cp -ax root/backup/* home
rm -rf root/backup
umount home
```

Now / and /home are encrypted but would not really boot...

5.) Prepare the system for booting

We mount the root partition into the root partition...
```

mkdir root/boot
mount /dev/sda1 root/boot
```

...and chroot into the system.

```
chroot root
```

If cryptsetup is not already installed, you should install it now (universe is needed again, as editor you can use vim)
```

apt-get update
apt-get install cryptsetup
```

Now edit /etc/initramfs-tools/modules with your fav. editor and delete the lines in it (should be only some comments...)
Now paste the following into it:
```
aes
dm-crypt
dm-mod
sha256
```

Now edit the /etc/fstab (UUIDs are only examples)

```

UUID=7153f497-1b66-476d-bb3b-85e3fe18b402 /               ext3    defaults,errors=remount-ro 0       1
UUID=ab5f1dca-45c1-4c66-8cfb-e6ca84ec6650 /home           ext3    defaults        0       2
```

to 

```

/dev/mapper/root /               ext3    defaults,errors=remount-ro 0       1
/dev/mapper/home /home           ext3    defaults                       0       0
```

and save it. Edit /etc/crypttab and paste
```
root /dev/sda3 none luks,retry=1,cipher=aes-cbc-essiv:sha256
home /dev/sda4 none luks,retry=1,cipher=aes-cbc-essiv:sha256
```

Edit /boot/grub/menu.lst and change
```

# kopt=root=/dev/sda3 ro quiet splash
```
to
```

# kopt=root=/dev/mapper/root ro
```
And make a
```
update-grub
```.
To be sure, look if your Ubuntu entries look like this:
```
title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,0)
kernel          /vmlinuz-2.6.20-15-generic root=/dev/mapper/root ro quiet
initrd          /initrd.img-2.6.20-15-generic
savedefault
```
There may be some locale/vga=x entries or so... That is absolutely OK

Update initramfs:
```
update-initramfs -u All
```

You see some error msgs because "libdevmapper" or so, that doesn't matter now.

Now you can reboot. You should see
Enter LUKS passphrase: 
Type in your root-partition password. After some seconds, enter your home-partition password (you will be asked again). If it does not work, boot with the live cd, mount the partitions, chroot into the fs and check which file is wrong.

So, that should be everything.. but

If you want to encrypt your swap partition, too, do the following while you booted into your encrypted system:

In /etc/crypttab, add the line
```
swap /dev/hda2 /dev/random swap,check=/bin/true
```

and in /etc/fstab, change the swap line to
```

/dev/mapper/swap  none            swap    sw              0       0
```

Don't reboot now.

Do the following:
```
sudo su
swapoff
dd if=/dev/zero of=/dev/sda2 bs=1M count=1
```

The first MB of the swap is changed...

**_[SIZE="5"]HIBERNATE WILL NOT WORK ANYMORE IF YOUR SWAP IS ENCRYPTED [WITH A RANDOM KEY][/SIZE]_**



If you want to decrypt your home partition, or any other partition with a [SIZE="7"]keyfile[/SIZE] [if it gets "stolen"... hm. That'd not be good...]

Create a keyfile, e.g. in /etc/keyfiles

```

sudo mkdir /etc/keyfiles
sudo dd if=/dev/urandom of=/etc/keyfiles/extrapartition.key bs=1 count=32 
```

Add the keyfile to the existing partition (the partition should not be mounted):

```
sudo cryptsetup luksAddKey /dev/sdaX /etc/keyfiles/extrapartition.key
```

Replace sdaX with the partition...
You have to enter the password for the partition (if you would not have to, "anybody" on your pc [with your account password :)] could add a keyfile)

Now modify /etc/crypttab and change [e.g.]

```

home /dev/mapper/extrapartition      none      luks,retry=1,cipher=aes-cbc-essiv:sha256
```

to

```

home /dev/mapper/extrapartition       /etc/keys/extrapartition.key      luks,retry=1,cipher=aes-cbc-essiv:sha256 
```

and reboot. Done.


I hope that will work :) (it worked perfectly for me and some others)

---

### Post by Kopfgeldjaeger on 2007-04-24
Er...and: If anyone tried it, a post here would be cool! Thank you

---

### Post by mckryptyk on 2007-04-25
I think you should replace "dd if=/dev/zero of=/dev/sdaX" with "dd if=/dev/urandom of=/dev/sdaX"

because I noticed a potential security flaw in your implementation. 

If someone has physical access to the hardrive, they can do a bit dump of the encrypted partitions to determine where the data is physically located. (It might not help them now, but it will make it easier for them later.)

That is why it is better to write the partitions with "if=/dev/urandom" instead of "if=/dev/zero".

<< Actually, "if=/dev/random" would be better, but by the time it completed, your hardware might be obsolete or the kernel might run out of entropy >>

The trade-off is that this would take much longer to complete the "dd" command.

---

### Post by Kopfgeldjaeger on 2007-04-25
Hm. Yes, 'they' could see what is shreddered...

If you have the time, it'd be really better with urandom. But for my 300GB drive, it would have been at least 8 or 9 times slower.. Hm. 

greetings

---

### Post by Chachee on 2007-05-02
Is there a way to modify this so you would have to use a usb key with a cert/keyfile on it?  Boot, input key, enter password.

I have a box I will be setting up in the next few days and will run this through it. 

Anything different for installing this on server you can think of off hand?

JT

---

### Post by quark_77 on 2007-05-02
Hi Kopfgeldjaeger,

I followed your tutorial to the letter. I have the following setup:
```
/dev/sda9 = linux swap
/dev/sda12 = linux root (AES enc)
/dev/sda13 = home, AES
```

/dev/sda12 mounts successfully as /dev/mapper/root using crypttab, however, home does not. It falls over with the following error:
```
Enter LUKS passphrase: 
Unable to make device node for 'temporary-cryptsetup-6019'
Failed to read from key storage
Command failed.
```

Any Ideas? This occurs at boot time.

Thanks, Quark_77

---

### Post by Kopfgeldjaeger on 2007-05-02
@Quark:
Do you use a key file? What happens when you try to luksOpen it with a live-cd?

@Chachee:
Well, I think this is possible. But I do not really know if you have access to the USB-Stick at boot time. You could try it as I described it above - maybe it only works with the home-partition, but not with the root-partition [because /etc/fstab].

greetings

---

### Post by quark_77 on 2007-05-02
Hi Kopfgeldjaeger,

I noticed a bunch of boot time errors saying sucha node couldn't be created under /dev/.static/dev/mapper. One look in there and no mapper! So I just did this:
```
sudo mkdir /dev/.static/dev/mapper
sudo mount -a
```
and up came /dev/mapper/home. Bingo. That's better!!

Two questions:
[LIST]
[*]Can you offer any guidance on using key files with luks?
[*]How do we use alternative ciphers such as Serpent?
[/LIST]

Thanks for the great tutorial, it's easier for me to follow than the German version!

Quark_77

---

### Post by Kopfgeldjaeger on 2007-05-02
@Keyfiles: Just look at the end of the HowTo ;)
@Alternative Ciphers: 
Add "serpent" to your /etc/initramfs-tools/modules and "sudo modprobe serpent".
The change
cryptsetup -c aes-cbc-essiv:sha256 -y -s 256 luksFormat /dev/sda9
--------------------^^^^^^^^^^^^^
this. I'm searching for what you can use instead of that...

greetings

---

### Post by Wurst09 on 2007-05-02
Hey folks, I've got a question. I followed the instructions (well basically the german version) and everything worked fine. Instead of the normal aes I used the padlock modules which is a hardware implementation of aes in a VIA cpu.
```
modprobe padlock
```
does the job like aes and I was able to encrypt and mount my partitions.
Of course I load padlock instead of aes in "etc/initramfs-tools/modules", but when it comes to updating the modules I get a nasty error:
```
update-initramfs: Generating /boot/initrd.img-2.6.20-15-generic
cat: /proc/cmdline: No such file or directory
/proc/devices: fopen failed: No such file or directory
Is device-mapper driver missing from kernel?
Failure to communicate with kernel device-mapper driver.
/proc/devices: fopen failed: No such file or directory
Is device-mapper driver missing from kernel?
Failure to communicate with kernel device-mapper driver.
Incompatible libdevmapper 1.02.08 (2006-07-17)(compat) and kernel driver 
Command failed
cryptsetup: WARNING: failed to determine cipher modules to load for root

```

When I try to boot with the encrypted partition I get an error that padlock could not be loaded and apparently linux falls back to normal aes. I'm able to mount / but then again I don't get gnome but only console and an error that the xserver crashed.
I'm trying to get you some bootlogs...

I would be very thankful if anyone has a possible solution for this problem.

---

### Post by Kopfgeldjaeger on 2007-05-02
Hm... strange. I have no idea what could be wrong. But I know that a libdevmapper-error  occurs when you "update-initramfs" in a chrooted-system, too.

greetings

---

### Post by Wurst09 on 2007-05-02
When I boot up, I get an error:
```
FATAL: Error inserting padlock (/lib/modules/2.6.~/kernel/drivers/crypto/padlock.ko): No such device.
Setting up cryptographic volume root (based on /dev/hda3)
Enter LUKS Passphrase:...
```

Seems like he can't find the module...

---

### Post by Kopfgeldjaeger on 2007-05-02
Could you paste the menu.lst entry here?

greetings

---

### Post by quark_77 on 2007-05-02
> **Kopfgeldjaeger said:**
> @Keyfiles: Just look at the end of the HowTo ;)
@Alternative Ciphers: 
Add "serpent" to your /etc/initramfs-tools/modules and "sudo modprobe serpent".
The change
cryptsetup -c aes-cbc-essiv:sha256 -y -s 256 luksFormat /dev/sda9
--------------------^^^^^^^^^^^^^
this. I'm searching for what you can use instead of that...

greetings

The line we need is:  serpent-cbc-essiv:sha256. I have a custom build kernel I compiled all the modules in (Y as opposed to M) in the crypto section so I don't have to worry about loading modules in the initramfs...

Sorry I missed the obvious keys bit at the end... duh. Thanks once again, fantastic howto.

---

### Post by Wurst09 on 2007-05-02
ok here we go.
menu.lst
```

# kopt=root=/dev/mapper/root ro

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.20-15-generic root=/dev/mapper/root ro quiet locale=de_DE
initrd		/initrd.img-2.6.20-15-generic
savedefault
boot
```

crypttab
```

# <target name>	<source device>		<key file>	<options>
root /dev/hda3 none luks,retry=1,cipher=aes-cbc-essiv:sha256
```

fstab
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
#UUID=bb27caa8-3b1e-4437-b1f7-63aac20c5851 /               xfs     defaults        0       1
/dev/mapper/root /               xfs    defaults,errors=remount-ro 0       1

# /dev/hda1
UUID=7def55ef-29e1-4bf5-86cb-1790a0eed746 /boot           ext3    defaults        0       2
# /dev/hda2
UUID=99b54d50-6d38-44ef-ab93-d6f112bb3703 none            swap    sw              0       0
# /dev/sda1
UUID=1a3ca81c-9432-4d87-b765-6140f69df618 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda        /media/cdrom1   udf,iso9660 user,noauto     0       0
```

modules
```

# List of modules that you want to include in your initramfs.
#
# Syntax:  module_name [args ...]
#
# You must run update-initramfs(8) to effect this change.
#
# Examples:
#
# raid1
# sd_mod
padlock
dm-crypt
dm-mod
sha256
```

I use only two partitions so there is no /home...

---

### Post by Kopfgeldjaeger on 2007-05-03
In your crypttab is
"root /dev/hda3 none luks,retry=1,cipher=aes-cbc-essiv:sha256"
But you do not load the module aes. As you want to use padlock, try it with another cipher=x in your crypttab. And remove the "quiet" from the menu.lst entry.

greetings (Ich hoff mal es funzt ;) )

---

### Post by m0untainrebel on 2007-05-04
i just installed a fresh install of ubuntu feisty and followed these instructions from the top. but when i get to running this line of code:

```
update-initramfs -u All
```

i get this error:

```

update-initramfs: Generating /boot/initrd.img-2.6.20-15-generic
cat: /proc/cmdline: No such file or directory
/proc/devices: fopen failed: No such file or directory
Is device-mapper driver missing from kernel?
Failure to communicate with kernel device-mapper driver.
/proc/devices: fopen failed: No such file or directory
Is device-mapper driver missing from kernel?
Failure to communicate with kernel device-mapper driver.
Incompatible libdevmapper 1.02.08 (2006-07-17)(compat) and kernel driver 
Command failed
cryptsetup: WARNING: failed to determine cipher modules to load for root

```

here are my files:

/boot/grub/menu.1st
```

# kopt=root=/dev/mapper/root ro

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=/dev/mapper/root ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=/dev/mapper/root ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

```

/etc/crypttab
```

# <target name> <source device>         <key file>      <options>
root /dev/sda3 none luks,retry=1,cipher=aes-cbc-essiv:sha256
home /dev/sda4 none luks,retry=1,cipher=aes-cbc-essiv:sha256

```

/etc/fstab
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
#UUID=83a27924-c569-4bdc-986e-959f382df70e /               ext3    defaults,errors=remount-ro 0       1
/dev/mapper/root /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=60845444-a7fa-4077-9fb1-74e7309de74c /boot           ext3    defaults        0       2
# /dev/sda4
#UUID=91a916b9-207b-4a83-90f3-6c1a5b6dec35 /home           ext3    defaults        0       2
/dev/mapper/home /home           ext3    defaults                       0       0
# /dev/sda2
UUID=637ddfb7-d2ae-4fb2-9857-f9f6fa72892b none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

/etc/initramfs-tools/modules
```

# raid1
# sd_mod
aes
dm-crypt
dm-mod
sha256

```

thanks!

---

### Post by Kopfgeldjaeger on 2007-05-04
Try this:
sudo mount -o bind /dev /media/root/dev
sudo mount -o bind /proc /media/root/proc

greetings

---

### Post by m0untainrebel on 2007-05-04
> **Kopfgeldjaeger said:**
> Try this:
sudo mount -o bind /dev /media/root/dev
sudo mount -o bind /proc /media/root/proc

greetings

awesome, thanks, it worked! i also had to change my menu.1st file around a bit, because it was giving me this:

```
Error 15: File not found

Press any key...
```

and then went back to grub. then i figured out that my menu.1st file was wrong. i had to change this:

```

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=/dev/mapper/root ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=/dev/mapper/root ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

```

to

```

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,0)
kernel          /vmlinuz-2.6.20-15-generic root=/dev/mapper/root ro
initrd          /initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,0)
kernel          /vmlinuz-2.6.20-15-generic root=/dev/mapper/root ro single
initrd          /initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /memtest86+.bin
quiet

```

and it works fine. thanks!

---

### Post by Wurst09 on 2007-05-04
> **Kopfgeldjaeger said:**
> In your crypttab is
"root /dev/hda3 none luks,retry=1,cipher=aes-cbc-essiv:sha256"
But you do not load the module aes. As you want to use padlock, try it with another cipher=x in your crypttab. And remove the "quiet" from the menu.lst entry.

greetings (Ich hoff mal es funzt ;) )

Hi Kopfgeldjäger,
when I load up the modules, I get this:
```
root@ubuntu:/# modprobe padlock
root@ubuntu:/# modprobe dm-crypt
root@ubuntu:/# modprobe dm-mod
root@ubuntu:/# modprobe sha256
root@ubuntu:/# cat /proc/crypto
name         : sha256
driver       : sha256-generic
module       : sha256
priority     : 0
refcnt       : 1
type         : digest
blocksize    : 64
digestsize   : 32

name         : cbc(aes)
driver       : cbc-aes-padlock
module       : padlock_aes
priority     : 400
refcnt       : 1
type         : blkcipher
blocksize    : 16
min keysize  : 16
max keysize  : 32
ivsize       : 16

name         : ecb(aes)
driver       : ecb-aes-padlock
module       : padlock_aes
priority     : 400
refcnt       : 1
type         : blkcipher
blocksize    : 16
min keysize  : 16
max keysize  : 32
ivsize       : 0

name         : aes
driver       : aes-padlock
module       : padlock_aes
priority     : 300
refcnt       : 1
type         : cipher
blocksize    : 16
min keysize  : 16
max keysize  : 32

name         : md5
driver       : md5-generic
module       : kernel
priority     : 0
refcnt       : 1
type         : digest
blocksize    : 64
digestsize   : 16

```
With this I can mount my already encrypted harddrive with the LiveCD without problems...
```
root@ubuntu:/media# mkdir boot
root@ubuntu:/media# mkdir root
root@ubuntu:/media# cryptsetup luksOpen /dev/hda3 root
Enter LUKS passphrase: 
key slot 0 unlocked.
Command successful.
root@ubuntu:/media# mount /dev/mapper/root root
```
The funny thing is, when I boot up I can mount and decrypt my harddisk but I only get it "read-only"-mounted so there occour some problems during the rest of the startup (no XOrg due to the incapability to write a temporary file I guess)

So the question remains: why is there a problem with padlock instead of aes (can't load module at startup) and why is my rootpartition readonly mounted??

Best regards and thanks for the help so far. I hope you can figure something out with this infos...

Didn't test that yet, but I've read this:
> [https://help.ubuntu.com/community/EncryptedFilesystem:](https://help.ubuntu.com/community/EncryptedFilesystem:)
If you use Ubuntu 6.10, your fstab won't use /dev/* anymore, but instead UUIDs. Therefore, you need to find out the UUID by using the following command:

$ sudo vol_id -u /dev/mapper/cryptoroot

Instead of the "/dev/mapper/cryptoroot", you enter the UUID - hence the line in your /mnt/target/etc/fstab will look similar to this one:

UUID=25e3f85a-3488-d58e-9372-f31a45789035 /               ext3    defaults,errors=remount-ro 0       1


Also found this one:
> [https://help.ubuntu.com/community/EncryptedFilesystemHowto](https://help.ubuntu.com/community/EncryptedFilesystemHowto)
I've just finished following this Howto in a fresh Xubuntu 6.10 installation. A couple things have changed in Edgy that affect this:

      You will get an error message about an incompatability in libdevmapper (IIRC). To fix this, you must modprobe dm-mod. See [WWW] this page. You should only need to do this once.

      Upstart will block the password from being entered; see [WWW] [https://launchpad.net/products/upstart/+bug/67799](https://launchpad.net/products/upstart/+bug/67799). Simply follow the fix in that bug, and remove 'quiet splash' from the default entry in /boot/grub/grub.conf.

      This is the thorniest: the script won't correctly get rid of /var, and therefore can't link /var to /usr/var, which means GDM won't start and you'll be stuck in a shell. I have no idea why. In any case, I was able to fix it by booting into knoppix and deleting var off the unencrypted partition, then booting into single-user ("recovery") mode and linking it while the encrypted partition was correctly mounted. Be sure to boot into single-user mode at that point. A regular boot will leave you with a broken sudo command ( the error message mentions something in /var/log/sudo ((again, IIRC)), which of course won't exist until you do the linking) meaning the only way to reboot will be to power cycle. Once I did the link, I rebooted normally and it worked.


---

### Post by Wurst09 on 2007-05-04
Sorry for doubleposting...
I've made some little progress. I don't get the error at bootup that the padlock module could not  be found.
I just added instead of aes in the modules:
```
padlock-aes
padlock_aes
padlock
```
Seems like one of those did the job...:) 

I still got the problem that my filesystem seems to be mounted readonly..
It seems like there is some similar problem
> This is the thorniest: the script won't correctly get rid of /var, and therefore can't link /var to /usr/var, which means GDM won't start and you'll be stuck in a shell. I have no idea why. In any case, I was able to fix it by booting into knoppix and deleting var off the unencrypted partition, then booting into single-user ("recovery") mode and linking it while the encrypted partition was correctly mounted. Be sure to boot into single-user mode at that point. A regular boot will leave you with a broken sudo command ( the error message mentions something in /var/log/sudo ((again, IIRC)), which of course won't exist until you do the linking) meaning the only way to reboot will be to power cycle. Once I did the link, I rebooted normally and it worked.
but I don't understand the solution... Maybe you could enlighten me...
Best regards.

*EDIT*
OK Problem solved... Somehow :)
Did the HowTo again and this time I choosed ext3 as root filesystem instead of xfs. AND IT WORKES... Don't ask me what went wrong when I tried with XFS but no no problems...
Well another happy Ubuntuuser with a fullencryped harddrive :)
Thanks for all the help and of course BIG THANKS for the HowTo.
Best Regards.

---

### Post by michux on 2007-05-07
Here is another howto that has proven to work fine in many cases:

[http://polishlinux.org/howtos/encrypted-home-partition-in-linux/](http://polishlinux.org/howtos/encrypted-home-partition-in-linux/)

(encrypted home partition + auto-mounting it when logging in)

---

### Post by Kopfgeldjaeger on 2007-05-07
Yeah... The personal data is on /home, but if you print something with OOo and this becomes saved in /var/xxx ? You cannot be absolutely sure that this is really secure.... But thanks for the link ;)

@Wurst: Great! I already heard somewhere else, that is does not work with XFS THIS way...

greetings

---

### Post by michux on 2007-05-08
> **Kopfgeldjaeger said:**
> Yeah... The personal data is on /home, but if you print something with OOo and this becomes saved in /var/xxx ? You cannot be absolutely sure that this is really secure.... But thanks for the link ;)

@Wurst: Great! I already heard somewhere else, that is does not work with XFS THIS way...

greetings

There is no problem with making /tmp a separate partition and encrypting it as well using the same tutorial. Or even encrypting most of your hard drive (or all of it), but I think it isn't very reasonable. 

Encrypted home partition is a good compromise between speed, security and troublelessness (is there such a word? :P)

For a more secure setup also encrypt /tmp and swap partition. Encrypting everything is a bit paranoid imho.

---

### Post by michux on 2007-05-26
BTW, there is another tutorial here: [TrueCrypt Tutorial: Truly Portable Data Encryption](http://polishlinux.org/howtos/truecrypt-howto/) -- it is a continuation of the tutorial for DM_Crypt explaining the steps to achieve home drive encryption with full automacy, but this time with TrueCrypt.

---

### Post by IamAcoconut on 2007-05-29
What to do after a kernel upgrade? ( 2.6.20-16)
My menu.lst entries look as follows:
```
title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.20-16-generic root=/dev/mapper/root ro quiet
initrd		/initrd.img-2.6.20-16-generic
quiet
savedefault

(...)

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.20-15-generic root=/dev/mapper/root ro quiet
initrd		/initrd.img-2.6.20-15-generic
quiet
savedefault
```
The second one works. When trying to boot the first one I see the following: 
```
Setting up cryptographic volume root (based on /dev/sda3)
cryptsetup: Source device /dev/sda3 not found
```

---

### Post by user2037 on 2007-06-06
It appears the kernel 2.6.20-16 also breaks this tutorial as the end result is "cryptsetup: Source device /dev/sda* not found". Perhaps hda* is used instead of sda*.

Is it possible to use UUIDs instead?

---

### Post by snobel on 2007-06-06
-

---

### Post by samuriCat on 2007-06-07
Totally dumb question: This is fascinating, but why on earth would someone need to encrypt like this? I thought that Ubuntu was secure -- especially behind a router's firewall, like I am.

---

### Post by basquiat on 2007-06-09
Encrypting disks does not raise system security from a technical (or a remote intruder's) point of view, but it protects your system in case some gains access physically, which is a big topic for (business) laptops on conferences or in coffee shops. 

Usually companies force you to use encryption on their mobile equipment so you are not allowed to get those  gadgets outside the company's building without it. You can easily replace stolen hardware, but the loss of sensitive data can be a real showstopper.

Privacy is another point. In some countries, the state's authorities are quite fast on seizing your hardware.

---

### Post by Kopfgeldjaeger on 2007-06-09
> **user2037 said:**
> It appears the kernel 2.6.20-16 also breaks this tutorial as the end result is "cryptsetup: Source device /dev/sda* not found". Perhaps hda* is used instead of sda*.

Is it possible to use UUIDs instead?
I think you can use UUIDs in crypttab. I can't try ATM because I have hardware problems with my PC... :(
 And you should check if the crypttab, /etc/modules and so are still correct, and then make a "sudo update-initramfs -u ALL"

greetings

---

### Post by Apo2k4 on 2007-06-10
I tried putting /dev/disk/by-uuid/foo into my crypttab and did a short update-initramfs -k bar -u, but my PC still can't find the device :/

---

### Post by Kopfgeldjaeger on 2007-06-10
Hm...
Boot with a live cd, mount the root filesystem and the boot partition, eg
/media/ubuntu/ and
/media/ubuntu/boot
/media/ubuntu/etc
etc. ;)

Then chroot into the system and make a (apt)update. Now it should work with the 2.6.20-16-generic/lowlatency kernel. 

greetings

---

### Post by John.Michael.Kane on 2007-08-01
Edit:never mind..

---

### Post by Ichigosan on 2007-08-02
> **Kopfgeldjaeger said:**
> I think you can use UUIDs in crypttab. I can't try ATM because I have hardware problems with my PC... :(
 And you should check if the crypttab, /etc/modules and so are still correct, and then make a "sudo update-initramfs -u ALL"

greetings



Hi,


Anyone figured out how to get around this cryptsetup: Source device /dev/sdaX not found?

Changed /dev/sdaX in crypttab and /etc/initramfs-tools/conf.d/cryptroot to the sdaX UUID without any luck. Now when I boot up it give the same error but "cryptsetup: source device UUID not found"

---

### Post by Kopfgeldjaeger on 2007-08-12
> **Ichigosan said:**
> Hi,


Anyone figured out how to get around this cryptsetup: Source device /dev/sdaX not found?

Changed /dev/sdaX in crypttab and /etc/initramfs-tools/conf.d/cryptroot to the sdaX UUID without any luck. Now when I boot up it give the same error but "cryptsetup: source device UUID not found"
Did you try "hdaX" ?

greetings

---

### Post by silanea on 2007-09-18
> **Kopfgeldjaeger said:**
> Try this:
sudo mount -o bind /dev /media/root/dev
sudo mount -o bind /proc /media/root/proc

greetings

I was stuck with the /proc/cmdline-error following a tutorial similar to yours. That solved it. I'd suggest incorporating the two commands into your tutorial; it took me two days to find a solution to the problem.

---

