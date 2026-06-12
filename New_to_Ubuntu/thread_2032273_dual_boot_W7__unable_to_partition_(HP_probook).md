---
title: "dual boot W7 : unable to partition (HP probook)"
date: 2012-07-23
forum: New to Ubuntu
---

### Post by Jumbo94 on 2012-07-23
Hello,

I just bought a Probook 4530s HP (W7 fitted).

I want to dual boot Ubuntu 12.04 LTS (I have a live CD ordered on the net).
My HD is defragmented and I released space on C.

When I try to install, I have two possibilities only : "Erase the disk an install Ubuntu" or "Something else" (I translate from French).

I select "Something else" and my partitions are :

/dev/sda1 (ntfs)   size : 314 MB used : 105 MB
/dev/sda2 (ntfs)   s : 380597 MB u : 61387 MB
unused                size : 344654 MB
/dev/sda3 (ntfs)   s :19217 MB u : 16292 MB
/dev/sda4 (fat32) s : 5363 MB u : 3077 MB

I select the line "unused" to define my partitions, but when I click on "New partition table", "Add" or "Modify" nothing happends. (others keys are active).

Moreover, I ignore what to select in "Hardware where the program will be installed".

That's where I'm glued...


PS : without auto-partitioning, I plan to proceed this way (I'm a beginner and that's web found data) :
root = 15 GO, swap = 4 or 6 GO (my computer is 4 GO RAM), /home : remaining space


What's your opinion ? Thanks for help.

---

### Post by Bufeu on 2012-07-23
Strange... Can be a damaged CD. Re-burn it. If that don't work, try Wubi. May be a bad hard drive.

EDIT: I got around 1 167 000 results on [Google]("http://www.google.com/search?q=install+ubuntu+alongside+is+not+shown"), maybe you can find something there?

---

### Post by bkratz on 2012-07-23
Generally HP uses all 4 available primary partitions. HP tools, windows backup, system boot and windows.  Most people end up making backup dvd's and deleting either hp tools or windows backup files freeing up a partition for other operating systems.


Here is a sample thread

