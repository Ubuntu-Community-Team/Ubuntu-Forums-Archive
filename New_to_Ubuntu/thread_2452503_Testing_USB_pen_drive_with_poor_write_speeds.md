---
title: "Testing USB pen drive with poor write speeds"
date: 2020-10-23
forum: New to Ubuntu
---

### Post by jcdenton1995 on 2020-10-23
Hello all,

So i have this [SanDisk Ultra Trek 64GB pen drive]("https://www.amazon.co.uk/SanDisk-Ultra-Ruggedized-Flash-Drive/dp/B07K7WYHDX?th=1") (USB 3.1) and I'm thinking of getting another but first I'm testing the write speed as many reviews I read before I bought it said that the write speed degrades massively over a relatively short period. I've already tested it once using the 'dd' utility, and the results were pretty poor, so I wanted to check the method I used was good. The method in question is basically what is found on [linuxconfig.com]("https://linuxconfig.org/how-to-benchmark-disk-performance-on-linux")


[LIST=1]
[*]First I used 'fdisk' to remove all partitions and created a single 'Linux' partition (not sure what Linux means in this context but it seemed the obvious choice) 
[*]ran 'sudo mkfs -t ext4 /dev/sda1' 
[*]ran 'sudo dd if=/dev/zero of=/dev/sda1 oflag=direct  bs=128k count =32k 
[/LIST]

below is a copy of dd's output...```
32768+0 records in
32768+0 records out
4294967296 bytes (4.3 GB, 4.0 GiB) copied, 527.162 s, 8.1 MB/s
```...I know there are many variables here and SanDisk probably didn't specify the write speed in the context of Linux, but they claim *read* speeds up to 130MB/s with write speeds "lower", significantly lower by the looks of my 8.1MB/s. It is in a blue USB type A port which I believe denotes the USB 3.1 standard?

For reference I have the most awful USB pen drive on earth that came as part of one of those promotional pens that companies hand out with their branding on, it doesn't even look like an electronic device and is easily ten years old, and after undergoing the same procedure plugged into the same port it was getting write speeds of 11MB/s plus.

The only steps I omitted that the guide recommends were to run the 'sync' command and also to run 'echo 3 > /proc/sys/vm/drop_caches'. I didn't use the former because I believe the 'dd' option 'oflag=direct' means caching isn't used, and the latter because I don't know what it does (also I cant use 'cat' to view the contents of that pseudo file, even with sudo, so I left it be).

Any critique is welcome!

**Edit:** From SanDisks Website -

"[COLOR=#0000ff][/COLOR]Most of the SanDisk USB flash drives fall under the entry level category  unless otherwise labeled as Ultra or Extreme. Entry level USB drives do  NOT have any defined transfer speed. The Ultra and Extreme USB flash  drives transfer speed MAY vary from 10MB/s to 260MB/s depending on the  specific product."

So, maybe it's normal? I'm still unsure...

---

### Post by sudodus on 2020-10-23
I recommend to use [FONT=Courier New]**sync**[/FONT] for all these tests (if run via a shell). If the process itself includes flushing the buffers, the [FONT=Courier New]**sync**[/FONT] command will finish at once, and, when you use it, there will be no doubt (and of course, avoid other write operations during the test).

A simple, yet fairly good write speed test is bundled in **Disks** alias [FONT=Courier New]**gnome-disks**[/FONT]. This works completely in a graphical user interface, and needs no [FONT=Courier New]**sync**[/FONT] command.

See [this link](https://unix.stackexchange.com/questions/41339/how-to-check-test-internal-card-reader-speed/552967#552967).

[hr][/hr]
If you want a [FONT=Courier New]**dd**[/FONT] command line, I would recommend [FONT=Courier New]**status=progress oflag=dsync**[/FONT]

See [this link](https://unix.stackexchange.com/questions/11262/how-do-i-know-if-dd-is-still-working/606946#606946) that is also mentioning the shellscript [FONT=Courier New]**watch-flush**[/FONT] (which is part of [mkusb](https://help.ubuntu.com/community/mkusb)).

[hr][/hr]
You can [wipe the whole drive](https://help.ubuntu.com/community/mkusb/wipe#Wipe_the_whole_device) (overwrite with zeros) with mkusb. This will restore the write speed of a well used (and tired) USB pendrive or memory card to almost the original speed. But don't do it too often because of the wear of memory cells.

---

### Post by jcdenton1995 on 2020-10-23
Thanks, this is really helpful. Especially being able to use mkusb to completely wipe a drive, as I did use Disks to do this after I (believe) I messed up the memory stick, although I'm not sure exactly what I did wrong. Also the 'status=progress' option is a little buggy for me for some reason.

Am I right in thinking that a good all round method of formatting a drive to work within Linux is to use fdisk to remove the existing partitions (if any) before creating a new GPT partition table and then populating it with one or more new partitions of the type 'Linux partition' (I don't understand what this is because it doesn't seem to refer to the partitioning scheme or the filesystem type?) before using mkfs to format the new partition as ext4?

Sorry if that's a bit wild, I only partially understand the whole shebang.

---

### Post by tea for one on 2020-10-23
> **jcdenton1995 said:**
> Am I right in thinking that a good all round method of formatting a drive to work within Linux is to use fdisk to remove the existing partitions (if any) before creating a new GPT partition table and then populating it with one or more new partitions of the type 'Linux partition' 

To create partition tables and partitions, it is easier to use gparted from the repositories.

[https://gparted.org/](https://gparted.org/)

---

### Post by GhX6GZMB on 2020-10-23
You won't find _any_ USB-Flash stick with high write speeds. It's in the technology.
The memory core is NAND-Flash and has certain write times (measured in ms, not ns). That's just the way it is. Semiconductor physics.
Read times are a completely different story. Reads are fast, and with block/sector buffering even faster.

---

### Post by sudodus on 2020-10-24
> **jcdenton1995 said:**
> 
Am I right in thinking that a good all round method of formatting a drive to work within Linux is to use fdisk to remove the existing partitions (if any) before creating a new GPT partition table and then populating it with one or more new partitions of the type 'Linux partition' (I don't understand what this is because it doesn't seem to refer to the partitioning scheme or the filesystem type?) before using mkfs to format the new partition as ext4?

Sorry if that's a bit wild, I only partially understand the whole shebang.

You can use fdisk like that, but I think it is straightforward to **remove the whole partition table by wiping the first mibibyte** (easy with mkusb). After that most partitioning tools will work (but if the drive is excessively slow it will usually help to wipe the whole device).

I agree with the  *@ tea for one* that gparted is a good tool for partitioning. It is available by default in *live Ubuntu*, and you can install it in *installed Ubuntu*.

```

