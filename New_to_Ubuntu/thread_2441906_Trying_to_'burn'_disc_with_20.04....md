---
title: "Trying to 'burn' disc with 20.04..."
date: 2020-04-27
forum: New to Ubuntu
---

### Post by Innernet on 2020-04-27
Hi.
Downloaded 20.04 .  It is in the 'downloaded' folder, shows being 2.5GB

Ran "echo "e5b72e9cfe20988991c9cd87bde43c0b691e3b67b01f76d23f8150615883ce11 *ubuntu-20.04-desktop-amd64.iso" | shasum -a 256 --check"
 to verify file health as suggested at the download site ---->  [https://ubuntu.com/download/desktop/thank-you?version=20.04&architecture=amd64](https://ubuntu.com/download/desktop/thank-you?version=20.04&architecture=amd64)

Result is :

externet@externet-Presario-CQ57-Notebook-PC:~$ echo "e5b72e9cfe20988991c9cd87bde43c0b691e3b67b01f76d23f8150615883ce11 *ubuntu-20.04-desktop-amd64.iso" | shasum -a 256 --check
shasum: ubuntu-20.04-desktop-amd64.iso: 
ubuntu-20.04-desktop-amd64.iso: FAILED open or read
shasum: WARNING: 1 listed file could not be read
externet@externet-Presario-CQ57-Notebook-PC:~$ 

What went wrong ?  How big is the .iso file supposed to be ?   Needs to be a DVD, not CD, right ?   What if Intel64 instead of AMD64 ?  They have not corrected that yet ?

Do I 'burn' the .iso or extracted files ?

---

### Post by mörgæs on 2020-04-28
For a CQ57 I suggest that you install something lighter than Ubuntu, say X/Lubuntu. It has a 64 bit processor so the AMD64 version is correct.

The 'AMD' in 'AMD64' is there for historical reasons and today it only creates confusion. An AMD64 ISO also works on Intel CPU's.

If you want to test the ISO file just run the command ```
sha256sum name_of_your_ISO_file
```

Yes, the ISO is too big for a CD. Must be DVD or USB.

---

### Post by Impavidus on 2020-04-28
**What went wrong ?**
The file is in your Downloads directory, but you ran the command in your home directory. First change to the Downloads directory: **cd Downloads** (or whatever your downloads directory is called).

**How big is the .iso file supposed to be ?**
Around 2.5GB sounds right.

**Needs to be a DVD, not CD, right ?**
Ubuntu live disk images have been too large for a cd for a long time. You can use a dvd, but it's more common nowadays to use a usb drive. Most modern computers can boot from usb. If you insist on a cd, there's still the minimal installer.

**What if Intel64 instead of AMD64 ? They have not corrected that yet ?**
AMD64 is the 64 bit instruction set invented by AMD. It's also used by 64 bit Intel processors. Yes, that name is a bit confusing now, but let's give credits to who deserves it.

**Do I 'burn' the .iso or extracted files ?**
You burn the .iso as an image to a dvd or usb drive. If you extract the files and burn those, it won't be bootable as there won't be a bootloader in the right place. Neither will it boot if you burn the .iso as a file. At least, on legacy systems. On UEFI systems there's a bit more flexibility.

---

### Post by CelticWarrior on 2020-04-28
> **Impavidus said:**
> On UEFI systems there's a bit more flexibility.

Indeed there is. Extracting the files to a FAT32 USB stick makes it bootable but only in UEFI systems. Those only need an ESP or an EFI folder inside a FAT32 partition with the proper efi files insides.

---

### Post by Innernet on 2020-04-28
Thanks, gentlemen.  Good instructions to my bad skills to discern things.

Ignored the error "shasum warning" at the terminal as have no idea how to go to the 'Downloads directory' in the terminal, and attempted 'burning' the DVD.
After four or five minutes,  Brasero apparently finished (100% done) !  prompted but then started to burn a checksum, never ending, (pictured) and not ejecting.  The optical drive did not feel like spinning.

Why does it show 100% done when there is something pending ?  It is stuck there as pictured for over 15 minutes doing nothing.  Hit cancel, and ejected the disc with a message "successfully burned"  "Want another copy ?"   
 Some developer is worse than me...

---

### Post by CelticWarrior on 2020-04-28
> **Innernet said:**
> (...) have no idea how to go to the 'Downloads directory' in the terminal   

Assuming your system is in plain English, the downloads directory is called... Downloads.
Knowing that the terminal always opens in the users' home directory and that Downloads is inside that directory, then it's as easy as ```
cd Downloads
```
If not in English change the name accordingly.

> Some developer is worse than me...
No, not really. Thinks are what they are.

---

### Post by Innernet on 2020-04-28
Thanks.
Recycled power, 20.04 DVD in,  prompts fine, nothing happens when choosing to try without installing in either safe graphics or not. Memory test ran fine.

Did the cd Downloads  earlier and showed 'command not recognized'
Yes, operating in English.

Been running Ubuntu since 05.10 and every time I upgrade; there is more and more hurdles.  The smooth wonderful operation of 07.04 has never been matched since.  The size is bigger and bigger and behavior is worse.
Still in 2020 I do not do Windows.

---

### Post by CelticWarrior on 2020-04-28
I've been using Linux since before Ubuntu.
I've never noticed any "worse behavior", all the opposite actually.

The thing is, I evolve with the times. I've burned hundreds of disks for installations in the past but not in the last 10 plus years. Even for installing on an old BIOSTAR motherboard that couldn't boot from USB I used a PLoP CD to chainload the USB installer instead of burning a full DVD and install from there. USBs are much faster in any step ("burning" and booting/installing) and are reusable thousands of times. Plastic waste is a serious environmental problem.

---

### Post by mörgæs on 2020-04-29
If Brasero is misbehaving you could try Xfburn.
Always burn with the slowest speed possible.

---

### Post by CelticWarrior on 2020-04-29
> **mörgæs said:**
> If Brasero is misbehaving you could try Xfburn.

Brasero isn't misbehaving. It's doing what it has been told to do. The option to do chesum is enabled by default, it can be disabled if the user doesn't want to wait the long time it takes.

> Always burn with the slowest speed possible.
This is an old myth. Depending on the hardware and media there could be higher failure rates with slower speeds.

---

### Post by mörgæs on 2020-04-29
The myth is young enough for me. I have never had a bad CD or DVD burn with slow speed (in the good old days when that was the way to install).

---

### Post by ActionParsnip on 2020-05-01
Always burn as slowly as possible

---

