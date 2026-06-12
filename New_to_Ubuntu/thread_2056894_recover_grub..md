---
title: "recover grub."
date: 2012-09-12
forum: New to Ubuntu
---

### Post by uadm on 2012-09-12
Hello dear members.
I wanna ask your help in my grub problem.
Story: I have Ubuntu 12.04 Server, and wanted to install lm-sensors, but its don't locate any sensors in my system. I read here, that there is a chance that ic can be fixed if ill modify ```
/etc/default/grub
``` with ```
GRUB_CMDLINE_LINUX="acpi_enforce_resources=lax"
``` and than  ```
sudo update-grub2
```. Bu it killed my grub. After reboot i got blackscreen and reboot after login + password.
I tried to fix it with ```
boot-repair
```, but it totally killed grub, and i cant start more, all i have is ```
grub rescue>
```So i run live-cd and tried to reinstall grub like discribed in that article:
[http://odzangba.wordpress.com/2011/05/14/455/](http://odzangba.wordpress.com/2011/05/14/455/)
```
fdisk -l shows
``````
Disk /dev/mapper/isw_dafeaicgej_Volume0: 250.1 GB, 250056151040 bytes
255 heads, 63 sectors/track, 30400 cylinders, total 488390920 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000513a8

                              Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_dafeaicgej_Volume0p1   *        2048   470753279   235375616   83  Linux
/dev/mapper/isw_dafeaicgej_Volume0p2       470755326   488390655     8817665    5  Extended
/dev/mapper/isw_dafeaicgej_Volume0p5       470755328   488390655     8817664   82  Linux swap / Solaris

Disk /dev/mapper/isw_dafeaicgej_Volume0p1: 241.0 GB, 241024630784 bytes
255 heads, 63 sectors/track, 29302 cylinders, total 470751232 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

**Disk /dev/mapper/isw_dafeaicgej_Volume0p1 doesn't contain a valid partition table**

Disk /dev/mapper/isw_dafeaicgej_Volume0p2: 9029 MB, 9029288960 bytes
255 heads, 63 sectors/track, 1097 cylinders, total 17635330 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

                                Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_dafeaicgej_Volume0p2p1               2    17635329     8817664   82  Linux swap / Solaris

Disk /dev/mapper/isw_dafeaicgej_Volume0p5: 9029 MB, 9029287936 bytes
255 heads, 63 sectors/track, 1097 cylinders, total 17635328 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

**Disk /dev/mapper/isw_dafeaicgej_Volume0p5 doesn't contain a valid partition table**

Disk /dev/sdc: 8103 MB, 8103395328 bytes
196 heads, 32 sectors/track, 2523 cylinders, total 15826944 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

```Volume0 its my raid1.

```
sudo grub-install --root-directory=/mnt /dev/mapper/isw_dafeaicgej_Volume0
```Tell me that all was fine, no errors, than i umount partition, rebooting. and i see grub loader with 7 systems (5 linuxes with ??????? and 2x Memtest).

Please. Help me to recover my system, you are my last hope. 
Sorry for my bad English.
Thanks.

---

### Post by dozdozez on 2012-09-12
I have nerver used a raid, but if you have one i think that you should activate it before reparing grub.

Look these links, i think they may be useful for you:

[http://askubuntu.com/questions/19789/restoring-grub2-on-software-raid-0-using-livecd-after-windows-7-wiped-it](http://askubuntu.com/questions/19789/restoring-grub2-on-software-raid-0-using-livecd-after-windows-7-wiped-it)
[https://help.ubuntu.com/community/Grub2/Installinghttps://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installinghttps://help.ubuntu.com/community/Grub2/Installing)


Good luck!

---

### Post by YannBuntu on 2012-09-12
Please indicate your Boot-Info URL. [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by ibbill on 2012-09-12
I have used this repair disk 3 or 4 times has always worked all the best.

[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by uadm on 2012-09-13
Thanks for answers, guys!
**ibbill** ive tried it in first case, it not works for me, like now.
**YannBuntu**[http://paste.ubuntu.com/1202543/](http://paste.ubuntu.com/1202543/) here it is.
Boot repair said me, that there is no OS found.

---

### Post by YannBuntu on 2012-09-13
> **uadm said:**
> [http://paste.ubuntu.com/1202543/](http://paste.ubuntu.com/1202543/) here it is.

You have RAID, and Boot-Repair-Disk is based on Debian stable which has too old RAID drivers.

Please use Boot-Repair from a 64bit [Ubuntu-Secure]("https://help.ubuntu.com/community/UbuntuSecureRemix") disk. And tell us the new URL that will appear.

---

### Post by uadm on 2012-09-13
**YannBuntu** Here is a new one.
[http://paste.ubuntu.com/1202659/](http://paste.ubuntu.com/1202659/)

---

### Post by YannBuntu on 2012-09-13
Much better. Now your RAID is correctly detected and activated.

The problem now is that grub-install fails:

```
grub-install --recheck /dev/mapper/isw_dafeaicgej_Volume0
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
No path or device is specified.
Try `/usr/sbin/grub-probe --help' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
```

