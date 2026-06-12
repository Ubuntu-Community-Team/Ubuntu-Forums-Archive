---
title: "Howto: Put GParted Live on a Partition"
date: 2008-08-04
forum: Outdated Tutorials &amp; Tips
---

### Post by RATM_Owns on 2008-08-04
NOTE:
Items colored in [COLOR=red]red[/COLOR] will have to be replaced by your own value.

Why would you want GParted on your hard disk? Because it's easy to do and you don't need to keep track of any CDs.

You'll need, say a 120MB partition (preferably ext3, but it could be anything GRUB reads) just to be safe. If you don't have one, you can make one with GParted Live CD or Ubuntu Live CD (System->Administration->Partition Editor)

Now let's say you have a 120MB ext3 partition at /dev/sda3
That's mine. Yours will probably be different.

The first step would be to switch to the omni-potent root.
```
sudo -s
```Next, let's mount the 120MB partition you made, I'm mounting it in /mnt, you can replace that.
```
mount -t [COLOR=red]ext3[/COLOR] /dev/[COLOR=red]sda3 /mnt[/COLOR]
```Download the latest stable release of GParted .zip file found here:
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)

Next, extract the GParted .zip to where the partition is.
```
unzip gparted-live-*.zip -d [COLOR=red]/mnt[/COLOR]
```To avoid mistakes, delete /mnt/makeboot.bat
```
rm [COLOR=red]/mnt[/COLOR]/makeboot.bat
```Finally, let's edit /boot/grub/menu.lst to allow you to boot into GParted.
```
cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
gedit /boot/grub/menu.lst
```And add these lines:
> title GParted live
root [COLOR=red](hd0,2)[/COLOR]
kernel         /live/vmlinuz1 toram boot=live union=aufs noswap noprompt vga=788 ip=frommedia
initrd         /live/initrd1.img
boot

---

### Post by dodle on 2008-09-03
When GParted boots I get the repeated error that initd can't find /dev/hdc.  Something like "device not found".  I don't have an hdc, only one hard drive.  It sounds like initd is looking for a cdrom.

---

### Post by Val3r10 on 2008-12-12
> **RATM_Owns said:**
> [...] add these lines:
kernel /live/vmlinuz1 **[COLOR="Red"]toram[/COLOR]** boot=live union=aufs noswap noprompt vga=788 ip=frommedia
Thanks for your tip.
Actually I've been fighting against for days because the "toram" cheatcode seems not properly working at all, whenever booting from devices less /dev/hdc. 
I.e. from hard disk partition or usb flash.

This way, the root partition is always locked in GParted... 

Do you have some workaround for this heavy issue ?
(which makes almost unuseful the whole goal for using a partition editor from boot disk)

Thank you

---