[http://ubuntuforums.org/showthread.php?t=1853014](http://ubuntuforums.org/showthread.php?t=1853014)

---

### Post by ajgreeny on 2012-07-23
Bkratz has it right.  HP has already used your 4 possible partitions.as shown in your partition info from the "Something Else" disk preparation screen.

You will need to delete one of those partitions, and it certainly should not be sda1 or sda2, which are essential for the windows OS.  I do not know what will be best as I can not terll what is on sda3 or sda4, but I suspect that sda4 is hp-tools, and sda3 is a recovery partition.

Re: your partition plans etc, they look good to me, though with 4 GB ram I think 4GB swap will be plenty; I doubt if it will ever be used unless you go into standby mode.

---

### Post by gerrygprs on 2012-07-23
I used Wubi on a HP laptop running Windows 7. I chose my C drive, and selected 20 GB for Ubuntu. Rebooted, and it started off my Ubuntu install. I then logged in to my Linux desktop, shutdown, and when I restarted my PC, it gave me an option for which OS to use (Dual boot).

I didn't have to configure anything, mess around with partitioning like years before. Everything worked right off the bat (sound, display, wifi). Overall time was no more than 30 mins tops. Most of it was downloading the software.

Open source OS have come a long way. I am really considering getting rid of Windows but I need to play a little bit more around with it to see if Ubuntu is right based on the programs I need.

---

### Post by oldfred on 2012-07-23
@gerrygprs
wubi is afile  inside the Windows NTFS partition. If you delete Windows you also delete your wubi install.

Good link from bkratz and info from ajgreeny.

More info.

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. 
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

---

### Post by audiomick on 2012-07-23
Good advice from OldFred, as usual.

Regarding this
> **Jumbo94 said:**
> Hello,PS : without auto-partitioning, I plan to proceed this way (I'm a beginner and that's web found data) :
root = 15 GO, swap = 4 or 6 GO (my computer is 4 GO RAM), /home : remaining space


Looks good to me. If you want the suspend function to work properly, you need to have a little more swap than your RAM. If you know you will never want to suspend, you might be able to get away with less  swap if you want to. Maybe 1GB or so. With 4GB of RAM, as long as you are not doing anything really RAM intensive like editing three films at once or something, you probably will never really use your swap space except for the suspend function.

---

### Post by Jumbo94 on 2012-07-24
Many thanks for your answers.

I will delete HP_RECOVERY or HP_TOOLS partition.

I tried to create recovery DVDs, but I had only four items and had to abort.
What are the effects or replacing HP_RECOVERY(E:) by DVDs ?

It is perhaps simpler to delete HP_tools partition : as far as I understand HP_tools allows BIOS access via Windows. I modify DOS extremely rarely and very basically, so it seems to be no use for me.

But I read in HP tools partition discussion that, if I want to upgrade HP software, it will make HP_tools partition reappear creating a mess. Is it a real threat ?


About the swap partition, I think to the "old days" of my new laptop (my former computer is 8 years old). In a few years, will it deal better with the net, videos, and so on, with 4 or 6 Go than with 1 or 2 (it is 4 Go RAM) ?

---

### Post by oldfred on 2012-07-25
You only need swap at  4GB if hibernating. You actually do not want to use swap as it is on the order of 10 times slower than RAM. If you want to edit videos or load very many large programs all at once then you may use swap.  But to really edit videos you cannot have enough RAM.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Do not know details of HP_tools. Some have just created another logical partition and copied it back and said it worked.

---

### Post by Jumbo94 on 2012-07-26
Thanks Oldfred,

indeed I found on French HP forum detailed data about deleting Hp tools primary partition to create a logical one.

Anyway, I plan to work Ubuntu. W7 will be there for few applications.

In each case I have to burn recovery DVDs, so I will do what is simplier :
- remove Hp recovery partition
- make a single free space with the new an former liberated spaces
- install Ubuntu.


About "Device for boot loader installation", which option do I have to select ?

1- /dev/sda ATA ST9750420AS (750.2 GB)
2- /dev/sda1 Windows 7 (loader)
3- /dev/sda2 Windows 7 (loader)
4- /dev/sda3 Windows Vista (loader)
5- /dev/sda4

(On my laptop sda1 = system, sda2 = C:, sda3 = HP_RECOVERY, sda4 = HP_TOOLS)

Regards

---

### Post by sid0972 on 2012-07-26
you have to select this one

1- /dev/sda ATA ST9750420AS (750.2 GB)

and make your mount point as " / " (without the quotes)

---

### Post by Jumbo94 on 2012-07-29
Hello,

I burnt recovery DVDs and deleted Hp_recovery partition. I installed Ubuntu 12.04 LTS : W7 and Ubuntu seem to work. :D

Many thanks for your answers. It was probably basical, but for me it was a difficult job to collect data to know how to proceed and how to avoid major system problem. :(

In fact I planed to install Ubuntu as I think it is important to have alternatives to Microsoft and which sometimes is not so convenient.

Not being abble to use my old printer with a new laptop decided me in one day time.

But now, it's my new Canon Lide 110 that refuses to work !

As far as I can read on the net, it doesn't seem so easy to solve. I made an attempt adding scanners libraries from Ubuntu softwares library but without success...

Do you have a solution ?

Thanks

---

### Post by oldfred on 2012-07-29
Do not know about your Cannon. I got Pixma 160 with scanner & printer about 5 years ago. It did not work at all. Then I found Cannon Asia had drivers.  But for the last few years,  it just works. Although 12.04 had a bit of regression as it would print only 1 page until some updates came thru. Not sure if totally working or not as I do not print a lot.

---

### Post by Jumbo94 on 2012-07-30
In fact it was easy... I just have to practise ! There are several scanner softwares in Ubuntu library.

My thread is solved now. Many thanks. :D

Jumbo94

---