You should create a bug report here: [https://bugs.launchpad.net/ubuntu/+source/grub2/+filebug](https://bugs.launchpad.net/ubuntu/+source/grub2/+filebug)

One question: you wrote in post#1 that your server is 12.04. Are you sure? (there is apparently no 12.04 on this disk, only one 10.04)

---

### Post by uadm on 2012-09-13
> **YannBuntu said:**
> Much better. Now your RAID is correctly detected and activated.
You should create a bug report here: [https://bugs.launchpad.net/ubuntu/+source/grub2/+filebug](https://bugs.launchpad.net/ubuntu/+source/grub2/+filebug)
...
One question: you wrote in post#1 that your server is 12.04. Are you sure? (there is apparently no 12.04 on this disk, only one 10.04)

Thanks. Ill report.
After working boot-repair i ran gparted, and make "check" of my Volume0p1, and after reboot i dont saw
>  and i see grub loader with 7 systems (5 linuxes with ??????? and 2x Memtest).
but i saw again
```
error: incompatible license.
grub rescue>
```
What i can do now to fix my server? work is stopped :[

Omg, now i even don't sure about version. That server was here wen i came, and old admin said that it is 12.04, but before there was 10.04.

Thanks!

---

### Post by YannBuntu on 2012-09-13
> **uadm said:**
> Omg, now i even don't sure about version. That server was here wen i came, and old admin said that it is 12.04, but before there was 10.04.

ok. So this must be the 10.04 one.

Let's try to fix it manually:

1) boot on your Ubuntu-Secure CD
2) choose "Try Ubuntu"
3) open a terminal (Ctrl+Alt+T)
4) type the following commands one by one:
```
sudo mount /dev/mapper/isw_dafeaicgej_Volume0p1 /mnt
for w in dev dev/pts proc sys; do sudo mount -B /$w /mnt/$w ;done
sudo chroot /mnt grub-install --recheck /dev/mapper/isw_dafeaicgej_Volume0
```
and tell me their outputs.
5) Reboot and tell me if better

---

### Post by Bashing-om on 2012-09-13
Just a reminder (american expression: do not teach grand-father how to suck eggs) on some raid levels ..grub must be installed out side of the raid arrays. What raid level is the op working with ?

a mere attempt to try to help <==BDQ

---

### Post by uadm on 2012-09-14
**Bashing-om **its Raid 1 Failure rate[/SIZE][/SIZE]


