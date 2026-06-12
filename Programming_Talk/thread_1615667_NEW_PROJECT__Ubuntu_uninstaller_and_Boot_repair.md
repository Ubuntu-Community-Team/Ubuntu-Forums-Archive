---
title: "NEW PROJECT : Ubuntu_uninstaller and Boot_repair"
date: 2010-11-07
forum: Programming Talk
---

### Post by YannBuntu on 2010-11-07
**Ubuntu Secure Remix** is a slightly improved Ubuntu Live-CD designed especially to install Ubuntu in dual-boot with Windows (or MacOS).

[IMG]http://doc.ubuntu-fr.org/lib/exe/fetch.php?hash=1504c6&media=http%3A%2F%2Fpix.toile-libre.org%2Fupload%2Fimg%2F1312537751.png[/IMG]

**_[Downloads]("https://help.ubuntu.com/community/UbuntuSecureRemix")_:** 
Ubuntu Secure can be downloaded here : [https://sourceforge.net/p/ubuntu-secured/](https://sourceforge.net/p/ubuntu-secured/)

**_Functionalities:_**
- same functionalities as the normal Ubuntu CD, but also :
- automatically backup of the MBRs when installing Ubuntu (CleanUbiquity), which is highly recommended for dual-boot Ubuntu-Windows (or MacOS)
- integrates [OS-Uninstaller]("https://help.ubuntu.com/community/OS-Uninstaller") (tool to uninstall any Operating System from your PC)
- integrates [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair"): tool to repair the PC boot (GRUB/MBR)

Enjoy :)

Ubuntu Secure does not aim at becoming a new distribution, but just to let people install Ubuntu without losing their MBR, until this functionality is [included officially in next releases of Ubuntu]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/747279") :D

**You can contribute by** :
- voting on Launchpad for these bugs: [1st]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/806291"), [2nd]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/747279"), [3rd]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/653474"), [4th]("https://bugs.launchpad.net/os-uninstaller/+bug/823152")
- [translating]("https://translations.launchpad.net/boot-repair/trunk") (now >30 languages)
- suggesting improvements
[URL="https://sourceforge.net/p/ubuntu-secured/home/Home/"]
Official website of Ubuntu-Secure-Remix[/URL]

---

### Post by YannBuntu on 2010-11-08
**Current version : v0.87** (click here, then on the "Télécharger ce fichier" link)
Remark : to facilitate the tests, I commented the lines that delete Ubuntu, and that restore the original bootsector. Of course you can uncomment them to test the whole thing :)

Please give me your feedback. :guitar:

---

### Post by v1ad on 2010-11-08
downside of it, is they still lose that disk space after they remove Ubuntu, u can format it to ntfs but it won't merge with the original one. but overall it seems like a good idea.

---

### Post by YannBuntu on 2010-11-08
You are right, but I don't think it would be a good idea to expand Windows partition with this Ubuntu uninstaller (except if someone knows a reliable method that does not break Windows). I prefer the user do it with Windows tools. ;)

---

### Post by wilee-nilee on 2010-11-08
So how is this program going to reload the mbr and what is it going to put there when it does. 

This is actually quite easy to do any way, every windows install only needs one command in a recovery console to reload the MS bootloader. I like the idea though, it would make many peoples lives easier I suspect if it could be a actual part of the Ubuntu or any Linux setup really.

None of those links are really bugs but people just not knowing what their doing to be honest, the dialogue shows this.

---

### Post by P4man on 2010-11-08
> **wilee-nilee said:**
> So how is this program going to reload the mbr and what is it going to put there when it does. 

Curious about that too. If you are going to remove grub and replace it with the windows bootloader (assuming the app checks for other linux installs and only does this if it finds windows and no linux), you might even run in to legal trouble. Silly as it may sound, I dont think you can freely distribute the windows MBR.

---

### Post by wilee-nilee on 2010-11-08
> **P4man said:**
> Curious about that too. If you are going to remove grub and replace it with the windows bootloader (assuming the app checks for other linux installs and only does this if it finds windows and no linux), you might even run in to legal trouble. Silly as it may sound, I dont think you can freely distribute the windows MBR.

Sure would make my life boring, I like helping in this area, oh well sooner or later I will be put out to pasture when I become even more incoherent.;)

---

### Post by YannBuntu on 2010-11-08
> **wilee-nilee said:**
> Sure would make my life boring, I like helping in this area (snip)

