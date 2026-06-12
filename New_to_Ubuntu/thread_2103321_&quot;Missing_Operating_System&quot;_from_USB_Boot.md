---
title: "&quot;Missing Operating System&quot; from USB Boot"
date: 2013-01-09
forum: New to Ubuntu
---

### Post by BadgerDeluxe on 2013-01-09
Hi everyone! :D I am brand-spankin new to Ubuntu (sorry for the annoyance), and Ubuntu/Linux is something that I am keenly interested in becoming familiar with as I delve deeper into programming and the like.

So I went through the process of formatting a thumb drive and putting 12.04 on it, but whenever I try to boot from the USB with this laptop it gives me the error "Missing Operating System" and just boots straight into Windows. What should be my first order of business in attempting to troubleshoot this?

My specs are as follows:
Gateway (Laptop) Model MT6831
OS: Windows Vista Home Premium
Processor: Intel Core 2 CPU - T5300 @ 1.73 GHz (2 CPUs)
Memory: 2038MB RAM

Thanks for any help in advance! :D

---

### Post by steeldriver on 2013-01-09
Hello and welcome

How exactly did you transfer the 12.04 download on to the thumb drive? just copying the iso file onto the drive is not enough, it needs to be written as a bootable image with a tool like unetbootin or pendrivelinux

---

### Post by chadk5utc on 2013-01-09
> **BadgerDeluxe said:**
> Hi everyone! :D I am brand-spankin new to Ubuntu (sorry for the annoyance), and Ubuntu/Linux is something that I am keenly interested in becoming familiar with as I delve deeper into programming and the like.

So I went through the process of formatting a thumb drive and putting 12.04 on it, but whenever I try to boot from the USB with this laptop it gives me the error "Missing Operating System" and just boots straight into Windows. What should be my first order of business in attempting to troubleshoot this?

My specs are as follows:
Gateway (Laptop) Model MT6831
OS: Windows Vista Home Premium
Processor: Intel Core 2 CPU - T5300 @ 1.73 GHz (2 CPUs)
Memory: 2038MB RAM

Thanks for any help in advance! :D

Did you set BIOS boot order on the laptop to look for usb?
What did you use to prep/install to the usb drive?

---

### Post by BadgerDeluxe on 2013-01-09
> **steeldriver said:**
> Hello and welcome

How exactly did you transfer the 12.04 download on to the thumb drive? just copying the iso file onto the drive is not enough, it needs to be written as a bootable image with a tool like unetbootin or pendrivelinux

Yes I used pendrivelinux :)

> **chadk5utc said:**
> Did you set BIOS boot order on the laptop to look for usb?
What did you use to prep/install to the usb drive?

Yeah, pendrivelinux and during the boot I make sure it boots from USB. So it seems like it tries to boot from the USB and then gives me the error.

---

### Post by chadk5utc on 2013-01-09
Ok at the ubuntu download page there is a link for the checksums bottom right of page. I suggest this be checked there is a windows utility called winmd5 or a few others that will test the files integrity. I had a friend call me last night with the same issue and it turned out for her to be a corrupted file issue during the download.

---

### Post by BadgerDeluxe on 2013-01-09
> **chadk5utc said:**
> Ok at the ubuntu download page there is a link for the checksums bottom right of page. I suggest this be checked there is a windows utility called winmd5 or a few others that will test the files integrity. I had a friend call me last night with the same issue and it turned out for her to be a corrupted file issue during the download.

Alright, currently downloading the checksum for 12.04.1 (bout 60% done) and I'll update here with any findings.

Quick video I recorded of what happens when I try, probably doesn't add any extra dimensions but just in case: [http://www.youtube.com/watch?v=VDz2aylGvJ4]("http://www.youtube.com/watch?v=VDz2aylGvJ4")

---

### Post by jtarin on 2013-01-10
You can get that error "Missing Operating System", when booting from a USB when it hasn't been formatted correctly before transferring the OS to it.

---

### Post by BadgerDeluxe on 2013-01-10
> **jtarin said:**
> You can get that error "Missing Operating System", when booting from a USB when it hasn't been formatted correctly before transferring the OS to it.

Ok, what should it be formatted to? It's been formatted to a FAT32 and then had the .iso mounted via pendrivelinux.

> **chadk5utc said:**
> Ok at the ubuntu download page there is a link for the checksums bottom right of page. I suggest this be checked there is a windows utility called winmd5 or a few others that will test the files integrity. I had a friend call me last night with the same issue and it turned out for her to be a corrupted file issue during the download.

I just tried the checksum and compared the first one I had (got via BitTorrent) and the new one (direct download via Ubuntu downloads page) and they had different checksum values.

I then proceeded to format the thumb drive and mount the NEWER .iso, but to no avail. Same issue. :/

---

### Post by jtarin on 2013-01-10
Whenever I have a "problematic" USB.....I use a WIN utility by Hewelett Packer called "[HPUSBDisk.exe]("http://en.kioskea.net/download/download-127-hp-usb-disk-storage-format-tool")".

---

### Post by BadgerDeluxe on 2013-01-10
> **jtarin said:**
> Whenever I have a "problematic" USB.....I use a WIN utility by Hewelett Packer called "[HPUSBDisk.exe]("http://en.kioskea.net/download/download-127-hp-usb-disk-storage-format-tool")".
That did the trick jtarin, thank you! :) Reformatted with that little program you gave me, re-mounted this time with 12.10 (I had tried that earlier with the same problem) but this time it worked swimmingly. Thank you guys so much, I look forward to tooling around with Ubuntu :)

---

### Post by jtarin on 2013-01-10
> **BadgerDeluxe said:**
> That did the trick jtarin, thank you! :) Reformatted with that little program you gave me, re-mounted this time with 12.10 (I had tried that earlier with the same problem) but this time it worked swimmingly. Thank you guys so much, I look forward to tooling around with Ubuntu :)Good enough!!! Any additional formatting problems with this tool? Make sure you have the latest version......but if your version works......that's all you need.I have used this to recover many corrupted USB's.

---

### Post by deierose on 2013-11-26
I have met problem of "Missing Operating System" on my Acer Windows 7 laptop. After tried many ways searched online, fortunately, the Windows Boot Genius from [http://download.cnet.com/Windows-Boot-Genius/3000-2094_4-75827488.html](http://download.cnet.com/Windows-Boot-Genius/3000-2094_4-75827488.html) support me fix the error. Then pc runs normally without data loss.

---

