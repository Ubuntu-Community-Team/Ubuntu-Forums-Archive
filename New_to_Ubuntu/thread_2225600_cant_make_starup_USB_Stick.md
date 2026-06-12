---
title: "cant make starup USB Stick"
date: 2014-05-22
forum: New to Ubuntu
---

### Post by gtravis3 on 2014-05-22
Howdy,
I have ubuntu up and running on a Dell XPS M140. But I think Ubuntu Desktop is too much for this old processor.  So I decided to make a live debian stick, Debian xfce,  and test it out.
The software downloaded with no problem, however, when I try to make the startup stick, I get the message:
**Invalid version string 'GNU/Linux'**
I was able to make startup sticks yesterday to look at lighter versions of Ubuntu. However, I don't know if the "use" vs install versions cant access my wireless network, because it did not, I did not want to install it. 
I googled the error message, but it seems that all the things that I could find were several years old and appeared to not be applicable to the current version of Desktop.
I would appreciate your advice.

---

### Post by LastDino on 2014-05-22
Have you tried with Unetbootin? 

Pr-installed one only likes Ubuntu.

---

### Post by slickymaster on 2014-05-22
Here's some good reads for you: [Debian Live Manual]("http://live.debian.net/manual/3.x/html/live-manual.en.html#1") and [Installing Debian on a USB stick -- live usb vs a true and full installation]("http://verahill.blogspot.pt/2012/02/installing-debian-on-usb-stick-live-usb.html")

---

### Post by gtravis3 on 2014-05-22
Well howdy again!
I had been using Startup Disk Creator fine until this morning.
Is Unetbootin a program that I need to download?
I tried **use** the lighter version of Ubuntu that you recommended, but was uncomfortable with not having  bring up my wireless.

---

### Post by LastDino on 2014-05-22
Yes, there are several similar programs available. One more is; Universal USB installer.

Just make sure Debian is listed in supported versions and you format the stick to fat32, you're good to go.

---

### Post by gtravis3 on 2014-05-22
Well howdy again!
I had been using Startup Disk Creator fine until this morning.
Is Unetbootin a program that I need to download?
I tried **use** the lighter version of Ubuntu that you recommended, but was uncomfortable with not having  bring up my wireless.

---

### Post by gtravis3 on 2014-05-22
Hi slickymaster,
I have looked at those reads, earlier, but I had anticipated that Ubuntu would at least **create** the startup on the flash drive using the debian live download.

---

### Post by gtravis3 on 2014-05-22
I went to the Unetbootin site, and clicked on the download for Linux.
After a bit of a wait, rather than a download, I got a page full of stuff like this:
ELF&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;è-4&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;4&#65533; &#65533;&#65533;(&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;À&#65533;&#65533;À&#65533;x/D&#65533;x/D&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;t&#65533;&#65533;t±t±&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;ýáÇUPX!
&#65533;&#65533;&#65533;&#65533;@Ü¬&#65533;@Ü¬&#65533;4&#65533;&#65533;&#376;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;?&#8216;E&#8222;h;ÞÞ¦#Öè|`2ð[!×¡6Ô%ú<&#352;GVâu&#8482;ÊC¨@ÎFËk:À&#8250;6xðÎ&#8482;z#Üo<&#8222;VV8ö"½©ÞÁÃ§á&#65533;Y>sµ4,O

---

### Post by LastDino on 2014-05-22
It is there in software centre, no need to go to its site.

---

### Post by gtravis3 on 2014-05-22
got it. Interesting that I have to run it via the command line

---

### Post by sudodus on 2014-05-22
I find Unetbootin in the System menu of 12.04.4 LTS, but I'm also happy running it from the command line. Does it work for you?

---

### Post by Tadaen_Sylvermane on 2014-05-22
```
sudo dd if=/path/to/iso of=/dev/sdX oflag=direct bs=1M
```

sdX being the drive letter of the flash drive. Do not add the partition number. I have had zero success with any of the tools to make a bootable usb on windows or linux. Above command only thing that works for me. Be careful with above though, a typo could wipe your hard drive if not careful.

---

### Post by LastDino on 2014-05-22
> **Tadaen_Sylvermane said:**
> ```
sudo dd if=/path/to/iso of=/dev/sdX oflag=direct bs=1M
```

sdX being the drive letter of the flash drive. Do not add the partition number. I have had zero success with any of the tools to make a bootable usb on windows or linux. Above command only thing that works for me. Be careful with above though, a typo could wipe your hard drive if not careful.

This might be my old hobby of hijacking threads kicking up, but I'm meaning to ask this for long time, what use is using ''bs=1M''? Is it similar to gparted leaving 1MB before partition? Does it matter if I change it to 0?

---

### Post by sudodus on 2014-05-22
> **LastDino said:**
> 
[QUOTE=Tadaen_Sylvermane;13030736]```
sudo dd if=/path/to/iso of=/dev/sdX oflag=direct bs=1M
```

sdX being the drive letter of the flash drive. Do not add the partition  number. I have had zero success with any of the tools to make a bootable  usb on windows or linux. Above command only thing that works for me. Be  careful with above though, a typo could wipe your hard drive if not  careful.

This might be my old hobby of hijacking threads kicking up, but I'm  meaning to ask this for long time, what use is using ''bs=1M''? Is it  similar to gparted leaving 1MB before partition? Does it matter if I  change it to 0?

This might be my old hobby of hijacking threads kicking up, but I'm meaning to ask this for long time, what use is using ''bs=1M''? Is it similar to gparted leaving 1MB before partition? Does it matter if I change it to 0?[/QUOTE]

1. ***dd*** is a very powerful tool, but it is nick-named 'disk destroyer' because it does what you tell it to do without questions. So if you tell it to wipe the internal drive with important data that are not backed up, it will do it. A simply typing error can make the difference between miracle and catastrophe.

I made the shell-script ***mkusb*** to make it safer to use dd. See this link

[Ubuntu Forums tutorial "Howto make USB boot drives"]("http://ubuntuforums.org/showthread.php?t=1958073")


2. ***bs***=BYTES alias block size means read and write up to BYTES bytes at a time, so it is different from gparted leaving 1MB before partition. I have found bs=4096 good in many computers.

---

### Post by Tadaen_Sylvermane on 2014-05-22
A script is a great idea. making one up now. As for the bs=1M. I really don't understand that, or the oflag=direct part. But they were part of the command I found while googling and it has worked so far so I use it every single time I need to make a bootable usb.

---

### Post by sudodus on 2014-05-23
There is an explanation of the so called operands bs= ..., conv symbols and flags in the manual page ```
man dd
```

Maybe you can find better explanations in some tutorial on the internet. Often dd works without conv symbols and flags while a good bs value makes it faster.

---

