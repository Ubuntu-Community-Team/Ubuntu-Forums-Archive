---
title: "Unsure on What Ubuntu Build to Install on Secondary Laptop"
date: 2017-05-16
forum: New to Ubuntu
---

### Post by jgamez065 on 2017-05-16
Hello! I just decided to join the forum because I need help... I have decided to secondary boot Ubuntu on this computer. (Using Windows 10 64 bit). I looked at the compatibility for Ubuntu but it cannot seem to find "HP Pavilion g7 Notebook PC" laptops. I have a little less than 6gb of RAM and over 450+ GB of space. Also curious about, when Ubuntu says 9 months of support and updates what does that mean it becomes unusable after a certain amount of time?



Thanks!

---

### Post by Bucky Ball on 2017-05-16
Welcome. It means that interim releases are supported for nine months after release and LTS versions are supported for five years. In other words, an excellent place for a new comer to start is with an LTS release. I suggest 16.04 LTS. The only reason to change this would be if you have extremely new hardware. The newest release may then be advisable if the LTS is not working well.

'Unsupported' means it will no longer get any updates/upgrades and that includes security updates. It also means you will get little support here (the forums don't support EOL releases) or from Canonical.

To trying Ubuntu. Your first step is to create install media, either USB or DVD, boot from that and 'Try Ubuntu' in a live session. This will allow you to try Ubuntu without changing anything on your disk drive (Ubuntu runs from the install media).

If everything's working fine there, then we can look at installing. Wouldn't worry too much about whether you can find your machine on some compatibility list or not. Some of those pages are dated and incomplete. I haven't looked at one in some time. Best way is to do a search for your machine and Ubuntu and see how other people are going with that combination.

For instance, search for 'HP Pavilion g7 ubuntu'. From what I see with a quick look just at the results, not the links themselves, is that machine has been around since about 12.04. My guess is it will work just fine. 

Hope that helps and good luck.

---

### Post by gordintoronto on 2017-05-17
Within Windows, you will need to shrink a partition to make space for Ubuntu. With MBR hard drives, HP has a nasty habit of consuming all four available primary partitions, so you might need to blow away an existing partition. See Full Circle Magazine, issue 41, page 36.

---

### Post by oldfred on 2017-05-17
Some HP will not boot a flash drive that is gpt partitioned. Some only boot from the USB2 port not USB3 ports.
[http://ubuntuforums.org/showthread.php?t=2213631&p=13468260#post13468260](http://ubuntuforums.org/showthread.php?t=2213631&p=13468260#post13468260)
HP Check if Customized UEFI settings available like this  HP ProBook 4340
[URL="https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216"]https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216

[/URL]
 HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079) 

Most if not all HP are not UEFI dual boot friendly, but many work arounds depending on configuration.

 HP Probook 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886) 

Boot-Repair now does the copy.
      
 Boot-Repair should automatically do copy file with 'use standard EFI file':
[http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi](http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi) 
    [       ]("https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216")
 Copy shimx64.efi to /EFI/Boot/bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186) 
    [URL="https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216"]
[/URL]

---

