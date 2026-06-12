---
title: "Problems with Secure Boot and NVRAM"
date: 2024-08-02
forum: New to Ubuntu
---

### Post by theinquisitor on 2024-08-02
For the last couple days I have been trying to install Linux onto an ASUS X555QA laptop. I first tried Debian, as I have installed Debian on desktops before and it worked just fine. It did work fine on my laptop, but I was having trouble getting my wifi card to work, so I decided to try installing linux mint. I probably should have just booted from a live usb, but I guess I didn't realize what could go wrong. Linux Mint fully installed and rebooted. Once the ASUS logo for my laptop flashed onto the screen, the following text appeared in the top left hand corner:

```

Could not create MokListRT: Volume Full
Could not create MokListXRT: Volume Full
Could not create SbatLevel1RT: Volume Full
Could not create MokListTrustedRT: Volume Full
Something has gone seriously wrong: import_mok_state() failed: Volume Full

```

After this point my first instinct was to use balena etcher to create a new bootable usb, this time with the latest LTS version of Ubuntu, and to try live booting from this. Again I got the same error message as soon as I tried this. Following this I ended up doing research, I have come to understand that this is a problem with Secure Boot, specifically NVRAM entries. Because of this I first tried to disable secure boot in my bios. This changed absolutely nothing. Something that I thought was interesting to note was when I looked at the boot options in the bios I noticed that the boot option for the Debian Grub boot loader was still available even after a fresh install of Linux Mint.

At this point, worrying that I now may not be able to install any operating system, I tried to install Windows, which thankfully worked successfully.  I also found a couple of Reddit posts talking of this problem specifically occuring with ASUS laptops. The fix was to apparently to reset all of the secure boot keys to factory default in BIOS. So I did this, and then I tried to again boot into a Live USB of Ubuntu. This thankfully worked. I installed Ubuntu, however upon reboot I encountered the exact same message. So I reset the secure boot keys, and successfully booted into Ubuntu. 

My problem now is that in order to boot into Ubuntu, I have to reset the keys every single time I turn on my laptop. At this point I'm honestly just going to switch back to Windows if I cant fix this, as this feels like exceptionally bad luck, and I'm at my wits end with it. Any ideas as how I might be able to get Ubuntu to boot normally? Also how does this problem even happen? Could somebody explain the technical side of this problem to me?

As a side note, what suggestions would you have for a laptop model to install Linux on? I want to try installing Linux on a laptop for personal use again in the future if this laptop doesn't work.

---

### Post by currentshaft on 2024-08-02
Off

---

### Post by theinquisitor on 2024-08-02
Yes I disabled it in my bios. It did not change anything.

---

### Post by currentshaft on 2024-08-02
.

---

### Post by theinquisitor on 2024-08-02
I just tried using the CSM option in my motherboards bios, and it seems to have fixed this issue. However is it safe to continually use a computer without secure boot? I'm considering on trying to update the bios to see if I can get secure boot to work.

---

### Post by currentshaft on 2024-08-02
.

---

### Post by theinquisitor on 2024-08-03
Well thank you for the help, at the very least now I can boot into Ubuntu normally. I will keep troubleshooting to see if I can get secure boot to work anyways just to see if I can.

---

