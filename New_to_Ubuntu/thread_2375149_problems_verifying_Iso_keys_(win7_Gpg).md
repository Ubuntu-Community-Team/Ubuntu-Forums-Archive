---
title: "problems verifying Iso keys (win7 Gpg)"
date: 2017-10-22
forum: New to Ubuntu
---

### Post by nabla- on 2017-10-22
Hello all,

Am trying to create a bootable ubuntu USB drive, following the instructions on the Ubuntu website.
I Downloaded version 16.04.3, and SHA256SUMS.gpg and SHA256SUMS (I saved this as a text file - not sure this is correct?), and put all three files in the same directory.

I'm working on a windows 7 machine and installed gpg a while ago, as well as Rufus to create bootable USB,as recommended on Ubuntu website.

Opening cmd as administrator I can verify I have gpg installed:

```

C:\Users>gpg --version
gpg (GnuPG) 2.2.1
libgcrypt 1.8.1
Copyright (C) 2017 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <https://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.


Home: C:/Users/user1/AppData/Roaming/gnupg
Supported algorithms:
Pubkey: RSA, ELG, DSA, ECDH, ECDSA, EDDSA
Cipher: IDEA, 3DES, CAST5, BLOWFISH, AES, AES192, AES256, TWOFISH,
        CAMELLIA128, CAMELLIA192, CAMELLIA256
Hash: SHA1, RIPEMD160, SHA256, SHA384, SHA512, SHA224
Compression: Uncompressed, ZIP, ZLIB, BZIP2

```

However, when trying the instructions on the Ubuntu Guide [HERE]("https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu?_ga=2.180764066.401873031.1508685086-1460732758.1507827466#2") I get error messages:


```

C:\Ubuntu>ls
SHA256SUMS.gpg  SHA256SUMS.txt  ubuntu-16.04.3-desktop-i386.iso


C:\Ubuntu>gpg --keyserver hkp://keyserver.ubuntu.com --recv-keys "8439 38DF 228D
 22F7 B374 2BC0 D94A A3F0 EFE2 1092" "C598 6B4F 1257 FFA8 6632 CBA7 4618 1433 FB
B7 5451"
key 46181433FBB75451:
72 signatures not checked due to missing keys
gpg: waiting for file 'C:/Users/user1/AppData/Roaming/gnupg/pubring.kbx' to becom
e accessible ...
gpg: waiting for file 'C:/Users/user1/AppData/Roaming/gnupg/pubring.kbx' to becom
e accessible ...
gpg: waiting for file 'C:/Users/user1/AppData/Roaming/gnupg/pubring.kbx' to becom
e accessible ...
^C

```

I keep getting the 'waiting for file to become accessible' message indefinitely until I Ctrl+C to exit. I am adminstrator on the machine, and opened the cmd as admin, but for some reason it can't access the file 'pubring.kbx' file.

I searched and found [THIS]("https://help.ubuntu.com/community/VerifyIsoHowto#Obtain_the_public_key_from_the_Ubuntu_key_server") guide and followed instructions, but it also gives me the same error messages using this code:

```

C:\Ubuntu>ls
SHA256SUMS.gpg  SHA256SUMS.txt  ubuntu-16.04.3-desktop-i386.iso


C:\Ubuntu>gpg --verify SHA256SUMS.gpg SHA256SUMS.txt
gpg: Signature made 08/03/17 14:56:51 GMT Daylight Time
gpg:                using DSA key 46181433FBB75451
gpg: Can't check signature: No public key
gpg: Signature made 08/03/17 14:56:51 GMT Daylight Time
gpg:                using RSA key D94AA3F0EFE21092
gpg: Can't check signature: No public key


C:\Ubuntu>gpg --keyserver hkp://keyserver.ubuntu.com --recv-keys 46181433FBB7545
1 D94AA3F0EFE21092
key D94AA3F0EFE21092:
25 signatures not checked due to missing keys
gpg: waiting for file 'C:/Users/user1/AppData/Roaming/gnupg/pubring.kbx' to becom
e accessible ...
gpg: waiting for file 'C:/Users/user1/AppData/Roaming/gnupg/pubring.kbx' to becom
e accessible ...
gpg: waiting for file 'C:/Users/user1/AppData/Roaming/gnupg/pubring.kbx' to becom
e accessible ...
gpg: waiting for file 'C:/Users/user1/AppData/Roaming/gnupg/pubring.kbx' to becom
e accessible ...
gpg: waiting for file 'C:/Users/user1/AppData/Roaming/gnupg/pubring.kbx' to becom
e accessible ...
gpg: waiting for file 'C:/Users/user1/AppData/Roaming/gnupg/pubring.kbx' to becom
e accessible ...
^C

```

