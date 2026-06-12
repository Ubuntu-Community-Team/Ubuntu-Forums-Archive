---
title: "Problems with Dual-Boot"
date: 2012-02-03
forum: New to Ubuntu
---

### Post by jorpoveda on 2012-02-03
Hello, I have my computer with a dual boot for a Windows XP and Ubuntu 10.04 LTS partitions. Recently I made an update and now whenever I start Ubuntu again it does not start it stays on a black screen and it never starts.

I have noted that in the GRUB menu there are 2 Ubuntu, one is the 2.6.32.38 and the 2.6.32.38.

How can I solve this and why does Ubuntu does not starts?

Thank you.

---

### Post by Mahkoe on 2012-02-04
Okay. In the grub menu there should be two different Ubuntu versions listed. If not, there will be a line that says "Previous Linux Versions" (which is what I see). Boot into the working older version and run this command;
```
sudo update-grub2
```
That worked for me last time this happened, if it doesn't, try this and let me know of the results.
Identify the partition name of your Ubuntu installation. Go into System -> Disk Utility (or GParted) and write down the /dev/sxy notation for your partition. You will now need to identify the grub partition notation for your Ubuntu partition. I learned how from this link: [http://www.gnu.org/software/grub/manual/html_node/Naming-convention.html](http://www.gnu.org/software/grub/manual/html_node/Naming-convention.html). Then, in the grub menu hit "c" to go into a command line. You may want to write these commands down so you don't forget:

/dev/sxy is to be replaced with your ubuntu partition name and (hd0,msdosX) with the grub partition
```

linux (hd0,msdosX)/vmlinuz root=/dev/sxy quiet splash
initrd (hd0,msdosX)/initrd.img
boot

```
If you didn't understand a sweet thing, try this site:
[http://aaron-kelley.net/blog/2011/04/grub-prompt-after-upgrade-to-ubuntu-11-04/](http://aaron-kelley.net/blog/2011/04/grub-prompt-after-upgrade-to-ubuntu-11-04/)
Best of luck

---

### Post by jorpoveda on 2012-02-04
Error was not solved, I still cant boot to the updated version of Ubuntu and the GRUB menu did not change. I dont know what to do.

---

### Post by Bartender on 2012-02-04
You might want to try [this]("https://help.ubuntu.com/community/Boot-Repair").  If you can get to another PC (Linux or Windows with ImgBurn installed) download and make this bootable disc.  It appears to be an automagic bootloader repair utility.  Might be easier than trying to manually fix it.

If GRUB is the problem!

---

### Post by jorpoveda on 2012-02-04
I have already fixed the problem, now it seems that my Ubuntu has some issues with graphics specially because I use a NVIDIA graphic card on this PC. 

What I am really interested is in updating the GRUB menu so it looks like the one in 11.10, with the Previous Linux Version option. Is there another way to accomplish this?

---

### Post by bogan on 2012-02-05
Hi!, **jorpoveda**.

You Posted:>  Error was not solved, I still cant boot to the updated version of Ubuntu  and the GRUB menu did not change. I dont know what to do.Be aware that the Grub menu display will only change if the editing using grub-update or -install - or Grub Customizer, see below - is done from the active installation, usually the first one in the list.> What I am really interested is in updating the GRUB menu so it looks  like the one in 11.10, with the Previous Linux Version option. Is there  another way to accomplish this?     To edit and re-arrange the Grub menu, plus add a background image, alter fonts and colours, and much else, you want Grub Customiser. It is an easy to use Graphics tool.

[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134) Go to Post #1 for a full explanation.>   now it seems that my Ubuntu has some issues with graphics specially because I use a NVIDIA graphic card on this PC.  For this your best bet is MAFoElffen's Magnum Opus in his Sticky Thread in the Installation & Updates Forum:[http://http://ubuntuforums.org/showthread.php?t=1743535&page=94]("http://http//ubuntuforums.org/showthread.php?t=1743535&page=94")  Go to Post #2 there is an index, or #280 is specific to nvidia drivers.

If your Video card is a recent one, Series 2, 4, 0r 5 you may find that the nvidia-current driver is not suitable.

Either Post the details of your system and card, or go to nvidia.com/drivers and download the driver it advises.

Chao!, **bogan**.

---

### Post by jorpoveda on 2012-02-06
I will check those drivers and thanks for yhe info on updating the GRUB, njow it looks nice and with more order.

---

