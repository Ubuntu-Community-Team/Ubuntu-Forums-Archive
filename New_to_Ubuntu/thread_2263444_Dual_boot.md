---
title: "Dual boot"
date: 2015-02-01
forum: New to Ubuntu
---

### Post by kostas14 on 2015-02-01
Hi, i have Windows 7 on my 1th SSD and Linux Ubunut 14 on my second storage  wich has 2 partitions.

Now after reinstalling some AHCI Drivers on Windows 7 because i couldnt see my Linux Storage on Windows on Device Manager it forced me to make new GKP or something that wrote Initial Storage or something. Now i cant boot to my Windows SSD but why? 

I have not installed the Linux on the first HDD so why cant i start from it isolatet when i dont have the Linux SSD connectet?

When both are installed i am getting the Error 

Loading Operatiing System error> no such device  " a big code "
entering rescue mode

I am serching int he web for answeres but somehow i cant find specified for my problem.

How can i solve my Problems without loosing any Data and rescuing Linux again? :(

---

### Post by sandyd on 2015-02-01
> **kostas14 said:**
> Hi, i have Windows 7 on my 1th SSD and Linux Ubunut 14 on my second storage  wich has 2 partitions.

Now after reinstalling some AHCI Drivers on Windows 7 because i couldnt see my Linux Storage on Windows on Device Manager it forced me to make new GKP or something that wrote Initial Storage or something. Now i cant boot to my Windows SSD but why? 

I have not installed the Linux on the first HDD so why cant i start from it isolatet when i dont have the Linux SSD connectet?

When both are installed i am getting the Error 

Loading Operatiing System error> no such device  " a big code "
entering rescue mode

I am serching int he web for answeres but somehow i cant find specified for my problem.

How can i solve my Problems without loosing any Data and rescuing Linux again? :(

Hi, can you boot from a linux livecd, go to Unity Dash (the button at the top left of the bar), and type in 'terminal'. Open the terminal, paste the following. It should generate a file. Please place the contents of the file here with ```
 blocks.
[code]
wget http://superb-dca2.dl.sourceforge.net/project/bootinfoscript/bootinfoscript/0.61/bootinfoscript-061.tar.gz
tar xvf bootinfoscript-061.tar.gz
sudo ./bootinfoscript


```

Thanks!

Side Note: The message above sounds suspiciously like "New GPT" and "Initialize Disk" options in Windows - does either sound similar to the message you got in windows?
Side Note #2: Linux partitions are not visible in Windows unless you use drivers that can read/write to linux partitions. Try [http://www.paragon-software.com/home/extfs-windows/](http://www.paragon-software.com/home/extfs-windows/) or [http://www.ext2fsd.com/](http://www.ext2fsd.com/)

---

### Post by kostas14 on 2015-02-01
I did this bootinfoscript bevore i startet this post. it dont worked for me. I mean yes i could get the ifnormations about the Linux system and see that there is a linux system and did a few recommendet thnings from this forum but at the end i just fixed the problem with a symple tool called testdisk :)

---

### Post by kostas14 on 2015-02-01
But i still have the problem that i cant boot the Windows SSD alone. Is  it because the Bootloader is on the linux CD? i mean i have 2 different  SSD´s why should it not work when the one is disconnectet?

---

### Post by ajgreeny on 2015-02-01
It sounds as if grub (the linux bootloader) is on your SSD but the configuration files it needs to work are on the Ubuntu disk.

I also assume from what you say that the ubuntu disk is an external one that is not always attached to your computer; I did not know this from your original post, so can you confirm if this is the case please, and if so you will need to restore the Win 7 bootloader files to the SSD.

I have not used Windows of any version for many years so am not sure the best way to restore the bootloader, but if you have a Win 7 install DVD that should give you a repair facility.

---