sudo apt update
sudo apt install gparted

```

---

### Post by jcdenton1995 on 2020-10-24
> **tea for one said:**
> To create partition tables and partitions, it is easier to use gparted from the repositories.

Thanks, I totally agree, but I always try to learn how to use the most basic command line utilities so I know I will be able to use them over multiple distros and potentially in scripts, if I get that far. 

> **ml9104 said:**
> You won't find _any_ USB-Flash stick with high write speeds. It's in the technology.
The memory core is NAND-Flash and has certain write times (measured in ms, not ns). That's just the way it is. Semiconductor physics.
Read times are a completely different story. Reads are fast, and with block/sector buffering even faster.

Yes, it looks like I underestimated the extent to which manufacturers will go to advertise a product. I mean don't get me wrong it's an inexpensive memory stick and I'd happily buy another, but when they claim read speeds up to 130 MB/s but with slower write speeds, I just didn't expect more than 10 times slower I guess...

> **sudodus said:**
> You can use fdisk like that, but I think it is straightforward to **remove the whole partition table by wiping the first mibibyte** (easy with mkusb). After that most partitioning tools will work (but if the drive is excessively slow it will usually help to wipe the whole device).

Thanks, out of interest is this because the first mebibyte will contain all the metadata like the partition table etc. with the actual partitions and their data normally starting at the first mebibyte boundary (I've just been reading about partition / sector alignment and I feel like this is related?)

---

### Post by sudodus on 2020-10-24
The partition table as well as the boot structure of grub (for BIOS mode alias CSM alias legacy mode) are all within the first mibibyte, so wiping it will remove many causes of [confusion](https://askubuntu.com/questions/144852/cant-format-my-usb-drive-i-have-already-tried-with-mkdosfs-and-gparted/933035#933035) for the partitioning tool, that you want to use later on.

fdisk is one of the the text mode tools, parted another one and gdisk a third one (gdisk is dedicated to gpt). There is also sfdisk, a script-oriented flavour of fdisk if you wish.

[hr][/hr]
[This link shows some aspects of USB drive speed and some links to test results](https://help.ubuntu.com/community/Installation/FromUSBStick/pre)

---

### Post by kurt18947 on 2020-10-25
> **tea for one said:**
> To create partition tables and partitions, it is easier to use gparted from the repositories.

[https://gparted.org/](https://gparted.org/)

Gparted is very good.

---

### Post by jcdenton1995 on 2020-10-25
I see, thanks for all your help, as well as the links, (and to everyone else too!).

---

### Post by C.S.Cameron on 2020-10-25
Phoronix make some very good benchmarking software

[https://www.phoronix-test-suite.com/?k=downloads](https://www.phoronix-test-suite.com/?k=downloads)

---

