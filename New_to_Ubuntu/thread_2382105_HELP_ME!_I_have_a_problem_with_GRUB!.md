---
title: "HELP ME! I have a problem with GRUB!"
date: 2018-01-09
forum: New to Ubuntu
---

### Post by rum0000000 on 2018-01-09
Hi everyone!
At first, i want to say that I am not good at English and i'll try my best to use it !!
This is my problem:
I have aldready had window 8.1, and i want to dual boot with ubuntu 16.04.
Then i made a boot usb, installed ubuntu and successed.
I restarted my laptop but**i didnt see GRUB boot, my laptop just boots directly to window.**
Then** i deleted ubuntu and re-installed, but the same thing happened.**
I tried to read about this error, and found that i could **use live-ubuntu and install boot-repair to repair the problem**
I made this step, and i required me to disable "secure boot", i agreed, boot-repair finished**, and nothing happened.**
**[https://paste.ubuntu.com/26351717/](https://paste.ubuntu.com/26351717/) Here is the result.**
[https://drive.google.com/open?id=1KTNwqe5Kw7Yh9p0TwiT5mSgQDUi8scYH](https://drive.google.com/open?id=1KTNwqe5Kw7Yh9p0TwiT5mSgQDUi8scYH) Here is the video about my BIOS and my boot manager.
Please help me! Thanks for reading my thread!
Edit1: I fixed it, i turned off secure-boot in BIOS and now i could boot into ubuntu, but i still didnt see Grub-boot, and i dont know whether my decision on turning off secure is harmful to my laptop, could you explain for me about it? Thanks for your reading.

---

### Post by yancek on 2018-01-09
What happens when you select either of the Ubuntu entries in the BIOS?

---

### Post by oldfred on 2018-01-09
Boot-Repair is suggesting to turn UEFI Secure Boot off.

Also can you boot both Ubuntu & Windows from UEFI boot menu?
Also does a hard drive boot entry boot into Ubuntu? Boot-Repair copied shimx64.efi to /EFI/Boot/bootx64.efi which was a copy of Windows .efi boot file. And that entry is a fallback or hard drive boot entry.

With HP, Boot-Repair adds a lot of entries to grub menu, you may have to scroll down to see Windows entry. It adds all the HP .efi files.
And most of those entries do not need to be in grub menu and you can houseclean them out.
       # Edit 25_custom entries created by Boot-Repair:
sudo cp -a /etc/grub.d/25_custom /etc/grub.d/bkp25_custom
# turn off execute bit or it will run backup also
sudo chmod a-x /etc/grub.d/bkp25_custom
sudo nano /etc/grub.d/25_custom
# Then do:
sudo update-grub

---

