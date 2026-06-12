---
title: "Manual Install"
date: 2012-02-25
forum: New to Ubuntu
---

### Post by pctechtwe on 2012-02-25
Is it possible to install any version of UBUNTU as an upgrade without booting from an UBUNTU DVD or USB stick?

---

### Post by parkerskouson on 2012-02-25
as an update you can only install the next official release. you wont be able to install 12.04 untill it actually comes out

---

### Post by WasMeHere on 2012-02-25
> **parkerskouson said:**
> as an update you can only install the next official release. you wont be able to install 12.04 untill it actually comes out

+1
What do you have now, and what do you want?

---

### Post by parkerskouson on 2012-02-25
> **Olle Wiklund said:**
> +1
What do you have now, and what do you want?

exactly

---

### Post by Jake5 on 2012-02-25
I think your gonna have to boot from disk.

---

### Post by pctechtwe on 2012-02-25
> **Olle Wiklund said:**
> +1
What do you have now, and what do you want?
I have an older desktop, with corrupted windows xp, and problems booting from a DVD or USB drive.  It may boot from its original CD drive. I just want to get ubuntu loaded so that I can access the internet and try to resolve any remainig driver issues.+-

---

### Post by WasMeHere on 2012-02-25
> **pctechtwe said:**
> I have an older desktop, with corrupted windows xp, and problems booting from a DVD or USB drive.  It may boot from its original CD drive. I just want to get ubuntu loaded so that I can access the internet and try to resolve any remainig driver issues.+-

No worries if you can boot your computer from the original CD drive :-)

The normal way to install Ubuntu is to boot from a CD or USB drive and either run a live session to test and later install, or to install 'directly'. But even then, you boot from a CD or USB drive. On very old computers you might need other alternatives: boot from floppy or to take out the hard disk drive and transfer (install) the system when it is attached to another computer.

How old is it and what specs: cpu, ram, graphics? Without knowing I suggest you download the Lubuntu iso file and burn an install CD. Try if you can run a live session from the CD to test the look and feel of Lubuntu! And after that post back and/or try to install Lubuntu!

Good luck :-)

---

### Post by pctechtwe on 2012-02-25
> **Olle Wiklund said:**
> No worries if you can boot your computer from the original CD drive :-)

The normal way to install Ubuntu is to boot from a CD or USB drive and either run a live session to test and later install, or to install 'directly'. But even then, you boot from a CD or USB drive. On very old computers you might need other alternatives: boot from floppy or to take out the hard disk drive and transfer (install) the system when it is attached to another computer.

How old is it and what specs: cpu, ram, graphics? Without knowing I suggest you download the Lubuntu iso file and burn an install CD. Try if you can run a live session from the CD to test the look and feel of Lubuntu! And after that post back and/or try to install Lubuntu!

Good luck :-)
Thanks Ollie, I will download the Lubuntu iso now

---

### Post by pctechtwe on 2012-02-26
> **pctechtwe said:**
> Thanks Ollie, I will download the Lubuntu iso now
downloaded lubunto iso to a netbook running Vista and burned the image to a CD using an  external DVD drive.  The installation disk booted ok. I chose to install lubunto but installation stopped at some point and left me at a command prompt. Did that happen because there is a copy of windows already installed?  If so how do I get the system to finish installing lubuntu over the existing XP, or possiby set up dual booting?

---

### Post by WasMeHere on 2012-02-26
> **pctechtwe said:**
> downloaded lubunto iso to a netbook running Vista and burned the image to a CD using an  external DVD drive.  The installation disk booted ok. I chose to install lubunto but installation stopped at some point and left me at a command prompt. Did that happen because there is a copy of windows already installed?  If so how do I get the system to finish installing lubuntu over the existing XP, or possiby set up dual booting?
First try to test Lubuntu live (do not install at once, instead run it to get a feeling how it works).

- Does your input devices work (keyboard, mouse, touchpad ...)
- Is the graphics working reasonably well?
- Is it at least as fast as Windows?
- Can you connect to internet?
- Can you play a video clip (audio and video)?

If this looks good enough, you are ready to install. It is possible to install in many ways, and I suggest either dual boot with Windows or using the whole drive.

To prepare for that please start a terminal window with
***ctrl + alt + t***
Run the following command
```
sudo fdisk -lu
``` and ```
df
```
and post its output within CODE tags, mark it and press the # icon at the top of this editing window.

This will show the layout of your internal HDD, and make it easier to discuss how to install Lubuntu.

