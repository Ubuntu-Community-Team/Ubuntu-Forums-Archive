---
title: "what is the simplest way to burn an iso to a usb"
date: 2014-02-12
forum: New to Ubuntu
---

### Post by nick58 on 2014-02-12
thank you

---

### Post by monkeybrain20122 on 2014-02-12
On Windows use something like LILI [http://www.linuxliveusb.com/](http://www.linuxliveusb.com/) or unetbootin. On Linux multisystem [http://liveusb.info/dotclear/index.php?pages/install](http://liveusb.info/dotclear/index.php?pages/install) or unetbootin or the startup disk creator on Ubuntu.. The last one is only for Ubuntu iso.

---

### Post by squakie on 2014-02-12
monkeybrain20122 mentioned several including one that is normally recommended - a semi "standard" - unetbootin.  It runs on many OS's - Windows, Linux, Mac (if I'm remembering correctly), etc..  So the experience is the same across any platforms.  It's simple to use, and you can point it to an ISO if you have downloaded one, or you can select what you want right in the unetbootin.

---

### Post by Bucky Ball on 2014-02-12
... and remember to format the USB to FAT32 before using UNetbootin, if you go that way. ;)

---

### Post by sudodus on 2014-02-12
I find it easy to use ***mkusb*** according to this

[Ubuntu Forums tutorial "Howto make USB boot drives"]("http://ubuntuforums.org/showthread.php?t=1958073")

You get general instructions and a lot of links at this Ubuntu wiki page

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

and there is a detailed help page for ***Unetbootin*** at this link

[Paul Sutton's Unetbootin how to]("http://zleap.net/unetbootln-usb-how_to/")[URL="http://ubuntuforums.org/showthread.php?t=1958073"]

[/URL]

---

### Post by asus-user on 2014-02-12
After I tried many programs to create bootable usb, I found out that **unetbootin** is best.

---

### Post by C.S.Cameron on 2014-02-12
UNetbootin has a bit ugly startup screen, I prefer Startup Disk Creator from the Live CD.
Either way you can remove the Try/Install screen by replacing the contents of syslinux.cfg with:

```
    default persistent
    label persistent
      say Booting a persistent Ubuntu session...
      kernel /casper/vmlinuz
      append  file=/cdrom/preseed/ubuntu.seed boot=casper persistent initrd=/casper/initrd.lz quiet splash noprompt --
```

for 64bit use "vmlinuz.efi"

---

### Post by Jason_Gibson on 2014-02-12
```
sudo dd if=/path/to/iso of=/dev/sdX oflag=direct bs=1M
```

Don't need special programs to do it, it's built in.

---

### Post by sudodus on 2014-02-12
Yes, ***dd*** is very powerful, but there is a reason why it is nicknamed 'disk destroyer'. The shell-script ***mkusb*** uses dd under the hood, and help you doing it safely.

---

### Post by NM5TF on 2014-02-12
> **sudodus said:**
> Yes, ***dd*** is very powerful, but there is a reason why it is nicknamed 'disk destroyer'. The shell-script ***mkusb*** uses dd under the hood, and help you doing it safely.

+100

there is a current thread about a guy that wiped his HDD using dd....:(

proceed with MUCH caution !!!

I have never had any problems using Start Up Disk Creator...:p

YMMV

tommy

---

### Post by Bucky Ball on 2014-02-12
Yea. dd is not the place to go for this unless you are a fairly experienced and confident user. I'd perhaps take a safer course.

---

### Post by asus-user on 2014-02-12
> **sudodus said:**
> Yes, ***dd*** is very powerful, but there is a reason why it is nicknamed 'disk destroyer'. The shell-script ***mkusb*** uses dd under the hood, and help you doing it safely.

**dd** stands for "**D**ata **D**escription" and is used for many purposes:

- Data transfer
- Master boot record backup and restore
- Data modification
- Disk wipe
- Data recovery
- Benchmarking drive performance
- Generating a file with random data
- Converting a file to upper case
- Creating empty files of arbitrary size

More info regarding that in [this wiki-page]("http://en.wikipedia.org/wiki/Dd_%28Unix%29#Usage").

---

### Post by sudodus on 2014-02-12
You are right *asus-user*. dd is very useful and powerful tool. I use it, but very carefully double-checking and triple-checking for typing errors. The power and lack of warnings makes it dangerous.

Simplest, yes, in the sense that dd can do the job with a short command line, but a minor typing error makes it destroy a lot of data.

So I would *not* recommend it in this thread with the title 'what  is the simplest way to burn an iso to a usb'. I would not recommend it  at all to beginners and I would be reluctant to mention it to average  linux users. ddrescue is a better alternative for data recovery from  failing drives. There are many alternatives, that are better for wiping  of whole disks, for example hdparm and dban.

---

### Post by Bucky Ball on 2014-02-12
> **sudodus said:**
>  The power and lack of warnings makes it dangerous.

Simplest, yes, in the sense that dd can do the job with a short command line, but a minor typing error makes it destroy a lot of data.

So I would *not* recommend it in this thread with the title 'what  is the simplest way to burn an iso to a usb'. I would not recommend it  at all to beginners and I would be reluctant to mention it to average  linux users.

^^^
This.

A small percentage of users, experienced or otherwise, would go that path.

---

