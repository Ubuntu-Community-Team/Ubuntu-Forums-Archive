---
title: "Xubuntu install problems"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by Bigtime_Scrub on 2008-06-04
I have a computer I want to put Xubuntu on. It had Ubuntu 8.04 but I was messing around with things and I screwed it up. I want to try Xubuntu now because I wanted to try something different. problem is I downloaded the Xubuntu iso, burned it to CD, and it refuses to boot at start up. I tried doing the wubi.exe installation, it goes through smoothly but then when it says to reboot and I do, Ubuntu loads and not Xubuntu. I don't understand why its doing this, Ubuntu was easy to install, getting rid of it is infuriating. I have a solution though, i am going to put an old copy of windows 2000 on my computer, and then Im going to have Xubuntu go in and erase it and install itself. 


Does anyone have a better solution for getting rid of Ubuntu?

---

### Post by Bigtime_Scrub on 2008-06-04
I understand that I can install Xubuntu via Synaptic in Ubuntu but thats not what I want. Things are working funny because I was messing with dependacies and deleting things in my home folder. I need to wipe my hard drive and install fresh. 

I just wanted to make myself clear.

---

### Post by cariboo on 2008-06-04
Why bother with all that. On your login screen there is button in the lower left hand corner, click on it and choose xfce, login and you are good to go. The underlying distribution is the same whether you choose to use Kubuntu, Xubuntu, Edubuntu or Ubuntu. The only thing that changes is the desktop.

That is the simplified version of it.

Jim

---

### Post by zxscooby on 2008-06-04
Did you remove tho old installation or just install a new one along side it? If both installations are on your hard drive then you should be able to enter the grub menu at boot and select the distro you want loaded.
You should be able to delete the partition your old install is on with the install cd.

---

### Post by superzorro on 2008-06-04
If you already have installed Ubuntu you could follow this guides:

[HTML]http://www.psychocats.net/ubuntu/xubuntu[/HTML]
[HTML]http://www.psychocats.net/ubuntu/purexfce[/HTML]

Just remeber that if you remove completely one desktop environment you will uninstall too the associated software that doesn't come in the new one (for example I think you must install Openoffice in Xubuntu)

---

### Post by Bigtime_Scrub on 2008-06-04
Nothing will boot correctly, i was going to use Knoppix to just delete the partitions but Knoppix wont boot from start. I went back and to the bios to boot from DVD and it wont. :mad:

Nothing will boot from disc and all I get is this screwed up ubuntu. 

I really really want Ubuntu gone. Will a hard drive nuker work? Then I can install Xubuntu fresh.

---

### Post by superzorro on 2008-06-04
Usually when I install Xubuntu I use the Alternative version not the Desktop, I had always better results.

---

### Post by Bigtime_Scrub on 2008-06-04
If I run the "forbidden" code will I be able to install a fresh Xubuntu?

---

### Post by jpryor68 on 2008-06-04
It sounds like you have a bad download or a bad cd burn. In the directory from which you downloaded the xubuntu iso you'll also see *.md5 files. Follow the instructions on this page <https://help.ubuntu.com/community/HowToMD5SUM> to verify that your download isn't corrupted. If it is, download again (and check the md5 sum again).

Once you know you have a good download, burn another installation cd. Use a slow burn speed, such as 4x. The instructions here may help: <https://help.ubuntu.com/community/BurningIsoHowto>. See also the info on "CD Integrity Check" linked on that page.

Once you know you've downloaded a good iso and gotten a clean burn, then you should be able to wipe your disk and install Xubuntu---which you say is what you want to do. As other commentors are pointing out, there are more conservative ways to get from where you are to where you want to be. But if you want to do a clean install, sure why not. It may save you some time and confusion.

---