I hope this app will give you time to help in other areas ;)

Indeed, the app does not use any fixmbr command nor any "generic" MBR, so AFAIK there is no legal issue. It creates an exact copy of _your_ MBR in a file called save-63-sectors.img , that you will find in /boot folder of all your Linux, and in the / folder of all other OSs. And it restores this MBR if needed. 

Also, a fixmbr command or a "generic" MBR would not work in case of Windows MBR/BIOS lock (anti-copy system that prevents Windows or your PC to start if your MBR is not the original one :mad: ).

You are right, if the app detects another Linux, it does not restore the MBR but just reinstalls GRUB so that your GRUB is updated. :)

---

### Post by wilee-nilee on 2010-11-08
Are you going to have it able to copy a upgrade mbr say from whatever to whatever MS OS? Lets say I have XP and Maverick dual booted, I buy Windows 7, I delete XP and do a partition pre-format and as we know the mbr gets the windows bootloader. So how will you dd the mbr then?

Not trying to put road blocks up, I suspect you have this figured out just curious how.

---

### Post by YannBuntu on 2010-11-08
Good remark :)

For the moment, I just put a warning for the user : "if Windows was installed after Ubuntu, please don't use this uninstallation tool".

To improve this, I need a way to check if the other OSs (Windows, MacOS, etc.) are older or not than the MBR backup. If someone has a tip, please tell me :)

---

### Post by YannBuntu on 2010-11-15
**VERSION 0.87 AVAILABLE** : [http://dl.free.fr/iKMAcNRfT](http://dl.free.fr/iKMAcNRfT) (click on "Télécharger ce fichier" to download it)

**Improvements:**
- clean_ubuntu_uninstaller : correction of detection of other Linux (thanks to Babdu89)
- clean_boot_repair : correction of detection of disks with linux
- clean_boot_repair : improvement of verbose


Remark : this version has fake file delete and MBR restore, so that you can test it safely. Your terminal logs will be appreciated :)

---

