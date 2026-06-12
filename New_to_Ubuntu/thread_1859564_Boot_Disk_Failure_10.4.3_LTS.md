---
title: "Boot Disk Failure 10.4.3 LTS"
date: 2011-10-14
forum: New to Ubuntu
---

### Post by schmitta on 2011-10-14
Hi -- I have the 10.4.3 CD that loads fine in LIVE mode and UBUNTU comes up ok. I clicked install on a brand new 160mb IDE drive (only HD in computer) and after the install I get BOOT DISK FAILURE. My BIOS is set up for CDROM,C,A (would like CDROM,A,C but can't get it). HD is in C SELECT mode. From an other post I redid the install and click ADVANCED on the last page and Boot sector was checked as well as the SDA (I am a newbie to LINUX) was set to the hard drive (the only partition that appeared on the list). So it looks like it should write the boot sector correctly. any ideas? Thanks. Alvin.....

---

### Post by sadaruwan12 on 2011-10-14
First of all welcome to the forum.

It looks like your bios is not switching to the hard drive. And from the details it seems to be an old BIOS any way do you have a option to select the hard disk as the first boot device and CDROM as the second.

---

### Post by schmitta on 2011-10-18
I reran the install and on the last page selected ADVANCED . Then I had two choices dev/sda and dev/sda1. sda went to the hard disk and sda1 went to ubuntu. I selected dev/sda1 to ubuntu and when it finished the install and a reset of the computer was performed the messages were ERROR: OUT OF DISK and grub rescue > . So this time I must have loaded ubuntu from the hard disk. In the ubuntu install I used the defaults and unbuntu took 158 MB of the 160 MB hard disk. What should I do next? Thank you. ALvin....

---

### Post by amjjawad on 2011-10-18
Hello and Welcome :)

1- Please check MD5SUM for the ISO file that you have downloaded.
This is howto:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

2- Howto create a Live-CD? this is howto: [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
Make sure to burn as slow as possible. I suggest 8x as burning speed.

3- Turn your machine on. Go to BIOS. Make sure your CD-Drive is the first device to boot from. Make sure your HDD is the second device to boot from. Save and Exit.

[IMG]http://ubuntuforums.org/picture.php?albumid=2145&pictureid=7126[/IMG]

4- If Ubuntu is the ONLY OS that will be installed on your HDD, then you have two options. Either to let the installer handle the whole thing and you sit back and watch OR you do that manually.

Please decide what you want to choose so I can carry on and explain further.

---

### Post by schmitta on 2011-10-22
To end the discussion on my Linux UBUNTU problems I was getting OUT OF DISK message. I found that the 4 $ computer's BIOS  stated that the hard disk was 8.4+ gig ( an old computer). My disk is 160 GB. So during the install (remember i do not know what I am doing) I set up the root partition ( / EX4) to 7 gig and the swap area to 1 gig. After I did that it would not load but I found in a kindle book I have on UBUNTU the command >sudo grub-install sda< which I modified to sda1. I ran the CD live version of UBUNTU and entered that command. and restarted the system. It coughed a few times but finally loaded UBUNTU from hard disk. I am writing this from Firefox under the UBUNTU I loaded. Also, I purchased a wireless card for the 4$ computer but was worried that the CDROM that came with the device only worked under windows. But UBUNTU recognized the wireless card and all I had to do was to supply the WPA code to get into my wireless router. SO I am totally amazed by Ubuntu. The EAGLE PCB program I use for may business will run under linux, The CCS C  compiler for my PIC microcomputers also works under linux (but not the IDE) so with the supplied Open Office supplied with UBUNTU I really do not need windows.

---

### Post by mörgæs on 2011-10-22
Good to hear! Please mark the thread 'solved' using 'thread tools'.

---

### Post by amjjawad on 2011-10-23
> **schmitta said:**
> I really do not need windows.
I just love that :D

Good job and glad to know that.

[IMG]http://ubuntuforums.org/picture.php?albumid=2161&pictureid=7263[/IMG]

---

