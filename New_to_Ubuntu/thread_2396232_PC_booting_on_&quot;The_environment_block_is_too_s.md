---
title: "PC booting on &quot;The environment block is too small&quot;"
date: 2018-07-12
forum: New to Ubuntu
---

### Post by mohamedsouleimanepiro on 2018-07-12
I have an issue with my asus X555L. When I boot a message appears "The evironment block is too small, press any key to continue" 

But when I press, there is a black screen and nothing happens. I have to shut down the PC.

This is a followup to this issue [https://askubuntu.com/questions/1054006/pc-still-booting-on-gnu-grub-even-after-boot-repair](https://askubuntu.com/questions/1054006/pc-still-booting-on-gnu-grub-even-after-boot-repair)

And here is the boot-repair report [http://paste.ubuntu.com/p/scgxHJPzQb/](http://paste.ubuntu.com/p/scgxHJPzQb/)

After boot-repair and booting again Ubuntu appears in UEFI only with USB plugged and I see this menu [ATTACH=CONFIG]280374[/ATTACH] of course when I choose any of the options only a black screen appears. 


Thank you,

---

### Post by oldfred on 2018-07-12
Do you get grub menu?
or grub>?
It looks like Boot-Repair's reinstall of grub added a missing ubuntu boot entry in UEFI.

Have you updated UEFI from Asus. Many systems have needed UEFI updates.

Many Asus need additional boot parameters. Best to experiment first to see which one or combination works, then we can make those permanent.

       Problems Installing on ASUS F555U   needed boot option pci=nomsi
[URL="http://ubuntuforums.org/showthread.php?t=2303665"]http://ubuntuforums.org/showthread.php?t=2303665
      [/URL]
 Asus x555u w/o pci=nomsi - space issue on drive and runaway log files filling drive
[https://ubuntuforums.org/showthread.php?t=2327103&page=3](https://ubuntuforums.org/showthread.php?t=2327103&page=3)
[https://ubuntuforums.org/showthread.php?t=2327570](https://ubuntuforums.org/showthread.php?t=2327570) 
            ASUS X540U pci=noaer instead of pci=nomsi and it also worked
[https://ubuntuforums.org/showthread.php?t=2391201](https://ubuntuforums.org/showthread.php?t=2391201)

At grub menu, you press e for edit and at end of Linux line replace or add to splash quiet parameters. If you replace them, you then can see boot process.
       
Similar to this nomodeset parameter, but you have Intel video and should not need nomodeset.
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) 
    
 

    [URL="http://ubuntuforums.org/showthread.php?t=2303665"]
[/URL]

---

### Post by mohamedsouleimanepiro on 2018-07-12
Hi @Oldfred,


I reinstalled Ubuntu and it is working but I have a bug/crash/freeze every 30 minutes at least. The system is very unstable, and when I reboot sometimes the UEFI has no boot option but when I reboot again Ubuntu works again. One of the last crashes gave this screen [ATTACH=CONFIG]280377[/ATTACH]and I had to do a hard shut down. [FONT=Arial][FONT=Verdana]
[/FONT][/FONT]
[FONT=Arial]As for Grub menu, I don't get it no more as well as grub>. Whether I have the UEFI or a regular Ubuntu boot with some delay. [/FONT]
[FONT=Arial]
[/FONT]
[FONT=Arial]I will try the options for updating  UEFI though, 

[/FONT]
[FONT=Arial]
[/FONT]
[FONT=Arial]Thanks,[/FONT]

---

### Post by oldfred on 2018-07-12
If at all possible do not do hard shutdown. That often corrupts file system and then you need repairs with fsck.

        Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key) 
   Holding down Ctrl+Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is, and S can be before E, but others should be in order
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[https://en.wikipedia.org/wiki/Magic_SysRq_key](https://en.wikipedia.org/wiki/Magic_SysRq_key)
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

Are you booting with one of the suggested boot parameters in the other threads?

---

### Post by mohamedsouleimanepiro on 2018-07-20
Hello again,


I tried all the options above and nothing seems  to work. I don't get Grub menu now and the boot doesn't work, except  that in some boots, I get "environment is too small" followed by a black  screen. 
I have to open a live USB session to get connected. 

I found an [article]("https://doc.ubuntu-fr.org/asus_r511lj") "in French" which is basically about installing Ubuntu on my model X555LJ. 

The article states that the disk should be partitioned to three part: 


    One Ext4 30000 Mo mounted on / 
    One swap of 7000 Mo 
    One ext4, mounted on /home for all the rest. 

But the author is not clear if the Efi partition should be removed or not so I kept it to stay safe.

But the same issues persist and now I can't even boot on Distro.

Thanks,

---

### Post by oldfred on 2018-07-20
I think you will need the boot parameters posted in links above whether BIOS or UEFI. And the crashing was the issue with your system if boot parameter not used. It fills hard drive with log file errors.

UEFI boot on gpt partitioned drives requires the ESP - efi system partition.
If you want BIOS boot you can, but if drive is still gpt then you need a 1 or 2MB unformatted partition with the bios_grub flag for grub to correctly install.

If not installing Windows then gpt is recommended.

Its just that in BIOS mode, Windows has to have MBR partitioning. And in UEFI boot mode it has to have MBR partitioning. Ubuntu will boot from gpt with either UEFI or BIOS if correct partitions are on drive.

---

### Post by mohamedsouleimanepiro on 2018-07-24
[FONT=Arial]Hi  @Oldfred,[/FONT][FONT=Arial]
[/FONT]
[FONT=Arial]
[/FONT]
[FONT=Arial]I think I misunderstood the boot parameters in my previous attempts. [/FONT]
[FONT=Arial]
[/FONT]
[FONT=Arial]I finally tried the pci=nomsi in kernel and pci=noaer as per pictures below: (there is an issue with picture uploads on the forum as no picture uploading works. So I linked Google Drive links instead)

Here is the [URL="https://drive.google.com/open?id=17PF_iziqktjM09xDygf1sm6GDUd3lcns"]Kernel menu
[/URL]
And the boot parameters fixes:

1- [pci=nomsi at end of line]("https://drive.google.com/open?id=1NCi3mTMpDyK0zhVgyg1ZF6ppm9YaXJs0")
2 -[pci=nomsi after splash]("https://drive.google.com/open?id=1zeX4zH2NMH9E2hYYjo09huD1NzJ0niuf")
3- [pci=nomsi before splash]("https://drive.google.com/open?id=1BTISjw_lfqsvdPYhIekD-i22tdCOiuY9") 
4- [pci=nomsi before splash with space]("https://drive.google.com/open?id=11v2VALv190wq6SGQ60mVWkQ69kE9JVV7") [/FONT]
[FONT=Arial]5- [pci=nomsi to replace splash ]("https://drive.google.com/open?id=1tOXwIwbFxV0ytBWmT3n2wdNysEJ818-L")
6- [pci=noaer at end of line]("https://drive.google.com/open?id=1yldcpW_9FxYfJIM2FZxHDIlRAdqGU9d9")
7- [pci=noaer before splash]("https://drive.google.com/open?id=1zv8zpQejO1Xw04rhFQbQhCmLz_4GVPu8")


[/FONT]
[FONT=Arial]But every-time I end up with a similar [screen]("https://drive.google.com/open?id=1OslfHhnWJopS_f_4MCmbbp4e9MRKnTqw"), I have then to reboot using systemctl reboot[/FONT]
[FONT=Arial]and when I tried journalctl -xb I had this [result]("https://drive.google.com/open?id=16lDTeCXRiYiRcrPmX4a24lCqSOCz54S0"). [/FONT]
[FONT=Arial]
[/FONT]
[FONT=Arial]Here is a boot repair report without reparation: [http://paste.ubuntu.com/p/jdg2vSJ3zX/](http://paste.ubuntu.com/p/jdg2vSJ3zX/)


Thanks,[/FONT]
[FONT=Arial]


-- 
Souleimane Piro

[/FONT]

---

### Post by oldfred on 2018-07-24
That looks like you are booting, but in emergency mode. 
Does exit then give standard command line terminal?
So then most like a graphics issue?

Did you update UEFI/BIOS from Asus also?

I normally suggest replacing quiet splash with boot parameters, as then you also see boot process and perhaps other errors. But my new SSD scrolls by so fast I do not see much anyway.

Are you using the pci=nomsi nomodeset ? You probably need both.

The pci=nomsi or pci=noaer will probably need to be made permanent in grub configuration, but nomodeset is only required until you install nVidia driver from Ubuntu repository.

---

### Post by mohamedsouleimanepiro on 2018-07-25
[FONT=Arial]Hi again,[/FONT]

[FONT=Arial]@Oldfred,[/FONT]
[FONT=Arial]
[/FONT]
[FONT=Arial]When I press exit Ubuntu starts loading for a very short time (3 sec) and the same emergency screen reappears until I reboot. [/FONT]
[FONT=Arial]
[/FONT]
[FONT=Arial]I can't really determine if it is a graphics issue. [/FONT]
[FONT=Arial]
[/FONT]
[FONT=Arial]I tried to replace Quiet splash by pci=nomsi and nomodeset and all I have is this [screen]("https://drive.google.com/open?id=1QbHeO-qYRn_M3aXuEaPZ2niPX0DbU62N") which stays frozen until I reboot.  [/FONT]
[FONT=Arial]
[/FONT]
[FONT=Arial]I actually always used the first kernel in the list. but when I tried the second one (recovery mode) I added pci=nomsi before nomodeset pre-entered. I obtained a [menu ]("https://drive.google.com/open?id=1riWA_wX2PEt9g86UgPuNf3jOqRHdp-pn")and then Ubuntu loaded but in 800x600 screen. After rebooting I couldn't access to Grub menu even with shift+down key, only the same "block too small" screen followed by same emergency mode screen. [/FONT]
[FONT=Arial]
[/FONT]
[FONT=Arial]I made a boot repair via live USB and acceded to recovery mode by adding pci=nomsi before nomodeset and I [changed settings for Nvidia.]("https://drive.google.com/open?id=1Gq9ESlXmsxgA9LfjddUa-X7RAvBTE0GF") but now always the same "block too small" and emergency mode. Without any kernel menu. [/FONT]
[FONT=Arial]
[/FONT]
[FONT=Arial]Concerning Bios, yes I updated it to the latest version from Asus website. [/FONT]
[FONT=Arial]
[/FONT]
[FONT=Arial]I tried however to replace Quiet splash by PCI=nomsi followed by nomodeset and I whether end up on the emergency mode screen or I get a frozen screen like [here]("https://drive.google.com/open?id=1_vTvAnr-LNJUIsJ1l4j7n-pycZqA_LSR") that I have to Reisub.[/FONT]
[FONT=Arial]
[/FONT]
[FONT=Arial]
[/FONT]
[FONT=Arial]here is the boot repair report [http://paste.ubuntu.com/p/9JH2DzZdCB/](http://paste.ubuntu.com/p/9JH2DzZdCB/)


Thanks,[/FONT]

---

### Post by oldfred on 2018-07-25
I do not see anything in Boot-Repair's report. It looks normal.
If rescue mode boots and you get low level graphics then it is a graphical issue.
But with nVidia installed it should just work.

Many UEFI laptops with hybrid graphics have settings to turn on or allow one graphical system or the other. I might try those settings.

I found this old answer and some with newer versions said it worked.
[https://askubuntu.com/questions/191852/error-invalid-environment-block-press-any-key-to-continue](https://askubuntu.com/questions/191852/error-invalid-environment-block-press-any-key-to-continue)

---