Also you can look at the following threads
[[COLOR="RoyalBlue"]_https://help.ubuntu.com/community/BootOptions_[/COLOR]]("https://help.ubuntu.com/community/BootOptions")
[[COLOR="RoyalBlue"]_Lubuntu One Stop Thread_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

---

### Post by rbowen1 on 2012-02-26
> The installation disk booted ok. I chose to install lubunto but installation stopped at some point and left me at a command prompt. Did that happen because there is a copy of windows already installed? If so how do I get the system to finish installing lubuntu over the existing XP, or possiby set up dual booting?

I have never installed lubunto but regular Ubuntu will inform you that XP was already installed and ask if you wanted to dual boot or blow away existing partitions.  Install a clean installation Ubuntu.  
  
Did you ever get the option to partition the disk?  Need to know what was going on before it stopped.

---

### Post by WasMeHere on 2012-02-26
> **rbowen1 said:**
> I have never installed lubunto but regular Ubuntu will inform you that XP was already installed and ask if you wanted to dual boot or blow away existing partitions.  Install a clean installation Ubuntu.  
  
Did you ever get the option to partition the disk?  Need to know what was going on before it stopped.
@rbowen1: Lubuntu also asks these questions. The main differences are the desktop environment and the set of installed application programs. Otherwise it is (almost the same) Ubuntu under the hood.

---

### Post by WasMeHere on 2012-02-26
If you have problems to install Lubuntu, an alternative that also often works is to install ***Linux Mint 11 or 9***. It is based on Ubuntu (uses the same repositories for the software) and it is often easy to get started and running... and yes, I know it is not the latest version, but I have good experience with those versions of Linux Mint.

For me it is not important which distro, flavour or version of linux you use. There are small differences, and it is worth testing which one is best for you and your computer. The hardware drivers are different, and it can make a big difference in performance when you find the best one for your hardware.

---

### Post by pctechtwe on 2012-02-26
> **Olle Wiklund said:**
> @rbowen1: Lubuntu also asks these questions. The main differences are the desktop environment and the set of installed application programs. Otherwise it is (almost the same) Ubuntu under the hood.
I never got an opportunity  to re-partition the hdd.  There appears to be some problem with my installation CD.

---

### Post by rbowen1 on 2012-02-26
Could be a comparability issue between your burner and the computers CD drive that you are trying to boot up.   Try booting the CD in another computer (maybe the one that you burned the CD).     Follow what Olle Wiklund advised and just select to try the live CD.  Do not install the OS.

---

### Post by pctechtwe on 2012-02-26
> **pctechtwe said:**
> I never got an opportunity  to re-partition the hdd.  There appears to be some problem with my installation CD.
Thanks again for all the help.   

I tried running a test session and ended up at the command line again. I really think there is some problem with the boot CD.   I may have to take your suggestions to install something other than lubuntu (***Linux Mint 11 or 9***), but I will try burning a new lubuntu Installation CD first.

---

### Post by pctechtwe on 2012-02-26
> **rbowen1 said:**
> Could be a comparability issue between your burner and the computers CD drive that you are trying to boot up.   Try booting the CD in another computer (maybe the one that you burned the CD).     Follow what Olle Wiklund advised and just select to try the live CD.  Do not install the OS.

I agree.   In the past I have had many problems sharing CDs created on DVD drives with systems that only have older CD drives.

---

### Post by WasMeHere on 2012-02-27
> **pctechtwe said:**
> Thanks again for all the help.   

I tried running a test session and ended up at the command line again. I really think there is some problem with the boot CD.   I may have to take your suggestions to install something other than lubuntu (***Linux Mint 11 or 9***), but I will try burning a new lubuntu Installation CD first.

1. Maybe you should set your burning session to work slowly (as slowly as possible) to increase the chance to success.

2. And, yes, it is a good idea to test Linux Mint if that won't help.

But there are a couple of other things, that might be worthwhile too:

3. Get the ***md5sum*** checksum file for each of your downloaded iso files and run a checksum test or download via torrent, that should do such checksum tests automatically!
[[COLOR="RoyalBlue"]_http://ubuntuforums.org/showthread.php?t=1864357_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1864357")

4. Try a live session in another computer according to
> **rbowen1 said:**
> Could be a comparability issue between your burner and the computers CD drive that you are trying to boot up.   Try booting the CD in another computer (maybe the one that you burned the CD).     Follow what Olle Wiklund advised and just select to try the live CD.  Do not install the OS.

---

### Post by mastablasta on 2012-02-27
Lubuntu has a bug that crashes installer if there is not enough ram.

---

### Post by WasMeHere on 2012-02-27
> **mastablasta said:**
> Lubuntu has a bug that crashes installer if there is not enough ram.

Is the bug only in Lubuntu? So it might be a good idea to try Xubuntu instead for an old computer? Or Ubuntu 10.04 LTS?

---