**YannBuntu**
```
[SIZE=1]ubuntu@ubuntu:~$ sudo mount /dev/mapper/isw_dafeaicgej_Volume0p1 /mnt
ubuntu@ubuntu:~$ for w in dev dev/pts proc sys; do sudo mount -B /$w /mnt/$w ;done
ubuntu@ubuntu:~$ sudo chroot /mnt grub-install --recheck /dev/mapper/isw_dafeaicgej_Volume0[/SIZE]
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
No path or device is specified.
Try `/usr/sbin/grub-probe --help' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
ubuntu@ubuntu:~$
```

The boot-repair says:
```
The boot files of [Ubuntu 10.04.4 LTS] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair].
```
When i ran gparted, it shows me that for Volume0
```
First Sector: 2,048
Last Sector:  470,753,279
```
Is it too far from start of the disk?

> **YannBuntu said:**
> You should create a bug report here: [https://bugs.launchpad.net/ubuntu/+source/grub2/+filebug](https://bugs.launchpad.net/ubuntu/+source/grub2/+filebug)
Can You explain me please, what to describe in bug report? I am a newbie here.

---

### Post by YannBuntu on 2012-09-14
> **uadm said:**
> ```
[SIZE=1]ubuntu@ubuntu:~$ sudo mount /dev/mapper/isw_dafeaicgej_Volume0p1 /mnt
ubuntu@ubuntu:~$ for w in dev dev/pts proc sys; do sudo mount -B /$w /mnt/$w ;done
ubuntu@ubuntu:~$ sudo chroot /mnt grub-install --recheck /dev/mapper/isw_dafeaicgej_Volume0[/SIZE]
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
No path or device is specified.
Try `/usr/sbin/grub-probe --help' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly
```

ok. This confirms that the bug is in GRUB.

> **uadm said:**
> Is it too far from start of the disk?

Yes.

Let's first report the bug:
1) Boot a Ubuntu liveCD, choose "Try Ubuntu". Create a Launchpad account if you haven't yet
2) Login to your account
3) Go here: [https://bugs.launchpad.net/ubuntu/+source/grub2/+filebug](https://bugs.launchpad.net/ubuntu/+source/grub2/+filebug)
4) Summary: "grub-probe: error: cannot find a device for /boot/grub"
5) Description: "grub-install fails with the following error: 
grub-probe: error: cannot find a device for /boot/grub
See original thread: http://ubuntuforums.org/showthread.php?t=2056894"
6) Validate the report
7) tell us the URL of the report so that we can follow-up

Then:
8.) use Gparted from liveCD to reduce the size of your Ubuntu partition from 241GB to 100GB. (reduce it from the right-side , sot that it still starts at the beginning of the disk). 
9) Reboot the PC.
10) Tell us what you observe.
11) If any problem, run Boot-Repair and tell us the new URL that will appear.

---

### Post by uadm on 2012-09-14
> **YannBuntu said:**
> 
8.) use Gparted from liveCD to reduce the size of your Ubuntu partition from 241GB to 100GB. (reduce it from the right-side , sot that it still starts at the beginning of the disk). 
But now i have 125 gb of used space. I need to mirror all to other pc, or i can set ~130gb, not 100 and all be safe?

---

### Post by YannBuntu on 2012-09-14
1) backup all your documents on an external disk (or DVDs) if you haven't yet

2) reduce the used space from 125G to <80GB (less is better, as [Ubuntu can block if the partition is full]("https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/610358")). Then reduce the partition size to 100GB.

---

### Post by uadm on 2012-09-17
> **YannBuntu said:**
> 1) backup all your documents on an external disk (or DVDs) if you haven't yet

2) reduce the used space from 125G to <80GB (less is better, as [Ubuntu can block if the partition is full]("https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/610358")). Then reduce the partition size to 100GB.

Hello YannBuntu.
I've reduced used space up to 35gb, and reduced patrition size to 78gb, than ran boot-repair... And nothing changed..
When i as splitting space i set "Free space preceding - 0 Mb", But after operations i get "First Sector: 2048" In volume info.
[http://paste.ubuntu.com/1210881/](http://paste.ubuntu.com/1210881/)
Here is an new log.

And sorry for delay. Here is a bug report:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1051927](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1051927)
Thanks for help.

---

### Post by YannBuntu on 2012-09-17
thanks for the report. I hope that devs will answer.

