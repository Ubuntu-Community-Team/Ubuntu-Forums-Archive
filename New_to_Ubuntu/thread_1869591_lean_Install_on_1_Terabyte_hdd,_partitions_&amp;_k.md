---
title: "lean Install on 1 Terabyte hdd, partitions &amp; keyboard layout Questions"
date: 2011-10-26
forum: New to Ubuntu
---

### Post by Koyanggi on 2011-10-26
Hello,
I have a 500GB HDD running Windows XP pro and a 320GB external HDD that I use to back up my picture, music, video files. The 320GB back up HDD is almost full.

So I was thinking of getting a new 1 Terabyte HDD to replace my 500GB HDD. Then use that 500GB HDD as the new back up to replace the 320GB HDD.

:confused:Does that sound like a good plan?
Instead of installing Windows XP pro, I am very interested in switching to Ubuntu.

I have downloaded the Ubuntu 11.10 image file and burned it onto a CD. The Try Ubuntu (Live CD desktop) works great.:) Now I want to install it.

I have two questions about the install.

#1. Allocate drive space section.

Use the checkboxes to choose whether you'd like to:

Install Ubuntu alongside another operating system, -  I"m not going to choose this!!!!

delete your existing operating system and replace it with Ubuntu, - I'm installing onto a new 1Terebyte HDD so there is no OS to replace. This is my 2nd choice.

or – if you're an advanced user – choose the Something else option - This is my 1st choice, but I'm not an advanced user and I'm afraid I will mess things up.

:confused:Question #1. Which one should I choose? If it's Something else option, could you direct me to where I can follow step by step directions for that?

#2. Select your preferred keyboard layout.

:confused:Question #2. I have an English/Korean keyboard. Which keyboard layout should I select?

Thank you for taking the time to read this. Help or no help, It's all good. Peace form Korea

---

### Post by kemtnbkr on 2011-10-26
Welcome to the forums and Ubuntu!

Your proposed scheme with the disks would work fine in my opinion.

If you let Ubuntu auto-partition its disk space, you will end up with only 2 partitions: swap space and the root filesystem.  This setup will work fine for you, especially as you are planning on having a backup HD.

However, if you think you might want to try installing another Ubuntu/ Linux distro, or if you just want to have custom partitions so your files are a bit better separated, the advanced option will probably be your best bet.  There are tons of differing opinions on this, so I'll just give you a conservative install recommendation that is 'on average' from what I've seen (not much :) ) 

Root partition- / - 10 GiB
Swap partition- about 1 to 2 times the size of your RAM; I have 3GB of RAM and rarely use any of my swap just fyi.
Home partition /home- rest of space on HD

You can really get into depth partitioning, making separate partitions for /var, /tmp, /usr, and so on, but personally I'd recommend staying with a simpler partitioning scheme at least for your first install.  

Good luck!  Ubuntu/ Linux is very powerful, but it has a bit of a learning curve :/

As for the keyboard, I have no experience at all with anything other than US English for the setup, so sorry I can't be of more help there.

---

### Post by oldfred on 2011-10-26
My suggestion is similar to kemtnbkr. I prefer smaller system partitions but since you have 1TB I might use 20 or 25GB for / (root). I might not make all the rest of the drive /home as that is huge. And you do not have to format it all initially. I still have some unallocated space on my 640GB drive but I keep adding 25GB / partitions for each new Ubuntu release so I have my old install and have space to experiment with the next version.

If drive is only going to be Ubuntu (never Windows), I would suggest using gpt not MBR as the partitioning scheme. You then do not have any logical partitions, they are all primary and it has a backup in case of problems. You do have to create a tiny bios_grub partition to correctly install grub2's boot loader to the drive.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

If using gpt create a 1MB bios_grub partition at the beginning of the drive. I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning.

GPT Advantages srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)

---

### Post by Koyanggi on 2011-11-02
Thank you Oldfred & Kemtnbkr for your helpful information and advice. :) I really appreciated it.

I went out and grabbed the 1T HDD, threw in the Cd and followed the instructions. I'm coming to you now from my new 11.10 install and all seems great. I moved all my music (286GB worth), pictures, and a few videos I wanted to still watch. Everything is working great so far. 

At this moment I can tell you that I really don't know what I'm am doing. I am just exploring around and seeing what things do. 

I had to get a new driver for my GPU, but that was easy.

I got the video player VLC. Perfect, plays all the formats that I like to use.

I used the bit torrent software - Transmission - works great - I could not live without it.

At the moment I'm looking at getting a new music player, how to get my Ipod up and running, also how to get Skype to recognize the webcam/mic that I have so I can talk to my family over in the U.S.  

There is plenty of information out there for me to reference and get those things going.

As a whole, I am very satisfied with how this OS is working. The adventure has begun.

Peace :)

---