### Post by YannBuntu on 2010-11-18
**VERSION 0.88** : [http://dl.free.fr/rHjMPA96a](http://dl.free.fr/rHjMPA96a)  (click on "Télécharger ce fichier")

**Improvements:**
- choice of the place to reinstall Grub
- possibility to choose not to reinstall Grub
- improvement of texts
- cleaning of code

---

### Post by YannBuntu on 2010-12-01
**VERSION 0.892** : [http://dl.free.fr/fXew6DIKL](http://dl.free.fr/fXew6DIKL)  (click on "Télécharger ce fichier")

**Improvements:**
- more robust reinstall of Grub
- security confirmation if Windows (or other OS) has been installed after Ubuntu
- improvement of texts

**@testers :** put the scripts in a USB key. Boot in live-CD, and when in live-session, first start the clean_ubuntu_installer with the following command :
[HTML]sudo bash ./clean_ubuntu_installer[/HTML]
You can cancel Ubiquity when its window appears, this is only to save your MBR. -> you can check a file called save-63-sectors.img appeared in all your partitions.
Then you can test the clean_boot_repair and the clean_ubuntu_uninstaller. This version is still inhibited, I commented the dangerous lines so you can test it without really erasing the selected partition.

**All functionnalities have been implemented, all cases are taken into account, so I am waiting your feedbacks before proposing a non-inhibited version** :)

---

### Post by YannBuntu on 2010-12-07
Updated the first post of this topic.

Question for experts : how many sectors are there before the 1st partition of a disk ?

---

### Post by nvteighen on 2010-12-07
> **YannBuntu said:**
> Updated the first post of this topic.

Question for experts : how many sectors are there before the 1st partition of a disk ?

I'm not quite versed on these low-level details of programming, but AFAIK, the first partition is immediately after the MBR, which is 512 bytes long... which I think equals 1 sector in most filesystems.

---

### Post by YannBuntu on 2010-12-07
Thank you for your answer. 

The Uninstaller seems to work for Windows-Linux dual-boot. I may propose a new version soon...

---

### Post by YannBuntu on 2011-01-31
**Version0.89999-7 :** [URL="http://dl.free.fr/eCx1x9aEO"]http://dl.free.fr/eCx1x9aEO
[/URL]
- now available as ISO
- many, many improvements thank to French users feedback :guitar:

Remark : French is by default, but you can choose English at start-up of the live-CD.

---

### Post by YannBuntu on 2011-03-03
Preview of the next version :

[[img]http://pix.toile-libre.org/upload/img/1299159724.png[/img]](http://pix.toile-libre.org/?img=1299159724.png)

[[img]http://pix.toile-libre.org/upload/img/1299160068.png[/img]](http://pix.toile-libre.org/?img=1299160068.png)

[[img]http://pix.toile-libre.org/upload/img/1299160096.png[/img]](http://pix.toile-libre.org/?img=1299160096.png)

It can now uninstall any OS ! :guitar:

**I need your help to correct the English strings, and translate it (it is currently only in English and French).**

---

### Post by cgroza on 2011-03-03
If this program is open source, where is the source? I only saw the binaries and I think it was written in C++, which I am learning right now, would not mind if I would read some code. :D

A source forge page would be great.

---

### Post by YannBuntu on 2011-03-03
Here is the code : [https://sourceforge.net/projects/os-uninstaller/files/](https://sourceforge.net/projects/os-uninstaller/files/)
It is written mainly in bash.

Thanks in advance for your advice :P

---

### Post by cgroza on 2011-03-03
> **YannBuntu said:**
> 
It is written mainly in bash.
:P
The icon set played me tricks, :D :D.

---

### Post by YannBuntu on 2011-03-03
Sorry, no C++ in this app, bash and python are enough :)

---

### Post by YannBuntu on 2011-03-06
**New version :** [Version 0.9](http://sourceforge.net/projects/os-uninstaller/files/ubuntu-10.10-remix-for-easy-multiboot.iso/download)
[[img]http://pix.toile-libre.org/upload/img/1299314740.jpg[/img]](http://pix.toile-libre.org/?img=1299314740.jpg)

Features:
- now in English :D
- automatically backup of the MBRs when installing Ubuntu (CleanUbiquity)
- allow to uninstall any Linux distribution using CleanUbiquity
- allow to uninstall any Linux distribution in dual-boot with another Linux using GRUB
- allow to uninstall Windows, MacOS, and other OS
- allow to repair the PC boot (when Windows can't boot any more, or when GRUB is broken...)
- allow to reinstall GRUB in 1 click
- allow to restore the MBR backup in 1 click


[[img]http://pix.toile-libre.org/upload/img/1299159724.png[/img]](http://pix.toile-libre.org/?img=1299159724.png)


[[img]http://pix.toile-libre.org/upload/img/1299426403.png[/img]](http://pix.toile-libre.org/?img=1299426403.png)

---

### Post by YannBuntu on 2011-03-06
I just uploaded again the ISO as there was one file missing.

I need your help to translate the sofware. (it is now just in English and French).

**To help translating, please [download this file]("http://sourceforge.net/projects/os-uninstaller/files/cleanuninstallertranslations/download")** , translate the sentences in your language, then send it to me by email.

---

### Post by YannBuntu on 2011-03-07
New menus :

[[img]http://pix.toile-libre.org/upload/img/1299502283.png[/img]](http://pix.toile-libre.org/?img=1299502283.png)

[[img]http://pix.toile-libre.org/upload/img/1299502334.png[/img]](http://pix.toile-libre.org/?img=1299502334.png)

---

### Post by YannBuntu on 2011-03-08
New features : 

[[img]http://pix.toile-libre.org/upload/img/1299636749.png[/img]](http://pix.toile-libre.org/?img=1299636749.png)

[[img]http://pix.toile-libre.org/upload/img/1299636787.png[/img]](http://pix.toile-libre.org/?img=1299636787.png)

---

### Post by YannBuntu on 2011-03-12
[[img]http://pix.toile-libre.org/upload/img/1299314740.jpg[/img]](http://pix.toile-libre.org/?img=1299314740.jpg)

**[Download last version:](http://sourceforge.net/projects/os-uninstaller/files/ubuntu-secured-remix-10.10.iso/download)**
- automatically backup of the MBRs when installing Ubuntu (CleanUbiquity), which is highly recommended for dual-boot Windows-Ubuntu
- allow to uninstall any Linux distribution using CleanUbiquity
- allow to uninstall any Linux distribution in dual-boot with another Linux using GRUB
- allow to uninstall Windows, MacOS, and other OS
- allow to repair the PC boot (when Windows can't boot any more, or when GRUB is broken...)
- allow to reinstall GRUB in 1 click
- allow to restore the MBR backup in 1 click

New feature : from now I enable my PPA repositories, so that you can update the tools without re-downloading the ISO.

---

### Post by Toxicbits on 2011-03-12
Kudos, that's really cool.

When are you going to submit it to the Software Center?

---

### Post by YannBuntu on 2011-03-12
Thanks for your encouragements ! ):P

Yes, I will propose these tools to the Ubuntu developpers. As explained in [the 1st message of this topic]("http://ubuntuforums.org/showpost.php?p=10084551&postcount=1"), the live-CD I propose here is only for letting everybody discover&use the 3 tools I included. Two Linux distributions already included them, and I hope Ubuntu will soon include them too :D

---

### Post by YannBuntu on 2011-03-13
New version : 

Improvements :
- includes Spanish translations

[[img]http://pix.toile-libre.org/upload/img/1300027085.png[/img]](http://pix.toile-libre.org/?img=1300027085.png)

---

### Post by Toxicbits on 2011-03-13
If you are going to use a launcchpad ppa, will one be able to translate it online collaboratively? It's rather uncomfortable to do it just using the text file

---

### Post by YannBuntu on 2011-03-13
Yes, I wish.

But indeed I don't know how to integrate .pot , .pot and .mo in our software. Any clue (tutorial..) would be appreciated. :P

---

### Post by YannBuntu on 2011-03-14
In addition to [Ubuntu Secured Remix 10.10](http://sourceforge.net/projects/os-uninstaller/files/ubuntu-secured-remix-10.10.iso/download), you can now discover :
 - [Xubuntu Secured Remix 10.10](http://sourceforge.net/projects/os-uninstaller/files/xubuntu-secured-remix-10.10.iso/download)
 - [Kubuntu Secured Remix 10.10]("http://sourceforge.net/projects/os-uninstaller/files/kubuntu-secured-remix-10.10.iso/download")

which are the normal version of Xubuntu and Kubuntu in which I added the 3 tools (Clean-Ubiquity, OS-Uninstaller, Boot-repair).

---

### Post by Toxicbits on 2011-03-14
I don't know much about coding, but I found this tutorial: [http://mywiki.wooledge.org/BashFAQ/098](http://mywiki.wooledge.org/BashFAQ/098)

Hope that helps

Toxicbits

---

### Post by nvteighen on 2011-03-14
Yeah, it'd be really nice that you used Launchpad Translations for this... I can spot an error in your Spanish translation right in the screenshot you've posted.

Change:
**¿Cual sistema operativo desee desinstalar?**

By:
**¿Cu_á_l sistema operativo dese_a_ desinstalar?**

---

### Post by YannBuntu on 2011-03-23
**@nvteighen :** thank you, I will correct the Spanish string this weekend.

**@all :** with the current **K**ubuntu Secured Remix 10.10, Clean-Ubiquity (the automatic MBR backup) and Boot-Repair are ok, but OS-uninstaller does not start. To make it start, first update the "cleanosuninstaller" package (this should install the python-glade2 package). If will upload the corrected ISO this weekend.

**Toxicbits :** thanks a lot, I think this is what I needed.

---

### Post by YannBuntu on 2011-04-01
Clean-Ubiquity has already been used with success by 2000 French users, I think it is the moment to propose it for official inclusion in Ubuntu's live-CD : [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/747279](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/747279)

Concerning the 2 other tools (OS-Uninstaller and Boot-Repair), they are only translated in 3 languages (English, French, Spanish), so I will wait for them to be translated in all the languages of the live-CD before proposing them for inclusion.

---

### Post by YannBuntu on 2011-04-02
I just managed to integrate translations into .mo files, it will make life easier for translators :)  (.po files can be found here : [http://sourceforge.net/projects/os-uninstaller/files/po.tar.gz/download](http://sourceforge.net/projects/os-uninstaller/files/po.tar.gz/download) )
I also improved integration into Kubuntu and Xubuntu.
Examples :
[[img]http://pix.toile-libre.org/upload/img/1301783209.png[/img]](http://pix.toile-libre.org/?img=1301783209.png)
[[img]http://pix.toile-libre.org/upload/img/1301783230.png[/img]](http://pix.toile-libre.org/?img=1301783230.png)
[[img]http://pix.toile-libre.org/upload/img/1301783118.png[/img]](http://pix.toile-libre.org/?img=1301783118.png)
[[img]http://pix.toile-libre.org/upload/img/1301783188.png[/img]](http://pix.toile-libre.org/?img=1301783188.png)

---

### Post by YannBuntu on 2011-04-03
You can now easily help by translating .po files : [http://sourceforge.net/projects/os-uninstaller/files/po.tar.gz/download](http://sourceforge.net/projects/os-uninstaller/files/po.tar.gz/download)

and voting for inclusion in Ubuntu's rep : [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/747279](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/747279)  ("Does this bug affect you ?)

---

### Post by YannBuntu on 2011-04-07
The OS-Uninstaller and Boot-Repair tools are now translated in 5 languages:
- English
- Spanish
- French
- Portuguese
- Swedish

Don't hesitate to [help](http://sourceforge.net/projects/os-uninstaller/files/po.tar.gz/download) if you speak another language !

:popcorn:

---

### Post by YannBuntu on 2011-04-09
The 3 tools (Clean-Ubiquity, OS-Uninstaller and Boot-Repair) work perfectly also in Natty !
Here is Ubuntu Secured Remix 11.04  ! ;)
[http://sourceforge.net/projects/os-uninstaller/files/ubuntu-secured-remix-11.04.iso/download](http://sourceforge.net/projects/os-uninstaller/files/ubuntu-secured-remix-11.04.iso/download)

Enjoy :)

---

### Post by YannBuntu on 2011-05-26
**New versions available :** :guitar:

- [Ubuntu Secured Remix 11.04]("http://sourceforge.net/projects/os-uninstaller/files/ubuntu-secured-remix-11.04.iso/download")  ( = Ubuntu 11.04  + Clean-Ubiquity v2 + Boot-Repair v2 + OS-Uninstaller v2 ) (md5: 0ba6083f0cfafb05afd58f0b0df1b8fc )
- [Xubuntu Secured Remix 11.04]("http://sourceforge.net/projects/os-uninstaller/files/xubuntu-secured-remix-11.04.iso/download")  ( = Xubuntu 11.04  + Clean-Ubiquity v2 + Boot-Repair v2 + OS-Uninstaller v2 ) (md5: 7690eb4b7bd04aa5e252c3b5fc2544de )

**Enjoy !**

---

### Post by YannBuntu on 2011-05-27
Now the tools included in Lubuntu : [Lubuntu Secured 11.04]("http://sourceforge.net/projects/os-uninstaller/files/lubuntu-secured-remix-11.04.iso/download")  (md5: e3bda598df67eb6dffceb0ef5b142130 )

---

### Post by YannBuntu on 2011-05-29
Now available for download :

[Kubuntu Secured 11.04 ]("http://sourceforge.net/projects/os-uninstaller/files/kubuntu-secured-remix-11.04.iso/download") ( = Kubuntu 11.04 with [Clean-Ubiquity]("https://launchpad.net/~yannubuntu/+archive/clean-ubiquity") safe installer, [Boot-Repair]("http://ubuntuforums.org/showpost.php?p=10871917&postcount=1"), and [OS-Uninstaller]("http://ubuntuforums.org/showpost.php?p=10871988&postcount=1"))

---

### Post by YannBuntu on 2011-05-31
For those who need Long Term Support :

Download: [Ubuntu Secured 10.04 LTS]("http://sourceforge.net/projects/os-uninstaller/files/ubuntu-secured-remix-10.04.iso/download") ( = Ubuntu 10.04.2 LTS with [Clean-Ubiquity]("https://launchpad.net/~yannubuntu/+archive/clean-ubiquity") safe installer, [Boot-Repair]("http://ubuntuforums.org/showpost.php?p=10871917&postcount=1"), and [OS-Uninstaller]("http://ubuntuforums.org/showpost.php?p=10871988&postcount=1"))

---

### Post by YannBuntu on 2011-06-01
Hi all,
After installing a 64bits Ubuntu on my HD, I finally managed to integrate Clean-Ubiquity (and the 2 other tools) in Ubuntu 64 bits :

[Ubuntu Secured 11.04 **64 bits**]("http://sourceforge.net/projects/os-uninstaller/files/ubuntu-secured-remix-11.04-64bits.iso/download") :guitar:

md5: 5f643b88ea373071583f86fec041fa35

---

### Post by YannBuntu on 2011-06-03
New versions available : see [message #1]("http://ubuntuforums.org/showpost.php?p=10084551&postcount=1") of this thread !

---

### Post by YannBuntu on 2011-06-04
Synthesis of the md5 of all available ISO:
- Ubuntu Sécurisée (French Remix) 11.04 32bits (md5: 1cb323c9c97d23ebcfc9181c914a36d4  )
- Ubuntu Secured 11.04 32bits (md5: 0ba6083f0cfafb05afd58f0b0df1b8fc )
- Xubuntu Secured 11.04 32bits (md5: 7690eb4b7bd04aa5e252c3b5fc2544de )
- Lubuntu Secured 11.04 32bits (md5: e3bda598df67eb6dffceb0ef5b142130 )
- Kubuntu Secured 11.04 32bits (md5: 48dc65c1268cbd3734f82ea26e757a7e )
- Ubuntu Sécurisée (French Remix) 10.04 32bits (md5: 68847d70b49b98653452fd483e2146d1  )
- Ubuntu Secured 10.04 LTS 32bits (md5: 493c8d683776738be68ab603f6d94a0b )
- Ubuntu Sécurisée (French Remix) 11.04 64bits (md5: 17df9f53a69dfed692fb77340310e927  )
- Ubuntu Secured 11.04 64bits (md5: 5f643b88ea373071583f86fec041fa35 )
- Xubuntu Secured 11.04 64bits (md5: c791b68ae7cfdc2bbd53665909356a95 )
- Kubuntu Secured 11.04 64bits (md5: 7e5407693ad13acf6b0cce828efbc0d9 )
- Ubuntu Secured 10.04 LTS 64bits (md5: e957380f933078b1b3df6f23834cae51 )

Download links in post#1 of this thread.

---

### Post by YannBuntu on 2011-08-04
Hi all,

I am on the way to release a new version of the 3 tools included in Ubuntu Secured CD.
[B]To make it better, I am searching volunteers with one of the following config:
- either separate /boot partition
- either RAID partitions[/B]

If you are in one of these configurations, please contact me !



By the way, Ubuntu Secured CD is now downloaded ~1000times/week, I would be happy if everybody could **vote for the following bugs:**

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/747279](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/747279)
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/806291](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/806291)

Thanks for your support ! :)

---

### Post by YannBuntu on 2011-08-09
Only few days before I upload the tools for rep integration ! :guitar:

It is the good time to **translate them into your language : **[https://translations.launchpad.net/boot-repair/trunk](https://translations.launchpad.net/boot-repair/trunk)

---

### Post by YannBuntu on 2011-08-10
A new version of the tools (Boot-Repair , OS-Uninstaller and Clean-Ubiquity) has arrived in the PPA, so please:

**Each time you boot on Ubuntu Secured CD, don't forget to connect internet and update your packages via this command:**

```
sudo apt-get update && sudo apt-get upgrade
```

before using Boot-repair or OS-Uninstaller.

---

### Post by Hylas de Niall on 2011-10-18
Wow! Great idea!
The added apps are exactly what wished i'd had, but was living without for the past however-many installations!
I didn't know they even existed!
*Thanks so much* for this iso, and will there be an 11.10 version?

---

### Post by YannBuntu on 2011-10-20
Happy you like it :)
Of course there will be a 11.10 ISO, but I need to buy a new PC for this, so maybe in 2 or 3 weeks... :)

---

### Post by YannBuntu on 2011-11-10
new ISOs with updated tools:
[B]- Ubuntu Secured Remix 11.10 32bits
- Ubuntu Secured Remix 11.10 64bits[/B]

available for download here: [https://sourceforge.net/p/ubuntu-secured/](https://sourceforge.net/p/ubuntu-secured/)

---

### Post by gabba on 2011-12-06
Would it be possible to add an advanced option to wipe the extra space **between the MBR and the first partition** where stupid applications like to write? I had to manually write zeros on sectors 1 to 62 in order to stop getting warnings about sectors used by FlexNet when reinstalling grub.

The procedure is already well described [here]("http://ubuntuforums.org/showthread.php?t=1661254"), but automating it would reduce the risk of messing up. Of course you need a big heavy warning about the possibility of some windows apps using that DRM or some HP system tools not working afterwards.

Lastly, a small request: would it be possible to open the pastebin page where you sent the report in the browser, instead of having the user copy it from the final dialog box? People tend to dismiss dialog boxes very quickly, and there's no obvious way to recover that URL afterwards except restarting the whole, long repair process.

Thanks for this nice software!

---

### Post by YannBuntu on 2011-12-06
Hello Gabba,

thanks for your suggestions, both are very interesting ! :KS
For better follow-up, please create a blueprint for each of them: [https://blueprints.launchpad.net/boot-repair](https://blueprints.launchpad.net/boot-repair)  (if you don't have time I will do it)

---

### Post by gabba on 2011-12-06
Done :) :

[https://blueprints.launchpad.net/boot-repair/+spec/wipe-hidden-sectors-track](https://blueprints.launchpad.net/boot-repair/+spec/wipe-hidden-sectors-track)

[https://blueprints.launchpad.net/boot-repair/+spec/auto-open-report-pastebin](https://blueprints.launchpad.net/boot-repair/+spec/auto-open-report-pastebin)

Edit: lol, just noticed that I still have 9.04 listed as my OS at the left. Except that the powers that be don't want me to edit my details until I have 50 posts. Given that I post about twice a year, I guess I'll update it in 2031. See you then.

---

### Post by YannBuntu on 2011-12-06
Thanks Gabba

(i do too have problems with this forum... i cannot find the way to change my signature :o )

---

### Post by Elwood72 on 2011-12-14
I have a quick question....

If my system came with Windows pre-installed; can I safely un-install it, and still leave my Ubuntu10.10 OS intact?

---

### Post by YannBuntu on 2011-12-14
Yes. OS-Uninstaller will simply remove Windows and update your GRUB menu.

Just a detail : if you only use Ubuntu, I recommend you go in the Advanced options and choose to format in "EXT" instead of "NTFS".

---

### Post by Elwood72 on 2011-12-14
> **YannBuntu said:**
> Yes. OS-Uninstaller will simply remove Windows and update your GRUB menu.

Just a detail : if you only use Ubuntu, I recommend you go in the Advanced options and choose to format in "EXT" instead of "NTFS".

Just to be sure;which "Advanced Options" ?

---

### Post by YannBuntu on 2011-12-15
After you choose to uninstall "Windows" and validate, a confirmation window will appear, with "Advanced options":

[[img]http://pix.toile-libre.org/upload/img/1323944035.png[/img]](http://pix.toile-libre.org/?img=1323944035.png)

---

### Post by TombstoneTim on 2012-03-04
Hello YannBuntu. I am new here, and also a new Ubuntu User.
 
I have downloaded the 64 bit Secured Remix CD iso file, but I can't seem to find a way to burn it to a CD. The downloaded file size is 706MB.
 
I am going to install it after Windows 7 on a 64bit laptop, with 6GB memory.
 
I am trying to use Nero 7 on a Windows XP PC to burn the image, but it won't allow me to burn it. The max size that I can burn a CD with is 702MB.
 
Any suggestions on what other program I can use? Or can the file size be reduced some way?
 
Thanks for creating this great product! I like the idea of having backups if something goes wrong with my install.
 
--Tim

---

### Post by YannBuntu on 2012-03-04
Hello Tim, welcome among us :)
you can either:
-burn the ISO on a DVD
- or (better) create a live-USB  (via LiliUSB or else.. see [https://help.ubuntu.com/community/Installation/FromUSBStick#Creating_a_bootable_Ubuntu_USB_flash_drive](https://help.ubuntu.com/community/Installation/FromUSBStick#Creating_a_bootable_Ubuntu_USB_flash_drive) )

---

### Post by TombstoneTim on 2012-03-04
Ok, I got it now. I incorrectly assumed that it must be a CD only. 
I made a DVD and all worked fine. Thanks for the help YannBuntu!

---

### Post by fun2599 on 2012-04-12
:idea: The actual download link is [http://sourceforge.net/projects/ubuntu-secured/files/ ]("http://sourceforge.net/projects/ubuntu-secured/files/")

---

### Post by YannBuntu on 2012-05-04
Ubuntu Secure Remix 12.04 LTS now available !!!

---

### Post by bgold2005 on 2012-10-04
(I posted this as a general question elsewhere but someone posted os-uninstall which led here)

I have windoze and grub in sda1,sda2 and sda3
the 'good" ubuntu on sda12 and 13

I. if I uninstall the os's in/on the intervening partitions wont your project disc delete those partitions for me?
if so wont the higher partitions re-number?
if so will your utility/disc re-set the "good ubuntu" and grub to take this into account?

II. my windoze is already booted from grub. so what are my options for installing either just the os uninstaller, or your entire secure ubuntu, without blowing away grub or windoze (or maybe keeping my "good" ubuntu)?

thanks

---

### Post by YannBuntu on 2012-10-04
Hello
> **bgold2005 said:**
> I have windoze and grub in sda1,sda2 and sda3
the 'good" ubuntu on sda12 and 13

Please indicate your [Boot-Info URL]("https://help.ubuntu.com/community/Boot-Info"), this will describe your current situation in detail.

> **bgold2005 said:**
> I. if I uninstall the os's in/on the intervening partitions wont your project disc delete those partitions for me?
if so wont the higher partitions re-number?
if so will your utility/disc re-set the "good ubuntu" and grub to take this into account?

OS-Uninstaller will format the system partition in NTFS by default (you can check and change via the Advanced options).
Higher partitions won't be re-numbered.
It will automatically reinstall/update GRUB so that the GRUB menu will take the change into account.

> **bgold2005 said:**
> II. my windoze is already booted from grub. so what are my options for installing either just the os uninstaller, or your entire secure ubuntu, without blowing away grub or windoze (or maybe keeping my "good" ubuntu)?

[Ubuntu-Secure]("https://help.ubuntu.com/community/UbuntuSecureRemix") disk is just an Ubuntu disk with 2 tools preinstalled (Boot-Repair and OS-Uninstaller).
Using OS-Uninstaller from Ubuntu-Secure or from a Ubuntu CD is equivalent.
If you ask OS-Uninstaller to remove your "old" Ubuntu, it won't touch your other systems.

---

### Post by YannBuntu on 2012-10-04
To make it easy the use of Boot-Repair (and OS-Uninstaller), i added 2 launchers in Ubuntu-Secure:

[[img]http://pix.toile-libre.org/upload/img/1349343251.png[/img]](http://pix.toile-libre.org/?img=1349343251.png)

---

### Post by YannBuntu on 2012-10-19
Ubuntu Secure Remix **12.10** is now available !!!

[http://ubuntuforums.org/showthread.php?t=2073446](http://ubuntuforums.org/showthread.php?t=2073446)

---

### Post by Joeviocoe on 2012-10-28
I want to triple boot (in 3 partitions, on same drive) Windows 7, Windows 8, and Ubuntu 12.04
 Everything works as expected until I install Ubuntu.  Windows 7  install creates the 100Mb boot partition... Windows 8 installs a new  graphical bootloader and  shows both Windows 7 and Windows 8.... 

and  when I install Ubuntu, GRUB is installed.  But GRUB won't show any  entries for the Windows 7 and 8 installations.  It DOES show, however,   an old installation of Windows 7 on another drive (since it has its own  bootloader intact).


 I tried repairing the windows boot with the repair cd and running  Bootrec /fixboot and /fixmbr.  And using Boot-Repair (recommended) from a bootable USB.
Ran Grub-update... But I still don't have detectable GRUB entries for Windows 7 or 8.  All attempt to manually enter GRUB entries for those Windows OSs have failed.


[http://paste.ubuntu.com/1312058/](http://paste.ubuntu.com/1312058/)  before
[http://paste.ubuntu.com/1312096/](http://paste.ubuntu.com/1312096/)  after
 my Boot-Info

sda is an old install of Win7 with Ubuntu embedded install (wubi) on my HDD.
sdb is an SSD and is what I WANT to triple boot with Win7, Win8, and Ubuntu.
sdb1 is my NTFS 100MB that was used by Windows as the Boot partition, and is now GRUB
sdb2 is my Win7 partition
sdb3 is my Win8 partition (I don't know why it says XP, maybe from my  attempts to fix).
sdb4 is Ubuntu 12.04

Am  I missing something?  
What is the best way to install all 3 OSs on my sdb (SSD)?  I want separate partitions and don't want to use VM or VHD.
Thanks.

---

### Post by YannBuntu on 2012-10-28
**@Joeviocoe:** welcome on the forums. This specific thread was dedicated to Ubuntu-Secure-Remix-12.04, so please open a new thread here: [http://ubuntuforums.org/newthread.php?do=newthread&f=333](http://ubuntuforums.org/newthread.php?do=newthread&f=333)

**@moderators:** please close this thread. New version is now available and discussed here: [http://ubuntuforums.org/showthread.php?t=2073446](http://ubuntuforums.org/showthread.php?t=2073446)

---

### Post by nothingspecial on 2012-10-28
Closed at the OP's request.

---

