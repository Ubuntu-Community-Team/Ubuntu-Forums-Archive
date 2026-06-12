---
title: "Live USB persistent encrypted | the Great Battle !"
date: 2015-03-24
forum: New to Ubuntu
---

### Post by madarada on 2015-03-24
Hello all,

I'm trying to build an USB persitent encrypted support able to boot on both most PC's and Mac machines.
A kind of Graal.
On after what I've read and test to make this USB bootable on mac machines is a very complicated matter.
It seems that there is a solution to this side:

**[https://github.com/SevenBits/Mac-Linux-USB-Loader](https://github.com/SevenBits/Mac-Linux-USB-Loader)** 
[COLOR=#b22222][I tried with no more success Lilly, Rufus, Unetbootin and so forth, from Windows, Mac and Linux...]
[/COLOR]
but that does not really work for me and I do not like deja-made solutions... :D

There are huge advantages of a permanent installation on the USB stick, but it also seems that it makes the things less versatile.

For this reason I head to a different solution. [COLOR=#b22222]**A live USB.**[/COLOR]
 following the indications of this yarn perfect:

**[http://ubuntuforums.org/showthread.php?t=2108487&page=3](http://ubuntuforums.org/showthread.php?t=2108487&page=3)**
 
(thank you to the various contributors and gurus), it becomes easy to create a Live USB with persistence (playing with casper-rw).

Unfortunately, encrypt the partition becomes a different matter.
 I do not know if it is only possible.
 After a few failures with gparted and disks I tried this stuff manually:

[B]cryptsetup --verbose --verify-passphrase luksFormat /dev/sdbx
cryptsetup luksOpen /dev/sdbx mount_usb
mkfs.ext3 -L casper-rw /dev/mapper/mount_usb
e2label /dev/mapper/mount_usb casper-rw
cryptsetup luksClose /dev/mapper/mount_usb
[/B]
the thing is that on the boot Linux just do not ask me the password to  open the partition as it is not recognise as the "main partition".

[COLOR=#000080]So I open this new thread with this double question:
 1) Is there a truly effective solution to create an USB persistent and encrypted able to boot on most Pcs and Mac?
 2) If not, is it possible to create a LIve USB with peristence, encrypted that boot on the encrypted partition?[/COLOR]

(Sorry for my poor english. I hope, however, have been quite clear).
Thanks in advance for the help..! :wink:

---

### Post by nerdtron on 2015-03-25
Do you really need it to be Live USB?

Why not do a full install on a USB drive. 16GB is enough and you can set to encrypt your home directory during the installation of Ubuntu.

---

### Post by Geoffrey_Arndt on 2015-03-25
Or another method that "may" be possible is to:

>  Create a Live persistent USB Flash stick (usbv3 is preferable),
>  After install and initial bootup . . . setup your standard desktop (wireless, restricted-extras, etc. as needed),
>  Install both "Encfs" and "Gnome-Encfs-Manager" (encfs is an encrypted file-container app, the Gnome-Encfs-Manager is a nice front end gui to manage encfs ([http://www.libertyzero.com/GEncfsM/](http://www.libertyzero.com/GEncfsM/))
>  I like to use Encfs along with a Cloud Service like Dropbox to easily encrypt folders, without needing to do so for individual files ([https://www.youtube.com/watch?v=U2kbyhYmtPo](https://www.youtube.com/watch?v=U2kbyhYmtPo))

The above is feasible (IF the Live Filesystem will be compatible with Encfs . . ?) on a Live Persistent USB Flash-stick,   the important files are encrypted , the base OS (Ubuntu or any Buntu) is not, but why encrypt anything but your sensitive data anyway?  But this may be worth checking out - - I may try it out, but I also like the CherryTree Db to contain sensitive material (and that does work quite well).

GG

---

### Post by madarada on 2015-03-26
Hello Nerdtron,

as i tried to explain it in the begining of the thread, Live USB is much more versatile than a full install when it comes to boot on different support. 
I have USB keys, full installed and encrypted that just do not boot on mac. 
In the opposite Live USB boot on those same mac.

As I wrote it, the perfect solution for me would be to make a **full installed USB with Luks encryption that could boot on ****most Pcs and Mac**. 
_I only use Live USB __for this reason._
I have not found the way to do this properly. 
If you know a way to do this, I will be more than happy that you to tell me how... :)

thank you very much for your answer !
:grin:

---

### Post by madarada on 2015-03-26
Hello Geoffrey,

I currently boot with a Live USB3 (sandisk and pny are good for that by the way).
What I've read, and which seems coherent, is that Luks encryption is far  much solid and efficient than encfs solutions.
Your way to do this, in any case, seems to be a good option for many reasons. Thanks a lot for that.
 However, I still look for The Graal that facilitates safety performance and versatility.

Thanks a lot again, best regards.
Madarada.

---

