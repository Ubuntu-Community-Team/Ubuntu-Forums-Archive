---
title: "Trouble installing Lubuntu"
date: 2013-09-15
forum: New to Ubuntu
---

### Post by bradley3 on 2013-09-15
Hi, I am new to this forum, and I am sorry if I posted this in the wrong thread. I am trying to create a dual boot. Right now I have Windows XP Pro, and I want to install lubuntu alongside XP, because its been running slowly. However, when I try to boot into the live CD, it just stays on the boot screen. Even after an hour, its not done booting. After 5 minutes, the CD stops spinning. What should I do?

---

### Post by oldos2er on 2013-09-15
Did you check the integrity of the CD?

What are your hardware specs?

---

### Post by bradley3 on 2013-09-15
Yes I did. In fact, the live CD boots fine on my laptop, but it has a graphical glitch on an old spare computer. The desktop I am trying to install it on is a Dell Optiplex 210L. It has 512 MB RAM and a 200 GB hard drive.

---

### Post by whitesmith on 2013-09-15
If "optical glitch" means "It booted but the screen didn't look quite right" then the CD essentially works on 2 computers. Since software is deterministic I'd say there is some hardware on the Optiplex it doesn't like. This is exactly why I hate proprietary anything and everything...hardware or software. If every damn thing were open we wouldn't have aggravations like this.

---

### Post by bradley3 on 2013-09-15
I tried other distros and it loaded fine. I also recall that I tried booting lubuntu from a flash drive, and that worked.

---

### Post by bradley3 on 2013-09-15
The computer with the optical glitch was a Compaq Presario 6000

---

### Post by whitesmith on 2013-09-15
Afraid this one is above my pay grade. Maybe request this thread be moved to hardware. I think that's the core of the apple.

---

### Post by sudodus on 2013-09-15
Please describe

1. your computer: brand name, model, cpu, (we know 512 MB ram) and graphics chip/card

2. the OS: which version of Lubuntu? 12.04, 12.10, 13.04; 32-bit or 64-bit.

3. If you have problems installing from the desktop iso, try the [alternate iso]("https://help.ubuntu.com/community/Lubuntu/Alternate_ISO"). It works better when less than 700 MB RAM.

---

### Post by bradley3 on 2013-09-15
The CPU is an intel Pentium III. Im not sure what the graphics card is at the moment, but I can check. When I tried to boot it, it was a few months ago. I used Lubuntu 12.04. When I used the flash drive, it did run extremely well, perhaps better than Windows 7. So, should I try to use the flash drive to boot once I find it again? Should I put the newest lubuntu version on it first?

I do have some experience with computers, and I do know how they work. This is a computer that was given to me because I fixed a friend's kid's computer. When I got it, it ran well, but once I installed antivirus, it slowed to a crawl. I know that malware isnt a problem with linux, plus lubuntu is not as bloated as windows, so I decided to try it out.

---

### Post by whitesmith on 2013-09-15
Hat tip to **sudous** for the alternate iso idea. By all means use the flash drive to boot. It looks like you discovered that the only purpose of AV apps is to slow down computers. Malware is usually not a problem on *nix unless someone does something really stupid, like using Wine as su.

---

### Post by bradley3 on 2013-09-15
So I should replace 12.04 with 13.04 before installing it, correct? And will it automatically create a dual boot? Will my data be intact?

---

### Post by sudodus on 2013-09-15
No, do not jump to conclusions!

It is worth testing various versions before installing anything. Such an old computer might have problems running the newest versions of Lubuntu because some drivers for old hardware have been dropped. You know that 12.04 works. You can run it again to have it as a reference (a fresh feeling or measurement, whatever suits you).

Then you can try 13.04 or even try new 13.10, that is in the pipe-line at the beta testing stage now. Try them live, but wait with the installation. You need desktop isos to test live, and you might need an alternate iso for installation, because of the low RAM.

If only 12.04 works well, you might be better off with some re-spin, for example LXLE, because standard Lubuntu 12.04 has end of life next month, while LXLE promises long time support until April 2017.

If you do not need dual boot (can skip Windows), the [One Button Installer ]("http://ubuntuforums.org/showthread.php?t=2172971")is an alternative (but I read in your first post, that you intend to keep Windows).

Anyway, partitioning and installation is risky, so ***backup*** Windows before doing anything else, unless you can and want to re-install it anyway.

---

### Post by bradley3 on 2013-09-15
Would defragmenting make it a bit safer? And I could always try the new version before installing it right?

---

### Post by sudodus on 2013-09-15
Some people think defragmenting is good, but some people say that it is not necessary, it will be done by the shrinking process anyway (when you shrink the NTFS partition to create space for Lubuntu).

And yes, you can always try the new version before installing (try *live*, booted from the CD/DVD/USB drive).

---

### Post by bradley3 on 2013-09-15
So, I will defragment, back up my files, boot the live USB, test it, and set up the dual boot. Just to be sure, does it set the dual boot as the default option?

---

### Post by vasa1 on 2013-09-15
> **sudodus said:**
> Some people think defragmenting is good, **but some people say that it is not necessary**, it will be done by the shrinking process anyway (when you shrink the NTFS partition to create space for Lubuntu).

And yes, you can always try the new version before installing (try *live*, booted from the CD/DVD/USB drive).
My feeling is that it is better to defrag first and then adjust the partitions.

Also, if OP gives you the information from **sudo fdisk -l** and **sudo parted -l** it may help with the dual boot process.

---

### Post by sudodus on 2013-09-15
> **bradley3 said:**
> So, I will defragment, back up my files, boot the live USB, test it, and set up the dual boot. Just to be sure, does it set the dual boot as the default option?

I suggest that you do the partitioning separately with ***gparted*** and before you start the installer. Do both booted from a CD/DVD/USB drive.

This is better than to use the default option. Use 'Something else' or 'Manual partitioning' at the partitioning screen during installation..

---

