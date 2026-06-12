---
title: "How do I make a bootable USB memory stick for trying out diffterent .iso images with?"
date: 2014-02-05
forum: New to Ubuntu
---

### Post by Punchy71 on 2014-02-05
Greetings,
   I am currently running Ubuntu 13.10 on my laptop and  trying to reformat my USB memory stick so I can try out different Linux distros. I just tried to reformat the stick but it didn't seem to do anything. When I point to the stick and right click properties it shows that my stick is 4GB in size but has the MSDOS type filesystem. I tried to reformat it to EXT4 but it didn't seem to take. What am I doing wrong?

Thank you

---

### Post by monkeybrain20122 on 2014-02-05
[http://liveusb.info/dotclear/index.php?pages/install](http://liveusb.info/dotclear/index.php?pages/install)

This is really easy to use. Add its repository and the gpg key to your sources.list following the instructions and install multisysem (ignore the last line usermod blah blah, that is for Debian). You can create a multiboot live usb with many distros. The usb should be formatted to FAT. 

I also find the disk utility a bit strange. So I just installed gparted instead (from the repo)

---

### Post by Punchy71 on 2014-02-05
> **monkeybrain20122 said:**
> [http://liveusb.info/dotclear/index.php?pages/install](http://liveusb.info/dotclear/index.php?pages/install)

This is really easy to use. Add its repository and the gpg key to your sources.list following the instructions and install multisysem (ignore the last line usermod blah blah, that is for Debian). You can create a multiboot live usb with many distros. The usb should be formatted to FAT. 

I also find the disk utility a bit strange. So I just installed gparted instead (from the repo)

Can I download and install this from the Ubuntu Software Center? That is currently the only way I know how to download and install programs using Ubuntu.

---

### Post by monkeybrain20122 on 2014-02-05
> **Punchy71 said:**
> Can I download and install this from the Ubuntu Software Center? That is currently the only way I know how to download and install programs using Ubuntu.

No it is not in the Ubuntu repository. Just cut and paste those commands in the instructions in the terminal and press enter one after the other would work.

Also, you may consider installing the synaptic package manager instead of the software center. It is much faster and gives you a lot more control (except it doesn't have the paid or no free applications in the software Centre) You can install it from the software centre or just in terminal
sudo apt-get install synaptic

---

### Post by Dave_L on 2014-02-05
Note that it's also possible to boot directly from an .iso.  That can save a lot of time.  I don't have the instructions handy, but there are examples around here.

---

### Post by stinkeye on 2014-02-06
> **Dave_L said:**
> Note that it's also possible to boot directly from an .iso.  That can save a lot of time.  I don't have the instructions handy, but there are examples around here.

Agree with this.
Booting from an iso is an easy way to test distros.
Its just a matter of putting the right code in **/etc/grub.d/40_custom**  and running **sudo update-grub**
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)


This is my standard menu entry in **/etc/grub.d/40_custom**....
```
menuentry 'ISO Lubuntu 13.10  ' {

set isofile="/distros/lubuntu-13.10-desktop-amd64.iso"

loopback loop ([COLOR="#FF0000"]**hd1,6**[/COLOR])$isofile

linux (loop)/casper/[COLOR="#EE82EE"]**vmlinuz**[/COLOR] boot=casper iso-scan/filename=$isofile noprompt noeject 

initrd (loop)/casper/initrd.lz 

}
```

Change **set isofile=** to reflect the location of your iso.
Change **loopback loop ([COLOR="#FF0000"]hd1,6[/COLOR])** to reflect your drive and partition where iso is.....first drive first partition is hd0,1
You can check this at the grub menu by pressing the "c" key and running...
```
search -l [COLOR="#FF8C00"]**label**[/COLOR]
``` 
where [COLOR="#FF8C00"]**label**[/COLOR] is the label of the partition containing your iso file.
**sudo blkid** will show your partition labels.

The other thing I may need to change is...
```
linux (loop)/casper/[COLOR="#EE82EE"]**vmlinuz.efi**[/COLOR] boot=casper iso-scan/filename=$isofile noprompt noeject [COLOR="#00FF00"]**nomodeset**[/COLOR]
```
Mount the iso and look in the **/casper** diectory for [COLOR="#EE82EE"]**vmlinuz**[/COLOR].
If it has an **efi** extension, use **[COLOR="#EE82EE"]vmlinuz.efi[/COLOR]** in place of [COLOR="#EE82EE"]**vmlinuz**[/COLOR] 
In cases were the boot from iso stalls, adding [COLOR="#00FF00"]**nomodeset**[/COLOR] usually fixes.

---

### Post by sudodus on 2014-02-06
> **Punchy71 said:**
> Greetings,
   I am currently running Ubuntu 13.10 on my laptop and  trying to reformat my USB memory stick so I can try out different Linux distros. I just tried to reformat the stick but it didn't seem to do anything. When I point to the stick and right click properties it shows that my stick is 4GB in size but has the MSDOS type filesystem. I tried to reformat it to EXT4 but it didn't seem to take. What am I doing wrong?

Thank you

Try ***Unetbootin*** according to [Paul Sutton's Unetbootin how to]("http://zleap.net/unetbootln-usb-how_to/")

or ***mkusb*** according to this [Ubuntu Forums tutorial "Howto make USB boot drives"]("http://ubuntuforums.org/showthread.php?t=1958073")

Read this general description [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

You need *not* reformat the drive if you use mkusb. The installation will  overwrite whatever is on the drive and clone what is needed from the  iso file. This works for Ubuntu install iso files as well as for several other (but not all) iso files.

---

### Post by mastablasta on 2014-02-06
or you can use Yumi: [http://www.pendrivelinux.com/yumi-multiboot-usb-creator/](http://www.pendrivelinux.com/yumi-multiboot-usb-creator/)
or multiysystem: [http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/](http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/)

i use Yumi to boot various images on 16GB drive i have with me.

---

### Post by monkeybrain20122 on 2014-02-06
One of OP's questions is how to format the disk. I just use gparted as the disk-utility apparently does nothing. Does d-u work for anyone?

BTW unetbootin doesn't do multiboot.

---