Meanwhile you can try to install GRUB into sda and sdb:
1) Backup all your data
2) Run Boot-Repair --> Advanced options --> "GRUB location" tab --> tick the "Place GRUB into: **sda**" --> Apply. Write on a paper the new URL that will appear.
3) Run Boot-Repair --> Advanced options --> "GRUB location" tab --> tick the "Place GRUB into: **sdb**" --> Apply. Write on a paper this 2nd new URL that will appear.
4) Reboot the PC and indicate if it's better. If not, please indicate the 2 URLs that are on your paper.

---

### Post by uadm on 2012-09-18
[http://paste.ubuntu.com/1212699/](http://paste.ubuntu.com/1212699/) here is log after **sda**
[http://paste.ubuntu.com/1212700/](http://paste.ubuntu.com/1212700/) here is after **sdb**
After reboot nothing changed : **grub rescue>** :(
As I understand - problem is that we cant access to the /boot/grub?

---

### Post by YannBuntu on 2012-09-18
Yes, this is what GRUB returns. I'm sorry I can't help more. Let's wait for GRUB devs suggestions.

---

### Post by uadm on 2012-09-21
May be some new info about how to fix grub?
Its silently on launchpad.

---

### Post by YannBuntu on 2012-09-21
I can't help more here, sorry. I will ask help to other forum helpers I know.

---

### Post by uadm on 2012-09-21
> **YannBuntu said:**
> I can't help more here, sorry. I will ask help to other forum helpers I know.

Thanks!

---

### Post by JKyleOKC on 2012-09-21
I'm one of those that Yann pointed to this problem, but unfortunately I've never used RAID so can't be much help with this situation...

Yann, would it help to try Lilo instead of Grub? If the problem is in grub-probe as things seem to indicate, perhaps an alternate bootloader -- maybe even burg -- could be a workaround until grub gets fixed... Just a wild thought since I don't know enough about the innards of RAID to know.

---

### Post by YannBuntu on 2012-09-21
**@JKyleOKC**, I think your suggestion is good. (I generally prefer to find a solution via the default bootloader in order to report the bug and improve Ubuntu, but this time GRUB devs don't answer so we'll have to find a workaround...)
Among alternative bootloaders, there are Lilo and also GRUB Legacy, and GAG, but I am not familiar with them, and never tried them on RAID, so I can't help much...

**@RAID experts:**
Another point I am not sure is where the bootloader should be installed in uadm's case :
1) on /dev/mapper/isw_dafeaicgej_Volume0 ?
2) or on sda and sdb?
(GRUB2 failed with both)
Is there a RAID expert who could answer this?

**@uadm:** please could you look into your BIOS settings and tell me which entries are available in the "boot order" ?

---

### Post by oldfred on 2012-09-21
I also do not know RAID, but I believe grub2's boot loader has to be installed to the root of the RAID not sda or sdb.

if RAID, see post #7 for an example.
For RAID reinstall from liveCD
sudo apt-get install mdadm
[http://ubuntuforums.org/showthread.php?t=2022679](http://ubuntuforums.org/showthread.php?t=2022679)

---

### Post by YannBuntu on 2012-09-21
@fred: for sure Uadm doesn't need mdadm, because his RAID is automatically activated on liveCD.
AFAIK there are different kinds of RAIDs: 
- some need mdadm, some need dmraid (which is preinstalled in Ubuntu). I think Uadm has a dmraid RAID.
- some need GRUB to be installed in the RAID (like the example you pointed), some need GRUB in sda&sdb...

---

### Post by uadm on 2012-09-25
Thanks for help Guys.

> **YannBuntu said:**
> **@uadm:** please could you look into your BIOS settings and tell me which entries are available in the "boot order" ?Here it is:
Boot Option priorities:
1. Intel Volume0
2. UEFI: JetFlash //my livecd

For info - here is my motherboard: [P8H61-M LE]("http://www.asus.com/Motherboards/Intel_Socket_1155/P8H61M_LE/#specifications")
May be you need some additional info?

---

### Post by YannBuntu on 2012-09-25
Volume0 corresponds to /dev/mapper/isw_dafeaicgej_Volume0 , so I think GRUB must be installed on /dev/mapper/isw_dafeaicgej_Volume0

This what Boot-Repair did by default (post#16), so now we come back to the "cannot find a device for /boot/grub" error of GRUB: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1051927](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1051927)

---

### Post by uadm on 2012-09-25
Maybe we can try to install any other boot loader?

---

### Post by oldfred on 2012-09-25
Normally you do install to the root of the RAID. But this looks like an UEFI system. So with RAID and UEFI do you still have to have a efi partition? I do not know.

Or change UEFI to boot in BIOS mode and then install to root of RAID should work.

---

### Post by YannBuntu on 2012-09-25
@fred: according to post#1, Ubuntu was working without EFI partition nor BIOS-Boot, so the BIOS is setup in Legacy mode.

---

### Post by uadm on 2012-09-27
> **oldfred said:**
> Normally you do install to the root of the RAID. But this looks like an UEFI system. So with RAID and UEFI do you still have to have a efi partition? I do not know.

Or change UEFI to boot in BIOS mode and then install to root of RAID should work.
YannBuntu was right - its not UEFI, it runs with Legacy mode.

So can we try to run another bootloader?

---

### Post by YannBuntu on 2012-09-27
I added recently an option in Boot-Repair to install GRUB Legacy:
[http://ubuntuforums.org/showpost.php?p=12257745&postcount=549](http://ubuntuforums.org/showpost.php?p=12257745&postcount=549)
Please try it and tell us the **new URL** + what you observe after reboot.

---

### Post by uadm on 2012-09-27
Hello Yann.
I had tried Grub Legacy:
1. [Running boot-repair: got some errors]("http://paste.debian.net/193540/")
2. [Pasting required commands]("http://paste.debian.net/193539/") - seems all ok.
3. [boot-repair log]("http://paste.debian.net/193538/")
in result:
error: file not found.
grub rescue>

---

### Post by YannBuntu on 2012-09-27
For information: with GRUB Legacy, the error was

```
$grub-install --recheck /dev/mapper/isw_dafeaicgej_Volume0
Probing devices to guess BIOS drives. This may take a long time.
/dev/mapper/../dm-0 does not have any corresponding BIOS drive.
```

Now, you can try with Lilo or GAG... i hope someone can guide you.

If i were you, i would try to disable RAID in the BIOS, then reinstall Ubuntu.

---

### Post by oldfred on 2012-09-27
I think with grub legacy, you always had to have the /boot partition outside of the RAID. 

It is only with grub2 and its updates that it includes many more drivers, so it works with RAID, some of the newer formats, and other configurations like UEFI.

---

### Post by uadm on 2012-09-27
I am not advanced user in linux, so can You tell me next:
1. When I disable raidm i need to enable it again when i were reinstalling Ubuntu?
2. Reinstall - it means full reinstall (all data lost) or some kind of update?
3. Its possible to save my configurations and apply its after reinstallation of ubuntu? (php, mysql, odbc, redmine, etc.) I burned tonns of time to configure it (because i'm newbie in linux, and because big amount of software).
4. It there any chance to fix it without data loss? 
Thanks.

---

### Post by YannBuntu on 2012-09-27
1. When I disable raidm i need to enable it again when i were reinstalling Ubuntu?  --> no, my idea is to avoid problems by disabling completely RAID from your PC

2. Reinstall - it means full reinstall (all data lost) or some kind of update?  --> full reinstall. But you can backup documents (and /home hidden files) before, and restore them once you have reinstalled. 
Remark: the English documentation is poor about this subject ([https://help.ubuntu.com/community/HomeFolder](https://help.ubuntu.com/community/HomeFolder)), i will try to improve it when i have time.

3. Its possible to save my configurations and apply its after reinstallation of ubuntu? (php, mysql, odbc, redmine, etc.) I burned tonns of time to configure it (because i'm newbie in linux, and because big amount of software). --> program configurations should be inside the hidden /home files& folders.

4. It there any chance to fix it without data loss? --> yes

---

### Post by uadm on 2012-09-28
The problem is - I am using raid to keep my data more safety. So, I dont know is disabling raid will be right move.
And will i have same problem, if i choose Debian, for example?
Thanks.

---