I set the gnupg folder so that it wasn't read-only in windows explorer, in case that might fix it but it didn't.

Done some searching but can't find any solution, or anyone with similar problem.

---

### Post by tea for one on 2017-10-22
An alternative solution is to check the md5sum of an Ubuntu ISO.

Here is a link for Windows software to verify md5sums.

[http://www.nullriver.com/products](http://www.nullriver.com/products) (You need the fourth entry on the list).

I have used this software in the past and it has proved to be reliable.

Best wishes

---

### Post by nabla- on 2017-10-22
Thanks for the reply, I've managed to confirm hash using CertUtil, but was hoping to also verify the gpg key (as a learning exercise more than anything) - from what I understand the gpg key can confirm the file is signed by a trusted user (as long as public key from key server is trusted), while the hash just confirms that the file was not changed during download? 

I have installed gpg4win and messing round with kleopatra and the cmd line scripts, I'm not having a great deal of success.

---

### Post by tea for one on 2017-10-22
> **nabla- said:**
> Thanks for the reply, I've managed to confirm hash using CertUtil, but was hoping to also verify the gpg key (as a learning exercise more than anything) - from what I understand the gpg key can confirm the file is signed by a trusted user (as long as public key from key server is trusted), while the hash just confirms that the file was not changed during download? 

I have installed gpg4win and messing round with kleopatra and the cmd line scripts, I'm not having a great deal of success.

I see that you have confirmed that the hash is OK, however we do not know the site where you downloaded the Ubuntu ISO.

Was it this site? [https://www.ubuntu.com/](https://www.ubuntu.com/)

If it was direct from the Ubuntu homepage then I'm sure that you can go to the next stage and burn your USB.

Are you reasonably familiar with making bootable USB devices?

---

### Post by nabla- on 2017-10-23
Hi thanks, yes it was the official Ubuntu site, and I'm happy with certificates etc now.

I made a live CD once, and I used to have Ubuntu dual booted on my laptop years ago, but have forgotten most of what I learned. This is the first time I've tried it on a USB.

Have managed to write to USB with Rufus (suggested on Ubuntu website) and fiddled with my BIOS settings to get it to boot, however when it boots I get the options try or install. 
When I click try Ubuntu desktop loads up, but display resolution is all messed up and I can't see the taskbar. I downloaded drivers for my nVidia graphics card as a .run file, put it in the home directory, and tried the following from a terminal:

```

sudo chmod +x file.run

```

This seems to work without any error messages then I try:

```

./file.run

```

It starts unpacking and running but then I get sudo password error so I try instead:

```

sudo ./file.run

```

...as suggested on every article I can find, but it gives me an error saying sudo command not found - do I need to install sudo, or set up some kind of permissions? (why does sudo work with first command but not the second)?

I'm wondering if I need to 'install' Ubuntu to the USB stick (if I can) rather than have the OS just running using the 'try' option. 
It's an 8GB stick, and ideally I want have it so that I can plug in my USB, boot ubuntu from it and be able to install a few small programs on it, rather than installing it to my hard-drive. I'd also maybe like to have a couple of GB free for data on the stick - so I'm not sure if I'd need some kind of partition manager to set this all up?

---

### Post by tea for one on 2017-10-24
> **nabla- said:**
> 
I'm wondering if I need to 'install' Ubuntu to the USB stick (if I can) rather than have the OS just running using the 'try' option. 
It's an 8GB stick, and ideally I want have it so that I can plug in my USB, boot ubuntu from it and be able to install a few small programs on it, rather than installing it to my hard-drive. I'd also maybe like to have a couple of GB free for data on the stick - so I'm not sure if I'd need some kind of partition manager to set this all up?

I see what you want to do and that's a good idea to experiment with Ubuntu.

You will need two USB sticks - one you have already prepared as "Try and Install" and your 8GB target device.

The partition manager is included as part of the installation process, but I do not think that you need to have two partitions on a 8GB device.

Ubuntu will run fine on a 8GB stick but there will only be a little room left for data/programs.

If you can, **unplug** your internal hard drive before installing to avoid a disaster.
Pay particular attention to drive names - i.e. sd**a**, sd**b**, sd**c**, etc.
Install Grub bootloader to the top level of your USB stick.

I do not have Nvidia graphics on my PC, however, as I understand the process, you install the OS and then install the Nvidia drivers.

Here is a link:-

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

Best wishes

---

### Post by nabla- on 2017-10-24
Thanks, 

I didn't have a 2nd USB, so I reformatted the USB, created a live CD, and used the following guide to install on the USB from the live CD:

[http://ubuntuhandbook.org/index.php/2014/11/install-real-ubuntu-os-usb-drive/](http://ubuntuhandbook.org/index.php/2014/11/install-real-ubuntu-os-usb-drive/)

The installation completed OK, but now my BIOS doesn't seem to recognise the USB as bootable like it did before. (With the original USB, I managed to get it to boot by checking a box in Rufus that said something like 'make compatible with older BIOS versions' and rewriting the ISO - it was then recognised as a HDD rather than any of the USB-XXX device options.)

I can't figure out how to install the grub bootloader to the USB - I don't think there was an option for this on the installation wizard when I set up the partitions. I also didn't see any checkbox for 'make bootable' or something like that.

It doesn't explain very well in that guide how to actually make bootable (step 6) but it does mention that it's important to do so. Not really very helpful, I think it assumes some prior knowledge.

I didn't 'launch gparted from unity dash' as I didn't know how / see any option, but I did delete all partitions on USB using Windows before I started, so assume I don't need that step?

---

### Post by tea for one on 2017-10-24
> **nabla- said:**
> I can't figure out how to install the grub bootloader to the USB - I don't think there was an option for this on the installation wizard when I set up the partitions. I also didn't see any checkbox for 'make bootable' or something like that.

From the Ubuntu Handbook link you mentioned, please refer to item 6 (where it says [COLOR="#FF0000"]IMPORTANT[/COLOR]) for installing Grub on your device.

You do not need to make an installed system "bootable", you have to choose which disk to boot from your BIOS.

---

### Post by nabla- on 2017-10-24
Hi, I already did that step but it still won't boot. My screen was exactly the same as the one shown in step 6 with my USB selected in that dropdow box. Except mine was sda not sdc.... But it was definitely the USB drive as it said Kingston just like in the screen shot.
The guide seems to imply it should work for sda or sdc... I don't know what the difference is?

---

### Post by tea for one on 2017-10-24
> **nabla- said:**
> Hi, I already did that step but it still won't boot. My screen was exactly the same as the one shown in step 6 with my USB selected in that dropdow box. Except mine was sda not sdc.... But it was definitely the USB drive as it said Kingston just like in the screen shot.
The guide seems to imply it should work for sda or sdc... I don't know what the difference is?

Hello again

It looks like we are getting close to a result.

Did you unplug your internal hard drive when you installed to the USB stick? 

Kingston is a pretty well known brand for external USB devices.

If you **only** had your USB stick inserted when you installed Ubuntu, then sda would be correct.

Is it possible to post a picture of your BIOS screen (taken with a camera or mobile phone) with only your USB device attached?

---

### Post by nabla- on 2017-10-24
Hi, thanks for all of your help on this. I reformatted the USB stick and started installation from scratch. This time I only set up 2 partitions (ext4 15GB, and swap space 1GB) instead of 3 like in the guide. It now boots up fine as expected (although it's quite slow but I guess this is due to slow speed of USB vs SATA... I think mine are 2.0 as well XD ).

I still have the problem that the screen is not displayed properly on my wide-screen monitor. Display settings don't seem to help, and trying the sudo ./ command above on the nvidia driver, it now runs the file this time but it gives me and error saying that I'm running X server and need to exit.

Basically the display ratio is too small so I have a thick black vertical bar at each side of the monitor, and the sidebar and task bar are behind the black bars... But I can move cursor behind them and see the button options from the tooltip on mouse over. I'm putting it down to needing the correct graphics drivers installed.

---

### Post by tea for one on 2017-10-25
Splendid - I'm pleased that you have persevered and almost obtained the outcome you want.

OS installation on an external USB device is an interesting learning curve.

Your display problem sounds like graphic card drivers and I think that you should start a separate thread in General Help to attract the attention of Nvidia users.

Please mark this thread as solved if you are happy with the result.

KInd regards

---

### Post by nabla- on 2017-10-26
Have discovered I can change display drivers from Xserver to Nvidia binary using ubuntu GUI in system settings, so am trying that. System still incredibly slow however and I think it's due to slow USB<-->RAM communications. I might try deleting the swap partition and some caching as I don't think it's helping the speed.

Anyway, will start other threads if I need to. Thanks again

---

